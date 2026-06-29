---
title: "Trustworthiness in Retrieval-Augmented Generation Systems: A Survey"
authors: Zhou, Y., Zhang, W., Shao, J., Liu, Y., Li, X., et al.
year: 2024
venue: arXiv:2409.10102
tags: [literature, rag-evaluation, survey, trustworthiness]
status: unread
url: https://arxiv.org/abs/2409.10102
ref: 22
---

# Trustworthiness in Retrieval-Augmented Generation Systems: A Survey

## Summary
Survey **6 chiều tin cậy** của RAG: **factuality, robustness, fairness, transparency, accountability, privacy**. Đề xuất khung hợp nhất **Trust-RAG Compass** cùng benchmark **TRC Bench** để đánh giá có hệ thống.

## Vai trò trong Capstone
- Tiêu chí phục vụ: **Hallucination (factuality), Source Traceability (transparency/accountability)**.
- Khung lý thuyết cho phần Expected Contribution (answer reliability & traceability).

## Key Contributions
- Hệ thống hóa **6 chiều tin cậy** cho RAG và các mối đe dọa tương ứng.
- Đề xuất **Trust-RAG Compass** + **TRC Bench** làm chuẩn đánh giá thống nhất.

## Methodology
- Review tài liệu; tổng hợp metric/đe dọa theo từng chiều; xây benchmark đối chiếu.

## Results & Findings
- RAG **tăng độ tin cậy** bằng cách neo câu trả lời vào tri thức ngoài & cập nhật → giảm hallucination.
- Nhưng **truy hồi kém hoặc dùng tri thức sai cách vẫn cho output không mong muốn** → cần đo nhiều chiều, không chỉ accuracy.

## Limitations
- Là khảo sát; TRC Bench cần kiểm chứng rộng hơn theo domain.

## Related Works
- [[21 - Niu 2024 - RAGTruth]] · [[07 - Ji 2023 - Hallucination Survey]] · [[23 - Bohnet 2022 - Attributed QA]] · [[_Sources Master List]] · [[Smart Solar Platform - Capstone 2026]]

## My Notes & Critiques
- Dùng 6 chiều này làm khung trình bày "reliability" của custom pipeline trong Discussion.

## Quotes
> "RAG can improve LLM reliability by grounding responses in external and up-to-date knowledge, reducing hallucinations."
> "Unreliable retrieval or improper knowledge utilization may still lead to undesirable outputs."

## References
Zhou, Y., Zhang, W., Shao, J., Liu, Y., Li, X., Jin, J., Qian, H., Liu, Z., Li, C., Zhang, J. C., Dou, Z., Yu, P. S. & Mao, J. (2024). *Trustworthiness in Retrieval-Augmented Generation Systems: A Survey*. arXiv:2409.10102.
