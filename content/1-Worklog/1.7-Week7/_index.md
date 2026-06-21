---
title: "Week 7 Worklog"
date: 2026-06-15
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---
### Week 7 Objectives:

* Develop the core social interaction feature: the user-to-user friend system.
* Automate the daily quest refresh flow using AWS Lambda triggers.
* Build a high-performance user search engine by integrating AWS OpenSearch with DynamoDB.
* Standardize infrastructure management (Infrastructure as Code) for the Node.js Serverless project using CloudFormation.
* Optimize the automated item data ingestion pipeline from AWS S3 to DynamoDB.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Write logic for friending between 2 users (handling data on the social table) | 06/15/2026 | 06/15/2026 | |
| 3 | - Write logic for the daily quest refresh function via Lambda trigger | 06/16/2026 | 06/16/2026 | [AWS Lambda Triggers](https://docs.aws.amazon.com/lambda/latest/dg/lambda-invocation.html) |
| 4 | - Apply AWS OpenSearch connected with DynamoDB to manage the user search function | 06/17/2026 | 06/17/2026 | [Amazon OpenSearch Service](https://aws.amazon.com/opensearch-service/) |
| 5 | - Learn and use CloudFormation to manage the serverless project configuration | 06/18/2026 | 06/18/2026 | [AWS CloudFormation](https://aws.amazon.com/cloudformation/) |
| 6 | - Write an event trigger for S3 (assets bucket) to facilitate uploading item data to DynamoDB | 06/19/2026 | 06/19/2026 | |


### Week 7 Achievements:

* Completed the friend system API, allowing users to successfully send requests and establish connections.
* The daily quest refresh function operates accurately based on the Lambda trigger schedule, ensuring a continuous user experience.
* Successfully configured the OpenSearch endpoint to synchronize data from DynamoDB's user table, delivering flexible and lightning-fast user search capabilities.
* Successfully transitioned resource declarations (Lambda functions, permissions, environment variables) into CloudFormation templates, making project deployment automated and highly manageable.
* Built a seamless S3 trigger flow: whenever new item data files are uploaded to the bucket, a Lambda function automatically reads and writes the information into DynamoDB without manual intervention.