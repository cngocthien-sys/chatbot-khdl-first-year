# Ghi chú nghiên cứu về Vector Database

## 1. Khái niệm

Vector Database là cơ sở dữ liệu được thiết kế để lưu trữ,
quản lý và tìm kiếm các vector embedding.

Trong hệ thống RAG, mỗi đoạn văn bản sau khi được xử lý
sẽ được chuyển thành vector và lưu trong vector database
cùng với các thông tin mô tả liên quan.

## 2. Vai trò trong hệ thống RAG

Vector database giúp hệ thống:

- Lưu embedding của các đoạn tài liệu.
- Tìm kiếm các đoạn có nội dung gần với câu hỏi.
- Truy xuất nhanh các chunk liên quan.
- Lưu metadata để phục vụ trích dẫn nguồn.

Quy trình:

Document Chunk
→ Embedding
→ Vector Database

User Question
→ Query Embedding
→ Similarity Search
→ Top-k Relevant Chunks

## 3. Metadata

Ngoài vector, hệ thống cần lưu metadata cho từng chunk.

Metadata dự kiến gồm:

- Tên tài liệu.
- Môn học.
- Chương.
- Số trang.
- Nội dung chunk.
- ID của chunk.

Metadata giúp hệ thống có thể hiển thị nguồn của câu trả lời.

## 4. Một số Vector Database được khảo sát

### FAISS

FAISS là thư viện tìm kiếm vector do Meta phát triển.

Ưu điểm:
- Tốc độ tìm kiếm nhanh.
- Dễ sử dụng trong Python.
- Phù hợp với thử nghiệm cục bộ.
- Không cần triển khai server riêng.

Hạn chế:
- Khả năng quản lý metadata không mạnh bằng các vector database chuyên dụng.

### ChromaDB

ChromaDB là vector database phổ biến cho các ứng dụng RAG.

Ưu điểm:
- Dễ tích hợp với LangChain.
- Hỗ trợ lưu vector và metadata.
- Phù hợp với ứng dụng demo.
- Có thể lưu dữ liệu cục bộ.

### Qdrant

Qdrant là vector database hỗ trợ tìm kiếm vector và metadata filtering.

Ưu điểm:
- Hiệu năng tốt.
- Hỗ trợ metadata filtering.
- Có thể triển khai dưới dạng server.

Trong phạm vi đồ án, Qdrant có thể được khảo sát thêm
nhưng không phải lựa chọn ưu tiên ở giai đoạn đầu.

## 5. Lựa chọn ban đầu

Trong giai đoạn xây dựng baseline,
nhóm dự kiến ưu tiên:

- FAISS hoặc
- ChromaDB.

Lý do:

- Dễ triển khai.
- Phù hợp với quy mô tài liệu nhỏ.
- Có nhiều tài liệu hướng dẫn.
- Tích hợp tốt với Python và các framework RAG.

## 6. Similarity Search

Khi người dùng đặt câu hỏi,
embedding của câu hỏi sẽ được so sánh với các vector trong cơ sở dữ liệu.

Hệ thống trả về top-k chunk có độ tương đồng cao nhất.

Ví dụ:

top-k = 3

Hệ thống chọn 3 đoạn tài liệu liên quan nhất để đưa vào context của LLM.

## 7. Tiêu chí lựa chọn

Các tiêu chí được xem xét khi lựa chọn vector database:

- Khả năng tìm kiếm vector.
- Tốc độ truy hồi.
- Khả năng lưu metadata.
- Khả năng tích hợp với Python.
- Độ phức tạp khi triển khai.
- Phù hợp với quy mô của đồ án.

## 8. Kết luận

Vector database là thành phần lưu trữ và truy hồi embedding
trong pipeline RAG.

Đối với phạm vi đồ án, FAISS hoặc ChromaDB là lựa chọn phù hợp
để xây dựng baseline trước khi xem xét các giải pháp phức tạp hơn.
