---
title: "Week 10 Worklog"
date: 2024-01-01
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Week 10 Objectives

* Study and synthesize official AWS documentation on the **Shared Responsibility Model**, **Amazon S3 Data Security**, and **IAM & AWS CloudTrail** into knowledge-sharing posts for the **AWS Study Group VN** community.
* Redesign and polish the **SecureTable** Frontend UI and animations into a clean, modern bilingual (`VI / EN`) restaurant experience.
* Review the entire `frontend/` codebase, fix image rendering issues, and synchronize UI business logic 100% with the team's Backend API specification.

### Tasks Implemented This Week

| Day | Task | Start Date | Completion Date | Reference Material |
|------|-----------|-------------|----------------|---------------|
| Mon | **Deep-Dive into Shared Responsibility & IAM Security:** <br> - Study the AWS Well-Architected Security Pillar, Root user MFA protection, temporary credentials (IAM Roles / Federation), and Least-Privilege policy scoping | 16/11/2026 | 16/11/2026 | https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/welcome.html <br> https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html |
| Tue | **Studying Amazon S3 Security & AWS CloudTrail Scope:** <br> - Review S3 default protections (4 Block Public Access settings, SSE-S3 encryption at rest, S3 Versioning storage cost trade-offs) and 90-day CloudTrail Event History coverage <br> - Draft practical checklists for community knowledge sharing | 17/11/2026 | 17/11/2026 | https://aws.amazon.com/compliance/shared-responsibility-model/ <br> https://docs.aws.amazon.com/AmazonS3/latest/userguide/security-best-practices.html |
| Wed | **Publishing 3 Posts on AWS Study Group VN & UI Redesign:** <br> - Publish 3 AWS Cloud Security posts to the **AWS Study Group VN** Facebook group <br> - Upgrade **SecureTable** customer UI layout and smooth transitions (`VI / EN`), fix dish/gallery image paths, and organize the `frontend/` directory | 18/11/2026 | 18/11/2026 | https://docs.aws.amazon.com/awscloudtrail/latest/userguide/view-cloudtrail-events.html |
| Thu | **Synchronizing Frontend Logic with Backend API Spec:** <br> - Audit every API endpoint call, request payload, and 5-role permission boundary in the UI to match the Backend `securetable-api.md` contract | 19/11/2026 | 19/11/2026 | https://docs.aws.amazon.com/apigateway/latest/developerguide/http-api-cors.html |
| Fri | **Repository Hygiene & Pushing `frontend/` to Team Git:** <br> - Verify `.gitignore` rules (`node_modules/`, `dist/`), validate local production builds, and push `frontend/` cleanly to the shared team repository without merge conflicts | 20/11/2026 | 20/11/2026 | https://cloudjourney.awsstudygroup.com/ |

### Week 10 Achievements

* Consolidated core **AWS Shared Responsibility**, **S3 Security**, **IAM**, and **CloudTrail** concepts into 3 approved posts on **AWS Study Group VN**.
* Delivered a polished, responsive, bilingual (`VI / EN`) **SecureTable** Frontend with smooth animations and complete visual assets.
* Verified 100% alignment between Frontend UI workflows and Backend API/RBAC specifications.
