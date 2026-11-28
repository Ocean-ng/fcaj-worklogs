---
title: "Worklog Tuần 7"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu tuần 7

* Phát triển hoàn chỉnh giao diện phía khách hàng (**Guest Portal**) cho dự án **SecureTable**: trang giới thiệu không gian quán, thực đơn trực quan phân loại 4 nhóm món và giỏ gọi món qua mã QR tại bàn.
* Xây dựng luồng khởi tạo và lưu giữ **Guest Session Token** trên trình duyệt khi bàn đang mở hóa đơn (`OPEN`), không bắt khách hàng phải tạo tài khoản đăng nhập.
* Tích hợp giao diện đăng nhập nhân viên với **Amazon Cognito User Pool** (xử lý đăng nhập, hỗ trợ xác thực MFA và giải mã nhóm quyền từ JWT Token).

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|------|-----------|-------------|----------------|---------------|
| 2 | **Xây dựng Trang chủ & Thực đơn phân loại cho Guest:** <br> - Thiết kế giao diện trang chủ hiển thị không gian nhà hàng và các món đặc trưng <br> - Xây dựng trang Thực đơn (`#/menu`) phân loại rõ 4 nhóm (Khai vị, Món chính, Đồ uống, Tráng miệng) kèm hình ảnh, giá bán và trạng thái còn/hết nguyên liệu | 26/10/2026 | 26/10/2026 | https://aws.amazon.com/serverless/ |
| 3 | **Phát triển Giỏ gọi món QR & Luồng Guest Session:** <br> - Xây dựng giao diện chọn số lượng món, ghi chú yêu cầu và kết nối luồng `POST /v1/guest/sessions` khi khách quét mã QR bàn <br> - Xử lý hiển thị thông báo rõ ràng nếu bàn chưa được Lễ tân mở hóa đơn hoặc hóa đơn đã đóng | 27/10/2026 | 27/10/2026 | https://000022.awsstudygroup.com/ |
| 4 | **Tìm hiểu luồng xác thực Amazon Cognito cho SPA:** <br> - Đọc tài liệu về **Amazon Cognito User Pools**, cơ chế xác thực người dùng trên ứng dụng Web Single-Page Application (App Client không dùng client secret) và cấu trúc chuỗi JWT (`id_token`, `access_token`) | 28/10/2026 | 28/10/2026 | https://docs.aws.amazon.com/cognito/latest/developerguide/cognito-user-identity-pools.html |
| 5 | **Xây dựng màn hình Đăng nhập Staff & Đọc nhóm quyền JWT:** <br> - Code giao diện đăng nhập `#/staff` kết nối với Cognito User Pool của nhóm, hỗ trợ bước nhập mã MFA khi tài khoản quản lý được yêu cầu <br> - Trích xuất thông tin nhóm quyền (`cognito:groups`) để tự động điều hướng nhân viên vào đúng màn hình nghiệp vụ được cấp phép | 29/10/2026 | 29/10/2026 | https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-integrate-with-cognito.html |
| 6 | **Kiểm thử luồng đăng nhập & Phân tách phiên Guest/Staff:** <br> - Kiểm thử tách biệt lưu trữ token của Staff và Guest Session Token trên trình duyệt <br> - Xử lý tự động đăng xuất và làm sạch phiên khi JWT hết hạn hoặc trả về mã `401 Unauthorized` | 30/10/2026 | 30/10/2026 | https://docs.aws.amazon.com/IAM/latest/UserGuide/security-creds.html |

### Kết quả đạt được trong tuần 7

* Hoàn thiện trải nghiệm xem thực đơn và đặt món bằng mã QR mượt mà, dễ sử dụng cho khách hàng mà không cần tạo tài khoản.
* Tích hợp thành công màn hình đăng nhập nhân viên với **Amazon Cognito**, tự động phân luồng giao diện dựa trên nhóm quyền của từng bộ phận.
* Nắm vững cách ứng dụng Frontend làm việc an toàn với thông tin xác thực ngắn hạn (JWT Token & Guest Session Token) khi giao tiếp với Amazon API Gateway.
