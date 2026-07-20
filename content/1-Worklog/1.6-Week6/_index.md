---
title: "Week 6 Worklog"
date: 2026-06-08
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---
### Week 6 Objectives:

* Standardize and clarify the entire business logic flow of the system.
* Enhance app security by optimizing login token management.
* Research solutions for automating background tasks on the server using the AWS EventBridge service.
* Separate and optimize the database structure (DB schema) to minimize unnecessary API calls from the Client to AWS.
* Design an optimal session management solution (session logic) for the two core modules: Learning and Minigame.

### Tasks to be done this week:
| Day | Task | Start Date | End Date | Resources |
| --- | --- | --- | --- | --- |
| Monday | - Design and complete the documentation for all project business flows | 08/06/2026 | 08/06/2026 | |
| Tuesday | - Build the logic to manage and store user login tokens | 09/06/2026 | 09/06/2026 | |
| Wednesday | - Learn about the AWS EventBridge service to manage background functions on the server | 10/06/2026 | 10/06/2026 | [AWS EventBridge Documentation](https://aws.amazon.com/eventbridge/) |
| Thursday | - Refine and adjust the database schema to reduce the Client's API calls to AWS | 11/06/2026 | 11/06/2026 | |
| Friday | - Research and design session logic for the learning and minigame parts of the app | 12/06/2026 | 12/06/2026 | |


### Week 6 Results:

* Completed the overall diagram and documented all project business flows, helping to provide a clear implementation direction for the next stages.
* The token processing system works safely, ensuring good access control and maintaining a valid login state for users.
* Mastered the operating mechanism of AWS EventBridge (Event Bus, Rules, Targets) and came up with a plan to deploy periodic tasks (cron jobs) running in the background on the Serverless architecture.
* The database schema was successfully improved thanks to reasonable data clustering techniques, significantly reducing the frequency of API calls from the Client, saving AWS resources and costs.
* Completed the session processing model for the learning and minigame parts, ensuring that the user's playing/learning progress data is always stored accurately and instantly.