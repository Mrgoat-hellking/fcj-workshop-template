---
title: "Week 11 Worklog"
date: 2025-11-17
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---


### Week 11 Objectives:

* enter the Project sprint
* review the services to be used

### Tasks to be implemented this week:
| Day | Task | Start Date | Completion Date | Resources |
| --- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2 | - Hybrid DNS Management with Amazon Route53 | 11/08/2025 | 11/08/2025 |
| 3 | - Building Serverless CRUD with Lambda and DynamoDB | 12/08/2025 | 12/08/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Serverless Storage and Auth with AWS Amplify | 13/08/2025 | 13/08/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Frontend Integration with API Gateway | 08/14/2025 | 08/15/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Network Integration with VPC Peering | 08/15/2025 | 08/15/2025 | <https://cloudjourney.awsstudygroup.com/> |

### Results achieved in week 11:

#### I have studied and understood the above lessons and these are the difficulties when applying them to the project.

* 1. **Lambda + DynamoDB (Serverless CRUD)**

Design an API Gateway that is synchronized with FFF's request/response.

Separate handlers, business logic, and error handling in Lambda to avoid confusing processing flows.

Switching from RDS to DynamoDB changes the data model (PK/SK, GSI).

FFF data has many relationships → difficult to optimize DynamoDB without designing One-Table.

Distributed logging + CloudWatch → complex debugging.

Configure IAM role to minimize permissions for Lambda to access DynamoDB.

CORS, mapping template, stage variables of API Gateway are prone to errors.

CI/CD from GitLab → Lambda needs automatic pipeline (zip code, deploy).

Optimize cold start, timeout when traffic increases.

Sample CRUD logic is too simple → FFF needs multi-step workflow.

2. **Amplify Storage & Auth**

Amplify uses Cognito + S3, needs to synchronize with FFF backend (roles, session).

Mapping Cognito permissions (User Pool / Identity Pool) with RBAC FFF is complex.

Synchronizing Amplify login with API Gateway IAM auth or JWT validator requires manual configuration.

Upload files via Amplify Storage → S3 policy, read/write permissions by user type.

Upload large files (images/videos) need presigned URL + security limits.

Amplify CLI creates many auto resources → easily messes up CloudFormation stack.

CI/CD with Amplify Hosting/Backend if combining GitLab is complicated.

3. **Frontend Integration with API Gateway**

Must clearly design endpoint URL, stage, mapping for frontend to connect Lambda/DynamoDB properly.

Configure CORS, headers, content-type so frontend fetch does not fail.

Handle authentication/authorization on frontend: Cognito JWT, token refresh.

Unified error handling: API returns error, frontend displays correct notification.

Manage versioning, stage environment: dev/staging/prod → avoid frontend calling wrong endpoint.

Optimize performance: multiple concurrent requests → avoid API Gateway throttling.

4. **Network Integration with VPC Peering**

Set up VPC Peering between FFF VPCs and Lambda/DynamoDB services that need to be accessed.

Configure route tables, security groups, NACLs so that Lambda/API Gateway traffic goes to the correct VPC.

Control DNS resolution between VPCs → avoid conflicts with private hosted zones.

Handle latency and throughput when peering multiple VPCs → affect performance.

Security control: only allow necessary IP/port, avoid exposing internal data.

When expanding multi-account → peering is complicated, difficult to scale if there are many VPCs.
