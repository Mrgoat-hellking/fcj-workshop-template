---
title: "Blog 1"
date: 2025-09-09
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Giúp khách hàng triển khai các AI agent sẵn sàng cho sản xuất ở quy mô lớn

  *by Swami Sivasubramanian ngày 16/07/2025 trong Amazon Bedrock, Amazon Connect, Amazon Nova, Amazon Q, Amazon Simple Storage Service (S3), Announcements, AWS Inferentia, AWS Trainium, AWS Transform, Featured, Thought Leadership* 

AI agent được dự đoán sẽ có tác động mang tính cách mạng như chính Internet, cho phép tự động hóa, giải quyết các vấn đề phức tạp và thúc đẩy đổi mới. Tuy nhiên, việc đưa AI agent vào vận hành ở quy mô lớn không chỉ dừng lại ở huấn luyện mô hình lớn—mà còn đòi hỏi một kiến trúc đảm **bảo bảo mật, độ tin cậy, khả năng mở rộng và tính linh hoạt**.

AWS giải quyết thách thức này bằng kiến trúc dựa trên **microservices**: mỗi năng lực của agent (bộ nhớ, định danh, giám sát, truy cập công cụ, tùy biến) được đóng gói thành một dịch vụ nhỏ, độc lập và kết nối lỏng lẻo thông qua một hub trung tâm. Cách phân tách này giúp tăng tính linh hoạt, dễ dàng thêm hoặc thay thế thành phần, đồng thời cho phép tổ chức tập trung vào giá trị kinh doanh thay vì phải xây dựng hạ tầng từ đầu.

---

## Hướng dẫn kiến trúc

So với cách tiếp cận nguyên khối (monolithic), AWS tách nhỏ chức năng của agent thành nhiều microservices:

**AgentCore**: môi trường serverless để điều phối các agent.

**Dịch vụ chức năng**: bộ nhớ, định danh, giám sát, gateway, bộ thông dịch mã.

**Dịch vụ tùy biến mô hình**: microservice fine-tuning Amazon Nova.

Thiết kế này cho phép khách hàng tự do chọn mô hình, tích hợp dữ liệu hiện có và kết nối liền mạch với các framework mã nguồn mở.

## Lựa chọn công nghệ và phạm vi giao tiếp
|Phạm vi giao tiếp	                     |  Công nghệ                                                           |
|----------------------------------------|----------------------------------------------------------------------|          
|Bên trong một microservice 	           | AWS Lambda, Step Functions                                           |
|Giữa các microservice trong một agent	 |Amazon SNS, AWS CloudFormation cross-stack references                 |
|Giữa các dịch vụ/agent	                 |Amazon EventBridge, API Gateway, AWS Cloud Map                        |

## Hub Pub/Sub

Mô hình **pub/sub hub** là trung tâm trong cách tiếp cận của AWS:

- Mỗi microservice chỉ giao tiếp với hub, không liên kết trực tiếp với các microservice khác.

- Kết quả, lỗi hoặc đầu ra trung gian được đẩy vào hub để xử lý tiếp.

- Lợi ích: giảm gọi đồng bộ, dễ mở rộng, giữ cho các thành phần tách rời.

- Hạn chế: cần giám sát và phối hợp để tránh tin nhắn sai hướng hoặc trùng lặp.

---

## Microservice lõi

Nền tảng của giải pháp, cung cấp lớp dữ liệu và giao tiếp:

- **Amazon** S3 cho dữ liệu và artifacts.

- **Amazon DynamoDB** cho metadata và catalog.

- **AWS Lambda** đảm bảo ghi dữ liệu và logic runtime nhất quán.

- **Amazon SNS** Topic làm hub trung tâm.

Điều này đảm bảo mọi thao tác ghi vào data lake và catalog đều được kiểm soát và nhất quán.

---

## Microservice cửa ngõ (Front Door)

Điểm truy cập chính cho các yêu cầu bên ngoài:

- Amazon API Gateway cung cấp giao diện REST.

- Amazon Cognito (OIDC) quản lý xác thực và phân quyền.

- Cơ chế loại bỏ trùng lặp được xây dựng với DynamoDB, khắc phục giới hạn của SNS FIFO và cho phép phát hiện trùng lặp chủ động.

---

## Microservices xử lý

Agent thường cần các công cụ chuyên biệt như duyệt web, thực thi mã, hoặc tìm kiếm. Những công cụ này được triển khai dưới dạng microservices:

- Lambda triggers đăng ký với hub và lọc thông điệp.

- Step Functions điều phối các pipeline (ví dụ: tiền xử lý, gọi mô hình).

- Lambda functions thực thi logic phân tích hoặc chuyển đổi cụ thể.

- Kết quả hoặc lỗi được trả về hub cho các dịch vụ kế tiếp.

---

## Microservice tùy biến mô hình (Nova)

Fine-tuning được xử lý như một microservice riêng biệt:

- Hỗ trợ cả fine-tuning toàn bộ và kỹ thuật tham số hiệu quả.

- Phương pháp gồm SFT, DPO, RLHF, CPT và Distillation.

- Chạy độc lập, nên việc cập nhật hoặc huấn luyện lại không ảnh hưởng đến runtime tổng thể.

## Các tính năng mới trong giải pháp
1. Amazon Bedrock AgentCore

- Môi trường serverless cho agent.

- Cách ly phiên làm việc và khả năng quan sát.

- Tích hợp với các framework mã nguồn mở.

2. Hỗ trợ công cụ mở rộng

- Microservices cho bộ nhớ, định danh, gateway, trình duyệt và bộ thông dịch.

- Mỗi thành phần có thể thay thế hoặc mở rộng dễ dàng.

3. Sự chấp nhận từ khách hàng

- Các doanh nghiệp như Itaú Unibanco, Innovaccer, Boomi, Box, và Epsilon đã áp dụng kiến trúc này để triển khai AI agent quy mô lớn, sẵn sàng cho sản xuất.


```yaml
Outputs:
  AgentCoreTopic:
    Value: !Ref AgentCoreTopic
    Export:
      Name: !Sub ${AWS::StackName}-AgentCoreTopic

  AgentMemoryTable:
    Value: !Ref AgentMemoryTable
    Export:
      Name: !Sub ${AWS::StackName}-AgentMemoryTable

  NovaCustomizationJob:
    Value: !Ref NovaCustomizationJob
    Export:
      Name: !Sub ${AWS::StackName}-NovaCustomizationJob
