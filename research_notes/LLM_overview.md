# Tổng quan về Large Language Model (LLM)

## 1. Khái niệm

Large Language Model (LLM) là mô hình ngôn ngữ có kích thước lớn,
được huấn luyện trên lượng dữ liệu văn bản lớn để học cách biểu diễn
và sinh ngôn ngữ tự nhiên.

LLM có thể thực hiện nhiều nhiệm vụ như:
- Trả lời câu hỏi.
- Tóm tắt văn bản.
- Dịch ngôn ngữ.
- Sinh nội dung.
- Hỗ trợ lập trình.
- Phân tích và giải thích văn bản.

## 2. Vai trò của LLM trong đề tài

Trong hệ thống chatbot hỏi đáp tài liệu, LLM đóng vai trò sinh câu trả lời
dựa trên những đoạn thông tin được truy hồi từ tài liệu học tập.

Quy trình cơ bản:

Câu hỏi người dùng
→ Truy hồi nội dung liên quan
→ Đưa ngữ cảnh vào LLM
→ Sinh câu trả lời
→ Trả câu trả lời kèm nguồn

## 3. Hạn chế khi sử dụng LLM trực tiếp

Nếu chỉ sử dụng LLM mà không cung cấp tài liệu làm ngữ cảnh,
một số vấn đề có thể xảy ra:

- Câu trả lời không bám sát giáo trình.
- Có thể sinh thông tin không chính xác.
- Khó xác định nguồn của câu trả lời.
- Nội dung trả lời có thể khác với kiến thức được trình bày trong môn học.

Hiện tượng mô hình sinh ra thông tin không có căn cứ được gọi là
hallucination.

## 4. LLM kết hợp với RAG

Để giảm hallucination và tăng khả năng kiểm chứng,
đề tài sử dụng LLM kết hợp với Retrieval-Augmented Generation (RAG).

RAG cung cấp cho LLM các đoạn nội dung liên quan lấy từ tài liệu học tập
trước khi mô hình sinh câu trả lời.

Lợi ích:
- Câu trả lời bám sát tài liệu.
- Có thể cung cấp trích dẫn nguồn.
- Giảm khả năng sinh thông tin không có căn cứ.
- Có thể cập nhật kiến thức bằng cách bổ sung tài liệu mới.

## 5. Mô hình dự kiến sử dụng

Trong giai đoạn thử nghiệm có thể sử dụng:

- GPT thông qua API.
- Gemini thông qua API.
- Qwen hoặc mô hình mã nguồn mở nếu cần thử nghiệm cục bộ.

Đề tài không huấn luyện LLM từ đầu mà sử dụng các mô hình đã được huấn luyện sẵn.

## 6. Kết luận

LLM là thành phần sinh câu trả lời trong hệ thống chatbot.
Trong đề tài, LLM được kết hợp với RAG để câu trả lời dựa trên nội dung
tài liệu học tập thay vì chỉ dựa vào kiến thức nội tại của mô hình.
