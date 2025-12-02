---
title: "Worklog Tuần 11"
date: 2025-11-17
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---


### Mục tiêu tuần 11:

* tiến vào giai đoạn nước rút của Project
* ôn lại các dịch vụ sẽ dùng

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Hybrid DNS Management with Amazon Route53                                           | 11/08/2025   | 11/08/2025      |
| 3   | - Building Serverless CRUD with Lambda and DynamoDB                      | 12/08/2025   | 12/08/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Serverless Storage and Auth with AWS Amplify | 13/08/2025   | 13/08/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Frontend Integration with API Gateway       | 14/08/2025   | 15/08/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - Network Integration with VPC Peering                                  | 15/08/2025   | 15/08/2025      | <https://cloudjourney.awsstudygroup.com/> |


### Kết quả đạt được tuần 11:

#### Đã học qua và hiểu những bài trên và đây là những khó khi áp dụng vào project.
* 1. **Lambda + DynamoDB (Serverless CRUD)**

Thiết kế API Gateway đồng bộ với request/response của FFF.

Tách rõ handler, business logic, error handling trong Lambda để tránh rối luồng xử lý.

Chuyển từ RDS sang DynamoDB làm thay đổi mô hình dữ liệu (PK/SK, GSI).

Dữ liệu FFF có nhiều quan hệ → khó tối ưu DynamoDB nếu không thiết kế One-Table.

Logging + CloudWatch phân tán → debug phức tạp.

Cấu hình IAM role tối thiểu quyền cho Lambda truy cập DynamoDB.

CORS, mapping template, stage variables của API Gateway dễ gây lỗi.

CI/CD từ GitLab → Lambda cần pipeline tự động (zip code, deploy).

Tối ưu cold start, timeout khi traffic tăng cao.

Logic CRUD mẫu quá đơn giản → FFF cần workflow nhiều bước.

2. **Amplify Storage & Auth**

Amplify dùng Cognito + S3, cần đồng bộ với backend FFF (roles, session).

Mapping quyền Cognito (User Pool / Identity Pool) với RBAC FFF phức tạp.

Đồng bộ đăng nhập Amplify với API Gateway IAM auth hoặc JWT validator cần cấu hình thủ công.

Upload file qua Amplify Storage → policy S3, quyền read/write theo user type.

Tải file lớn (ảnh/video) cần presigned URL + giới hạn bảo mật.

Amplify CLI tạo nhiều resource auto → dễ gây rối CloudFormation stack.

CI/CD với Amplify Hosting/Backend nếu kết hợp GitLab phức tạp.

3. **Frontend Integration với API Gateway**

Phải thiết kế rõ endpoint URL, stage, mapping để frontend kết nối Lambda/DynamoDB đúng cách.

Cấu hình CORS, headers, content-type để frontend fetch không bị lỗi.

Xử lý authentication/authorization trên frontend: Cognito JWT, token refresh.

Thống nhất error handling: API trả lỗi, frontend hiển thị đúng thông báo.

Quản lý versioning, stage environment: dev/staging/prod → tránh frontend gọi nhầm endpoint.

Tối ưu performance: nhiều request đồng thời → tránh API Gateway throttling.

4. **Network Integration với VPC Peering**

Thiết lập VPC Peering giữa các VPC của FFF và các service Lambda/DynamoDB cần truy cập.

Cấu hình route table, security group, NACL để traffic Lambda/API Gateway đi đúng VPC.

Kiểm soát DNS resolution giữa các VPC → tránh conflict với private hosted zones.

Xử lý latency và throughput khi peering nhiều VPC → ảnh hưởng performance.

Kiểm soát bảo mật: chỉ cho phép IP/port cần thiết, tránh lộ dữ liệu nội bộ.

Khi mở rộng multi-account → peering phức tạp, khó scale nếu có nhiều VPC.