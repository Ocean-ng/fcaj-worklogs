---
title: "Week 11 Worklog"
date: 2024-01-01
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Week 11 Objectives

* Conduct cloud security posture reviews and threat checks on the AWS environment using **Amazon GuardDuty** and **AWS Security Hub**.
* Audit the **SecureTable** implementation against the 5 evaluated **AWS Well-Architected Framework** pillars (Operational Excellence, Security, Reliability, Performance Efficiency, and Cost Optimization).
* Compile reproducible Step-by-Step deployment documentation, code snippets, and screenshots for the **Workshop** guide.

### Tasks Implemented This Week

| Day | Task | Start Date | Completion Date | Reference Material |
|------|-----------|-------------|----------------|---------------|
| Mon | **Threat Review with Amazon GuardDuty:** <br> - Study how GuardDuty analyzes CloudTrail Events, VPC Flow Logs, and DNS Logs to detect anomalous behavior <br> - Verify zero suspicious IAM credential or API activity across the project environment | 23/11/2026 | 23/11/2026 | https://docs.aws.amazon.com/guardduty/latest/ug/what-is-guardduty.html |
| Tue | **Security Posture Check with AWS Security Hub:** <br> - Benchmark resource configurations against **AWS Foundational Security Best Practices** <br> - Confirm S3 Block Public Access enforcement, Root MFA status, scoped IAM Roles (no wildcards), and zero exposed secrets | 24/11/2026 | 24/11/2026 | https://docs.aws.amazon.com/securityhub/latest/userguide/what-is-securityhub.html |
| Wed | **Well-Architected Alignment Audit for SecureTable:** <br> - Verify 1-to-1 alignment between the `SecureTable_Architecture.svg` diagram and the deployed AWS environment in `ap-southeast-1` <br> - Review failure handling, DynamoDB transactional consistency, and Serverless auto-scaling characteristics | 25/11/2026 | 25/11/2026 | https://docs.aws.amazon.com/wellarchitected/latest/serverless-applications-lens/welcome.html |
| Thu | **Authoring Step-by-Step Workshop Documentation:** <br> - Document reproducible deployment steps (Prerequisites, S3/CloudFront Frontend, DynamoDB, Cognito/IAM, Lambda/API Gateway, Automation, Security & Cleanup) with syntax-highlighted snippets and console screenshots | 26/11/2026 | 26/11/2026 | https://github.com/thienluhoan/fcj-workshop-template |
| Fri | **Exploring GenAI Security with Amazon Bedrock Guardrails:** <br> - Study modern AI safety controls using **Amazon Bedrock Guardrails** (Prompt Injection defense, PII redaction, IAM policy enforcement) and draft new technical blog posts | 27/11/2026 | 27/11/2026 | https://docs.aws.amazon.com/bedrock/latest/userguide/guardrails.html |

### Week 11 Achievements

* Verified strong security compliance across the AWS account and **SecureTable** resources using **AWS Security Hub** and **Amazon GuardDuty**.
* Confirmed full alignment between the production deployment and the designed architecture across all 5 evaluated **AWS Well-Architected** pillars.
* Structured bilingual Step-by-Step Workshop documentation and expanded technical blog coverage into Generative AI security with **Amazon Bedrock Guardrails**.
