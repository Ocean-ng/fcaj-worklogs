---
title: "Các bài blogs đã đăng"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

> Phần này tổng hợp **3 bài viết chia sẻ kiến thức và nhật ký nghiên cứu** về **Bảo mật đám mây AWS (AWS Cloud Security)** mà mình đã tự nghiên cứu từ tài liệu chính thức của AWS và đăng tải trên cộng đồng [AWS Study Group VN](https://www.facebook.com/groups/660548818043427/user/100016726392723).

### [Blog 1 - Tìm hiểu mô hình trách nhiệm chung và bảo mật dữ liệu Amazon S3](3.1-Blog1/)
Tổng hợp quá trình nghiên cứu về **AWS Shared Responsibility Model** đối với Amazon EC2 và Amazon S3, đi sâu vào các cơ chế bảo vệ dữ liệu trên S3 gồm **Block Public Access**, mã hóa mặc định **SSE-S3** và quản lý phiên bản với **S3 Versioning** kèm bài toán cân đối chi phí lưu trữ.

### [Blog 2 - AWS Shared Responsibility Model (Mô hình trách nhiệm chung trên AWS)](3.2-Blog2/)
Phân tích ranh giới trách nhiệm bảo mật giữa AWS (**“Security of the Cloud”**) và khách hàng (**“Security in the Cloud”**), làm rõ sự thay đổi trách nhiệm theo từng loại dịch vụ (IaaS như EC2 so với dịch vụ được quản lý như S3) cùng Checklist rà soát khi thiết kế hệ thống.

### [Blog 3 - AWS Security: Bắt đầu từ danh tính và quyền truy cập (IAM & CloudTrail)](3.3-Blog3/)
Hệ thống hóa 4 nguyên tắc cốt lõi bảo vệ danh tính và quyền truy cập theo **AWS Well-Architected Security Pillar**: Bảo vệ Root User bằng MFA, sử dụng thông tin xác thực tạm thời (IAM Role / Federation), áp dụng **Least Privilege** theo prefix trên S3 và theo dõi hoạt động qua **AWS CloudTrail**.
