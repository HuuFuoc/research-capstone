---
title: "FreshStack: Building Realistic Benchmarks for Evaluating Retrieval on Technical Documents"
authors: Thakur, N., Lin, J., Havens, S., Carbin, M., Khattab, O. & Drozdov, A.
year: 2025
venue: arXiv:2504.13128
tags: [literature, rag-evaluation, benchmark, technical-documents]
status: unread
url: https://arxiv.org/abs/2504.13128
ref: 31
---

# FreshStack: Building Realistic Benchmarks for Evaluating Retrieval on Technical Documents

## Summary
Khung **tự động dựng benchmark** (bộ dữ liệu chuẩn để đo) cho truy hồi (retrieval) **trên tài liệu kỹ thuật + code**. Rất sát đề tài vì tài liệu dự án của bạn cũng là *technical/requirement docs*. Dùng "nugget" (mẩu thông tin đúng) từ hỏi-đáp cộng đồng để chấm điểm.

## Vai trò trong Capstone
- Tiêu chí phục vụ: **Accuracy/Relevance (retrieval)** — phương pháp xây bộ test **không bị nhiễm dữ liệu (uncontaminated)** trên tài liệu kỹ thuật.
- Mẫu hình để **tự tạo benchmark** đánh giá retrieval trên tài liệu dự án thay vì chỉ dùng bộ chuẩn tiếng Anh phổ thông.

## Key Contributions
- Quy trình 3 bước: (1) thu thập corpus từ code & technical docs; (2) sinh **nugget** từ Q&A cộng đồng; (3) gán hỗ trợ ở **mức nugget** bằng *fusion* (gộp nhiều kỹ thuật truy hồi) + kiến trúc hybrid.
- Tạo **5 dataset** trên chủ đề mới/ngách → đủ khó để lộ điểm yếu mô hình.

## Methodology
- Tự động hoá xây benchmark; đo retrieval bằng cách kiểm mỗi câu trả lời được hỗ trợ bởi nugget nào (nugget-level support).

## Results & Findings
- Mô hình truy hồi hiện có (dùng "out-of-the-box" — chạy thẳng không tinh chỉnh) **thua xa oracle** (giới hạn lý tưởng) ở **cả 5 chủ đề** → còn nhiều dư địa cải thiện.
- Có **2/5 chủ đề mà reranker KHÔNG cải thiện** retrieval giai đoạn 1 → rerank không phải lúc nào cũng hữu ích.

## Limitations
- Tập trung chủ đề code/kỹ thuật tiếng Anh; cần thích ứng cho tài liệu dự án tiếng Việt.

## Related Works
- [[18 - Friel 2024 - RAGBench]] · [[32 - Tang 2024 - MultiHop-RAG]] · [[08 - 2025 - Document Chunking Strategies]] · [[_Sources Master List]] · [[Bảng thuật ngữ (Glossary)]]

## My Notes & Critiques
- Ý tưởng "tự dựng benchmark từ Q&A nội bộ" rất hợp để đánh giá retrieval trên tài liệu dự án của team.

## Quotes
> "Existing retrieval models, when applied out-of-the-box, significantly underperform oracle approaches on all five topics, denoting plenty of headroom to improve IR quality."
> "We identify cases where rerankers do not improve first-stage retrieval accuracy (two out of five topics)."

## References
Thakur, N., Lin, J., Havens, S., Carbin, M., Khattab, O. & Drozdov, A. (2025). *FreshStack: Building Realistic Benchmarks for Evaluating Retrieval on Technical Documents*. arXiv:2504.13128.
