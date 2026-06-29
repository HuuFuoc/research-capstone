---
title: "Model Internals-based Answer Attribution for Trustworthy Retrieval-Augmented Generation (MIRAGE)"
authors: Qi, J., Sarti, G., Fernández, R. & Bisazza, A.
year: 2024
venue: EMNLP 2024 (Main, pp. 6037-6053)
tags: [literature, attribution, source-traceability]
status: unread
url: https://arxiv.org/abs/2406.13663
ref: 24
---

# Model Internals-based Answer Attribution for Trustworthy RAG (MIRAGE)

## Summary
**MIRAGE** — phương pháp plug-and-play dùng **nội tại model + saliency** để phát hiện token câu trả lời nhạy ngữ cảnh và ghép chúng với tài liệu truy hồi đóng góp. Attribution **trung thực hơn self-citation** (vốn hay sai định dạng, bịa nguồn).

## Vai trò trong Capstone
- Tiêu chí phục vụ: **Source Traceability** — kỹ thuật khả thi để hiện trích dẫn nguồn trung thực.
- Lựa chọn kỹ thuật cho phần demo traceability của custom pipeline.

## Key Contributions
- Quy attribution về tài liệu nguồn **dựa trên nội tại model** (không cần LM tự trích dẫn).
- Tương quan cao với attribution của con người trên QA trích đa ngữ; trên QA mở, **chất lượng & hiệu quả ngang self-citation** nhưng kiểm soát mịn hơn.

## Methodology
- Dùng saliency để phát hiện **context-sensitive answer tokens**, ghép với tài liệu truy hồi đóng góp vào dự đoán token đó; cho phép chỉnh tham số attribution.

## Results & Findings
- Tránh được lỗi self-citation (sai format, nguồn không tồn tại); attribution trung thực với cách model thực sự dùng ngữ cảnh.

## Limitations
- Cần truy cập **nội tại model** (khó với API đóng); chi phí tính saliency.

## Related Works
- [[23 - Bohnet 2022 - Attributed QA]] · [[04 - Asai 2023 - Self-RAG]] · [[22 - Zhou 2024 - Trustworthiness in RAG Survey]] · [[_Sources Master List]] · [[Smart Solar Platform - Capstone 2026]]

## My Notes & Critiques
- Lưu ý: cần model mở để dùng MIRAGE; nếu dùng LLM API đóng thì phải dựa self-citation + kiểm chứng (xem [[23 - Bohnet 2022 - Attributed QA]]).

## Quotes
> "Self-citing LLMs often struggle to match the required format, refer to non-existent sources, and fail to faithfully reflect LLMs' context usage."
> "MIRAGE detects context-sensitive answer tokens and pairs them with retrieved documents contributing to their prediction via saliency methods."

## References
Qi, J., Sarti, G., Fernández, R. & Bisazza, A. (2024). *Model Internals-based Answer Attribution for Trustworthy Retrieval-Augmented Generation*. EMNLP 2024, 6037–6053. arXiv:2406.13663.
