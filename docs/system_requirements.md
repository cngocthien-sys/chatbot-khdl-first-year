# Yêu cầu hệ thống chatbot AI hỏi đáp tài liệu

## 1. Mục tiêu hệ thống

Hệ thống được xây dựng nhằm hỗ trợ sinh viên năm nhất ngành Khoa học dữ liệu
tra cứu và hỏi đáp nội dung trong các tài liệu học tập.

Chatbot sử dụng kiến trúc Retrieval-Augmented Generation (RAG) để truy hồi
thông tin từ tài liệu và cung cấp câu trả lời dựa trên nội dung đã truy hồi.

## 2. Đối tượng sử dụng

Đối tượng chính là sinh viên năm nhất ngành Khoa học dữ liệu.

Người dùng có thể chưa có nhiều kinh nghiệm với các thuật ngữ chuyên ngành,
do đó câu trả lời cần rõ ràng, dễ hiểu và có nguồn tham khảo.

## 3. Yêu cầu chức năng

### FR01 - Tải tài liệu

Hệ thống cho phép người dùng tải tài liệu học tập lên.

Định dạng dự kiến:
- PDF
- DOCX

### FR02 - Đặt câu hỏi

Người dùng có thể nhập câu hỏi bằng tiếng Việt liên quan đến nội dung
của tài liệu đã cung cấp.

### FR03 - Truy hồi thông tin

Hệ thống tìm kiếm các đoạn văn bản có nội dung liên quan đến câu hỏi
trong kho tài liệu.

### FR04 - Sinh câu trả lời

Chatbot sử dụng LLM để tạo câu trả lời dựa trên các đoạn văn bản
được truy hồi.

### FR05 - Trích dẫn nguồn

Câu trả lời cần hiển thị nguồn tham khảo, bao gồm:
- Tên tài liệu
- Số trang hoặc vị trí của nội dung trong tài liệu

### FR06 - Xử lý trường hợp không có thông tin

Nếu không tìm thấy thông tin phù hợp trong tài liệu, chatbot cần thông báo
rằng chưa tìm thấy nội dung thay vì tự tạo câu trả lời không có căn cứ.

### FR07 - Hỗ trợ hội thoại

Người dùng có thể tiếp tục đặt câu hỏi liên quan đến câu hỏi trước đó.

## 4. Yêu cầu phi chức năng

### NFR01 - Thời gian phản hồi

Thời gian phản hồi dự kiến dưới 10 giây đối với điều kiện sử dụng thông thường.

### NFR02 - Khả năng sử dụng

Giao diện cần đơn giản và phù hợp với sinh viên năm nhất.

### NFR03 - Độ tin cậy

Câu trả lời phải ưu tiên thông tin có trong tài liệu được cung cấp.

### NFR04 - Khả năng mở rộng

Hệ thống có thể bổ sung thêm tài liệu và môn học trong tương lai.

### NFR05 - Ngôn ngữ

Câu hỏi và câu trả lời chủ yếu bằng tiếng Việt.
Tài liệu nguồn có thể bao gồm cả tiếng Việt và tiếng Anh.

## 5. Phạm vi ban đầu

Trong giai đoạn đầu, hệ thống tập trung vào tài liệu phục vụ sinh viên năm nhất
ngành Khoa học dữ liệu.

Hệ thống chưa hướng tới:
- Hỏi đáp kiến thức mở ngoài tài liệu.
- Xử lý số lượng lớn người dùng đồng thời.
- Huấn luyện mô hình ngôn ngữ lớn từ đầu.
