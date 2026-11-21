---
title: "Worklog Tuần 4"
date: 2026-10-05
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4

* Tìm hiểu và thực hành dịch vụ lưu trữ đối tượng Amazon Simple Storage Service (Amazon S3): Storage Classes, Versioning, Lifecycle Policies.
* Nắm vững các cơ chế bảo mật dữ liệu trên Amazon S3: Block Public Access, Bucket Policy, Server-Side Encryption và chia sẻ tệp tin an toàn qua Pre-signed URL.
* Tìm hiểu dịch vụ cơ sở dữ liệu quan hệ được quản lý Amazon RDS (Multi-AZ, Read Replicas, Automated Backups) và cơ sở dữ liệu NoSQL Amazon DynamoDB.
* Thực hành kết nối an toàn từ tầng ứng dụng (EC2) tới tầng cơ sở dữ liệu (RDS) đặt trong Private Subnet.

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|------|-----------|-------------|----------------|---------------|
| 2 | **Lưu trữ đối tượng với Amazon S3:** <br> - Tìm hiểu kiến trúc Amazon S3 (Buckets, Objects, Keys) và các lớp lưu trữ (S3 Standard, Intelligent-Tiering, Glacier) <br> - Thực hành khởi tạo S3 Bucket, bật Object Versioning và thiết lập Lifecycle Rule tự động chuyển dữ liệu cũ sang lớp lưu trữ chi phí thấp | 05/10/2026 | 05/10/2026 | https://000057.awsstudygroup.com/ |
| 3 | **Bảo mật S3 & Pre-signed URL:** <br> - Cấu hình S3 Block Public Access và viết JSON Bucket Policy giới hạn quyền truy cập theo IAM Principal và điều kiện IP <br> - Tìm hiểu mã hóa dữ liệu tĩnh (SSE-S3, SSE-KMS) <br> - Thực hành tạo Pre-signed URL bằng AWS CLI để cấp quyền tải lên/tải xuống tệp tin có thời hạn mà không cần mở public bucket | 06/10/2026 | 06/10/2026 | https://000057.awsstudygroup.com/ |
| 4 | **Cơ sở dữ liệu Amazon RDS:** <br> - Tìm hiểu kiến trúc Amazon RDS, phân biệt cơ chế dự phòng Multi-AZ Deployment (High Availability) và Read Replicas (tăng hiệu năng đọc) <br> - Tạo DB Subnet Group nằm trong các Private Subnets <br> - Khởi tạo RDS MySQL/PostgreSQL instance và cấu hình Security Group chỉ cho phép kết nối từ Security Group của App Server | 07/10/2026 | 07/10/2026 | https://000005.awsstudygroup.com/ |
| 5 | **Kết nối App – DB & Sao lưu dữ liệu:** <br> - Thực hành kết nối từ EC2 App Server vào RDS instance trong Private Subnet và khởi tạo schema mẫu <br> - Thực hành tạo DB Snapshot thủ công, kiểm tra tính năng Automated Backup và Point-in-Time Recovery | 08/10/2026 | 08/10/2026 | https://000005.awsstudygroup.com/ |
| 6 | **Tìm hiểu Amazon DynamoDB & Tổng kết:** <br> - Tìm hiểu cơ sở dữ liệu NoSQL Amazon DynamoDB (Partition Key, Sort Key, On-Demand vs Provisioned Capacity) <br> - Thực hành tạo bảng DynamoDB, thêm/truy vấn bản ghi và dọn dẹp RDS instance, S3 bucket sau thực hành | 09/10/2026 | 09/10/2026 | https://000005.awsstudygroup.com/ |

### Kết quả đạt được trong tuần 4

* Làm chủ cách quản lý và tối ưu chi phí lưu trữ trên Amazon S3 thông qua Versioning và Lifecycle Policies.
* Thực thi bảo mật nghiêm ngặt cho kho lưu trữ S3: giữ bucket ở chế độ Private hoàn toàn, kiểm soát truy cập bằng Bucket Policy, mã hóa SSE và cấp quyền truy cập tạm thời qua Pre-signed URL.
* Hiểu rõ kiến trúc triển khai cơ sở dữ liệu Amazon RDS an toàn trong Private Subnet, sử dụng Security Group Chaining (chỉ nhận lưu lượng từ Security Group của tầng ứng dụng) và nắm vững cơ chế Multi-AZ.
* Phân biệt được trường hợp sử dụng giữa cơ sở dữ liệu quan hệ (Amazon RDS) và NoSQL hiệu năng cao (Amazon DynamoDB).
