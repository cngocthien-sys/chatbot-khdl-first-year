# Tổng quan về Retrieval-Augmented Generation (RAG)

## 1. Khái niệm

Retrieval-Augmented Generation (RAG) là kiến trúc kết hợp giữa
hệ thống truy hồi thông tin và mô hình ngôn ngữ lớn (LLM).

Thay vì để LLM chỉ dựa vào kiến thức nội tại,
RAG tìm kiếm các đoạn thông tin liên quan từ nguồn dữ liệu bên ngoài
và đưa những thông tin đó vào ngữ cảnh trước khi sinh câu trả lời.

## 2. Vai trò của RAG trong đề tài

Trong đề tài chatbot hỏi đáp tài liệu,
RAG được sử dụng để giúp hệ thống trả lời dựa trên chính tài liệu học tập
của sinh viên năm nhất ngành Khoa học dữ liệu.

Quy trình cơ bản:

Tài liệu
→ Trích xuất văn bản
→ Chia văn bản thành các đoạn nhỏ
→ Sinh embedding
→ Lưu vào vector database

Khi người dùng đặt câu hỏi:

Câu hỏi
→ Sinh embedding của câu hỏi
→ Tìm các đoạn liên quan
→ Đưa các đoạn này vào LLM
→ Sinh câu trả lời
→ Trả lời kèm trích dẫn nguồn

## 3. Hai giai đoạn chính của hệ thống RAG

### 3.1. Giai đoạn xây dựng kho dữ liệu

Các tài liệu PDF hoặc DOCX được:

- Trích xuất nội dung.
- Làm sạch văn bản.
- Chia thành các chunk.
- Sinh embedding cho từng chunk.
- Lưu vector và metadata vào vector database.

Metadata có thể bao gồm:

- Tên tài liệu.
- Môn học.
- Chương.
- Số trang.

## 3.2. Giai đoạn hỏi đáp

Khi sinh viên nhập câu hỏi:

1. Câu hỏi được chuyển thành vector embedding.
2. Hệ thống tìm các chunk gần nhất trong vector database.
3. Các chunk liên quan nhất được chọn làm context.
4. Context cùng câu hỏi được gửi tới LLM.
5. LLM sinh câu trả lời dựa trên context.
6. Hệ thống hiển thị câu trả lời kèm nguồn.

## 4. Lợi ích của RAG

RAG phù hợp với đề tài vì:

- Câu trả lời bám sát tài liệu học tập.
- Giảm hallucination của LLM.
- Cho phép hiển thị nguồn tham khảo.
- Không cần huấn luyện lại LLM từ đầu.
- Có thể cập nhật kiến thức bằng cách thêm tài liệu mới.
- Phù hợp với hệ thống hỏi đáp tài liệu chuyên ngành.

## 5. Các thành phần chính

Hệ thống RAG dự kiến gồm:

### Document Loader

Đọc nội dung từ PDF và DOCX.

### Text Processing

Làm sạch và chuẩn hóa văn bản.

### Chunking

Chia tài liệu thành các đoạn nhỏ để phục vụ truy hồi.

### Embedding Model

Chuyển văn bản thành vector số.

### Vector Database

Lưu trữ và tìm kiếm các vector.

### Retriever

Tìm các đoạn văn bản liên quan nhất đến câu hỏi.

### LLM

Sinh câu trả lời dựa trên câu hỏi và các đoạn tài liệu được truy hồi.

## 6. Kiến trúc dự kiến của đề tài

Pipeline ban đầu:

PDF/DOCX
→ Text Extraction
→ Cleaning
→ Chunking
→ Embedding
→ Vector Database

Sau đó:

User Question
→ Query Embedding
→ Retriever
→ Relevant Chunks
→ Prompt + Context
→ LLM
→ Answer + Source

## 7. Hướng thực nghiệm

Ở các tuần tiếp theo, nhóm dự kiến so sánh:

- Phương pháp chunking.
- Kích thước chunk.
- Độ overlap.
- Mô hình embedding.
- Số lượng kết quả truy hồi top-k.

Trước tiên hệ thống sẽ xây dựng một baseline RAG đơn giản,
sau đó mới bổ sung các kỹ thuật nâng cao nếu cần.

## 8. Kết luận

RAG là kiến trúc chính của hệ thống chatbot trong đề tài.
Nó giúp kết hợp khả năng sinh ngôn ngữ của LLM với thông tin
được truy hồi trực tiếp từ tài liệu học tập.
