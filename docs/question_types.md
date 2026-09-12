# Phân loại các dạng câu hỏi của sinh viên năm nhất

## 1. Mục đích

Phân loại các dạng câu hỏi thường gặp giúp xác định cách chatbot cần trả lời
và hỗ trợ thiết kế bộ dữ liệu kiểm thử cho hệ thống.

## 2. Các dạng câu hỏi chính

### 2.1. Câu hỏi định nghĩa khái niệm

Ví dụ:
- List trong Python là gì?
- Biến là gì?
- DataFrame là gì?

Yêu cầu trả lời:
- Ngắn gọn.
- Dễ hiểu.
- Bám sát định nghĩa trong tài liệu.

### 2.2. Câu hỏi giải thích

Ví dụ:
- Vì sao cần chuẩn hóa dữ liệu?
- Vì sao phải chia dữ liệu thành tập train và test?

Yêu cầu trả lời:
- Giải thích từng bước.
- Có ví dụ nếu tài liệu cho phép.

### 2.3. Câu hỏi so sánh

Ví dụ:
- List và Tuple khác nhau như thế nào?
- CSV và Excel khác nhau như thế nào?

Yêu cầu trả lời:
- Nêu điểm giống.
- Nêu điểm khác.
- Có thể trình bày dạng bảng.

### 2.4. Câu hỏi về công thức

Ví dụ:
- Công thức tính trung bình là gì?
- Standard deviation được tính như thế nào?

Yêu cầu trả lời:
- Trình bày công thức rõ ràng.
- Giải thích ý nghĩa các thành phần.

### 2.5. Câu hỏi về mã nguồn

Ví dụ:
- Đoạn code này có tác dụng gì?
- Hàm read_csv() dùng để làm gì?

Yêu cầu trả lời:
- Giải thích chức năng.
- Phân tích từng dòng nếu cần.

### 2.6. Câu hỏi truy xuất thông tin cụ thể

Ví dụ:
- Trong tài liệu có nói gì về NumPy?
- Khái niệm dữ liệu định lượng nằm ở trang nào?

Yêu cầu trả lời:
- Trích dẫn tên tài liệu.
- Chỉ rõ số trang hoặc vị trí nguồn.

## 3. Kết luận

Các dạng câu hỏi trên sẽ được sử dụng để xây dựng bộ câu hỏi kiểm thử
và thiết kế cách phản hồi của chatbot trong các giai đoạn tiếp theo.
