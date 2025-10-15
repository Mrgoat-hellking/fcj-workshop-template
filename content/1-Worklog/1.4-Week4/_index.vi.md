---
title: "Worklog Tuần 4"
date: 2025-09-29
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---


### Mục tiêu tuần 4:

* tiếp tục tìm hiểu và học hỏi các dịch vụ của AWS 
* công tác tìm hiểu và tiến hành làm Project web bán hàng .
* Tham dự event AI-DLC(AI-Drien Development Lifecycle)
### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Edge Computing with CloudFront and Lambda@**Edge** <br> - Windows Workloads on AWS                                    | 29/09/2025   | 29/09/2025      |
| 3   | - Directory Services with AWS Managed Microsoft AD <br> - Building Highly Available Web Applications <br> - làm dự án 
                             | 30/09/2025   | 30/09/2025      |  |
| 4   | - VM Migration with AWS VM Import/Export <br> - làm dự án 
 | 1/10/2025   | 1/10/2025      |  |
| 5   | - Database Migration with AWS Database Migration Service (DMS) and Schema Conversion Tool (SCT) <br> - làm dự án 
                 | 2/10/2025   | 2/10/2025      |  |
| 6   | - tham dự event <br> - tổng kết tuần thứ 2 làm dự án Web bán hàng                                         | 3/10/2025   | 3/10/2025      |  |


### Kết quả đạt được tuần 4:

* 1. Hiểu được các dịch vụ hỗ trợ triển khai và di chuyển hệ thống trên AWS

* Nắm vững quy trình Import/Export máy ảo (VM) giữa môi trường on-premise và AWS.
* Hiểu rõ cách sử dụng AWS Directory Service để triển khai và quản lý Active Directory trên AWS.
* Biết cách triển khai WordPress trên kiến trúc AWS Cloud, gồm EC2, RDS, Auto Scaling, Load Balancer và CloudFront.
* Nắm được quy trình chuyển đổi và di chuyển cơ sở dữ liệu (schema + data) bằng AWS DMS & SCT.
*  Làm quen với Amazon WorkSpaces – dịch vụ Desktop ảo cho môi trường doanh nghiệp.

* 2. Có thể làm được

* Triển khai và mở rộng ứng dụng web từ một máy chủ sang kiến trúc nhiều tầng có khả năng auto scaling và load balancing.
* Kết hợp các dịch vụ AWS để tạo hệ thống hoàn chỉnh (EC2 + RDS + S3 + CloudFront).
* Thực hiện migration cơ sở dữ liệu giữa các môi trường khác nhau.
* Tạo và quản lý môi trường làm việc ảo hóa (WorkSpaces) cho người dùng nội bộ.
  
* 3. Thực hành và thao tác chính

* a. VM Import/Export:

  * Import máy ảo từ môi trường cục bộ lên AWS (qua S3 → AMI → EC2).
  * Export ngược lại VM từ AWS ra on-premise.
  * Quản lý quyền truy cập và ACL của S3 bucket.
  * Dọn dẹp tài nguyên sau khi thực hành.
  
* b. AWS Directory Service:

  * Tạo Managed Microsoft AD.
  * Kết nối EC2 Windows vào domain.
  * Quản lý user, group, và policy qua AD.
  * Cấu hình DNS và mạng nội bộ.

* c. Triển khai WordPress trên AWS Cloud:

  * Tạo VPC và subnet (public/private).
  * Cấu hình Security Group, Load Balancer, Auto Scaling Group.
  * Deploy WordPress trên EC2, kết nối với RDS.
  * Kết hợp CloudFront làm CDN để tăng tốc truy cập.
  * Backup và khôi phục dữ liệu.

* d. Database Migration (DMS & SCT):

  * Chuyển đổi schema bằng AWS Schema Conversion Tool.
  * Di chuyển dữ liệu bằng Database Migration Service.
  * Cấu hình replication instance, endpoint, task.
  * Theo dõi tiến trình qua CloudWatch Metrics.

* e. Amazon WorkSpaces:

  * Tạo và cấu hình môi trường desktop ảo.
  * Quản lý người dùng, cấp quyền truy cập.
  * Kết nối và kiểm thử hiệu suất hoạt động.

* 4. Kỹ năng đạt được

* Thực hành quy trình migration thực tế từ hệ thống on-premise lên AWS Cloud.
* Thành thạo các thao tác triển khai ứng dụng web có khả năng mở rộng.
* Hiểu sâu hơn về Load Balancing, Auto Scaling, Directory, Migration, WorkSpaces.
* Nắm rõ quy trình dọn dẹp tài nguyên và tối ưu chi phí sau khi triển khai.
* Biết thiết kế, triển khai và quản lý hệ thống đa dịch vụ trên AWS.



* **cuối cùng tuần này khá là căng cảm ơn đến anh  Thịnh Nguyễn đã giúp đỡ em**