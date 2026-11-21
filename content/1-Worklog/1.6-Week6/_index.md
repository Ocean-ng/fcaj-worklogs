---
title: "Week 6 Worklog"
date: 2024-01-01
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives

* Master private network connectivity on AWS using **VPC Endpoints** (Gateway Endpoints and Interface Endpoints / AWS PrivateLink).
* Deploy an **S3 Gateway Endpoint** enabling EC2 instances in Private Subnets to access Amazon S3 entirely over the AWS private network without a NAT Gateway or Internet Gateway.
* Deploy an **S3 Interface Endpoint** and simulate hybrid on-premises connectivity with **Amazon Route 53 Resolver**.
* Implement and verify **VPC Endpoint Policies** combined with **S3 Bucket Policies** to enforce strict data perimeter controls.

### Tasks Implemented This Week

| Day | Task | Start Date | Completion Date | Reference Material |
|------|-----------|-------------|----------------|---------------|
| Mon | **VPC Endpoints Overview & Lab Provisioning:** <br> - Compare Gateway Endpoints (free, route-table based for S3/DynamoDB) vs. Interface Endpoints (ENI-based, powered by AWS PrivateLink) <br> - Provision the lab VPC and Private Subnet EC2 instances using CloudFormation | 19/10/2026 | 19/10/2026 | https://000008.awsstudygroup.com/ |
| Tue | **Deploying & Testing S3 Gateway Endpoint:** <br> - Create an S3 Gateway Endpoint associated with the Private Subnet Route Table <br> - Verify the S3 Prefix List added to the Route Table <br> - Connect to the Private EC2 via SSM Session Manager and verify private S3 access (`aws s3 ls`, `aws s3 cp`) without Internet access | 20/10/2026 | 20/10/2026 | https://000008.awsstudygroup.com/ |
| Wed | **Deploying S3 Interface Endpoint for Hybrid Access:** <br> - Provision a simulated On-premises network environment connected to the cloud VPC <br> - Create an S3 Interface Endpoint with a Security Group allowing HTTPS (443) from the On-premises CIDR <br> - Test S3 access using the endpoint-specific DNS name via `--endpoint-url` | 21/10/2026 | 21/10/2026 | https://000008.awsstudygroup.com/ |
| Thu | **Hybrid DNS with Route 53 Private Hosted Zone & Resolver:** <br> - Configure a Route 53 Private Hosted Zone with Alias records pointing to the S3 Interface Endpoint <br> - Configure Route 53 Inbound Resolver Endpoints so On-premises hosts resolve S3 domains to private ENI IP addresses (verified via `dig`) | 22/10/2026 | 22/10/2026 | https://000008.awsstudygroup.com/ |
| Fri | **Securing Access with VPC Endpoint Policies & Cleanup:** <br> - Author a custom JSON VPC Endpoint Policy restricting access to a single designated S3 Bucket <br> - Configure an S3 Bucket Policy using the `aws:SourceVpce` condition key to block non-endpoint access <br> - Document steps and screenshots for the Workshop section and clean up lab stacks | 23/10/2026 | 23/10/2026 | https://000008.awsstudygroup.com/ |

### Week 6 Achievements

* Mastered the architectural, routing, and cost differences between **S3 Gateway Endpoints** and **S3 Interface Endpoints (AWS PrivateLink)**.
* Established end-to-end private connectivity to Amazon S3 from both cloud Private Subnets and simulated On-premises networks without traversing the public Internet.
* Configured hybrid DNS resolution using **Amazon Route 53 Private Hosted Zones** and **Inbound Resolver Endpoints**.
* Enforced a strong data perimeter by combining **VPC Endpoint Policies** with **S3 Bucket Policies (`aws:SourceVpce`)**, forming the core technical foundation of the Workshop guide.
