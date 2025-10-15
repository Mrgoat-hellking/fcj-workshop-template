---
title: "Week 6 Worklog"
date: 2025-10-13
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---



### Week 6 Objectives:

* Midterm review is intense
* Continue studying AWS services
* Working on the Project: Integrating AI into the website

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - - Network Monitoring with VPC Flow Logs <br> - Billing Console Delegationv                               | 13/10/2025 | 13/10/2025      |
| 3   | - Managing Quotas with Service Quotas <br>  - Cost and Usage Management        | 14/10/2025 | 14/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Snapshot Automation with Amazon EBS Data Lifecycle Manager <br> - Anomaly Detection for EBS Backups | 15/10/2025 | 15/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Development Environment with AWS Toolkit for VS Code <br> - Identity Federation with AWS Single Sign-On   | 16/10/2025 | 16/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | -                                                                             | 17/10/2025 | 17/10/2025      | <https://cloudjourney.awsstudygroup.com/> |


### Week 6 Achievements:

1. **Understanding AWS Services**

   * Monitoring & Logging: Track network and system activity through VPC Flow Logs and CloudWatch Logs.

   * Billing & Cost Management: Manage finances, delegate billing access, and monitor spending.

   * Quota Management: Control and request resource increases via Service Quotas.

   * Automation & Lifecycle: Automate snapshot creation and lifecycle management with EBS Data Lifecycle Manager.

   * Development Tools: Develop and deploy applications directly from VS Code using AWS Toolkit.

   * Identity & Access: Centralized access management through AWS Single Sign-On (IAM Identity Center).

2. **AWS Resource Practice and Operations**

* Network Monitoring:

  * Enabled VPC Flow Logs to monitor network traffic within the VPC.

  * Logged data into CloudWatch Logs, filtered and analyzed it to detect abnormal EC2 connections.

* Cost & Quota Management:

  * Reviewed and requested resource limit increases via Service Quotas.

  * Applied IAM Policies to restrict access by Region, instance type, and volume type for better cost control.

  * Granted Billing access to IAM users, monitored invoices, and reviewed cost reports through the Billing Console.

* Backup Automation:

  * Created EBS Snapshots and configured Data Lifecycle Manager (DLM) to automate backup, archiving, and deletion of old snapshots.

  * Set up multi-level snapshot schedules (daily/weekly) to optimize storage costs.

* Anomaly Detection:

  * Applied Anomaly Detection in CloudWatch or DLM to monitor unusual backup activities, ensuring data integrity.

* Development Environment:

  * Connected AWS to VS Code for deploying, monitoring, and managing resources without using the AWS Console.

  * Debugged and deployed serverless applications directly within the IDE.

* Centralized Identity Federation:

  * Configured AWS IAM Identity Center (SSO) to enable users to access multiple AWS accounts through a single portal.

  * Organized accounts under Organizational Units and assigned permissions to each group or project.

3. **Achievements**

* Mastered how to:

  * Monitor networks, traffic, and system logs using VPC Flow Logs.

  * Manage and optimize AWS operating costs.

  * Control and track resources via Service Quotas.

  * Automate backups using EBS Data Lifecycle Manager.

  * Set up AWS development environments directly in VS Code.

  * Centrally manage users and access through IAM Identity Center.

* Successfully connected and utilized AWS Console, AWS CLI, and AWS Toolkit for VS Code in parallel.

4. **Conclusion**

* Through these lessons, a complete AWS system management workflow was established, covering:

* Monitoring – Cost Management – Quota Control – Automation – Identity – Application Development.

* This integrated approach enables efficient AWS infrastructure operation, minimizes risks, enhances security, and optimizes resource usage.
