# Ghi chú nghiên cứu về Embedding

## 1. Khái niệm

Embedding là phương pháp biểu diễn dữ liệu văn bản dưới dạng vector số.

Mỗi câu, đoạn văn hoặc tài liệu được chuyển thành một vector nhiều chiều.
Các văn bản có ý nghĩa gần nhau thường có vector nằm gần nhau trong không gian vector.

Ví dụ:

"Machine Learning là gì?"
và
"Khái niệm học máy"

có nội dung gần nhau nên embedding của chúng có xu hướng tương đồng.

## 2. Vai trò của Embedding trong hệ thống RAG

Trong hệ thống RAG, embedding được sử dụng để:

- Biểu diễn các đoạn tài liệu thành vector.
- Biểu diễn câu hỏi của người dùng thành vector.
- So sánh mức độ tương đồng giữa câu hỏi và các đoạn tài liệu.
- Tìm ra các đoạn nội dung liên quan nhất để đưa vào LLM.

Quy trình:

Document Chunk
→ Embedding Model
→ Vector

User Question
→ Embedding Model
→ Query Vector

Query Vector
→ Similarity Search
→ Relevant Chunks

## 3. Tại sao cần Embedding

Nếu chỉ tìm kiếm bằng từ khóa, hệ thống có thể bỏ sót các câu có cùng ý nghĩa
nhưng sử dụng từ khác nhau.

Ví dụ:

Câu hỏi:
"Học máy là gì?"

Tài liệu:
"Machine Learning là một lĩnh vực..."

Tìm kiếm từ khóa đơn giản có thể không nhận ra mối liên hệ giữa
"Học máy" và "Machine Learning".

Embedding giúp tìm kiếm dựa trên ngữ nghĩa thay vì chỉ dựa trên từ khóa.

## 4. Mô hình embedding dự kiến thử nghiệm

Trong đề tài, nhóm dự kiến khảo sát một số mô hình hỗ trợ tiếng Việt.

### multilingual-e5-base

Đây là mô hình embedding đa ngôn ngữ,
có thể xử lý tiếng Việt và tiếng Anh.

Ưu điểm:
- Hỗ trợ nhiều ngôn ngữ.
- Phù hợp với tài liệu song ngữ Việt - Anh.
- Được sử dụng phổ biến trong các bài toán semantic search.

### Vietnamese-bi-encoder

Đây là mô hình embedding được thiết kế cho tiếng Việt.

Ưu điểm:
- Tập trung vào dữ liệu tiếng Việt.
- Có thể phù hợp với các tài liệu học tập chủ yếu bằng tiếng Việt.

## 5. Cách đánh giá mô hình embedding

Các mô hình embedding sẽ được so sánh trên cùng bộ câu hỏi kiểm thử.

Một số tiêu chí dự kiến:

- Khả năng truy hồi đúng đoạn chứa câu trả lời.
- Recall@k.
- Thời gian sinh embedding.
- Kích thước vector.
- Khả năng xử lý tài liệu tiếng Việt và tiếng Anh.

## 6. Similarity Search

Sau khi có embedding của câu hỏi,
hệ thống tính độ tương đồng giữa vector câu hỏi và các vector tài liệu.

Một phương pháp phổ biến là cosine similarity.

Giá trị similarity càng cao thì hai vector càng gần nhau về mặt ngữ nghĩa.

Các đoạn có điểm cao nhất sẽ được chọn làm top-k context.

Ví dụ:

top-k = 3

Hệ thống chọn 3 chunk có độ tương đồng cao nhất với câu hỏi.

## 7. Hướng thử nghiệm

Trong các tuần tiếp theo, nhóm dự kiến:

- So sánh multilingual-e5-base và Vietnamese-bi-encoder.
- Thử các kích thước chunk khác nhau.
- Thử nhiều giá trị top-k.
- Đo Recall@k trên bộ câu hỏi kiểm thử.
- Chọn mô hình embedding phù hợp nhất cho hệ thống.

## 8. Kết luận

Embedding là thành phần quan trọng của module truy hồi trong hệ thống RAG.

Chất lượng embedding ảnh hưởng trực tiếp đến khả năng tìm đúng nội dung
liên quan trong tài liệu, từ đó ảnh hưởng đến chất lượng câu trả lời của chatbot.
