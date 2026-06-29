---
title: "Vietnamese Legal Information Retrieval in Question-Answering System"
authors: Nguyen Ba, T., Doan The, V., Pham Quang, T. & Tran Van, T.
year: 2024
venue: arXiv:2409.13699 (HUST IT4772E)
tags: [literature, rag, vietnamese, domain-specific, retrieval, reranking]
status: unread
url: https://arxiv.org/abs/2409.13699
ref: 27
---

# Vietnamese Legal Information Retrieval in Question-Answering System

## Summary
RAG cho **QA pháp luật tiếng Việt**: xử lý các thách thức đặc thù tiếng Việt (token dài, ensemble thiếu ổn định) bằng 3 cải tiến — **xử lý dữ liệu** vượt giới hạn embedding, **RRF chuẩn hóa thứ tự** (kết hợp keyword + vector), và **re-rank bằng Active Retrieval** thay cross-encoder.

## Vai trò trong Capstone
- Tiêu chí phục vụ: **Accuracy/Relevance, Retrieval** trong ngữ cảnh **tiếng Việt** (embedding & chunking tiếng Việt).
- Tham khảo kỹ thuật xử lý tài liệu tiếng Việt + reranking cho custom pipeline.

## Key Contributions
- Quy trình xử lý dữ liệu tiếng Việt khắc phục giới hạn của embedding model (token quá dài).
- **Reciprocal Rank Fusion chuẩn hóa thứ tự** để hợp nhất kết quả keyword + vector ổn định hơn.
- **Active Retrieval re-ranking** — đề xuất như một phương pháp re-rank thay cross-encoder truyền thống.

## Methodology
- Pipeline RAG: semantic (dense) + keyword search → RRF chuẩn hóa → re-rank Active Retrieval → đưa vào LLM; chú trọng **thứ tự tài liệu tham chiếu** ảnh hưởng độ chính xác câu trả lời.

## Results & Findings
- Tích hợp ba kỹ thuật vào hệ QID hoàn chỉnh giúp **tăng đáng kể hiệu năng & độ tin cậy** (báo cáo định tính; số liệu chi tiết trong bản full).

## Limitations
- Báo cáo kỹ thuật (report); thiếu số liệu định lượng công khai trong abstract; gắn domain pháp luật.

## Related Works
- [[02 - Karpukhin 2020 - Dense Passage Retrieval]] · [[08 - 2025 - Document Chunking Strategies]] · [[18 - Friel 2024 - RAGBench]] · [[_Sources Master List]] · [[Smart Solar Platform - Capstone 2026]]

## My Notes & Critiques
- Rất sát nếu tài liệu dự án bằng tiếng Việt: tham khảo cách xử lý token dài + hybrid RRF + reranking.

## Quotes
> "RAG has gained significant recognition for enhancing the capabilities of large language models by mitigating hallucination issues in QA systems, which is particularly beneficial in the legal domain."
> "A critical issue often overlooked is the ordering of final relevant documents used as reference to ensure answer accuracy."

## References
Nguyen Ba, T., Doan The, V., Pham Quang, T. & Tran Van, T. (2024). *Vietnamese Legal Information Retrieval in Question-Answering System*. arXiv:2409.13699.
