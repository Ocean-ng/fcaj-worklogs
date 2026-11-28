---
title: "Week 7 Worklog"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Week 7 Objectives

* Build the customer-facing **Guest Portal** for **SecureTable**: restaurant landing view, 4-category visual menu, and QR table ordering cart.
* Implement client-side **Guest Session Token** handling bound to active (`OPEN`) bills without requiring customers to register an account.
* Integrate the Staff login screen with **Amazon Cognito User Pools** (supporting password + MFA sign-in flows and decoding JWT group claims for role-based navigation).

### Tasks Implemented This Week

| Day | Task | Start Date | Completion Date | Reference Material |
|------|-----------|-------------|----------------|---------------|
| Mon | **Building Guest Home & Categorized Menu Views:** <br> - Develop the restaurant showcase home view highlighting dining ambiance and signature dishes <br> - Build the `#/menu` screen organized into 4 categories (Appetizers, Main Courses, Beverages, Desserts) displaying dish photos, prices, and real-time availability | 26/10/2026 | 26/10/2026 | https://aws.amazon.com/serverless/ |
| Tue | **Developing QR Ordering Cart & Guest Session Handling:** <br> - Build item quantity selectors and order submission UI wired to `POST /v1/guest/sessions` upon scanning a table QR code <br> - Display clear user prompts whenever a table has no active `OPEN` bill or after bill settlement | 27/10/2026 | 27/10/2026 | https://000022.awsstudygroup.com/ |
| Wed | **Studying Amazon Cognito Authentication for SPAs:** <br> - Review **Amazon Cognito User Pool** documentation for public Single-Page Application clients (no client secret) and inspect JWT token claims (`id_token`, `access_token`) | 28/10/2026 | 28/10/2026 | https://docs.aws.amazon.com/cognito/latest/developerguide/cognito-user-identity-pools.html |
| Thu | **Implementing Staff Login UI & JWT Role Routing:** <br> - Build the `#/staff` sign-in interface integrated with the team's Cognito User Pool, including TOTP MFA verification steps <br> - Parse `cognito:groups` claims to route signed-in staff directly to their authorized workspace | 29/10/2026 | 29/10/2026 | https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-integrate-with-cognito.html |
| Fri | **Testing Session Isolation & Token Expiration:** <br> - Verify clean separation between Staff Cognito JWT storage and Guest Session Tokens in the browser <br> - Implement automatic session cleanup and redirect upon token expiry or `401 Unauthorized` responses | 30/10/2026 | 30/10/2026 | https://docs.aws.amazon.com/IAM/latest/UserGuide/security-creds.html |

### Week 7 Achievements

* Delivered an intuitive, account-free QR menu browsing and table ordering interface for restaurant guests.
* Integrated Staff authentication with **Amazon Cognito**, automatically tailoring UI workspaces according to user group claims.
* Ensured clean client-side handling of short-lived tokens (Cognito JWTs and bill-scoped Guest Session Tokens) for API Gateway requests.
