---
title: "Worklog Tuần 5"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu tuần 5

* Nghiên cứu bộ khung **AWS Well-Architected Framework** (trọng tâm vào Security, Reliability, Operational Excellence, Performance Efficiency và Cost Optimization).
* Thống nhất bài toán thực tế và phạm vi dự án **SecureTable** (Hệ thống quản lý nguyên liệu và gọi món bằng mã QR trên nền tảng AWS Serverless tại Region `ap-southeast-1`).
* Thiết kế sơ đồ kiến trúc chuẩn AWS Architecture Icons và phân tích luồng nghiệp vụ cho 5 nhóm vai trò: `Guest`, `Reception`, `Kitchen`, `Inventory`, `Admin`.
* Lập bảng dự toán chi phí vận hành hàng tháng và 12 tháng dựa trên kịch bản tải thực tế bằng **AWS Pricing Calculator**.

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|------|-----------|-------------|----------------|---------------|
| 2 | **Nghiên cứu AWS Well-Architected Framework:** <br> - Tìm hiểu các nguyên tắc thiết kế cốt lõi của 6 trụ cột AWS Well-Architected <br> - Đi sâu vào Security Pillar (Least Privilege IAM, bảo vệ dữ liệu truyền tải/lưu trữ, truy vết thao tác) | 12/10/2026 | 12/10/2026 | https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html |
| 3 | **Phân tích yêu cầu nghiệp vụ dự án SecureTable:** <br> - Xác định bài toán sai lệch tồn kho, chậm chuyển đơn bếp và đối chiếu doanh thu thủ công ở nhà hàng nhỏ <br> - Phân định quyền hạn và luồng thao tác của 5 nhóm người dùng (`Guest`, `Reception`, `Kitchen`, `Inventory`, `Admin`) <br> - Lựa chọn bộ dịch vụ AWS Serverless: S3, CloudFront, API Gateway, Lambda, DynamoDB, Cognito, EventBridge Scheduler, SNS, CloudWatch, CloudTrail, WAF | 13/10/2026 | 13/10/2026 | https://aws.amazon.com/serverless/ |
| 4 | **Thiết kế sơ đồ kiến trúc chuẩn AWS:** <br> - Tự tay thiết kế sơ đồ kiến trúc `SecureTable_Architecture` trên Draw.io với bộ AWS Architecture Icons chính thức <br> - Biểu diễn rõ ràng 4 luồng xử lý: Guest gọi món qua QR, Staff xác thực qua Cognito, xử lý giao dịch Kitchen/Inventory và luồng Automation báo cáo/sao lưu | 14/10/2026 | 14/10/2026 | https://aws.amazon.com/architecture/icons/ |
| 5 | **Dự toán ngân sách với AWS Pricing Calculator:** <br> - Xây dựng giả định tải thực tế (10 bàn, ~40.000 REST API requests/tháng, ~60.000 Lambda invocations ở mức 256 MB, ~1 GB DynamoDB) tại Region Singapore (`ap-southeast-1`) <br> - Tính toán chi phí từng dịch vụ ($5.60/tháng + $2.00 dự phòng = **$7.60/tháng**) và đề xuất phương án tối ưu chi phí | 15/10/2026 | 15/10/2026 | https://calculator.aws/ |
| 6 | **Đánh giá rủi ro & Hoàn thiện tài liệu Proposal:** <br> - Phân tích rủi ro bảo mật mã QR tĩnh (giới hạn Guest Session theo hóa đơn đang `OPEN`), xung đột đặt món đồng thời (dùng DynamoDB Transactions) và rủi ro vượt ngân sách <br> - Biên tập hoàn chỉnh tài liệu Proposal song ngữ Tiếng Việt – Tiếng Anh | 16/10/2026 | 16/10/2026 | https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/welcome.html |

### Kết quả đạt được trong tuần 5

* Hoàn thiện kiến trúc tổng thể cho hệ thống **SecureTable** tuân thủ chặt chẽ các nguyên tắc của **AWS Well-Architected Framework**.
* Xây dựng sơ đồ kiến trúc rõ nét, đúng chuẩn icon và tên dịch vụ của AWS, phản ánh chính xác luồng dữ liệu thực tế của sản phẩm.
* Lập bảng dự toán chi phí minh bạch (**$7.60/tháng** tương đương **$91.20/năm**) kèm giải pháp kiểm soát ngân sách bằng AWS Budgets.
* Xác định rõ các biện pháp kiểm soát rủi ro nghiệp vụ và an toàn thông tin ngay từ khâu thiết kế.
