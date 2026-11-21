---
title: "Week 11 Worklog"
date: 2024-01-01
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Week 11 Objectives

* Explore intelligent threat detection and Cloud Security Posture Management (CSPM) services: **Amazon GuardDuty**, **AWS Security Hub**, and **AWS Config**.
* Assess account security compliance against industry standards including **CIS AWS Foundations Benchmark** and **AWS Foundational Security Best Practices**.
* Learn **Infrastructure as Code (IaC)** using **AWS CloudFormation** to standardize and automate network and security provisioning.
* Remediate high-priority configuration findings identified by AWS Security Hub.

### Tasks Implemented This Week

| Day | Task | Start Date | Completion Date | Reference Material |
|------|-----------|-------------|----------------|---------------|
| Mon | **Threat Detection with Amazon GuardDuty:** <br> - Study how Amazon GuardDuty uses Machine Learning and threat intelligence feeds to analyze CloudTrail Events, VPC Flow Logs, and DNS Logs <br> - Enable GuardDuty (30-day Free Trial), generate Sample Findings, and analyze Low/Medium/High severity threat categories | 23/11/2026 | 23/11/2026 | https://docs.aws.amazon.com/guardduty/ |
| Tue | **Security Posture Management with AWS Security Hub:** <br> - Enable AWS Security Hub along with `AWS Foundational Security Best Practices` and `CIS AWS Foundations Benchmark` <br> - Evaluate the overall account Security Score and inspect failed security controls | 24/11/2026 | 24/11/2026 | https://docs.aws.amazon.com/securityhub/ |
| Wed | **Security Finding Remediation:** <br> - Remediate high-priority Security Hub findings: enforce account-level S3 Block Public Access, restrict all VPC Default Security Groups, rotate aging IAM Access Keys, and verify MFA enforcement | 25/11/2026 | 25/11/2026 | https://docs.aws.amazon.com/securityhub/ |
| Thu | **Infrastructure as Code with AWS CloudFormation:** <br> - Study AWS CloudFormation YAML template anatomy (`Parameters`, `Resources`, `Outputs`, `Mappings`) <br> - Codify the Workshop VPC, Private/Public Subnets, Route Tables, Security Groups, and EC2 resources into a reusable CloudFormation template | 26/11/2026 | 26/11/2026 | https://000037.awsstudygroup.com/ |
| Fri | **Stack Deployment Verification & Cleanup:** <br> - Test one-click provisioning (`Create Stack`) and deterministic teardown (`Delete Stack`) via CloudFormation <br> - Disable GuardDuty and Security Hub after evaluation to prevent post-trial charges | 27/11/2026 | 27/11/2026 | https://000037.awsstudygroup.com/ |

### Week 11 Achievements

* Understood how **Amazon GuardDuty** continuously detects compromised IAM credentials, cryptocurrency mining, and command-and-control traffic without agent installation.
* Evaluated and improved the AWS account's security posture using **AWS Security Hub** aligned with the **CIS AWS Foundations Benchmark**.
* Adopted **AWS CloudFormation (IaC)** to provision and tear down multi-tier cloud environments reliably, eliminating manual configuration drift and orphaned billable resources.
