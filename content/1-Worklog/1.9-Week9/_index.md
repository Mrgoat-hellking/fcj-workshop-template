---
title: "Week 9 Worklog"
date: 2025-11-03
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---


### Week 9 Objectives:

* Learn more about aws services
* Continue working on the project

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - Serverless Backend with Lambda, S3, and DynamoDB <br> - Frontend Development for Serverless APIs  | 03/11/2025 | 03/11/2025      |
| 3   | - Deployment Automation with AWS SAM <br> - User Authentication with Amazon Cognito | 04/11/2025 | 04/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Custom Domains and SSL for Serverless Applications <br> - Event Processing with SQS and SNS| 05/11/2025 | 05/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - CI/CD for Serverless Applications <br> - Monitoring Serverless Applications <br> - Building GraphQL APIs with AWS AppSync | 06/11/2025 | 06/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   |  - Building Serverless APIs <br> - Serverless Chat Application | 07/11/2025 | 07/11/2025      | <https://cloudjourney.awsstudygroup.com/> |


### Week 9 Achievements:

#### **Frontend Development for Serverless APIs**

Build a web interface (frontend) to call API created by API Gateway + Lambda.

Deploy front-end: can host static site (HTML/CSS/JS) connecting to serverless backend.

Deploy Lambda function to handle request logic from API Gateway.

Configure API Gateway as endpoint for frontend: define route, HTTP method,…

Test API with Postman: ensure API Gateway + Lambda runs correctly before frontend calls.

Test frontend: web app calls API Gateway, receives results from Lambda and displays.

#### **Deployment Automation with AWS SAM**

Use AWS SAM (Serverless Application Model) to define serverless application via YAML file, then SAM will convert to CloudFormation when deploying.

Create and deploy front-end, Lambda function and API Gateway with SAM.

Test API with Postman and frontend after deploying.

#### **User Authentication with Amazon Cognito**

Create a Cognito User Pool to manage registration, login, email verification, password change, password reset.

Use Identity Pool if you need to grant AWS Credentials (temporarily) to users to access services such as S3, DynamoDB.

Create API and Lambda: after the user authenticates via Cognito, Lambda handles the API request.

Frontend: build login/registration UI, call Cognito API to log in and get token; then send token to API Gateway/Lambda.

#### **Custom Domains & SSL for Serverless Apps**

Use API Gateway to configure a custom domain name (“custom domain”) instead of the default hostname of API Gateway.

Use Amazon Certificate Manager (ACM) to create or import SSL/TLS certificate for the domain, ensuring HTTPS.

Select custom domain type: edge-optimized (using CloudFront) or regional.

Configure Base Path Mapping to map domain + path to API Gateway stages.

Create DNS record (Route 53 or other DNS) to point domain to CloudFront distribution or endpoint provided by API Gateway.

SSL and security: you can choose TLS security policy, ACM will manage certificate renewal.
AWS Docs

#### **Event Processing with SQS & SNS **

When users place an order, API sends messages to SQS queue to ensure “queue” to process the order.

At the same time, SNS is used to notify admin every time there is a new order.

Create Lambdas:

* checkout_order to receive orders from API and push messages to SQS + publish SNS.

* handle_order for admin to process orders: read from SQS, write orders to DynamoDB.

* delete_order for admin to delete order: delete message in SQS.

* order_management for admin to view order list (using DynamoDB).

Architecture uses SQS for durability and asynchronous processing, SNS for fan-out notifications.

#### **CI/CD for Serverless Apps**

Use AWS SAM Pipelines to automate the process of building, packaging and deploying serverless applications.

Initialize CI/CD pipeline: sam pipeline init to create pipeline configuration for AWS CodePipeline

Pipeline includes many stages: Source (Git), Build (using SAM CLI), Deploy (CloudFormation/SAM).

Use build container image provided by AWS SAM to compile serverless app, helping reduce the effort of creating separate CI image.

Pipeline follows AWS best-practice pattern: supports multi-account, multi-region.

#### **Monitoring Serverless Applications**

Use CloudWatch Logs to debug Lambda: log invocations, errors, etc.

Create custom metrics in CloudWatch to monitor business or performance metrics.

Configure CloudWatch Alarms based on metrics to alert when there is an abnormal situation.

Use AWS X-Ray to trace requests: draw service maps, see the path of requests and find bottlenecks.

###**Building GraphQL APIs with AWS AppSync**

Use AWS AppSync to create serverless GraphQL APIs, combined with AWS data sources such as DynamoDB, Lambda or Aurora Serverless.

Define GraphQL schema: type, query, mutation, subscription (if real-time required).
AWS Docs

Configure resolvers:

Use VTL mapping template to convert GraphQL requests into data source query operations.

Or use Direct Lambda Resolver: Lambda handles GraphQL logic, avoiding the need to write VTL.

If using a relational database (Aurora Serverless), AppSync can connect via Data API to execute SQL commands via GraphQL mutation/query.

API access can be managed in the following ways: AWS IAM, Cognito User Pools,… (authentication + authorization).

#### **Building Serverless APIs (Serverless with Lambda, API Gateway and SAM)**

Backend architecture uses Lambda, API Gateway, DynamoDB, S3, and Cognito.

Frontend is a JavaScript application (Vue.js) hosted on S3 / Amplify.

Use AWS SAM to define serverless resources and deploy backend (Lambda + API Gateway + DynamoDB)

Lambda reads / writes data from DynamoDB: for example, Lambda scans DynamoDB table to return list of “parks” (rides, attractions).

Deploy API Gateway for frontend to call API; Lambda handles request logic.

In realtime: Lambda subscribes to SNS topic, saves information to DynamoDB, and forwards payload to IoT Core so frontend can receive real-time data.

#### **Serverless Chat Application**

Build a serverless real-time chat application using API Gateway WebSocket, Lambda, and DynamoDB.

When a client connects (“$connect”), Lambda stores the connection ID in DynamoDB.

When a client disconnects (“$disconnect”), Lambda deletes the connection ID from DynamoDB.

When a client sends a message (“sendmessage” route), Lambda reads the connection IDs from DynamoDB and uses the API Gateway Management API to broadcast the message to all connected clients.
