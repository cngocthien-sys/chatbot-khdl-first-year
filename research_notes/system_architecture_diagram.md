# Sơ đồ kiến trúc hệ thống chatbot RAG

## 1. Giai đoạn xây dựng kho tri thức

```mermaid
flowchart LR
    A["PDF / DOCX"] --> B["Document Loader"]
    B --> C["Text Extraction"]
    C --> D["Text Cleaning"]
    D --> E["Chunking"]
    E --> F["Embedding Model"]
    F --> G["Vector Database"]
    G --> H["Vector + Metadata"]
```

## 2. Giai đoạn hỏi đáp

```mermaid
flowchart LR
    A["User Question"] --> B["Query Embedding"]
    B --> C["Retriever"]
    C --> D["Top-k Relevant Chunks"]
    D --> E["Prompt + Context"]
    E --> F["LLM"]
    F --> G["Answer + Citation"]
```

## 3. Kiến trúc tổng thể

```mermaid
flowchart TD
    A["PDF / DOCX"] --> B["Document Loader"]
    B --> C["Text Extraction"]
    C --> D["Text Cleaning"]
    D --> E["Chunking"]
    E --> F["Embedding Model"]
    F --> G["Vector Database"]

    H["Sinh viên"] --> I["Câu hỏi"]
    I --> J["Query Embedding"]
    J --> K["Retriever"]

    G --> K
    K --> L["Top-k Relevant Chunks"]
    L --> M["Prompt + Context"]
    M --> N["LLM"]
    N --> O["Câu trả lời"]
    O --> P["Trích dẫn tài liệu và số trang"]
```

## 4. Mô tả

Hệ thống gồm hai luồng chính:

- Luồng xử lý tài liệu để xây dựng kho tri thức.
- Luồng hỏi đáp để truy hồi nội dung liên quan và cung cấp cho LLM.

Vector Database lưu embedding của các chunk cùng metadata như tên tài liệu và số trang.

Retriever tìm các chunk liên quan nhất đến câu hỏi của sinh viên.

LLM sử dụng câu hỏi và context được truy hồi để sinh câu trả lời kèm trích dẫn nguồn.
