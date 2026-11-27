---
title: "Blog 5"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 3.5. </b> "
---

# Automating Time-Based Serverless Workflows with Amazon EventBridge Scheduler, AWS Lambda, and DynamoDB

* **Topic:** Serverless Automation & Reliability on AWS
* **Author:** Thuy Nga

---

In production cloud systems—such as sending daily revenue summaries, triggering weekly database backups, expiring stale sessions, or revoking access at the end of a billing cycle—**time-based task scheduling** is a foundational requirement. Running a dedicated 24/7 EC2 instance solely to execute `crontab` jobs wastes compute budget during idle hours and introduces a single point of failure if the instance goes unhealthy.

**Amazon EventBridge Scheduler** addresses this with a fully **Serverless** task scheduler capable of managing anything from a few recurring jobs to millions of per-user one-time schedules with zero server maintenance.

![Time-based Serverless Architecture with Amazon EventBridge Scheduler, AWS Lambda, and DynamoDB (Source: AWS Compute Blog)](/images/3-BlogsPosted/blog5-eventbridge-scheduler.png)

### 1. Key Capabilities of EventBridge Scheduler

* **Recurring and Auto-Deleting One-Time Schedules:** Alongside familiar `cron()` and `rate()` expressions, applications can dynamically create one-time `at(yyyy-mm-ddThh:mm:ss)` schedules from Lambda (as shown in the diagram for subscription expiration workflows) and set `ActionAfterCompletion = DELETE` so completed schedules clean themselves up automatically.
* **Built-In Timezone Support:** Select local timezones directly (such as `Asia/Ho_Chi_Minh`) without manual UTC offset calculations.
* **270+ Universal AWS Service Targets:** Beyond invoking **AWS Lambda**, EventBridge Scheduler can call AWS APIs directly across **Amazon SNS**, **Amazon SQS**, **Amazon DynamoDB** (e.g., `ExportTableToPointInTime`), and **AWS Step Functions**.

### 2. Reliability and Least-Privilege IAM Controls

* **Retry Policies & Dead-Letter Queues (DLQs):** If a target Lambda function experiences transient errors or throttling at trigger time, EventBridge Scheduler automatically retries according to your configured backoff policy and routes exhausted events to an **Amazon SQS DLQ** so critical jobs are never silently lost.
* **Flexible Time Windows:** For batch reporting or backup schedules that do not need to fire at the exact `00:00:00` second, configuring a Flexible Time Window (e.g., 15 minutes) spreads invocations evenly and prevents sudden read/write spikes against downstream **Amazon DynamoDB** tables.
* **Scoped IAM Execution Roles:** EventBridge Scheduler assumes a dedicated **IAM Execution Role** whose Trust Policy trusts `scheduler.amazonaws.com` and grants `lambda:InvokeFunction` strictly on the target function ARNs.

### Practical Implementation Checklist

* Choose `ActionAfterCompletion = DELETE` for one-time `at()` schedules to prevent orphaned schedule clutter.
* Explicitly set the business timezone (`Asia/Ho_Chi_Minh`) on daily and weekly reporting schedules.
* Attach an **SQS Dead-Letter Queue** and monitor `InvocationDroppedCount` in CloudWatch for critical workflows like database backups and financial summaries.
* Design target Lambda handlers to be **idempotent** so a retry never duplicates records or double-sends reports.

### References

1. [Introducing Amazon EventBridge Scheduler – AWS Compute Blog](https://aws.amazon.com/blogs/compute/introducing-amazon-eventbridge-scheduler/)
2. [What is Amazon EventBridge Scheduler? – User Guide](https://docs.aws.amazon.com/scheduler/latest/UserGuide/what-is-scheduler.html)
3. [Managing schedule retries and dead-letter queues – EventBridge Scheduler User Guide](https://docs.aws.amazon.com/scheduler/latest/UserGuide/managing-schedule-dlq.html)
4. [Identity and Access Management for Amazon EventBridge Scheduler](https://docs.aws.amazon.com/scheduler/latest/UserGuide/security-iam.html)

`#AWS` `#Serverless` `#EventBridge` `#AWSLambda`
