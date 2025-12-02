---
title: "Worklog Tuần 10"
date: 2025-11-10
weight: 10s
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

#### **Elastic Beanstalk Workshop**

#### **Deploying Node.js Applications với Elastic Beanstalk**

Triển khai ứng dụng Node.js bằng Elastic Beanstalk để tự động hóa quá trình deploy, scaling và quản lý môi trường chạy ứng dụng.

Elastic Beanstalk hỗ trợ Node.js platform, tự thiết lập EC2, load balancer, auto scaling và môi trường runtime.

Triển khai ứng dụng: dùng EB CLI (eb init, eb create, eb deploy) để đóng gói mã nguồn, tạo environment và xuất bản app.

Quản lý môi trường: theo dõi logs, cấu hình scaling, cập nhật version, rollback khi cần.


#### **CI/CD with Elastic Beanstalk and CDK Pipelines**

Thiết lập CI/CD tự động cho ứng dụng bằng AWS CDK Pipelines và Elastic Beanstalk.

CDK định nghĩa hạ tầng: tạo Elastic Beanstalk Application, Environment và Pipeline dưới dạng IaC.

Pipeline: lấy source từ repository, build ứng dụng, tạo package và tự động deploy sang Elastic Beanstalk mỗi khi có thay đổi mã nguồn.

Triển khai: chạy cdk deploy lần đầu để tạo pipeline; từ đó về sau mọi thay đổi code sẽ tự động được build và cập nhật lên môi trường EB.

Hỗ trợ mở rộng: có thể thêm nhiều stage (dev/staging/prod), thêm bước test hoặc xác thực trước–sau deploy.

#### **WordPress on AWS**
#### **WordPress Architecture on AWS**
Triển khai WordPress trên AWS theo kiến trúc nhiều tầng để tăng hiệu năng và khả năng mở rộng.

Web tier: chạy WordPress trên các EC2 trong Auto Scaling Group, nhận traffic qua Application Load Balancer.

Database: dùng RDS/Aurora MySQL để lưu trữ dữ liệu WordPress an toàn, bền vững.

File sharing: sử dụng EFS để chia sẻ plugins, themes, uploads giữa nhiều EC2.

Static content: lưu hình ảnh trên S3 và phân phối qua CloudFront để giảm tải và tăng tốc.

Caching: tích hợp ElastiCache để tối ưu truy vấn và giảm áp lực lên database.

#### **Running WordPress on Amazon EC2** 

Dùng Amazon EC2 để khởi tạo một máy chủ (instance) — chạy web server + PHP + MySQL (hoặc MariaDB) để hosting WordPress. 

Đảm bảo cấu hình security group cho phép HTTP (và nếu cần HTTPS) để người dùng truy cập website từ Internet. 

Cài đặt Apache (httpd), PHP + extension MySQL; tải WordPress, giải nén vào thư mục web root, cấu hình file wp-config.php để kết nối database. 

Khởi động dịch vụ web + database; sau đó truy cập public DNS/IP để chạy script cài đặt WordPress, thiết lập site.

#### **Amazon ECS Workshop**
#### **Containerization với Amazon ECS và AWS Fargate**

Docker → đóng gói ứng dụng thành container (ảnh Docker). 

Amazon ECS: dịch vụ điều phối container — quản lý scheduling, scaling, deployment container. 

AWS Fargate: compute engine serverless cho container — chạy container mà không cần quản lý máy chủ / EC2 ở tầng dưới.

#### **CI/CD Pipeline cho ECS Applications**

Sử dụng container + registry: đóng gói ứng dụng thành Docker image, đẩy lên Amazon ECR. 
AWS Docs

Pipeline gồm các bước chính: Source → Build → Deploy. Source từ Git repo (ví dụ GitHub/CodeCommit), Build với AWS CodeBuild tạo Docker image, rồi push image lên ECR. 
AWS Builder Center

Sau build, pipeline deploy image mới tới ECS cluster: ECS sẽ pull image từ ECR và chạy lại service/container (thường là Fargate), đảm bảo deployment tự động và ít downtime.

#### **Machine Learning Essentials**
#### **Machine Learning với Amazon SageMaker***

Amazon SageMaker là dịch vụ ML toàn phần trên AWS, giúp bạn build, train, deploy mô hình ML/AI mà không cần tự quản lý hạ tầng. 

Bạn có thể dùng môi trường tích hợp (IDE) SageMaker Studio để phát triển, xử lý dữ liệu, thử nghiệm, và deploy mô hình. 


SageMaker hỗ trợ toàn bộ workflow ML — từ chuẩn bị dữ liệu, feature‑engineering, huấn luyện mô hình, tuning hyper‑parameters, đến deploy mô hình vào production.

#### **SageMaker Immersion Day**

SageMaker Immersion Day là workshop thực hành dành cho ML engineer / data scientist / developer muốn học end-to-end quy trình ML với SageMaker: từ xử lý dữ liệu → feature-engineering → train → deploy model.

Các bước chính trong workshop: mở môi trường với SageMaker Studio, chuẩn bị dataset (upload lên S3), feature-engineering, train & tune model, sau đó deploy model & thử inference.

Workshop cung cấp cả thuật toán built-in và khả năng sử dụng custom model (bring-your-own-model), cho phép bạn thử cả ML cơ bản lẫn ML tuỳ chỉnh.

#### **Data Lake**
#### **Data Lake Fundamentals on AWS**

Data Lake là kho trung tâm để lưu trữ mọi dữ liệu — cấu trúc, bán cấu trúc, phi cấu trúc — ở bất kỳ quy mô nào, giữ dữ liệu “thô” mà không cần định dạng trước. 

AWS sử dụng Amazon S3 làm nền tảng lưu trữ chính cho Data Lake — đơn giản, linh hoạt, dễ mở rộng và tích hợp tốt với các dịch vụ phân tích khác. 

Để quản lý metadata và schema, dùng AWS Glue (Glue Data Catalog, crawler) để “catalogue” dữ liệu — giúp dễ tìm, phân tích và chia sẻ dữ liệu giữa nhóm. 


#### **Building a Data Lake với dữ liệu của bạn trên AWS**

Lưu trữ dữ liệu raw — upload dữ liệu (CSV, JSON, logs, v.v.) lên Amazon S3; S3 đóng vai trò kho trung tâm cho data lake. 

Dùng AWS Glue để crawl dữ liệu: tự động phát hiện schema, table; tạo metadata/catalog để dễ quản lý & truy vấn. 

Xây pipeline ETL/ELT serverless: Glue xử lý ingest & transform dữ liệu (từ raw → cleaned/structured) trước khi lưu lại ở S3 (có thể theo tầng raw → refined → aggregated).