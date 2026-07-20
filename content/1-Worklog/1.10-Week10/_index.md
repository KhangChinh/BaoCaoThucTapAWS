---
title: "Week 10 Worklog"
date: 2026-07-06
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---
### Week 10 Objectives:

* Finalize the minigame module, ensuring the level generation feature runs smoothly.
* Automate the in-game shop system using cron jobs on AWS EventBridge.
* Re-evaluate the search infrastructure, cancel AWS OpenSearch, and migrate to Algolia to optimize performance.
* Conduct End-to-End (E2E) testing across the entire system to ensure overall quality.
* Research the AWS CloudFront content delivery network (CDN) to improve loading speeds and security.
* Document system flows to serve as a crucial prerequisite for designing the Architecture Diagram.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Support the team in finalizing the level generation function for the minigame | 07/06/2026 | 07/06/2026 | |
| 3 | - Use AWS EventBridge to create a weekly reset function for the shop | 07/07/2026 | 07/07/2026 | [AWS EventBridge Scheduler](https://aws.amazon.com/eventbridge/scheduler/) |
| 4 | - Cancel AWS OpenSearch service and switch to Algolia <br> - Learn about the CloudFront service for upcoming project integration | 07/08/2026 | 07/08/2026 | [Algolia](https://www.algolia.com/) <br> [Amazon CloudFront](https://aws.amazon.com/cloudfront/) |
| 5 | - Review and test all existing functions integrated into the project | 07/09/2026 | 07/09/2026 | |
| 6 | - Compile data flows into a text file to support drawing the project's architecture diagram | 07/10/2026 | 07/10/2026 | |


### Week 10 Achievements:

* The minigame level generation function was finalized and successfully integrated into the main application flow.
* Successfully set up a schedule (cron job) on EventBridge, enabling the shop to automatically refresh its item list accurately every week.
* Successfully migrated the search system to Algolia, simplifying operational processes and improving query speed compared to OpenSearch.
* Mastered CloudFront's caching and content delivery mechanisms, fully prepared to optimize the loading speed of static resources (images, assets).
* Through comprehensive E2E testing (QA), the system proved stable; all functions are tightly linked, and no critical errors were detected.
* Completed a detailed text description of the architecture flows (API Gateway, Lambda, DynamoDB, S3, etc.), establishing a solid foundation for designing the official Architecture Diagram for the final report.