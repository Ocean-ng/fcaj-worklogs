---
title: "Week 8 Worklog"
date: 2024-01-01
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Week 8 Objectives

* Build internal staff operational interfaces for **SecureTable**: `Reception`, `Kitchen`, `Inventory`, and `Admin` workspaces.
* Develop the **Admin Revenue & Security/Audit Logs** view to inspect sensitive operational changes and system security events.
* Harden client-side rendering against **Cross-Site Scripting (XSS)** and review cost-aware encryption choices with the team.

### Tasks Implemented This Week

| Day | Task | Start Date | Completion Date | Reference Material |
|------|-----------|-------------|----------------|---------------|
| Mon | **Developing `Reception` Table & Bill Management UI:** <br> - Build an interactive table floor map showing live statuses (Available, Occupied, Closing) <br> - Implement workflows for opening bills, reviewing table order items, and settling/closing bills | 02/11/2026 | 02/11/2026 | https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/best-practices.html |
| Tue | **Developing `Kitchen` Queue Display UI:** <br> - Build the incoming dish queue interface with periodic polling updates <br> - Implement action controls for marking dishes completed (`Serve`) or rejecting items with explicit reason codes (`Out of Ingredient` / `Customer Request`) | 03/11/2026 | 03/11/2026 | https://docs.aws.amazon.com/lambda/latest/dg/welcome.html |
| Wed | **Developing `Inventory` Stock Management UI:** <br> - Build forms for recording ingredient stock-in receipts, performing stock counts/adjustments, and viewing ingredient movement history | 04/11/2026 | 04/11/2026 | https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/transaction-apis.html |
| Thu | **Building `Admin` Financial & Audit Logs Dashboard:** <br> - Design daily/summary financial reporting views for Admin users <br> - Build the **Audit Logs** viewer (`/v1/audit-logs`) displaying actor, role, action type, and timestamp for operational accountability | 05/11/2026 | 05/11/2026 | https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/sec_detect_investigate_events.html |
| Fri | **Client-Side XSS Hardening & Security Config Review:** <br> - Sanitize and safely render user/API strings in the UI to prevent **XSS** injection issues, and verify zero secrets exist in `frontend/` <br> - Align with the team on adopting free default encryption (`SSE-S3` and DynamoDB AWS-owned keys) to stay within budget | 06/11/2026 | 06/11/2026 | https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/EncryptionAtRest.html |

### Week 8 Achievements

* Completed operational UI views across all four staff roles (`Reception`, `Kitchen`, `Inventory`, `Admin`) in a unified web portal.
* Delivered a transparent **Audit Logs & Financial** dashboard supporting end-to-end traceability of sensitive restaurant actions.
* Eliminated client-side XSS rendering bugs and maintained strict repository secret hygiene.
