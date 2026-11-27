---
title: "Week 11 Worklog"
date: 2024-01-01
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Week 11 Objectives

* Study cloud threat detection and posture management services (**Amazon GuardDuty**, **AWS Security Hub**) and evaluate security-vs-cost trade-offs for Serverless workloads.
* Manually audit AWS account configurations against **AWS Foundational Security Best Practices / CIS Benchmarks** and verify **SecureTable** against the 5 evaluated **AWS Well-Architected Framework** pillars.
* Compile reproducible Step-by-Step deployment documentation, code snippets, and screenshots for the **Workshop** guide.

### Tasks Implemented This Week

| Day | Task | Start Date | Completion Date | Reference Material |
|------|-----------|-------------|----------------|---------------|
| Mon | **Studying Amazon GuardDuty & Serverless Cost Trade-Offs:** <br> - Study how GuardDuty analyzes CloudTrail, VPC Flow Logs, and DNS Logs <br> - Evaluate cost-effectiveness: since SecureTable is 100% Serverless (no VPC/EC2) under a <$10/month budget, document why application-layer controls (Cognito, Least-Privilege IAM, WAF, Audit Logs) are prioritized over paid GuardDuty ingestion | 23/11/2026 | 23/11/2026 | https://docs.aws.amazon.com/guardduty/latest/ug/what-is-guardduty.html |
| Tue | **Manual Security Audit via AWS Security Best Practices:** <br> - Study **AWS Security Hub / CIS Benchmark** controls and perform a manual compliance check across the project account <br> - Verify S3 Block Public Access on all buckets, Root MFA enforcement, scoped IAM Roles (no `*` wildcards), and zero leaked secrets in Git | 24/11/2026 | 24/11/2026 | https://docs.aws.amazon.com/securityhub/latest/userguide/fsbp-standard.html |
| Wed | **Well-Architected Alignment Audit for SecureTable:** <br> - Verify 1-to-1 alignment between the `SecureTable_Architecture.svg` diagram and the deployed AWS environment in `ap-southeast-1` <br> - Review failure handling, DynamoDB transactional consistency, and Serverless auto-scaling characteristics | 25/11/2026 | 25/11/2026 | https://docs.aws.amazon.com/wellarchitected/latest/serverless-applications-lens/welcome.html |
| Thu | **Authoring Step-by-Step Workshop Documentation:** <br> - Document reproducible deployment steps (Prerequisites, S3/CloudFront Frontend, DynamoDB, Cognito/IAM, Lambda/API Gateway, Automation, Security & Cleanup) with syntax-highlighted snippets and console screenshots | 26/11/2026 | 26/11/2026 | https://github.com/thienluhoan/fcj-workshop-template |
| Fri | **Exploring GenAI Security with Amazon Bedrock Guardrails:** <br> - Study modern AI safety controls using **Amazon Bedrock Guardrails** (Prompt Injection defense, PII redaction, IAM policy enforcement) and draft new technical blog posts | 27/11/2026 | 27/11/2026 | https://docs.aws.amazon.com/bedrock/latest/userguide/guardrails.html |

### Week 11 Achievements

* Understood **Amazon GuardDuty** and **AWS Security Hub** capabilities while making justified cost-aware security trade-offs for a sub-$10/month Serverless architecture.
* Confirmed full alignment between the production deployment and the designed architecture across all 5 evaluated **AWS Well-Architected** pillars.
* Structured bilingual Step-by-Step Workshop documentation and expanded technical blog coverage into Generative AI security with **Amazon Bedrock Guardrails**.
