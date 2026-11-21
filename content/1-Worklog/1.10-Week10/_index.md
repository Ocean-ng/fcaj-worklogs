---
title: "Week 10 Worklog"
date: 2026-11-16
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Week 10 Objectives

* Establish centralized performance monitoring and log aggregation with **Amazon CloudWatch** (Metrics, Logs, Alarms, Dashboards).
* Enable and analyze VPC network traffic using **VPC Flow Logs** to detect rejected connections (`REJECT`) and anomalous port scanning.
* Deploy account-wide API audit logging with **AWS CloudTrail**, enforcing **Log File Integrity Validation**.
* Build real-time automated security alerting via email using **Amazon EventBridge** and **Amazon SNS**.

### Tasks Implemented This Week

| Day | Task | Start Date | Completion Date | Reference Material |
|------|-----------|-------------|----------------|---------------|
| Mon | **Infrastructure Monitoring with Amazon CloudWatch:** <br> - Study CloudWatch Metrics, Namespaces, Dimensions, and CloudWatch Logs <br> - Configure CloudWatch Alarms monitoring CPU Utilization, API Gateway 4xx/5xx error rates, and Lambda invocation errors <br> - Build a unified CloudWatch Dashboard visualizing system health | 16/11/2026 | 16/11/2026 | https://000018.awsstudygroup.com/ |
| Tue | **Network Traffic Analysis with VPC Flow Logs:** <br> - Configure VPC Flow Logs to publish network traffic records to a CloudWatch Log Group <br> - Write **CloudWatch Logs Insights** queries filtering `REJECT` records to identify unauthorized port probes or Security Group misconfigurations | 17/11/2026 | 17/11/2026 | https://000032.awsstudygroup.com/ |
| Wed | **API Audit Logging with AWS CloudTrail:** <br> - Understand AWS CloudTrail's role in auditing *"Who did what, when, and from which IP"* across the AWS account <br> - Create a Multi-Region Trail delivering logs to a dedicated S3 Bucket, encrypted with SSE-KMS and protected by **Log File Integrity Validation** (SHA-256 digest chaining) | 18/11/2026 | 18/11/2026 | https://000032.awsstudygroup.com/ |
| Thu | **Automated Security Alerts with EventBridge & SNS:** <br> - Create an Amazon SNS Topic with an email subscription <br> - Configure Amazon EventBridge Rules matching high-risk CloudTrail events (e.g., Root Console Sign-in, Security Group modifications, KMS key deletion) to trigger instant SNS email alerts | 19/11/2026 | 19/11/2026 | https://000032.awsstudygroup.com/ |
| Fri | **Incident Alerting Verification & Log Retention:** <br> - Trigger a test Security Group rule modification and verify real-time SNS email alert delivery <br> - Set CloudWatch Log Group retention policies (14 days) to prevent unbounded storage costs | 20/11/2026 | 20/11/2026 | https://000018.awsstudygroup.com/ |

### Week 10 Achievements

* Built a centralized observability pipeline using **Amazon CloudWatch** Dashboards and Alarms for proactive operational awareness.
* Analyzed network-level telemetry with **VPC Flow Logs** and CloudWatch Logs Insights to diagnose connectivity issues and spot blocked traffic patterns.
* Established tamper-evident audit logging with **AWS CloudTrail** and **Log File Integrity Validation** for forensic traceability.
* Automated real-time security notifications by integrating **CloudTrail, Amazon EventBridge, and Amazon SNS**.
