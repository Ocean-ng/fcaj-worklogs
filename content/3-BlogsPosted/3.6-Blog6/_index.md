---
title: "Blog 6"
date: 2024-01-01
weight: 6
chapter: false
pre: " <b> 3.6. </b> "
---

# Enforcing Mandatory AI Safety for Generative AI Applications with Amazon Bedrock Guardrails and IAM Condition Keys

* **Topic:** Generative AI Security & IAM Governance on AWS
* **Author:** Thuy Nga

---

As engineering teams integrate Large Language Models (LLMs) into applications via **Amazon Bedrock**, cloud security expands beyond traditional network firewalls and SQL injection defenses to address AI-specific threats: adversarial **Prompt Injection and Jailbreaks**, **System Prompt Leakage**, and accidental exposure of **Personally Identifiable Information (PII)** in user prompts or model responses.

**Amazon Bedrock Guardrails** provides a model-agnostic safety layer inspecting inputs and outputs inline. However, from an **Information Assurance** governance perspective, a critical question remains: *How can security teams guarantee that no developer or Lambda function accidentally invokes a foundation model without attaching the approved Guardrail?*

![IAM Policy-Based Enforcement for Amazon Bedrock Guardrails (Source: AWS Machine Learning Blog)](/images/3-BlogsPosted/blog6-bedrock-guardrails-iam.jpg)

### 1. Layered Safeguards in Amazon Bedrock Guardrails

When bound to `InvokeModel` or `Converse` API calls, Bedrock Guardrails evaluates both **user inputs (prompts)** and **model responses** across multiple configurable filters:
* **Prompt Attack Filter:** Detects and blocks Prompt Injection and Jailbreak attempts designed to override safety instructions or extract system prompts verbatim.
* **Sensitive Information Filters (PII Redaction):** Automatically blocks or masks sensitive entities (`[EMAIL]`, `[PHONE]`, national IDs) before prompts reach the model or before outputs return to clients.
* **Content Filters & Denied Topics:** Blocks harmful categories and prevents the assistant from answering out-of-scope topics (for example, ensuring a restaurant ordering assistant refuses financial or medical advice).
* **Contextual Grounding Checks:** Detects ungrounded hallucinations in Retrieval-Augmented Generation (RAG) responses.

### 2. Mandatory Governance Using the `bedrock:GuardrailIdentifier` IAM Condition Key

Relying solely on application code to pass the `guardrailIdentifier` parameter leaves room for human error during deployments.

As shown in the AWS architecture diagram above, security engineers can attach an explicit `Deny` statement to the application's IAM Role (or AWS Organizations SCP) using the **`bedrock:GuardrailIdentifier`** condition key:

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

With this explicit `Deny` guardrail in place:
* **Compliant Flow (User A):** Requests carrying the approved Guardrail ARN pass IAM evaluation and invoke Amazon Bedrock safely.
* **Non-Compliant Flow (User B):** Any model invocation missing the Guardrail identifier (or referencing an unapproved version) is **immediately rejected by AWS IAM (`AccessDeniedException`)** before reaching the foundation model.

### Security Checklist for Generative AI Workloads on AWS

* Never store API keys, credentials, or authorization logic inside System Prompts—enforce access control strictly in backend code and AWS IAM.
* Enable **Prompt Attack Filters** and **PII Redaction** in Amazon Bedrock Guardrails for all user-facing AI endpoints.
* Enforce the **`bedrock:GuardrailIdentifier`** condition key in IAM Policies or SCPs so 100% of model invocations traverse approved guardrails.
* Route Guardrail intervention metrics and logs to **Amazon CloudWatch** to monitor prompt attack attempts in real time.

### References

1. [Amazon Bedrock Guardrails announces IAM policy-based enforcement to deliver safe AI interactions – AWS Machine Learning Blog](https://aws.amazon.com/blogs/machine-learning/amazon-bedrock-guardrails-announces-iam-policy-based-enforcement-to-deliver-safe-ai-interactions/)
2. [Stop harmful content in models using Amazon Bedrock Guardrails – Amazon Bedrock User Guide](https://docs.aws.amazon.com/bedrock/latest/userguide/guardrails.html)
3. [Designing for the inevitable: System prompt leakage and mitigations in generative AI applications – AWS Security Blog](https://aws.amazon.com/blogs/security/designing-for-the-inevitable-system-prompt-leakage-and-mitigations-in-generative-ai-applications/)
4. [Detect prompt attacks with Content filters – Amazon Bedrock User Guide](https://docs.aws.amazon.com/bedrock/latest/userguide/guardrails-prompt-attack.html)

`#AWS` `#CloudSecurity` `#GenerativeAI` `#AmazonBedrock` `#IAM`
