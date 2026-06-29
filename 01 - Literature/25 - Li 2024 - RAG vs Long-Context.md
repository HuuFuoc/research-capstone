---
title: "Retrieval Augmented Generation or Long-Context LLMs? A Comprehensive Study and Hybrid Approach"
authors: Li, Z., Li, C., Zhang, M., Mei, Q. & Bendersky, M.
year: 2024
venue: EMNLP 2024 (Industry Track)
tags: [literature, rag-comparison, cost, latency]
status: unread
url: https://arxiv.org/abs/2407.16833
ref: 25
---

# Retrieval Augmented Generation or Long-Context LLMs? A Comprehensive Study and Hybrid Approach

## Summary
So sánh toàn diện **RAG vs Long-Context (LC) LLM** (Gemini-1.5, GPT-4): LC **vượt accuracy** khi đủ tài nguyên, nhưng **RAG rẻ hơn nhiều**. Đề xuất **Self-Route** — định tuyến truy vấn sang RAG hoặc LC dựa trên tự phản ánh của model để đạt accuracy gần LC với chi phí thấp.

## Vai trò trong Capstone
- Tiêu chí phục vụ: **Cost, Response Time, Accuracy** — đây là "existing solution" (LC) để đối chiếu với custom RAG pipeline.
- Dữ liệu định lượng cho lập luận chi phí/độ trễ.

## Key Contributions
- So sánh hệ thống RAG vs LC trên nhiều dataset/độ dài.
- Đề xuất **Self-Route**: route động RAG↔LC bằng self-reflection → giảm mạnh chi phí tính toán.

## Methodology
- Đánh giá cùng tập câu hỏi với RAG và LC; phân tích đánh đổi accuracy–cost; xây cơ chế route dựa khả năng tự đánh giá của LLM.

## Results & Findings
- **LC nhất quán vượt RAG về accuracy trung bình** khi đủ tài nguyên (context window lớn).
- **RAG giữ lợi thế chi phí rõ rệt**; Self-Route đạt accuracy ~ LC nhưng tốn ít hơn nhiều.

## Limitations
- Phụ thuộc model LC mạnh & cửa sổ ngữ cảnh lớn; kết luận có thể đổi khi giá token/độ trễ LC giảm.

## Related Works
- [[04 - Asai 2023 - Self-RAG]] · [[03 - Gao 2024 - RAG Survey]] · [[28 - Edge 2024 - GraphRAG]] · [[_Sources Master List]] · [[Smart Solar Platform - Capstone 2026]]

## My Notes & Critiques
- Khung cost–accuracy ở đây là trục so sánh chính giữa custom RAG và giải pháp long-context/LLM thuần.

## Quotes
> "When resourced sufficiently, LC consistently outperforms RAG in terms of average performance. However, RAG's significantly lower cost remains a distinct advantage."

## References
Li, Z., Li, C., Zhang, M., Mei, Q. & Bendersky, M. (2024). *Retrieval Augmented Generation or Long-Context LLMs? A Comprehensive Study and Hybrid Approach*. EMNLP 2024 (Industry Track). arXiv:2407.16833.
