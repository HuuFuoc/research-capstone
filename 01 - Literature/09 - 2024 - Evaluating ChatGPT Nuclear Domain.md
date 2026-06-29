---
title: "Evaluating ChatGPT on Nuclear Domain-Specific Data"
authors: Anwar, M., de Costa, M., Hammad, I. & Lau, D.
year: 2024
venue: arXiv:2409.00090
tags: [literature, rag-evaluation, case-study, domain-specific]
status: unread
url: https://arxiv.org/abs/2409.00090
ref: 9
---

# Evaluating ChatGPT on Nuclear Domain-Specific Data

## Summary
Case study **so sánh trực tiếp plain LLM (ChatGPT) vs RAG** trên hỏi–đáp dữ liệu chuyên ngành hạt nhân; đánh giá bằng **cả con người lẫn LLM**. Mẫu hình methodology rất sát đề tài (custom RAG vs giải pháp sẵn có trên tài liệu chuyên ngành).

## Vai trò trong Capstone
- Tiêu chí phục vụ: **Accuracy, Hallucination, Cost Efficiency** — methodology so sánh RAG vs plain LLM.
- Tham chiếu thiết kế thí nghiệm "RAG vs non-RAG" cho domain hẹp.

## Key Contributions
- Thực chứng RAG **giảm hallucination & tăng độ chính xác** trên domain hạt nhân so với ChatGPT thuần.
- Đề xuất quy trình đánh giá **dual** (human + LLM-as-judge) cho QA chuyên ngành.

## Methodology
- Hai cấu hình: (1) ChatGPT trả lời trực tiếp; (2) ChatGPT + RAG (truy hồi từ tài liệu hạt nhân).
- Chấm điểm song song bằng con người và bằng LLM trên cùng tập câu hỏi.

## Results & Findings
- Tích hợp RAG cho **câu trả lời chính xác và phù hợp ngữ cảnh hơn** với truy vấn chuyên ngành.
- Khẳng định LLM thuần vẫn "prone to generating incorrect or 'hallucinated' information".

## Limitations
- Domain hẹp (hạt nhân); cỡ mẫu câu hỏi và mô hình giới hạn → tổng quát hóa cần thận trọng.
- Dùng ChatGPT đóng → khó tách riêng đóng góp của retriever vs generator.

## Related Works
- [[26 - 2025 - RAG in Industry Interview Study]] · [[06 - Es 2024 - RAGAs]] · [[01 - Lewis 2020 - RAG]] · [[_Sources Master List]] · [[Smart Solar Platform - Capstone 2026]]

## My Notes & Critiques
- Khung "human + LLM judge" ở đây có thể tái dùng cho phần đánh giá của capstone.

## Quotes
> "[LLMs] remain prone to generating incorrect or 'hallucinated' information."
> "Integrating RAG with ChatGPT yields improvement in performance ... particularly in generating more accurate and contextually appropriate responses for nuclear domain-specific queries."

## References
Anwar, M., de Costa, M., Hammad, I. & Lau, D. (2024). *Evaluating ChatGPT on Nuclear Domain-Specific Data*. arXiv:2409.00090.
