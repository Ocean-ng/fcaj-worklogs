---
title: "Worklog Tuần 6"
date: 2024-01-01
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu tuần 6

* Thiết lập hạ tầng lưu trữ và phân phối giao diện Web tĩnh cho hệ thống **SecureTable** bằng **Amazon S3** và **Amazon CloudFront** tại Region `ap-southeast-1`.
* Áp dụng cơ chế **Origin Access Control (OAC)** để giữ S3 Bucket ở chế độ riêng tư tuyệt đối (Block Public Access), chỉ cho phép truy cập nội dung qua CloudFront với giao thức mã hóa HTTPS.
* Tìm hiểu sâu về kết nối mạng riêng tư trên AWS thông qua **VPC Endpoints** (Gateway Endpoint và Interface Endpoint / AWS PrivateLink) để hạn chế lưu lượng đi qua Internet công cộng.

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|------|-----------|-------------|----------------|---------------|
| 2 | **Khởi tạo S3 Bucket lưu trữ Frontend tĩnh:** <br> - Tạo S3 Bucket tại `ap-southeast-1` cho các tệp HTML/CSS/JS của giao diện Guest và Staff trong dự án SecureTable <br> - Giữ nguyên cấu hình **Block all public access** và kiểm tra mã hóa mặc định **SSE-S3** | 19/10/2026 | 19/10/2026 | https://docs.aws.amazon.com/AmazonS3/latest/userguide/security-best-practices.html |
| 3 | **Triển khai Amazon CloudFront với Origin Access Control (OAC):** <br> - Khởi tạo CloudFront Distribution kết nối tới S3 Origin thông qua **Origin Access Control (SigV4)** <br> - Cập nhật S3 Bucket Policy chỉ cấp quyền `s3:GetObject` cho Service Principal `cloudfront.amazonaws.com` kèm điều kiện `AWS:SourceArn` | 20/10/2026 | 20/10/2026 | https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/private-content-restricting-access-to-s3.html |
| 4 | **Cấu hình HTTPS, Caching & Định tuyến SPA:** <br> - Thiết lập Viewer Protocol Policy thành `Redirect HTTP to HTTPS` với chuẩn TLS 1.2+ <br> - Cấu hình Default Root Object (`index.html`), Custom Error Responses và kiểm thử truy cập giao diện Web qua tên miền CloudFront | 21/10/2026 | 21/10/2026 | https://000058.awsstudygroup.com/ |
| 5 | **Nghiên cứu kết nối riêng tư với VPC Endpoints:** <br> - Tìm hiểu sự khác nhau giữa **Gateway VPC Endpoint** (miễn phí cho S3 và DynamoDB qua Route Table) và **Interface VPC Endpoint** (dùng AWS PrivateLink & ENI) <br> - Thực hành cấu hình VPC Endpoint Policy giới hạn quyền truy cập vào đúng S3 Bucket/DynamoDB Table chỉ định | 22/10/2026 | 22/10/2026 | https://000008.awsstudygroup.com/ |
| 6 | **Kiểm thử bảo mật S3 Origin & Dọn dẹp tài nguyên lab:** <br> - Kiểm chứng truy cập trực tiếp vào Object URL của S3 bị từ chối (`403 Access Denied`) trong khi truy cập qua CloudFront HTTPS hoạt động bình thường (`200 OK`) <br> - Dọn dẹp các VPC Endpoint thực hành để tránh phát sinh chi phí theo giờ | 23/10/2026 | 23/10/2026 | https://docs.aws.amazon.com/vpc/latest/privatelink/concepts.html |

### Kết quả đạt được trong tuần 6

* Đưa thành công tầng giao diện Web của **SecureTable** lên nền tảng **Amazon S3 + Amazon CloudFront** với tốc độ tải nhanh và truyền tải an toàn qua HTTPS.
* Thực thi nghiêm ngặt tiêu chí bảo mật của Security Pillar: khóa hoàn toàn truy cập trực tiếp vào S3 Bucket nhờ **Block Public Access** kết hợp **CloudFront OAC**.
* Nắm vững kiến trúc kết nối riêng tư bằng **VPC Gateway/Interface Endpoints** giúp bảo vệ lưu lượng nội bộ tới S3 và DynamoDB mà không cần đi ra Internet.
