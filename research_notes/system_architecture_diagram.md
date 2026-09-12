# Sơ đồ kiến trúc hệ thống chatbot RAG

## 1. Giai đoạn xây dựng kho tri thức

```mermaid
flowchart LR
    A[PDF / DOCX] --> B[Document Loader]
    B --> C[Text Extraction]
    C --> D[Text Cleaning]
    D --> E[Chunking]
    E --> F[Embedding Model]
    F --> G[Vector Database]

    G --> H[(Vector + Metadata)]
## 2. Giai đoạn hỏi đáp

```mermaid
flowchart LR
    A[User Question] --> B[Query Embedding]
    B --> C[Retriever]
    C --> D[Top-k Relevant Chunks]
    D --> E[Prompt + Context]
    E --> F[LLM]
    F --> G[Answer + Citation]
