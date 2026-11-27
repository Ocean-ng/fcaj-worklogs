---
title: "Week 5 Worklog"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Week 5 Objectives

* Study the **AWS Well-Architected Framework** pillars (focusing on Security, Reliability, Operational Excellence, Performance Efficiency, and Cost Optimization).
* Finalize problem statement and project scope for **SecureTable** (an AWS Serverless Ingredient Management and QR Code Ordering System in `ap-southeast-1`).
* Design the architecture diagram using official AWS Architecture Icons and define workflows across 5 user roles: `Guest`, `Reception`, `Kitchen`, `Inventory`, and `Admin`.
* Build a detailed monthly and 12-month infrastructure cost estimate based on realistic traffic assumptions using the **AWS Pricing Calculator**.

### Tasks Implemented This Week

| Day | Task | Start Date | Completion Date | Reference Material |
|------|-----------|-------------|----------------|---------------|
| Mon | **AWS Well-Architected Framework Study:** <br> - Study core design principles across the 6 AWS Well-Architected pillars <br> - Deep dive into the Security Pillar (Least-Privilege IAM, data protection in transit/at rest, audit traceability) | 12/10/2026 | 12/10/2026 | https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html |
| Tue | **SecureTable Business Requirement Analysis:** <br> - Analyze inventory discrepancy, delayed kitchen tickets, and manual billing reconciliation challenges in small restaurants <br> - Define permissions and workflows for 5 user roles (`Guest`, `Reception`, `Kitchen`, `Inventory`, `Admin`) <br> - Select AWS Serverless stack: S3, CloudFront, API Gateway, Lambda, DynamoDB, Cognito, EventBridge Scheduler, SNS, CloudWatch, CloudTrail, WAF | 13/10/2026 | 13/10/2026 | https://aws.amazon.com/serverless/ |
| Wed | **Standardized AWS Architecture Diagramming:** <br> - Design the `SecureTable_Architecture` diagram in Draw.io using official AWS Architecture Icons <br> - Map out the 4 core flows: Guest QR ordering, Cognito staff authentication, transactional Kitchen/Inventory updates, and scheduled report/backup automation | 14/10/2026 | 14/10/2026 | https://aws.amazon.com/architecture/icons/ |
| Thu | **Cost Modeling with AWS Pricing Calculator:** <br> - Model workload assumptions (10 tables, ~40,000 REST API requests/month, ~60,000 Lambda invocations at 256 MB, ~1 GB DynamoDB) in Singapore (`ap-southeast-1`) <br> - Estimate per-service monthly costs ($5.60 base + $2.00 contingency = **$7.60/month**) and define cost optimization controls | 15/10/2026 | 15/10/2026 | https://calculator.aws/ |
| Fri | **Risk Assessment & Bilingual Proposal Completion:** <br> - Analyze static QR abuse mitigation (binding Guest Sessions strictly to `OPEN` bills), concurrent order race conditions (DynamoDB Transactions), and cost protection <br> - Finalize bilingual Vietnamese/English Proposal documentation | 16/10/2026 | 16/10/2026 | https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/welcome.html |

### Week 5 Achievements

* Designed a cohesive AWS Serverless architecture for **SecureTable** aligned with **AWS Well-Architected** principles.
* Produced a clean, standardized AWS architecture diagram accurately reflecting production service interactions.
* Delivered a transparent cost breakdown (**$7.60/month**, **$91.20/year**) backed by AWS Budgets monitoring.
* Defined concrete technical mitigations for QR session security and inventory consistency prior to implementation.
