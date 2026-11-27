---
title: "Blog 5"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 3.5. </b> "
---

# Tự động hóa tác vụ theo thời gian quy mô lớn với Amazon EventBridge Scheduler, AWS Lambda và DynamoDB

* **Chủ đề:** Serverless Automation & Reliability trên AWS
* **Tác giả:** Thúy Nga

---

Trong các ứng dụng thực tế (như gửi báo cáo doanh thu cuối ngày, xuất bản sao lưu dữ liệu hàng tuần, thu hồi phiên truy cập hết hạn hay hủy gói đăng ký khi đến kỳ), bài toán **lập lịch chạy tác vụ theo thời gian (Scheduling)** xuất hiện ở hầu hết mọi dự án. Nếu duy trì một máy chủ EC2 bật 24/7 chỉ để chạy `crontab`, hệ thống vừa tốn chi phí nhàn rỗi, vừa tạo ra điểm lỗi đơn (Single Point of Failure) khi máy chủ đó bị treo.

**Amazon EventBridge Scheduler** giải quyết bài toán này theo hướng hoàn toàn **Serverless**, cho phép quản lý từ vài tác vụ định kỳ của dự án nhỏ đến hàng triệu lịch chạy độc lập mà không cần vận hành bất kỳ máy chủ nào.

![Kiến trúc lập lịch theo thời gian với Amazon EventBridge Scheduler, AWS Lambda và DynamoDB (Nguồn: AWS Compute Blog)](/images/3-BlogsPosted/blog5-eventbridge-scheduler.png)

### 1. Điểm khác biệt đáng chú ý của EventBridge Scheduler

* **Hỗ trợ cả lịch định kỳ (Recurring) và lịch chạy một lần tự hủy (One-time Schedule):** Ngoài biểu thức `cron()` và `rate()` quen thuộc, ứng dụng có thể dùng Lambda gọi API tạo một lịch `at(yyyy-mm-ddThh:mm:ss)` cho từng sự kiện cụ thể (như minh họa trên sơ đồ khi hẹn ngày kết thúc gói dịch vụ của người dùng) và bật `ActionAfterCompletion = DELETE` để lịch tự động xóa sau khi chạy xong.
* **Hỗ trợ múi giờ địa phương (Timezone-aware):** Cho phép chọn trực tiếp múi giờ (ví dụ `Asia/Ho_Chi_Minh`) thay vì phải tự cộng trừ thủ công sang giờ UTC như các rule cũ.
* **Tích hợp hơn 270 dịch vụ AWS (Universal Targets):** Không chỉ gọi được **AWS Lambda**, EventBridge Scheduler có thể gọi thẳng tới các API của **Amazon SNS**, **Amazon SQS**, **DynamoDB** (như `ExportTableToPointInTime`) hay **Step Functions** thông qua AWS SDK Targets.

### 2. Cơ chế đảm bảo độ tin cậy (Reliability) và Bảo mật (IAM)

* **Chính sách thử lại (Retry Policy) & Dead-Letter Queue (DLQ):** Nếu thời điểm kích hoạt mà hàm Lambda đích gặp lỗi tạm thời hoặc bị giới hạn đồng thời (Throttling), EventBridge Scheduler hỗ trợ cấu hình số lần retry tối đa và tự động đẩy sự kiện thất bại vào hàng đợi **Amazon SQS DLQ** để không làm mất tác vụ quan trọng.
* **Cửa sổ thời gian linh hoạt (Flexible Time Window):** Với hàng loạt báo cáo hoặc tác vụ backup không bắt buộc phải nổ đúng từng giây `00:00:00`, bật Flexible Time Window (ví dụ 15 phút) giúp phân tán tải đều hơn, tránh gây nghẽn đột ngột lên cơ sở dữ liệu **Amazon DynamoDB** phía sau.
* **Phân quyền IAM tách biệt:** EventBridge Scheduler sử dụng một **IAM Execution Role** riêng gắn cho từng lịch (hoặc nhóm lịch) với Trust Policy chỉ tin cậy `scheduler.amazonaws.com` và chỉ cấp quyền `lambda:InvokeFunction` lên đúng ARN của hàm Lambda mục tiêu.

### Checklist khi áp dụng EventBridge Scheduler vào dự án

* Xác định rõ tác vụ là định kỳ (`cron` / `rate`) hay chạy một lần (`at`) để bật tự động xóa lịch (`DELETE`) sau khi hoàn tất, tránh rác tài nguyên.
* Đặt đúng múi giờ nghiệp vụ (`Asia/Ho_Chi_Minh`) cho các báo cáo tổng kết ngày/tuần.
* Gắn **SQS Dead-Letter Queue** và theo dõi metric `InvocationDroppedCount` trên CloudWatch đối với các tác vụ quan trọng như sao lưu dữ liệu hay chốt số liệu tài chính.
* Đảm bảo hàm Lambda được gọi theo lịch có tính **Idempotent** (chạy lặp lại 2 lần cho cùng một sự kiện vẫn không làm nhân đôi dữ liệu hay gửi trùng báo cáo).

### Tài liệu tham khảo

1. [Introducing Amazon EventBridge Scheduler – AWS Compute Blog](https://aws.amazon.com/blogs/compute/introducing-amazon-eventbridge-scheduler/)
2. [What is Amazon EventBridge Scheduler? – User Guide](https://docs.aws.amazon.com/scheduler/latest/UserGuide/what-is-scheduler.html)
3. [Managing schedule retries and dead-letter queues – EventBridge Scheduler User Guide](https://docs.aws.amazon.com/scheduler/latest/UserGuide/managing-schedule-dlq.html)
4. [Identity and Access Management for Amazon EventBridge Scheduler](https://docs.aws.amazon.com/scheduler/latest/UserGuide/security-iam.html)

`#AWS` `#Serverless` `#EventBridge` `#AWSLambda`
