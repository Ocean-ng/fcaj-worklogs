---
title: "Worklog Tuần 11"
date: 2024-01-01
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Mục tiêu tuần 11

* Nghiên cứu các dịch vụ phát hiện mối đe dọa và quản trị tư thế bảo mật đám mây (**Amazon GuardDuty**, **AWS Security Hub**) và đánh giá bài toán tối ưu chi phí bảo mật cho kiến trúc Serverless.
* Rà soát thủ công cấu hình an toàn tài khoản AWS theo chuẩn **CIS AWS Foundations / Foundational Security Best Practices** và đối chiếu dự án **SecureTable** với 5 trụ cột **AWS Well-Architected Framework**.
* Biên soạn tài liệu hướng dẫn triển khai Step-by-Step cho mục **Workshop**, đảm bảo tính tái lập (Reproducible) từ đầu đến cuối.

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|------|-----------|-------------|----------------|---------------|
| 2 | **Nghiên cứu Amazon GuardDuty & Đánh giá chi phí cho Serverless:** <br> - Tìm hiểu cơ chế phân tích CloudTrail, VPC Flow Logs và DNS Logs của GuardDuty <br> - Phân tích bài toán chi phí - hiệu quả: vì SecureTable là 100% Serverless (không dùng VPC/EC2) và ngân sách dưới $10/tháng nên không bật GuardDuty trả phí mà tập trung bảo vệ bằng Cognito, IAM Least Privilege, WAF và Audit Logs | 23/11/2026 | 23/11/2026 | https://docs.aws.amazon.com/guardduty/latest/ug/what-is-guardduty.html |
| 3 | **Rà soát cấu hình an toàn theo chuẩn AWS Security Best Practices:** <br> - Nghiên cứu bộ tiêu chí của **AWS Security Hub / CIS Benchmark** và tự kiểm tra trực tiếp trên tài khoản dự án <br> - Xác minh toàn bộ S3 Buckets bật Block Public Access, Root Account bật MFA, IAM Roles không cấp quyền thừa (`*`) và không lộ thông tin xác thực trong Git | 24/11/2026 | 24/11/2026 | https://docs.aws.amazon.com/securityhub/latest/userguide/fsbp-standard.html |
| 4 | **Rà soát kiến trúc SecureTable theo Well-Architected:** <br> - Kiểm tra sự đồng nhất 100% giữa sơ đồ kiến trúc `SecureTable_Architecture.svg` và môi trường triển khai thực tế trên AWS Region `ap-southeast-1` <br> - Rà soát cơ chế xử lý lỗi (Failure Handling), giao dịch DynamoDB Transactions và khả năng mở rộng tự động của Lambda/API Gateway | 25/11/2026 | 25/11/2026 | https://docs.aws.amazon.com/wellarchitected/latest/serverless-applications-lens/welcome.html |
| 5 | **Biên soạn tài liệu hướng dẫn thực hành Workshop:** <br> - Viết tài liệu hướng dẫn triển khai từng bước (Prerequisites, Frontend S3/CloudFront, DynamoDB, Cognito/IAM, Lambda/API Gateway, Automation, Security & Cleanup) kèm code snippets và ảnh chụp màn hình rõ nét | 26/11/2026 | 26/11/2026 | https://github.com/thienluhoan/fcj-workshop-template |
| 6 | **Nghiên cứu bảo mật AI hiện đại với Amazon Bedrock Guardrails:** <br> - Tìm hiểu xu hướng bảo vệ ứng dụng Generative AI bằng **Amazon Bedrock Guardrails** (chống Prompt Injection, lọc dữ liệu nhạy cảm PII) để mở rộng kiến thức chuyên ngành An toàn thông tin | 27/11/2026 | 27/11/2026 | https://docs.aws.amazon.com/bedrock/latest/userguide/guardrails.html |

### Kết quả đạt được trong tuần 11

* Nắm vững cơ chế hoạt động của **Amazon GuardDuty** và **AWS Security Hub**, đồng thời đưa ra quyết định kiến trúc hợp lý về mặt chi phí - bảo mật cho dự án Serverless quy mô nhỏ (rà soát cấu hình chuẩn CIS kết hợp bảo vệ tầng ứng dụng mà không phát sinh phí dịch vụ dư thừa).
* Đảm bảo sản phẩm triển khai thực tế khớp hoàn toàn với sơ đồ kiến trúc đã thiết kế và thỏa mãn cả 5 trụ cột đánh giá của **AWS Well-Architected Framework**.
* Chuẩn hóa tài liệu hướng dẫn thực hành Step-by-Step song ngữ và mở rộng kiến thức sang mảng bảo mật Generative AI với **Amazon Bedrock Guardrails**.
