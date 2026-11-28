---
title: "Week 6 Worklog"
date: 2024-01-01
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives

* Initialize the `React + Vite` Frontend codebase for **SecureTable**, designing a clean, responsive layout suited for both mobile diners (scanning QR codes) and tablet/desktop staff.
* Implement a bilingual **Vietnamese - English (`VI / EN`)** localization layer and client-side routing separating customer and staff portals.
* Study secure static website hosting on a **private Amazon S3 Bucket** delivered via **Amazon CloudFront** with **Origin Access Control (OAC)** and the **CloudFront Free Plan**.

### Tasks Implemented This Week

| Day | Task | Start Date | Completion Date | Reference Material |
|------|-----------|-------------|----------------|---------------|
| Mon | **Designing SecureTable Sitemap & UI Wireframes:** <br> - Sketch responsive layouts for the customer portal (Home, categorized Menu, QR Table Ordering Cart) and the internal Staff POS portal <br> - Prioritize mobile readability for guests scanning table QR codes | 19/10/2026 | 19/10/2026 | https://cloudjourney.awsstudygroup.com/ |
| Tue | **Scaffolding React + Vite Frontend & SPA Routing:** <br> - Set up the `frontend/` directory structure (`src/components`, `src/pages`, `src/services`, `public/`) <br> - Configure hash-based SPA routing separating customer views (`#/`, `#/menu`) from staff views (`#/staff`) for seamless S3/CloudFront static delivery | 20/10/2026 | 20/10/2026 | https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/GettingStarted.SimpleDistribution.html |
| Wed | **Implementing Bilingual Localization (`VI / EN`):** <br> - Build an `i18n` translation module enabling instant `VI / EN` switching across navigation menus, table statuses, dish statuses, and user notifications | 21/10/2026 | 21/10/2026 | https://docs.aws.amazon.com/wellarchitected/latest/serverless-applications-lens/web-applications.html |
| Thu | **Studying Private S3 Hosting with CloudFront OAC:** <br> - Study AWS documentation on hosting SPAs **without public S3 Static Website Hosting**: keeping **Block all public access** enabled and granting read access solely to CloudFront via **Origin Access Control (SigV4)** | 22/10/2026 | 22/10/2026 | https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/private-content-restricting-access-to-s3.html |
| Fri | **CloudFront Free Plan Review & `.env` Contract Alignment:** <br> - Review **CloudFront Free Plan** allowances (including bundled AWS WAF capabilities) <br> - Align `VITE_*` environment variables (`VITE_API_GATEWAY_URL`, `VITE_COGNITO_USER_POOL_ID`, `VITE_COGNITO_CLIENT_ID`) in `.env.example` with Backend/Infra teammates | 23/10/2026 | 23/10/2026 | https://000058.awsstudygroup.com/ |

### Week 6 Achievements

* Built a clean, responsive `React + Vite` frontend foundation with full Vietnamese and English (`VI / EN`) language support.
* Established a clear `.env` integration contract with Backend and Infrastructure teammates to avoid Git merge conflicts.
* Mastered private S3 origin security using **CloudFront Origin Access Control (OAC)** and `index.html` root object configuration.
