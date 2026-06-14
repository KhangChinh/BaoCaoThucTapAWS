---
title: "Week 6 Worklog"
date: 2026-06-08
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---
### Week 6 Objectives:

* Standardize and document the complete operational and business flows of the system.
* Enhance application security by optimizing the management of user login tokens.
* Research background and automated task execution solutions on the server using AWS EventBridge.
* Refactor the database schema to effectively reduce unnecessary API calls from the Client to AWS.
* Design a tailored session management logic for two core sub-modules: Learning and Minigame.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Map out and finalize the documentation for all project business flows | 06/08/2026 | 06/08/2026 | |
| 3 | - Implement logic for managing and storing user login tokens | 06/09/2026 | 06/09/2026 | |
| 4 | - Learn about AWS EventBridge for managing background functions on the server | 06/10/2026 | 06/10/2026 | [AWS EventBridge Documentation](https://aws.amazon.com/eventbridge/) |
| 5 | - Refactor the database schema to minimize client-side API calls to AWS | 06/11/2026 | 06/11/2026 | |
| 6 | - Research and design session logic for the learning & minigame features | 06/12/2026 | 06/12/2026 | |


### Week 6 Achievements:

* Successfully finalized the overall system workflow and business logic documentation, providing a solid blueprint for subsequent development stages.
* The token handling logic is now robust, secure, and preserves valid user authentication states seamlessly.
* Grasped the core concepts of AWS EventBridge (Event Bus, Rules, Targets) and established a strategy for setting up scheduled background cron jobs.
* Optimized the database schema efficiently, yielding a visible reduction in redundant API queries from the front-end, saving compute resources and costs.
* Designed a viable session state model for the learning and minigame features, ensuring real-time and precise tracking of user progress.