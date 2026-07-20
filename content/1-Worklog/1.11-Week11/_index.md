---
title: "Week 11 Worklog"
date: 2026-07-13
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---
### Week 11 Objectives:

* Optimize static resource loading speed by routing the Client through the AWS CloudFront content delivery network (CDN).
* Visualize the entire system with a standard Architecture Diagram.
* Build the app into an executable file (.exe) and deploy it to the Production environment.
* Perform direct testing on Production to ensure the product operates perfectly before acceptance.
* Prepare a demo script and a detailed outline for the final project report.

### Tasks to be done this week:
| Day | Task | Start Date | End Date | Resources |
| --- | --- | --- | --- | --- |
| Monday | - Change the configuration so the Client calls AWS CloudFront instead of calling S3 directly | 13/07/2026 | 13/07/2026 | [Amazon CloudFront](https://aws.amazon.com/cloudfront/) |
| Tuesday | - Draw and complete the project architecture diagram | 14/07/2026 | 14/07/2026 | |
| Wednesday | - Compress/build the project into an .exe file for deployment <br> - Download and test functions on the production environment | 15/07/2026 | 15/07/2026 | |
| Thursday | - Create a script and prepare content to record a demo video for the project | 16/07/2026 | 16/07/2026 | |
| Friday | - Synthesize data and prepare content to write the project report | 17/07/2026 | 17/07/2026 | |


### Week 11 Results:

* Successfully configured CloudFront Distribution, helping the Client load static files much faster and more securely than accessing S3 directly.
* The system architecture diagram was drawn in detail, clearly showing the interaction flow between AWS services (API Gateway, Lambda, DynamoDB, Cognito, S3, CloudFront...).
* The project was successfully packaged as an `.exe` file. The deployment process to Production went smoothly.
* Through actual testing (User Acceptance Testing) on Production, all core features operated stably without errors.
* Completed the detailed script for the demo video and created a full outline for the final report document.