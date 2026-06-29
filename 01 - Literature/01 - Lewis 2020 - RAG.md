---
title: Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks
authors: Lewis, P. et al.
year: 2020
venue: NeurIPS 2020 (pp. 9459-9474)
tags: [literature, rag-foundation]
status: unread
url: https://arxiv.org/abs/2005.11401
ref: 1
---

# Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks

## Summary
Paper gốc định nghĩa khái niệm RAG: kết hợp **bộ nhớ tham số** (mô hình seq2seq đã pre-train) với **bộ nhớ phi tham số** (chỉ mục vector Wikipedia) để giải các tác vụ NLP đòi hỏi nhiều tri thức. Cite **bắt buộc** cho Introduction & Related Works.

## Vai trò trong Capstone
- Tiêu chí phục vụ: **Source Traceability** (tri thức nằm trong nguồn truy hồi được, không "ẩn" trong tham số).
- Nền tảng lý thuyết cho toàn bộ custom RAG pipeline.

## Key Contributions
- Đề xuất kiến trúc RAG hợp nhất retriever (DPR) + generator (BART) huấn luyện end-to-end.
- Hai biến thể: **RAG-Sequence** (dùng cùng một tập passage cho cả câu trả lời) và **RAG-Token** (mỗi token có thể dựa trên passage khác nhau).
- Đạt SOTA trên 3 tác vụ open-domain QA tại thời điểm công bố.
- Sinh văn bản **cụ thể, đa dạng và đúng sự thật hơn** so với baseline chỉ dùng tham số.

## Methodology
- **Retriever:** Dense Passage Retrieval (DPR) — truy hồi top-k passage từ chỉ mục vector Wikipedia (non-parametric memory).
- **Generator:** BART (seq2seq) sinh câu trả lời có điều kiện trên truy vấn + passage.
- Truy hồi được coi như **biến tiềm ẩn** (latent variable), marginalize qua các passage; huấn luyện end-to-end chỉ với giám sát ở đầu ra.

## Results & Findings
- Vượt các kiến trúc retrieve-and-extract chuyên biệt trên open-domain QA (Natural Questions, TriviaQA, WebQuestions...).
- Trên tác vụ sinh (generation), RAG tạo nội dung đúng sự thật và đặc thù hơn baseline parametric-only.

## Limitations
- Provenance (truy vết nguồn ra quyết định) và **cập nhật tri thức thế giới** vẫn là bài toán mở (nêu trực tiếp trong abstract).
- Phụ thuộc chất lượng retriever; chỉ mục Wikipedia cố định tại thời điểm index.

## Related Works
- [[02 - Karpukhin 2020 - Dense Passage Retrieval]] · [[03 - Gao 2024 - RAG Survey]] · [[_Sources Master List]] · [[Smart Solar Platform - Capstone 2026]]

## My Notes & Critiques
- Đây là điểm neo cho luận điểm "RAG tăng tính truy vết & giảm hallucination" trong Research Problem.

## Quotes
> "Their ability to access and precisely manipulate knowledge is still limited, and hence on knowledge-intensive tasks, their performance lags behind task-specific architectures."
> "Providing provenance for their decisions and updating their world knowledge remain open research problems."

## References
Lewis, P., Perez, E., Piktus, A., Petroni, F., Karpukhin, V., Goyal, N., Küttler, H., Lewis, M., Yih, W., Rocktäschel, T., Riedel, S. & Kiela, D. (2020). *Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks*. NeurIPS 2020, 9459–9474. arXiv:2005.11401.
