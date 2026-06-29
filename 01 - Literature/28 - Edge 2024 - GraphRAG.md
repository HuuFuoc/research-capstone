---
title: "From Local to Global: A Graph RAG Approach to Query-Focused Summarization"
authors: Edge, D., Trinh, H., Cheng, N., Bradley, J., Chao, A., Mody, A., Truitt, S., Metropolitansky, D., Ness, R. O. & Larson, J.
year: 2024
venue: arXiv:2404.16130 (Microsoft Research)
tags: [literature, rag-architecture, graphrag, existing-solution]
status: unread
url: https://arxiv.org/abs/2404.16130
ref: 28
---

# From Local to Global: A Graph RAG Approach to Query-Focused Summarization (GraphRAG)

## Summary
**GraphRAG** (Microsoft): RAG thường **thất bại với câu hỏi toàn cục** ("Các chủ đề chính của bộ dữ liệu là gì?") vì đó là query-focused summarization. GraphRAG dùng LLM xây **knowledge graph thực thể** + **tóm tắt cộng đồng (community summaries)**, rồi tổng hợp partial response → câu trả lời cuối, mở rộng theo cả độ tổng quát của câu hỏi lẫn quy mô văn bản.

## Vai trò trong Capstone
- Tiêu chí phục vụ: **Accuracy/Relevance** cho câu hỏi tổng hợp toàn bộ tài liệu dự án.
- Là **existing solution** (kiến trúc nâng cao) để đối chiếu với custom pipeline.

## Key Contributions
- Kết hợp điểm mạnh RAG (truy hồi) và QFS (tóm tắt toàn cục) — **scale tới corpus ~1 triệu token**.
- Quy trình 2 giai đoạn: (1) trích **entity knowledge graph**; (2) **pregenerate community summaries** cho cụm thực thể liên quan.
- Sinh câu trả lời map-reduce: partial response từ mỗi community summary → tổng hợp cuối.

## Methodology
- LLM xây graph index; phát hiện cộng đồng (community detection) trên graph; tóm tắt cộng đồng; với mỗi câu hỏi → tổng hợp phản hồi từ các community summary liên quan.

## Results & Findings
- Trên câu hỏi **sensemaking toàn cục** (dataset cỡ triệu token), GraphRAG cải thiện **đáng kể về tính bao quát (comprehensiveness) và đa dạng (diversity)** so với RAG vector baseline.

## Limitations
- Chi phí xây graph + tóm tắt cộng đồng (nhiều lần gọi LLM) → tốn kém/độ trễ cao hơn naive RAG; phù hợp câu hỏi tổng hợp hơn là tra cứu sự kiện đơn lẻ.

## Related Works
- [[03 - Gao 2024 - RAG Survey]] · [[25 - Li 2024 - RAG vs Long-Context]] · [[29 - Sarthi 2024 - RAPTOR]] · [[_Sources Master List]] · [[Smart Solar Platform - Capstone 2026]]

## My Notes & Critiques
- Cân nhắc GraphRAG cho truy vấn "tổng hợp toàn bộ tài liệu dự án"; đo cả cost vì chi phí index cao.

## Quotes
> "RAG fails on global questions directed at an entire text corpus, such as 'What are the main themes in the dataset?', since this is inherently a query-focused summarization task."
> "GraphRAG leads to substantial improvements over a conventional RAG baseline for both the comprehensiveness and diversity of generated answers."

## References
Edge, D., Trinh, H., Cheng, N., Bradley, J., Chao, A., Mody, A., Truitt, S., Metropolitansky, D., Ness, R. O. & Larson, J. (2024). *From Local to Global: A Graph RAG Approach to Query-Focused Summarization*. arXiv:2404.16130.
