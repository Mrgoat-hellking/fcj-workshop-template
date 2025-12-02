---
title: "Worklog Tuần 7"
date: 2025-10-20
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---


### Mục tiêu tuần 7:

* Tiếp tục học tập và làm quen với các dịch vụ của AWS
* tuần này không có gì mới ngoài ôn tập để 31/10 làm midterm
* Học thêm trên Udemy - clf-C02

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                  | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Security Compliance with AWS Security Hub  <br> - Private Access to S3 with VPC Endpoints <br> -  Application Protection with AWS WAF | 20/10/2025   | 20/10/2025      |
| 3   | - Encryption with AWS Key Management Service (KMS) <br> - Data Protection with Amazon Macie <br> -  Credentials Management with AWS Secrets Manager | 21/10/2025   | 21/10/2025      |  |
| 4   | - Security Governance with AWS Firewall Manager <br> - Threat Detection with AWS GuardDuty <br> - Systems Patching with EC2 Image Builder  | 22/10/2025   | 22/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Cross-Domain Authentication with Amazon Cognito <br> - S3 Security Best Practices <br> - Data Protection with AWS Backup  | 23/10/2025   | 23/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - Network Integration with VPC Peering <br> - Centralized Network Management with AWS Transit Gateway <br> - Messaging Systems with SQS and SNS  | 24/10/2025   | 24/10/2025      | <https://cloudjourney.awsstudygroup.com/> |


### Kết quả đạt được tuần 7:

*  hiểu được **AWS Security Hub** trong việc đảm bảo tuân thủ an ninh và bảo mật trên môi trường đám mây.
* chức năng :
   + thu thập , chuẩn hóa theo dạng AWS Security Finding Format (ASFF).
   + Cung cấp điểm số bảo mật (security score) thể hiện tỷ lệ kiểm soát đạt yêu cầu so với tổng kiểm soát đang hoạt động.
* Kiểm soát và đánh giá:
   + Mỗi tiêu chuẩn gồm nhiều kiểm soát (controls) thực hiện quét và đánh giá tài nguyên AWS.
   + Kết quả được phân loại thành Passed, Failed, Unknown hoặc No data, giúp theo dõi trạng thái tuân thủ.

* **Private Access to S3 with VPC Endpoints**
* VPC Endpoint cho phép kết nối trực tiếp từ VPC tới dịch vụ AWS mà không cần địa chỉ IP công cộng hoặc Internet Gateway.
* Gateway Endpoint: dùng cho S3 và DynamoDB, định tuyến thông qua bảng định tuyến (route table) nội bộ.
* Interface Endpoint: dùng PrivateLink, kết nối thông qua ENI (Elastic Network Interface) với DNS nội bộ.
* Đã tạo Gateway Endpoint cho S3 trong AWS Console và cấu hình route table cho subnet nội bộ.
* Kiểm tra kết nối bằng cách truy cập S3 qua CLI trong VPC, xác nhận không qua Internet.

* **Application Protection with AWS WAF**
* AWS WAF là dịch vụ tường lửa ứng dụng web giúp giám sát và kiểm soát lưu lượng HTTP(S) đến các ứng dụng được triển khai trên CloudFront, ALB hoặc API Gateway.
* Chức năng chính:
   + Cho phép hoặc chặn yêu cầu dựa trên điều kiện như IP, chuỗi truy vấn, hoặc mẫu tấn công.
   + Hỗ trợ Managed Rule Groups từ AWS và đối tác, cùng các custom rules. 
* Có thể tích hợp: kết hợp cùng AWS Shield, CloudFront, hoặc ALB để bảo vệ toàn diện.
* Tạo được Web ACL trong AWS WAF và gắn với CloudFront Distribution

*  **Encryption with AWS Key Management Service (KMS)**
*  AWS KMS là dịch vụ quản lý khóa tập trung cho phép tạo, lưu trữ và kiểm soát quyền truy cập khóa mã hóa.
*  Chức năng chính là hỗ trợ mã hóa đối xứng, bất đối xứng, và quản lý quyền truy cập thông qua IAM policy và key policy.
*  Có 2 loại khóa chính : 1.AWS Managed Keys (do AWS tạo và quản lý) 2.Customer Managed Keys (do người dùng tạo, có thể gán chính sách truy cập).
*  KMS được tích hợp sẵn với các dịch vụ như S3, EBS, RDS, Lambda, CloudTrail.
*  Đã tạo Customer Managed Key (CMK) trong KMS và gán mô tả, quyền sử dụng.

* **Data Protection with Amazon Macie**
* Amazon Macie là dịch vụ bảo mật do AWS cung cấp, giúp phát hiện, phân loại và bảo vệ dữ liệu nhạy cảm được lưu trữ trong Amazon S3.
   + tự động tạo danh mục (inventory),theo dõi quyền truy cập (public access, cross-account) và cảnh báo nếu phát hiện rủi ro rò rỉ dữ liệu
* Dịch vụ có hai chế độ chính:
   + Automated Sensitive Data Discovery – tự động quét dữ liệu nhạy cảm định kỳ.
   + Custom Discovery Jobs – người dùng tự chỉ định phạm vi và tiêu chí quét cụ thể.
* Toàn bộ dữ liệu và kết quả phân tích đều được mã hóa bằng AWS KMS, đảm bảo tính an toàn khi lưu trữ và truyền tải.
* Đã tạo được Amazon Macie để tự động phát hiện và bảo vệ dữ liệu nhạy cảm trong Amazon S3.  


* **Credentials Management with AWS Secrets Manager**
* AWS Secrets Manager là dịch vụ quản lý thông tin nhạy cảm như mật khẩu, khóa API, chứng chỉ, hoặc token dùng trong ứng dụng và dịch vụ AWS.
* Dịch vụ có thể tích hợp với các hệ thống như RDS, Redshift, DocumentDB, giúp tự động thay đổi mật khẩu cơ sở dữ liệu định kỳ mà không ảnh hưởng đến kết nối.
* Dịch vụ hỗ trợ mã hóa dữ liệu bằng AWS KMS và cho phép xoay vòng (rotation) mật khẩu tự động nhờ tích hợp với AWS Lambda.
* Đã tạo được AWS Secrets Manager để quản lý và bảo vệ thông tin xác thực một cách an toàn, tự động.

* **Security Governance with AWS Firewall Manager**
* AWS Firewall Manager là dịch vụ quản lý chính sách bảo mật tập trung cho toàn bộ tài khoản trong AWS Organizations.
* Dịch vụ này duy trì nhất quán các chính sách tường lửa trên nhiều tài khoản và tài nguyên (VPC, CloudFront, ALB, Route 53).
* Firewall Manager thường tích hợp với AWS WAF, AWS Shield Advanced, Security Groups, và VPC để có thể tự động triển khai quy tắc bảo vệ theo chuẩn định sẵn.
* Đặc biệt tích hợp chặt chẽ với Security Hub để hiển thị các cảnh báo và tình trạng bảo mật tập trung.
* Firewall Manager giúp doanh nghiệp chuẩn hóa kiểm soát bảo mật, tiết kiệm thời gian vận hành và giảm rủi ro do con người.
* Đã tạo được Firewall Manager để quản lý và áp dụng chính sách tường lửa tập trung trên nhiều tài khoản AWS

* **Threat Detection with AWS GuardDuty**
* Amazon GuardDuty là dịch vụ phát hiện mối đe dọa tự động sử dụng machine learning, phân tích hành vi (behavioral analytics) và nguồn tình báo bảo mật (threat intelligence).
* Dịch vụ giám sát log từ CloudTrail, VPC Flow Logs, DNS logs, và các nguồn dữ liệu khác để phát hiện hành vi bất thường hoặc xâm nhập tiềm ẩn.
* GuardDuty có thể nhận diện hoạt động dò quét, truy cập trái phép, key bị rò rỉ, hoặc kết nối đến domain độc hại.
* GuardDuty tích hợp với Security Hub, EventBridge, Lambda để tự động phản ứng như cô lập instance hoặc khóa tài khoản nghi ngờ.
* GuardDuty giúp tăng cường khả năng phòng thủ chủ động (threat hunting) và hỗ trợ bằng chứng cho các quy trình điều tra sự cố.
* Đã tạo được GuardDuty để phát hiện và cảnh báo mối đe dọa bảo mật tự động trong tài khoản AWS.
  
* **Systems Patching with EC2 Image Builder**
* EC2 Image Builder là công cụ tự động tạo, kiểm thử và cập nhật AMI (Amazon Machine Image) giúp đảm bảo máy chủ luôn được vá lỗi và chuẩn hóa.
* Dịch vụ cho phép định nghĩa pipeline gồm các giai đoạn: source → build → test → distribute.
* Hỗ trợ custom components để cài đặt phần mềm, cấu hình hệ điều hành và cập nhật bản vá bảo mật.
* EC2 Image Builder tích hợp với Systems Manager (SSM), CloudWatch, và IAM để tự động hóa quy trình build – deploy AMI định kỳ.
* Đã tạo được EC2 Image Builder để tự động xây dựng và cập nhật AMI bảo mật, có bản vá mới nhất.

* **Cross-Domain Authentication with Amazon Cognito**
* Amazon Cognito là dịch vụ xác thực (authentication) và quản lý người dùng (user management) được quản lý hoàn toàn bởi AWS.

* Cung cấp hai thành phần chính:
   + User Pools – dùng để xác thực và quản lý người dùng.
   + Identity Pools – cấp quyền truy cập tạm thời (federated access) đến các tài nguyên AWS.
* Cognito tự động xử lý sign-up, sign-in, MFA, xác thực email, và đặt lại mật khẩu
* Có thể tích hợp Amazon API Gateway, AppSync, hoặc các ứng dụng di động để tạo luồng xác thực liền mạch.
* Đã tạo được Amazon Cognito để xác thực người dùng và liên kết đăng nhập giữa nhiều miền ứng dụng.

* **S3 Security Best Practices**
* AWS S3 lưu trữ dữ liệu có tính mở rộng cao, nên cần tuân thủ các best practice bảo mật để tránh rò rỉ dữ liệu.

* Nguyên tắc cốt lõi gồm:
   + Private by default: mọi bucket nên mặc định không công khai.
   + Block Public Access: bật toàn bộ tùy chọn chặn truy cập công khai.
   + Encryption: bật SSE-S3 hoặc SSE-KMS cho mã hóa dữ liệu.
   + Access Control: sử dụng IAM policies, bucket policies, và ACLs hợp lý.
* Kết hợp Macie, GuardDuty và Security Hub để tăng khả năng phát hiện vi phạm quyền truy cập dữ liệu.
* Đã tạo được cấu hình S3 tuân thủ best practice bảo mật và mã hóa dữ liệu an toàn.

* **Data Protection with AWS Backup**
* AWS Backup là dịch vụ tự động sao lưu tập trung (centralized backup) cho nhiều tài nguyên AWS như EC2, EBS, RDS, DynamoDB, FSx, EFS, và S3.
* Cho phép định nghĩa Backup Plan, Backup Vault, và Lifecycle Policies để kiểm soát thời gian lưu trữ, xóa hoặc di chuyển bản sao lưu.
* Mọi dữ liệu sao lưu được mã hóa bằng KMS và có thể phục hồi ở cấp tài nguyên hoặc toàn hệ thống.
* Dịch vụ hỗ trợ cross-region và cross-account backup, giúp doanh nghiệp đáp ứng yêu cầu khôi phục sau thảm họa (DR).
* Backup Audit Manager giúp giám sát, báo cáo và đảm bảo tuân thủ các chính sách bảo vệ dữ liệu.
* Đã tạo được AWS Backup để tự động sao lưu và khôi phục dữ liệu trên các dịch vụ AWS.

* **Network Integration with VPC Peering**
* giữa hai Virtual Private Cloud (VPC) để chúng có thể giao tiếp qua địa chỉ IP riêng mà không cần sử dụng internet công cộng hoặc VPN.

* Kết nối này là phi trung gian (point-to-point), không phụ thuộc vào cổng hay thiết bị trung gian, giúp giảm độ trễ và tăng tính bảo mật.

* Các VPC có thể ở cùng hoặc khác vùng (inter-region peering), miễn là không có xung đột địa chỉ IP.

* Sau khi thiết lập peering, lưu lượng có thể được định tuyến qua route tables, cho phép EC2, RDS, Lambda và các dịch vụ nội bộ giao tiếp an toàn.

* VPC Peering không hỗ trợ transitive routing, nghĩa là VPC A kết nối với B và B với C thì A không thể nói chuyện trực tiếp với C.
* đã tạo được VPC Peering để kết nối an toàn giữa hai VPC bằng địa chỉ IP nội bộ.

* **Centralized Network Management with AWS Transit Gateway**
* AWS Transit Gateway (TGW) là dịch vụ kết nối mạng trung tâm (hub) cho phép liên kết nhiều VPC, VPN, và Direct Connect thông qua một điểm quản lý tập trung.

* TGW hoạt động như bộ định tuyến (router) ở cấp vùng (regional), giúp giảm số lượng kết nối chéo phức tạp (VPC Peering mesh).

* Mỗi VPC chỉ cần gắn một Transit Gateway attachment, và tất cả lưu lượng giữa các mạng sẽ đi qua TGW, hỗ trợ transitive routing (A ↔ B ↔ C).

* Quản trị viên có thể kiểm soát luồng lưu lượng thông qua route tables riêng cho mỗi attachment, đảm bảo cách ly hoặc chia sẻ tài nguyên theo yêu cầu.

* TGW hỗ trợ multicast, cross-account, cross-region peering, và bandwidth cao (lên đến hàng chục Gbps).

* Dịch vụ này tích hợp với AWS Network Manager để giám sát toàn bộ cấu trúc liên kết, giúp phát hiện sự cố hoặc kiểm tra đường truyền.
* Tạo được AWS Transit Gateway để kết nối và quản lý tập trung nhiều VPC và mạng on-premises.


* **Messaging Systems with SQS and SNS**
* Amazon Simple Queue Service (SQS) và Amazon Simple Notification Service (SNS) là hai dịch vụ nhắn tin phi đồng bộ (asynchronous messaging), giúp tách rời các thành phần trong hệ thống phân tán.

* SQS: dịch vụ hàng đợi tin nhắn, cho phép lưu trữ tạm thời và xử lý tuần tự các message giữa các ứng dụng.

* Có hai loại:

   + Standard Queue: hiệu năng cao, đảm bảo giao hàng ít nhất một lần.

   + FIFO Queue: đảm bảo đúng thứ tự và không trùng lặp tin nhắn.

* Hỗ trợ cơ chế visibility timeout, dead-letter queue, và message retention để đảm bảo xử lý ổn định.

* SNS: dịch vụ xuất bản/thông báo (pub/sub), giúp phát tán thông điệp đến nhiều subscriber cùng lúc (email, SMS, Lambda, SQS, HTTP endpoint).

* Hai dịch vụ có thể kết hợp: SNS gửi thông báo đến nhiều SQS queues để fan-out dữ liệu đến các hệ thống khác nhau.

* SQS và SNS giúp giảm tải, tăng khả năng mở rộng, và tránh tình trạng nghẽn luồng (bottleneck) trong kiến trúc microservices.

* Dịch vụ được quản lý hoàn toàn, không yêu cầu máy chủ, tự động mở rộng và đảm bảo độ tin cậy cao (durability > 99.999999%).
* Đã tạo được hệ thống nhắn tin phi đồng bộ bằng SQS và SNS để truyền thông tin giữa các dịch vụ AWS.


* **kết Luận**
* tất cả các dịch vụ của Security AWS đều được liên kết với nhau để giúp có khả năng phòng thủ mạnh hơn , nhưng nó cũng phức tạp và cực kì nhiều kiến thức cần được trải nghiệm qua.
* về phần học thêm cho Midterm thì đã làm hết 6 phần và học lại liên tục.