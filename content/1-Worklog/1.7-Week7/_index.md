---
title: "Week 7 Worklog"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Week 7 Objectives

* Understand Serverless computing architecture on AWS using **AWS Lambda** and **Amazon API Gateway**.
* Develop AWS Lambda functions (Python/Node.js), configure Least-Privilege Execution Roles, manage Environment Variables, and test event payloads.
* Build RESTful and HTTP APIs with Amazon API Gateway, configure CORS and Throttling, and integrate Lambda Proxy Integration.
* Implement OAuth 2.0 / OIDC user authentication with **Amazon Cognito User Pools** and secure API Gateway endpoints using a Cognito Authorizer.

### Tasks Implemented This Week

| Day | Task | Start Date | Completion Date | Reference Material |
|------|-----------|-------------|----------------|---------------|
| Mon | **AWS Lambda Fundamentals:** <br> - Study event-driven execution, container lifecycle (Cold Start vs. Warm Start), and resource limits in AWS Lambda <br> - Create a Least-Privilege Lambda Execution Role granting only CloudWatch logging and scoped S3 access <br> - Write and test a Lambda function processing JSON events from S3 and API triggers | 26/10/2026 | 26/10/2026 | https://000022.awsstudygroup.com/ |
| Tue | **Building APIs with Amazon API Gateway:** <br> - Compare API Gateway types (REST API, HTTP API, WebSocket API) <br> - Define resources and methods (`GET`, `POST`) connected to Lambda via Lambda Proxy Integration <br> - Configure CORS headers and deploy the API to a `dev` stage | 27/10/2026 | 27/10/2026 | https://000022.awsstudygroup.com/ |
| Wed | **User Authentication with Amazon Cognito:** <br> - Distinguish between Cognito User Pools (Authentication) and Identity Pools (Federated AWS Credentials) <br> - Create a Cognito User Pool, enforce password complexity policies, enable email OTP verification, and configure an App Client | 28/10/2026 | 28/10/2026 | https://docs.aws.amazon.com/cognito/ |
| Thu | **Securing API Gateway with Cognito Authorizer:** <br> - Attach a Cognito User Pool Authorizer to Amazon API Gateway methods <br> - Authenticate via Cognito Hosted UI to obtain JWT tokens (`id_token` / `access_token`) <br> - Verify API security in Postman: confirm `401 Unauthorized` without a token and `200 OK` with a valid Bearer JWT | 29/10/2026 | 29/10/2026 | https://docs.aws.amazon.com/apigateway/ |
| Fri | **API Throttling & Verification:** <br> - Configure Usage Plans and stage-level Throttling (Rate Limit / Burst Limit) on API Gateway to prevent resource exhaustion attacks <br> - Inspect Lambda execution logs in CloudWatch and clean up test stages | 30/10/2026 | 30/10/2026 | https://000022.awsstudygroup.com/ |

### Week 7 Achievements

* Built an end-to-end Serverless backend combining **Amazon API Gateway** and **AWS Lambda** with zero server maintenance.
* Enforced least-privilege execution permissions on Lambda functions using scoped IAM Execution Roles.
* Integrated centralized authentication using **Amazon Cognito User Pools**, protecting backend API routes with JWT validation via **Cognito Authorizer**.
* Hardened API endpoints with strict CORS rules and rate-limiting (Throttling) controls to mitigate abuse and unexpected cost spikes.
