---
title: "Worklog Tuần 9"
date: 2025-11-03
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Mục tiêu tuần 9:

* Tìm hiểu sâu hơn về các dịch vụ aws 
* Tiếp tục làm project 

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Serverless Backend with Lambda, S3, and DynamoDB <br> -  Frontend Development for Serverless APIs | 03/11/2025   | 03/11/2025      |
| 3   | - Deployment Automation with AWS SAM <br> - User Authentication with Amazon Cognito  | 04/11/2025   | 04/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Custom Domains and SSL for Serverless Applications  <br> - Event Processing with SQS and SNS | 05/11/2025   | 05/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - CI/CD for Serverless Applications <br> - Monitoring Serverless Applications <br> - Building GraphQL APIs with AWS AppSync | 06/11/2025   | 06/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - Building Serverless APIs <br> - Serverless Chat Application              | 07/11/2025   | 07/11/2025      | <https://cloudjourney.awsstudygroup.com/> |


### Kết quả đạt được tuần 9:

####  **Frontend Development for Serverless APIs**

Xây dựng giao diện web (frontend) để gọi API được tạo bởi API Gateway + Lambda. 

Triển khai front-end: có thể host static site (HTML/CSS/JS) kết nối với backend serverless. 

Triển khai Lambda function để xử lý logic request từ API Gateway. 

Cấu hình API Gateway làm điểm cuối (endpoint) cho frontend: định nghĩa route, phương thức HTTP,… 

Kiểm thử API bằng Postman: đảm bảo API Gateway + Lambda chạy đúng trước khi frontend gọi. 

Kiểm thử frontend: web app gọi API Gateway, nhận kết quả từ Lambda và hiển thị. 

#### **Deployment Automation với AWS SAM**

Sử dụng AWS SAM (Serverless Application Model) để định nghĩa ứng dụng serverless qua file YAML, rồi SAM sẽ chuyển thành CloudFormation khi deploy. 

Tạo và triển khai front-end, Lambda function và API Gateway bằng SAM. 

Kiểm thử API bằng Postman và frontend sau khi deploy. 


#### **User Authentication với Amazon Cognito**

Tạo Cognito User Pool để quản lý đăng ký, đăng nhập, xác minh email, đổi mật khẩu, reset mật khẩu. 

Dùng Identity Pool nếu cần cấp AWS Credentials (tạm thời) cho user để truy cập các dịch vụ như S3, DynamoDB. 


Tạo API và Lambda: sau khi user xác thực qua Cognito, Lambda xử lý API request. 


Frontend: xây UI đăng nhập / đăng ký, gọi API Cognito để đăng nhập và lấy token; sau đó gửi token tới API Gateway / Lambda. 


#### **Custom Domains & SSL cho Ứng dụng Serverless** 

Dùng API Gateway để cấu hình tên miền tùy chỉnh (“custom domain”) thay vì hostname mặc định của API Gateway. 

Sử dụng Amazon Certificate Manager (ACM) để tạo hoặc import chứng chỉ SSL/TLS cho domain, đảm bảo HTTPS. 

Chọn loại custom domain: edge-optimized (sử dụng CloudFront) hoặc regional. 

Cấu hình Base Path Mapping để ánh xạ domain + đường dẫn (path) tới các stage của API Gateway. 


Tạo record DNS (Route 53 hoặc DNS khác) để trỏ domain tới CloudFront distribution hoặc endpoint do API Gateway cung cấp. 


SSL và bảo mật: bạn có thể chọn security policy TLS, ACM sẽ quản lý gia hạn chứng chỉ. 
AWS Docs

#### **Event Processing with SQS & SNS**

Khi người dùng đặt đơn hàng, API gửi message vào hàng đợi SQS để đảm bảo “queue” xử lý đơn hàng. 

Đồng thời, SNS được dùng để thông báo tới admin mỗi khi có đơn mới. 


Tạo các Lambda:

   * checkout_order để nhận đơn từ API và đẩy message vào SQS + publish SNS. 

   * handle_order để admin xử lý đơn: đọc từ SQS, ghi đơn vào DynamoDB. 

   * delete_order để admin xóa đơn: xóa message trong SQS. 

   * order_management cho admin xem danh sách đơn (dùng DynamoDB). 

Kiến trúc sử dụng SQS cho độ bền và khả năng xử lý bất đồng bộ, SNS để fan-out thông báo. 


#### **CI/CD cho Ứng dụng Serverless** 

Sử dụng AWS SAM Pipelines để tự động hóa quá trình build, package và deploy ứng dụng serverless. 


Khởi tạo pipeline CI/CD: sam pipeline init để tạo cấu hình pipeline cho AWS CodePipeline 

Pipeline gồm nhiều stage: Source (Git), Build (dùng SAM CLI), Deploy (CloudFormation/SAM). 


Sử dụng build container image do AWS SAM cung cấp để biên dịch serverless app, giúp giảm công sức tạo ảnh CI riêng. 


Pipeline theo mẫu best-practice AWS: hỗ trợ multi-account, multi-region. 


#### **Monitoring Serverless Applications**

Sử dụng CloudWatch Logs để debug Lambda: ghi log các invocation, lỗi,… 

Tạo custom metric trong CloudWatch để theo dõi chỉ số nghiệp vụ hoặc hiệu năng. 


Cấu hình CloudWatch Alarm dựa trên các metric để cảnh báo khi có tình trạng bất thường. 

Dùng AWS X-Ray để trace request: vẽ service map, xem đường đi của request và tìm bottleneck. 


#### **Building GraphQL APIs with AWS AppSync**

Sử dụng AWS AppSync để tạo API GraphQL serverless, kết hợp với các nguồn dữ liệu AWS như DynamoDB, Lambda hoặc Aurora Serverless. 

Định nghĩa schema GraphQL: type, query, mutation, subscription (nếu cần real-time). 
AWS Docs

Cấu hình resolvers:

Dùng VTL mapping template để chuyển đổi GraphQL request thành các thao tác truy vấn nguồn dữ liệu. 

Hoặc dùng Direct Lambda Resolver: Lambda xử lý logic GraphQL, đỡ phải viết VTL. 


Nếu dùng database quan hệ (Aurora Serverless), AppSync có thể kết nối qua Data API để thực thi lệnh SQL thông qua GraphQL mutation/query. 


Có thể quản lý truy cập API bằng các cách: AWS IAM, Cognito User Pools,… (authentication + authorization).

#### **Building Serverless APIs (Serverless with Lambda, API Gateway và SAM)**

Kiến trúc backend sử dụng Lambda, API Gateway, DynamoDB, S3, và Cognito. 

Frontend là một ứng dụng JavaScript (Vue.js) host trên S3 / Amplify. 


Sử dụng AWS SAM để định nghĩa tài nguyên serverless và deploy backend (Lambda + API Gateway + DynamoDB) 


Lambda đọc / ghi dữ liệu từ DynamoDB: ví dụ Lambda scan bảng DynamoDB để trả về danh sách “công viên” (rides, attractions). 

Triển khai API Gateway để frontend gọi API; Lambda xử lý logic request. 

Trong phần realtime: Lambda subscribe SNS topic, lưu thông tin vào DynamoDB, và forward payload tới IoT Core để frontend có thể nhận dữ liệu thời gian thực. 


#### **Serverless Chat Application**

Xây dựng ứng dụng chat thời gian thực serverless sử dụng API Gateway WebSocket, Lambda và DynamoDB. 

Khi client kết nối (“$connect”), Lambda lưu connection ID vào DynamoDB. 

Khi client ngắt kết nối (“$disconnect”), Lambda xóa connection ID khỏi DynamoDB. 

Khi client gửi tin nhắn (“sendmessage” route), Lambda đọc các connection ID từ DynamoDB và dùng API Gateway Management API để broadcast tin nhắn đến tất cả client đang kết nối. 



