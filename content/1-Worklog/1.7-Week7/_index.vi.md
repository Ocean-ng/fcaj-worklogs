---
title: "Worklog Tuần 7"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu tuần 7

* Xây dựng hệ thống xác thực và phân quyền nhân viên cho **SecureTable** bằng **Amazon Cognito User Pool** (các nhóm quyền `Reception`, `Kitchen`, `Inventory`, `Admin`).
* Thiết kế cơ chế xác thực phiên tạm thời (**Guest Session Token**) không cần tài khoản Cognito cho khách quét mã QR tại bàn, ràng buộc chặt với trạng thái hóa đơn đang mở (`OPEN`).
* Thiết lập **Amazon API Gateway (REST API)** kết hợp **Cognito Authorizer** bảo vệ các đường dẫn nội bộ của nhân viên và phân tách rõ với nhóm API công khai của Guest.
* Thiết kế **AWS IAM Execution Roles** tuân thủ nguyên tắc **Least Privilege** cho từng hàm AWS Lambda.

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|------|-----------|-------------|----------------|---------------|
| 2 | **Khởi tạo Amazon Cognito User Pool cho Staff:** <br> - Tạo Cognito User Pool tại `ap-southeast-1`, cấu hình chính sách độ mạnh mật khẩu và xác thực email <br> - Tạo các Cognito User Groups tương ứng với 4 vai trò nhân viên: `Reception`, `Kitchen`, `Inventory`, `Admin` và cấu hình App Client | 26/10/2026 | 26/10/2026 | https://docs.aws.amazon.com/cognito/latest/developerguide/cognito-user-identity-pools.html |
| 3 | **Thiết kế AWS IAM Execution Roles theo Least Privilege:** <br> - Phân tách IAM Role riêng cho từng nhóm hàm Lambda thay vì dùng chung một Role quyền rộng (`*`) <br> - Giới hạn từng IAM Policy theo đúng hành động (`dynamodb:GetItem`, `dynamodb:PutItem`, `dynamodb:TransactWriteItems`) và đúng ARN bảng DynamoDB cần thiết | 27/10/2026 | 27/10/2026 | https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html |
| 4 | **Cấu hình Amazon API Gateway & Cognito Authorizer:** <br> - Thiết kế cấu trúc REST API (`/v1/guest/*` và `/v1/staff/*`) trên Amazon API Gateway <br> - Tích hợp **Cognito User Pool Authorizer** bắt buộc kiểm tra JWT Token hợp lệ trên toàn bộ nhánh `/v1/staff/*` và kiểm tra thêm nhóm quyền (RBAC) bên trong Lambda | 28/10/2026 | 28/10/2026 | https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-integrate-with-cognito.html |
| 5 | **Xây dựng cơ chế bảo mật Guest Session Token:** <br> - Thiết kế luồng `POST /v1/guest/sessions`: chỉ cấp Guest Session Token khi bàn đang ở trạng thái `OCCUPIED` và có hóa đơn `OPEN` tương ứng trong DynamoDB <br> - Đảm bảo khi Reception đóng hóa đơn, phiên Guest lập tức hết hiệu lực để hạn chế rủi ro đặt món trái phép từ mã QR tĩnh | 29/10/2026 | 29/10/2026 | https://000022.awsstudygroup.com/ |
| 6 | **Cấu hình CORS, Throttling & Kiểm thử phân quyền:** <br> - Cấu hình CORS chỉ cho phép domain CloudFront của SecureTable và thiết lập giới hạn Rate Limit / Burst Limit trên Stage của API Gateway <br> - Kiểm thử bằng Postman các trường hợp không có token (`401`), sai nhóm quyền nhân viên (`403`) và phiên Guest đã đóng bill | 30/10/2026 | 30/10/2026 | https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-request-throttling.html |

### Kết quả đạt được trong tuần 7

* Hoàn thiện cơ chế xác thực và phân quyền hai tầng cho **SecureTable**: dùng **Amazon Cognito JWT + RBAC** cho nhân viên và **Guest Session gắn theo hóa đơn mở** cho thực khách tại bàn.
* Áp dụng nghiêm ngặt nguyên tắc **Least Privilege** trên tất cả **IAM Execution Roles**, sử dụng thông tin xác thực tạm thời của Role và tuyệt đối không nhúng Access Key tĩnh vào code.
* Bảo vệ tầng giao tiếp **Amazon API Gateway** bằng Cognito Authorizer, cấu hình CORS chặt chẽ và giới hạn tần suất gọi API (Throttling).
