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
