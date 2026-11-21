---
title: "Worklog Tuần 1"
date: 2026-09-14
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Mục tiêu tuần 1

* Làm quen với quy trình làm việc, nội quy và lộ trình đào tạo của chương trình First Cloud AI Journey (FCAJ).
* Nắm vững các khái niệm nền tảng về Điện toán đám mây (Cloud Computing), các mô hình dịch vụ (IaaS, PaaS, SaaS) và hạ tầng toàn cầu AWS Global Infrastructure.
* Khởi tạo tài khoản AWS Free Tier, thiết lập bảo mật tài khoản Root và cấu hình cảnh báo chi phí với AWS Budgets.
* Tìm hiểu sâu và thực hành quản lý định danh, phân quyền truy cập theo nguyên tắc đặc quyền tối thiểu (Least Privilege) với AWS IAM và AWS CLI.

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|------|-----------|-------------|----------------|---------------|
| 2 | **Định hướng & Onboarding:** <br> - Tìm hiểu quy định, văn hóa làm việc và tiêu chí đánh giá của chương trình FCAJ <br> - Thiết lập môi trường làm việc cá nhân (Git, Hugo, VS Code) và khởi tạo trang báo cáo thực tập | 14/09/2026 | 14/09/2026 | https://cloudjourney.awsstudygroup.com/ |
| 3 | **Nền tảng Cloud & Hạ tầng AWS:** <br> - Nghiên cứu tổng quan về Cloud Computing và 6 lợi ích cốt lõi của điện toán đám mây <br> - Tìm hiểu kiến trúc AWS Global Infrastructure: Regions, Availability Zones (AZs), Edge Locations <br> - Khảo sát các nhóm dịch vụ cốt lõi: Compute, Storage, Networking, Database, Security | 15/09/2026 | 15/09/2026 | https://cloudjourney.awsstudygroup.com/ |
| 4 | **Khởi tạo & Bảo mật AWS Account:** <br> - Đăng ký tài khoản AWS Free Tier và xác thực phương thức thanh toán <br> - Kích hoạt bảo mật đa lớp (Virtual MFA) cho Root Account <br> - Cấu hình AWS Budgets và Billing Alarm để kiểm soát ngưỡng chi phí sử dụng | 16/09/2026 | 16/09/2026 | https://000001.awsstudygroup.com/ <br> https://000007.awsstudygroup.com/ |
| 5 | **Quản lý định danh với AWS IAM:** <br> - Tìm hiểu kiến trúc AWS IAM: Users, Groups, Roles và JSON Policies <br> - Thực hành tạo IAM Admin User thay thế Root User cho các tác vụ quản trị hằng ngày <br> - Thiết lập IAM Password Policy và phân quyền theo nhóm chức năng | 17/09/2026 | 17/09/2026 | https://000002.awsstudygroup.com/ |
| 6 | **Thực hành Switch Role & AWS CLI:** <br> - Thực hành ủy quyền truy cập bằng IAM Role và tính năng Switch Role <br> - Cài đặt AWS CLI v2, tạo Access Key cho IAM User và cấu hình bằng `aws configure` <br> - Kiểm thử truy vấn tài nguyên qua CLI (`aws sts get-caller-identity`, `aws iam list-users`) và dọn dẹp tài nguyên | 18/09/2026 | 18/09/2026 | https://000002.awsstudygroup.com/ <br> https://000011.awsstudygroup.com/ |

### Kết quả đạt được trong tuần 1

* Hiểu rõ quy trình thực tập FCAJ cũng như kiến trúc hạ tầng toàn cầu của AWS (Regions, Availability Zones, Edge Locations).
* Hoàn tất khởi tạo tài khoản AWS cá nhân, bảo vệ tài khoản Root bằng MFA và thiết lập cảnh báo ngân sách tự động với AWS Budgets để tránh phát sinh chi phí ngoài ý muốn.
* Nắm vững cơ chế hoạt động của AWS IAM, áp dụng nguyên tắc Least Privilege (đặc quyền tối thiểu), tách biệt hoàn toàn tài khoản Root khỏi các thao tác vận hành thường ngày.
* Thành thạo kết hợp giữa giao diện AWS Management Console và công cụ dòng lệnh AWS CLI v2 để kiểm tra và quản lý tài nguyên.
