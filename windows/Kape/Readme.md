# 1. KAPE là gì?

Kroll Artifact Parser and Extractor (KAPE) là một chương trình phân loại, phân tích mục tiêu từ một thiết bị hoặc vị trí lưu trữ, tìm các thông tin có liên quan. 
KAPE cho phép các nhà điều tra tìm và ưu tiên các hệ thống quan trọng hơn đối với trường hợp của họ. Ngoài ra, KAPE có thể được sử dụng để thu thập các thông tin quan trọng trước khi bắt đầu quá trình phân tích. 

# 2. Cách thức hoạt động của KAPE

KAPE phục vụ hai chức năng chính: 
1) Thu thập tệp
2) Xử lý tệp đã thu thập bằng một hoặc nhiều chương trình. 

KAPE đọc các tệp cấu hình và dựa trên nội dung của các tệp này để thu thập, xử lý. KAPE rất dễ mở rộng hoặc mở rộng chức năng. Quá trình hoạt động được chia làm 2 giai đoạn: 

- Khi bắt đầu cần phải chọn chỉ mục, các module, sau khi khởi chạy KAPE sẽ tạo một bản sao và lưu giữ siêu dữ liệu về tất cả các tệp có sẵn từ một vị trí nguồn vào một thư mục nhất định.

- Kape sẽ chạy một hoặc nhiều tùy chọn. Điều này hoạt động bằng cách "target" mục tiêu tên tệp hoặc thư mục cụ thể. Các chương trình khác nhau được chạy đối với các tệp và đầu ra từ các chương trình đó được lưu trong các thư mục được đặt tên theo một danh mục: EvidenceOfExecution, BrowserHistory, AccountUsage, v.v.

# 3. Thực nghiệm

Đây là một ví dụ đơn giản trong đó chúng tôi vừa chỉ định đường dẫn đầy đủ cho từng tệp mà chúng tôi quan tâm. Trong một số trường hợp, như $MFT và $SDS, chúng tôi phải sử dụng một thuộc tính bổ sung, AlwaysAddToQueue, bởi vì Windows sẽ, trên một tệp đang chạy. hệ thống, nói dối và nói rằng tệp đó không tồn tại (dù sao cũng thông qua các phương tiện thông thường).

Hãy xem xét một ví dụ khác:

Các ví dụ trực quan tham khảo trên [blog trực tiếp](https://binaryforay.blogspot.com/2019/02/introducing-kape.html) của nhà phát triển
