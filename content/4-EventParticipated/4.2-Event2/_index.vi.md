---
title: "Event 2"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---

# Bài thu hoạch “AWS Cloud Security & Generative AI Builders Day”

### 1. Thông tin & Mục đích của sự kiện

* **Thời gian:** 13:30 – 17:00, ngày 28/10/2026
* **Địa điểm:** Văn phòng AWS Việt Nam – Tầng 26, Tòa nhà Bitexco Financial Tower, Quận 1, TP.HCM
* **Mục tiêu cốt lõi:**
  - Hệ thống hóa các nguyên tắc thiết kế bảo mật đám mây theo trụ cột **Security Pillar** của **AWS Well-Architected Framework**.
  - Hướng dẫn xây dựng vành đai bảo vệ dữ liệu (**Data Perimeter**) bằng IAM, VPC Endpoints (AWS PrivateLink) và KMS.
  - Trình diễn quy trình tự động hóa phát hiện mối đe dọa và quản trị tư thế bảo mật với **Amazon GuardDuty** và **AWS Security Hub**.
  - Giới thiệu các cơ chế kiểm soát an toàn dữ liệu và quyền riêng tư khi xây dựng ứng dụng Generative AI với **Amazon Bedrock Guardrails**.

### 2. Nội dung chuyên môn nổi bật

#### Bảo mật theo chiều sâu (Defense in Depth) trên AWS
* Không dựa vào một lớp tường lửa duy nhất mà thiết lập bảo vệ ở mọi tầng:
  - **Tầng Biên & Ứng dụng:** Amazon CloudFront, AWS Shield và AWS WAF lọc các cuộc tấn công OWASP Top 10 và DDoS.
  - **Tầng Mạng VPC:** Phân tách Public/Private Subnets, kiểm soát gói tin bằng Security Groups (Stateful) và Network ACLs (Stateless).
  - **Tầng Định danh & Dữ liệu:** Áp dụng IAM Least Privilege, sử dụng thông tin xác thực tạm thời (IAM Roles / STS) thay cho Long-term Access Keys và mã hóa dữ liệu bằng AWS KMS.

#### Thiết lập Vành đai dữ liệu (Data Perimeter) với VPC Endpoints
* Phân tích kịch bản ngăn chặn rò rỉ dữ liệu (Data Exfiltration): ngay cả khi thông tin xác thực IAM bị lộ, kẻ tấn công bên ngoài cũng không thể truy cập vào S3 Bucket của doanh nghiệp nếu Bucket Policy kiểm tra điều kiện `aws:SourceVpce` hoặc `aws:SourceVpc`.
* Minh họa thực tế cách kết hợp **S3 Gateway Endpoint**, **S3 Interface Endpoint** và **VPC Endpoint Policy** cho mô hình mạng Hybrid Cloud.

#### Tự động hóa SecOps với GuardDuty, Security Hub & EventBridge
* Cách **Amazon GuardDuty** phát hiện bất thường từ CloudTrail, VPC Flow Logs và DNS Logs mà không cần triển khai Agent.
* Sử dụng **AWS Security Hub** để gom nhóm cảnh báo và đối chiếu tự động với bộ tiêu chuẩn **CIS AWS Foundations Benchmark**.
* Xây dựng luồng phản ứng tự động (Automated Playbook): `GuardDuty Finding` → `Amazon EventBridge` → `AWS Lambda` tự động cách ly Security Group và gửi thông báo qua `Amazon SNS`.

#### Bảo mật ứng dụng Generative AI trên Amazon Bedrock
* Dữ liệu prompt và kết quả đầu ra của khách hàng trên Amazon Bedrock không bao giờ được dùng để huấn luyện lại mô hình nền tảng gốc.
* Sử dụng **VPC Interface Endpoint (PrivateLink)** để gọi API Amazon Bedrock hoàn toàn qua mạng nội bộ và dùng **Bedrock Guardrails** để lọc thông tin nhạy cảm (PII Redaction) cũng như ngăn chặn Prompt Injection.

### 3. Bài học rút ra & Ứng dụng vào kỳ thực tập

* **Củng cố trực tiếp cho bài Workshop của kỳ thực tập:** Phần trình bày về **Data Perimeter** và **VPC Endpoints** tại sự kiện đã giúp mình hiểu sâu hơn bản chất của điều kiện `aws:SourceVpce` và kiến trúc **Route 53 Inbound Resolver**, từ đó hoàn thiện mạch lạc chương 4 và chương 5 của mục **5-Workshop**.
* **Định hình rõ lộ trình nghề nghiệp ngành An toàn thông tin:** Sự kiện giúp mình thấy rõ sự giao thoa giữa **An toàn thông tin truyền thống** và **Cloud Security / DevSecOps**, nơi mọi chính sách bảo mật, kiểm toán tuân thủ và phản ứng sự cố đều được định nghĩa và tự động hóa bằng mã nguồn (Policy as Code & Automated Remediation).
* **Thực hành ngay trên tài khoản lab cá nhân:** Ngay sau sự kiện, mình đã áp dụng kiến thức học được vào các bài thực hành ở **Tuần 8 (KMS & Secrets)**, **Tuần 9 (CloudFront & WAF)**, **Tuần 10 (CloudTrail & Flow Logs)** và **Tuần 11 (GuardDuty & Security Hub)**.
