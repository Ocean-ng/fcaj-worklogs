---
title: "Week 4 Worklog"
date: 2026-10-05
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Objectives

* Understand and practice object storage with Amazon Simple Storage Service (Amazon S3): Storage Classes, Versioning, and Lifecycle Policies.
* Master Amazon S3 data security controls: Block Public Access, Bucket Policies, Server-Side Encryption, and secure temporary sharing via Pre-signed URLs.
* Study managed relational databases with Amazon RDS (Multi-AZ, Read Replicas, Automated Backups) and NoSQL databases with Amazon DynamoDB.
* Practice secure database connectivity from application instances (EC2) to Amazon RDS isolated in Private Subnets.

### Tasks Implemented This Week

| Day | Task | Start Date | Completion Date | Reference Material |
|------|-----------|-------------|----------------|---------------|
| Mon | **Object Storage with Amazon S3:** <br> - Study Amazon S3 architecture (Buckets, Objects, Keys) and storage classes (S3 Standard, Intelligent-Tiering, Glacier) <br> - Create an S3 Bucket, enable Object Versioning, and configure Lifecycle Rules to transition aging data automatically | 05/10/2026 | 05/10/2026 | https://000057.awsstudygroup.com/ |
| Tue | **S3 Security & Pre-signed URLs:** <br> - Configure S3 Block Public Access and author JSON Bucket Policies restricting access by IAM Principal and IP conditions <br> - Explore data-at-rest encryption (SSE-S3, SSE-KMS) <br> - Generate time-limited Pre-signed URLs via AWS CLI for secure uploads/downloads without making buckets public | 06/10/2026 | 06/10/2026 | https://000057.awsstudygroup.com/ |
| Wed | **Managed Relational Databases with Amazon RDS:** <br> - Study Amazon RDS architecture, comparing Multi-AZ Deployments (High Availability) vs. Read Replicas (read scaling) <br> - Create a DB Subnet Group spanning Private Subnets <br> - Provision an RDS MySQL/PostgreSQL instance and restrict its Security Group to accept traffic only from the App Server Security Group | 07/10/2026 | 07/10/2026 | https://000005.awsstudygroup.com/ |
| Thu | **App-to-DB Connectivity & Backups:** <br> - Connect from an EC2 App Server to the Private Subnet RDS instance and initialize a sample schema <br> - Practice manual DB Snapshots, Automated Backups, and Point-in-Time Recovery concepts | 08/10/2026 | 08/10/2026 | https://000005.awsstudygroup.com/ |
| Fri | **Amazon DynamoDB & Weekly Review:** <br> - Explore Amazon DynamoDB NoSQL fundamentals (Partition Key, Sort Key, On-Demand vs. Provisioned Capacity) <br> - Create a DynamoDB table, test item queries, and clean up RDS instances and S3 test buckets | 09/10/2026 | 09/10/2026 | https://000005.awsstudygroup.com/ |

### Week 4 Achievements

* Mastered storage lifecycle management and cost optimization on Amazon S3 using Versioning and Lifecycle Policies.
* Enforced strict S3 security by keeping buckets private, applying fine-grained Bucket Policies and Server-Side Encryption, and using Pre-signed URLs for controlled object access.
* Deployed Amazon RDS securely inside Private Subnets using Security Group chaining and understood Multi-AZ failover mechanisms.
* Understood trade-offs and use cases between relational databases (Amazon RDS) and serverless NoSQL (Amazon DynamoDB).
