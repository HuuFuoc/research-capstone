---
title: "RAPTOR: Recursive Abstractive Processing for Tree-Organized Retrieval"
authors: Sarthi, P., Abdullah, S., Tuli, A., Khanna, S., Goldie, A. & Manning, C. D.
year: 2024
venue: ICLR 2024
tags: [literature, chunking, indexing, retrieval]
status: unread
url: https://arxiv.org/abs/2401.18059
ref: 29
---

# RAPTOR: Recursive Abstractive Processing for Tree-Organized Retrieval

## Summary
Khắc phục hạn chế "chỉ truy hồi các chunk ngắn rời rạc": **RAPTOR** đệ quy **embed → cluster → tóm tắt** chunk, dựng **cây tóm tắt nhiều tầng** từ dưới lên; lúc suy luận truy hồi xuyên các mức trừu tượng → hiểu tài liệu dài tốt hơn, mạnh cho multi-hop QA.

## Vai trò trong Capstone
- Tiêu chí phục vụ: **Retrieval accuracy, Response Time** trên tài liệu dài (requirement/technical docs).
- Lựa chọn chunking/indexing nâng cao cho custom pipeline — đối chiếu chunking cố định ([[08 - 2025 - Document Chunking Strategies]]).

## Key Contributions
- Kỹ thuật index **cây tóm tắt đệ quy** tích hợp thông tin ở nhiều mức trừu tượng.
- Cải thiện rõ so với retrieval truyền thống trên nhiều tác vụ; **SOTA** ở QA suy luận nhiều bước.

## Methodology
- Chunk tài liệu → embed (SBERT) → giảm chiều **UMAP** → cluster **GMM** → tóm tắt cụm → lặp lên tầng trên, tạo cây; truy hồi từ cây ở inference.

## Results & Findings
- Ghép **RAPTOR + GPT-4** cải thiện best performance trên **QuALITY +20% absolute accuracy**.
- Retrieval theo tóm tắt đệ quy vượt RA-LM truyền thống trên nhiều benchmark.

## Limitations
- Chi phí tiền xử lý (clustering + tóm tắt) cao; cây cần cập nhật khi corpus thay đổi.

## Related Works
- [[08 - 2025 - Document Chunking Strategies]] · [[02 - Karpukhin 2020 - Dense Passage Retrieval]] · [[28 - Edge 2024 - GraphRAG]] · [[_Sources Master List]] · [[Smart Solar Platform - Capstone 2026]]

## My Notes & Critiques
- Phù hợp tài liệu kỹ thuật dài; nên benchmark RAPTOR vs chunking cố định trên dữ liệu dự án.

## Quotes
> "We introduce the novel approach of recursively embedding, clustering, and summarizing chunks of text, constructing a tree with differing levels of summarization from the bottom up."
> "By coupling RAPTOR retrieval with the use of GPT-4, we can improve the best performance on the QuALITY benchmark by 20% in absolute accuracy."

## References
Sarthi, P., Abdullah, S., Tuli, A., Khanna, S., Goldie, A. & Manning, C. D. (2024). *RAPTOR: Recursive Abstractive Processing for Tree-Organized Retrieval*. ICLR 2024. arXiv:2401.18059.
