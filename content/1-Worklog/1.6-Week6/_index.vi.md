---
title: "Worklog Tuần 6"
date: 2024-01-01
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu tuần 6

* Tìm hiểu chuyên sâu về kết nối mạng riêng tư trên AWS thông qua **VPC Endpoints** (Gateway Endpoint và Interface Endpoint / AWS PrivateLink).
* Thực hành triển khai **S3 Gateway Endpoint** giúp các máy chủ EC2 trong Private Subnet truy cập Amazon S3 hoàn toàn qua mạng nội bộ AWS mà không cần NAT Gateway hay Internet Gateway.
* Thực hành triển khai **S3 Interface Endpoint** và mô phỏng kết nối từ môi trường On-premises qua VPN/Private DNS với **Amazon Route 53 Resolver**.
* Thiết lập và kiểm thử **VPC Endpoint Policies** kết hợp **S3 Bucket Policies** để giới hạn chặt chẽ phạm vi truy cập dữ liệu.

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|------|-----------|-------------|----------------|---------------|
| 2 | **Tổng quan VPC Endpoints & Chuẩn bị hạ tầng:** <br> - Phân tích sự khác nhau giữa Gateway Endpoint (miễn phí, định tuyến qua Route Table cho S3/DynamoDB) và Interface Endpoint (dùng ENI trong Subnet, hỗ trợ bởi AWS PrivateLink) <br> - Khởi tạo môi trường mạng VPC và máy chủ EC2 trong Private Subnet bằng CloudFormation template | 19/10/2026 | 19/10/2026 | https://000008.awsstudygroup.com/ |
| 3 | **Triển khai & Kiểm thử S3 Gateway Endpoint:** <br> - Tạo S3 Gateway Endpoint gắn vào Route Table của Private Subnet <br> - Kiểm tra Prefix List tự động thêm vào Route Table <br> - Kết nối vào Private EC2 qua SSM Session Manager và kiểm thử lệnh `aws s3 ls`, `aws s3 cp` thành công mà không đi qua Internet | 20/10/2026 | 20/10/2026 | https://000008.awsstudygroup.com/ |
| 4 | **Triển khai S3 Interface Endpoint cho mô hình On-premises:** <br> - Khởi tạo môi trường mô phỏng On-premises kết nối với VPC đám mây <br> - Tạo S3 Interface Endpoint với Security Group mở cổng HTTPS (443) cho dải mạng On-premises <br> - Kiểm thử truy cập S3 qua Endpoint-specific DNS name bằng tham số `--endpoint-url` | 21/10/2026 | 21/10/2026 | https://000008.awsstudygroup.com/ |
| 5 | **Tích hợp DNS với Route 53 Private Hosted Zone & Resolver:** <br> - Cấu hình Route 53 Private Hosted Zone và bản ghi Alias trỏ về S3 Interface Endpoint <br> - Thiết lập Route 53 Inbound Resolver Endpoint để máy chủ On-premises phân giải tự động tên miền S3 về IP Private của Interface Endpoint (kiểm tra bằng lệnh `dig`) | 22/10/2026 | 22/10/2026 | https://000008.awsstudygroup.com/ |
| 6 | **Bảo mật với VPC Endpoint Policy & Dọn dẹp:** <br> - Viết Custom JSON Policy trên VPC Endpoint chỉ cho phép truy cập duy nhất một S3 Bucket được chỉ định <br> - Cấu hình S3 Bucket Policy với điều kiện `aws:SourceVpce` để khóa truy cập từ ngoài Endpoint <br> - Ghi chép tài liệu thực hành cho phần Workshop và dọn dẹp tài nguyên | 23/10/2026 | 23/10/2026 | https://000008.awsstudygroup.com/ |

### Kết quả đạt được trong tuần 6

* Nắm vững sự khác biệt kiến trúc, chi phí và kịch bản áp dụng giữa **S3 Gateway Endpoint** và **S3 Interface Endpoint (AWS PrivateLink)**.
* Triển khai thành công luồng truy cập S3 hoàn toàn khép kín từ cả trong VPC lẫn mạng On-premises mà không đi qua Internet công cộng, giúp tăng cường bảo mật và giảm chi phí NAT Gateway.
* Hiểu và cấu hình thành công cơ chế phân giải tên miền lai (Hybrid DNS) với **Amazon Route 53 Private Hosted Zone** và **Inbound Resolver**.
* Áp dụng kiểm soát truy cập hai chiều bằng **VPC Endpoint Policy** và **S3 Bucket Policy (`aws:SourceVpce`)**, hoàn thành bộ khung thực hành cốt lõi cho bài Workshop.
