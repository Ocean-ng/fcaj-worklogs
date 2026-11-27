---
title: "Week 7 Worklog"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Week 7 Objectives

* Build staff authentication and role-based access control (RBAC) for **SecureTable** using **Amazon Cognito User Pools** (`Reception`, `Kitchen`, `Inventory`, `Admin` groups).
* Design a temporary **Guest Session Token** mechanism for table QR ordering without requiring customer registration, strictly bound to active (`OPEN`) bills.
* Configure **Amazon API Gateway (REST API)** with a **Cognito Authorizer** protecting internal staff routes while separating guest endpoints.
* Author scoped **AWS IAM Execution Roles** following the **Principle of Least Privilege** for each AWS Lambda function.

### Tasks Implemented This Week

| Day | Task | Start Date | Completion Date | Reference Material |
|------|-----------|-------------|----------------|---------------|
| Mon | **Setting Up Amazon Cognito User Pool for Staff:** <br> - Create a Cognito User Pool in `ap-southeast-1`, enforcing password policies and email verification <br> - Configure Cognito User Groups for the 4 staff roles (`Reception`, `Kitchen`, `Inventory`, `Admin`) and register the web App Client | 26/10/2026 | 26/10/2026 | https://docs.aws.amazon.com/cognito/latest/developerguide/cognito-user-identity-pools.html |
| Tue | **Authoring Least-Privilege IAM Execution Roles:** <br> - Separate IAM Execution Roles per Lambda domain instead of sharing a single wildcard (`*`) role <br> - Scope IAM policies strictly to required actions (`dynamodb:GetItem`, `dynamodb:PutItem`, `dynamodb:TransactWriteItems`) and specific DynamoDB table ARNs | 27/10/2026 | 27/10/2026 | https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html |
| Wed | **Configuring API Gateway & Cognito Authorizer:** <br> - Structure REST API routes (`/v1/guest/*` and `/v1/staff/*`) on Amazon API Gateway <br> - Attach a **Cognito User Pool Authorizer** enforcing JWT verification on `/v1/staff/*`, paired with group-level RBAC validation inside Lambda handlers | 28/10/2026 | 28/10/2026 | https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-integrate-with-cognito.html |
| Thu | **Implementing Scoped Guest Session Security:** <br> - Build the `POST /v1/guest/sessions` flow: issue a Guest Session Token only when the target table is `OCCUPIED` and linked to an `OPEN` bill in DynamoDB <br> - Ensure closing a bill immediately invalidates the guest session to mitigate remote static QR abuse | 29/10/2026 | 29/10/2026 | https://000022.awsstudygroup.com/ |
| Fri | **CORS, Throttling & Authorization Testing:** <br> - Restrict CORS headers to the SecureTable CloudFront origin and configure stage-level Rate/Burst Throttling on API Gateway <br> - Test authorization edge cases in Postman: missing token (`401`), unauthorized staff role (`403`), and expired/closed bill guest sessions | 30/10/2026 | 30/10/2026 | https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-request-throttling.html |

### Week 7 Achievements

* Implemented dual-path access control for **SecureTable**: **Amazon Cognito JWT + RBAC** for restaurant staff and **bill-bound Guest Sessions** for table diners.
* Enforced **Least-Privilege IAM Execution Roles** using short-lived role credentials with zero hardcoded keys in source code.
* Hardened **Amazon API Gateway** endpoints with Cognito Authorizers, strict CORS origins, and request throttling.
