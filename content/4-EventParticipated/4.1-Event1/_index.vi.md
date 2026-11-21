---
title: "Event 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# Bài thu hoạch “GenAI-powered App-DB Modernization Workshop”

### 1. Thông tin & Mục đích của sự kiện

* **Thời gian:** 09:00 – 12:30, ngày 23/09/2026
* **Địa điểm:** Văn phòng AWS Việt Nam – Tầng 26, Tòa nhà Bitexco Financial Tower, Quận 1, TP.HCM
* **Mục tiêu cốt lõi:**
  - Chia sẻ các phương pháp thực hành tốt nhất (Best Practices) trong hiện đại hóa ứng dụng và cơ sở dữ liệu trên đám mây.
  - Giới thiệu phương pháp thiết kế **Domain-Driven Design (DDD)** và kiến trúc hướng sự kiện (**Event-Driven Architecture**).
  - Hướng dẫn tiêu chí lựa chọn dịch vụ Compute và Database phù hợp cho từng giai đoạn mở rộng.
  - Trình diễn cách ứng dụng công cụ AI **Amazon Q Developer** vào toàn bộ vòng đời phát triển và bảo mật phần mềm (SDLC).

### 2. Danh sách diễn giả

* **Jignesh Shah** — Director, Open Source Databases, AWS
* **Erica Liu** — Sr. GTM Specialist, Application Modernization, AWS
* **Fabrianne Effendi** — Associate Specialist Solutions Architect, Serverless, AWS

### 3. Nội dung chuyên môn nổi bật

#### Thách thức của kiến trúc Monolith truyền thống
* Chu kỳ phát hành tính năng mới kéo dài, dễ gây gián đoạn toàn hệ thống khi một thành phần gặp lỗi.
* Khó mở rộng độc lập từng phân hệ có tải cao, dẫn đến lãng phí tài nguyên hạ tầng.
* Rủi ro bảo mật cao khi toàn bộ ứng dụng chia sẻ chung một cơ sở dữ liệu và một phạm vi quyền truy cập rộng.

#### Chuyển dịch sang Microservices & Event-Driven Architecture
* Phân tách hệ thống thành các dịch vụ độc lập, giao tiếp bất đồng bộ qua sự kiện với 3 thành phần trọng tâm:
  - **Queue Management (Amazon SQS):** Đệm lưu lượng và xử lý tác vụ bất đồng bộ, chống quá tải hệ thống đích.
  - **Event Routing & Pub/Sub (Amazon EventBridge / SNS):** Giảm sự phụ thuộc chặt (Loose Coupling) giữa các dịch vụ.
  - **Caching Strategy (Amazon ElastiCache):** Tăng tốc độ phản hồi và giảm áp lực truy vấn trực tiếp vào Database.

#### Phương pháp Domain-Driven Design (DDD)
* Quy trình 4 bước: Xác định Domain Events → Sắp xếp theo dòng thời gian (Event Storming) → Xác định Actors & Commands → Phân định ranh giới ngữ cảnh (**Bounded Contexts**).
* Giúp đội ngũ kỹ thuật và nghiệp vụ thống nhất ngôn ngữ chung (**Ubiquitous Language**) trước khi viết code hay thiết kế bảng dữ liệu.

#### Lộ trình tiến hóa tầng Compute & Amazon Q Developer
* So sánh mô hình chia sẻ trách nhiệm (**Shared Responsibility Model**) khi dịch chuyển từ Amazon EC2 → Amazon ECS → AWS Fargate → **AWS Lambda**.
* Ứng dụng **Amazon Q Developer** để tự động hóa rà soát lỗ hổng bảo mật trong mã nguồn (Security Scanning), nâng cấp phiên bản ngôn ngữ (Java/.NET Transformation) và sinh tài liệu kỹ thuật.

### 4. Bài học rút ra & Ứng dụng vào kỳ thực tập

* **Tư duy thiết kế hướng sự kiện và Serverless:** Hiểu rõ lý do nên ưu tiên **AWS Lambda**, **API Gateway** và **EventBridge** cho các hệ thống cần tối ưu chi phí vận hành và tự động co giãn — kiến thức này được mình áp dụng trực tiếp vào thiết kế kiến trúc trong mục **Proposal** và thực hành ở **Tuần 7** và **Tuần 10**.
* **Bảo mật theo từng Bounded Context:** Việc tách nhỏ dịch vụ đi kèm với tách biệt IAM Execution Role cho từng hàm Lambda giúp hạn chế tối đa phạm vi ảnh hưởng (Blast Radius) nếu xảy ra sự cố an ninh.
* **Tận dụng AI có kiểm soát:** Biết cách sử dụng các công cụ hỗ trợ lập trình và kiểm tra bảo mật mã nguồn để tăng tốc độ viết CloudFormation template và IAM JSON Policy chính xác hơn.
