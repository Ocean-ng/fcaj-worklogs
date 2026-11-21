---
title: "Worklog Tuần 5"
date: 2026-10-12
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu tuần 5

* Nghiên cứu 6 trụ cột của bộ khung **AWS Well-Architected Framework**, trọng tâm vào hai trụ cột Bảo mật (Security Pillar) và Tối ưu chi phí (Cost Optimization Pillar).
* Phân tích yêu cầu bài toán thực tế, xác định phạm vi hệ thống và lựa chọn tập dịch vụ AWS phù hợp cho bản đề xuất dự án (Proposal).
* Thiết kế sơ đồ kiến trúc tổng thể (Architecture Diagram) và luồng dữ liệu của hệ thống bằng công cụ Draw.io.
* Thực hành ước tính chi phí vận hành hạ tầng hàng tháng/hàng năm bằng công cụ **AWS Pricing Calculator**.

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|------|-----------|-------------|----------------|---------------|
| 2 | **Nghiên cứu AWS Well-Architected Framework:** <br> - Tìm hiểu 6 trụ cột: Operational Excellence, Security, Reliability, Performance Efficiency, Cost Optimization, Sustainability <br> - Đi sâu vào các nguyên tắc thiết kế của Security Pillar (Identity Foundation, Traceability, Security at all layers, Data Protection) | 12/10/2026 | 12/10/2026 | https://docs.aws.amazon.com/wellarchitected/ |
| 3 | **Phân tích bài toán & Lựa chọn dịch vụ AWS:** <br> - Xác định yêu cầu chức năng và phi chức năng (độ trễ, khả năng mở rộng, mức độ bảo mật dữ liệu) <br> - Đối chiếu và lựa chọn các dịch vụ AWS Serverless & Managed Services (Amazon S3, VPC Endpoints, Lambda, API Gateway, Cognito) để giảm chi phí vận hành | 13/10/2026 | 13/10/2026 | https://cloudjourney.awsstudygroup.com/ |
| 4 | **Thiết kế sơ đồ kiến trúc (Architecture Diagram):** <br> - Sử dụng bộ icon chuẩn AWS Architecture Icons trên Draw.io <br> - Vẽ sơ đồ kiến trúc mạng, luồng thu thập/xử lý dữ liệu và biên giới bảo mật (VPC, Subnets, Endpoints, IAM Roles) | 14/10/2026 | 14/10/2026 | https://aws.amazon.com/architecture/icons/ |
| 5 | **Ước tính ngân sách với AWS Pricing Calculator:** <br> - Liệt kê định lượng khối lượng tải (số lượng requests, dung lượng lưu trữ S3, thời gian thực thi Lambda, lưu lượng truyền tải dữ liệu) <br> - Nhập thông số lên AWS Pricing Calculator và xuất báo cáo dự toán chi phí theo tháng và 12 tháng | 15/10/2026 | 15/10/2026 | https://calculator.aws/ |
| 6 | **Đánh giá rủi ro & Hoàn thiện Proposal:** <br> - Xây dựng ma trận đánh giá rủi ro (mất kết nối mạng, lỗi thiết bị/dịch vụ, vượt ngân sách) và phương án giảm thiểu <br> - Tổng hợp và hoàn thiện tài liệu Proposal trên trang báo cáo thực tập | 16/10/2026 | 16/10/2026 | https://cloudjourney.awsstudygroup.com/ |

### Kết quả đạt được trong tuần 5

* Nắm vững tư duy thiết kế hệ thống đám mây theo chuẩn **AWS Well-Architected Framework**, đảm bảo cân bằng giữa tính bảo mật, độ tin cậy và chi phí.
* Hoàn thành sơ đồ kiến trúc giải pháp trực quan, chuẩn hóa theo bộ ký hiệu kỹ thuật của AWS.
* Tính toán minh bạch và tối ưu chi phí hạ tầng bằng **AWS Pricing Calculator**, tận dụng hiệu quả các dịch vụ Serverless và Free Tier.
* Hoàn thiện bản đề xuất dự án (Proposal) kèm kế hoạch quản trị rủi ro và lộ trình triển khai rõ ràng.
