---
title: "Worklog Tuần 9"
date: 2024-01-01
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Mục tiêu tuần 9

* Xây dựng tầng kết nối API tập trung (`apiClient.js`) trên Frontend của **SecureTable** để giao tiếp với **Amazon API Gateway** theo đúng hợp đồng phân quyền của nhóm.
* Xử lý đính kèm khóa chống gửi trùng (**Idempotency-Key**) khi đặt món và xử lý mã phản hồi `401 / 403 / 304` mượt mà trên giao diện.
* Tìm hiểu luồng tự động hóa báo cáo và sao lưu dữ liệu (`EventBridge Scheduler + SNS + DynamoDB Export to S3`) trong kiến trúc chung của nhóm và tham dự sự kiện **AWS Cloud Mastery**.

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|------|-----------|-------------|----------------|---------------|
| 2 | **Xây dựng module `apiClient.js` kết nối API Gateway:** <br> - Viết hàm gọi API dùng chung tự động đính kèm Bearer JWT Token (cho Staff) hoặc Guest Session Token (cho khách tại bàn) vào HTTP Header | 09/11/2026 | 09/11/2026 | https://docs.aws.amazon.com/apigateway/latest/developerguide/welcome.html |
| 3 | **Tích hợp `Idempotency-Key` & Tối ưu tải màn hình Bếp:** <br> - Sinh mã `Idempotency-Key` duy nhất cho mỗi lượt bấm gửi đơn món để tránh tạo đơn trùng khi mạng chập chờn <br> - Hỗ trợ kiểm tra `ETag` (`304 Not Modified`) cho màn hình hàng đợi Bếp để giảm dung lượng dữ liệu tải lại | 10/11/2026 | 10/11/2026 | https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/transaction-apis.html |
| 4 | **Đồng bộ ma trận quyền RBAC giữa Frontend và Backend:** <br> - Rà soát từng nút chức năng trên UI khớp với bộ phân quyền Backend (`ADMIN`, `RECEPTION`, `KITCHEN`, `INVENTORY`) <br> - Xử lý bắt lỗi `403 Forbidden` và hiển thị thông báo thân thiện khi tài khoản thao tác vượt quá quyền được cấp | 11/11/2026 | 11/11/2026 | https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html |
| 5 | **Tìm hiểu luồng Automation Báo cáo & Backup của dự án:** <br> - Đọc tài liệu về **Amazon EventBridge Scheduler**, **Amazon SNS** và **DynamoDB PITR / Export to S3** để nắm rõ cách hệ thống tự động gửi email báo cáo cho Admin và sao lưu dữ liệu hàng tuần | 12/11/2026 | 12/11/2026 | https://docs.aws.amazon.com/scheduler/latest/UserGuide/what-is-scheduler.html |
| 6 | **Kiểm thử luồng gọi API & Tham dự AWS Cloud Mastery (14/11):** <br> - Kiểm thử các trạng thái tải dữ liệu (Loading, Empty State, Error) trên toàn bộ màn hình Frontend <br> - Tham dự buổi chia sẻ trực tiếp **AWS Cloud Mastery** (Sáng Thứ Bảy 14/11/2026 tại Tầng 26 Bitexco) cùng nhóm | 13/11/2026 | 14/11/2026 | https://000022.awsstudygroup.com/ |

### Kết quả đạt được trong tuần 9

* Hoàn thành tầng giao tiếp API chuẩn hóa trên Frontend, đảm bảo mọi yêu cầu gửi lên **Amazon API Gateway** đều mang đúng thông tin xác thực và chống trùng lặp đơn hàng.
* Hiểu rõ bức tranh tổng thể của toàn bộ dự án **SecureTable** (cả phần luồng gọi món trực tuyến lẫn luồng tự động hóa ngầm phía sau).
* Học hỏi thêm nhiều kinh nghiệm rà soát kiến trúc và chuẩn bị dự án thực tế qua buổi giao lưu **AWS Cloud Mastery** tại văn phòng AWS Việt Nam.
