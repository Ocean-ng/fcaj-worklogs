---
title: "Các bài blogs đã đăng"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

> Phần này tổng hợp các bài viết chia sẻ kiến thức và nhật ký nghiên cứu về **Bảo mật đám mây AWS (AWS Cloud Security)** mà mình đã đăng tải trên cộng đồng [AWS Study Group VN](https://www.facebook.com/groups/660548818043427/user/100016726392723) trong quá trình thực tập chương trình **First Cloud AI Journey**.

### [Blog 1 - Tìm hiểu mô hình trách nhiệm chung và bảo mật dữ liệu Amazon S3](3.1-Blog1/)
Bài viết tổng hợp quá trình nghiên cứu về **AWS Shared Responsibility Model** đối với Amazon EC2 và Amazon S3, đi sâu vào các cơ chế bảo vệ dữ liệu trên S3 bao gồm **S3 Block Public Access**, mã hóa mặc định **SSE-S3** và quản lý phiên bản với **S3 Versioning** kèm những lưu ý về kiểm soát chi phí lưu trữ.

### [Blog 2 - AWS Shared Responsibility Model (Mô hình trách nhiệm chung trên AWS)](3.2-Blog2/)
Bài viết phân tích ranh giới trách nhiệm bảo mật giữa AWS (**"Security of the Cloud"**) và khách hàng (**"Security in the Cloud"**), làm rõ sự thay đổi trách nhiệm theo từng loại dịch vụ (từ hạ tầng IaaS như Amazon EC2 đến dịch vụ Managed như Amazon S3) và cung cấp Checklist thực tế khi thiết kế hệ thống trên AWS.

### [Blog 3 - AWS Security: Bắt đầu từ danh tính và quyền truy cập (IAM & CloudTrail)](3.3-Blog3/)
Bài viết hệ thống hóa 4 nguyên tắc cốt lõi để bảo vệ danh tính và quyền truy cập theo **AWS Well-Architected Security Pillar**: Bảo vệ Root User bằng MFA, sử dụng liên kết danh tính (Federation) và thông tin xác thực tạm thời (IAM Role), áp dụng nguyên tắc đặc quyền tối thiểu (**Least Privilege**) trên tài nguyên S3, và giám sát hoạt động tài khoản với **AWS CloudTrail**.
