# Khảo sát và so sánh các giải pháp hỏi đáp tài liệu

## 1. Mục tiêu

Khảo sát một số giải pháp hỏi đáp tài liệu hiện có nhằm xác định
những ưu điểm có thể kế thừa và những hạn chế cần khắc phục
trong hệ thống chatbot của đề tài.

## 2. ChatGPT / Gemini khi hỏi trực tiếp

### Ưu điểm

- Khả năng hiểu ngôn ngữ tự nhiên tốt.
- Câu trả lời trôi chảy.
- Có kiến thức trên nhiều lĩnh vực.
- Hỗ trợ tiếng Việt.

### Hạn chế

- Không đảm bảo câu trả lời bám sát giáo trình.
- Có thể xảy ra hallucination.
- Khó xác định chính xác nguồn thông tin.
- Nội dung có thể khác với tài liệu môn học của sinh viên.

### Hướng kế thừa

Sử dụng LLM làm thành phần sinh câu trả lời,
nhưng cung cấp context được truy hồi từ tài liệu bằng RAG.

## 3. ChatPDF

### Ưu điểm

- Cho phép tải PDF và hỏi đáp trực tiếp.
- Giao diện đơn giản.
- Có khả năng tham chiếu nội dung tài liệu.

### Hạn chế

- Người dùng khó kiểm soát pipeline xử lý bên trong.
- Khó tùy chỉnh embedding và retrieval.
- Không phù hợp cho việc thực nghiệm các cấu hình RAG.

### Hướng kế thừa

Kế thừa ý tưởng hỏi đáp trực tiếp trên tài liệu
và hiển thị nguồn của câu trả lời.

## 4. AskYourPDF

### Ưu điểm

- Hỗ trợ hỏi đáp tài liệu.
- Có giao diện hội thoại.
- Có thể xử lý nhiều loại tài liệu.

### Hạn chế

- Là hệ thống đóng.
- Khó thực hiện các thử nghiệm về chunking,
embedding và retrieval.
- Không được thiết kế riêng cho sinh viên năm nhất ngành Khoa học dữ liệu.

## 5. Chatbot RAG của đề tài

Hệ thống của đề tài dự kiến có các đặc điểm:

- Tập trung vào sinh viên năm nhất ngành Khoa học dữ liệu.
- Trả lời dựa trên tài liệu học tập được cung cấp.
- Hỗ trợ tài liệu tiếng Việt và tiếng Anh.
- Hiển thị tên tài liệu và số trang.
- Cho phép thử nghiệm nhiều phương pháp chunking.
- So sánh các mô hình embedding.
- Đánh giá chất lượng retrieval bằng các độ đo định lượng.

## 6. Bảng so sánh

| Giải pháp | Bám tài liệu | Trích dẫn nguồn | Có thể tùy chỉnh RAG | Phù hợp đề tài |
|---|---|---|---|---|
| ChatGPT/Gemini trực tiếp | Thấp | Hạn chế | Không | Trung bình |
| ChatPDF | Có | Có | Hạn chế | Khá |
| AskYourPDF | Có | Có | Hạn chế | Khá |
| Hệ thống của đề tài | Có | Có | Có | Cao |

## 7. Kết luận

Nhóm lựa chọn tự xây dựng hệ thống RAG nhằm chủ động kiểm soát
quá trình xử lý tài liệu, embedding, retrieval và sinh câu trả lời.

Điểm khác biệt chính là hệ thống được thiết kế cho tài liệu học tập
của sinh viên năm nhất ngành Khoa học dữ liệu và có khả năng
đánh giá, so sánh các cấu hình truy hồi.
