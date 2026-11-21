---
title: "Worklog Tuần 11"
date: 2026-11-23
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Mục tiêu tuần 11

* Tìm hiểu các dịch vụ phát hiện mối đe dọa thông minh và quản trị tư thế bảo mật đám mây (CSPM): **Amazon GuardDuty**, **AWS Security Hub** và **AWS Config**.
* Đánh giá mức độ tuân thủ bảo mật của tài khoản AWS theo bộ tiêu chuẩn quốc tế **CIS AWS Foundations Benchmark** và **AWS Foundational Security Best Practices**.
* Tìm hiểu phương pháp Quản lý hạ tầng bằng mã (**Infrastructure as Code - IaC**) với **AWS CloudFormation** để chuẩn hóa và tự động hóa việc khởi tạo hạ tầng mạng & bảo mật.
* Khắc phục (Remediation) các cảnh báo cấu hình sai được phát hiện bởi AWS Security Hub.

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|------|-----------|-------------|----------------|---------------|
| 2 | **Phát hiện mối đe dọa với Amazon GuardDuty:** <br> - Tìm hiểu cơ chế phân tích log tự động của Amazon GuardDuty dựa trên Machine Learning và Threat Intelligence từ ba nguồn: CloudTrail Events, VPC Flow Logs và DNS Logs <br> - Kích hoạt GuardDuty (Free Trial 30 ngày), tạo Sample Findings và phân tích mức độ nghiêm trọng (Low, Medium, High) của từng loại cảnh báo | 23/11/2026 | 23/11/2026 | https://docs.aws.amazon.com/guardduty/ |
| 3 | **Quản trị tư thế bảo mật với AWS Security Hub:** <br> - Kích hoạt AWS Security Hub và bộ tiêu chuẩn `AWS Foundational Security Best Practices` cùng `CIS AWS Foundations Benchmark` <br> - Phân tích điểm số bảo mật tổng thể (Security Score) và danh sách các Controls chưa đạt chuẩn trên tài khoản | 24/11/2026 | 24/11/2026 | https://docs.aws.amazon.com/securityhub/ |
| 4 | **Khắc phục lỗ hổng cấu hình (Security Remediation):** <br> - Dựa trên báo cáo của Security Hub, thực hiện khắc phục các cảnh báo ưu tiên cao: bật S3 Block Public Access cấp tài khoản, siết chặt Default Security Group trong mọi VPC, xoay vòng Access Key cũ và bật MFA | 25/11/2026 | 25/11/2026 | https://docs.aws.amazon.com/securityhub/ |
| 5 | **Tự động hóa hạ tầng với AWS CloudFormation (IaC):** <br> - Tìm hiểu cấu trúc template YAML của AWS CloudFormation (`Parameters`, `Resources`, `Outputs`, `Mappings`) <br> - Đóng gói kiến trúc VPC, Private/Public Subnets, Route Tables, Security Groups và EC2 của bài Workshop thành tệp CloudFormation template có thể tái sử dụng | 26/11/2026 | 26/11/2026 | https://000037.awsstudygroup.com/ |
| 6 | **Kiểm thử triển khai Stack & Dọn dẹp:** <br> - Thực hành triển khai (Create Stack) và thu hồi toàn bộ hạ tầng (Delete Stack) chỉ với một thao tác qua CloudFormation <br> - Tắt GuardDuty và Security Hub sau khi hoàn tất đánh giá để tránh phát sinh phí sau thời gian dùng thử | 27/11/2026 | 27/11/2026 | https://000037.awsstudygroup.com/ |

### Kết quả đạt được trong tuần 11

* Hiểu rõ cách **Amazon GuardDuty** tự động phát hiện các hành vi xâm nhập, rò rỉ IAM Credentials hay kết nối tới IP độc hại mà không cần cài đặt agent lên máy chủ.
* Biết cách sử dụng **AWS Security Hub** để đo lường định lượng điểm số an toàn của tài khoản AWS theo chuẩn **CIS Benchmark** và trực tiếp xử lý các điểm yếu cấu hình nhằm nâng cao Security Score.
* Làm chủ kỹ năng viết và vận hành **AWS CloudFormation (IaC)**, giúp khởi tạo và dọn dẹp môi trường bài lab/dự án nhất quán, tránh sai sót thủ công và không bỏ sót tài nguyên gây tốn phí.
