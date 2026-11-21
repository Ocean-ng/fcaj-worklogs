---
title: "Week 12 Worklog"
date: 2024-01-01
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

### Week 12 Objectives

* Conduct comprehensive End-to-End (E2E) verification of the technical Workshop (Private Connectivity to Amazon S3 from VPC and On-premises using Gateway/Interface Endpoints & Route 53 Private DNS) and project architecture.
* Perform a final account security audit and cost review using **AWS Cost Explorer** and **AWS Trusted Advisor**, ensuring zero lingering billable resources.
* Finalize and polish bilingual content (Vietnamese & English) across all 7 sections of the Hugo internship report: Worklog, Proposal, Blogs Posted, Events Participated, Workshop, Self-evaluation, and Feedback.
* Verify automated CI/CD deployment via GitHub Actions and complete the FCAJ internship report submission.

### Tasks Implemented This Week

| Day | Task | Start Date | Completion Date | Reference Material |
|------|-----------|-------------|----------------|---------------|
| Mon | **End-to-End (E2E) Workshop Verification:** <br> - Re-run the complete Workshop workflow from CloudFormation stack provisioning, S3 Gateway Endpoint, and S3 Interface Endpoint setup to Route 53 Inbound Resolver and VPC Endpoint Policy testing <br> - Validate CLI outputs (`aws s3 ls`, `dig`) and verify step-by-step screenshots | 30/11/2026 | 30/11/2026 | https://000008.awsstudygroup.com/ |
| Tue | **Finalizing Workshop & Proposal Documentation:** <br> - Proofread and refine all 6 chapters of `5-Workshop` (Overview, Prerequisites, S3 from VPC, S3 from On-premises, VPC Endpoint Policies, Cleanup) in both Vietnamese and English <br> - Review architecture diagrams and AWS Pricing Calculator estimates in `2-Proposal` | 01/12/2026 | 01/12/2026 | https://cloudjourney.awsstudygroup.com/ |
| Wed | **Compiling Blogs, Events & Self-Evaluation:** <br> - Finalize translated technical blog posts in `3-BlogsPosted` and AWS event summaries in `4-EventParticipated` <br> - Complete the internship self-evaluation (`6-Self-evaluation`) and program feedback (`7-Feedback`) | 02/12/2026 | 02/12/2026 | |
| Thu | **Account Cost Audit & Resource Cleanup:** <br> - Inspect AWS Cost Explorer and active resources across all regions, confirming complete deletion of VPC Endpoints, Route 53 Resolver Endpoints, CloudFormation Stacks, S3 Buckets, and Elastic IPs | 03/12/2026 | 03/12/2026 | https://000007.awsstudygroup.com/ |
| Fri | **GitHub Pages Deployment & Final Review:** <br> - Verify Hugo build integrity and push the complete codebase to the GitHub repository (`Ocean-ng.github.io`) <br> - Test navigation, image links, and VI/EN language switching on the live GitHub Pages site for final submission | 04/12/2026 | 04/12/2026 | https://ocean-ng.github.io/fcaj-worklogs/ |

### Week 12 Achievements

* Verified 100% reproducibility of the technical **Workshop** covering private Amazon S3 connectivity via Gateway Endpoints, Interface Endpoints (PrivateLink), Route 53 Hybrid DNS, and Endpoint Policies.
* Confirmed a clean, secure AWS account with zero orphaned resources or unexpected post-internship charges.
* Delivered a complete, bilingual (Vietnamese – English) **First Cloud AI Journey** internship report website powered by Hugo and GitHub Pages.
* Consolidated three months of hands-on AWS Cloud and Information Security experience, preparing a strong foundation for final defense and a future career as a Cloud Security Engineer.
