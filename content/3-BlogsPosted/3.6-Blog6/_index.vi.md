---
title: "Blog 6"
date: 2024-01-01
weight: 6
chapter: false
pre: " <b> 3.6. </b> "
---

# Bắt buộc kiểm soát an toàn cho ứng dụng Generative AI với Amazon Bedrock Guardrails và IAM Condition Key

* **Chủ đề:** Generative AI Security & IAM Governance trên AWS
* **Tác giả:** Thúy Nga

---

Khi các nhóm phát triển tích hợp mô hình ngôn ngữ lớn (LLM) vào sản phẩm thông qua **Amazon Bedrock**, rủi ro bảo mật không còn dừng ở lỗi cấu hình mạng hay SQL Injection truyền thống mà xuất hiện thêm các mối đe dọa đặc thù của AI: người dùng cố tình chèn câu lệnh thao túng mô hình (**Prompt Injection / Jailbreak**), khai thác làm lộ câu lệnh hệ thống (**System Prompt Leakage**) hoặc vô tình gửi thông tin định danh cá nhân nhạy cảm (**PII** như số điện thoại, email, thẻ căn cước) vào hội thoại.

**Amazon Bedrock Guardrails** cung cấp một lớp kiểm duyệt an toàn độc lập nằm ngay trên luồng gọi mô hình. Tuy nhiên, câu hỏi đặt ra cho đội ngũ **An toàn thông tin** là: *Làm sao đảm bảo không một lập trình viên hay hàm Lambda nào trong tài khoản gọi thẳng API mô hình mà "quên" đính kèm Guardrail?*

![Bắt buộc áp dụng Amazon Bedrock Guardrails bằng IAM Condition Key (Nguồn: AWS Machine Learning Blog)](/images/3-BlogsPosted/blog6-bedrock-guardrails-iam.jpg)

### 1. Các lớp bảo vệ cốt lõi của Amazon Bedrock Guardrails

Khi được gắn vào lệnh gọi `InvokeModel` hoặc `Converse`, Bedrock Guardrails kiểm tra cả chiều **Input (Prompt của người dùng)** lẫn chiều **Output (Phản hồi của mô hình)** dựa trên các bộ lọc:
* **Prompt Attack Filter:** Phát hiện và chặn sớm các kỹ thuật Prompt Injection và Jailbreak tìm cách vượt qua quy tắc an toàn hoặc trích xuất nguyên văn System Prompt.
* **Sensitive Information Filters (PII Redaction):** Tự động chặn hoặc che dấu (`[EMAIL]`, `[PHONE]`) các dữ liệu nhạy cảm trước khi đi tới mô hình hoặc trước khi trả về cho người dùng.
* **Content Filters & Denied Topics:** Chặn nội dung độc hại và từ chối trả lời các chủ đề nằm ngoài phạm vi nghiệp vụ cho phép của ứng dụng (ví dụ: chatbot hỗ trợ đặt món không được phép tư vấn tài chính hay y tế).
* **Contextual Grounding Check:** Phát hiện hiện tượng "ảo giác" (Hallucination) khi câu trả lời không bám sát nguồn dữ liệu tham chiếu trong kiến trúc RAG.

### 2. Khóa chặt ở tầng quản trị bằng điều kiện `bedrock:GuardrailIdentifier` trong IAM

Nếu việc truyền tham số `guardrailIdentifier` chỉ phụ thuộc vào code của từng developer, một bản cập nhật thiếu sót có thể khiến ứng dụng gọi thẳng vào mô hình nền tảng mà không có lớp chắn bảo vệ.

Như minh họa trong sơ đồ của AWS, đội ngũ bảo mật có thể thiết lập **IAM Policy** trên IAM Role của ứng dụng sử dụng Condition Key **`bedrock:GuardrailIdentifier`**:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "DenyInvokeWithoutApprovedGuardrail",
      "Effect": "Deny",
      "Action": [
        "bedrock:InvokeModel",
        "bedrock:InvokeModelWithResponseStream",
        "bedrock:Converse",
        "bedrock:ConverseStream"
      ],
      "Resource": "*",
      "Condition": {
        "StringNotEquals": {
          "bedrock:GuardrailIdentifier": "arn:aws:bedrock:ap-southeast-1:123456789012:guardrail/abc123xyz"
        }
      }
    }
  ]
}
```

Với chính sách `Deny` tường minh này:
* **Luồng hợp lệ (User A):** Request từ ứng dụng có đính kèm đúng ARN của Guardrail đã được phê duyệt → được phép gọi tới Amazon Bedrock.
* **Luồng vi phạm (User B):** Request không đính kèm Guardrail hoặc dùng sai phiên bản Guardrail → bị **AWS IAM từ chối ngay lập tức (`AccessDeniedException`)** trước khi chạm tới mô hình.

### Checklist khi triển khai ứng dụng Generative AI an toàn trên AWS

* Không lưu bí mật hệ thống, API Key hoặc logic phân quyền vào trong System Prompt — luôn thực thi kiểm tra quyền ở tầng Backend và IAM.
* Bật **Prompt Attack Filter** và **PII Redaction** trên Amazon Bedrock Guardrails cho mọi ứng dụng tương tác với người dùng bên ngoài.
* Áp dụng điều kiện **`bedrock:GuardrailIdentifier`** trong IAM Policy (hoặc Service Control Policy - SCP) để bắt buộc 100% lệnh gọi mô hình phải đi qua Guardrail chuẩn.
* Đẩy nhật ký vi phạm Guardrail về **Amazon CloudWatch** để theo dõi xu hướng tấn công Prompt Injection theo thời gian thực.

### Tài liệu tham khảo

1. [Amazon Bedrock Guardrails announces IAM policy-based enforcement to deliver safe AI interactions – AWS Machine Learning Blog](https://aws.amazon.com/blogs/machine-learning/amazon-bedrock-guardrails-announces-iam-policy-based-enforcement-to-deliver-safe-ai-interactions/)
2. [Stop harmful content in models using Amazon Bedrock Guardrails – Amazon Bedrock User Guide](https://docs.aws.amazon.com/bedrock/latest/userguide/guardrails.html)
3. [Designing for the inevitable: System prompt leakage and mitigations in generative AI applications – AWS Security Blog](https://aws.amazon.com/blogs/security/designing-for-the-inevitable-system-prompt-leakage-and-mitigations-in-generative-ai-applications/)
4. [Detect prompt attacks with Content filters – Amazon Bedrock User Guide](https://docs.aws.amazon.com/bedrock/latest/userguide/guardrails-prompt-attack.html)

`#AWS` `#CloudSecurity` `#GenerativeAI` `#AmazonBedrock` `#IAM`
