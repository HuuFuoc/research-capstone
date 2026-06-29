---
title: Dense Passage Retrieval for Open-Domain Question Answering
authors: Karpukhin, V. et al.
year: 2020
venue: EMNLP 2020 (pp. 6769-6781)
tags: [literature, rag-foundation]
status: unread
url: https://aclanthology.org/2020.emnlp-main.550
ref: 2
---

# Dense Passage Retrieval for Open-Domain Question Answering

## Summary
Chứng minh truy hồi passage có thể thực hiện **chỉ bằng biểu diễn dày (dense embeddings)** học từ một lượng nhỏ cặp câu hỏi–passage qua khung **dual-encoder**, vượt xa BM25/TF-IDF truyền thống. Nền tảng cho retriever của mọi pipeline RAG.

## Vai trò trong Capstone
- Hiểu cơ chế Dense Retrieval & dual-encoder cho retriever của custom pipeline.
- Cơ sở để biện minh lựa chọn embedding + vector search (so với keyword/BM25).

## Key Contributions
- Cho thấy dense retrieval học được vượt trội phương pháp sparse (TF-IDF/BM25) mà không cần pretraining bổ sung nặng nề.
- Thiết lập SOTA mới cho nhiều benchmark open-domain QA khi ghép với reader.

## Methodology
- **Dual-encoder BERT:** một encoder cho câu hỏi, một cho passage; điểm liên quan = tích vô hướng của hai vector.
- Huấn luyện với **in-batch negatives** (dùng passage của câu hỏi khác trong batch làm negative) để hiệu quả về dữ liệu/tính toán.
- Index passage bằng FAISS để truy hồi xấp xỉ nhanh ở quy mô lớn.

## Results & Findings
- Cải thiện **9%–19% tuyệt đối** về top-20 passage retrieval accuracy so với hệ Lucene-BM25 mạnh.
- Giúp hệ QA end-to-end đạt SOTA trên nhiều benchmark (Natural Questions, TriviaQA...).

## Limitations
- Cần dữ liệu giám sát (cặp câu hỏi–passage) để huấn luyện encoder.
- Dense retrieval có thể thua sparse ở truy vấn nặng từ khóa/hiếm (entity, mã, số) — gợi ý hướng hybrid (xem [[18 - Friel 2024 - RAGBench]], hybrid retrieval).

## Related Works
- [[01 - Lewis 2020 - RAG]] · [[29 - Sarthi 2024 - RAPTOR]] · [[_Sources Master List]] · [[Smart Solar Platform - Capstone 2026]]

## My Notes & Critiques
- Đối chiếu BM25 vs dense là một thí nghiệm tốt cho phần retrieval của custom pipeline.

## Quotes
> "Retrieval can be practically implemented using dense representations alone, where embeddings are learned from a small number of questions and passages by a simple dual-encoder framework."
> "Our dense retriever outperforms a strong Lucene-BM25 system largely by 9%-19% absolute in terms of top-20 passage retrieval accuracy."

## References
Karpukhin, V., Oğuz, B., Min, S., Lewis, P., Wu, L., Edunov, S., Chen, D. & Yih, W. (2020). *Dense Passage Retrieval for Open-Domain Question Answering*. EMNLP 2020, 6769–6781. arXiv:2004.04906.
