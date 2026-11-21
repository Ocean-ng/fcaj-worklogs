---
title: "Blog 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Enforcing Least Privilege in Kubernetes with Session Policies in Amazon EKS Pod Identity

In enterprise Kubernetes (Amazon EKS) environments, granting Pods fine-grained access to AWS resources (such as Amazon S3, DynamoDB, or Secrets Manager) in strict accordance with the **Principle of Least Privilege** is a persistent challenge. Creating a dedicated IAM Role for every microservice or namespace leads to IAM Role sprawl and quickly exhausts AWS account IAM quotas.

**Session Policies** in **Amazon EKS Pod Identity** solve this problem by allowing platform teams to reuse a shared base IAM Role while dynamically scoping down effective permissions per Pod at session issuance time.

---

### 1. How Session Policies Work in EKS Pod Identity

When a Pod in Amazon EKS requests temporary AWS credentials through the EKS Pod Identity Agent, the EKS control plane invokes the AWS Security Token Service (STS) `AssumeRoleForPodIdentity` API.

With **Session Policies**, you can attach an inline IAM policy directly to a **Pod Identity Association** (the binding between a Kubernetes `ServiceAccount`, `Namespace`, and `IAM Role`).

Key evaluation rule:
* **Effective Permissions** = **Intersection** of the `IAM Role Identity-based Policy` and the `Session Policy`.
* A Session Policy can **only restrict (narrow)** permissions granted by the base IAM Role; it can **never escalate** permissions beyond what the base IAM Role allows.

---

### 2. Practical Use Case

Suppose you manage a shared S3 Bucket named `fcaj-shared-artifacts-bucket` storing artifacts for multiple tenant workloads (`team-alpha`, `team-beta`).

Instead of maintaining 20 separate IAM Roles for 20 microservices, you can:
1. Create **one base IAM Role** (`EKS-S3-Base-Role`) allowing read/write operations across `arn:aws:s3:::fcaj-shared-artifacts-bucket/*`.
2. When associating this Role with `team-alpha`'s `ServiceAccount`, attach a **Session Policy** scoping access strictly to the `team-alpha/*` prefix:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:GetObject",
        "s3:PutObject"
      ],
      "Resource": "arn:aws:s3:::fcaj-shared-artifacts-bucket/team-alpha/*"
    }
  ]
}
```

Because effective permissions are the intersection of both policies, `team-alpha` Pods cannot access objects under `team-beta/*`, even though they share `EKS-S3-Base-Role`.

---

### 3. Configuring via AWS CLI

You can create or update a Pod Identity Association with a Session Policy directly through the AWS CLI:

```bash
aws eks create-pod-identity-association \
  --cluster-name fcaj-prod-cluster \
  --namespace team-alpha \
  --service-account alpha-worker-sa \
  --role-arn arn:aws:iam::123456789012:role/EKS-S3-Base-Role \
  --policy file://session-policy-alpha.json
```

---

### 4. Security and Operational Takeaways

* **Eliminates Over-Permissioning:** Prevents lateral movement across prefixes or tables if a single microservice Pod is compromised.
* **Prevents IAM Role Sprawl:** Reduces the number of IAM Roles by 70–80% in multi-tenant EKS clusters, avoiding IAM quota limits.
* **Cross-Account Compatibility:** Works seamlessly with IAM Role chaining for workloads accessing resources across AWS Organizations accounts.
* **Clear Separation of Duties:** Cloud Security teams define the maximum permission boundary on the base IAM Role, while Platform teams further tighten per-pod permissions via Session Policies.
