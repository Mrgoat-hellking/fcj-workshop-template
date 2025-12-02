---
title: "Week 7 Worklog"
date: 2025-10-20
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---


### Week 7 Objectives:

* Continue studying and becoming familiar with AWS services.
* No new topics this week—focus on review in preparation for the midterm on October 31.
* Additional learning through Udemy – CLF-C02 course.
### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | -  Security Compliance with AWS Security Hub <br> - Private Access to S3 with VPC Endpoints <br> - Application Protection with AWS WAF    | 20/10/2025 | 20/10/2025      |
| 3   | -  Encryption with AWS Key Management Service (KMS) <br> - Data Protection with Amazon Macie <br> - Credentials Management with AWS Secrets Manager       | 21/10/2025 | 21/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | -  Security Governance with AWS Firewall Manager <br> - Threat Detection with AWS GuardDuty <br> - Systems Patching with EC2 Image Builder | 22/10/2025 | 22/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | -  Cross-Domain Authentication with Amazon Cognito <br>  - S3 Security Best Practices <br> - Data Protection with AWS Backup    | 23/10/2025 | 23/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | -  Network Integration with VPC Peering <br> - Centralized Network Management with AWS Transit Gateway <br> - Messaging Systems with SQS and SNS                            | 24/10/2025 | 24/10/2025      | <https://cloudjourney.awsstudygroup.com/> |


### Week 7 Achievements:

* **AWS Security Hub**
* Gained understanding of AWS Security Hub’s role in maintaining security compliance across AWS environments.

   + Functions: collects and standardizes findings in the AWS Security Finding Format (ASFF).

   + Provides a security score representing the ratio of compliant controls to total active controls.

   + Each standard includes multiple controls that continuously scan and assess AWS resources, producing results categorized as Passed, Failed, Unknown, or No data.

* **Private Access to S3 with VPC Endpoints**
Established a secure connection from a VPC to AWS services without public IPs or an Internet Gateway.

+ Gateway Endpoints: used for S3 and DynamoDB, routing internally via route tables.

+ Interface Endpoints: use PrivateLink through ENIs and internal DNS.

+ Configured a Gateway Endpoint for S3 and verified connectivity through the CLI without public internet traversal.

* **Application Protection with AWS WAF**
AWS WAF provides web application firewall capabilities for monitoring and controlling HTTP(S) traffic to CloudFront, ALB, or API Gateway.

+ Core functions: allow or block requests based on IP, query strings, or attack patterns.

+ Supports both managed rule groups and custom rule sets.

+ Integrated with AWS Shield, CloudFront, or ALB for comprehensive protection.

+ Successfully created and attached a Web ACL to a CloudFront distribution.

* **Encryption with AWS Key Management Service (KMS)**
AWS KMS offers centralized key management for encryption operations.

+ Supports symmetric and asymmetric encryption with IAM and key policies for access control.

+ Includes AWS-managed and customer-managed keys (CMKs).

+ Integrated with S3, EBS, RDS, Lambda, and CloudTrail.

+ Created a customer-managed CMK and configured usage permissions.

* **Data Protection with Amazon Macie**
* Amazon Macie automatically detects, classifies, and protects sensitive data stored in S3.

+ Provides inventory, monitors access control, and alerts on potential data leaks.

+ Two operating modes: Automated Sensitive Data Discovery and Custom Discovery Jobs.

+ All results are encrypted using AWS KMS.

+ Successfully deployed Macie for automated detection of sensitive data in S3.

* **Credentials Management with AWS Secrets Manager**
* AWS Secrets Manager securely manages sensitive credentials such as passwords, API keys, and tokens.

+ Integrates with RDS, Redshift, and DocumentDB for automatic password rotation via Lambda.

+ Encrypts secrets with KMS.

+ Successfully implemented Secrets Manager for secure and automated credential management.

* **Security Governance with AWS Firewall Manager**
Centralized policy management service for enforcing consistent firewall configurations across AWS Organizations.

+ Integrates with AWS WAF, Shield Advanced, Security Groups, and VPCs.

+ Synchronizes alerts and compliance statuses through Security Hub.

+ Enables standardized, organization-wide security control.

+ Successfully created Firewall Manager to enforce unified firewall policies.

* **Threat Detection with AWS GuardDuty**
GuardDuty uses machine learning and threat intelligence to detect anomalies and potential security threats.

+ Monitors CloudTrail, VPC Flow Logs, and DNS logs for malicious or unauthorized activity.

+ Detects reconnaissance, compromised credentials, and communication with malicious domains.

+ Integrates with Security Hub, EventBridge, and Lambda for automated response.

+ Successfully deployed GuardDuty for continuous threat detection and alerting.

* **Systems Patching with EC2 Image Builder**
Automates the creation, testing, and deployment of secure AMIs.

+ Pipeline stages: source → build → test → distribute.

+ Supports custom components for installing software and applying security patches.

+ Integrates with SSM, CloudWatch, and IAM for automation.

+ Successfully created Image Builder pipeline for secure AMI maintenance.

* **Cross-Domain Authentication with Amazon Cognito**
AWS Cognito manages user authentication and authorization.

+ Consists of User Pools for authentication and Identity Pools for temporary AWS access.

+ Supports MFA, email verification, password reset, and cross-domain federated sign-in.

+ Integrated with API Gateway, AppSync, and mobile applications.

+ Successfully deployed Cognito for user authentication and federated access.

* **S3 Security Best Practices**
Implemented security best practices for S3 data protection.

+ Principles: Private by default, Block Public Access, Encryption (SSE-S3/SSE-KMS), and Access Control via IAM/Bucket Policies/ACLs.

+ Combined with Macie, GuardDuty, and Security Hub for compliance monitoring.

+ Successfully configured S3 for secure storage and access management.

* **Data Protection with AWS Backup**
AWS Backup provides centralized and automated backup management across AWS resources.

+ Defines Backup Plans, Vaults, and Lifecycle Policies.

+ Encrypts all data with KMS and supports cross-region/cross-account backup.

+ Backup Audit Manager ensures compliance and visibility.

+ Successfully created AWS Backup for automated backup and recovery.

* **Network Integration with VPC Peering**
Established secure communication between two VPCs using private IPs.

+ Point-to-point, non-transitive connection with low latency and high security.

+ Supports inter-region connectivity if CIDR blocks do not overlap.

+ Configured route tables for internal communication across resources.

+ Successfully created VPC Peering for secure inter-VPC traffic.

* **Centralized Network Management with AWS Transit Gateway**
AWS Transit Gateway acts as a central hub for connecting multiple VPCs, VPNs, and Direct Connect links.

+ Simplifies complex peering meshes with transitive routing capability.

+ Provides attachment-based routing tables for granular traffic control.

+ Supports multicast, cross-account, cross-region, and high-bandwidth connections.

+ Integrated with AWS Network Manager for monitoring and topology management.

+ Successfully deployed Transit Gateway for centralized network management.

* **Messaging Systems with SQS and SNS**
Implemented asynchronous messaging architecture using SQS and SNS.

+ SQS: message queue system with Standard and FIFO queues for reliable delivery.

+ SNS: publish/subscribe system for distributing notifications across multiple endpoints.

+ Combined SNS and SQS for fan-out message distribution.

+ Ensures high scalability, reliability, and decoupling of microservices.

+ Successfully built an asynchronous messaging system using SQS and SNS.

* **Conclusion**

* All AWS Security services are closely integrated, collectively strengthening cloud defense posture. However, the ecosystem is complex and requires extensive hands-on experience to master.
* For midterm preparation, six review sections have been completed and continuously revisited.
