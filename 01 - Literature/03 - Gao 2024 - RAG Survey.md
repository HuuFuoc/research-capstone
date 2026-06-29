---
title: "Retrieval-Augmented Generation for Large Language Models: A Survey"
authors: Gao, Y. et al.
year: 2024
venue: arXiv:2312.10997
tags: [literature, rag-foundation]
status: unread
url: https://arxiv.org/abs/2312.10997
ref: 3
---

# Retrieval-Augmented Generation for Large Language Models: A Survey

## Summary
Survey toàn cảnh RAG — đưa ra khung phân loại ba thế hệ **Naive / Advanced / Modular RAG** và mổ xẻ ba trụ cột: **retrieval, generation, augmentation**. Dùng để định vị custom pipeline trong bản đồ kiến trúc RAG.

## Vai trò trong Capstone
- Tiêu chí phục vụ: **Accuracy / Relevance**.
- Khung phân loại kiến trúc để định vị custom pipeline (thuộc Advanced/Modular RAG).

## Key Contributions
- Hệ thống hóa tiến hóa RAG thành 3 paradigm: **Naive** (index–retrieve–generate cơ bản), **Advanced** (tối ưu pre/post-retrieval: rewrite query, rerank), **Modular** (các module linh hoạt, có thể lặp/định tuyến).
- Phân tích từng trụ cột retrieval/generation/augmentation cùng kỹ thuật SOTA.
- Tổng hợp **framework & benchmark đánh giá** RAG, nêu thách thức và hướng nghiên cứu.

## Methodology
- Dạng review: khảo sát–phân loại tài liệu, không có thực nghiệm gốc; đề xuất taxonomy và bảng so sánh kỹ thuật.

## Results & Findings
- RAG hợp nhất tri thức nội tại của LLM với kho ngoài động → tăng độ chính xác, độ tin cậy, cho phép cập nhật tri thức liên tục và tích hợp tri thức chuyên ngành.
- Advanced/Modular RAG cải thiện rõ chất lượng truy hồi & sinh so với Naive.

## Limitations
- Là khảo sát (tổng hợp), không phải đánh giá thực nghiệm thống nhất; bối cảnh thay đổi nhanh nên cần cập nhật.
- Các thách thức mở: chất lượng truy hồi, độ trễ, đánh giá chuẩn hóa.

## Related Works
- [[05 - Gupta 2024 - Comprehensive RAG Survey]] · [[17 - Yu 2024 - Evaluation of RAG Survey]] · [[_Sources Master List]] · [[Smart Solar Platform - Capstone 2026]]

## My Notes & Critiques
- Dùng taxonomy Naive/Advanced/Modular để mô tả vị trí kỹ thuật của custom pipeline trong paper.

## Quotes
> "LLMs encounter challenges like hallucination, outdated knowledge, and non-transparent, untraceable reasoning processes. RAG has emerged as a promising solution by incorporating knowledge from external databases."
> "This comprehensive review ... encompass[es] the Naive RAG, the Advanced RAG, and the Modular RAG."

## References
Gao, Y., Xiong, Y., Gao, X., Jia, K., Pan, J., Bi, Y., Dai, Y., Sun, J., Wang, M. & Wang, H. (2023). *Retrieval-Augmented Generation for Large Language Models: A Survey*. arXiv:2312.10997.
