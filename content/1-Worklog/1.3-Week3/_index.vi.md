---
title: "Worklog Tuần 3"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu tuần 3

* Tìm hiểu chuyên sâu về dịch vụ máy chủ ảo Amazon EC2: các dòng Instance Types, Amazon Machine Image (AMI), Key Pair và User Data.
* Nắm vững kiến trúc lưu trữ khối với Amazon EBS (Volumes, Snapshots) và dịch vụ chia sẻ tệp tin Amazon EFS.
* Thực hành kết nối và quản trị máy chủ trong Private Subnet an toàn qua Bastion Host và AWS Systems Manager (SSM) Session Manager (không cần mở port 22 SSH).
* Tìm hiểu cân bằng tải (Elastic Load Balancing - ALB) và tự động co giãn (Amazon EC2 Auto Scaling).

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|------|-----------|-------------|----------------|---------------|
| 2 | **Amazon EC2 & User Data:** <br> - Tìm hiểu các họ EC2 Instance (General Purpose, Compute/Memory Optimized) và mô hình tính phí <br> - Thực hành khởi tạo Amazon Linux 2023 và Windows Server EC2 <br> - Sử dụng User Data script để tự động cài đặt và cấu hình Web Server (Nginx/Apache) khi khởi động | 28/09/2026 | 28/09/2026 | https://000004.awsstudygroup.com/ |
| 3 | **Lưu trữ Amazon EBS & Tham dự AWS Cloud & AI Day 2026 Watch Party:** <br> - Thực hành gắn EBS Volume (`gp3`), tạo EBS Snapshot và đóng gói Custom AMI <br> - Tham dự sự kiện *"AWS Cloud & AI Day 2026 – HCMC Watch Party"* tại Văn phòng AWS Việt Nam (Tầng 26 Bitexco) tìm hiểu về Agentic AI và hiện đại hóa hạ tầng Cloud | 29/09/2026 | 29/09/2026 | https://000004.awsstudygroup.com/ |
| 4 | **Quản trị máy chủ an toàn với SSM Session Manager:** <br> - So sánh mô hình Bastion Host truyền thống với AWS Systems Manager (SSM) Session Manager <br> - Tạo IAM Role gắn policy `AmazonSSMManagedInstanceCore` cho EC2 <br> - Thực hành truy cập shell vào EC2 trong Private Subnet qua trình duyệt mà không cần mở Inbound Port 22 hay dùng SSH Key | 30/09/2026 | 30/09/2026 | https://000014.awsstudygroup.com/ |
| 5 | **Application Load Balancer & Auto Scaling:** <br> - Tìm hiểu kiến trúc High Availability cho tầng Compute với Application Load Balancer (ALB) và Target Groups <br> - Thiết lập Launch Template và Auto Scaling Group (ASG) tự động tăng/giảm số lượng EC2 theo tải CPU | 01/10/2026 | 01/10/2026 | https://000006.awsstudygroup.com/ |
| 6 | **Tham dự sự kiện AWS & Tổng kết tuần:** <br> - Tham dự buổi trò chuyện trực tiếp *"Fireside Chat with Dr. Werner: Navigating the Future of Cloud & AI in Vietnam"* cùng CTO Amazon tại Tầng 26 Bitexco <br> - Kiểm thử khả năng chịu lỗi (Fault Tolerance) sau ALB và dọn dẹp tài nguyên lab (ASG, ALB, EC2, EBS) | 02/10/2026 | 02/10/2026 | https://000004.awsstudygroup.com/ |

### Kết quả đạt được trong tuần 3

* Thành thạo quy trình triển khai, tự động hóa khởi tạo máy chủ Amazon EC2 bằng User Data và đóng gói môi trường chuẩn hóa thông qua Custom AMI.
* Hiểu rõ cách quản lý lưu trữ bền vững trên EC2 với Amazon EBS Volumes và cơ chế sao lưu/phục hồi bằng EBS Snapshots.
* Áp dụng thành công phương pháp bảo mật vận hành hiện đại với **AWS Systems Manager Session Manager**, loại bỏ rủi ro lộ khóa SSH và không cần mở cổng 22 trên Security Group.
* Nắm được cách thiết kế tầng ứng dụng có tính sẵn sàng cao (High Availability) và tự động mở rộng thông qua Application Load Balancer kết hợp Auto Scaling Group.
