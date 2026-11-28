---
title: "Worklog Tuần 11"
date: 2024-01-01
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Mục tiêu tuần 11

* Đóng gói bản build Frontend của **SecureTable** và triển khai lên **Amazon S3 Bucket riêng tư** phân phối qua **Amazon CloudFront** (bật **Origin Access Control - OAC** và **AWS WAF** trong gói CloudFront Free Plan) tại Region `ap-southeast-1`.
* Phối hợp cùng toàn nhóm chạy kiểm thử tích hợp End-to-End (E2E) nối thông từ giao diện CloudFront xuống API Gateway, Cognito, Lambda và DynamoDB.
* Xây dựng kịch bản chi tiết cho buổi **quay Demo sản phẩm của nhóm (diễn ra vào cuối tuần 28–29/11/2026)** và hoàn thiện trang báo cáo cá nhân trên GitHub Pages.

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|------|-----------|-------------|----------------|---------------|
| 2 | **Đóng gói bản Build Frontend & Triển khai lên Amazon S3:** <br> - Cập nhật cấu hình kết nối môi trường AWS thật (`ap-southeast-1`) và xuất bản build tĩnh của Frontend <br> - Tạo S3 Bucket riêng tư (giữ nguyên `ACLs disabled` và `Block all public access`) và tải các tệp giao diện (`index.html` ở thư mục gốc) lên S3 | 23/11/2026 | 23/11/2026 | https://docs.aws.amazon.com/AmazonS3/latest/userguide/access-control-block-public-access.html |
| 3 | **Cấu hình Amazon CloudFront (OAC & AWS WAF):** <br> - Khởi tạo CloudFront Distribution sử dụng **CloudFront Free Plan**, bật **AWS WAF** và kết nối tới S3 Origin bằng **Origin Access Control (Sign requests)** <br> - Áp dụng S3 Bucket Policy cho CloudFront, cấu hình `Default root object: index.html` và kiểm tra truy cập HTTPS qua domain `cloudfront.net` | 24/11/2026 | 24/11/2026 | https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/private-content-restricting-access-to-s3.html |
| 4 | **Kiểm thử tích hợp toàn luồng (E2E) cùng các thành viên trong nhóm:** <br> - Phối hợp test thực tế luồng nghiệp vụ từ giao diện CloudFront: Reception mở bàn & hóa đơn → Guest quét QR xem thực đơn và gọi món → Kitchen hoàn tất/từ chối món → Inventory kiểm tra tồn kho → Reception chốt hóa đơn → Admin xem doanh thu & Audit Logs | 25/11/2026 | 25/11/2026 | https://docs.aws.amazon.com/wellarchitected/latest/serverless-applications-lens/opex-testing.html |
| 5 | **Đóng góp tài liệu triển khai Frontend cho Workshop nhóm:** <br> - Tổng hợp hình ảnh chụp màn hình cấu hình S3, CloudFront OAC và các lưu ý kỹ thuật để hoàn thiện phần hướng dẫn **Triển khai Frontend (`5.3-Frontend-dev`)** trong tài liệu Workshop chung của nhóm | 26/11/2026 | 26/11/2026 | https://github.com/thienluhoan/fcj-workshop-template |
| 6 | **Lên kịch bản quay Demo sản phẩm (28–29/11) & Cập nhật trang Báo cáo:** <br> - Soạn kịch bản phân cảnh chi tiết, chuẩn bị dữ liệu mẫu thực đơn/nguyên liệu để mình trực tiếp thực hiện **buổi Demo và quay video minh chứng sản phẩm SecureTable cho nhóm vào ngày 28–29/11/2026** <br> - Đồng bộ Proposal, bộ tài liệu Workshop (`5.1` - `5.10`), Blogs, Events và Worklog lên trang báo cáo GitHub Pages cá nhân | 27/11/2026 | 27/11/2026 | https://docs.aws.amazon.com/waf/latest/developerguide/waf-chapter.html |

### Kết quả đạt được trong tuần 11

* Triển khai thành công giao diện **SecureTable** hoạt động thực tế trên **Amazon CloudFront + Private S3 Bucket (OAC)** qua kết nối HTTPS an toàn.
* Kiểm chứng sự phối hợp trơn tru giữa Frontend của mình với hệ thống API Gateway, Cognito, Lambda và DynamoDB do các thành viên trong nhóm xây dựng.
* Hoàn tất kịch bản và dữ liệu chuẩn bị cho buổi **Demo & quay video minh chứng sản phẩm vào ngày 28–29/11/2026**.
