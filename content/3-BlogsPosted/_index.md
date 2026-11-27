---
title: "Blogs Posted"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

> This section compiles technical blog posts and research notes on **AWS Cloud Security**, **Serverless Architecture**, and **Generative AI Safety** authored from official AWS documentation and shared with the [AWS Study Group VN](https://www.facebook.com/groups/660548818043427/user/100016726392723) community.

### [Blog 1 - Exploring the Shared Responsibility Model and Amazon S3 Data Security](3.1-Blog1/)
A structured study summary examining the **AWS Shared Responsibility Model** across Amazon EC2 and Amazon S3, focusing on **S3 Block Public Access**, default **SSE-S3** encryption at rest, and **S3 Versioning** storage trade-offs.

### [Blog 2 - AWS Shared Responsibility Model](3.2-Blog2/)
An analytical breakdown distinguishing AWS responsibilities (**“Security of the Cloud”**) from customer responsibilities (**“Security in the Cloud”**) across IaaS (EC2) and managed services (S3), paired with a system design security checklist.

### [Blog 3 - AWS Security: Starting with Identity and Access Control (IAM & CloudTrail)](3.3-Blog3/)
Four foundational identity governance practices aligned with the **AWS Well-Architected Security Pillar**: protecting the Root user with MFA, preferring federation and temporary credentials (IAM Roles), scoping **Least Privilege** down to S3 prefixes, and auditing activity with **AWS CloudTrail**.

### [Blog 4 - Protecting Origins Behind Amazon CloudFront with AWS WAF, OAC, and Auto-Rotated Custom Headers](3.4-Blog4/)
How to prevent attackers from bypassing edge defenses to hit backend origins directly: enforcing **Origin Access Control (OAC)** for S3 origins and combining **AWS WAF + auto-rotated `X-Origin-Verify` secrets via AWS Secrets Manager & Lambda** for ALB/API origins.

### [Blog 5 - Automating Time-Based Serverless Workflows with Amazon EventBridge Scheduler, AWS Lambda, and DynamoDB](3.5-Blog5/)
Replacing traditional cron servers with **Amazon EventBridge Scheduler** to orchestrate timezone-aware recurring and one-time schedules at scale, complete with built-in retry policies, Dead-Letter Queues, and practical applications in automated reporting and DynamoDB backups.

### [Blog 6 - Enforcing Mandatory AI Safety for Generative AI Applications with Amazon Bedrock Guardrails and IAM Condition Keys](3.6-Blog6/)
Addressing modern Generative AI security challenges on AWS: using **Amazon Bedrock Guardrails** to block **Prompt Injection** and redact sensitive **PII**, while enforcing the **`bedrock:GuardrailIdentifier`** IAM condition key so no developer or workload can invoke foundation models without active guardrails.
