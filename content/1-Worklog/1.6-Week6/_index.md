---
title: "Week 6 Worklog"
date: 2024-01-01
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives

* Provision static web hosting and edge content delivery for **SecureTable** using **Amazon S3** and **Amazon CloudFront** in `ap-southeast-1`.
* Implement **Origin Access Control (OAC)** to keep the origin S3 Bucket strictly private (Block Public Access enabled), serving web assets exclusively over CloudFront HTTPS.
* Study private AWS network connectivity using **VPC Endpoints** (Gateway Endpoints and Interface Endpoints / AWS PrivateLink) to minimize public Internet exposure.

### Tasks Implemented This Week

| Day | Task | Start Date | Completion Date | Reference Material |
|------|-----------|-------------|----------------|---------------|
| Mon | **Provisioning Private S3 Bucket for Frontend Assets:** <br> - Create an S3 Bucket in `ap-southeast-1` to store HTML/CSS/JS bundles for SecureTable Guest and Staff portals <br> - Enforce all four **Block Public Access** settings and verify default **SSE-S3** encryption at rest | 19/10/2026 | 19/10/2026 | https://docs.aws.amazon.com/AmazonS3/latest/userguide/security-best-practices.html |
| Tue | **Deploying CloudFront with Origin Access Control (OAC):** <br> - Create a CloudFront Distribution connected to the S3 Origin using **Origin Access Control (SigV4)** <br> - Apply a scoped S3 Bucket Policy granting `s3:GetObject` solely to `cloudfront.amazonaws.com` conditioned on `AWS:SourceArn` | 20/10/2026 | 20/10/2026 | https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/private-content-restricting-access-to-s3.html |
| Wed | **HTTPS Enforcement, Caching & SPA Routing:** <br> - Configure Viewer Protocol Policy to `Redirect HTTP to HTTPS` enforcing TLS 1.2+ <br> - Set Default Root Object (`index.html`), configure Custom Error Responses, and test frontend loading via the CloudFront domain | 21/10/2026 | 21/10/2026 | https://000058.awsstudygroup.com/ |
| Thu | **Private Connectivity Study with VPC Endpoints:** <br> - Compare **Gateway VPC Endpoints** (free route-table routing for S3 and DynamoDB) vs. **Interface VPC Endpoints** (AWS PrivateLink ENIs) <br> - Practice authoring VPC Endpoint Policies scoping traffic strictly to approved S3 buckets and DynamoDB tables | 22/10/2026 | 22/10/2026 | https://000008.awsstudygroup.com/ |
| Fri | **S3 Origin Lockdown Verification & Lab Cleanup:** <br> - Verify direct S3 Object URL requests return `403 Access Denied` while CloudFront HTTPS requests return `200 OK` <br> - Clean up sandbox Interface VPC Endpoints to avoid hourly ENI charges | 23/10/2026 | 23/10/2026 | https://docs.aws.amazon.com/vpc/latest/privatelink/concepts.html |

### Week 6 Achievements

* Deployed **SecureTable**'s web frontend on **Amazon S3 + Amazon CloudFront** with low-latency global edge caching and HTTPS encryption in transit.
* Enforced Security Pillar best practices by keeping the S3 origin completely private via **Block Public Access** and **CloudFront OAC**.
* Mastered private connectivity patterns using **VPC Gateway and Interface Endpoints** for S3 and DynamoDB workloads.
