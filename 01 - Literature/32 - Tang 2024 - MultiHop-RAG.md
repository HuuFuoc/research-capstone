---
title: "MultiHop-RAG: Benchmarking Retrieval-Augmented Generation for Multi-Hop Queries"
authors: Tang, Y. & Yang, Y.
year: 2024
venue: arXiv:2401.15391
tags: [literature, rag-evaluation, benchmark, multi-hop]
status: unread
url: https://arxiv.org/abs/2401.15391
ref: 32
---

# MultiHop-RAG: Benchmarking RAG for Multi-Hop Queries

## Summary
Benchmark cho **câu hỏi multi-hop** (cần ghép nhiều mẩu bằng chứng + nhiều bước suy luận mới trả lời được). Chỉ ra RAG hiện tại **làm chưa tốt** loại câu hỏi này — cả ở khâu truy hồi lẫn khâu suy luận.

## Vai trò trong Capstone
- Tiêu chí phục vụ: **Accuracy/Relevance** cho câu hỏi phức tạp (vd. tổng hợp từ nhiều requirement/business rule).
- Bộ test để kiểm pipeline tùy chỉnh trên truy vấn khó (không chỉ câu hỏi đơn giản 1 đoạn).

## Key Contributions
- Xây **MultiHop-RAG**: knowledge base từ tin tức tiếng Anh + câu hỏi multi-hop + đáp án chuẩn + bằng chứng hỗ trợ.
- Định nghĩa các **kiểu truy vấn multi-hop** để đo khả năng *ghép bằng chứng* (evidence chaining).

## Methodology
- So sánh nhiều embedding model ở khâu truy hồi; đánh giá các LLM mạnh (GPT-4, PaLM, Llama2-70B) ở khâu trả lời khi đã có bằng chứng.

## Results & Findings
- **RAG hiện tại truy hồi & trả lời multi-hop chưa đạt** — ngay cả khi cấp sẵn bằng chứng, LLM SOTA vẫn chật vật suy luận nhiều bước.
- → Cần kỹ thuật truy hồi/suy luận tốt hơn cho câu hỏi tổng hợp.

## Limitations
- Domain tin tức tiếng Anh; loại multi-hop theo thiết kế bộ dữ liệu, có thể khác đặc thù tài liệu dự án.

## Related Works
- [[31 - Thakur 2025 - FreshStack]] · [[28 - Edge 2024 - GraphRAG]] · [[29 - Sarthi 2024 - RAPTOR]] · [[_Sources Master List]] · [[Bảng thuật ngữ (Glossary)]]

## My Notes & Critiques
- Nếu người dùng hỏi câu tổng hợp (nhiều business rule), cân nhắc GraphRAG/RAPTOR; dùng MultiHop-RAG làm phép thử.

## Quotes
> "Existing RAG systems are inadequate in answering multi-hop queries, which require retrieving and reasoning over multiple pieces of supporting evidence."

## References
Tang, Y. & Yang, Y. (2024). *MultiHop-RAG: Benchmarking Retrieval-Augmented Generation for Multi-Hop Queries*. arXiv:2401.15391.
