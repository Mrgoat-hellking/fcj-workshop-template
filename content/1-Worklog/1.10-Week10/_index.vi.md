---
title: "Worklog Tuần 10"
date: 2025-11-10
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---



### Mục tiêu tuần 10:

* Tìm hiểu sâu hơn về các dịch vụ aws 
* Tiếp tục làm project 

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Elastic Beanstalk Workshop <br>&emsp; - Deploying Node.js Applications  <br>&emsp;  -  CI/CD with Elastic Beanstalk and CDK Pipelines                                       | 10/11/2025   | 10/11/2025      |
| 3   | - WordPress on AWS <br>&emsp; -  WordPress Architecture on AWS <br>&emsp; - Running WordPress on Amazon EC2  | 11/11/2025   | 11/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Amazon ECS Workshop <br>&emsp; -  Containerization with Amazon ECS and AWS Fargate <br>&emsp; - Infrastructure as Code for ECS with CDK  <br>&emsp; - CI/CD Pipeline for ECS Applications| 12/11/2025   | 12/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Machine Learning Essentials <br>&emsp; - Machine Learning with Amazon SageMaker <br>&emsp; - SageMaker Immersion Day  | 13/11/2025   | 13/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - Data Lake <br>&emsp;  - Data Lake Fundamentals on <br>&emsp; - Building a Data Lake with Your Own DataAWS                                                      | 14/11/2025   | 14/11/2025      | <https://cloudjourney.awsstudygroup.com/> |


### Kết quả đạt được tuần 10

Deploying Node.js Applications với Elastic Beanstalk
Triển khai ứng dụng Node.js bằng Elastic Beanstalk để tự động hóa quá trình deploy, scaling và quản lý môi trường chạy ứng dụng.

Elastic Beanstalk hỗ trợ Node.js platform, tự thiết lập EC2, load balancer, auto scaling và môi trường runtime.

Triển khai ứng dụng: dùng EB CLI (eb init, eb create, eb deploy) để đóng gói mã nguồn, tạo environment và xuất bản app.

Quản lý môi trường: theo dõi logs, cấu hình scaling, cập nhật version, rollback khi cần.

Frontend hoặc client có thể gọi API Node.js được deploy trên Elastic Beanstalk thông qua domain ứng dụng.