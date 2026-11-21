---
title: "Worklog Tuần 7"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu tuần 7

* Tìm hiểu kiến trúc điện toán phi máy chủ (Serverless Computing) trên AWS với **AWS Lambda** và **Amazon API Gateway**.
* Thực hành viết hàm AWS Lambda (Python/Node.js), cấu hình Execution Role theo nguyên tắc Least Privilege, Environment Variables và kiểm thử sự kiện.
* Thiết lập RESTful API và HTTP API với Amazon API Gateway, cấu hình CORS, Throttling và tích hợp Lambda Proxy Integration.
* Triển khai hệ thống xác thực và phân quyền người dùng chuẩn OAuth 2.0 / OIDC với **Amazon Cognito User Pools** và gắn Cognito Authorizer bảo vệ API Gateway.

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|------|-----------|-------------|----------------|---------------|
| 2 | **Nền tảng AWS Lambda:** <br> - Tìm hiểu mô hình thực thi hướng sự kiện (Event-driven), vòng đời container (Cold Start vs Warm Start) và giới hạn tài nguyên của AWS Lambda <br> - Tạo Lambda Execution Role chỉ cấp quyền ghi log CloudWatch và đọc/ghi vào S3 Bucket chỉ định <br> - Viết và kiểm thử hàm Lambda xử lý dữ liệu JSON từ sự kiện S3/API | 26/10/2026 | 26/10/2026 | https://000022.awsstudygroup.com/ |
| 3 | **Xây dựng API với Amazon API Gateway:** <br> - Tìm hiểu các loại API trên API Gateway (REST API, HTTP API, WebSocket API) <br> - Thiết kế các tài nguyên và phương thức (`GET`, `POST`), kết nối với hàm Lambda qua cơ chế Lambda Proxy Integration <br> - Cấu hình CORS và triển khai API lên môi trường Stage (`dev`) | 27/10/2026 | 27/10/2026 | https://000022.awsstudygroup.com/ |
| 4 | **Quản lý định danh người dùng với Amazon Cognito:** <br> - Tìm hiểu sự khác biệt giữa Cognito User Pools (Authentication) và Identity Pools (Authorization cấp AWS Credentials tạm thời) <br> - Khởi tạo Cognito User Pool, cấu hình chính sách mật khẩu mạnh, xác thực email OTP và tạo App Client | 28/10/2026 | 28/10/2026 | https://docs.aws.amazon.com/cognito/ |
| 5 | **Bảo mật API Gateway bằng Cognito Authorizer:** <br> - Cấu hình Cognito User Pool Authorizer trên Amazon API Gateway <br> - Thực hành đăng nhập lấy chuỗi JWT (`id_token` / `access_token`) từ Cognito Hosted UI <br> - Kiểm thử gọi API qua Postman: xác nhận trả về `401 Unauthorized` khi thiếu token và `200 OK` khi đính kèm Bearer JWT hợp lệ | 29/10/2026 | 29/10/2026 | https://docs.aws.amazon.com/apigateway/ |
| 6 | **Giới hạn tần suất (Rate Limiting) & Kiểm thử:** <br> - Thiết lập Usage Plan, API Key và giới hạn Throttling (Rate Limit / Burst Limit) trên API Gateway để chống tấn công làm cạn kiệt tài nguyên <br> - Kiểm tra CloudWatch Logs của Lambda và dọn dẹp các endpoint thử nghiệm | 30/10/2026 | 30/10/2026 | https://000022.awsstudygroup.com/ |

### Kết quả đạt được trong tuần 7

* Xây dựng thành công luồng Backend Serverless hoàn chỉnh kết hợp **Amazon API Gateway** và **AWS Lambda** mà không cần quản trị máy chủ vật lý hay EC2.
* Hiểu rõ cơ chế phân quyền cho hàm Lambda thông qua IAM Execution Role và cách xử lý lỗi, theo dõi log thực thi trên CloudWatch.
* Tích hợp thành công hệ thống xác thực tập trung **Amazon Cognito User Pools**, bảo vệ các API nhạy cảm bằng **JWT / Cognito Authorizer**.
* Áp dụng các biện pháp bảo vệ API thiết yếu như cấu hình CORS chuẩn xác và giới hạn lưu lượng truy cập (Throttling) để ngăn ngừa lạm dụng API và giảm thiểu chi phí đột biến.
