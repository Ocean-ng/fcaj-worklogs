---
title: "Worklog Tuần 10"
date: 2024-01-01
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Mục tiêu tuần 10

* Tăng cường bảo vệ tầng biên cho giao diện Web và API của **SecureTable** bằng tường lửa ứng dụng **AWS WAF** tích hợp trên **Amazon CloudFront**.
* Thiết lập hệ thống giám sát vận hành tập trung với **Amazon CloudWatch** (Lambda Logs, API Gateway Metrics, CloudWatch Alarms gửi cảnh báo qua SNS).
* Theo dõi và kiểm toán hoạt động API cấp tài khoản AWS bằng **AWS CloudTrail**, phân biệt rõ với Audit Logs nghiệp vụ trong DynamoDB.
* Viết và chia sẻ các bài Blog kỹ thuật về **Shared Responsibility Model**, **Bảo mật S3** và **IAM & CloudTrail** lên nhóm cộng đồng **AWS Study Group VN**.

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|------|-----------|-------------|----------------|---------------|
| 2 | **Tích hợp tường lửa ứng dụng AWS WAF trên CloudFront:** <br> - Tìm hiểu cấu trúc Web ACL, AWS Managed Rules (chống SQLi, XSS, Bad Inputs) và Rate-based Rules trên AWS WAF <br> - Thử nghiệm cấu hình lọc các request web bất thường và đánh giá cơ chế tính phí trong CloudFront Free Plan vs WAF độc lập | 16/11/2026 | 16/11/2026 | https://000026.awsstudygroup.com/ |
| 3 | **Thiết lập giám sát với Amazon CloudWatch Logs & Metrics:** <br> - Rà soát CloudWatch Log Groups của tất cả các hàm Lambda trong SecureTable và đặt thời gian lưu trữ hợp lý (Log Retention) để tránh lãng phí dung lượng <br> - Theo dõi các chỉ số `Errors`, `Duration`, `Throttles` của Lambda và `4XXError`, `5XXError`, `Latency` của API Gateway | 17/11/2026 | 17/11/2026 | https://000018.awsstudygroup.com/ |
| 4 | **Cấu hình CloudWatch Alarms & Tổng hợp bài viết S3 Security:** <br> - Tạo CloudWatch Standard Alarms kích hoạt thông báo qua Amazon SNS khi tỷ lệ lỗi Lambda hoặc lỗi 5XX API vượt ngưỡng <br> - Đọc sâu tài liệu Shared Responsibility Model & S3 Security và đăng bài chia sẻ lên nhóm **AWS Study Group VN** | 18/11/2026 | 18/11/2026 | https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/AlarmThatSendsEmail.html |
| 5 | **Kiểm toán hoạt động tài khoản với AWS CloudTrail:** <br> - Kiểm tra lịch sử Management Events trong 90 ngày qua trên **AWS CloudTrail Event History** tại Region `ap-southeast-1` <br> - Phân biệt phạm vi của CloudTrail (kiểm toán thao tác hạ tầng AWS) với bảng Audit Logs trong DynamoDB (truy vết nghiệp vụ nhà hàng) và đăng bài Blog về IAM & CloudTrail | 19/11/2026 | 19/11/2026 | https://docs.aws.amazon.com/awscloudtrail/latest/userguide/view-cloudtrail-events.html |
| 6 | **Kiểm thử kịch bản lỗi & Cảnh báo tự động:** <br> - Giả lập các request sai định dạng payload và timeout để kiểm tra khả năng xử lý lỗi an toàn của Lambda và xác nhận cảnh báo CloudWatch Alarm hoạt động chính xác | 20/11/2026 | 20/11/2026 | https://000032.awsstudygroup.com/ |

### Kết quả đạt được trong tuần 10

* Nâng cao năng lực phòng thủ lớp ứng dụng cho **SecureTable** bằng **AWS WAF** kết hợp **Amazon CloudFront HTTPS**.
* Hoàn thiện trụ cột **Operational Excellence** với hệ thống logging, đo lường metrics và cảnh báo sự cố tự động qua **Amazon CloudWatch & SNS**.
* Hiểu sâu cơ chế truy vết kép: dùng **AWS CloudTrail** cho tầng quản trị tài khoản AWS và **DynamoDB Audit Logs** cho tầng nghiệp vụ ứng dụng, đồng thời hoàn thành chuỗi bài Blog chia sẻ kiến thức trên **AWS Study Group VN**.
