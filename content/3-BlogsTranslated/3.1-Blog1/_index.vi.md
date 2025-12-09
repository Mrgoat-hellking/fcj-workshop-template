---
title: "Blog 1"
date: 2025-09-09
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Nomalab tự động hóa phát hiện ngắt quảng cáo trong quy trình làm việc của phương tiện truyền thông với AWS

*bởi Thomas Buatois, Iryna Oliinykova và Ken Shek vào ngày 04 tháng 4 năm 2025 trong Amazon Bedrock, Amazon Machine Learning, Amazon OpenSearch Service, Amazon Rekognition, Amazon Transcribe, Analytics, Artificial Intelligence, AWS Elemental MediaConvert, Data Science & Analytics for Media, Generative AI, Media & Entertainment, Media Services, Media Chain & Archive, Monetization*

**Ngành Truyền thông và Giải trí (M&E)** đang trải qua một sự chuyển đổi chưa từng có, với khối lượng và độ phức tạp của nội dung tiếp tục tăng trưởng nhanh chóng.
Để duy trì tính cạnh tranh, các đài truyền hình và nhà xuất bản phải tìm ra các giải pháp sáng tạo để tối ưu hóa quy trình làm việc của họ từ khâu tiếp nhận đến phân phối.

Nhận thức được thách thức này, Nomalab, một nền tảng quản lý phương tiện truyền thông dựa trên đám mây hàng đầu có sẵn trên AWS Marketplace, đã tận dụng sức mạnh của AI và Generative AI thông qua Hướng dẫn Media2Cloud trên AWS (Media2Cloud).

Media2Cloud là một nền tảng mã nguồn mở, không máy chủ, minh họa cách thức áp dụng các công nghệ đám mây và AI mới nhất có thể thúc đẩy hiệu quả và định vị các tổ chức truyền thông hướng đến thành công lâu dài.
Bài viết này khám phá cách Nomalab sử dụng sáng tạo các dịch vụ AWS và AI tổng hợp đang chuyển đổi quy trình làm việc truyền thông và thiết lập một tiêu chuẩn mới về hiệu quả xử lý nội dung.

---

## Trường hợp sử dụng Nomalab

Khách hàng của Nomalab—bao gồm các tập đoàn truyền thông lớn—đang phải đối mặt với nhu cầu ngày càng tăng về việc cung cấp nhiều nội dung hơn cho các nền tảng truyền hình tuyến tính và OTT hơn bao giờ hết. Tự động hóa đã trở nên thiết yếu để duy trì lợi thế cạnh tranh về trải nghiệm người xem và hiệu quả hoạt động.

Một điểm khó khăn chính trong quy trình phân phối nội dung là việc tạo siêu dữ liệu phân đoạn cho nội dung dài, đặc biệt là việc xác định chuỗi tiêu đề, phần giới thiệu cuối phim và các điểm chèn quảng cáo tôn trọng mạch truyện.
Mục tiêu là tạo ra một hệ thống tạo siêu dữ liệu chính xác mà không cần sự can thiệp của con người, giúp tăng tốc đáng kể việc chuẩn bị nội dung và giảm chi phí.

“Khách hàng của chúng tôi cần có khả năng chèn quảng cáo liền mạch vào chương trình của họ, nhưng việc xem xét thủ công hàng giờ cảnh quay để xác định các đoạn quảng cáo xen kẽ phù hợp lại cực kỳ tốn thời gian”,
Romane Lafon, Giám đốc Công nghệ Truyền thông Kỹ thuật số tại Nomalab, giải thích.
“Chúng tôi biết AI có thể là giải pháp, nhưng chúng tôi muốn một giải pháp có độ chính xác cao và tiết kiệm chi phí để vận hành trên quy mô lớn”.

Để đáp ứng các tiêu chuẩn chất lượng nghiêm ngặt, Nomalab đặt mục tiêu đạt độ chính xác trên 90% trong việc xác định các điểm phân đoạn—tương đương hoặc vượt trội hơn hiệu suất của con người. Điều này giúp khách hàng tự tin áp dụng hoàn toàn các quy trình làm việc tự động.

---

## Tích hợp Media2Cloud và Trí tuệ Nhân tạo (AI)

Khi đối mặt với việc tự động hóa phát hiện đoạn quảng cáo xen kẽ, Nomalab đã chuyển sang Media2Cloud. Nền tảng này không chỉ đơn giản hóa việc di chuyển nội dung video và siêu dữ liệu sang AWS mà còn khai thác những hiểu biết sâu sắc hơn về nội dung bằng cách tận dụng khả năng trích xuất siêu dữ liệu được hỗ trợ bởi AI.

“Bằng cách tích hợp Media2Cloud và các khả năng AI tiên tiến, chúng tôi đã có thể phát triển một giải pháp mạnh mẽ độc đáo, tự động hóa các tác vụ chính và mang lại kết quả có thể đo lường được cho khách hàng của chúng tôi”, Lafon cho biết.

---

## Cách thức hoạt động
Media2Cloud sử dụng kết hợp AI/ML truyền thống và AI tạo sinh để phát hiện các điểm ngắt nội dung tự nhiên—được gọi là điểm chương—khi bối cảnh hình ảnh và tường thuật thay đổi.
**Bước 1: Phát hiện Cảnh quay Trực quan**
Quá trình bắt đầu với Amazon Rekognition Segment API, cung cấp khả năng phát hiện cảnh quay chính xác đến từng khung hình và nhận dạng tín hiệu kỹ thuật (ví dụ: thanh màu, khung hình đen, phần giới thiệu cuối phim).

---
## Bước 2: Nhóm Cảnh quay thành Cảnh
Các cảnh quay được phát hiện sẽ được nhóm lại thành các cảnh logic bằng mô hình Nhúng Đa phương thức Amazon Titan thông qua Amazon Bedrock.
Các khung hình được chuyển đổi thành các nhúng vector, nắm bắt ý nghĩa ngữ nghĩa, được lưu trữ trong Amazon OpenSearch Service bằng cách sử dụng chỉ mục K-NN để nhóm các khung hình tương tự lại với nhau.

---
## Bước 3: Phân tích Luồng Hội thoại
Tiếp theo, Amazon Transcribe chuyển đổi lời nói thành văn bản có dấu thời gian, và Amazon Bedrock phân tích luồng hội thoại để xác định các chuyển tiếp chủ đề, giúp tạo ra các điểm ngắt chương tự nhiên phù hợp với tín hiệu trực quan.


---

## Bước 4: Căn chỉnh Tín hiệu Âm thanh và Hình ảnh
Bằng cách căn chỉnh các cảnh được phát hiện với các đoạn hội thoại chuyển tiếp, quy trình làm việc sẽ xác định các cơ hội ngắt quảng cáo tự nhiên, không gây khó chịu - những điểm mà các đoạn quảng cáo gián đoạn ít gây ảnh hưởng nhất đến trải nghiệm của người xem.

---
## Đặt Ngắt Quảng cáo
Dựa trên nền tảng này, tính năng phát hiện ngắt quảng cáo của Media2Cloud xác định chính xác các cơ hội đặt quảng cáo chính xác theo từng khung hình, đồng thời tạo siêu dữ liệu theo ngữ cảnh bằng IAB Content Taxonomy V3 và GARM Taxonomy.

Lớp ngữ cảnh này cho phép các máy chủ quyết định quảng cáo đưa ra các lựa chọn vị trí thông minh dựa trên nội dung xung quanh.

---

## Tích hợp
Nomalab mở rộng Media2Cloud với giai đoạn hậu đánh giá độc quyền, phản ánh quá trình ra quyết định của con người.

Các quy tắc kinh doanh tùy chỉnh tinh chỉnh và ưu tiên các cơ hội ngắt quảng cáo, đảm bảo chỉ chọn những ngắt quảng cáo phù hợp và chiến lược nhất.

Sự chuyển đổi nàyrms dữ liệu phát hiện thô thành thông tin chi tiết ở cấp độ sản xuất, mang lại vị trí quảng cáo tối ưu đồng thời duy trì tính toàn vẹn của trải nghiệm xem.

Hình 6 – Quy trình phân tích của Nomalab tích hợp các dịch vụ AWS và logic hậu đánh giá độc quyền.
“Việc tích hợp với Media2Cloud là rất quan trọng,” Lafon nói.
“Nó cung cấp một nền tảng đám mây có khả năng mở rộng, để chúng tôi có thể tập trung vào các tính năng được hỗ trợ bởi AI mang lại giá trị thực sự.

Khả năng AI tạo sinh của Amazon Bedrock là một bước đột phá — kết hợp thị giác máy tính, chuyển giọng nói thành văn bản, hiểu ngôn ngữ tự nhiên và các quy tắc kinh doanh để đạt được độ chính xác gần như con người.”

## Lợi ích và Kết quả
Bằng cách tự động hóa phát hiện quảng cáo ngắt quãng, Nomalab đã cải thiện đáng kể hiệu quả quy trình làm việc.

Một người vận hành thủ công có thể xử lý khoảng 25 chương trình mỗi ngày; giờ đây, với tính năng tự động hóa của AWS, toàn bộ thư viện có thể được phân tích trong vài giờ — ở quy mô lớn và với độ chính xác nhất quán.
“Mục tiêu chung của chúng tôi là đạt tỷ lệ chính xác 90% trở lên, và chúng tôi gần đạt được hoặc cao hơn tùy thuộc vào loại nội dung,” Lafon nói.

“Điều tuyệt vời nhất là khách hàng của chúng tôi không phải lo lắng về sự phức tạp—họ chỉ cần nhận được nội dung đa phương tiện được làm giàu đầy đủ, sẵn sàng để tiếp nhận và phân phối.”
Khả năng mở rộng là một lợi ích quan trọng khác:
“Chúng tôi xử lý hàng chục nghìn nội dung mỗi năm mà vẫn kiểm soát được chi phí,” Lafon nói thêm. “Đây là lợi ích đôi bên cùng có lợi cho chúng tôi và khách hàng.”

## Hướng tới Tương lai
Khi ngành truyền thông phát triển, quy trình làm việc của Nomalab làm nổi bật cách AWS và AI tạo sinh đang chuyển đổi hoạt động truyền thông.
“Đây chỉ là bước khởi đầu,” Lafon nói.
“Chúng tôi đang khám phá tự động hóa để phân loại nội dung, làm giàu siêu dữ liệu và thậm chí là kiểm soát chất lượng truyền thông. Tiềm năng là vô hạn.”

Bằng cách kết hợp Amazon Bedrock, Amazon Rekognition và Amazon Transcribe, Nomalab chứng minh sức mạnh của việc kết hợp công nghệ AI và đám mây để đạt được độ chính xác ngang tầm con người trong các quy trình làm việc tự động.
Sự kết hợp giữa các dịch vụ AI/ML nền tảng và AI tạo sinh này mở ra những hiểu biết mới từ nội dung đa phương tiện—thiết lập một chuẩn mực mới cho tự động hóa trong ngành truyền thông.
Nhìn về tương lai, khi AI dựa trên đám mây tiếp tục phát triển, những công nghệ này sẽ thúc đẩy các quy trình xử lý nội dung ngày càng thông minh và tự động - trở thành yếu tố khác biệt quan trọng cho các tổ chức truyền thông cạnh tranh.

Đối với các công ty truyền thông đang tìm kiếm các hoạt động bền vững trong tương lai, thành công của Nomalab trên AWS minh chứng cho những gì có thể đạt được bằng cách áp dụng những cải tiến mới nhất về AI, điện toán đám mây và AI tạo sinh - chuyển đổi quy trình làm việc truyền thông cho kỷ nguyên số.