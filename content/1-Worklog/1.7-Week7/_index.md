---
title: "Week 7 Worklog"
date: 2026-06-15
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---
### Week 7 Objectives:

* Develop the core social interaction feature: a friend system between users.
* Automate the daily quest refresh flow through AWS Lambda triggers.
* Build a high-speed user search tool by integrating AWS OpenSearch with DynamoDB.
* Standardize infrastructure management (Infrastructure as Code) for the Serverless Node.js project using CloudFormation.
* Optimize the automatic item data entry pipeline from AWS S3 to DynamoDB.

### Tasks to be done this week:
| Day | Task | Start Date | End Date | Resources |
| --- | --- | --- | --- | --- |
| Monday | - Write friend logic between 2 users (processing data on the social table) | 15/06/2026 | 15/06/2026 | |
| Tuesday | - Write logic for the automatic daily quest refresh feature via Lambda trigger | 16/06/2026 | 16/06/2026 | [AWS Lambda Triggers](https://docs.aws.amazon.com/lambda/latest/dg/lambda-invocation.html) |
| Wednesday | - Apply AWS OpenSearch connected to DynamoDB to manage the user search feature | 17/06/2026 | 17/06/2026 | [Amazon OpenSearch Service](https://aws.amazon.com/opensearch-service/) |
| Thursday | - Learn and use CloudFormation to configure the serverless project | 18/06/2026 | 18/06/2026 | [AWS CloudFormation](https://aws.amazon.com/cloudformation/) |
| Friday | - Write an event trigger for S3 (assets bucket) to upload item data to DynamoDB automatically | 19/06/2026 | 19/06/2026 | |


### Week 7 Results:

* Completed the friend API, allowing users to send requests and successfully establish relationships.
* The daily quest refresh feature works accurately based on Lambda's trigger schedule, ensuring a continuous experience for users.
* Successfully configured the OpenSearch endpoint to sync data from the DynamoDB user table, bringing faster and more flexible user search capabilities.
* Successfully converted resource declarations (Lambda functions, access permissions, environment variables) to CloudFormation templates, making project deployment automatic and easy to control.
* Successfully built the S3 trigger flow: whenever a new item data file is pushed to the bucket, Lambda automatically reads and writes the information to DynamoDB without manual intervention.