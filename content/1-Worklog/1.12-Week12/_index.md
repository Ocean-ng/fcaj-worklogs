---
title: "Week 12 Worklog"
date: 2024-01-01
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

### Week 12 Objectives

* Execute comprehensive End-to-End (E2E) functional and security testing of the **SecureTable** platform deployed on AWS (`ap-southeast-1`).
* Reconcile actual AWS usage in **AWS Cost Explorer / Billing** against the **AWS Pricing Calculator** budget estimate, and validate deterministic **Clean-up** procedures.
* Proofread and finalize bilingual content (Vietnamese & English) across all 7 sections of the Hugo internship report website.
* Finalize Live Demo / Production verification artifacts and submit the **First Cloud AI Journey** internship report.

### Tasks Implemented This Week

| Day | Task | Start Date | Completion Date | Reference Material |
|------|-----------|-------------|----------------|---------------|
| Mon | **End-to-End (E2E) Testing of SecureTable:** <br> - Verify the complete workflow: Reception opens table & bill → Guest scans QR & places order → Kitchen completes/rejects dish → Inventory updates stock → Reception closes bill → Admin reviews financials & Audit Logs <br> - Test negative/security edge cases (ordering on closed bills, exceeding available stock, unauthorized role calls) | 30/11/2026 | 30/11/2026 | https://docs.aws.amazon.com/wellarchitected/latest/serverless-applications-lens/opex-testing.html |
| Tue | **Demo Verification & Cost Reconciliation:** <br> - Prepare Live Demo / video walkthrough proving production functionality matches the designed AWS architecture <br> - Compare AWS Billing & Cost Explorer metrics against the AWS Pricing Calculator budget (**$7.60/month**) | 01/12/2026 | 01/12/2026 | https://docs.aws.amazon.com/cost-management/latest/userguide/ce-what-is.html |
| Wed | **Finalizing Blogs, Events, Self-Evaluation & Feedback:** <br> - Verify all technical blog posts (with official AWS references and architecture diagrams) and event reports at the AWS Vietnam office <br> - Proofread `6-Self-evaluation` and `7-Feedback` across both Vietnamese and English versions | 02/12/2026 | 02/12/2026 | https://cloudjourney.awsstudygroup.com/ |
| Thu | **Validating Resource Clean-up Procedures:** <br> - Verify step-by-step post-demo Clean-up instructions (deleting EventBridge Schedules, CloudWatch Alarms, API Gateway/Lambda, DynamoDB tables/PITR, emptying & deleting S3 Buckets, disabling CloudFront Distributions) | 03/12/2026 | 03/12/2026 | https://000007.awsstudygroup.com/ |
| Fri | **GitHub Pages Deployment & Final Submission Review:** <br> - Push finalized files to the GitHub repository (`Ocean-ng/fcaj-worklogs`) and verify GitHub Actions build success <br> - Test all navigation routes, architecture diagrams, code blocks, and VI/EN language switching on the live website | 04/12/2026 | 04/12/2026 | https://ocean-ng.github.io/fcaj-worklogs/ |

### Week 12 Achievements

* Validated **SecureTable**'s End-to-End Serverless workflow on AWS with transactional data integrity, strict RBAC/session security, and full observability.
* Ensured complete cost estimation, optimization strategies, and clean-up documentation to prevent unexpected post-project AWS charges.
* Delivered a polished, bilingual (Vietnamese – English) **First Cloud AI Journey** internship report website meeting all FCAJ template and reference requirements.
* Consolidated three months of practical AWS Cloud and Information Security engineering experience, ready for final project defense.
