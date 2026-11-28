---
title: "Worklog Tuần 8"
date: 2024-01-01
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu tuần 8

* Xây dựng đầy đủ các màn hình nghiệp vụ nội bộ cho nhân viên trong **SecureTable**: Lễ tân (`Reception`), Bếp (`Kitchen`), Thủ kho (`Inventory`) và Quản trị viên (`Admin`).
* Phát triển bảng theo dõi **Security & Audit Logs Dashboard** trên giao diện Admin để tra cứu lịch sử thao tác nhạy cảm và trạng thái bảo vệ hệ thống.
* Rà soát bảo mật phía giao diện người dùng (làm sạch dữ liệu hiển thị chống **Cross-Site Scripting - XSS**) và thống nhất phương án tối ưu chi phí bảo mật cùng nhóm.

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|------|-----------|-------------|----------------|---------------|
| 2 | **Phát triển giao diện Lễ tân (`Reception`) & Sơ đồ bàn:** <br> - Xây dựng màn hình quản lý trạng thái bàn trực quan (Trống, Đang phục vụ, Đang thanh toán) <br> - Thiết kế luồng mở hóa đơn mới, xem chi tiết các món khách đã gọi tại bàn và thực hiện đóng/chốt hóa đơn | 02/11/2026 | 02/11/2026 | https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/best-practices.html |
| 3 | **Phát triển màn hình Bếp (`Kitchen Display`):** <br> - Xây dựng giao diện hàng đợi món đang chờ chế biến, tự động làm mới định kỳ để bếp nhận đơn kịp thời <br> - Thiết kế nút xác nhận hoàn tất món (`Serve`) và từ chối món kèm lý do (`Hết nguyên liệu` / `Khách yêu cầu hủy`) | 03/11/2026 | 03/11/2026 | https://docs.aws.amazon.com/lambda/latest/dg/welcome.html |
| 4 | **Phát triển màn hình Kho nguyên liệu (`Inventory`):** <br> - Xây dựng form ghi nhận phiếu nhập kho nguyên liệu, kiểm kê/điều chỉnh số lượng tồn kho thực tế và bảng tra cứu lịch sử biến động nguyên liệu | 04/11/2026 | 04/11/2026 | https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/transaction-apis.html |
| 5 | **Xây dựng màn hình Admin Báo cáo & Security/Audit Logs:** <br> - Thiết kế bảng tổng hợp doanh thu theo ngày/kỳ cho Admin <br> - Xây dựng giao diện tra cứu **Audit Logs** (`/v1/audit-logs`) hiển thị rõ người thực hiện, vai trò, hành động và thời gian để dễ dàng đối chiếu khi có sai lệch số liệu | 05/11/2026 | 05/11/2026 | https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/sec_detect_investigate_events.html |
| 6 | **Xử lý chống XSS trên Frontend & Rà soát cấu hình an toàn:** <br> - Rà soát cách render chuỗi văn bản trên giao diện để ngăn chặn lỗi **XSS** khi có dữ liệu đầu vào chứa thẻ lạ, đồng thời kiểm tra không lưu bất kỳ khóa bí mật nào trong thư mục `frontend/` <br> - Thảo luận cùng nhóm về việc sử dụng mã hóa mặc định miễn phí (`SSE-S3` và AWS-owned key của DynamoDB) thay cho KMS trả phí | 06/11/2026 | 06/11/2026 | https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/EncryptionAtRest.html |

### Kết quả đạt được trong tuần 8

* Hoàn thiện trọn bộ giao diện tác nghiệp cho tất cả các bộ phận trong nhà hàng (`Reception`, `Kitchen`, `Inventory`, `Admin`) trên cùng một ứng dụng Web thống nhất.
* Xây dựng trực quan màn hình **Audit Logs & Security** giúp người quản lý theo dõi minh bạch các thao tác đóng hóa đơn, hủy món và điều chỉnh kho.
* Đảm bảo an toàn hiển thị dữ liệu phía trình duyệt (chống XSS) và giữ mã nguồn Frontend sạch sẽ, không chứa thông tin xác thực nhạy cảm.
