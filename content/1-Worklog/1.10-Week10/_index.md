---
title: "Week 10 Worklog"
date: 2026-07-06
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---
### Week 10 Objectives:

* Complete the minigame module, ensuring the level generation feature works smoothly.
* Automate the shop system using a cron job on AWS EventBridge.
* Re-evaluate the search infrastructure, decide to cancel AWS OpenSearch and switch to the Algolia platform to optimize performance.
* Perform an overall system check (End-to-End Testing) to ensure quality.
* Research the AWS CloudFront content delivery network (CDN) to increase page load speed and security.
* Document the system flow, serving as an important premise for designing the Architecture Diagram.

### Tasks to be done this week:
| Day | Task | Start Date | End Date | Resources |
| --- | --- | --- | --- | --- |
| Monday | - Support the team in completing the level generation feature for the minigame | 06/07/2026 | 06/07/2026 | |
| Tuesday | - Use AWS EventBridge to create a cron job to reset the shop weekly | 07/07/2026 | 07/07/2026 | [AWS EventBridge Scheduler](https://aws.amazon.com/eventbridge/scheduler/) |
| Wednesday | - Cancel the AWS OpenSearch service, switch to Algolia <br> - Learn about the CloudFront service to prepare for integration into the project | 08/07/2026 | 08/07/2026 | [Algolia](https://www.algolia.com/) <br> [Amazon CloudFront](https://aws.amazon.com/cloudfront/) |
| Thursday | - Check the overview of all existing functions in the project | 09/07/2026 | 09/07/2026 | |
| Friday | - Synthesize data flows into a text file to support drawing the project architecture diagram | 10/07/2026 | 10/07/2026 | |


### Week 10 Results:

* The minigame level generation feature was completed and successfully integrated into the app's main flow.
* Successfully set up the schedule (cron job) on EventBridge, helping the shop automatically refresh the item list every week accurately.
* Successfully switched the search system to Algolia, helping to simplify the operation process and improve query speed compared to OpenSearch.
* Mastered CloudFront's caching and content delivery mechanisms, getting ready to optimize the loading speed of static resources (images, assets).
* Through the overall testing process (QA), the system operated stably, the functions were tightly linked, and no serious errors were detected.
* Completed a detailed text description of the architecture flow (API Gateway, Lambda, DynamoDB, S3...), creating a solid foundation to draw the official Architecture diagram for the report.