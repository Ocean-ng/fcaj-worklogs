---
title: "Blog 3"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# Tự động hóa phát hiện mối đe dọa và phản ứng sự cố an ninh trên AWS với GuardDuty, Security Hub và EventBridge

Trong vận hành an ninh đám mây (Cloud SecOps), khoảng thời gian từ lúc lỗ hổng xuất hiện hoặc thông tin xác thực bị đánh cắp cho tới khi đội ngũ quản trị phát hiện (Mean Time to Detect - **MTTD**) và cô lập (Mean Time to Respond - **MTTR**) quyết định mức độ thiệt hại của toàn hệ thống. Nếu chỉ dựa vào việc đọc log thủ công trên CloudTrail hay VPC Flow Logs, quản trị viên rất dễ bỏ sót các dấu hiệu tấn công tinh vi.

Bài viết này tổng hợp mô hình tự động hóa giám sát, đánh giá tuân thủ và phản ứng sự cố theo thời gian thực trên AWS mà mình đã nghiên cứu và thực hành trong kỳ thực tập.

---

### 1. Kiến trúc 3 tầng của hệ thống Cloud SecOps tự động

Một hệ thống phòng thủ chủ động trên AWS được kết hợp từ 3 nhóm dịch vụ chính:

1. **Tầng Phát hiện & Đánh giá (Detection & Posture Management):**
   * **Amazon GuardDuty:** Phân tích liên tục luồng dữ liệu từ **AWS CloudTrail Events**, **VPC Flow Logs** và **Route 53 DNS Query Logs** bằng Machine Learning và danh sách Threat Intelligence để phát hiện hành vi bất thường (ví dụ: IAM Access Key bị sử dụng từ Tor exit node, EC2 kết nối tới máy chủ đào tiền ảo hoặc dò quét cổng nội bộ).
   * **AWS Security Hub:** Thu thập cảnh báo chuẩn hóa theo định dạng **ASFF (AWS Security Finding Format)** từ GuardDuty, Inspector, IAM Access Analyzer và tự động chấm điểm cấu hình tài khoản theo chuẩn **CIS AWS Foundations Benchmark**.

2. **Tầng Điều phối sự kiện (Event Routing):**
   * **Amazon EventBridge:** Đóng vai trò bộ lọc sự kiện trung tâm, lắng nghe mọi Finding có mức độ nghiêm trọng từ `HIGH` trở lên được đẩy ra từ GuardDuty hoặc Security Hub theo thời gian thực.

3. **Tầng Phản ứng & Cảnh báo (Automated Remediation & Notification):**
   * **Amazon SNS:** Gửi cảnh báo tức thời tới Email / Slack / Microsoft Teams của đội trực an ninh.
   * **AWS Lambda:** Thực thi kịch bản phản ứng tự động (Playbook) chỉ trong vài giây để cô lập tài nguyên bị xâm nhập.

---

### 2. Mẫu cấu hình EventBridge Rule bắt cảnh báo mức độ cao từ GuardDuty

Để chỉ kích hoạt cảnh báo và phản ứng tự động đối với các mối đe dọa có mức độ nghiêm trọng cao (`severity >= 7.0`), ta định nghĩa Event Pattern trên Amazon EventBridge như sau:

```json
{
  "source": ["aws.guardduty"],
  "detail-type": ["GuardDuty Finding"],
  "detail": {
    "severity": [
      { "numeric": [">=", 7.0] }
    ]
  }
}
```

---

### 3. Kịch bản tự động cô lập (Auto-Quarantine) bằng AWS Lambda

Khi GuardDuty phát hiện một máy chủ EC2 có hành vi giao tiếp với máy chủ điều khiển độc hại (`Backdoor:EC2/C&CActivity.B!DNS`), EventBridge sẽ kích hoạt ngay một hàm AWS Lambda thực hiện 3 bước tự động:
1. **Cách ly mạng tức thời:** Thay thế Security Group hiện tại của EC2 bằng một `Quarantine-Security-Group` (không có bất kỳ Inbound hay Outbound Rule nào) để cắt đứt kết nối của kẻ tấn công nhưng vẫn giữ máy chủ ở trạng thái chạy nhằm bảo toàn dữ liệu trên RAM phục vụ điều tra số (Forensics).
2. **Chụp ảnh bằng chứng:** Tự động gọi API tạo **EBS Snapshot** cho toàn bộ các ổ đĩa gắn với EC2 đó và gắn thẻ `ForensicEvidence=True`.
3. **Thông báo chi tiết:** Gửi thông tin Instance ID, loại Finding, Region và thời gian xảy ra sự cố qua **Amazon SNS** tới kỹ sư trực hệ thống.

---

### 4. Bài học rút ra từ thực tế thực tập

* **Không cài đặt Agent nhưng vẫn bao phủ toàn diện:** Điểm mạnh lớn nhất của GuardDuty là hoạt động hoàn toàn ở tầng Control Plane của AWS (đọc trực tiếp luồng CloudTrail, VPC Flow Logs, DNS Logs nội bộ), nên kẻ tấn công dù chiếm được quyền `root` trên hệ điều hành EC2 cũng không thể "tắt" được GuardDuty.
* **Cô lập thay vì xóa máy chủ:** Trong ứng cứu sự cố (Incident Response), việc đổi Security Group sang nhóm cách ly và chụp EBS Snapshot tốt hơn nhiều so với việc `Terminate` máy chủ ngay lập tức, vì giúp giữ lại đầy đủ dấu vết để tìm ra nguyên nhân gốc rễ (Root Cause Analysis).
* **Kiểm soát chi phí khi học tập:** GuardDuty cung cấp 30 ngày dùng thử miễn phí (Free Trial); khi thực hành trên tài khoản sinh viên, luôn theo dõi mục Usage trong GuardDuty Console và tắt dịch vụ sau khi hoàn tất bài lab.
