---
title: "Các bài blogs đã đăng"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

> Phần này tổng hợp các bài viết chuyên đề và bài dịch kỹ thuật về bảo mật hạ tầng đám mây (Cloud Security), kiến trúc mạng khép kín và quản lý định danh trên AWS được biên soạn trong quá trình thực tập tại chương trình **AWS First Cloud AI Journey (FCAJ)**.

### [Blog 1 - Kiểm soát đặc quyền tối thiểu trong Kubernetes với Session Policies trên Amazon EKS Pod Identity](3.1-Blog1/)
Bài viết phân tích chuyên sâu tính năng **Session Policies** trong **Amazon EKS Pod Identity**, cho phép thu hẹp quyền IAM linh hoạt cho từng Pod/ServiceAccount dựa trên cơ chế phép giao quyền hạn (Permission Intersection) mà không cần nhân bản hàng trăm IAM Roles riêng lẻ trong cụm Kubernetes quy mô lớn.

### [Blog 2 - Thiết kế kiến trúc mạng khép kín (Zero-Internet Exposure) với AWS PrivateLink và VPC Endpoints](3.2-Blog2/)
Bài viết trình bày phương pháp loại bỏ hoàn toàn lưu lượng đi qua Internet công cộng khi kết nối từ Private Subnet hoặc trung tâm dữ liệu On-premises tới Amazon S3 và các dịch vụ AWS. Nội dung đi sâu vào so sánh Gateway Endpoint và Interface Endpoint, cơ chế Hybrid DNS với Route 53 Resolver và cách dựng vành đai dữ liệu (Data Perimeter) bằng VPC Endpoint Policy.

### [Blog 3 - Tự động hóa phát hiện mối đe dọa và phản ứng sự cố an ninh trên AWS với GuardDuty, Security Hub và EventBridge](3.3-Blog3/)
Bài viết chia sẻ kiến trúc giám sát và vận hành an ninh tự động (SecOps) trên AWS: kết hợp Amazon GuardDuty để phát hiện hành vi xâm nhập bằng Machine Learning, chuẩn hóa điểm số tuân thủ CIS Benchmark qua AWS Security Hub và tự động cô lập tài nguyên/cảnh báo tức thời qua Amazon EventBridge và AWS Lambda.
