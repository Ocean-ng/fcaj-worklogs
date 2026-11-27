---
title: "Các bài blogs đã đăng"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

> Phần này tổng hợp các bài Blog kỹ thuật và nhật ký nghiên cứu chuyên sâu về **Bảo mật đám mây AWS (Cloud Security)**, **Kiến trúc Serverless** và **An toàn cho ứng dụng Generative AI** mà mình đã tự nghiên cứu từ tài liệu chính thức của AWS và chia sẻ trên cộng đồng [AWS Study Group VN](https://www.facebook.com/groups/660548818043427/user/100016726392723).

### [Blog 1 - Tìm hiểu mô hình trách nhiệm chung và bảo mật dữ liệu Amazon S3](3.1-Blog1/)
Tổng hợp quá trình nghiên cứu về **AWS Shared Responsibility Model** đối với Amazon EC2 và Amazon S3, đi sâu vào các cơ chế bảo vệ dữ liệu trên S3 gồm **Block Public Access**, mã hóa mặc định **SSE-S3** và quản lý phiên bản với **S3 Versioning** kèm bài toán cân đối chi phí lưu trữ.

### [Blog 2 - AWS Shared Responsibility Model (Mô hình trách nhiệm chung trên AWS)](3.2-Blog2/)
Phân tích ranh giới trách nhiệm bảo mật giữa AWS (**“Security of the Cloud”**) và khách hàng (**“Security in the Cloud”**), làm rõ sự thay đổi trách nhiệm theo từng loại dịch vụ (IaaS như EC2 so với dịch vụ được quản lý như S3) cùng Checklist rà soát khi thiết kế hệ thống.

### [Blog 3 - AWS Security: Bắt đầu từ danh tính và quyền truy cập (IAM & CloudTrail)](3.3-Blog3/)
Hệ thống hóa 4 nguyên tắc cốt lõi bảo vệ danh tính và quyền truy cập theo **AWS Well-Architected Security Pillar**: Bảo vệ Root User bằng MFA, sử dụng thông tin xác thực tạm thời (IAM Role / Federation), áp dụng **Least Privilege** theo prefix trên S3 và theo dõi hoạt động qua **AWS CloudTrail**.

### [Blog 4 - Bảo vệ Origin phía sau Amazon CloudFront bằng AWS WAF, OAC và Custom Header xoay vòng tự động](3.4-Blog4/)
Phân tích cách ngăn chặn triệt để hành vi đi vòng qua CDN (Origin Bypass) để tấn công trực tiếp vào tầng ứng dụng: sử dụng **Origin Access Control (OAC)** cho S3 Origin và kết hợp **AWS WAF + Custom Header (`X-Origin-Verify`) xoay vòng tự động bằng AWS Secrets Manager & Lambda** cho ALB/API Origin.

### [Blog 5 - Tự động hóa tác vụ theo thời gian quy mô lớn với Amazon EventBridge Scheduler, AWS Lambda và DynamoDB](3.5-Blog5/)
Chia sẻ kiến trúc lập lịch Serverless hiện đại thay thế cho máy chủ Cron truyền thống bằng **Amazon EventBridge Scheduler**: hỗ trợ lịch định kỳ (Recurring) và lịch chạy một lần (One-time) theo múi giờ địa phương, tích hợp Retry Policy/DLQ và ứng dụng thực tế vào luồng tự động hóa báo cáo, sao lưu dữ liệu.

### [Blog 6 - Bắt buộc kiểm soát an toàn cho ứng dụng Generative AI với Amazon Bedrock Guardrails và IAM Condition Key](3.6-Blog6/)
Tìm hiểu xu hướng bảo mật ứng dụng AI tạo sinh hiện nay trên AWS: sử dụng **Amazon Bedrock Guardrails** để chặn tấn công **Prompt Injection** và ẩn thông tin định danh cá nhân (**PII**), đồng thời dùng điều kiện **`bedrock:GuardrailIdentifier`** trong IAM Policy để bắt buộc mọi lệnh gọi mô hình đều phải đi qua lớp kiểm duyệt an toàn.
