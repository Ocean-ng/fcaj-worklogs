---
title: "Blog 2"
date: 2026-10-28
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

# Designing Zero-Internet Exposure Network Architectures with AWS PrivateLink and VPC Endpoints

In many traditional cloud deployments, workloads running in Private Subnets route traffic through a **NAT Gateway** and **Internet Gateway** simply to reach AWS service APIs such as Amazon S3, DynamoDB, KMS, or Secrets Manager. This pattern not only incurs hourly and per-GB NAT Gateway processing charges, but also unnecessarily broadens the network perimeter.

This article summarizes practical lessons from designing a **Zero-Internet Exposure** architecture using **VPC Gateway Endpoints**, **Interface Endpoints (AWS PrivateLink)**, and bidirectional **Data Perimeters**.

---

### 1. Gateway Endpoint vs. Interface Endpoint: Choosing the Right Model

AWS provides two distinct VPC Endpoint architectures operating at different networking layers:

| Criterion | Gateway VPC Endpoint | Interface VPC Endpoint (AWS PrivateLink) |
|---|---|---|
| **Supported Services** | Amazon S3 and Amazon DynamoDB | 100+ AWS services (S3, KMS, SSM, Secrets Manager, ECR...), Partner & Custom PrivateLink services |
| **Routing Mechanism** | Injects a managed Prefix List (`pl-xxxxxx`) into Subnet **Route Tables** | Provisions private **ENI** network interfaces inside Subnets resolved via **DNS** |
| **On-Premises / Cross-VPC Access** | **Not supported** (scoped strictly to the local VPC) | **Fully supported** over Site-to-Site VPN, Direct Connect, and Transit Gateway |
| **Pricing** | **Free of charge** | Hourly fee per ENI + per-GB data processing charge |

**Rule of Thumb:**
* For EC2, ECS, or VPC-attached Lambda workloads accessing Amazon S3 or DynamoDB inside the same VPC → **Always deploy a Gateway Endpoint** to eliminate NAT Gateway data processing fees.
* For on-premises servers (connected via VPN or Direct Connect) requiring private access to Amazon S3 → **Deploy an S3 Interface Endpoint** paired with **Amazon Route 53 Inbound Resolver**.

---

### 2. Solving Hybrid DNS for S3 Interface Endpoints

When an S3 Interface Endpoint is created, AWS generates endpoint-specific DNS names (`*.vpce-0123456789abcdef.s3.us-west-2.vpce.amazonaws.com`). So that on-premises applications can continue using standard S3 URLs (`bucket.s3.us-west-2.amazonaws.com`) seamlessly resolved to private ENI IP addresses:

1. Create a **Route 53 Private Hosted Zone** for `s3.<region>.amazonaws.com` associated with the Cloud VPC, containing `A - Alias` records (`*` and `@`) pointing to the S3 Interface Endpoint.
2. Deploy a **Route 53 Inbound Resolver Endpoint** in the Cloud VPC: On-premises DNS servers forward `*.s3.<region>.amazonaws.com` queries to the Inbound Resolver IP addresses, receiving the private `10.x.x.x` IP of the Interface Endpoint.

---

### 3. Enforcing a Bidirectional Data Perimeter

Deploying a VPC Endpoint alone is insufficient from an Information Security perspective. If an attacker compromises an EC2 instance inside a Private Subnet, they could abuse an unrestricted VPC Endpoint to exfiltrate sensitive data to an external attacker-controlled S3 Bucket.

To establish a bidirectional Data Perimeter, combine both controls below:

1. **Outbound Control (VPC Endpoint Policy):** Restrict the VPC Endpoint so it can only communicate with your organization's designated S3 buckets:
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowOnlyCorporateBucket",
      "Effect": "Allow",
      "Principal": "*",
      "Action": ["s3:GetObject", "s3:PutObject", "s3:ListBucket"],
      "Resource": [
        "arn:aws:s3:::fcaj-internal-data-bucket",
        "arn:aws:s3:::fcaj-internal-data-bucket/*"
      ]
    }
  ]
}
```

2. **Inbound Control (S3 Bucket Policy with `aws:SourceVpce`):** Deny any request to the S3 Bucket that does not originate from the approved VPC Endpoint:
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "DenyAccessNotFromVPCE",
      "Effect": "Deny",
      "Principal": "*",
      "Action": "s3:*",
      "Resource": [
        "arn:aws:s3:::fcaj-internal-data-bucket",
        "arn:aws:s3:::fcaj-internal-data-bucket/*"
      ],
      "Condition": {
        "StringNotEquals": {
          "aws:SourceVpce": "vpce-0123456789abcdef0"
        }
      }
    }
  ]
}
```

Even if an IAM User's Access Key is accidentally leaked outside the corporate network, an external attacker cannot use those credentials to download objects from the bucket because requests from the public Internet fail the `aws:SourceVpce` condition check.
