---
title: "Worklog Tuần 8"
date: 2024-01-01
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu tuần 8

* Thiết kế và khởi tạo hệ thống bảng dữ liệu **Amazon DynamoDB** cho dự án **SecureTable** (quản lý bàn, hóa đơn, thực đơn, đơn gọi món, tồn kho nguyên liệu, tài chính và nhật ký thao tác Audit Logs).
* Phát triển và tích hợp các hàm **AWS Lambda** xử lý nghiệp vụ cốt lõi: `GuestServices`, `Ordering`, `Reception`, `Kitchen`, `Inventory` và `AdminDashboard`.
* Áp dụng **DynamoDB Transactions**, **Conditional Expressions** và khóa chống trùng lặp (**Idempotency-Key**) để đảm bảo tính nhất quán tồn kho khi nhiều khách đặt món cùng lúc.
* Thực hành bảo mật khóa mã hóa với **AWS KMS** và quản lý cấu hình an toàn qua biến môi trường được bảo vệ / **SSM Parameter Store**.

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|------|-----------|-------------|----------------|---------------|
| 2 | **Thiết kế & Khởi tạo các bảng Amazon DynamoDB:** <br> - Thiết kế Partition Key, Sort Key và Global Secondary Indexes (GSI) cho các bảng Bàn, Hóa đơn (Bills), Đơn hàng (Orders), Nguyên liệu (Ingredients), Tài chính và Audit Logs <br> - Khởi tạo bảng ở chế độ On-Demand / tối ưu dung lượng và bật mã hóa dữ liệu tĩnh (Encryption at Rest) | 02/11/2026 | 02/11/2026 | https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/best-practices.html |
| 3 | **Phát triển Lambda `GuestServices` & `Ordering`:** <br> - Xây dựng API xem thực đơn theo tình trạng nguyên liệu khả dụng (`GET /v1/guest/menu`) <br> - Phát triển `Ordering Lambda` sử dụng **DynamoDB `TransactWriteItems`** và `Idempotency-Key` để vừa tạo đơn món vừa đặt giữ (reserve) nguyên liệu nguyên tử (Atomic), chống âm kho khi đặt đồng thời | 03/11/2026 | 03/11/2026 | https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/transaction-apis.html |
| 4 | **Phát triển Lambda `Reception`, `Kitchen` & `Inventory`:** <br> - Xây dựng luồng Reception mở bàn, chuyển trạng thái `CLOSING` và chốt hóa đơn <br> - Xây dựng luồng Kitchen xác nhận hoàn tất món (trừ kho thực tế) hoặc từ chối món (hoàn trả lượng nguyên liệu đã đặt giữ) <br> - Xây dựng luồng Inventory nhập kho, điều chỉnh hao hụt và ghi nhận lịch sử | 04/11/2026 | 04/11/2026 | https://docs.aws.amazon.com/lambda/latest/dg/welcome.html |
| 5 | **Phát triển `AdminDashboard` & Ghi nhận Audit Logs:** <br> - Xây dựng hàm tổng hợp báo cáo doanh thu, chi phí nguyên liệu cho Admin <br> - Ghi nhận đầy đủ **Audit Logs nghiệp vụ** (ai thực hiện, thao tác gì, thời gian, giá trị trước/sau) vào bảng Audit trên DynamoDB cho các hành động nhạy cảm như sửa kho hay đóng/hủy món | 05/11/2026 | 05/11/2026 | https://000022.awsstudygroup.com/ |
| 6 | **Bảo mật dữ liệu & Cấu hình với AWS KMS / Parameter Store:** <br> - Nghiên cứu cơ chế mã hóa khóa với **AWS KMS** và lưu trữ cấu hình nhạy cảm trên **SSM Parameter Store (`SecureString`)** <br> - Rà soát toàn bộ mã nguồn dự án đảm bảo không tồn tại bất kỳ mật khẩu hay khóa bí mật nào bị hard-code | 06/11/2026 | 06/11/2026 | https://000020.awsstudygroup.com/ |

### Kết quả đạt được trong tuần 8

* Triển khai hoàn chỉnh tầng dữ liệu **Amazon DynamoDB** và các hàm **AWS Lambda** nghiệp vụ trung tâm của hệ thống **SecureTable**.
* Giải quyết triệt để bài toán xung đột dữ liệu (Race Condition) khi nhiều bàn gọi món cùng lúc nhờ **DynamoDB Transactions**, **Conditional Updates** và cơ chế **Idempotency**.
* Đảm bảo khả năng truy vết nghiệp vụ minh bạch (Traceability) thông qua bảng **Audit Logs** lưu lịch sử mọi thay đổi quan trọng của nhân viên.
* Tuân thủ nguyên tắc bảo vệ dữ liệu và cấu hình an toàn, không hard-code thông tin nhạy cảm trong repository.
