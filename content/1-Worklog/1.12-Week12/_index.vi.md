---
title: "Worklog Tuần 12"
date: 2024-01-01
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

### Mục tiêu tuần 12

* Thực hiện kiểm thử tổng thể End-to-End (E2E) toàn bộ quy trình nghiệp vụ thực tế của hệ thống **SecureTable** trên môi trường AWS (`ap-southeast-1`).
* Đối chiếu chi phí sử dụng thực tế trên **AWS Cost Explorer / Billing** với bảng dự toán ngân sách, kiểm tra quy trình dọn dẹp tài nguyên (**Clean-up**) triệt để.
* Hoàn thiện và rà soát chuẩn song ngữ (Tiếng Việt – Tiếng Anh) cho toàn bộ 7 chuyên mục trên website báo cáo thực tập Hugo.
* Chuẩn bị minh chứng Demo sản phẩm và hoàn tất thủ tục nộp báo cáo kỳ thực tập chương trình **First Cloud AI Journey**.

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|------|-----------|-------------|----------------|---------------|
| 2 | **Kiểm thử End-to-End (E2E) hệ thống SecureTable:** <br> - Kiểm thử trọn vẹn luồng nghiệp vụ: Reception mở bàn & hóa đơn → Guest quét QR gọi món → Kitchen hoàn tất/từ chối món → Inventory cập nhật kho → Reception đóng hóa đơn → Admin kiểm tra doanh thu & Audit Logs <br> - Kiểm thử các kịch bản biên (đặt món khi hóa đơn đã đóng, đặt vượt tồn kho, gọi API trái quyền) | 30/11/2026 | 30/11/2026 | https://docs.aws.amazon.com/wellarchitected/latest/serverless-applications-lens/opex-testing.html |
| 3 | **Chuẩn bị Minh chứng Demo & Rà soát phần Cost:** <br> - Ghi hình / chuẩn bị kịch bản Live Demo minh chứng sản phẩm chạy thực tế khớp đúng sơ đồ kiến trúc <br> - Đối chiếu chi phí vận hành trên AWS Billing & Cost Explorer với bảng dự toán AWS Pricing Calculator (**$7.60/tháng**) | 01/12/2026 | 01/12/2026 | https://docs.aws.amazon.com/cost-management/latest/userguide/ce-what-is.html |
| 4 | **Hoàn thiện Blogs, Events, Tự đánh giá & Góp ý:** <br> - Rà soát danh sách các bài Blog kỹ thuật (kèm đầy đủ tài liệu tham khảo và hình ảnh sơ đồ AWS) cùng các sự kiện đã tham gia tại văn phòng AWS Việt Nam <br> - Hoàn thiện mục `6-Self-evaluation` và `7-Feedback` trên cả hai phiên bản Tiếng Việt và Tiếng Anh | 02/12/2026 | 02/12/2026 | https://cloudjourney.awsstudygroup.com/ |
| 5 | **Kiểm tra quy trình Dọn dẹp tài nguyên (Clean-up):** <br> - Rà soát chi tiết hướng dẫn Clean-up sau khi kết thúc demo (xóa EventBridge Schedules, tắt CloudWatch Alarms, xóa API Gateway/Lambda, xóa bảng DynamoDB/PITR, làm trống và xóa S3 Buckets, vô hiệu hóa CloudFront Distribution) | 03/12/2026 | 03/12/2026 | https://000007.awsstudygroup.com/ |
| 6 | **Kiểm tra GitHub Pages & Nghiệm thu báo cáo thực tập:** <br> - Đẩy mã nguồn hoàn chỉnh lên GitHub repository (`Ocean-ng/fcaj-worklogs`) và kiểm tra workflow GitHub Actions <br> - Kiểm tra toàn bộ link điều hướng, hình ảnh, code blocks và chuyển đổi ngôn ngữ VI/EN trên trang chính thức | 04/12/2026 | 04/12/2026 | https://ocean-ng.github.io/fcaj-worklogs/ |

### Kết quả đạt được trong tuần 12

* Kiểm chứng thành công quy trình hoạt động End-to-End của **SecureTable** trên hạ tầng AWS Serverless với dữ liệu nhất quán, phân quyền chặt chẽ và giám sát đầy đủ.
* Đảm bảo đầy đủ bảng dự toán chi phí, chiến lược tối ưu hóa chi phí và hướng dẫn dọn dẹp tài nguyên triệt để nhằm tránh mọi chi phí phát sinh ngoài ý muốn.
* Hoàn thiện website báo cáo thực tập **First Cloud AI Journey** song ngữ (Việt – Anh) đúng chuẩn template, đầy đủ references và minh chứng thực tế.
* Tổng kết vững vàng hành trang kiến thức AWS Cloud & An toàn thông tin sau 3 tháng thực tập, sẵn sàng cho buổi bảo vệ và chặng đường nghề nghiệp phía trước.
