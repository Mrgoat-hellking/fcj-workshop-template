---
title: "Week 3 Worklog"
date: 2025-09-22
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---


### Week 3 Objectives:

* Continue learning and exploring more AWS functionalities.
* Module 3

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - Scaling Applications with EC2 Auto Scaling <br> - Monitoring with Amazon CloudWatch                                                                                                   | 09/22/2025 | 09/22/2025      |
| 3   | - Hybrid DNS Management with Amazon Route 53 <br> - Command Line Operations with AWS CLI                                    | 09/23/2025 | 09/23/2025      |  |
| 4   | - NoSQL Database Essentials with Amazon DynamoDB <br> - In-Memory Caching with Amazon ElastiCache | 09/24/2025 | 09/24/2025      |  |
| 5   | - Networking on AWS Workshop   <br> - Write Proposal  | 09/25/2025 | 09/25/2025      |  |
| 6   | -  Content Delivery with Amazon CloudFront  <br> - Write Proposal                                                                     | 09/26/2025 | 09/26/2025      |  |


### Achievements in Week 3:

* **Understanding application deployment architecture on AWS** with scalability using EC2 Auto Scaling:

  * Create Launch Template
  * Configure Load Balancer (Target Group + Load Balancer)
  * Create Auto Scaling Group
  * Experiment with scaling methods: manual, scheduled, dynamic/predictive
  * Read metrics/data from predictive scaling
  * Cleanup resources afterward

* Capabilities achieved:

  * Deploy a web application with scalable architecture. From an application running on a single server, you can move to a cluster architecture with load balancing and auto scaling.

* Basic EC2 practice:

  * Monitoring with Amazon CloudWatch
  * Hybrid DNS Management with Amazon Route 53
  * Command Line Operations with AWS CLI

* EC2 Instance initialization and management:

  * Create, configure, and launch EC2
  * Connect to the instance via SSH
  * Manage lifecycle (Start/Stop/Terminate)

* Networking & Security:

  * Create and edit Security Groups to control access
  *  Use Elastic IP for assigning static IP to EC2

* Application Deployment:

  * Install basic software on EC2
  * Deploy a simple web application

* Skills gained:

  * Mastering virtual server administration on AWS
  * Understanding connection and security for application infrastructure

* Storage & Access Management:

  * NoSQL Database Essentials with Amazon DynamoDB
  * In-Memory Caching with Amazon ElastiCache
  * Networking on AWS Workshop

* Amazon S3 (Simple Storage Service):

  * Create and manage buckets
  * Upload/Download data
  * Configure access permissions (public/private)
  * Manage Versioning to track file history

* IAM (Identity and Access Management):

  * Create Users, Groups, Roles
  * Assign Policies following the “least privilege” principle
  * Manage Access Keys and Secret Keys securely

* CloudWatch:

  * Monitor system metrics
  * Record logs for EC2 and other services

* Skills gained:

  * Build security and access control foundation in AWS
  * Monitor and optimize system operations

  * Content Delivery with CloudFront + S3

* Amazon CloudFront:

  * CDN service that speeds up content delivery using caching at edge locations

  * S3 + CloudFront integration:

  * S3 bucket as origin storing static content (HTML, CSS, JS, images)
  *  CloudFront distributes and caches content, reducing latency for end-users

* Practice:

  * Create an S3 bucket and upload content
  * Create CloudFront distribution pointing to S3 origin
  * Configure cache policy, TTL, and access permissions
  * Test website delivery via CloudFront
  * Delete resources after completion to avoid costs

* Skills gained:

  * Build a high-performance static website using S3 + CloudFront
  * Manage caching and secure content delivery
  * Takeaways after the workshop series:
  * Foundational knowledge: Understanding AWS core services
  * Administration skills: Practice managing resources through Console and CLI
  * Application deployment: Create EC2, configure networking, distribute content with S3 + CloudFront
  * Security & monitoring: Manage permissions with IAM, monitor systems with CloudWatch
  * Practical application ability: Capable of deploying a basic web system on AWS with performance, security, scalability, and cost optimization.
