---
title: "Worklog Tuần 6"
date: 2024-01-01
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu tuần 6

* Khởi tạo cấu trúc mã nguồn Frontend (`React + Vite`) cho dự án **SecureTable**, định hình bố cục giao diện tối giản, dễ thao tác trên cả điện thoại (cho khách quét QR) và máy tính bảng/laptop (cho nhân viên).
* Xây dựng hệ thống chuyển đổi song ngữ **Tiếng Việt - Tiếng Anh (`VI / EN`)** và bộ định tuyến trang cho cổng khách hàng và cổng nội bộ nhân viên.
* Nghiên cứu cách triển khai website tĩnh an toàn lên **Amazon S3 Bucket riêng tư** phân phối qua **Amazon CloudFront** với **Origin Access Control (OAC)** và **CloudFront Free Plan**.

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|------|-----------|-------------|----------------|---------------|
| 2 | **Thiết kế Sitemap & Wireframe giao diện SecureTable:** <br> - Phác thảo bố cục màn hình cho khách hàng (Trang chủ giới thiệu quán, Thực đơn phân nhóm, Giỏ gọi món tại bàn) và cổng nhân viên POS <br> - Lựa chọn tông màu ấm áp, trực quan để khách dễ đọc thực đơn trên màn hình di động khi quét mã QR | 19/10/2026 | 19/10/2026 | https://cloudjourney.awsstudygroup.com/ |
| 3 | **Khởi tạo dự án Frontend React + Vite & Định tuyến:** <br> - Khởi tạo cấu trúc thư mục `frontend/` (`src/components`, `src/pages`, `src/services`, `public/`) <br> - Thiết lập bộ định tuyến tách biệt giao diện khách (`#/`, `#/menu`) và cổng đăng nhập nhân viên (`#/staff`) để tiện triển khai dạng SPA trên S3/CloudFront | 20/10/2026 | 20/10/2026 | https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/GettingStarted.SimpleDistribution.html |
| 4 | **Xây dựng bộ từ điển Song ngữ Việt - Anh (`i18n`):** <br> - Thiết kế module chuyển đổi ngôn ngữ tức thời `VI / EN` cho toàn bộ nhãn nút bấm, trạng thái bàn, trạng thái món ăn và thông báo lỗi trên giao diện | 21/10/2026 | 21/10/2026 | https://docs.aws.amazon.com/wellarchitected/latest/serverless-applications-lens/web-applications.html |
| 5 | **Nghiên cứu lưu trữ Frontend trên S3 + CloudFront (OAC):** <br> - Đọc tài liệu AWS về cách host SPA mà **không bật S3 Static Website Hosting công khai**: giữ nguyên **Block all public access** trên S3 và cấp quyền đọc cho CloudFront thông qua **Origin Access Control (SigV4)** | 22/10/2026 | 22/10/2026 | https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/private-content-restricting-access-to-s3.html |
| 6 | **Tìm hiểu CloudFront Free Plan & Hợp đồng biến môi trường:** <br> - Tìm hiểu phạm vi tính năng miễn phí của **CloudFront Free Plan** (kèm AWS WAF cơ bản) <br> - Thống nhất với bạn làm Backend/Infra danh sách biến cấu hình `VITE_*` (`VITE_API_GATEWAY_URL`, `VITE_COGNITO_USER_POOL_ID`, `VITE_COGNITO_CLIENT_ID`) trong `.env.example` | 23/10/2026 | 23/10/2026 | https://000058.awsstudygroup.com/ |

### Kết quả đạt được trong tuần 6

* Dựng xong bộ khung dự án Frontend (`React + Vite`) gọn nhẹ, hỗ trợ đầy đủ 2 ngôn ngữ Tiếng Việt và Tiếng Anh.
* Thống nhất chuẩn biến môi trường kết nối AWS với các thành viên phụ trách Backend và Hạ tầng trong nhóm, tránh xung đột mã nguồn trên Git.
* Nắm vững quy trình bảo mật S3 Origin bằng **Origin Access Control (OAC)** và cấu hình `Default root object: index.html` trên CloudFront để chuẩn bị đưa giao diện lên AWS.
