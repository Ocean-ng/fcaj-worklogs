---
title: "Week 5 Worklog"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Week 5 Objectives

* Study the core principles of the **AWS Well-Architected Framework** in preparation for the team project phase.
* Collaborate with teammates to survey small restaurant workflows and finalize the **SecureTable** project scope (an AWS Serverless Ingredient Management and QR Code Ordering System in `ap-southeast-1`).
* Define clear team role boundaries: taking ownership of **Frontend development (Guest & Staff UI), client-side security integration, S3 + CloudFront hosting, and product Demo production**.
* Review the team's architecture diagram, 5-role access model, and monthly budget estimate.

### Tasks Implemented This Week

| Day | Task | Start Date | Completion Date | Reference Material |
|------|-----------|-------------|----------------|---------------|
| Mon | **AWS Well-Architected Framework Study:** <br> - Read overview documentation on the 6 AWS Well-Architected pillars, focusing on Security and Cost Optimization for small workloads | 12/10/2026 | 12/10/2026 | https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html |
| Tue | **Team Problem Survey & Serverless Architecture Alignment:** <br> - Discuss operational pain points in small restaurants (paper order mistakes, stock discrepancies, manual revenue tallying) <br> - Agree as a team on a **100% AWS Serverless** stack (S3, CloudFront, API Gateway, Lambda, DynamoDB, Cognito, EventBridge Scheduler, SNS) instead of EC2/RDS to stay under a $10/month budget | 13/10/2026 | 13/10/2026 | https://aws.amazon.com/serverless/ |
| Wed | **Team Role Allocation & User Flow Mapping:** <br> - Finalize 4-member responsibilities: taking charge of **Frontend Web (React/Vite), security UI integration, and Product Demo** <br> - Map out screen-by-screen interactions for the 5 user roles: `Guest` (QR ordering), `Reception`, `Kitchen`, `Inventory`, and `Admin` | 14/10/2026 | 14/10/2026 | https://docs.aws.amazon.com/wellarchitected/latest/serverless-applications-lens/web-applications.html |
| Thu | **Reviewing Architecture Diagram & Budget Estimate:** <br> - Walk through browser-to-cloud request flows (**CloudFront + S3** -> **API Gateway / Cognito**) with teammates on `SecureTable_Architecture` <br> - Review the monthly cost estimate (~$7.60/month for a 10-table setup) referenced against AWS Pricing Calculator | 15/10/2026 | 15/10/2026 | https://calculator.aws/ |
| Fri | **QR Session Risk Review & Team Proposal Finalization:** <br> - Discuss static table QR security limitations with the team (binding Guest Sessions strictly to `OPEN` bills) <br> - Proofread the team's bilingual Vietnamese/English **Proposal** document | 16/10/2026 | 16/10/2026 | https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/welcome.html |

### Week 5 Achievements

* Clarified **SecureTable**'s functional scope and my exact responsibilities within the team (Frontend UI, S3/CloudFront delivery, and Product Demo).
* Understood the cost and operational rationale behind choosing **AWS Serverless** over traditional EC2/RDS instances.
* Mapped out user journeys across all 5 roles to prepare for UI design and frontend scaffolding in Week 6.
