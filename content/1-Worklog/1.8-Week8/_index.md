---
title: "Week 8 Worklog"
date: 2024-01-01
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Week 8 Objectives

* Design and provision **Amazon DynamoDB** tables for **SecureTable** (tables, bills, menu items, orders, ingredient inventory, financials, and business Audit Logs).
* Implement and integrate core **AWS Lambda** functions: `GuestServices`, `Ordering`, `Reception`, `Kitchen`, `Inventory`, and `AdminDashboard`.
* Apply **DynamoDB Transactions**, **Conditional Expressions**, and **Idempotency-Keys** to guarantee inventory consistency under concurrent customer ordering.
* Study AWS encryption options (KMS CMK vs. default SSE-S3 / DynamoDB AWS-owned keys) and ensure zero hardcoded credentials in source code.

### Tasks Implemented This Week

| Day | Task | Start Date | Completion Date | Reference Material |
|------|-----------|-------------|----------------|---------------|
| Mon | **Amazon DynamoDB Data Modeling & Provisioning:** <br> - Design Partition Keys, Sort Keys, and Global Secondary Indexes (GSIs) for Tables, Bills, Orders, Ingredients, Financials, and Audit Logs <br> - Provision DynamoDB tables in `ap-southeast-1` with Encryption at Rest enabled | 02/11/2026 | 02/11/2026 | https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/best-practices.html |
| Tue | **Developing `GuestServices` & `Ordering` Lambdas:** <br> - Implement menu availability queries (`GET /v1/guest/menu`) based on real-time stock <br> - Build `Ordering Lambda` using **DynamoDB `TransactWriteItems`** and `Idempotency-Key` validation to atomically record orders and reserve ingredients, preventing negative stock race conditions | 03/11/2026 | 03/11/2026 | https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/transaction-apis.html |
| Wed | **Developing `Reception`, `Kitchen` & `Inventory` Lambdas:** <br> - Implement Reception table opening, `CLOSING` state transition, and bill settlement workflows <br> - Implement Kitchen dish completion (committing ingredient deduction) and dish rejection (releasing reserved stock) <br> - Build Inventory stock-in and adjustment tracking APIs | 04/11/2026 | 04/11/2026 | https://docs.aws.amazon.com/lambda/latest/dg/welcome.html |
| Thu | **`AdminDashboard` & Business Audit Logging:** <br> - Build revenue and ingredient consumption aggregation endpoints for Admin users <br> - Record structured **Business Audit Logs** (actor, action, timestamp, before/after state) in DynamoDB for sensitive actions such as stock adjustments and bill closures | 05/11/2026 | 05/11/2026 | https://000022.awsstudygroup.com/ |
| Fri | **Evaluating Encryption & Secret Trade-Offs:** <br> - Study **AWS KMS** and **Secrets Manager** pricing vs. Serverless security needs <br> - Adopt free default encryption (**SSE-S3** and DynamoDB **AWS-owned keys**) paired with **IAM Execution Role (SigV4)** access so Lambda requires zero static DB passwords and incurs zero monthly KMS/Secrets fees | 06/11/2026 | 06/11/2026 | https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/EncryptionAtRest.html |

### Week 8 Achievements

* Delivered the core **Amazon DynamoDB** persistence tier and business **AWS Lambda** functions powering **SecureTable**.
* Eliminated concurrent ordering race conditions and duplicate submissions using **DynamoDB Transactions**, **Conditional Expressions**, and **Idempotency-Keys**.
* Established end-to-end operational traceability with immutable business **Audit Logs** in DynamoDB.
* Verified strict secret hygiene across all backend configurations and repositories.
