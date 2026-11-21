---
title: "Worklog Tuần 12"
date: 2024-01-01
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

### Mục tiêu tuần 12

* Thực hiện kiểm thử tổng thể End-to-End (E2E) cho toàn bộ bài thực hành Workshop (Kết nối riêng tư tới Amazon S3 từ VPC và On-premises với Gateway/Interface Endpoints & Route 53 Private DNS) và kiến trúc dự án.
* Rà soát toàn diện bảo mật tài khoản và tối ưu hóa chi phí bằng **AWS Cost Explorer** và **AWS Trusted Advisor**, đảm bảo không còn tài nguyên dư thừa phát sinh phí.
* Biên tập, chuẩn hóa song ngữ (Tiếng Việt & Tiếng Anh) toàn bộ 7 hạng mục trên trang báo cáo thực tập Hugo: Worklog, Proposal, Blogs Posted, Events Participated, Workshop, Self-evaluation và Feedback.
* Kiểm tra tự động hóa CI/CD bằng GitHub Actions và hoàn tất nộp báo cáo kỳ thực tập FCAJ.

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|------|-----------|-------------|----------------|---------------|
| 2 | **Kiểm thử End-to-End (E2E) bài Workshop:** <br> - Chạy lại toàn bộ quy trình bài Workshop từ bước khởi tạo CloudFormation, tạo S3 Gateway Endpoint, S3 Interface Endpoint, cấu hình Route 53 Inbound Resolver cho đến kiểm thử VPC Endpoint Policy <br> - Đối chiếu kết quả câu lệnh CLI (`aws s3 ls`, `dig`) và chụp ảnh màn hình minh họa sắc nét cho từng bước | 30/11/2026 | 30/11/2026 | https://000008.awsstudygroup.com/ |
| 3 | **Hoàn thiện tài liệu Workshop & Proposal:** <br> - Rà soát và biên tập chi tiết nội dung 6 phần của mục `5-Workshop` (Tổng quan, Chuẩn bị, S3 từ VPC, S3 từ On-premises, VPC Endpoint Policy, Dọn dẹp tài nguyên) trên cả bản Tiếng Việt và Tiếng Anh <br> - Kiểm tra lại toàn bộ sơ đồ kiến trúc và bảng dự toán ngân sách trong mục `2-Proposal` | 01/12/2026 | 01/12/2026 | https://cloudjourney.awsstudygroup.com/ |
| 4 | **Tổng hợp Blogs, Events & Tự đánh giá:** <br> - Cập nhật các bài blog kỹ thuật đã dịch/viết tại mục `3-BlogsPosted` và nhật ký các sự kiện AWS đã tham dự tại mục `4-EventParticipated` <br> - Viết bản tự đánh giá năng lực (`6-Self-evaluation`) và đóng góp ý kiến (`7-Feedback`) sau 3 tháng thực tập tại FCAJ | 02/12/2026 | 02/12/2026 | |
| 5 | **Kiểm toán chi phí & Dọn dẹp tài khoản AWS (Clean up):** <br> - Sử dụng AWS Cost Explorer và Bills để kiểm tra chi tiết từng Region, đảm bảo đã xóa toàn bộ VPC Endpoints, Route 53 Resolver Endpoints, CloudFormation Stacks, S3 Buckets và Elastic IPs không còn sử dụng | 03/12/2026 | 03/12/2026 | https://000007.awsstudygroup.com/ |
| 6 | **Triển khai GitHub Pages & Nghiệm thu báo cáo:** <br> - Kiểm tra build Hugo cục bộ và đẩy mã nguồn hoàn chỉnh lên GitHub repository (`Ocean-ng.github.io`) <br> - Kiểm tra giao diện, đường dẫn ảnh và chuyển đổi song ngữ VI/EN trên trang GitHub Pages chính thức, hoàn tất nộp báo cáo thực tập | 04/12/2026 | 04/12/2026 | https://ocean-ng.github.io/fcaj-worklogs/ |

### Kết quả đạt được trong tuần 12

* Kiểm chứng thành công 100% các bước kỹ thuật trong bài **Workshop** về bảo mật kết nối riêng tư tới Amazon S3 qua Gateway Endpoint, Interface Endpoint (PrivateLink), Route 53 Hybrid DNS và Endpoint Policies.
* Đảm bảo tài khoản AWS sạch sẽ, an toàn và không còn bất kỳ tài nguyên ngầm nào gây phát sinh chi phí sau khi kết thúc thực tập.
* Hoàn thiện trang web báo cáo thực tập **First Cloud AI Journey** song ngữ (Tiếng Việt – Tiếng Anh) chỉn chu, đầy đủ 7 chuyên mục trên nền tảng Hugo và GitHub Pages.
* Hệ thống hóa toàn bộ kiến thức về hạ tầng đám mây và an toàn thông tin trên AWS, sẵn sàng cho buổi bảo vệ và định hướng phát triển sự nghiệp Cloud Security Engineer.
