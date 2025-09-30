---
title: "Worklog Tuần 3"
date: 2025-09-22
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---



### Mục tiêu tuần 3:

* Tiếp tục học và tìm hiểu thêm các chức năng của AWS.
* module 3 

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Scaling Applications with EC2 Auto Scaling <br> - Monitoring with Amazon CloudWatch                                                                                 | 22/09/2025   | 22/09/2025      |
| 3   | - Hybrid DNS Management with Amazon Route 53 <br> - Command Line Operations with AWS CLI
                                            | 23/09/2025   | 23/09/2025      |  |
| 4   | - NoSQL Database Essentials with Amazon DynamoDB <br> - In-Memory Caching with Amazon ElastiCache                   | 24/09/2025   | 24/09/2025      |  |
| 5   | - Networking on AWS Workshop <br> - viết Proposal
     | 25/09/2025   | 25/09/2025      |  |
| 6   | -     Content Delivery with Amazon CloudFront <br> - viết proposal                                      | 26/09/2025   | 26/09/2025      |  |



### Kết quả đạt được tuần 3:
* **Hiểu được kiến trúc triển khai ứng dụng trên AWS** với khả năng mở rộng Scaling Applications with EC2 Auto Scaling
  * Tạo Launch Template

  * Thiết lập Load Balancer (Target Group + Load Balancer)

  * Tạo Auto Scaling Group

  * Thử nghiệm các cách scaling: thủ công, theo lịch (scheduled), theo động (dynamic / predictive)

  * Đọc metric / dữ liệu từ predictive scaling

  * Cuối cùng là cleanup tài nguyên 

* **có thể làm được**
  * triển khai ứng dụng web theo kiến trúc có khả năng mở rộng.Từ ứng dụng ban đầu chạy trên một máy chủ, bạn có thể đưa vào kiến trúc cluster với load balancing và auto scaling.


* Thực hành EC2 cơ bản :
  *  Monitoring with Amazon CloudWatch
  * Hybrid DNS Management with Amazon Route 53
  * Command Line Operations with AWS CLI

* **Khởi tạo và quản lý EC2 instance:**
  * Tạo, cấu hình và khởi chạy EC2.
  * Kết nối SSH vào máy ảo.
  * Quản lý vòng đời (Start/Stop/Terminate).
* Networking & Security:
  * Tạo và chỉnh sửa Security Group để kiểm soát truy cập.
  * Sử dụng Elastic IP để gán IP tĩnh cho EC2.
* Triển khai ứng dụng:
  * Cài đặt phần mềm cơ bản trên EC2.
  * Deploy ứng dụng web đơn giản.
* Kỹ năng đạt được:
  * Làm chủ thao tác quản trị máy chủ ảo hóa trên AWS.
  * Biết cách kết nối và bảo mật hạ tầng ứng dụng.
*  Lưu trữ & Quản lý truy cập :
  * NoSQL Database Essentials with Amazon DynamoDB
  * In-Memory Caching with Amazon ElastiCache
  * Networking on AWS Workshop
* Amazon S3 (Simple Storage Service):
  * Tạo và quản lý bucket.
  * Upload/Download dữ liệu.
  * Cấu hình quyền truy cập (public/private).
  * Quản lý Versioning để theo dõi lịch sử file.
* IAM (Identity and Access Management):
  * Tạo User, Group, Role.
  * Gán Policy theo nguyên tắc “least privilege”.
  * Quản lý bảo mật khóa truy cập (Access Key, Secret Key).
* CloudWatch:
  * Theo dõi metrics của hệ thống.
  * Ghi nhận logs cho EC2 và các dịch vụ khác.
* Kỹ năng đạt được:
  * Xây dựng nền tảng bảo mật và phân quyền trong AWS.
  * Giám sát và tối ưu vận hành hệ thống.


*  Phân phối nội dung với CloudFront + S3 
*  Content Delivery with Amazon CloudFront
* Amazon CloudFront:
  * Dịch vụ CDN (Content Delivery Network) giúp phân phối nội dung nhanh hơn nhờ cache tại các edge location.
* Kết hợp S3 + CloudFront:
  * S3 bucket làm origin chứa nội dung tĩnh (HTML, CSS, JS, hình ảnh).
  * CloudFront phân phối và cache nội dung, giảm độ trễ khi người dùng truy cập.
* Thực hành:
  * Tạo S3 bucket và upload nội dung.
  * Tạo CloudFront distribution trỏ đến S3 origin.
  * Cấu hình cache policy, TTL, quyền truy cập.
  * Kiểm tra website phân phối qua CloudFront.
  * Xóa tài nguyên sau khi hoàn thành để tránh chi phí.
* Kỹ năng đạt được:
  * Xây dựng website tĩnh hiệu suất cao bằng S3 + CloudFront.
  * Quản lý caching và bảo mật nội dung phân phối.

