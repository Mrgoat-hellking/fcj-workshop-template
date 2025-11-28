---
title: "Week 10 Worklog"
date: 2025-11-10
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---


### Week 10 Objectives:

* Connect and get acquainted with members of First Cloud Journey.
* Understand basic AWS services, how to use the console & CLI.

### Tasks to be carried out this week:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Elastic Beanstalk Workshop <br>&emsp; - Deploying Node.js Applications  <br>&emsp;  -  CI/CD with Elastic Beanstalk and CDK Pipelines                                       | 10/11/2025   | 10/11/2025      |
| 3   | - WordPress on AWS <br>&emsp; -  WordPress Architecture on AWS <br>&emsp; - Running WordPress on Amazon EC2  | 11/11/2025   | 11/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Amazon ECS Workshop <br>&emsp; -  Containerization with Amazon ECS and AWS Fargate <br>&emsp; - Infrastructure as Code for ECS with CDK  <br>&emsp; - CI/CD Pipeline for ECS Applications| 12/11/2025   | 12/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Machine Learning Essentials <br>&emsp; - Machine Learning with Amazon SageMaker <br>&emsp; - SageMaker Immersion Day  | 13/11/2025   | 13/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - Data Lake <br>&emsp;  - Data Lake Fundamentals on <br>&emsp; - Building a Data Lake with Your Own DataAWS                                                      | 14/11/2025   | 14/11/2025      | <https://cloudjourney.awsstudygroup.com/> |



### Week 10 Achievements:

#### **Elastic Beanstalk Workshop**

#### **Deploying Node.js Applications with Elastic Beanstalk**

Deploy Node.js applications using Elastic Beanstalk to automate deployment, scaling, and application environment management.

Elastic Beanstalk supports Node.js platform, self-configuring EC2, load balancer, auto-scaling, and runtime environment.

Deploy applications: use EB CLI (eb init, eb create, eb deploy) to package source code, create environment, and publish the app.

Environment management: monitor logs, configure scaling, update version, and rollback when needed.

#### **CI/CD with Elastic Beanstalk and CDK Pipelines**

Set up automated CI/CD for applications using AWS CDK Pipelines and Elastic Beanstalk.

CDK defines infrastructure: create Elastic Beanstalk Application, Environment, and Pipeline as IaC.

Pipeline: get source from repository, build application, create package and automatically deploy to Elastic Beanstalk every time there is a change in source code.

Deployment: run cdk deploy for the first time to create pipeline; from then on, all code changes will be automatically built and updated to EB environment.

Extendable support: can add more stages (dev/staging/prod), add test steps or pre-post-deploy authentication.

#### **WordPress on AWS**
#### **WordPress Architecture on AWS**
Deploy WordPress on AWS in a multi-tier architecture to increase performance and scalability.

Web tier: run WordPress on EC2s in Auto Scaling Group, receive traffic via Application Load Balancer.

Database: use RDS/Aurora MySQL to store WordPress data securely and sustainably.

File sharing: use EFS to share plugins, themes, uploads between multiple EC2s.

Static content: store images on S3 and distribute via CloudFront to reduce load and speed.

Caching: integrate ElastiCache to optimize queries and reduce pressure on the database.

#### **Running WordPress on Amazon EC2**

Use Amazon EC2 to initialize a server (instance) — run web server + PHP + MySQL (or MariaDB) to host WordPress.

Make sure the security group configuration allows HTTP (and if necessary HTTPS) for users to access the website from the Internet.

Install Apache (httpd), PHP + MySQL extension; download WordPress, unzip to the web root directory, configure the wp-config.php file to connect to the database.

Start the web service + database; then access the public DNS/IP to run the WordPress installation script, set up the site.

#### **Amazon ECS Workshop**
#### **Containerization with Amazon ECS and AWS Fargate**

Docker → package applications into containers (Docker images).

Amazon ECS: container orchestration service — manage scheduling, scaling, and deployment of containers.

AWS Fargate: serverless compute engine for containers — run containers without managing underlying servers/EC2s.

#### **CI/CD Pipeline for ECS Applications**

Using containers + registry: package applications into Docker images, push them to Amazon ECR.
AWS Docs

The pipeline consists of the following main steps: Source → Build → Deploy. Source from Git repo (e.g., GitHub/CodeCommit), Build with AWS CodeBuild to create a Docker image, and then push the image to ECR.

AWS Builder Center

After the build, the pipeline deploys the new image to the ECS cluster: ECS pulls the image from ECR and re-runs the service/container (usually Fargate), ensuring automated deployment and minimal downtime.

#### **Machine Learning Essentials**
#### **Machine Learning with Amazon SageMaker***

Amazon SageMaker is a full-stack ML service on AWS that helps you build, train, and deploy ML/AI models without having to manage the infrastructure yourself.

You can use the SageMaker Studio integrated environment (IDE) to develop, process data, test, and deploy models.

SageMaker supports the entire ML workflow — from data preparation, feature engineering, model training, hyper-parameter tuning, to deploying models into production.

#### **SageMaker Immersion Day**

SageMaker Immersion Day is a hands-on workshop for ML engineers / data scientists / developers who want to learn the end-to-end ML process with SageMaker: from data processing → feature-engineering → train → deploy model.

The main steps in the workshop: open an environment with SageMaker Studio, prepare dataset (upload to S3), feature-engineering, train & tune the model, then deploy the model & test inference.

The workshop provides both built-in algorithms and the ability to use custom models (bring-your-own-model), allowing you to try both basic ML and custom ML.

### **Data Lake**
#### **Data Lake Fundamentals on AWS**

A Data Lake is a central repository for storing any data — structured, semi-structured, unstructured — at any scale, keeping the data “raw” without any pre-formatting.

AWS uses Amazon S3 as the primary storage platform for your Data Lake — it’s simple, flexible, scalable, and integrates well with other analytics services.

To manage metadata and schemas, use AWS Glue (Glue Data Catalog, crawler) to “catalog” your data — making it easy to find, analyze, and share data across teams.

#### **Building a Data Lake with Your Data on AWS**

Storing raw data — uploading data (CSV, JSON, logs, etc.) to Amazon S3; S3 acts as the central repository for your data lake.

Using AWS Glue to crawl data: auto-discovern schema, table; create metadata/catalog for easy management & query.

Build serverless ETL/ELT pipeline: Glue processes ingest & transform data (from raw → cleaned/structured) before saving to S3 (can be in layers raw → refined → aggregated).