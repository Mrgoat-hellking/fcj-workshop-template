---
title: "Week 8 Worklog"
date: 2025-10-27
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---



### Week 8 Objectives:

* Continue learning and familiarizing yourself with AWS services
* Learn and implement projects
* 
### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - Containerization with Docker <br> - Container Orchestration with Amazon ECS <br> - Container Orchestration with Amazon ECS        | 27/10/2025 | 27/10/2025      |
| 3   | - CI/CD Pipeline with AWS CodePipeline <br>  - Automated Deployments with AWS CodePipeline <br> - DevOps with AWS CodePipeline     | 28/10/2025 | 28/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Hybrid Storage with AWS Storage Gateway <br> - Windows File Storage with Amazon FSx | 29/10/2025 | 29/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Windows File Storage with Amazon FSx <br> - Building Advanced Applications with Amazon DynamoDB       | 30/10/2025 | 30/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - Workflow Orchestration with AWS Step Functions <br> - Storage Performance Workshop     | 31/10/2025 | 31/10/2025      | <https://cloudjourney.awsstudygroup.com/> |


### Week 8 Achievements:

**Containerization with Docker**
* Build and push Docker images for backend + frontend, deploy on EC2.

* Create Docker network and launch containers, test applications via public IP.

* Use Docker Compose to manage stacks and redeploy the entire system quickly.

**Container Orchestration with Amazon ECS**
* Understand Amazon ECS architecture, create and manage ECS clusters.

* Define ECS tasks and services, configure Application Load Balancer for load balancing.

* Deploy containerized applications on ECS, test deployment and clean up resources after completion.

**Container Orchestration with Amazon ECS**
* Build containerized Spring Boot (Java 21) microservices and deploy to ECS Fargate.

* Use AWS CDK to create VPC + NAT Gateway, ECS Cluster, Load Balancer, and API Gateway.

* Create DynamoDB using CDK to serve as a backend storage for service “products”.

* Instrument ECS service with AWS X‑Ray (add sidecar, declare Inspector, test trace).

* Clean up resources after completing the workshop.

**CI/CD Pipeline with AWS CodePipeline**
* Set up automated CI/CD for containers on Amazon ECS, using GitLab, GitHub or CodeBuild.

* Deploy integration workflow (build → deploy) to ECS Service, ensuring automatic application updates.

* Monitor containers with Container Insights + collect logs via FireLens, ensuring effective observation and debugging.

* Clean up AWS resources after completion to optimize costs.

**Automated Deployments with AWS CodePipeline**

* Set up a CodePipeline pipeline integrating CodeCommit → CodeBuild → CodeDeploy to deploy Node.js applications to EC2.

* Configure CodeDeploy Agent on EC2 (via Session Manager or User Data).

* Deploy the application in-place to EC2 instances, test after deployment.

* Set up infrastructure (VPC, Security Group, RDS if needed) to serve the pipeline.

* Clean up AWS resources after completing the lab to save costs.

**DevOps with AWS CodePipeline**

* Create an IAM Role for CodeBuild to interact with the EKS cluster.

* Configure aws-auth to allow CodeBuild to use kubectl with permissions on the cluster.

* Set up a CodePipeline pipeline using CloudFormation to automatically build + deploy sample services to EKS.

* Trigger new releases when changing code on GitHub → automatically update services on EKS.

* Clean up all resources (deployment, stack, bucket) after the lab to avoid additional costs.

**Hybrid Storage with AWS Storage Gateway**

* Create S3 bucket + initialize EC2 to use as Storage Gateway.

* Configure AWS Storage Gateway, create SMB/NFS file share and mount on on-premises machine.

* Set up SMB access (guest) to share files from on-prem machine to S3.

* Test by creating files on mounted drive → files are synchronized to S3.

* Clean up resources: delete Gateway, EC2, S3 bucket after completion.

**Windows File Storage with Amazon FSx**

* Deploy FSx Windows File Server using CloudFormation in VPC.

* Create and map SMB file shares on EC2 Windows, test with sample data.

* Enable shadow copies to save previous file versions & configure backup storage.

* Enable Continuous Access share to support HA for applications such as SQL Server.

* Adjust storage capacity and throughput according to needs; clean up resources after doing lab

**Building Advanced Applications with Amazon DynamoDB**
* Do hands-on DynamoDB lab to understand the basics of querying, Streams, Global Tables and NoSQL data model.

* Build advanced “design patterns” for DynamoDB (partitioning, GSI, adjacency list).

* Deploy global serverless applications with DynamoDB Global Tables.

**Workflow Orchestration with AWS Step Functions**
* Design and implement state machine orchestration using Lambda: including task, branching (Choice) and parallel (Parallel).

* Configure retry & catch errors when Lambda encounters problems for more sustainable workflow.

* Use token callback (waitForTaskToken) to allow pause/resume workflow.

* Set up debugging / logging, visualize workflow and clean up resources after lab completion
**Storage Performance Workshop**
* Initialize resources via CloudFormation (EC2, Security Group) to run performance lab.

* Optimize S3 throughput, use parallel prefix, sync command, and upload multiple small files to increase TPS.

* Optimize EFS performance: configure IOPS, I/O size, multi-threading and choose appropriate performance mode.

* Clean up resources after lab: delete S3 bucket, terminate EC2, delete CloudFormation stack.