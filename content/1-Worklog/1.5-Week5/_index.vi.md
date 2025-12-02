---
title: "Worklog Tuần 5"
date: 2025-10-06
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---


### Mục tiêu tuần 5:

* Tiếp tục học các dịch vụ của AWS
* Tiếp tục làm Ptoject 

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Serverless Automation with AWS Lambda <br> - Advanced Monitoring with CloudWatch and Grafana   | 06/10/2025   | 06/10/2025      |
| 3   | - CloudWatch Advanced Workshop <br> - Resource Organization with Tags and Resource Groups                         |07/10/2025   | 07/10/2025      |  |
| 4   | - Access Control with IAM and Resource Tags <br> - Systems Management with AWS Systems Manager    | 08/10/2025   | 08/10/2025      | |
| 5   | - Remote Server Access with Systems Manager Session Manag <br> - Infrastructure as Code with AWS CloudFormation <br> - Cloud Development Kit (AWS CDK) Essentials | 09/10/2025   | 09/10/2025      |  |
| 6   | -  AWS CDK Advanced <br> - Infrastructure as Code Workshop Series <br> -Right-Sizing with EC2 Resource Optimization                                                 | 10/10/2025   | 10/10/2025      | |

### Kết quả đạt được tuần 5:

 1. Hiểu và nắm được kiến thức trọng tâm

* Hiểu rõ khái niệm Serverless Computing và cách AWS Lambda hoạt động dựa trên sự kiện (Event-driven).
* Nắm được các dịch vụ giám sát nâng cao gồm Amazon CloudWatch và Grafana để theo dõi hiệu suất hệ thống.

* Hiểu tổ chức và phân loại tài nguyên bằng Tags và Resource Groups.
*
* Nắm vững quản lý truy cập với IAM Policies kết hợp Resource Tags nhằm đảm bảo nguyên tắc Least Privilege.

* Biết cách quản trị hệ thống tập trung thông qua AWS Systems Manager (Automation, Inventory, Compliance).

* Hiểu cơ chế truy cập máy chủ từ xa an toàn với Systems Manager Session Manager, không cần SSH key.

* Nắm rõ khái niệm và quy trình triển khai hạ tầng như mã (Infrastructure as Code – IaC) thông qua AWS CloudFormation và AWS CDK.

* Phân biệt và ứng dụng CDK Essentials và CDK Advanced trong việc tái sử dụng và mở rộng cấu trúc hạ tầng.

* Hiểu và áp dụng Right-Sizing & Resource Optimization trong EC2 nhằm tiết kiệm chi phí và nâng cao hiệu suất.

2. Thực hành và cấu hình trên AWS

* Đã tạo và cấu hình các Lambda function để tự động hóa tác vụ như xử lý log hoặc backup dữ liệu.

* Thiết lập CloudWatch Dashboards, Metrics, Logs, và Alarms để giám sát hiệu suất EC2, RDS, Lambda.

* Kết nối Amazon Managed Grafana để trực quan hóa dữ liệu CloudWatch.

* Tạo và áp dụng Resource Tags nhất quán để phân nhóm tài nguyên theo dự án, môi trường, và chi phí.

* Thiết lập IAM Policies có điều kiện theo Tag nhằm kiểm soát quyền truy cập chính xác.

* Cấu hình AWS Systems Manager để quản lý phiên bản, chạy Automation Documents, và kiểm tra Compliance.

* Sử dụng Session Manager để truy cập EC2 mà không cần mở cổng SSH, đảm bảo bảo mật.

* Triển khai CloudFormation Templates (YAML/JSON) để tạo hạ tầng tự động gồm EC2, S3, IAM Roles, Security Groups.

* Phát triển và triển khai hạ tầng bằng AWS CDK (Python/TypeScript), sử dụng Constructs và Stacks để tổ chức mã nguồn.

* Thực hành CDK Workshop Series để tạo pipeline tự động hóa triển khai đa môi trường (dev, test, prod).

* Sử dụng Compute Optimizer và Cost Explorer để xác định loại EC2 tối ưu và đề xuất Right-Sizing.

3. Kết quả đạt được

* Nắm vững các công cụ tự động hóa quản lý và triển khai hạ tầng AWS (Lambda, CloudFormation, CDK).

* Biết cách giám sát, phân tích, và tối ưu tài nguyên bằng CloudWatch, Grafana và Systems Manager.

* Thành thạo kỹ năng truy cập và điều phối hệ thống thông qua Session Manager mà không cần SSH.

* Áp dụng hiệu quả nguyên tắc Least Privilege khi phân quyền IAM.

* Biết cách tối ưu chi phí và hiệu năng EC2 dựa trên dữ liệu thực tế.

* Sẵn sàng triển khai môi trường hạ tầng linh hoạt, tự động hóa và tiết kiệm chi phí trên AWS.

4. Kết nối và mở rộng

* Kết hợp sử dụng AWS Management Console và AWS CLI/CDK để quản lý tài nguyên song song.

* Có khả năng phân tích log, tạo cảnh báo, và phản ứng tự động bằng Lambda + CloudWatch Events.

  * Sẵn sàng mở rộng học tập sang DevOps pipelines (CodePipeline, CodeBuild) và bảo mật đa tầng (KMS, SCPs).