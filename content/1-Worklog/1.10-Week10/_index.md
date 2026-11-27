---
title: "Week 10 Worklog"
date: 2024-01-01
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Week 10 Objectives

* Strengthen edge and web application protection for **SecureTable** using **AWS WAF** integrated with **Amazon CloudFront**.
* Establish centralized operational monitoring using **Amazon CloudWatch** (Lambda Logs, API Gateway Metrics, and CloudWatch Alarms notifying via SNS).
* Audit AWS account-level management API activity with **AWS CloudTrail**, clearly distinguishing infrastructure logs from DynamoDB business Audit Logs.
* Author and publish technical blogs on the **Shared Responsibility Model**, **Amazon S3 Security**, and **IAM & CloudTrail** to the **AWS Study Group VN** community.

### Tasks Implemented This Week

| Day | Task | Start Date | Completion Date | Reference Material |
|------|-----------|-------------|----------------|---------------|
| Mon | **Edge Protection with AWS WAF on CloudFront:** <br> - Study Web ACLs, AWS Managed Rule Groups (SQLi, XSS, Bad Inputs), and Rate-based Rules in AWS WAF <br> - Test abnormal web request filtering and evaluate CloudFront Free Plan WAF inclusion vs. standalone WAF pricing | 16/11/2026 | 16/11/2026 | https://000026.awsstudygroup.com/ |
| Tue | **Observability with Amazon CloudWatch Logs & Metrics:** <br> - Configure explicit Log Retention policies across all SecureTable Lambda Log Groups to optimize storage costs <br> - Monitor Lambda `Errors`, `Duration`, `Throttles` and API Gateway `4XXError`, `5XXError`, and `Latency` metrics | 17/11/2026 | 17/11/2026 | https://000018.awsstudygroup.com/ |
| Wed | **CloudWatch Alarms & S3 Security Knowledge Sharing:** <br> - Configure CloudWatch Standard Alarms publishing email alerts via Amazon SNS whenever Lambda error counts or API 5XX thresholds breach <br> - Synthesize Shared Responsibility Model & S3 data protection findings and publish to **AWS Study Group VN** | 18/11/2026 | 18/11/2026 | https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/AlarmThatSendsEmail.html |
| Thu | **Account Activity Auditing with AWS CloudTrail:** <br> - Inspect 90-day Management Events in **AWS CloudTrail Event History** in `ap-southeast-1` <br> - Differentiate CloudTrail (AWS control-plane auditing) from DynamoDB Audit Logs (application business traceability) and publish IAM & CloudTrail blog posts | 19/11/2026 | 19/11/2026 | https://docs.aws.amazon.com/awscloudtrail/latest/userguide/view-cloudtrail-events.html |
| Fri | **Error Handling & Alerting Validation:** <br> - Simulate malformed request payloads and error conditions to verify graceful Lambda exception handling and confirm CloudWatch Alarm -> SNS notification delivery | 20/11/2026 | 20/11/2026 | https://000032.awsstudygroup.com/ |

### Week 10 Achievements

* Hardened **SecureTable**'s web perimeter using **AWS WAF** paired with **Amazon CloudFront HTTPS**.
* Satisfied **Operational Excellence** requirements with structured logging, real-time metrics, and automated **CloudWatch + SNS** alerting.
* Established dual-layer audit visibility across **AWS CloudTrail** and **DynamoDB Audit Logs**, while publishing technical knowledge-sharing blogs to **AWS Study Group VN**.
