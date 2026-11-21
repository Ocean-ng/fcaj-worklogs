---
title: "Bản đề xuất"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# IoT Weather Platform for Lab Research  
## Giải pháp AWS Serverless hợp nhất cho giám sát thời tiết thời gian thực  

### 1. Tóm tắt điều hành  
IoT Weather Platform được thiết kế dành cho nhóm nghiên cứu *ITea Lab* tại TP. Hồ Chí Minh nhằm nâng cao khả năng thu thập, bảo mật và phân tích dữ liệu thời tiết. Nền tảng hỗ trợ tối đa 5 trạm thời tiết, có khả năng mở rộng lên 10–15 trạm, sử dụng thiết bị biên Raspberry Pi kết hợp cảm biến ESP32 để truyền dữ liệu qua giao thức MQTT có mã hóa TLS. Nền tảng tận dụng các dịch vụ AWS Serverless để cung cấp giám sát thời gian thực, phân tích dự đoán và tối ưu chi phí, với quyền truy cập giới hạn an toàn cho các thành viên phòng lab thông qua Amazon Cognito.  

### 2. Tuyên bố vấn đề  
*Vấn đề hiện tại*  
Các trạm thời tiết hiện tại yêu cầu thu thập dữ liệu thủ công, khó quản lý và thiếu cơ chế kiểm soát truy cập tập trung khi mở rộng nhiều trạm. Chưa có hệ thống tập trung cho dữ liệu hoặc phân tích thời gian thực, trong khi các nền tảng thương mại bên thứ ba thường tốn kém và phức tạp.  

*Giải pháp*  
Nền tảng sử dụng AWS IoT Core để tiếp nhận dữ liệu MQTT an toàn, AWS Lambda và Amazon API Gateway để xử lý, Amazon S3 để lưu trữ (bao gồm Data Lake), cùng AWS Glue Crawlers và các tác vụ ETL để trích xuất, chuyển đổi, tải dữ liệu từ S3 Data Lake sang S3 Bucket phân tích. AWS Amplify với Next.js cung cấp giao diện web trực quan, và Amazon Cognito đảm bảo xác thực người dùng chặt chẽ. Các tính năng chính bao gồm bảng điều khiển thời gian thực, phân tích xu hướng, bảo mật dữ liệu đầu-cuối và chi phí vận hành cực thấp.  

*Lợi ích và hoàn vốn đầu tư (ROI)*  
Giải pháp tạo nền tảng vững chắc để phòng lab phát triển hệ thống IoT quy mô lớn hơn, đồng thời cung cấp nguồn dữ liệu sạch phục vụ huấn luyện mô hình AI. Hệ thống loại bỏ thao tác tổng hợp báo cáo thủ công, đơn giản hóa bảo trì và nâng cao độ tin cậy dữ liệu. Chi phí vận hành hàng tháng ước tính khoảng 0,70 USD (theo AWS Pricing Calculator), tương đương 8,40 USD cho 12 tháng. Thời gian hoàn vốn dự kiến từ 6–12 tháng nhờ tiết kiệm đáng kể thời gian vận hành thủ công.  

### 3. Kiến trúc giải pháp  
Nền tảng áp dụng kiến trúc AWS Serverless để quản lý dữ liệu từ 5 trạm dựa trên Raspberry Pi (mở rộng lên 15 trạm). Dữ liệu được tiếp nhận qua AWS IoT Core, lưu trữ trong S3 Data Lake và xử lý bởi AWS Glue Crawlers cùng ETL jobs để chuyển đổi và tải vào S3 Bucket phục vụ phân tích. AWS Lambda và Amazon API Gateway đảm nhận tầng xử lý API, trong khi AWS Amplify lưu trữ bảng điều khiển Next.js được bảo vệ bởi Amazon Cognito.  

![IoT Weather Station Architecture](/images/2-Proposal/edge_architecture.jpeg)

![IoT Weather Platform Architecture](/images/2-Proposal/platform_architecture.jpeg)

*Dịch vụ AWS sử dụng*  
- **AWS IoT Core**: Tiếp nhận dữ liệu MQTT an toàn từ 5 trạm (mở rộng lên 15 trạm).  
- **AWS Lambda**: Xử lý dữ liệu sự kiện và kích hoạt Glue jobs.  
- **Amazon API Gateway**: Cung cấp RESTful/HTTP API giao tiếp với ứng dụng web.  
- **Amazon S3**: Lưu trữ dữ liệu thô (Data Lake) và dữ liệu đã qua xử lý (2 bucket riêng biệt, bật Block Public Access và mã hóa SSE).  
- **AWS Glue**: Crawlers lập chỉ mục dữ liệu, ETL jobs chuyển đổi và chuẩn hóa dữ liệu.  
- **AWS Amplify**: Lưu trữ và triển khai CI/CD cho giao diện web Next.js.  
- **Amazon Cognito**: Quản lý định danh và phân quyền truy cập (JWT) cho thành viên phòng lab.  

*Thiết kế thành phần*  
- **Thiết bị biên (Edge Devices)**: Raspberry Pi thu thập và tiền xử lý dữ liệu cảm biến ESP32, gửi tới AWS IoT Core.  
- **Tiếp nhận dữ liệu (Data Ingestion)**: AWS IoT Core xác thực chứng chỉ thiết bị X.509 và nhận bản tin MQTT.  
- **Lưu trữ dữ liệu (Data Storage)**: Dữ liệu thô lưu trong S3 Data Lake; dữ liệu sạch lưu ở S3 Analytics Bucket.  
- **Xử lý dữ liệu (Data Processing)**: AWS Glue Crawlers cập nhật Data Catalog; ETL jobs chuyển đổi dữ liệu phục vụ truy vấn.  
- **Giao diện Web (Web Interface)**: AWS Amplify vận hành ứng dụng Next.js hiển thị biểu đồ thời gian thực.  
- **Quản lý người dùng (User Management)**: Amazon Cognito User Pool kiểm soát đăng nhập cho 5 tài khoản nghiên cứu viên.  

### 4. Triển khai kỹ thuật  
*Các giai đoạn triển khai*  
Dự án gồm 2 phần — thiết lập trạm thời tiết biên và xây dựng nền tảng đám mây AWS — trải qua 4 giai đoạn:  
1. **Nghiên cứu và thiết kế kiến trúc**: Khảo sát kết nối Raspberry Pi – ESP32 và thiết kế kiến trúc AWS Serverless theo chuẩn Well-Architected.  
2. **Ước tính chi phí và đánh giá khả thi**: Sử dụng AWS Pricing Calculator để tính toán chi phí theo tải thực tế (Tháng 1).  
3. **Tinh chỉnh kiến trúc & Bảo mật**: Tối ưu hóa tần suất gọi Lambda, thiết lập IAM Roles theo nguyên tắc Least Privilege và bảo mật S3/Cognito (Tháng 2).  
4. **Phát triển, kiểm thử và triển khai**: Lập trình thiết bị biên, cấu hình dịch vụ AWS với SDK/CloudFormation, triển khai Next.js trên Amplify và kiểm thử End-to-End (Tháng 2–3).  

*Yêu cầu kỹ thuật*  
- **Trạm thời tiết biên**: Cảm biến (nhiệt độ, độ ẩm, lượng mưa, tốc độ gió), vi điều khiển ESP32, Raspberry Pi chạy Docker để lọc nhiễu dữ liệu và truyền ~1 MB/ngày/trạm qua MQTT over TLS.  
- **Nền tảng đám mây**: Sử dụng AWS Amplify (Next.js), AWS Lambda, AWS Glue (ETL), Amazon S3 (2 buckets), AWS IoT Core (Rules & Policies) và Amazon Cognito.  

### 5. Lộ trình & Mốc triển khai  
- **Giai đoạn chuẩn bị**: Khảo sát thiết bị trạm cũ và thống nhất yêu cầu hệ thống.  
- **Giai đoạn thực tập (3 tháng / 12 tuần)**:  
  - *Tháng 1 (Tuần 1–4)*: Nắm vững nền tảng AWS (IAM, VPC, EC2, S3, RDS) và chuẩn bị thiết bị.  
  - *Tháng 2 (Tuần 5–8)*: Thiết kế kiến trúc, triển khai kết nối mạng riêng tư, xây dựng Serverless API, Cognito và bảo mật khóa KMS/Secrets.  
  - *Tháng 3 (Tuần 9–12)*: Bảo mật tầng ứng dụng (CloudFront, WAF), thiết lập giám sát (CloudWatch, CloudTrail), kiểm thử E2E và nghiệm thu.  

### 6. Ước tính ngân sách  
Chi tiết dự toán chi phí có thể tra cứu trên [AWS Pricing Calculator](https://calculator.aws/#/estimate?id=621f38b12a1ef026842ba2ddfe46ff936ed4ab01).

*Chi phí hạ tầng AWS ước tính hàng tháng:*  
- **AWS Lambda**: 0,00 USD/tháng (1.000 requests, 512 MB bộ nhớ - thuộc ngưỡng Free Tier).  
- **Amazon S3 Standard**: 0,15 USD/tháng (6 GB lưu trữ, 2.100 requests).  
- **Data Transfer**: 0,02 USD/tháng (1 GB inbound, 1 GB outbound).  
- **AWS Amplify**: 0,35 USD/tháng (256 MB, thời gian phản hồi 500 ms).  
- **Amazon API Gateway**: 0,01 USD/tháng (2.000 requests).  
- **AWS Glue ETL Jobs**: 0,02 USD/tháng (2 DPU).  
- **AWS Glue Crawlers**: 0,07 USD/tháng (1 crawler).  
- **AWS IoT Core (MQTT)**: 0,08 USD/tháng (5 thiết bị, 45.000 bản tin).  

**Tổng chi phí AWS**: **~0,70 USD/tháng** (~8,40 USD/12 tháng).  
- **Chi phí phần cứng**: 265 USD chi phí đầu tư ban đầu một lần (Raspberry Pi 5 và bộ cảm biến).  

### 7. Đánh giá rủi ro  
*Ma trận rủi ro*  
- **Gián đoạn kết nối mạng tại trạm**: Ảnh hưởng trung bình, xác suất trung bình.  
- **Lỗi cảm biến phần cứng**: Ảnh hưởng cao, xác suất thấp.  
- **Phát sinh chi phí vượt dự toán**: Ảnh hưởng trung bình, xác suất thấp.  

*Chiến lược giảm thiểu*  
- **Mạng**: Lưu đệm (Local Buffering) trên Raspberry Pi bằng Docker container và đồng bộ lại khi có mạng.  
- **Cảm biến**: Kiểm tra định kỳ, chuẩn bị linh kiện cảm biến dự phòng.  
- **Chi phí & Bảo mật**: Thiết lập cảnh báo AWS Budgets, giới hạn Rate Limiting trên API Gateway và áp dụng IAM Least Privilege.  

*Kế hoạch dự phòng*  
- Xuất dữ liệu cục bộ từ thẻ nhớ Raspberry Pi nếu đường truyền Internet tại trạm bị gián đoạn dài ngày.  
- Sử dụng AWS CloudFormation để khôi phục hoặc thu hồi nhanh cấu hình hạ tầng khi cần thiết.  

### 8. Kết quả kỳ vọng  
- **Cải tiến kỹ thuật**: Tự động hóa hoàn toàn luồng thu thập, bảo mật và phân tích dữ liệu thời tiết theo thời gian thực, sẵn sàng mở rộng lên 10–15 trạm.  
- **Giá trị dài hạn**: Xây dựng kho dữ liệu chuẩn hóa phục vụ nghiên cứu AI/Machine Learning và làm mô hình tham chiếu kiến trúc AWS Serverless an toàn cho các dự án tiếp theo.
