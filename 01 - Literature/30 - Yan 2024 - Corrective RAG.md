---
title: "Corrective Retrieval Augmented Generation (CRAG)"
authors: Yan, S.-Q., Gu, J.-C., Zhu, Y. & Ling, Z.-H.
year: 2024
venue: arXiv:2401.15884
tags: [literature, rag-architecture, robustness, existing-solution]
status: unread
url: https://arxiv.org/abs/2401.15884
ref: 30
---

# Corrective Retrieval Augmented Generation (CRAG)

## Summary
**CRAG** tăng **robustness** cho RAG khi truy hồi sai: một **retrieval evaluator** nhẹ chấm chất lượng tài liệu → 3 hành động **{Correct, Incorrect, Ambiguous}**; kích hoạt **web search** mở rộng và thuật toán **decompose-then-recompose** để lọc nhiễu, giữ thông tin then chốt. Plug-and-play, ghép được với mọi pipeline RAG.

## Vai trò trong Capstone
- Tiêu chí phục vụ: **Accuracy/Relevance, Hallucination** (tự sửa khi retrieval kém).
- Là **existing solution** song song [[04 - Asai 2023 - Self-RAG]] để benchmark custom pipeline.

## Key Contributions
- **Retrieval evaluator** nhẹ + cơ chế hành động theo độ tin cậy (Correct/Incorrect/Ambiguous).
- Dùng **web search quy mô lớn** bù cho corpus tĩnh/hạn chế.
- **Decompose-then-recompose**: tách rồi ghép lại để tập trung thông tin quan trọng, loại nhiễu.

## Methodology
- Sau truy hồi: evaluator chấm độ liên quan → nếu kém thì tìm web; chạy decompose-then-recompose trước khi đưa vào generator. Mô-đun độc lập, gắn vào RAG có sẵn.

## Results & Findings
- Thí nghiệm trên **4 dataset** (sinh ngắn & dài) cho thấy CRAG **cải thiện đáng kể** hiệu năng các phương pháp RAG nền.

## Limitations
- Phụ thuộc chất lượng evaluator và web search (nhiễu/độ trễ); thêm bước → tăng độ trễ/cost.

## Related Works
- [[04 - Asai 2023 - Self-RAG]] · [[20 - Ru 2024 - RAGChecker]] · [[28 - Edge 2024 - GraphRAG]] · [[_Sources Master List]] · [[Smart Solar Platform - Capstone 2026]]

## My Notes & Critiques
- CRAG + Self-RAG là hai baseline "self-correcting" nên đưa vào so sánh; lưu ý web search ảnh hưởng cost/traceability.

## Quotes
> "A lightweight retrieval evaluator is designed to assess the overall quality of retrieved documents for a query, returning a confidence degree based on which different knowledge retrieval actions can be triggered."
> "CRAG can significantly improve the performance of RAG-based approaches."

## References
Yan, S.-Q., Gu, J.-C., Zhu, Y. & Ling, Z.-H. (2024). *Corrective Retrieval Augmented Generation*. arXiv:2401.15884.
