---
title: "Worklog Tuần 5"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu tuần 5

* Tìm hiểu các nguyên tắc cốt lõi của **AWS Well-Architected Framework** để chuẩn bị bước vào giai đoạn làm dự án nhóm.
* Cùng nhóm khảo sát thực tế quy trình vận hành quán ăn nhỏ, thống nhất đề tài **SecureTable** (Hệ thống quản lý nguyên liệu và gọi món bằng mã QR trên nền tảng AWS Serverless tại Region `ap-southeast-1`).
* Phân chia rõ vai trò giữa các thành viên trong nhóm: nhận nhiệm vụ phụ trách **Frontend (giao diện Guest & Staff), bảo mật tầng giao diện, triển khai S3 + CloudFront và quay dựng Demo sản phẩm**.
* Cùng nhóm rà soát sơ đồ kiến trúc, phân quyền 5 nhóm vai trò và dự toán ngân sách vận hành thử nghiệm trên AWS.

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|------|-----------|-------------|----------------|---------------|
| 2 | **Tìm hiểu AWS Well-Architected Framework:** <br> - Đọc tài liệu tổng quan về 6 trụ cột của AWS Well-Architected, chú trọng Security Pillar và Cost Optimization Pillar cho ứng dụng nhỏ | 12/10/2026 | 12/10/2026 | https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html |
| 3 | **Họp nhóm khảo sát bài toán & Chốt kiến trúc Serverless:** <br> - Thảo luận bài toán thực tế tại quán ăn quy mô nhỏ (nhầm đơn giấy, sai lệch nguyên liệu kho, tổng hợp doanh thu thủ công) <br> - Nhóm thống nhất chọn kiến trúc **100% AWS Serverless** (S3, CloudFront, API Gateway, Lambda, DynamoDB, Cognito, EventBridge Scheduler, SNS) thay cho EC2/RDS để tối ưu chi phí dưới $10/tháng | 13/10/2026 | 13/10/2026 | https://aws.amazon.com/serverless/ |
| 4 | **Phân chia công việc nhóm & Xác định luồng người dùng:** <br> - Thống nhất phân công trong nhóm 4 người: mình đảm nhận mảng **Frontend Web (React/Vite), tích hợp giao diện bảo mật & phụ trách Demo** <br> - Phân tích chi tiết thao tác trên giao diện của 5 vai trò: `Guest` (quét QR gọi món), `Reception`, `Kitchen`, `Inventory` và `Admin` | 14/10/2026 | 14/10/2026 | https://docs.aws.amazon.com/wellarchitected/latest/serverless-applications-lens/web-applications.html |
| 5 | **Phối hợp rà soát sơ đồ kiến trúc & Dự toán chi phí:** <br> - Cùng các bạn trong nhóm kiểm tra luồng dữ liệu từ trình duyệt người dùng qua **CloudFront + S3** vào **API Gateway / Cognito** trên bản vẽ `SecureTable_Architecture` <br> - Tìm hiểu cách nhóm lập bảng dự toán chi phí (~$7.60/tháng cho 10 bàn) tham chiếu theo AWS Pricing Calculator | 15/10/2026 | 15/10/2026 | https://calculator.aws/ |
| 6 | **Góp ý rủi ro giao diện & Hoàn thiện Proposal nhóm:** <br> - Thảo luận cùng nhóm về giới hạn bảo mật của mã QR cố định tại bàn (cần khóa phiên Guest theo hóa đơn đang mở `OPEN`) <br> - Rà soát nội dung bản đề xuất **Proposal** song ngữ Việt - Anh của nhóm | 16/10/2026 | 16/10/2026 | https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/welcome.html |

### Kết quả đạt được trong tuần 5

* Xác định rõ phạm vi nghiệp vụ của dự án **SecureTable** và nắm chắc ranh giới công việc cá nhân trong nhóm (Frontend, triển khai S3/CloudFront và Demo).
* Hiểu rõ lý do nhóm lựa chọn mô hình **AWS Serverless** để vừa đảm bảo khả năng mở rộng vừa giữ chi phí thử nghiệm ở mức thấp.
* Nắm vững luồng tương tác của cả 5 nhóm người dùng để làm cơ sở thiết kế màn hình giao diện trong tuần tiếp theo.
