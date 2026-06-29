---
title: "A Systematic Investigation of Document Chunking Strategies and Embedding Sensitivity"
authors: Shaukat, M. A., Adnan, M. & Kuhn, C. C. N.
year: 2026
venue: arXiv:2603.06976
tags: [literature, rag-evaluation, chunking, embedding]
status: unread
url: https://arxiv.org/abs/2603.06976
ref: 8
---

# A Systematic Investigation of Document Chunking Strategies and Embedding Sensitivity

## Summary
Nghiên cứu thực nghiệm so sánh **36 phương pháp tách tài liệu** trên **6 lĩnh vực tri thức** với **5 mô hình embedding**. Kết luận: **chunking theo nội dung (content-aware)** vượt rõ tách độ dài cố định (naive fixed-length); chiến lược tối ưu **phụ thuộc lĩnh vực**.

## Vai trò trong Capstone
- Tiêu chí phục vụ: **Response Time**, retrieval accuracy, **Cost** (đánh đổi hiệu quả vs chi phí tính toán).
- Hướng dẫn chọn chunking + embedding cho custom pipeline trên tài liệu dự án.

## Key Contributions
- Khảo sát thực nghiệm quy mô lớn: 36 phương pháp × 6 domain × 5 embedding model.
- Định lượng **đánh đổi hiệu quả–chi phí** (effectiveness vs computational efficiency).
- Chỉ ra **biến thiên theo domain** của chiến lược chunking tối ưu.

## Methodology
- Đánh giá retrieval theo **nDCG@5** cho từng cặp (chiến lược chunk, embedding model) trên nhiều domain.

## Results & Findings
- **Paragraph Group Chunking** tốt nhất, nDCG@5 ≈ **0.459**; tách theo ký tự cơ bản (character-based) < **0.244**.
- Chunking tốt hơn + embedding model lớn hơn cho lợi ích **bổ trợ nhau** (complementary).

## Limitations
- Kết quả gắn với bộ domain/embedding đã chọn; cần kiểm chứng trên tài liệu dự án cụ thể (tiếng Việt, doc kỹ thuật).

## Related Works
- [[02 - Karpukhin 2020 - Dense Passage Retrieval]] · [[29 - Sarthi 2024 - RAPTOR]] · [[_Sources Master List]] · [[Smart Solar Platform - Capstone 2026]]

## My Notes & Critiques
- Là cơ sở thực nghiệm để chọn chunking cho custom pipeline; nên tái lập nDCG trên dữ liệu dự án.

## Quotes
> "Content-aware chunking significantly improves retrieval effectiveness over naive fixed-length splitting."

## References
Shaukat, M. A., Adnan, M. & Kuhn, C. C. N. (2026). *A Systematic Investigation of Document Chunking Strategies and Embedding Sensitivity*. arXiv:2603.06976.
