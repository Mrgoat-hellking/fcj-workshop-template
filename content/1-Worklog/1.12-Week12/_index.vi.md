---
title: "Worklog Tuần 12"
date: 2025-01-01
weight: 12
chapter: false
pre: " <b> 1.12 </b> "
---


### Mục tiêu tuần 12:

* tiến vào giai đoạn nước rút của Project
* ôn lại các dịch vụ sẽ dùng

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Database Essentials with Amazon Relational Database Service (RDS)                    | 11/08/2025   | 11/08/2025      |
| 3   | - Access Management with AWS Identity and Access Management (IAM)                         | 12/08/2025   | 12/08/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Serverless Automation with AWS Lambda| 13/08/2025   | 13/08/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - AWS CDK Advanced      | 14/08/2025   | 15/08/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - Application Protection with AWS WAF                             | 15/08/2025   | 15/08/2025      | <https://cloudjourney.awsstudygroup.com/> |


### Kết quả đạt được tuần 12:

* **Serverless, Amplify & Network Integration Challenges**

API Gateway đồng bộ request/response, handler & business logic tách riêng, error handling rõ ràng

Chuyển từ RDS sang DynamoDB: PK/SK, GSI, dữ liệu nhiều quan hệ khó tối ưu One-Table

Logging phân tán CloudWatch → debug khó

IAM role tối thiểu cho Lambda, CORS/mapping template dễ lỗi

CI/CD GitLab → deploy Lambda tự động, tối ưu cold start & timeout

CRUD đơn giản → workflow FFF phức tạp

* **Serverless Automation Challenges (AWS Lambda)**

Tách rõ handler, business logic, error handling để tránh rối luồng xử lý

Cold start, timeout khi traffic cao

Logging phân tán qua CloudWatch → khó debug

IAM role tối thiểu cho Lambda, đảm bảo security

CI/CD GitLab → deploy Lambda tự động, zip code, versioning

Workflow phức tạp → CRUD mẫu không đủ

Kết nối với DynamoDB, S3, API Gateway cần mapping chính xác

Quản lý concurrency, throttling khi nhiều request đồng thời

* **AWS CDK Advanced Challenges**

Thiết kế hạ tầng IaC phức tạp, quản lý stack nhiều service (Lambda, RDS, DynamoDB, S3, API Gateway)

Dependency giữa stack → deploy đúng thứ tự, tránh lỗi cyclic dependency

Parameter, environment variable, context management phức tạp

Versioning, update stack → tránh downtime hoặc mất dữ liệu

Security: IAM role/policy phải đồng bộ với CDK
* **Application Protection Challenges (AWS WAF)**

Thiết kế rules chống SQL injection, XSS, bot traffic phù hợp FFF

Tuning rate-based rules để tránh false positive/block nhầm user hợp lệ

Kết hợp WAF với API Gateway, CloudFront, ALB → cấu hình phức tạp

Logging + monitoring qua CloudWatch → debug request bị block khó

Update rules khi FFF thay đổi API/endpoint