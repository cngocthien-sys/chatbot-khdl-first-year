# Thiết kế kiến trúc hệ thống chatbot RAG

## 1. Mục tiêu

Thiết kế kiến trúc tổng thể cho hệ thống chatbot AI hỏi đáp tài liệu
hỗ trợ sinh viên năm nhất ngành Khoa học dữ liệu.

Hệ thống được xây dựng theo kiến trúc Retrieval-Augmented Generation (RAG).

## 2. Kiến trúc tổng thể

Hệ thống gồm hai giai đoạn chính:

### Giai đoạn 1 - Xây dựng kho tri thức

PDF / DOCX
→ Document Loader
→ Text Extraction
→ Text Cleaning
→ Chunking
→ Embedding Model
→ Vector Database

### Giai đoạn 2 - Hỏi đáp

User Question
→ Query Embedding
→ Retriever
→ Top-k Relevant Chunks
→ Prompt + Context
→ LLM
→ Answer + Citation

## 3. Các thành phần

### 3.1. Document Loader

Chức năng:

- Đọc tài liệu PDF.
- Đọc tài liệu DOCX.
- Giữ thông tin về tên tài liệu và số trang.

Công cụ dự kiến:

- PyMuPDF.
- pdfplumber.
- python-docx.

## 3.2. Text Processing

Chức năng:

- Loại bỏ ký tự thừa.
- Chuẩn hóa Unicode tiếng Việt.
- Loại header/footer nếu cần.
- Giữ metadata của tài liệu.

## 3.3. Chunking

Tài liệu được chia thành các đoạn nhỏ để phục vụ truy hồi.

Các phương pháp dự kiến thử nghiệm:

- Fixed-size chunking.
- Fixed-size chunking có overlap.
- Chia theo tiêu đề hoặc cấu trúc đoạn văn.

Các tham số cần khảo sát:

- chunk_size.
- chunk_overlap.

## 3.4. Embedding Model

Embedding model chuyển mỗi chunk thành vector.

Các mô hình dự kiến:

- multilingual-e5-base.
- Vietnamese-bi-encoder.

Mục tiêu là lựa chọn mô hình có khả năng truy hồi tốt
đối với tài liệu tiếng Việt và song ngữ Việt - Anh.

## 3.5. Vector Database

Dùng để lưu:

- Vector embedding.
- Nội dung chunk.
- Tên tài liệu.
- Số trang.
- Metadata khác.

Giải pháp ban đầu:

- FAISS hoặc
- ChromaDB.

## 3.6. Retriever

Retriever nhận embedding của câu hỏi
và tìm các chunk liên quan nhất.

Cấu hình ban đầu:

top-k = 3 hoặc 5.

Sau khi có baseline có thể khảo sát thêm:

- BM25.
- Hybrid Retrieval.
- Re-ranking.

## 3.7. Large Language Model

LLM nhận:

- Câu hỏi của sinh viên.
- Các đoạn tài liệu được truy hồi.

LLM sinh câu trả lời dựa trên context được cung cấp.

Mô hình có thể sử dụng:

- GPT.
- Gemini.
- Qwen.

## 3.8. Citation

Mỗi câu trả lời cần cố gắng hiển thị:

- Tên tài liệu.
- Số trang.
- Đoạn nội dung liên quan.

Việc này giúp sinh viên kiểm tra lại câu trả lời trong tài liệu gốc.

## 4. Luồng xử lý chi tiết

### Offline

1. Người dùng cung cấp tài liệu.
2. Hệ thống trích xuất văn bản.
3. Văn bản được làm sạch.
4. Văn bản được chia thành các chunk.
5. Mỗi chunk được chuyển thành embedding.
6. Vector và metadata được lưu trong vector database.

### Online

1. Sinh viên đặt câu hỏi.
2. Câu hỏi được chuyển thành embedding.
3. Retriever tìm top-k chunk liên quan.
4. Các chunk được đưa vào prompt.
5. LLM sinh câu trả lời.
6. Hệ thống trả kết quả kèm nguồn.

## 5. Công nghệ dự kiến

| Thành phần | Công nghệ dự kiến |
|---|---|
| Ngôn ngữ | Python |
| Xử lý PDF | PyMuPDF / pdfplumber |
| DOCX | python-docx |
| RAG Framework | LangChain hoặc LlamaIndex |
| Embedding | multilingual-e5 / Vietnamese-bi-encoder |
| Vector Database | FAISS / ChromaDB |
| LLM | GPT / Gemini / Qwen |
| Giao diện | Streamlit |
| Đánh giá | Recall@k, MRR, RAGAS |

## 6. Nguyên tắc triển khai

Ở giai đoạn đầu, nhóm ưu tiên xây dựng một baseline RAG đơn giản
chạy end-to-end.

Sau khi baseline hoạt động ổn định mới tiến hành:

- So sánh embedding.
- Thử nghiệm chunk size.
- Thử nghiệm overlap.
- Thử nghiệm top-k.
- Bổ sung BM25 hoặc re-ranking nếu cần.

## 7. Kết luận

Kiến trúc trên được lựa chọn vì phù hợp với phạm vi đồ án,
dễ triển khai theo từng module và cho phép đánh giá riêng
chất lượng retrieval cũng như chất lượng câu trả lời.
