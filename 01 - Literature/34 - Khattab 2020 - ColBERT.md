---
title: "ColBERT: Efficient and Effective Passage Search via Contextualized Late Interaction over BERT"
authors: Khattab, O. & Zaharia, M.
year: 2020
venue: SIGIR 2020
tags: [literature, retrieval, reranking, foundation]
status: unread
url: https://arxiv.org/abs/2004.12832
ref: 34
---

# ColBERT: Efficient & Effective Passage Search via Late Interaction over BERT

## Summary
Mô hình xếp hạng (ranking) dùng **late interaction** (tương tác trễ — mã hoá query/doc **riêng** rồi mới so khớp chi tiết ở cuối). Nhờ vậy **tính trước vector tài liệu offline** → nhanh hơn cross-encoder **~2 bậc độ lớn** mà vẫn chính xác. Nền tảng cho retriever/reranker hiệu quả.

## Vai trò trong Capstone
- Tiêu chí phục vụ: **Response Time + Accuracy/Relevance** — cân bằng tốc độ và độ chính xác ở khâu truy hồi/rerank.
- Phương án retriever/reranker khả thi cho custom pipeline (giữa dual-encoder nhanh và cross-encoder chính xác).

## Key Contributions
- Kiến trúc **late interaction**: query & doc mã hoá độc lập bằng BERT, so khớp bằng phép tương tác "rẻ mà mạnh" (MaxSim).
- Cho phép **pre-compute** biểu diễn tài liệu → tăng tốc truy vấn; hỗ trợ truy hồi end-to-end qua vector index.

## Methodology
- Mỗi token query so khớp với token doc gần nhất (MaxSim) rồi cộng điểm; tách encode khỏi match nên cache được vector doc.

## Results & Findings
- Nhanh hơn các reranker BERT truyền thống **~2 bậc độ lớn**, độ chính xác cạnh tranh; vừa rerank vừa làm retriever trực tiếp.

## Limitations
- Lưu vector **theo token** tốn bộ nhớ/đĩa hơn embedding 1-vector/đoạn; cần kỹ thuật nén (về sau có ColBERTv2).

## Related Works
- [[02 - Karpukhin 2020 - Dense Passage Retrieval]] · [[31 - Thakur 2025 - FreshStack]] · [[_Sources Master List]] · [[Bảng thuật ngữ (Glossary)]]

## My Notes & Critiques
- Cân nhắc late-interaction (ColBERT) nếu cross-encoder rerank quá chậm cho yêu cầu response time của platform.

## Quotes
> "ColBERT introduces a late interaction architecture that independently encodes the query and the document using BERT and then employs a cheap yet powerful interaction step that models their fine-grained similarity."

## References
Khattab, O. & Zaharia, M. (2020). *ColBERT: Efficient and Effective Passage Search via Contextualized Late Interaction over BERT*. SIGIR 2020. arXiv:2004.12832.
