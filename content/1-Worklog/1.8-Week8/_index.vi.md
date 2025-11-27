---
title: "Worklog Tuần 8"
date: 2025-10-27
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---



### Mục tiêu tuần 8:

  * Tiếp tục học tập và làm quen với các dịch vụ của AWS
  * Tìm hiểu và làm project

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Containerization with Docker <br> - Container Orchestration with Amazon ECS <br> - Container Orchestration with Amazon ECS | 27/10/2025   | 27/10/2025      |
| 3   | - CI/CD Pipeline with AWS CodePipeline <br>  - Automated Deployments with AWS CodePipeline <br> - DevOps with AWS CodePipeline | 28/10/2025   | 28/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Hybrid Storage with AWS Storage Gateway <br> - Windows File Storage with Amazon FSx | 29/10/2025   | 29/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Windows File Storage with Amazon FSx <br> - Building Advanced Applications with Amazon DynamoDB  | 30/10/2025   | 30/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - Workflow Orchestration with AWS Step Functions <br> - Storage Performance Workshop  | 31/10/2025   | 31/10/2025      | <https://cloudjourney.awsstudygroup.com/> |


### Kết quả đạt được tuần 8:

**Containerization with Docker**
* Build và push Docker image cho backend + frontend, triển khai trên EC2.

* Tạo Docker network và khởi chạy container, kiểm thử ứng dụng qua public IP.

* Sử dụng Docker Compose để quản lý stack và deploy lại toàn hệ thống nhanh chóng.

**Container Orchestration with Amazon ECS**
* Hiểu kiến trúc Amazon ECS, tạo và quản lý cluster ECS. 


* Định nghĩa task và service ECS, cấu hình Application Load Balancer để cân bằng tải. 


* Triển khai ứng dụng container hóa trên ECS, kiểm thử deployment và dọn dẹp tài nguyên sau khi hoàn thành. 

**Container Orchestration with Amazon ECS**
* Xây dựng microservice Spring Boot (Java 21) container hóa và deploy lên ECS Fargate. 

* Sử dụng AWS CDK để tạo VPC + NAT Gateway, ECS Cluster, Load Balancer, và API Gateway. 

* Tạo DynamoDB bằng CDK để làm backend lưu trữ cho service “products”. 

* Instrument hóa ECS service với AWS X‑Ray (thêm sidecar, khai báo Inspector, test trace). 

* Dọn dẹp tài nguyên sau khi hoàn thành workshop. 

**CI/CD Pipeline with AWS CodePipeline**
* Thiết lập CI/CD tự động cho container trên Amazon ECS, sử dụng GitLab, GitHub hoặc CodeBuild. 
  
* Triển khai quy trình tích hợp (build → deploy) lên ECS Service, đảm bảo tự động cập nhật ứng dụng. 


* Giám sát container bằng Container Insights + thu log qua FireLens, đảm bảo quan sát và debug hiệu quả. 

* Dọn dẹp tài nguyên AWS sau khi hoàn thành để tối ưu chi phí.

**Automated Deployments with AWS CodePipeline**

* Thiết lập pipeline CodePipeline tích hợp CodeCommit → CodeBuild → CodeDeploy để deploy ứng dụng Node.js lên EC2. 

* Cấu hình CodeDeploy Agent trên EC2 (qua Session Manager hoặc User Data). 

* Triển khai ứng dụng theo kiểu “in‑place” lên các instance EC2, kiểm thử sau deploy. 


* Thiết lập hạ tầng (VPC, Security Group, RDS nếu cần) phục vụ pipeline. 

* Dọn dẹp tài nguyên AWS sau khi hoàn thành lab để tiết kiệm chi phí.

**DevOps with AWS CodePipeline**

* Tạo IAM Role để CodeBuild tương tác với EKS cluster. 

* Cấu hình aws-auth để cho phép CodeBuild sử dụng kubectl với quyền trên cluster. 

* Thiết lập pipeline CodePipeline bằng CloudFormation để tự động build + deploy service mẫu lên EKS. 


* Kích hoạt release mới khi thay đổi code trên GitHub → tự động cập nhật service trên EKS. 

* Dọn dẹp toàn bộ tài nguyên (deployment, stack, bucket) sau lab để tránh chi phí phát sinh.

**Hybrid Storage with AWS Storage Gateway**

* Tạo S3 bucket + khởi tạo EC2 dùng làm Storage Gateway. 

* Cấu hình AWS Storage Gateway, tạo file share SMB/NFS và mount trên máy on‑premises. 

* Thiết lập quyền truy cập SMB (guest) để chia sẻ file từ máy on‑prem lên S3. 

* Kiểm tra bằng cách tạo file trên ổ mount → file được đồng bộ lên S3. 

* Dọn dẹp tài nguyên: xóa Gateway, EC2, S3 bucket sau khi hoàn thành.

**Windows File Storage with Amazon FSx**

* Triển khai FSx Windows File Server bằng CloudFormation trong VPC. 

* Tạo và ánh xạ các file share SMB trên EC2 Windows, kiểm thử với dữ liệu mẫu. 

* Kích hoạt shadow copies để lưu phiên bản file trước đó & cấu hình lưu trữ dự phòng. 

* Kích hoạt Continuous Access share để hỗ trợ HA cho ứng dụng như SQL Server. 

* Điều chỉnh dung lượng lưu trữ và hiệu năng (throughput) theo nhu cầu; dọn dẹp tài nguyên sau khi làm lab

**Building Advanced Applications with Amazon DynamoDB**
* Làm hands-on lab DynamoDB để nắm cơ bản truy vấn, Streams, Global Tables và mô hình dữ liệu NoSQL. 

* Xây dựng các “design pattern” nâng cao cho DynamoDB (partitioning, GSI, adjacency list). 

* Triển khai ứng dụng serverless toàn cầu với DynamoDB Global Tables.

**Workflow Orchestration with AWS Step Functions**
* Thiết kế và triển khai state machine orchestration dùng Lambda: bao gồm task, branching (Choice) và song song (Parallel). 

* Cấu hình retry & bắt lỗi (catch) khi Lambda gặp sự cố để workflow bền vững hơn. 

* Sử dụng token callback (waitForTaskToken) để cho phép pause/resume luồng công việc. 

* Thiết lập debugging / logging, visual hóa luồng công việc và dọn dẹp tài nguyên sau khi hoàn thành lab
**Storage Performance Workshop**
* Khởi tạo tài nguyên qua CloudFormation (EC2, Security Group) để chạy lab hiệu suất. 

* Tối ưu throughput S3, sử dụng parallel prefix, sync command, và upload nhiều file nhỏ để tăng TPS.

* Tối ưu hiệu suất EFS: cấu hình IOPS, kích thước I/O, multi-threading và lựa chọn chế độ hiệu suất phù hợp. 

* Dọn dẹp tài nguyên sau lab: xóa bucket S3, terminate EC2, xóa CloudFormation stack. 


