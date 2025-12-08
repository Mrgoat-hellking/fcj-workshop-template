---
title: "Week 12 Worklog"
date: 2025-01-01
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---


### Week 12 Objectives:

* enter the Project sprint
* review the services to be used

### Tasks to be implemented this week:
| Day | Task | Start date | Completion date | Resources |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------ | --------------- | ----------------------------------------- |
| 2 | - Database Essentials with Amazon Relational Database Service (RDS) | 24/11/2025 | 24/11/2025 |
| 3 | - Access Management with AWS Identity and Access Management (IAM) | 25/11/2025 | 25/11/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Serverless Automation with AWS Lambda | 26/11/2025 | 26/11/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - AWS CDK Advanced | 27/11/2025 | 27/11/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Application Protection with AWS WAF | 28/11/2025 | 28/11/2025 | <https://cloudjourney.awsstudygroup.com/> |


### Results achieved in week 12:

* **Serverless, Amplify & Network Integration Challenges**

API Gateway synchronizes request/response, separate handler & business logic, clear error handling

Move from RDS to DynamoDB: PK/SK, GSI, multi-relational data difficult to optimize One-Table

Distributed logging CloudWatch → difficult to debug

Minimum IAM role for Lambda, CORS/mapping template prone to errors

CI/CD GitLab → deploy Lambda automatically, optimize cold start & timeout

Simple CRUD → complex FFF workflow

* **Serverless Automation Challenges (AWS Lambda)**

Clearly separate handler, business logic, error handling to avoid confusing processing flow

Cold start, timeout when traffic is high

Distributed logging via CloudWatch → difficult to debug

Minimum IAM role for Lambda, ensure security

CI/CD GitLab → Automatic Lambda deployment, zip code, versioning

Complex workflow → Insufficient sample CRUD

Connecting to DynamoDB, S3, API Gateway requires accurate mapping

Managing concurrency, throttling when multiple requests are made simultaneously

* **AWS CDK Advanced Challenges**

Designing complex IaC infrastructure, managing multiple service stacks (Lambda, RDS, DynamoDB, S3, API Gateway)

Dependency between stacks → deploying in the correct order, avoiding cyclic dependency errors

Complex parameters, environment variables, context management

Versioning, updating stack → avoiding downtime or data loss

Security: IAM role/policy must be synchronized with CDK
* **Application Protection Challenges (AWS WAF)**

Designing rules against SQL injection, XSS, bot traffic suitable for FFF

Tuning rate-based rules to avoid false positives/blocking valid users

Combining WAF with API Gateway, CloudFront, ALB → complex configuration

Logging + monitoring via CloudWatch → difficult to debug blocked requests

Update rules when FFF changes API/endpoint