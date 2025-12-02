---
title: "Blog 3"
date: 2025-01-01
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

# Tối ưu hóa Dấu chân Mạng trong Ứng dụng Không Máy chủ
*bởi Chris McPeek vào ngày 21 tháng 3 năm 2025 trong Amazon API Gateway, Amazon Elastic Kubernetes Service, Amazon EventBridge, Amazon Simple Queue Service (SQS), Amazon Simple Storage Service (S3), AWS Lambda, Không Máy chủ*

*Tác giả: Anton Aleksandrov, Kiến trúc sư Giải pháp Chính, AWS Serverless và Daniel Abib, Kiến trúc sư Giải pháp Chuyên gia Cấp cao, AWS.*

Các nhà phát triển ứng dụng không máy chủ thường gặp phải các tình huống phải vận chuyển khối lượng dữ liệu lớn, đặc biệt là trong các ứng dụng đám mây hiện đại yêu cầu dữ liệu phong phú. Ví dụ bao gồm các nền tảng phân tích tạo báo cáo chi tiết, hệ thống thương mại điện tử quản lý danh mục sản phẩm lớn, ứng dụng chăm sóc sức khỏe truyền hồ sơ bệnh nhân hoặc dịch vụ tài chính tổng hợp dữ liệu giao dịch khổng lồ.

Tuy nhiên, nhiều dịch vụ không máy chủ có giới hạn kích thước tải trọng nghiêm ngặt — ví dụ:
AWS Lambda: 6 MB cho mỗi yêu cầu/phản hồi

Amazon SQS và Amazon EventBridge: 256 KB cho mỗi tin nhắn

Bài viết này giải thích cách sử dụng các kỹ thuật nén dữ liệu để giảm thiểu dung lượng mạng và truyền tải các tải trọng lớn hơn trong phạm vi các ràng buộc hiện có.

---

## Tổng quan
Khi các ứng dụng đám mây phát triển để đáp ứng các tính năng mới và Mục tiêu Mức Dịch vụ (SLO), kích thước tải trọng thường tăng lên. Cuối cùng, bạn có thể đạt đến các giới hạn do dịch vụ áp đặt, chẳng hạn như:
Lệnh gọi đồng bộ Lambda: 6 MB

API Gateway: 10 MB

SQS/EventBridge: 256 KB

Nếu tải trọng đạt đến hàng chục MB hoặc bao gồm các đối tượng nhị phân lớn, bạn có thể lưu trữ dữ liệu trên Amazon S3 và sử dụng URL được ký trước để tải lên/tải xuống trực tiếp.

Hình 1 – Kiến trúc mẫu để xử lý các tải trọng lớn.

Khi xử lý các tin nhắn lớn thông qua SQS hoặc EventBridge, bạn có thể lưu trữ nội dung tin nhắn trong S3 và chỉ gửi một tham chiếu. Sau đó, người dùng sẽ lấy toàn bộ tin nhắn trực tiếp từ S3.
Tuy nhiên, mặc dù các kỹ thuật này hoạt động hiệu quả, chúng lại tạo ra sự phức tạp về mặt kiến ​​trúc và yêu cầu sửa đổi các quy trình làm việc hiện có.
Ngoài ra, khi kích thước tải trọng tăng lên, chi phí truyền dữ liệu cũng tăng lên, đặc biệt là thông qua Cổng NAT, Điểm cuối VPC hoặc truyền dữ liệu liên vùng. Ví dụ: các hàm Lambda bên trong VPC có thể gọi các điểm cuối công cộng hoặc các dịch vụ bên ngoài.

Hình 2 – Ví dụ về việc sử dụng các thiết bị mạng ảo với các ứng dụng không máy chủ.

Cả Cổng NAT và Điểm cuối VPC đều được tính phí theo GB dữ liệu được xử lý, khiến việc nén dữ liệu trở thành một kỹ thuật tối ưu hóa có giá trị.

---
**Nén Dữ liệu là gì?
Nén dữ liệu làm giảm kích thước dữ liệu để cải thiện hiệu suất và hiệu quả chi phí cho việc lưu trữ và truyền tải. Các công cụ như gzip và zstd được sử dụng rộng rãi, được chuẩn hóa theo IANA và IETF RFC 9110.

Các trình duyệt hiện đại (Chrome, Firefox), các công cụ HTTP (curl, Postman) và các môi trường chạy (Node.js, Python) đều hỗ trợ nén dữ liệu gốc.

Khi máy khách gửi dữ liệu nén, họ chỉ định dữ liệu đó bằng tiêu đề Content-Type. Để nhận phản hồi nén, máy khách chỉ định các phương thức nén được hỗ trợ trong tiêu đề yêu cầu Accept-Encoding.

Hình 3 – Tiêu đề yêu cầu Accept-Encoding chỉ định các phương thức nén được hỗ trợ.

Sau đó, máy chủ nén phản hồi bằng một phương thức được hỗ trợ và bao gồm tiêu đề Content-Encoding để chỉ ra loại nén.

Hình 4 – Tiêu đề phản hồi Content-Encoding chỉ định phương thức nén.

Điều này làm giảm số byte được truyền qua mạng, cải thiện độ trễ. Các định dạng văn bản như JSON, XML, HTML và YAML nén tốt, trong khi các tệp nhị phân (PDF, JPEG) nén kém hiệu quả hơn.

---

## Nén dữ liệu với API Gateway
Amazon API Gateway cung cấp tính năng nén tích hợp thông qua cấu hình minimumCompressionSize, tự động nén các phản hồi có kích thước trên một mức nhất định (0 byte–10 MB).

Hình 5 – Xử lý nén dữ liệu trong API Gateway.

Cách thức hoạt động
API Gateway tự động giải nén các yêu cầu đến và nén các phản hồi đi.

Nén là hai chiều và hoạt động liền mạch với các dữ liệu JSON.

Máy khách chỉ định nén trong tiêu đề Content-Encoding; API Gateway giải nén trước khi chuyển tiếp đến các tích hợp.

API Gateway nén các phản hồi tích hợp khi máy khách bao gồm tiêu đề Accept-Encoding phù hợp.

Kết quả kiểm tra:

Tắt nén: Kích thước phản hồi = 1 MB, độ trễ = 660 ms

Bật nén: Kích thước phản hồi = 220 KB, độ trễ = 550 ms

→ Giảm 78% dung lượng mạng và phản hồi nhanh hơn 110 ms.

Để duy trì nén từ đầu đến cuối (để Lambda có thể xử lý giải nén), hãy cấu hình binaryMediaTypes để cho phép truyền qua nhị phân.

---

## Xử lý Dữ liệu Nén trong AWS Lambda
API AWS Lambda Invoke hỗ trợ các payload dạng văn bản (ví dụ: JSON) lên đến 6 MB (đồng bộ) hoặc 256 KB (không đồng bộ).

Tuy nhiên, bạn có thể nén các payload trong mã Lambda để vượt qua giới hạn và giảm chi phí truyền tải.

Hình 7 – Vận chuyển các payload đã nén trong các ứng dụng không có máy chủ.
Đoạn mã dưới đây cho thấy cách nén các payload phản hồi trong Node.js bằng cách sử dụng mô-đun zlib tích hợp:

Hình 8 – Mã mẫu triển khai nén payload phản hồi trong một hàm Lambda.
Chi tiết chính:
Dòng 1 nhập gzip từ mô-đun zlib.

Dòng 11 nén mộtd Dữ liệu được mã hóa theo chuẩn Base64 (vì Lambda mong đợi đầu ra dạng văn bản).

Dòng 13–21 tạo đối tượng phản hồi với isBase64Encoded=true và các tiêu đề phù hợp.

Kết quả:
Một JSON 20 MB chưa nén được trả về dưới dạng tải trọng nén 2,5 MB — giảm 80% dung lượng mạng.

Hình 9 – Ảnh chụp màn hình từ Postman cho thấy kích thước tải trọng ban đầu so với sau khi nén.

Phương pháp này cho phép truyền tải tải trọng lớn hơn nhiều lần so với giới hạn mặc định của Lambda.

---

## Sử dụng URL Hàm với Tải trọng Nén
Việc truyền tải tải trọng nén thông qua URL Hàm Lambda không yêu cầu cấu hình bổ sung.

Trình xử lý chỉ cần nén và mã hóa Base64 cho phản hồi.

Các yêu cầu đến được đánh dấu là nhị phân sẽ tự động được chuyển đến hàm của bạn dưới dạng chuỗi Base64.

Hình 10 – Mã mẫu triển khai giải nén tải trọng yêu cầu trong hàm Lambda.

Đánh đổi và Kết quả Kiểm tra
Nén ngốn nhiều CPU, làm tăng thời gian gọi và chi phí tiềm ẩn. Tuy nhiên, nó làm giảm việc truyền dữ liệu và độ trễ—thường mang lại hiệu quả tiết kiệm ròng.

Các thử nghiệm sử dụng Node.js trên kiến ​​trúc ARM với tải trọng JSON ngẫu nhiên cho thấy:
Nén một đối tượng JSON 1 MB đã tăng thêm ~124 ms thời gian tính toán cho bộ nhớ 1 GB.

10 triệu lần gọi → +16 đô la chi phí tính toán.

Nhưng việc giảm 70% kích thước tải trọng đã tiết kiệm ~300 đô la (NAT Gateway) hoặc ~70 đô la (VPC Endpoint).

Mức tiết kiệm phụ thuộc vào loại tải trọng và tỷ lệ nén. Đối với dữ liệu có độ nén thấp, kết quả có thể khác nhau.

---
## Ứng dụng Mẫu
Bạn có thể kiểm tra điều này trong tài khoản AWS của riêng mình bằng cách sử dụng dự án mẫu trong kho lưu trữ GitHub được cung cấp.

Mẫu này cung cấp hai hàm Lambda để chứng minh khả năng nén gzip cho các thao tác GET và POST thông qua URL Hàm và API Gateway.

Kết quả cho thấy giảm hơn 80% dung lượng mạng khi sử dụng tải trọng JSON.

Hình 11 – Ảnh chụp màn hình từ Postman hiển thị kích thước tải trọng ban đầu và sau khi nén.

---
## Kết luận
Nén dữ liệu cho phép truyền tải tải trọng lớn hơn và giảm đáng kể dung lượng mạng. Nó cải thiện độ trễ và giúp kiểm soát chi phí truyền tải, đặc biệt là đối với dữ liệu chạy qua Cổng NAT hoặc Điểm cuối VPC.
Tuy nhiên, nén làm tăng chi phí CPU — bạn nên cân bằng chi phí tính toán với mức tiết kiệm mạng.
Nén hiệu quả nhất đối với các tải trọng văn bản lớn, trong đó việc tăng nhỏ thời gian tính toán được bù đắp bằng việc truyền dữ liệu nhanh hơn và rẻ hơn.
Bằng cách áp dụng các kỹ thuật này trong AWS Lambda và API Gateway, bạn có thể làm cho các ứng dụng không máy chủ của mình hiệu quả hơn, có khả năng mở rộng hơn và được tối ưu hóa chi phí.s