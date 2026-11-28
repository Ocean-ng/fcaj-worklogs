---
title: "Week 9 Worklog"
date: 2024-01-01
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Week 9 Objectives

* Implement a centralized API communication layer (`apiClient.js`) in the **SecureTable** Frontend aligned with the team's **Amazon API Gateway** contract.
* Add **Idempotency-Key** request headers for order submissions and handle `401 / 403 / 304` HTTP responses cleanly across UI screens.
* Study the team's scheduled reporting and backup workflow (`EventBridge Scheduler + SNS + DynamoDB Export to S3`) and attend the **AWS Cloud Mastery** event.

### Tasks Implemented This Week

| Day | Task | Start Date | Completion Date | Reference Material |
|------|-----------|-------------|----------------|---------------|
| Mon | **Building Centralized `apiClient.js` for API Gateway:** <br> - Write shared HTTP client helpers automatically attaching Staff Cognito Bearer JWTs or Guest Session Tokens to outgoing requests | 09/11/2026 | 09/11/2026 | https://docs.aws.amazon.com/apigateway/latest/developerguide/welcome.html |
| Tue | **Adding `Idempotency-Key` & Kitchen Polling Optimization:** <br> - Generate unique `Idempotency-Key` headers per order submission to prevent duplicate orders on flaky mobile connections <br> - Support `ETag` (`304 Not Modified`) handling on the Kitchen queue view to reduce redundant payload transfers | 10/11/2026 | 10/11/2026 | https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/transaction-apis.html |
| Wed | **Synchronizing UI Controls with Backend RBAC Matrix:** <br> - Align every UI action against backend role permissions (`ADMIN`, `RECEPTION`, `KITCHEN`, `INVENTORY`) <br> - Handle `403 Forbidden` responses gracefully with clear bilingual feedback | 11/11/2026 | 11/11/2026 | https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html |
| Thu | **Studying Project Reporting & Backup Automation Flows:** <br> - Review **Amazon EventBridge Scheduler**, **Amazon SNS**, and **DynamoDB PITR / Export to S3** documentation to understand how scheduled Admin reports and weekly backups operate | 12/11/2026 | 12/11/2026 | https://docs.aws.amazon.com/scheduler/latest/UserGuide/what-is-scheduler.html |
| Fri | **UI State Testing & Attending AWS Cloud Mastery (14/11):** <br> - Test loading, empty, and network-error states across all Frontend views <br> - Attend the in-person **AWS Cloud Mastery** sharing session (Saturday morning, 14/11/2026 at Level 26 Bitexco) with teammates | 13/11/2026 | 14/11/2026 | https://000022.awsstudygroup.com/ |

### Week 9 Achievements

* Delivered a reliable Frontend API integration layer enforcing authentication headers and duplicate-order protection via `Idempotency-Key`.
* Gained end-to-end understanding of **SecureTable**'s online request flows and background automation pipelines.
* Gathered practical architectural and presentation advice at the **AWS Cloud Mastery** event at the AWS Vietnam office.
