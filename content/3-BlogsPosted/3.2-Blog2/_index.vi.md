---
title: "Blog 2"
date: 2026-10-28
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

# Thiết kế kiến trúc mạng khép kín (Zero-Internet Exposure) với AWS PrivateLink và VPC Endpoints

Trong nhiều hệ thống đám mây truyền thống, các máy chủ đặt tại Private Subnet thường phải đi qua **NAT Gateway** và **Internet Gateway** để gọi tới các API dịch vụ của AWS như Amazon S3, DynamoDB, KMS hay Secrets Manager. Mô hình này không chỉ làm tăng chi phí xử lý lưu lượng qua NAT Gateway (tính phí theo giờ và theo từng GB dữ liệu) mà còn mở ra bề mặt tấn công không cần thiết khi lưu lượng phải định tuyến ra biên mạng.

Bài viết này tổng hợp kinh nghiệm thực tế khi thiết kế kiến trúc **Zero-Internet Exposure** bằng **VPC Gateway Endpoint**, **Interface Endpoint (AWS PrivateLink)** và thiết lập vành đai dữ liệu (**Data Perimeter**).

---

### 1. Khi nào dùng Gateway Endpoint và khi nào dùng Interface Endpoint?

AWS cung cấp hai loại VPC Endpoint với cơ chế hoạt động ở hai tầng khác nhau:

| Tiêu chí | Gateway VPC Endpoint | Interface VPC Endpoint (AWS PrivateLink) |
|---|---|---|
| **Dịch vụ hỗ trợ** | Amazon S3 và Amazon DynamoDB | Hơn 100+ dịch vụ AWS (S3, KMS, SSM, Secrets Manager, ECR...), dịch vụ đối tác & dịch vụ nội bộ |
| **Cơ chế định tuyến** | Thêm mục định tuyến (Prefix List `pl-xxxxxx`) vào **Route Table** của Subnet | Tạo card mạng ảo **ENI** có địa chỉ IP Private trực tiếp bên trong Subnet và phân giải qua **DNS** |
| **Truy cập từ On-premises / VPC Peering** | **Không hỗ trợ** (chỉ dùng cho tài nguyên nằm ngay trong VPC đó) | **Hỗ trợ đầy đủ** qua Site-to-Site VPN, Direct Connect, Transit Gateway |
| **Chi phí** | **Miễn phí hoàn toàn** | Tính phí theo giờ cho mỗi ENI + phí dữ liệu xử lý (per GB) |

**Kinh nghiệm thực tiễn:**
* Nếu ứng dụng chạy trên EC2/ECS/Lambda bên trong VPC cần đọc/ghi S3 hoặc DynamoDB → **Luôn bật Gateway Endpoint** (vừa miễn phí, vừa giảm tải cho NAT Gateway).
* Nếu máy chủ từ trung tâm dữ liệu On-premises (kết nối qua VPN/Direct Connect) cần truy cập S3 mà không đi qua Internet → **Sử dụng S3 Interface Endpoint** kết hợp với **Route 53 Inbound Resolver**.

---

### 2. Bài toán Hybrid DNS khi dùng S3 Interface Endpoint từ On-premises

Khi tạo một S3 Interface Endpoint, AWS sinh ra các tên miền riêng có dạng `*.vpce-0123456789abcdef.s3.us-west-2.vpce.amazonaws.com`. Để các ứng dụng ở On-premises vẫn gọi được tên miền chuẩn `bucket.s3.us-west-2.amazonaws.com` mà tự động trỏ về IP Private của Endpoint trong VPC, ta có thể triển khai:

1. **Amazon Route 53 Private Hosted Zone** cho miền `s3.<region>.amazonaws.com` gắn với Cloud VPC, tạo bản ghi `A - Alias` (`*` và `@`) trỏ vào DNS của S3 Interface Endpoint.
2. **Route 53 Inbound Resolver Endpoint** đặt trong Cloud VPC: Hệ thống DNS tại On-premises sẽ cấu hình Conditional Forwarder đẩy các truy vấn `*.s3.<region>.amazonaws.com` lên IP của Inbound Resolver, từ đó nhận về địa chỉ IP Private (`10.x.x.x`) của Interface Endpoint.

---

### 3. Xây dựng vành đai dữ liệu (Data Perimeter) hai chiều

Chỉ tạo VPC Endpoint thôi là chưa đủ về mặt An toàn thông tin. Kẻ tấn công nếu chiếm được một EC2 trong Private Subnet có thể lợi dụng chính VPC Endpoint đó để tải dữ liệu lên một S3 Bucket bên ngoài của kẻ tấn công (Data Exfiltration).

Để khóa chặt hai chiều, ta cần kết hợp đồng thời:

1. **Chiều đi (VPC Endpoint Policy):** Giới hạn Endpoint trong VPC chỉ được phép gọi tới đúng S3 Bucket của tổ chức:
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowOnlyCorporateBucket",
      "Effect": "Allow",
      "Principal": "*",
      "Action": ["s3:GetObject", "s3:PutObject", "s3:ListBucket"],
      "Resource": [
        "arn:aws:s3:::fcaj-internal-data-bucket",
        "arn:aws:s3:::fcaj-internal-data-bucket/*"
      ]
    }
  ]
}
```

2. **Chiều đến (S3 Bucket Policy với `aws:SourceVpce`):** Từ chối mọi truy cập vào S3 Bucket nếu request không đi qua đúng VPC Endpoint đã chỉ định:
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "DenyAccessNotFromVPCE",
      "Effect": "Deny",
      "Principal": "*",
      "Action": "s3:*",
      "Resource": [
        "arn:aws:s3:::fcaj-internal-data-bucket",
        "arn:aws:s3:::fcaj-internal-data-bucket/*"
      ],
      "Condition": {
        "StringNotEquals": {
          "aws:SourceVpce": "vpce-0123456789abcdef0"
        }
      }
    }
  ]
}
```

Ngay cả khi Access Key của một IAM User vô tình bị lộ ra ngoài Internet, kẻ tấn công cũng không thể sử dụng key đó để tải dữ liệu từ S3 Bucket vì request từ máy của kẻ tấn công không thỏa mãn điều kiện `aws:SourceVpce`.
