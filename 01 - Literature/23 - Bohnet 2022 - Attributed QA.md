---
title: "Attributed Question Answering: Evaluation and Modeling for Attributed Large Language Models"
authors: Bohnet, B., Tran, V. Q., Verga, P., Aharoni, R., Andor, D., et al.
year: 2022
venue: arXiv:2212.08037 (Google Research)
tags: [literature, attribution, source-traceability, evaluation]
status: unread
url: https://arxiv.org/abs/2212.08037
ref: 23
---

# Attributed Question Answering: Evaluation and Modeling for Attributed Large Language Models

## Summary
Hình thức hóa bài toán **Attributed QA** — bước đầu cho "attributed LLMs": câu trả lời phải **quy được về nguồn xác định**. Đề xuất khung đánh giá tái lập được, lấy nhãn người làm chuẩn vàng và một **metric tự động tương quan** để phát triển. Định nghĩa metric **AIS** (Attributable to Identified Sources).

## Vai trò trong Capstone
- Tiêu chí phục vụ: **Source Traceability** — metric gốc (AIS) để đo độ truy vết nguồn.
- Cơ sở định nghĩa cách đo "source traceability" trong Research Question.

## Key Contributions
- Định nghĩa & nghiên cứu **Attributed QA**; khung đánh giá **tái lập được**, benchmark nhiều kiến trúc.
- Trả lời 2 câu hỏi cốt lõi: **đo attribution thế nào** và **SOTA đạt mức nào**; gợi mở cách **xây LLM có attribution**.

## Methodology
- Nhãn người (AIS) làm gold; dùng metric tự động tương quan để phát triển; so sánh các kiến trúc (retrieve-then-read, post-hoc, v.v.).

## Results & Findings
- Ngay hệ **retrieve-then-read tốt nhất chỉ đạt ~65.5% AIS** → attribution còn xa hoàn hảo.
- Correctness ≠ attribution: câu trả lời có thể đúng nhưng không quy được về nguồn (và ngược lại).

## Limitations
- Tập trung QA dạng trích; metric AIS dựa nhãn người tốn kém.

## Related Works
- [[24 - Qi 2024 - MIRAGE Answer Attribution]] · [[01 - Lewis 2020 - RAG]] · [[22 - Zhou 2024 - Trustworthiness in RAG Survey]] · [[_Sources Master List]] · [[Smart Solar Platform - Capstone 2026]]

## My Notes & Critiques
- AIS là metric chuẩn để báo cáo "source traceability" của custom pipeline; nêu rõ correctness ≠ attribution khi phân tích.

## Quotes
> "We believe the ability of an LLM to attribute the text that it generates is likely to be crucial in this setting."
> "We formulate and study Attributed QA as a key first step in the development of attributed LLMs."

## References
Bohnet, B., Tran, V. Q., Verga, P., Aharoni, R., Andor, D., et al. (2022). *Attributed Question Answering: Evaluation and Modeling for Attributed Large Language Models*. arXiv:2212.08037.
