---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Secure Hybrid Access to S3 using VPC Endpoints

#### Overview

**AWS PrivateLink** provides private connectivity to AWS services from VPCs and on-premises networks without exposing traffic to the public Internet.

In this hands-on workshop, you will create, configure, and verify **VPC Endpoints** that enable workloads to reach Amazon S3 entirely over the AWS private network.

You will deploy two types of VPC endpoints to access Amazon S3: a **Gateway VPC Endpoint** and an **Interface VPC Endpoint**. Each endpoint type offers distinct architectural benefits depending on whether traffic originates inside an AWS VPC or from an on-premises data center:
+ **Gateway Endpoint** — Routes traffic from your VPC to Amazon S3 or DynamoDB over the AWS private network at no additional cost using Route Table prefix lists.
+ **Interface Endpoint (AWS PrivateLink)** — Provisions Elastic Network Interfaces (ENIs) with private IP addresses in your subnets, enabling private connectivity from both cloud VPCs and on-premises environments (via Site-to-Site VPN or Direct Connect) integrated with **Amazon Route 53 Private DNS and Inbound Resolver**.

#### Workshop Contents

1. [Workshop Overview](5.1-Workshop-overview/)
2. [Prerequisites](5.2-Prerequiste/)
3. [Access S3 from VPC using Gateway Endpoint](5.3-S3-vpc/)
4. [Access S3 from On-premises using Interface Endpoint & Route 53](5.4-S3-onprem/)
5. [Securing Access with VPC Endpoint Policies](5.5-Policy/)
6. [Clean up Resources](5.6-Cleanup/)
