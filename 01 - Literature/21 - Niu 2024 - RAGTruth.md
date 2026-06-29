---
title: "RAGTruth: A Hallucination Corpus for Developing Trustworthy Retrieval-Augmented Language Models"
authors: Niu, C., Wu, Y., Zhu, J., Xu, S., Shum, K., Zhong, R., Song, J. & Zhang, T.
year: 2024
venue: ACL 2024 (Long Papers)
tags: [literature, hallucination, benchmark, corpus]
status: unread
url: https://arxiv.org/abs/2401.00396
ref: 21
---

# RAGTruth: A Hallucination Corpus for Developing Trustworthy Retrieval-Augmented Language Models

## Summary
Corpus **~18.000 câu trả lời RAG** sinh tự nhiên từ nhiều LLM, **gán nhãn hallucination ở mức từ (word-level) và mức case** kèm cường độ. Cho phép fine-tune model nhỏ phát hiện hallucination **ngang GPT-4 prompt-based**.

## Vai trò trong Capstone
- Tiêu chí phục vụ: **Hallucination rate** — phương pháp/baseline đo lường thực nghiệm chuẩn.
- Có thể dùng để huấn luyện/đánh giá bộ phát hiện hallucination cho custom pipeline.

## Key Contributions
- Corpus hallucination quy mô lớn, **chú thích cấp từ** đầu tiên cho khung RAG chuẩn, đa domain/đa tác vụ.
- Benchmark tần suất hallucination giữa các LLM và đánh giá hiệu quả các phương pháp phát hiện hiện có.
- Chứng minh **fine-tune LLM nhỏ trên RAGTruth** đạt hiệu năng phát hiện cạnh tranh GPT-4 (rẻ hơn).

## Methodology
- Sinh câu trả lời RAG đa dạng → chuyên gia gán nhãn span hallucination + loại + cường độ → dùng làm tập huấn luyện/đánh giá detector.

## Results & Findings
- Dù có RAG, LLM **vẫn đưa ra tuyên bố không được hỗ trợ hoặc mâu thuẫn** với ngữ cảnh truy hồi.
- Detector nhỏ fine-tuned đạt mức cạnh tranh prompt GPT-4 → khả thi về cost.

## Limitations
- Nhãn tiếng Anh, theo tập tác vụ chọn trước; chuyển sang tài liệu/tiếng Việt cần dữ liệu mới.

## Related Works
- [[07 - Ji 2023 - Hallucination Survey]] · [[22 - Zhou 2024 - Trustworthiness in RAG Survey]] · [[20 - Ru 2024 - RAGChecker]] · [[_Sources Master List]] · [[Smart Solar Platform - Capstone 2026]]

## My Notes & Critiques
- Mô hình "fine-tune detector nhỏ" là hướng giảm cost đánh giá hallucination cho capstone.

## Quotes
> "RAGTruth [is] a corpus tailored for analyzing word-level hallucinations in various domains and tasks within the standard RAG frameworks for LLM applications."
> "It is possible to finetune a relatively small LLM and achieve competitive hallucination detection performance compared to GPT-4 prompt-based approaches."

## References
Niu, C., Wu, Y., Zhu, J., Xu, S., Shum, K., Zhong, R., Song, J. & Zhang, T. (2024). *RAGTruth: A Hallucination Corpus for Developing Trustworthy Retrieval-Augmented Language Models*. ACL 2024. arXiv:2401.00396.
