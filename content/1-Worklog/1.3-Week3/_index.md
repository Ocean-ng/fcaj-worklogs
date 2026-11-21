---
title: "Week 3 Worklog"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Objectives

* Dive deep into Amazon EC2 virtual servers: Instance Types, Amazon Machine Images (AMI), Key Pairs, and User Data automation.
* Understand block storage architecture with Amazon EBS (Volumes, Snapshots) and shared file storage with Amazon EFS.
* Practice secure access and management of Private Subnet instances using Bastion Hosts and AWS Systems Manager (SSM) Session Manager (zero open SSH ports).
* Learn traffic distribution and elasticity using Application Load Balancer (ALB) and EC2 Auto Scaling.

### Tasks Implemented This Week

| Day | Task | Start Date | Completion Date | Reference Material |
|------|-----------|-------------|----------------|---------------|
| Mon | **Amazon EC2 & User Data Automation:** <br> - Study EC2 instance families (General Purpose, Compute/Memory Optimized) and pricing models <br> - Launch Amazon Linux 2023 and Windows Server EC2 instances <br> - Use User Data scripts to bootstrap and configure a web server (Nginx/Apache) automatically on launch | 28/09/2026 | 28/09/2026 | https://000004.awsstudygroup.com/ |
| Tue | **Amazon EBS Storage & Custom AMIs:** <br> - Explore EBS volume types (`gp3`, `gp2`, `io2`), practice creating, attaching, and expanding EBS volumes <br> - Create EBS Snapshots for backup and package pre-configured instances into Custom AMIs | 29/09/2026 | 29/09/2026 | https://000004.awsstudygroup.com/ |
| Wed | **Secure Administration with SSM Session Manager:** <br> - Compare traditional Bastion Hosts with AWS Systems Manager (SSM) Session Manager <br> - Create an IAM Role with `AmazonSSMManagedInstanceCore` attached to EC2 <br> - Access Private Subnet EC2 shell sessions via browser without opening Inbound Port 22 or managing SSH keys | 30/09/2026 | 30/09/2026 | https://000014.awsstudygroup.com/ |
| Thu | **Application Load Balancer & Auto Scaling:** <br> - Study High Availability compute architecture with Application Load Balancer (ALB) and Target Groups <br> - Configure Launch Templates and Auto Scaling Groups (ASG) to scale EC2 capacity dynamically based on CPU utilization | 01/10/2026 | 01/10/2026 | https://000006.awsstudygroup.com/ |
| Fri | **AWS Fireside Chat Event & Weekly Cleanup:** <br> - Attend *"Fireside Chat with Dr. Werner: Navigating the Future of Cloud & AI in Vietnam"* with Amazon CTO Dr. Werner Vogels at Level 26 Bitexco <br> - Verify ALB fault tolerance and clean up ASG, ALB, EC2 instances, EBS Volumes, and Snapshots | 02/10/2026 | 02/10/2026 | https://000004.awsstudygroup.com/ |

### Week 3 Achievements

* Automated EC2 instance bootstrapping with User Data and standardized server images using Custom AMIs.
* Managed persistent block storage using Amazon EBS Volumes and verified backup/restore workflows with EBS Snapshots.
* Applied security best practices by adopting **AWS Systems Manager Session Manager**, eliminating SSH key exposure and closing Inbound Port 22 on Security Groups.
* Built a highly available, self-healing compute tier using Application Load Balancer and EC2 Auto Scaling Groups.
