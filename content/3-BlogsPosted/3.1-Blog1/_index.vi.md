---
title: "Blog 1"
date: 2026-10-15
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Kiểm soát đặc quyền tối thiểu trong Kubernetes với Session Policies trên Amazon EKS Pod Identity

Trong các cụm Kubernetes (Amazon EKS) quy mô doanh nghiệp, việc cấp quyền cho các Pod truy cập tài nguyên AWS (như Amazon S3, DynamoDB, Secrets Manager) theo đúng nguyên tắc **Đặc quyền tối thiểu (Principle of Least Privilege)** luôn là bài toán thách thức. Nếu tạo một IAM Role riêng cho từng microservice hoặc từng namespace, số lượng IAM Roles sẽ tăng theo cấp số nhân và nhanh chóng chạm ngưỡng giới hạn (Quota) của tài khoản AWS.

Tính năng **Session Policies** trong **Amazon EKS Pod Identity** giải quyết triệt để vấn đề này bằng cách cho phép tái sử dụng một IAM Role chung nhưng thu hẹp quyền hạn cụ thể cho từng Pod ngay tại thời điểm cấp phát phiên làm việc (Session).

---

### 1. Cơ chế hoạt động của Session Policies trong EKS Pod Identity

Khi một Pod trong Amazon EKS yêu cầu thông tin xác thực AWS tạm thời thông qua EKS Pod Identity Agent, dịch vụ EKS sẽ gọi API `AssumeRoleForPodIdentity` của AWS Security Token Service (STS).

Với tính năng **Session Policies**, bạn có thể đính kèm một chính sách IAM nội tuyến (Inline Session Policy) trực tiếp vào **Pod Identity Association** (liên kết giữa Kubernetes `ServiceAccount`, `Namespace` và `IAM Role`).

Nguyên tắc cốt lõi cần nhớ:
* **Quyền thực tế (Effective Permissions)** = **Phép giao (Intersection)** giữa `IAM Role Identity-based Policy` và `Session Policy`.
* Session Policy **chỉ có thể thu hẹp** quyền hạn đã có của IAM Role gốc, tuyệt đối **không thể mở rộng** thêm quyền mà IAM Role gốc không cho phép.

---

### 2. Kịch bản ứng dụng thực tế

Giả sử bạn có một S3 Bucket dùng chung tên là `fcaj-shared-artifacts-bucket` chứa dữ liệu của nhiều nhóm ứng dụng (`team-alpha`, `team-beta`).

Thay vì tạo 20 IAM Roles khác nhau cho 20 dịch vụ, bạn chỉ cần:
1. Tạo **1 IAM Role nền tảng** (`EKS-S3-Base-Role`) cho phép đọc/ghi trên toàn bộ bucket `arn:aws:s3:::fcaj-shared-artifacts-bucket/*`.
2. Khi gắn Role này cho `ServiceAccount` của `team-alpha`, bạn truyền thêm một **Session Policy** chỉ cho phép truy cập tiền tố `team-alpha/*`:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:GetObject",
        "s3:PutObject"
      ],
      "Resource": "arn:aws:s3:::fcaj-shared-artifacts-bucket/team-alpha/*"
    }
  ]
}
```

Nhờ phép giao quyền hạn, Pod của `team-alpha` hoàn toàn không thể đọc được dữ liệu trong thư mục `team-beta/*` dù đang dùng chung `EKS-S3-Base-Role`.

---

### 3. Triển khai nhanh qua AWS CLI

Bạn có thể tạo hoặc cập nhật Pod Identity Association kèm Session Policy trực tiếp bằng AWS CLI:

```bash
aws eks create-pod-identity-association \
  --cluster-name fcaj-prod-cluster \
  --namespace team-alpha \
  --service-account alpha-worker-sa \
  --role-arn arn:aws:iam::123456789012:role/EKS-S3-Base-Role \
  --policy file://session-policy-alpha.json
```

---

### 4. Lợi ích nổi bật về mặt An toàn thông tin & Vận hành

* **Chống cấp quyền dư thừa (Anti Over-Permissioning):** Ngăn chặn rủi ro một Pod bị xâm nhập có thể leo thang đọc dữ liệu của các phân hệ khác dùng chung IAM Role.
* **Giải quyết bài toán IAM Role Sprawl:** Giảm tới 70–80% số lượng IAM Roles phải duy trì trong tài khoản AWS, tránh chạm ngưỡng IAM Role Quota trên các cụm EKS lớn.
* **Hỗ trợ Cross-Account linh hoạt:** Kết hợp mượt mà với mô hình IAM Role Chaining khi Pod cần truy cập tài nguyên nằm ở một tài khoản AWS khác trong AWS Organizations.
* **Tách biệt trách nhiệm rõ ràng:** Đội ngũ Cloud Security quản lý IAM Role gốc (cận trên của quyền hạn), trong khi đội Platform/DevOps có thể thu hẹp phạm vi cho từng workload qua Session Policy khi triển khai ứng dụng.
