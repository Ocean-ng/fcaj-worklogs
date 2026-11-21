---
title: "Worklog Tuần 8"
date: 2024-01-01
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu tuần 8

* Nắm vững cơ chế mã hóa dữ liệu và quản lý khóa mật mã trên AWS với **AWS Key Management Service (AWS KMS)**.
* Phân biệt rõ giữa AWS Managed Keys và Customer Managed Keys (CMK), hiểu cơ chế Envelope Encryption và tự động xoay vòng khóa (Key Rotation).
* Thực hành loại bỏ hoàn toàn việc lưu cứng mật khẩu/API Key trong mã nguồn (Hardcoded Secrets) bằng cách sử dụng **AWS Systems Manager Parameter Store** và **AWS Secrets Manager**.
* Tích hợp ứng dụng/Lambda truy xuất thông tin cấu hình và chuỗi kết nối Database an toàn trong thời gian chạy (Runtime).

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|------|-----------|-------------|----------------|---------------|
| 2 | **Quản lý khóa mã hóa với AWS KMS:** <br> - Tìm hiểu kiến trúc AWS KMS, cơ chế Envelope Encryption (Data Key & KMS Master Key) <br> - Khởi tạo Customer Managed Key (Symmetric CMK), cấu hình Key Policy phân tách quyền Key Administrator và Key User <br> - Bật tính năng tự động xoay vòng khóa định kỳ (Automatic Key Rotation) | 02/11/2026 | 02/11/2026 | https://000020.awsstudygroup.com/ |
| 3 | **Mã hóa dữ liệu đa dịch vụ với KMS:** <br> - Thực hành cấu hình mã hóa S3 Bucket bằng SSE-KMS với Customer Managed Key <br> - Kiểm thử kịch bản một IAM User có quyền đọc S3 (`s3:GetObject`) nhưng không có quyền giải mã KMS (`kms:Decrypt`) sẽ bị từ chối truy cập dữ liệu <br> - Thực hành mã hóa và giải mã tệp tin qua AWS CLI (`aws kms encrypt`, `aws kms decrypt`) | 03/11/2026 | 03/11/2026 | https://000020.awsstudygroup.com/ |
| 4 | **Quản lý cấu hình với SSM Parameter Store:** <br> - Tìm hiểu các kiểu tham số trên Systems Manager Parameter Store (`String`, `StringList`, `SecureString`) <br> - Lưu trữ các biến cấu hình hệ thống theo cấu trúc phân cấp (`/app/prod/db-host`, `/app/prod/api-key`) được mã hóa bằng KMS Key | 04/11/2026 | 04/11/2026 | https://docs.aws.amazon.com/systems-manager/ |
| 5 | **Bảo mật thông tin nhạy cảm với AWS Secrets Manager:** <br> - So sánh trường hợp sử dụng giữa SSM Parameter Store và AWS Secrets Manager <br> - Lưu trữ thông tin đăng nhập Database trên AWS Secrets Manager và tìm hiểu cơ chế tự động đổi mật khẩu định kỳ (Automatic Secret Rotation) | 05/11/2026 | 05/11/2026 | https://docs.aws.amazon.com/secretsmanager/ |
| 6 | **Tích hợp truy xuất Secrets từ AWS Lambda:** <br> - Cấp quyền IAM tối thiểu (`ssm:GetParameter`, `secretsmanager:GetSecretValue`, `kms:Decrypt`) cho Lambda Execution Role <br> - Viết code sử dụng AWS SDK (`boto3`) để đọc và giải mã tham số `SecureString` trong bộ nhớ đệm, sau đó dọn dẹp KMS key/Secret thử nghiệm | 06/11/2026 | 06/11/2026 | https://000020.awsstudygroup.com/ |

### Kết quả đạt được trong tuần 8

* Hiểu sâu cơ chế bảo vệ dữ liệu tĩnh (Encryption at Rest) trên AWS thông qua **AWS KMS** và mô hình **Envelope Encryption**.
* Thiết lập thành công lớp bảo vệ kép cho dữ liệu nhạy cảm trên S3 và EBS: yêu cầu đồng thời cả quyền truy cập tài nguyên (IAM/Bucket Policy) lẫn quyền sử dụng khóa giải mã (`kms:Decrypt`) trên KMS Key Policy.
* Loại bỏ triệt để lỗ hổng lộ thông tin xác thực trong mã nguồn bằng cách chuyển toàn bộ cấu hình và mật khẩu sang **SSM Parameter Store (`SecureString`)** và **AWS Secrets Manager**.
* Nắm vững tiêu chí lựa chọn giữa Parameter Store (miễn phí cho Standard Parameters, phù hợp cấu hình ứng dụng) và Secrets Manager (hỗ trợ xoay vòng mật khẩu RDS tự động).
