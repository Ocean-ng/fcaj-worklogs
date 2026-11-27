---
title: "Worklog Tuần 9"
date: 2024-01-01
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Mục tiêu tuần 9

* Xây dựng phân hệ tự động hóa lập lịch báo cáo doanh thu và sao lưu dữ liệu cho **SecureTable** bằng **Amazon EventBridge Scheduler**, **AWS Lambda** và **Amazon SNS**.
* Cấu hình khôi phục theo thời điểm (**DynamoDB Point-in-Time Recovery - PITR**), xuất dữ liệu định kỳ (**DynamoDB Export to S3**) và tối ưu hóa chi phí lưu trữ dài hạn bằng **S3 Lifecycle Policy** (chuyển sang S3 Glacier Flexible Retrieval).
* Tham gia sự kiện kỹ thuật **AWS Cloud Mastery** tại văn phòng AWS Việt Nam để rà soát kiến trúc và học hỏi kinh nghiệm thực chiến.

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|------|-----------|-------------|----------------|---------------|
| 2 | **Tìm hiểu & Thiết lập Amazon EventBridge Scheduler:** <br> - Nghiên cứu cơ chế lập lịch Serverless với EventBridge Scheduler (hỗ trợ múi giờ `Asia/Ho_Chi_Minh`, chính sách Retry và Dead-Letter Queue) <br> - Tạo IAM Execution Role riêng chỉ cho phép Scheduler kích hoạt đúng hàm `Report Lambda` và `Backup Lambda` | 09/11/2026 | 09/11/2026 | https://docs.aws.amazon.com/scheduler/latest/UserGuide/what-is-scheduler.html |
| 3 | **Phát triển `Report Lambda` & Gửi thông báo qua Amazon SNS:** <br> - Viết hàm `Report Lambda` tổng hợp số lượng hóa đơn, doanh thu ngày/tuần và lượng nguyên liệu tiêu hao từ DynamoDB <br> - Tạo Amazon SNS Topic, xác thực Email nhận thông báo của Admin và kiểm thử gửi báo cáo tự động | 10/11/2026 | 10/11/2026 | https://docs.aws.amazon.com/sns/latest/dg/welcome.html |
| 4 | **Triển khai DynamoDB PITR & `Backup Lambda` (Export to S3):** <br> - Bật tính năng **Point-in-Time Recovery (PITR)** trên các bảng dữ liệu quan trọng của SecureTable <br> - Phát triển `Backup Lambda` gọi API `ExportTableToPointInTime` để xuất bản sao dữ liệu hàng tuần ra S3 Backup Bucket riêng tư | 11/11/2026 | 11/11/2026 | https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/PointInTimeRecovery.html |
| 5 | **Tối ưu chi phí lưu trữ bản sao lưu với S3 Lifecycle:** <br> - Thiết lập **S3 Lifecycle Rule** trên S3 Backup Bucket để tự động chuyển các bản xuất dữ liệu cũ sang lớp **S3 Glacier Flexible Retrieval** và hết hạn bản sao quá hạn lưu trữ <br> - Kiểm tra tính bất đồng bộ của quá trình Export và ghi chú rõ giới hạn thời gian khôi phục | 12/11/2026 | 12/11/2026 | https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lifecycle-mgmt.html |
| 6 | **Kiểm thử luồng Automation & Tham dự AWS Cloud Mastery (14/11):** <br> - Kiểm thử End-to-End luồng EventBridge Scheduler kích hoạt báo cáo/backup và kiểm tra log thực thi <br> - Tham dự buổi chia sẻ trực tiếp **AWS Cloud Mastery** (Sáng Thứ Bảy 14/11/2026 tại Tầng 26 Bitexco) để trao đổi kinh nghiệm tối ưu kiến trúc Serverless | 13/11/2026 | 14/11/2026 | https://aws.amazon.com/blogs/compute/introducing-amazon-eventbridge-scheduler/ |

### Kết quả đạt được trong tuần 9

* Vận hành thành công luồng tự động hóa hoàn toàn tách biệt với luồng đặt món chính: tự động tổng hợp báo cáo gửi qua **Amazon SNS** và tự động xuất bản sao lưu sang **Amazon S3** theo lịch **EventBridge Scheduler**.
* Đáp ứng tiêu chí **Reliability** và **Cost Optimization** của Well-Architected nhờ kết hợp **DynamoDB PITR**, **Export to S3** và chính sách vòng đời dữ liệu **S3 Lifecycle**.
* Đúc kết thêm nhiều kinh nghiệm quý báu về bảo mật và vận hành hệ thống thực tế thông qua sự kiện **AWS Cloud Mastery**.
