---
title: "Week 11 Worklog"
date: 2024-01-01
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Week 11 Objectives

* Package the **SecureTable** Frontend production bundle and deploy it to a **private Amazon S3 Bucket** served via **Amazon CloudFront** (with **Origin Access Control - OAC** and **AWS WAF** under the CloudFront Free Plan) in `ap-southeast-1`.
* Collaborate with all teammates to run End-to-End (E2E) integration tests connecting the CloudFront UI to API Gateway, Cognito, Lambda, and DynamoDB.
* Prepare the walkthrough script and sample data for **recording the team's product Demo (scheduled for 28–29/11/2026)** and update my personal GitHub Pages report.

### Tasks Implemented This Week

| Day | Task | Start Date | Completion Date | Reference Material |
|------|-----------|-------------|----------------|---------------|
| Mon | **Building Production Frontend & Uploading to Private S3:** <br> - Configure live AWS (`ap-southeast-1`) endpoints and build static frontend assets <br> - Create a private S3 Bucket (`ACLs disabled`, `Block all public access` enabled) and upload frontend files with `index.html` at the bucket root | 23/11/2026 | 23/11/2026 | https://docs.aws.amazon.com/AmazonS3/latest/userguide/access-control-block-public-access.html |
| Tue | **Configuring Amazon CloudFront (OAC & AWS WAF):** <br> - Create a CloudFront Distribution under the **CloudFront Free Plan**, enable **AWS WAF**, and connect the S3 origin via **Origin Access Control (Sign requests)** <br> - Apply the CloudFront S3 Bucket Policy, set `Default root object: index.html`, and verify HTTPS access via the `cloudfront.net` domain | 24/11/2026 | 24/11/2026 | https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/private-content-restricting-access-to-s3.html |
| Wed | **Team End-to-End (E2E) Integration Testing:** <br> - Run full workflow verification with teammates from the CloudFront UI: Reception opens table & bill → Guest scans QR and places order → Kitchen serves/rejects items → Inventory verifies stock → Reception closes bill → Admin checks revenue & Audit Logs | 25/11/2026 | 25/11/2026 | https://docs.aws.amazon.com/wellarchitected/latest/serverless-applications-lens/opex-testing.html |
| Thu | **Authoring Frontend Deployment Steps for Team Workshop:** <br> - Capture S3 and CloudFront OAC configuration screenshots and write deployment notes for section **`5.3-Frontend-dev`** in the team's shared Workshop guide | 26/11/2026 | 26/11/2026 | https://github.com/thienluhoan/fcj-workshop-template |
| Fri | **Scripting Product Demo (28–29/11) & Updating Report Site:** <br> - Prepare the step-by-step demonstration script and sample menu/inventory data to **present and record the SecureTable product Demo for the team on 28–29/11/2026** <br> - Sync Proposal, Workshop chapters (`5.1` - `5.10`), Blogs, Events, and Worklogs on my GitHub Pages site | 27/11/2026 | 27/11/2026 | https://docs.aws.amazon.com/waf/latest/developerguide/waf-chapter.html |

### Week 11 Achievements

* Deployed **SecureTable**'s live web interface on **Amazon CloudFront + Private S3 Bucket (OAC)** over HTTPS.
* Verified seamless end-to-end integration between my Frontend portal and the API Gateway, Cognito, Lambda, and DynamoDB services built by my teammates.
* Finalized the demo walkthrough script and test dataset for **recording the team's product Demo on 28–29/11/2026**.
