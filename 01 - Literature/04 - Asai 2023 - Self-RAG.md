---
title: "Self-RAG: Learning to Retrieve, Generate, and Critique through Self-Reflection"
authors: Asai, A. et al.
year: 2023
venue: ICLR 2024 (arXiv:2310.11511)
tags: [literature, rag-foundation, baseline]
status: unread
url: https://arxiv.org/abs/2310.11511
ref: 4
---

# Self-RAG: Learning to Retrieve, Generate, and Critique through Self-Reflection

## Summary
Khung **Self-Reflective RAG**: huấn luyện một LM tự **quyết định khi nào cần truy hồi**, rồi tự **phê bình** passage truy hồi và phần sinh của chính nó bằng các **reflection token** đặc biệt. Là *existing solution* mạnh để dùng làm **baseline** so sánh với custom pipeline.

## Vai trò trong Capstone
- Tiêu chí phục vụ: **Hallucination Reduction**, **Custom vs. Existing RAG**.
- Baseline tiên tiến (adaptive retrieval + self-critique) để đối chiếu chất lượng/độ truy vết.

## Key Contributions
- **Adaptive retrieval on-demand**: chỉ truy hồi khi cần, tránh nhồi cố định k passage gây nhiễu.
- Giới thiệu **reflection tokens** cho phép mô hình tự đánh giá độ liên quan của passage và mức được hỗ trợ (supported) của câu trả lời.
- **Điều khiển được lúc suy luận** (controllable inference): điều chỉnh hành vi theo yêu cầu tác vụ.
- Một mô hình hợp nhất, không cần module critique riêng.

## Methodology
- LM sinh xen kẽ token nội dung và reflection token (`Retrieve?`, `IsRelevant`, `IsSupported`, `IsUseful`).
- Truy hồi kích hoạt động; mỗi đoạn sinh được chấm điểm để chọn ứng viên tốt nhất (segment-level beam).
- Reflection token cho phép cân bằng tính sáng tạo vs. bám nguồn ngay khi inference.

## Results & Findings
- Self-RAG (7B & 13B) **vượt ChatGPT và Llama2-chat tăng cường truy hồi** trên open-domain QA, reasoning, fact verification.
- Cải thiện đáng kể **factuality và độ chính xác trích dẫn** cho sinh văn bản dài.

## Limitations
- Cần dữ liệu huấn luyện có reflection token (chưng cất từ GPT-4) → chi phí thiết lập.
- Chất lượng tự phê bình phụ thuộc mô hình critic; có thể sai khi nguồn mâu thuẫn.

## Related Works
- [[01 - Lewis 2020 - RAG]] · [[30 - Yan 2024 - Corrective RAG]] · [[24 - Qi 2024 - MIRAGE Answer Attribution]] · [[_Sources Master List]] · [[Smart Solar Platform - Capstone 2026]]

## My Notes & Critiques
- So sánh custom pipeline vs Self-RAG (và CRAG) là trục chính trả lời Research Question về "existing vs custom".

## Quotes
> "Indiscriminately retrieving and incorporating a fixed number of retrieved passages ... diminishes LM versatility or can lead to unhelpful response generation."
> "Generating reflection tokens makes the LM controllable during the inference phase, enabling it to tailor its behavior to diverse task requirements."

## References
Asai, A., Wu, Z., Wang, Y., Sil, A. & Hajishirzi, H. (2024). *Self-RAG: Learning to Retrieve, Generate, and Critique through Self-Reflection*. ICLR 2024. arXiv:2310.11511.
