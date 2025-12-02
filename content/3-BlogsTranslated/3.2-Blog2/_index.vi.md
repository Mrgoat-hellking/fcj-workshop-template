---
title: "Blog 2"
date: 2025-01-01
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---
# Tối ưu hóa Tìm kiếm Đa phương thức bằng API Nhúng TwelveLabs và Dịch vụ Tìm kiếm Mở Amazon

*bởi James Le, Gitika Vijh và Kruthi Jayasimha Rao vào ngày 04 tháng 4 năm 2025 trong mục Nâng cao (300), Dịch vụ Tìm kiếm Mở Amazon, Giải pháp Đối tác*

Sự phát triển theo cấp số nhân của nội dung video đã tạo ra cả cơ hội lẫn thách thức. Các nhà sáng tạo nội dung, nhà tiếp thị và nhà nghiên cứu hiện đang phải đối mặt với nhiệm vụ khó khăn là tìm kiếm, phân tích và trích xuất thông tin chi tiết có giá trị một cách hiệu quả từ các thư viện video khổng lồ.

Các phương pháp tìm kiếm dựa trên từ khóa truyền thống thường không hiệu quả khi phân tích các yếu tố hình ảnh, âm thanh hoặc ngữ cảnh trong video, khiến các tổ chức khó khai thác hết tiềm năng của các tài sản đa phương tiện.

Bằng cách tích hợp API Nhúng của TwelveLabs với Dịch vụ Tìm kiếm Mở Amazon, giờ đây chúng ta có thể tương tác và thu thập thông tin chi tiết trực tiếp từ nội dung video. Công nghệ hiểu video tiên tiến dựa trên AI của TwelveLabs, kết hợp với cơ sở dữ liệu vector và khả năng phân tích của OpenSearch, cho phép khám phá video đa phương thức với khả năng hiểu ngữ cảnh sâu sắc.

Bài viết này trình bày cách tích hợp API Nhúng TwelveLabs với Dịch vụ OpenSearch để xây dựng giải pháp tìm kiếm đa phương thức. Bạn sẽ học cách:
* Tạo các nội dung nhúng phong phú, có ngữ cảnh từ nội dung video.

* Lưu trữ và lập chỉ mục các nội dung nhúng này trong OpenSearch.

* Kích hoạt khả năng tìm kiếm trên các phương thức văn bản, hình ảnh và âm thanh.

Cuối cùng, bạn sẽ hiểu cách triển khai một hệ thống có thể chuyển đổi cách tổ chức của bạn xử lý và trích xuất giá trị từ nội dung video.

---

### TwelveLabs là Đối tác Nâng cao của AWS và Nhà cung cấp AWS Marketplace, chuyên về các giải pháp hiểu video.

API Nhúng của TwelveLabs chuyển đổi nội dung video thô thành dữ liệu có ý nghĩa, có thể tìm kiếm được bằng cách sử dụng các mô hình học máy tiên tiến.

Mỗi video được chuyển đổi thành một vector nhúng dày đặc 1024 chiều, thể hiện các đặc điểm ngữ nghĩa cốt lõi trên nhiều phương thức—hình ảnh, văn bản và âm thanh.

---

## Các tính năng chính của API Nhúng TwelveLabs
* Hiểu biết đa phương thức – Tạo các nhúng nắm bắt biểu cảm hình ảnh, ngôn ngữ cơ thể, lời nói và bối cảnh tổng thể.

* Tính nhất quán về thời gian – Mô hình hóa mối quan hệ giữa các phương thức theo thời gian để biểu diễn ngữ cảnh chính xác.

* Tính linh hoạt – Xử lý tất cả các phương thức (video, văn bản, âm thanh) một cách tự nhiên mà không cần mô hình riêng biệt.

* Hiệu suất cao – Sử dụng phương pháp tiếp cận video gốc để đạt được tính nhất quán về thời gian và ngữ cảnh vượt trội.

## Lợi ích và Trường hợp Sử dụng
API Nhúng mang lại một số lợi thế cho doanh nghiệp và nhà phát triển làm việc với nội dung video:

Khả năng Tìm kiếm Nâng cao – Thực hiện tìm kiếm đa phương thức trên các thư viện video bằng văn bản, âm thanh hoặc hình ảnh.

Đề xuất Nội dung – Cải thiện độ chính xác của đề xuất thông qua sự tương đồng về ngữ cảnh giữa các video.

Phát hiện và Phân đoạn Cảnh – Tự động phát hiện và phân đoạn cảnh để phân tích dễ dàng hơn.

Kiểm duyệt Nội dung – Xác định hiệu quả nội dung không phù hợp trên các tập dữ liệu lớn.

**Các trường hợp sử dụng phổ biến bao gồm**:
Phát hiện bất thường

Phân tích cảm xúc

Phân loại đa dạng

Đề xuất nội dung thông minh

## Tổng quan về kiến ​​trúc
Kiến trúc này tích hợp TwelveLabs Embed API và Amazon OpenSearch Service để hỗ trợ tìm kiếm đa phương thức nâng cao. Kiến trúc bao gồm:

* 1. TwelveLabs Embed API – Tạo nhúng vector 1024 chiều từ nội dung video, ghi lại các mối quan hệ đa phương thức.

* 2. Amazon OpenSearch Service (Cơ sở dữ liệu Vector) – Lưu trữ và lập chỉ mục các nhúng cho tìm kiếm dựa trên vector.

* 3. AWS Secrets Manager – Lưu trữ khóa API, thông tin xác thực OpenSearch và bí mật truy cập một cách an toàn.

* 4. Các thành phần tích hợp – TwelveLabs SDK và OpenSearch Client để xử lý video, tạo nhúng và lập chỉ mục dữ liệu.

---

## Trường hợp sử dụng
Trong bản demo, hai video ví dụ được sử dụng:
* Video chim Robin trong rừng của Federico Maderno

* Video đảo của Bellergy RC

Tuy nhiên, kiến ​​trúc này cũng áp dụng cho các trường hợp sử dụng khác như:
* Tìm kiếm hàng nghìn giờ cảnh quay tin tức lưu trữ.

* Tự động gắn thẻ siêu dữ liệu cho bối cảnh hình ảnh và âm thanh phức tạp.

* Thực hiện các truy vấn đa phương thức (văn bản, hình ảnh hoặc âm thanh sang video).

* Truy xuất nhanh các clip liên quan đến tin tức nóng hổi hoặc điểm nổi bật.

Bằng cách tích hợp TwelveLabs Embed API với Dịch vụ OpenSearch, các tổ chức có thể:
* Tạo các nhúng 1024 chiều để ghi lại nội dung video, tín hiệu âm thanh và văn bản trên màn hình.

* Cho phép tìm kiếm văn bản sang video, hình ảnh sang video và âm thanh sang video.

* Giảm thời gian truy xuất từ ​​vài giờ xuống còn vài giây.

---

## Hướng dẫn giải pháp
**Bước 1 – Thiết lập TwelveLabs SDK**
Lấy Khóa API TwelveLabs của bạn.

Lưu khóa này trong AWS Secrets Manager (ví dụ: trong TL_API_KEY).

Sử dụng AWS SDK để truy xuất và sử dụng khóa này trong môi trường Python của bạn.

---

**Bước 2 – Tạo Nhúng Video**
Sử dụng API Nhúng để tạo nhúng đa phương thức.

Mô hình (Marengo-retrieval-2.7) xử lý video, ghi lại mối quan hệ giữa hình ảnh, văn bản và âm thanh.
Nhúng được thực hiện không đồng bộ để tạo và thể hiện nội dung phong phú, có tính thời gianTính năng e.

---
**Bước 3 – Cấu hình Amazon OpenSearch**
Cài đặt opensearch-py, botocore và requests-aws4auth.

Xác thực với miền OpenSearch của bạn bằng thông tin đăng nhập đã lưu trữ.

Xác minh kết nối và truy xuất thông tin cụm.

---

**Bước 4 – Tạo Chỉ mục Vector**
Xác định một chỉ mục với trường knn_vector 1024 chiều để tìm kiếm tương tự.

Điều này cho phép truy vấn k-láng giềng gần nhất (kNN) nhanh chóng trên các video nhúng.

---
**Bước 5 – Nhập Nhúng vào OpenSearch**
Sau khi các nhúng được tạo, hãy nhập chúng vào chỉ mục bằng API hàng loạt.

Mỗi tài liệu lưu trữ:
Tiêu đề video

Thời gian bắt đầu và kết thúc phân đoạn

Véc-tơ nhúng

---
**Bước 6 – Thực hiện Tìm kiếm Vectơ**
Chạy truy vấn tìm kiếm dựa trên vectơ để tìm các nhúng tương tự nhất bằng cách sử dụng:

def search_similar_segments(query_vector, k=5):
```yaml
   query = {
     "size": k,
      "query": {
        "knn": {
           "embedding_field": {
           "vector": query_vector,
               "k": k
             }
          }
         }
      }

```
Hàm này truy xuất k phân đoạn video giống nhất với một vectơ truy vấn nhất định.

---
**Bước 7 – Tìm kiếm Văn bản thành Video**
Chuyển đổi truy vấn văn bản (ví dụ: “Chim ăn thức ăn”) thành nhúng vectơ bằng mô hình nhúng văn bản của TwelveLabs, sau đó thực hiện tìm kiếm kNN trong OpenSearch.
Kết quả trả về:
Tên video

Khoảng thời gian

Điểm tương đồng

---

**Bước 8 – Tìm kiếm Âm thanh-Video**
Sử dụng khả năng nhúng âm thanh của TwelveLabs để chuyển đổi một đoạn âm thanh (ví dụ: "Rock 808 beat.mp3") thành một vectơ.

Thực hiện tìm kiếm vectơ để tìm các đoạn video có đặc điểm âm thanh phù hợp.

---
**Bước 9 – Tìm kiếm Hình ảnh-Video**
Sử dụng một hình ảnh (ví dụ: Hình ảnh Đại dương của shotbyjagar) để tạo nhúng và thực hiện ghép hình ảnh-video.

Các cảnh tương tự về mặt hình ảnh được tìm thấy dựa trên các đặc điểm hình dạng, màu sắc và bố cục được mã hóa trong nhúng.

## Kết quả và Thông tin chi tiết
Mỗi tìm kiếm trả về một danh sách được xếp hạng các phân đoạn video có liên quan, bao gồm điểm tương đồng và dấu thời gian.
Ví dụ:

Truy vấn văn bản: "Chim ăn thức ăn" sẽ tìm các phân đoạn từ video robin-bird.mp4.

Truy vấn hình ảnh: Một hình ảnh đại dương sẽ tìm các phân đoạn có điểm cao từ video island.mp4.

Truy vấn âm thanh: Một track nhịp điệu sẽ truy xuất các đoạn video được đồng bộ hóa trực quan.

Điều này cho phép truy xuất video đa phương thức với khả năng hiểu ngữ nghĩa giống con người.

---
## Dọn dẹp
Để tránh phát sinh chi phí, hãy xóa:
Miền Dịch vụ OpenSearch.

Bất kỳ bucket S3, Secret và hàm Lambda nào đã tạo.

---

## Kết luận
Việc tích hợp API Nhúng TwelveLabs với Dịch vụ Amazon OpenSearch mang đến một giải pháp mạnh mẽ, có khả năng mở rộng cho tìm kiếm và phân tích video đa phương thức.

Bằng cách kết hợp các nhúng gốc video của TwelveLabs với khả năng tìm kiếm vector của OpenSearch, bạn có thể thực hiện tìm kiếm văn bản sang video, hình ảnh sang video và âm thanh sang video - mở ra những hiểu biết theo ngữ cảnh mà các phương pháp truyền thống không thể sánh kịp.

Cách tiếp cận này trao quyền cho các nhà phát triển và tổ chức:

Nâng cao khả năng tìm kiếm và khám phá video.

Cải thiện sự tương tác của người dùng với khả năng truy xuất nội dung thông minh.

Cho phép phân tích nâng cao trên các tập dữ liệu đa phương tiện khổng lồ.

Khi các ngành công nghiệp ngày càng phụ thuộc vào video để giao tiếp, học tập và tiếp thị, tìm kiếm AI đa phương thức sẽ là yếu tố khác biệt quan trọng trong việc quản lý và hiểu các kho lưu trữ video lớn.