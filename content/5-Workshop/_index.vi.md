---
title: "Workshop"
date: 2026-10-19
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Đảm bảo truy cập Hybrid an toàn đến S3 bằng cách sử dụng VPC Endpoint

#### Tổng quan

**AWS PrivateLink** cung cấp kết nối riêng tư đến các dịch vụ AWS từ VPC hoặc trung tâm dữ liệu tại chỗ (On-premises) mà không làm lộ lưu lượng truy cập ra ngoài mạng Internet công cộng.

Trong bài thực hành (Workshop) này, chúng ta sẽ thiết lập, cấu hình và kiểm thử các **VPC Endpoints** để cho phép hệ thống máy chủ tiếp cận dịch vụ Amazon S3 hoàn toàn qua hạ tầng mạng riêng của AWS.

Chúng ta sẽ triển khai hai loại VPC Endpoint để truy cập Amazon S3: **Gateway VPC Endpoint** và **Interface VPC Endpoint**. Mỗi loại mang lại lợi ích kiến trúc riêng tùy thuộc vào việc bạn truy cập S3 từ bên trong VPC trên Cloud hay từ trung tâm dữ liệu On-premises:
+ **Gateway Endpoint** — Gửi lưu lượng đến Amazon S3 hoặc DynamoDB qua mạng nội bộ AWS hoàn toàn miễn phí. Lưu lượng từ VPC được định tuyến đến Gateway Endpoint thông qua bảng định tuyến (Route Tables) bằng Prefix List.
+ **Interface Endpoint (AWS PrivateLink)** — Tạo các giao diện mạng đàn hồi (ENI) có địa chỉ IP Private ngay trong Subnet để nhận lưu lượng gửi đến dịch vụ đích, hỗ trợ kết nối từ cả mạng On-premises (qua Site-to-Site VPN / Direct Connect) và kết hợp với **Amazon Route 53 Private DNS / Inbound Resolver**.

#### Nội dung thực hành

1. [Tổng quan về Workshop](5.1-Workshop-overview/)
2. [Chuẩn bị hạ tầng](5.2-Prerequiste/)
3. [Truy cập đến S3 từ VPC với Gateway Endpoint](5.3-S3-vpc/)
4. [Truy cập đến S3 từ TTDL On-premises với Interface Endpoint & Route 53](5.4-S3-onprem/)
5. [Bảo mật với VPC Endpoint Policies](5.5-Policy/)
6. [Dọn dẹp tài nguyên](5.6-Cleanup/)
