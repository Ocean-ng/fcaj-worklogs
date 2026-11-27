---
title: "Week 9 Worklog"
date: 2024-01-01
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Week 9 Objectives

* Build automated revenue reporting and scheduled backup pipelines for **SecureTable** using **Amazon EventBridge Scheduler**, **AWS Lambda**, and **Amazon SNS**.
* Configure **DynamoDB Point-in-Time Recovery (PITR)**, weekly **DynamoDB Export to S3**, and long-term storage cost optimization using **S3 Lifecycle Policies** (transitioning archives to S3 Glacier Flexible Retrieval).
* Attend the in-person **AWS Cloud Mastery** technical sharing session at the AWS Vietnam office to refine system architecture practices.

### Tasks Implemented This Week

| Day | Task | Start Date | Completion Date | Reference Material |
|------|-----------|-------------|----------------|---------------|
| Mon | **Configuring Amazon EventBridge Scheduler:** <br> - Study Serverless scheduling with EventBridge Scheduler (timezone-aware `Asia/Ho_Chi_Minh` schedules, retry policies, and DLQs) <br> - Author a dedicated IAM Role permitting Scheduler to invoke only `Report Lambda` and `Backup Lambda` | 09/11/2026 | 09/11/2026 | https://docs.aws.amazon.com/scheduler/latest/UserGuide/what-is-scheduler.html |
| Tue | **Developing `Report Lambda` & Amazon SNS Notifications:** <br> - Implement `Report Lambda` aggregating closed bills, daily/weekly revenue, and ingredient usage from DynamoDB <br> - Create an Amazon SNS Topic, confirm Admin email subscription, and verify automated summary email delivery | 10/11/2026 | 10/11/2026 | https://docs.aws.amazon.com/sns/latest/dg/welcome.html |
| Wed | **Enabling DynamoDB PITR & `Backup Lambda` (Export to S3):** <br> - Enable **Point-in-Time Recovery (PITR)** on critical SecureTable DynamoDB tables <br> - Implement `Backup Lambda` invoking `ExportTableToPointInTime` to export weekly table snapshots to a private S3 Backup Bucket | 11/11/2026 | 11/11/2026 | https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/PointInTimeRecovery.html |
| Thu | **Backup Storage Cost Optimization with S3 Lifecycle:** <br> - Configure **S3 Lifecycle Rules** on the S3 Backup Bucket to transition aging exports to **S3 Glacier Flexible Retrieval** and expire obsolete archives <br> - Document asynchronous export behavior and realistic recovery time expectations | 12/11/2026 | 12/11/2026 | https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lifecycle-mgmt.html |
| Fri | **Automation Verification & AWS Cloud Mastery Event (14/11):** <br> - Verify End-to-End EventBridge Scheduler execution for both reporting and backup workflows <br> - Attend **AWS Cloud Mastery** (Saturday morning, 14/11/2026 at Level 26 Bitexco) to exchange practical Serverless architecture insights | 13/11/2026 | 14/11/2026 | https://aws.amazon.com/blogs/compute/introducing-amazon-eventbridge-scheduler/ |

### Week 9 Achievements

* Delivered a decoupled automation pipeline handling scheduled management reports via **Amazon SNS** and weekly **DynamoDB Exports to S3** via **EventBridge Scheduler**.
* Strengthened **Reliability** and **Cost Optimization** pillars by combining **DynamoDB PITR**, **Export to S3**, and **S3 Lifecycle** tiering.
* Gained actionable architectural feedback from mentors and peers at the **AWS Cloud Mastery** event.
