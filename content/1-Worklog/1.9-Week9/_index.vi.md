---
title: "Worklog Tuần 9"
date: 2026-11-09
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Mục tiêu tuần 9

* Tìm hiểu kiến trúc phân phối nội dung toàn cầu với **Amazon CloudFront (CDN)** và lưu trữ giao diện Web hiện đại với **AWS Amplify**.
* Triển khai cơ chế **Origin Access Control (OAC)** để khóa chặt S3 Bucket gốc, buộc mọi người dùng chỉ được truy cập tài nguyên tĩnh thông qua CloudFront qua giao thức HTTPS.
* Quản lý chứng chỉ số SSL/TLS miễn phí với **AWS Certificate Manager (ACM)** để bảo vệ dữ liệu truyền tải (Encryption in Transit).
* Bảo vệ tầng ứng dụng Web và API trước các cuộc tấn công phổ biến (OWASP Top 10: SQL Injection, Cross-Site Scripting, HTTP Flood) bằng tường lửa ứng dụng **AWS WAF**.

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|------|-----------|-------------|----------------|---------------|
| 2 | **Phân phối nội dung với Amazon CloudFront & OAC:** <br> - Tìm hiểu cơ chế Caching tại Edge Locations, Origins, Behaviors và TTL trên Amazon CloudFront <br> - Khởi tạo CloudFront Distribution kết nối với Private S3 Bucket qua Origin Access Control (OAC) <br> - Cập nhật S3 Bucket Policy chỉ cho phép Service Principal `cloudfront.amazonaws.com` đọc dữ liệu | 09/11/2026 | 09/11/2026 | https://000058.awsstudygroup.com/ |
| 3 | **Mã hóa đường truyền với ACM & HTTPS:** <br> - Tìm hiểu quy trình cấp phát và gia hạn tự động chứng chỉ SSL/TLS trên AWS Certificate Manager (ACM) <br> - Cấu hình Viewer Protocol Policy trên CloudFront thành `Redirect HTTP to HTTPS` và thiết lập Security Policy tối thiểu `TLSv1.2_2021` | 10/11/2026 | 10/11/2026 | https://docs.aws.amazon.com/acm/ |
| 4 | **Tường lửa ứng dụng Web với AWS WAF:** <br> - Tìm hiểu kiến trúc AWS WAF: Web ACLs, Rule Groups, Managed Rules và Custom Rules <br> - Khởi tạo Web ACL gắn với CloudFront / API Gateway, kích hoạt bộ quy tắc `AWSManagedRulesCommonRuleSet` và `AWSManagedRulesSQLiRuleSet` | 11/11/2026 | 11/11/2026 | https://000026.awsstudygroup.com/ |
| 5 | **Cấu hình Rate-based Rule & Kiểm thử tấn công mô phỏng:** <br> - Thiết lập Rate-based Rule trên AWS WAF để tự động chặn IP gửi vượt ngưỡng request trong 5 phút (chống Brute-force / Layer 7 DDoS) <br> - Kiểm thử gửi request chứa chuỗi payload SQL Injection/XSS giả lập (`?id=1' OR '1'='1`) và xác nhận AWS WAF trả về mã lỗi `403 Forbidden` | 12/11/2026 | 12/11/2026 | https://000026.awsstudygroup.com/ |
| 6 | **Triển khai Frontend với AWS Amplify & Dọn dẹp:** <br> - Tìm hiểu quy trình CI/CD tự động build và host ứng dụng Web (Next.js / Static Web) trên AWS Amplify <br> - Phân tích WAF Sampled Requests, đánh giá hiệu quả lọc lưu lượng và dọn dẹp Web ACL, CloudFront Distribution thử nghiệm | 13/11/2026 | 13/11/2026 | https://000026.awsstudygroup.com/ |

### Kết quả đạt được trong tuần 9

* Triển khai thành công kiến trúc phân phối Web tĩnh an toàn qua **Amazon CloudFront** kết hợp **Origin Access Control (OAC)**, đảm bảo S3 Bucket luôn ẩn hoàn toàn khỏi Internet trực tiếp.
* Đảm bảo tiêu chuẩn bảo mật dữ liệu trên đường truyền (Encryption in Transit) bằng HTTPS và chính sách TLS 1.2+ nghiêm ngặt.
* Nắm vững cách cấu hình **AWS WAF** để phòng chống hiệu quả các lỗ hổng tầng ứng dụng theo chuẩn OWASP Top 10 (SQLi, XSS) cũng như ngăn chặn tấn công vét cạn bằng Rate-based Rules.
* Hiểu quy trình tích hợp và triển khai giao diện người dùng nhanh chóng với AWS Amplify.
