---
title: "Week 2 Worklog"
date: 2026-09-21
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Week 2 Objectives

* Master cloud networking architecture on AWS using Amazon Virtual Private Cloud (Amazon VPC).
* Understand IP addressing (CIDR Blocks) and segmenting Public and Private Subnets across multiple Availability Zones.
* Configure network routing using Route Tables, Internet Gateway (IGW), and NAT Gateway.
* Differentiate and implement multi-layered network security using Security Groups (Stateful) and Network ACLs (Stateless).
* Explore advanced connectivity models including VPC Peering and AWS Site-to-Site VPN.

### Tasks Implemented This Week

| Day | Task | Start Date | Completion Date | Reference Material |
|------|-----------|-------------|----------------|---------------|
| Mon | **Amazon VPC Planning:** <br> - Study Amazon VPC concepts and CIDR block calculation (e.g., `10.0.0.0/16`) <br> - Design a Multi-AZ network topology with Public and Private Subnets <br> - Create a Custom VPC and Subnets on the AWS Management Console | 21/09/2026 | 21/09/2026 | https://000003.awsstudygroup.com/ |
| Tue | **Routing & Internet Connectivity:** <br> - Understand Route Tables and Internet Gateway (IGW) mechanisms <br> - Attach an IGW to the VPC and configure the Public Route Table (`0.0.0.0/0` -> IGW) <br> - Enable Auto-assign Public IPv4 addressing on Public Subnets | 22/09/2026 | 22/09/2026 | https://000003.awsstudygroup.com/ |
| Wed | **Network Security (Security Groups & NACLs):** <br> - Analyze differences between Security Groups (instance-level, stateful) and Network ACLs (subnet-level, stateless) <br> - Configure Inbound/Outbound rules restricting source IPs and ports <br> - Test packet filtering behavior for ICMP, SSH, and HTTP traffic | 23/09/2026 | 23/09/2026 | https://000003.awsstudygroup.com/ |
| Thu | **NAT Gateway for Private Subnets:** <br> - Address the requirement for Private Subnet instances to download patches from the Internet without exposing a public IP <br> - Provision a NAT Gateway in the Public Subnet with an Elastic IP <br> - Update the Private Route Table to route outbound traffic through the NAT Gateway | 24/09/2026 | 24/09/2026 | https://000003.awsstudygroup.com/ |
| Fri | **VPC Peering & Site-to-Site VPN:** <br> - Practice private inter-VPC communication using VPC Peering and bidirectional route updates <br> - Study AWS Site-to-Site VPN components (Virtual Private Gateway, Customer Gateway) <br> - Clean up NAT Gateway, Elastic IP, and lab resources to prevent idle charges | 25/09/2026 | 25/09/2026 | https://000003.awsstudygroup.com/ <br> https://000019.awsstudygroup.com/ |

### Week 2 Achievements

* Designed and provisioned a complete Multi-AZ Custom VPC isolating public-facing resources from internal private workloads.
* Mastered packet routing flows across Route Tables, Internet Gateways, and NAT Gateways.
* Applied Defense-in-Depth network security by combining subnet-level NACLs and instance-level Security Groups, clearly distinguishing stateful and stateless behavior during troubleshooting.
* Gained foundational knowledge of inter-VPC connectivity via VPC Peering and hybrid cloud connections via Site-to-Site VPN.
