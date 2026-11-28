---
title: "Worklog Tuần 10"
date: 2024-01-01
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Mục tiêu tuần 10

* Nghiên cứu hệ thống và tổng hợp tài liệu chính thức của AWS về **Shared Responsibility Model**, **Bảo mật lưu trữ Amazon S3**, **Quản lý định danh IAM & AWS CloudTrail** để viết bài chia sẻ kiến thức lên cộng đồng **AWS Study Group VN**.
* Nâng cấp toàn diện giao diện và hiệu ứng chuyển động (UI/UX & Animations) cho Frontend **SecureTable** theo phong cách nhà hàng hiện đại, tối giản và mượt mà.
* Rà soát lại toàn bộ mã nguồn `frontend/`, sửa lỗi hiển thị hình ảnh và đồng bộ chặt chẽ logic gọi API khớp với đặc tả Backend của nhóm.

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|------|-----------|-------------|----------------|---------------|
| 2 | **Nghiên cứu sâu Shared Responsibility Model & IAM Security:** <br> - Đọc tài liệu AWS Well-Architected Security Pillar, bảo vệ Root User bằng MFA, sử dụng thông tin xác thực tạm thời (IAM Role / Federation) và nguyên tắc Least Privilege | 16/11/2026 | 16/11/2026 | https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/welcome.html <br> https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html |
| 3 | **Nghiên cứu Bảo mật Amazon S3 & AWS CloudTrail:** <br> - Tìm hiểu chi tiết cơ chế mặc định trên S3 (4 cài đặt Block Public Access, mã hóa SSE-S3, S3 Versioning và lưu ý chi phí lưu nhiều phiên bản) cùng phạm vi tra cứu 90 ngày của CloudTrail Event History <br> - Biên soạn checklist bảo mật để đăng bài chia sẻ lên nhóm học tập | 17/11/2026 | 17/11/2026 | https://aws.amazon.com/compliance/shared-responsibility-model/ <br> https://docs.aws.amazon.com/AmazonS3/latest/userguide/security-best-practices.html |
| 4 | **Đăng 3 bài chia sẻ lên AWS Study Group VN & Nâng cấp UI Frontend:** <br> - Đăng tải 3 bài viết tổng hợp kiến thức bảo mật AWS lên cộng đồng **AWS Study Group VN** <br> - Thiết kế lại bố cục giao diện và hiệu ứng chuyển động mượt mà, tối giản cho trang khách hàng của **SecureTable** (song ngữ Việt - Anh), sửa lỗi hiển thị hình ảnh món ăn và đóng gói thư mục `frontend/` | 18/11/2026 | 18/11/2026 | https://docs.aws.amazon.com/awscloudtrail/latest/userguide/view-cloudtrail-events.html |
| 5 | **Đồng bộ lại Logic Frontend khớp đặc tả API Backend:** <br> - Rà soát kỹ từng đường dẫn API, tham số gửi đi và kiểm tra phân quyền của 5 vai trò trên giao diện để khớp 100% với đặc tả `securetable-api.md` của bạn làm Backend | 19/11/2026 | 19/11/2026 | https://docs.aws.amazon.com/apigateway/latest/developerguide/http-api-cors.html |
| 6 | **Kiểm tra cấu hình `.gitignore` & Đưa mã nguồn `frontend/` lên Git:** <br> - Kiểm tra quy tắc loại trừ `node_modules/` và `dist/` trong `.gitignore`, đóng gói bản build thử nghiệm và đẩy phần code `frontend/` lên kho mã nguồn chung của nhóm mà không gây xung đột | 20/11/2026 | 20/11/2026 | https://cloudjourney.awsstudygroup.com/ |

### Kết quả đạt được trong tuần 10

* Hệ thống hóa vững chắc kiến thức cốt lõi về **AWS Shared Responsibility Model**, **S3 Data Protection**, **IAM Least Privilege** và **CloudTrail**, hoàn thành 3 bài chia sẻ được duyệt trên nhóm **AWS Study Group VN**.
* Hoàn thiện giao diện **SecureTable** có tính thẩm mỹ cao, chuyển động mượt mà, song ngữ `VI / EN` rõ ràng và hiển thị đầy đủ hình ảnh món ăn, không gian quán.
* Đảm bảo toàn bộ logic xử lý ở tầng giao diện khớp chặt chẽ với đặc tả API và phân quyền của Backend.
