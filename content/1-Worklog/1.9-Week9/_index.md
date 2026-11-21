---
title: "Week 9 Worklog"
date: 2024-01-01
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Week 9 Objectives

* Understand global content delivery with **Amazon CloudFront (CDN)** and modern web hosting with **AWS Amplify**.
* Implement **Origin Access Control (OAC)** to keep origin S3 buckets completely private while serving assets exclusively through CloudFront over HTTPS.
* Manage SSL/TLS certificates using **AWS Certificate Manager (ACM)** to enforce Encryption in Transit.
* Protect web applications and APIs against common Layer 7 attacks (OWASP Top 10: SQL Injection, Cross-Site Scripting, HTTP floods) using **AWS WAF**.

### Tasks Implemented This Week

| Day | Task | Start Date | Completion Date | Reference Material |
|------|-----------|-------------|----------------|---------------|
| Mon | **Content Delivery with Amazon CloudFront & OAC:** <br> - Study edge caching, Origins, Cache Behaviors, and TTL settings in Amazon CloudFront <br> - Create a CloudFront Distribution connected to a private S3 Bucket using Origin Access Control (OAC) <br> - Update the S3 Bucket Policy to allow read access solely from the `cloudfront.amazonaws.com` service principal | 09/11/2026 | 09/11/2026 | https://000058.awsstudygroup.com/ |
| Tue | **Encryption in Transit with ACM & HTTPS:** <br> - Study automated SSL/TLS certificate provisioning and renewal in AWS Certificate Manager (ACM) <br> - Set CloudFront Viewer Protocol Policy to `Redirect HTTP to HTTPS` and enforce a minimum security policy of `TLSv1.2_2021` | 10/11/2026 | 10/11/2026 | https://docs.aws.amazon.com/acm/ |
| Wed | **Web Application Firewall with AWS WAF:** <br> - Study AWS WAF architecture: Web ACLs, Rule Groups, Managed Rules, and Custom Rules <br> - Provision a Web ACL associated with CloudFront / API Gateway and enable `AWSManagedRulesCommonRuleSet` and `AWSManagedRulesSQLiRuleSet` | 11/11/2026 | 11/11/2026 | https://000026.awsstudygroup.com/ |
| Thu | **Rate-Based Rules & Simulated Attack Testing:** <br> - Configure an AWS WAF Rate-based Rule to block offending source IPs exceeding request thresholds within a 5-minute window <br> - Send simulated SQL Injection and XSS test payloads (`?id=1' OR '1'='1`) and verify AWS WAF blocks requests with `403 Forbidden` | 12/11/2026 | 12/11/2026 | https://000026.awsstudygroup.com/ |
| Fri | **Frontend Hosting with AWS Amplify & Cleanup:** <br> - Explore automated CI/CD build and hosting workflows for web frontends (Next.js / Static Web) on AWS Amplify <br> - Review WAF Sampled Requests metrics and clean up test Web ACLs and CloudFront distributions | 13/11/2026 | 13/11/2026 | https://000026.awsstudygroup.com/ |

### Week 9 Achievements

* Built a secure content delivery architecture using **Amazon CloudFront** with **Origin Access Control (OAC)**, preventing direct public access to S3 origin buckets.
* Enforced Encryption in Transit across all endpoints via HTTPS redirection and modern TLS 1.2+ policies.
* Configured **AWS WAF** Managed Rule Groups and Rate-based Rules to defend web endpoints against OWASP Top 10 exploits (SQLi, XSS) and Layer 7 brute-force/flooding attacks.
* Understood frontend deployment workflows with AWS Amplify.
