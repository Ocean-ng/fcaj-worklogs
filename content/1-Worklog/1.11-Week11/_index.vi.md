---
title: "Worklog Tuần 11"
date: 2024-01-01
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Mục tiêu tuần 11

* Rà soát toàn diện tư thế bảo mật đám mây (CSPM) và phát hiện mối đe dọa trên tài khoản AWS bằng **Amazon GuardDuty** và **AWS Security Hub**.
* Đối chiếu toàn bộ hệ thống **SecureTable** theo 5 trụ cột chấm điểm của **AWS Well-Architected Framework** (Operational Excellence, Security, Reliability, Performance Efficiency, Cost Optimization).
* Đóng gói cấu hình và tài liệu hướng dẫn triển khai Step-by-Step cho mục **Workshop**, đảm bảo tính tái lập (Reproducible) từ đầu đến cuối.

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|------|-----------|-------------|----------------|---------------|
| 2 | **Rà soát mối đe dọa với Amazon GuardDuty:** <br> - Tìm hiểu cách GuardDuty phân tích CloudTrail Events, VPC Flow Logs và DNS Logs để phát hiện hành vi xâm nhập <br> - Kiểm tra tài khoản triển khai dự án đảm bảo không có cảnh báo sử dụng IAM Credentials bất thường | 23/11/2026 | 23/11/2026 | https://docs.aws.amazon.com/guardduty/latest/ug/what-is-guardduty.html |
| 3 | **Đánh giá tuân thủ bảo mật với AWS Security Hub:** <br> - Đối chiếu cấu hình các dịch vụ trong tài khoản theo bộ chuẩn **AWS Foundational Security Best Practices** <br> - Xác minh toàn bộ S3 Buckets bật Block Public Access, Root Account bật MFA, IAM Roles không cấp quyền thừa (`*`) và không lộ thông tin xác thực | 24/11/2026 | 24/11/2026 | https://docs.aws.amazon.com/securityhub/latest/userguide/what-is-securityhub.html |
| 4 | **Rà soát kiến trúc SecureTable theo Well-Architected:** <br> - Kiểm tra sự đồng nhất 100% giữa sơ đồ kiến trúc `SecureTable_Architecture.svg` và môi trường triển khai thực tế trên AWS Region `ap-southeast-1` <br> - Rà soát cơ chế xử lý lỗi (Failure Handling), giao dịch DynamoDB Transactions và khả năng mở rộng tự động của Lambda/API Gateway | 25/11/2026 | 25/11/2026 | https://docs.aws.amazon.com/wellarchitected/latest/serverless-applications-lens/welcome.html |
| 5 | **Biên soạn tài liệu hướng dẫn thực hành Workshop:** <br> - Viết tài liệu hướng dẫn triển khai từng bước (Prerequisites, Frontend S3/CloudFront, DynamoDB, Cognito/IAM, Lambda/API Gateway, Automation, Security & Cleanup) kèm code snippets và ảnh chụp màn hình rõ nét | 26/11/2026 | 26/11/2026 | https://github.com/thienluhoan/fcj-workshop-template |
| 6 | **Nghiên cứu bảo mật AI hiện đại với Amazon Bedrock Guardrails:** <br> - Tìm hiểu xu hướng bảo vệ ứng dụng Generative AI bằng **Amazon Bedrock Guardrails** (chống Prompt Injection, lọc PII) và viết bài Blog kỹ thuật bổ sung cho cộng đồng | 27/11/2026 | 27/11/2026 | https://docs.aws.amazon.com/bedrock/latest/userguide/guardrails.html |

### Kết quả đạt được trong tuần 11

* Xác nhận tài khoản AWS và hệ thống **SecureTable** đáp ứng tốt các tiêu chuẩn an toàn cốt lõi trên **AWS Security Hub** và không phát sinh cảnh báo rủi ro trên **GuardDuty**.
* Đảm bảo sản phẩm triển khai thực tế khớp hoàn toàn với sơ đồ kiến trúc đã thiết kế và thỏa mãn cả 5 trụ cột đánh giá của **AWS Well-Architected Framework**.
* Chuẩn hóa tài liệu hướng dẫn thực hành Step-by-Step song ngữ và mở rộng kiến thức sang mảng bảo mật Generative AI với **Amazon Bedrock Guardrails**.
