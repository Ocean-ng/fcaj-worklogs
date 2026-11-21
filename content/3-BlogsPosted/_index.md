---
title: "Blogs Posted"
date: 2026-11-15
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

> This section compiles technical articles and translated deep-dives focusing on AWS Cloud Security, Zero-Internet network architectures, and fine-grained identity governance authored during the **AWS First Cloud AI Journey (FCAJ)** internship.

### [Blog 1 - Enforcing Least Privilege in Kubernetes with Session Policies in Amazon EKS Pod Identity](3.1-Blog1/)
An in-depth look at **Session Policies** in **Amazon EKS Pod Identity**, enabling engineers to dynamically scope down IAM permissions per Kubernetes Pod/ServiceAccount through permission intersection without proliferating hundreds of distinct IAM Roles across large clusters.

### [Blog 2 - Designing Zero-Internet Exposure Network Architectures with AWS PrivateLink and VPC Endpoints](3.2-Blog2/)
A technical guide to eliminating public Internet traversal when connecting workloads in Private Subnets or On-premises data centers to Amazon S3 and AWS services. Covers Gateway vs. Interface Endpoints, hybrid DNS resolution with Route 53 Resolver, and enforcing data perimeters with VPC Endpoint Policies.

### [Blog 3 - Automating Threat Detection and Security Incident Response on AWS with GuardDuty, Security Hub, and EventBridge](3.3-Blog3/)
A practical blueprint for automated Cloud SecOps on AWS: combining ML-powered threat detection in Amazon GuardDuty, continuous CIS Benchmark compliance scoring in AWS Security Hub, and event-driven containment and alerting via Amazon EventBridge and AWS Lambda.
