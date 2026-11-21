---
title: "Worklog Tuần 2"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu tuần 2

* Nắm vững kiến trúc mạng đám mây trên AWS thông qua dịch vụ Amazon Virtual Private Cloud (Amazon VPC).
* Hiểu cách quy hoạch dải IP (CIDR Block), phân chia Public Subnet và Private Subnet trên nhiều Availability Zones.
* Làm chủ cơ chế định tuyến với Route Tables, Internet Gateway (IGW) và NAT Gateway.
* Phân biệt rõ và thực hành thiết lập bảo mật mạng đa lớp bằng Security Groups (Stateful) và Network ACLs (Stateless).
* Tìm hiểu các mô hình kết nối mạng nâng cao như VPC Peering và AWS Site-to-Site VPN.

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|------|-----------|-------------|----------------|---------------|
| 2 | **Quy hoạch mạng Amazon VPC:** <br> - Tìm hiểu khái niệm Amazon VPC, cách tính CIDR block (ví dụ `10.0.0.0/16`) <br> - Thiết kế kiến trúc mạng Multi-AZ gồm Public Subnets và Private Subnets <br> - Thực hành khởi tạo Custom VPC và các Subnets trên AWS Console | 21/09/2026 | 21/09/2026 | https://000003.awsstudygroup.com/ |
| 3 | **Định tuyến & Kết nối Internet:** <br> - Tìm hiểu cơ chế hoạt động của Route Table và Internet Gateway (IGW) <br> - Gắn IGW vào VPC và cấu hình Public Route Table (`0.0.0.0/0` trỏ về IGW) <br> - Bật thuộc tính Auto-assign Public IPv4 cho Public Subnet | 22/09/2026 | 22/09/2026 | https://000003.awsstudygroup.com/ |
| 4 | **Bảo mật tầng mạng (Security Group & NACL):** <br> - Phân tích sự khác biệt giữa Security Group (mức Instance, Stateful) và Network ACL (mức Subnet, Stateless) <br> - Thực hành cấu hình Inbound/Outbound Rules giới hạn IP và Port truy cập <br> - Kiểm thử luồng chặn/cho phép gói tin ICMP và SSH/HTTP | 23/09/2026 | 23/09/2026 | https://000003.awsstudygroup.com/ |
| 5 | **NAT Gateway cho Private Subnet:** <br> - Tìm hiểu bài toán cho phép máy chủ trong Private Subnet tải bản vá/gói phần mềm từ Internet mà không lộ IP Public <br> - Khởi tạo NAT Gateway đặt tại Public Subnet kèm Elastic IP <br> - Cấu hình Private Route Table định tuyến lưu lượng ra Internet qua NAT Gateway | 24/09/2026 | 24/09/2026 | https://000003.awsstudygroup.com/ |
| 6 | **Kết nối VPC Peering & VPN:** <br> - Tìm hiểu kết nối liên mạng giữa hai VPC qua VPC Peering và cập nhật Route Tables hai chiều <br> - Nghiên cứu kiến trúc AWS Site-to-Site VPN (Virtual Private Gateway, Customer Gateway) <br> - Xóa NAT Gateway, Elastic IP và các tài nguyên thực hành để tiết kiệm chi phí | 25/09/2026 | 25/09/2026 | https://000003.awsstudygroup.com/ <br> https://000019.awsstudygroup.com/ |

### Kết quả đạt được trong tuần 2

* Tự tay thiết kế và triển khai hoàn chỉnh một Custom VPC theo chuẩn Multi-AZ với sự tách biệt rõ ràng giữa vùng mạng công cộng (Public Subnet) và vùng mạng nội bộ (Private Subnet).
* Hiểu sâu cơ chế định tuyến gói tin trong VPC thông qua Route Tables, Internet Gateway và NAT Gateway.
* Nắm vững tư duy bảo mật mạng chiều sâu (Defense in Depth): kết hợp Network ACL ở biên Subnet và Security Group ở từng máy chủ, hiểu rõ tính chất Stateful vs Stateless khi xử lý sự cố kết nối.
* Nắm được kiến trúc kết nối mở rộng giữa nhiều VPC bằng VPC Peering và mô hình mạng lai (Hybrid Cloud) qua Site-to-Site VPN.
