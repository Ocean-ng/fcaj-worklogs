---
title: "Event 2"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---

# Workshop Report: “AWS Cloud Security & Generative AI Builders Day”

### 1. Event Overview & Objectives

* **Date & Time:** 13:30 – 17:00, 28/10/2026
* **Location:** AWS Vietnam Office – Level 26, Bitexco Financial Tower, District 1, Ho Chi Minh City
* **Core Objectives:**
  - Systematize cloud security design principles aligned with the **Security Pillar** of the **AWS Well-Architected Framework**.
  - Demonstrate how to build a robust **Data Perimeter** using AWS IAM, VPC Endpoints (AWS PrivateLink), and AWS KMS.
  - Showcase automated threat detection and compliance posture management with **Amazon GuardDuty** and **AWS Security Hub**.
  - Introduce data privacy controls and safety guardrails for Generative AI applications using **Amazon Bedrock Guardrails**.

### 2. Key Technical Highlights

#### Defense in Depth on AWS
* Establishing layered security controls across every architectural boundary:
  - **Edge & Application Layer:** Amazon CloudFront, AWS Shield, and AWS WAF mitigating OWASP Top 10 exploits and DDoS traffic.
  - **VPC Network Layer:** Segmenting Public and Private Subnets, enforcing packet filtering with stateful Security Groups and stateless Network ACLs.
  - **Identity & Data Layer:** Enforcing Least-Privilege IAM policies, adopting short-lived credentials via IAM Roles/STS over static access keys, and encrypting data at rest with AWS KMS.

#### Enforcing Data Perimeters with VPC Endpoints
* Analyzing data exfiltration prevention: even if an IAM access key is compromised, external actors cannot read corporate S3 buckets when Bucket Policies enforce `aws:SourceVpce` or `aws:SourceVpc` conditions.
* Practical walkthrough combining **S3 Gateway Endpoints**, **S3 Interface Endpoints**, and **VPC Endpoint Policies** across hybrid cloud networks.

#### Automated Cloud SecOps with GuardDuty, Security Hub & EventBridge
* How **Amazon GuardDuty** identifies threats across CloudTrail, VPC Flow Logs, and DNS logs without agent deployment.
* Using **AWS Security Hub** to aggregate findings and benchmark accounts against the **CIS AWS Foundations Benchmark**.
* Building automated containment playbooks: `GuardDuty Finding` → `Amazon EventBridge` → `AWS Lambda` quarantine execution and `Amazon SNS` alerting.

#### Securing Generative AI Workloads on Amazon Bedrock
* Customer prompts and responses in Amazon Bedrock remain private and are never used to train base foundation models.
* Using **VPC Interface Endpoints (PrivateLink)** to invoke Bedrock APIs privately without Internet exposure, paired with **Bedrock Guardrails** for PII redaction and Prompt Injection defense.

### 3. Key Takeaways & Application to My Internship

* **Direct Reinforcement for My Technical Workshop:** The session on **Data Perimeters** and **VPC Endpoints** deepened my understanding of the `aws:SourceVpce` condition key and **Route 53 Inbound Resolver** hybrid DNS architecture, directly strengthening Chapters 4 and 5 of my **5-Workshop** guide.
* **Career Alignment with Information Assurance:** Seeing how traditional Information Security principles translate into **Cloud Security and DevSecOps**—where security guardrails, compliance audits, and incident containment are codified and automated—gave me a clear roadmap for my career as a Cloud Security Engineer.
* **Immediate Hands-On Practice:** I directly applied the architectures learned at this event during my weekly labs in **Week 8 (KMS & Secrets)**, **Week 9 (CloudFront & WAF)**, **Week 10 (CloudTrail & Flow Logs)**, and **Week 11 (GuardDuty & Security Hub)**.
