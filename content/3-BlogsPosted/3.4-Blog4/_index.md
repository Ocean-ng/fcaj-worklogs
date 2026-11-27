---
title: "Blog 4"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 3.4. </b> "
---

# Protecting Origins Behind Amazon CloudFront with AWS WAF, OAC, and Auto-Rotated Custom Headers

* **Topic:** Edge & Origin Security on AWS
* **Author:** Thuy Nga

---

When deploying web applications on AWS, architectures commonly place **Amazon CloudFront** and **AWS WAF** at the edge to accelerate content delivery and filter malicious Layer 7 traffic (SQL Injection, XSS, HTTP floods). However, a frequent security misconfiguration is **enabling edge protection on CloudFront while leaving the underlying origin directly reachable from the Internet** (such as an S3 Bucket, Application Load Balancer, or API endpoint). If an attacker discovers the origin DNS name or IP address, they can send requests directly to the origin (Origin Bypass), completely circumventing AWS WAF rules at the edge.

![Enhancing Amazon CloudFront Origin Security with AWS WAF and AWS Secrets Manager (Source: AWS Security Blog)](/images/3-BlogsPosted/blog4-cloudfront-waf-origin.png)

### 1. For Amazon S3 Origins: Enforce Origin Access Control (OAC)

When hosting static frontend assets on **Amazon S3**, never configure the bucket for public access. Instead:
* Keep all four **S3 Block Public Access** settings enabled on the bucket.
* Configure **Origin Access Control (OAC)** on CloudFront so CloudFront signs every origin request using **AWS Signature Version 4 (SigV4)** (including native support for SSE-KMS encrypted buckets).
* Restrict the **S3 Bucket Policy** to grant `s3:GetObject` exclusively to the `cloudfront.amazonaws.com` service principal conditioned on `AWS:SourceArn` matching your specific CloudFront Distribution ARN.

### 2. For ALB or Dynamic Origins: Combine AWS WAF with Auto-Rotated Custom Headers

For dynamic origins such as an Internet-facing **Application Load Balancer (ALB)**, enforce strict origin verification following the reference architecture above:
1. **First Line of Defense at the Edge:** Viewers connect to **Amazon CloudFront**, where the edge **AWS WAF** inspects incoming requests and drops malicious payloads close to the source.
2. **Custom Secret Header Injection (`X-Origin-Verify`):** Before forwarding legitimate requests to the origin, CloudFront injects a custom HTTP header `X-Origin-Verify` containing a shared secret value.
3. **Origin Verification:** A regional **AWS WAF** Web ACL attached to the **Origin ALB** inspects the `X-Origin-Verify` header. Any direct Internet request missing this header (or carrying an invalid token) is immediately blocked (`403 Forbidden`). Pairing this with the CloudFront Managed Prefix List on the ALB Security Group adds network-layer defense in depth.
4. **Zero-Downtime Secret Rotation:** To eliminate long-lived static secret risks, **AWS Secrets Manager** and **AWS Lambda** automatically rotate the `X-Origin-Verify` token across both CloudFront and the origin WAF Web ACL using `AWSCURRENT` / `AWSPENDING` staging labels without dropping active traffic.

### Web Tier Security Design Checklist

* Test whether external clients can reach your S3 bucket URL, ALB DNS name, or API origin directly without passing through CloudFront.
* Adopt **Origin Access Control (OAC)** instead of legacy OAI for all S3 origins.
* For ALB origins, combine the CloudFront Managed Prefix List on Security Groups with auto-rotated `X-Origin-Verify` header validation via AWS Secrets Manager.
* Enforce `Redirect HTTP to HTTPS` on CloudFront to guarantee encryption in transit.

### References

1. [How to enhance Amazon CloudFront origin security with AWS WAF and AWS Secrets Manager – AWS Security Blog](https://aws.amazon.com/blogs/security/how-to-enhance-amazon-cloudfront-origin-security-with-aws-waf-and-aws-secrets-manager/)
2. [Restricting access to an Amazon S3 origin (Origin Access Control) – Amazon CloudFront Developer Guide](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/private-content-restricting-access-to-s3.html)
3. [Restricting access to Application Load Balancers – Amazon CloudFront Developer Guide](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/restrict-access-to-load-balancer.html)
4. [AWS WAF Developer Guide](https://docs.aws.amazon.com/waf/latest/developerguide/waf-chapter.html)

`#AWS` `#CloudSecurity` `#CloudFront` `#AWSWAF`
