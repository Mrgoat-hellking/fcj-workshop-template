---
title: "Worklog Tuần 6"
date: 2025-10-13
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---



### Mục tiêu tuần 6:

* ôn tập midterm căng 
* vẫn tiếp tục học các dịch vụ của AWS
* Làm dự án Project : liên kết AI vào trang web
* tham giá sự kiện : WORKSHOP “DATA SCIENCE ON AWS” – MỞ KHÓA SỨC MẠNH DỮ LIỆU CÙNG ĐIỆN TOÁN ĐÁM MÂY
### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   |  - Network Monitoring with VPC Flow Logs <br> - Billing Console Delegation | 13/10/2025   | 13/10/2025      |
| 3   | - Managing Quotas with Service Quotas <br> - Cost and Usage Management | 14/10/2025   | 14/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Snapshot Automation with Amazon EBS Data Lifecycle Manager <br> - Anomaly Detection for EBS Backups| 15/10/2025   | 15/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Development Environment with AWS Toolkit for VS Code <br> - Identity Federation with AWS Single Sign-On <br> -  WORKSHOP “DATA SCIENCE ON AWS” – MỞ KHÓA SỨC MẠNH DỮ LIỆU CÙNG ĐIỆN TOÁN ĐÁM MÂY | 16/10/2025   | 16/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | -                                           | 17/10/2025   | 17/10/2025      | <https://cloudjourney.awsstudygroup.com/> |


### Kết quả đạt được tuần 6:

1. **hiểu các dịch vụ** 
  
  * Monitoring & Logging: theo dõi hoạt động mạng và hệ thống qua VPC Flow Logs và CloudWatch Logs.

  * Billing & Cost Management: quản lý tài chính, ủy quyền truy cập, giám sát chi phí.

  * Quota Management: giới hạn và yêu cầu tăng tài nguyên qua Service Quotas.

  * Automation & Lifecycle: tự động hóa sao lưu và lưu trữ snapshot với EBS Data Lifecycle Manager.

  * Development Tools: phát triển và triển khai ứng dụng trực tiếp trên VS Code với AWS Toolkit.

  * Identity & Access: quản lý truy cập tập trung qua AWS Single Sign-On (IAM Identity Center).

2.  **Thực hành và vận hành tài nguyên AWS**

* Giám sát mạng nội bộ (Network Monitoring):

  * Kích hoạt VPC Flow Logs để theo dõi lưu lượng mạng trong VPC.

  * Ghi log vào CloudWatch Logs, lọc và phân tích dữ liệu nhằm phát hiện bất thường trong kết nối EC2.

* Quản lý chi phí và hạn mức (Cost & Quota Management):

  * Xem, kiểm tra và yêu cầu tăng giới hạn tài nguyên (quota) thông qua Service Quotas.

  * Sử dụng IAM Policies để giới hạn quyền truy cập tài nguyên theo vùng (Region), loại instance và loại volume, giúp kiểm soát chi phí hiệu quả.

  * Kích hoạt quyền truy cập Billing cho người dùng IAM, theo dõi hóa đơn và báo cáo chi phí từ Billing Console.

* Tự động hóa backup (Automation):

  * Tạo EBS Snapshot và cấu hình Data Lifecycle Manager (DLM) để tự động sao lưu, lưu trữ archive và xóa snapshot cũ.

  * Thiết lập lịch snapshot nhiều cấp độ (daily/weekly) để tối ưu chi phí lưu trữ.

* Phát hiện bất thường (Anomaly Detection):

  * Áp dụng tính năng Anomaly Detection trên CloudWatch hoặc DLM để giám sát các backup bất thường, đảm bảo tính toàn vẹn dữ liệu.

* Môi trường phát triển (Development Environment):

  * Kết nối AWS từ VS Code để triển khai, giám sát và quản lý tài nguyên không cần mở AWS Console.

  * Debug và deploy ứng dụng serverless trực tiếp trong IDE.

* Liên kết danh tính tập trung (Identity Federation):

  * Cấu hình AWS IAM Identity Center (SSO) để cho phép người dùng truy cập nhiều tài khoản AWS qua cùng một portal.

  * Tổ chức tài khoản theo Organizational Units, gán quyền cho từng nhóm / dự án.

3. **Kết quả đạt được**

* Nắm vững cách:

  * Giám sát mạng, lưu lượng và nhật ký hệ thống bằng VPC Flow Logs.

  * Quản lý và tối ưu chi phí vận hành AWS.

  * Giới hạn và theo dõi tài nguyên bằng Service Quotas.

  * Tự động hóa backup bằng EBS Data Lifecycle Manager.

  * Thiết lập môi trường phát triển AWS ngay trong VS Code.

  * Quản lý người dùng và truy cập tập trung bằng IAM Identity Center.

* Kết nối và sử dụng song song giữa AWS Console, AWS CLI, và AWS Toolkit trong VS Code thành công.

4. Kết luận

* Qua các bài học, đã xây dựng được quy trình tổng thể quản lý hệ thống AWS bao gồm:

* Giám sát – Quản lý chi phí – Hạn mức – Tự động hóa – Danh tính – Phát triển ứng dụng.
Toàn bộ giúp vận hành hạ tầng AWS hiệu quả, giảm thiểu rủi ro, đảm bảo bảo mật và tối ưu tài nguyên.
