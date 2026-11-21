---
title: "Week 8 Worklog"
date: 2026-11-02
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Week 8 Objectives

* Master data encryption and cryptographic key management on AWS using **AWS Key Management Service (AWS KMS)**.
* Differentiate between AWS Managed Keys and Customer Managed Keys (CMKs), understand Envelope Encryption, and configure automatic Key Rotation.
* Eliminate hardcoded credentials and API keys from source code by adopting **AWS Systems Manager Parameter Store** and **AWS Secrets Manager**.
* Integrate application/Lambda workloads to retrieve encrypted configuration parameters and database credentials securely at runtime.

### Tasks Implemented This Week

| Day | Task | Start Date | Completion Date | Reference Material |
|------|-----------|-------------|----------------|---------------|
| Mon | **Cryptographic Key Management with AWS KMS:** <br> - Study AWS KMS architecture and Envelope Encryption (Data Keys vs. KMS Master Keys) <br> - Create a symmetric Customer Managed Key (CMK), author a Key Policy separating Key Administrators from Key Users <br> - Enable annual Automatic Key Rotation | 02/11/2026 | 02/11/2026 | https://000020.awsstudygroup.com/ |
| Tue | **Multi-Service Data Encryption with KMS:** <br> - Configure S3 Bucket encryption using SSE-KMS with a Customer Managed Key <br> - Verify that an IAM User with `s3:GetObject` permission is still denied access if lacking `kms:Decrypt` permission on the CMK <br> - Practice encrypting and decrypting files via AWS CLI (`aws kms encrypt`, `aws kms decrypt`) | 03/11/2026 | 03/11/2026 | https://000020.awsstudygroup.com/ |
| Wed | **Configuration Management with SSM Parameter Store:** <br> - Explore Systems Manager Parameter Store types (`String`, `StringList`, `SecureString`) <br> - Store hierarchical application parameters (`/app/prod/db-host`, `/app/prod/api-key`) encrypted with a KMS CMK | 04/11/2026 | 04/11/2026 | https://docs.aws.amazon.com/systems-manager/ |
| Thu | **Credential Protection with AWS Secrets Manager:** <br> - Compare use cases and pricing between SSM Parameter Store and AWS Secrets Manager <br> - Store database credentials in AWS Secrets Manager and study automated secret rotation workflows | 05/11/2026 | 05/11/2026 | https://docs.aws.amazon.com/secretsmanager/ |
| Fri | **Runtime Secret Retrieval from AWS Lambda:** <br> - Grant scoped IAM permissions (`ssm:GetParameter`, `secretsmanager:GetSecretValue`, `kms:Decrypt`) to the Lambda Execution Role <br> - Use AWS SDK (`boto3`) to fetch and decrypt `SecureString` parameters in memory, then schedule test KMS keys and secrets for cleanup | 06/11/2026 | 06/11/2026 | https://000020.awsstudygroup.com/ |

### Week 8 Achievements

* Gained deep understanding of Encryption at Rest on AWS using **AWS KMS** and **Envelope Encryption**.
* Implemented dual-layer access control for sensitive S3 objects, requiring both resource permissions (`s3:GetObject`) and cryptographic key permissions (`kms:Decrypt`).
* Eliminated hardcoded secrets in application code by centralizing configurations and credentials in **SSM Parameter Store (`SecureString`)** and **AWS Secrets Manager**.
* Learned when to choose Parameter Store (cost-effective hierarchical configuration) versus Secrets Manager (native automatic rotation for database credentials).
