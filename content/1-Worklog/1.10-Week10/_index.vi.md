---
title: "Worklog Tuần 10"
date: 2026-11-16
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Mục tiêu tuần 10

* Thiết lập hệ thống giám sát hiệu năng và thu thập log tập trung với **Amazon CloudWatch** (Metrics, Logs, Alarms, Dashboards).
* Kích hoạt và phân tích lưu lượng mạng ra/vào VPC bằng **VPC Flow Logs** để phát hiện các kết nối bị từ chối (`REJECT`) hoặc quét cổng bất thường.
* Triển khai nhật ký kiểm toán toàn bộ thao tác API trên tài khoản AWS với **AWS CloudTrail** kèm tính năng xác thực tính toàn vẹn của tệp log (Log File Integrity Validation).
* Xây dựng luồng cảnh báo sự cố bảo mật tự động theo thời gian thực qua email bằng **Amazon EventBridge** và **Amazon SNS**.

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|------|-----------|-------------|----------------|---------------|
| 2 | **Giám sát hạ tầng với Amazon CloudWatch:** <br> - Tìm hiểu kiến trúc CloudWatch Metrics, Namespaces, Dimensions và CloudWatch Logs <br> - Thiết lập CloudWatch Alarms theo dõi ngưỡng CPU Utilization, lỗi 4xx/5xx của API Gateway và lỗi thực thi Lambda <br> - Tạo CloudWatch Dashboard trực quan hóa trạng thái sức khỏe hệ thống | 16/11/2026 | 16/11/2026 | https://000018.awsstudygroup.com/ |
| 3 | **Phân tích lưu lượng mạng với VPC Flow Logs:** <br> - Cấu hình VPC Flow Logs đẩy bản ghi lưu lượng mạng của VPC vào CloudWatch Log Group <br> - Sử dụng **CloudWatch Logs Insights** viết truy vấn lọc các gói tin có trạng thái `REJECT` để nhận diện hành vi dò quét cổng (Port Scanning) hoặc cấu hình sai Security Group | 17/11/2026 | 17/11/2026 | https://000032.awsstudygroup.com/ |
| 4 | **Nhật ký kiểm toán với AWS CloudTrail:** <br> - Tìm hiểu vai trò của AWS CloudTrail trong việc truy vết *"Ai đã làm gì, vào lúc nào, từ IP nào"* trên tài khoản AWS <br> - Tạo Multi-Region Trail lưu trữ log vào S3 Bucket chuyên biệt, bật mã hóa SSE-KMS và kích hoạt **Log File Integrity Validation** (băm SHA-256 chống chỉnh sửa log) | 18/11/2026 | 18/11/2026 | https://000032.awsstudygroup.com/ |
| 5 | **Tự động cảnh báo với Amazon EventBridge & SNS:** <br> - Tạo Amazon SNS Topic và đăng ký nhận cảnh báo qua Email <br> - Thiết lập EventBridge Rule bắt các sự kiện nhạy cảm từ CloudTrail (ví dụ: đăng nhập Root Account, thay đổi Security Group, xóa KMS Key) để bắn thông báo tức thời qua SNS | 19/11/2026 | 19/11/2026 | https://000032.awsstudygroup.com/ |
| 6 | **Kiểm thử luồng Incident Alerting & Tổng kết:** <br> - Thực hiện thao tác thử nghiệm thay đổi một rule trên Security Group và kiểm tra độ trễ nhận email cảnh báo từ SNS <br> - Rà soát chính sách lưu giữ log (Log Retention Policy = 14 ngày) trên CloudWatch để tối ưu chi phí | 20/11/2026 | 20/11/2026 | https://000018.awsstudygroup.com/ |

### Kết quả đạt được trong tuần 10

* Xây dựng hoàn chỉnh hệ thống quan sát (Observability) tập trung với **Amazon CloudWatch**, kết hợp Dashboard và Alarms để phát hiện sớm các bất thường về tài nguyên.
* Thành thạo cách bật và truy vấn **VPC Flow Logs** bằng CloudWatch Logs Insights để điều tra sự cố kết nối mạng và giám sát lưu lượng bị chặn ở tầng VPC.
* Thiết lập hệ thống kiểm toán bất biến với **AWS CloudTrail**, đảm bảo tính chống chối bỏ (Non-repudiation) và phát hiện mọi can thiệp trái phép vào tệp nhật ký nhờ Log File Integrity Validation.
* Tự động hóa quy trình phản ứng sự cố an ninh theo thời gian thực bằng sự kết hợp giữa **CloudTrail + Amazon EventBridge + Amazon SNS**.
