---
title: "Blog 4"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 3.4. </b> "
---

# Bảo vệ Origin phía sau Amazon CloudFront bằng AWS WAF, OAC và Custom Header xoay vòng tự động

* **Chủ đề:** Edge & Origin Security trên AWS
* **Tác giả:** Thúy Nga

---

Khi triển khai ứng dụng web trên AWS, nhiều hệ thống đặt **Amazon CloudFront** và **AWS WAF** ở phía trước để tăng tốc phân phối nội dung và lọc các request độc hại (SQL Injection, XSS, HTTP Flood). Tuy nhiên, một lỗ hổng cấu hình rất phổ biến là **chỉ bật bảo vệ ở CloudFront nhưng lại để lộ đường dẫn trực tiếp vào Origin phía sau** (như S3 Bucket, Application Load Balancer hoặc API Gateway). Nếu kẻ tấn công tìm ra tên miền hoặc IP của Origin, họ có thể gửi request đi vòng qua CloudFront (Origin Bypass) và vô hiệu hóa hoàn toàn lớp tường lửa AWS WAF ở biên.

![Kiến trúc bảo vệ Origin phía sau Amazon CloudFront bằng AWS WAF và Secrets Manager (Nguồn: AWS Security Blog)](/images/3-BlogsPosted/blog4-cloudfront-waf-origin.png)

### 1. Với Origin là Amazon S3: Dùng Origin Access Control (OAC)

Khi lưu trữ giao diện web tĩnh trên **Amazon S3**, tuyệt đối không bật chế độ Public Bucket. Thay vào đó:
* Bật đầy đủ 4 tùy chọn **S3 Block Public Access** trên bucket.
* Cấu hình **Origin Access Control (OAC)** trên CloudFront để CloudFront ký xác thực từng request gọi xuống S3 bằng giao thức **AWS Signature Version 4 (SigV4)** (hỗ trợ tốt cả bucket mã hóa bằng AWS KMS).
* Trên **S3 Bucket Policy**, chỉ cấp quyền `s3:GetObject` cho Service Principal `cloudfront.amazonaws.com` kèm điều kiện `AWS:SourceArn` khớp đúng ARN của CloudFront Distribution.

### 2. Với Origin là ALB hoặc API: Kết hợp AWS WAF và Custom Header xoay vòng tự động

Với các Origin động như **Application Load Balancer (ALB)** nằm ở Public Subnet, ta cần đảm bảo ALB chỉ chấp nhận lưu lượng đi qua đúng CloudFront Distribution của mình theo kiến trúc trên sơ đồ:
1. **Lớp lọc đầu tiên tại Biên (Edge):** Người dùng gửi request tới **Amazon CloudFront**, tại đây **AWS WAF** kiểm tra và chặn sớm các lưu lượng tấn công tầng ứng dụng.
2. **Đính kèm khóa bí mật trên Header (`X-Origin-Verify`):** Khi chuyển tiếp request hợp lệ về Origin, CloudFront tự động chèn thêm một Custom HTTP Header tên là `X-Origin-Verify` mang giá trị chuỗi bí mật.
3. **Xác thực tại Origin:** Một **AWS WAF** thứ hai gắn trên **Origin ALB** kiểm tra header `X-Origin-Verify`. Mọi request đi thẳng từ Internet vào ALB mà không có header này (hoặc sai giá trị) sẽ lập tức bị chặn (`403 Forbidden`). Đồng thời có thể kết hợp thêm AWS Managed Prefix List của CloudFront trên Security Group của ALB để giới hạn ngay từ tầng mạng.
4. **Xoay vòng bí mật tự động (Auto Secret Rotation):** Để tránh rủi ro lộ giá trị header tĩnh theo thời gian, **AWS Secrets Manager** kết hợp hàm **AWS Lambda** tự động sinh mã mới định kỳ và đồng bộ cập nhật trên cả CloudFront lẫn WAF ACL tại Origin mà không gây gián đoạn dịch vụ (nhờ cơ chế `AWSCURRENT` / `AWSPENDING`).

### Checklist khi thiết kế bảo mật tầng Web trên AWS

* Kiểm tra xem người dùng bên ngoài có thể gọi trực tiếp vào S3 URL, ALB DNS name hoặc API Origin mà không đi qua CloudFront hay không.
* Dùng **Origin Access Control (OAC)** thay cho cơ chế OAI cũ khi kết nối CloudFront với Amazon S3.
* Với Origin là ALB, kết hợp giới hạn Security Group bằng CloudFront Managed Prefix List và kiểm tra header bí mật `X-Origin-Verify` được xoay vòng định kỳ qua Secrets Manager.
* Luôn cấu hình chuyển hướng `Redirect HTTP to HTTPS` trên CloudFront để mã hóa toàn bộ dữ liệu truyền tải.

### Tài liệu tham khảo

1. [How to enhance Amazon CloudFront origin security with AWS WAF and AWS Secrets Manager – AWS Security Blog](https://aws.amazon.com/blogs/security/how-to-enhance-amazon-cloudfront-origin-security-with-aws-waf-and-aws-secrets-manager/)
2. [Restricting access to an Amazon S3 origin (Origin Access Control) – Amazon CloudFront Developer Guide](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/private-content-restricting-access-to-s3.html)
3. [Restricting access to Application Load Balancers – Amazon CloudFront Developer Guide](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/restrict-access-to-load-balancer.html)
4. [AWS WAF Developer Guide](https://docs.aws.amazon.com/waf/latest/developerguide/waf-chapter.html)

`#AWS` `#CloudSecurity` `#CloudFront` `#AWSWAF`
