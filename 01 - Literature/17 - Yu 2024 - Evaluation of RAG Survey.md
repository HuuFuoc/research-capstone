---
title: "Evaluation of Retrieval-Augmented Generation: A Survey"
authors: Yu, H., Gan, A., Zhang, K., Tong, S., Liu, Q. & Liu, Z.
year: 2024
venue: arXiv:2405.07437 (CCF Big Data 2024)
tags: [literature, rag-evaluation, survey]
status: unread
url: https://arxiv.org/abs/2405.07437
ref: 17
---

# Evaluation of Retrieval-Augmented Generation: A Survey

## Summary
Survey chuyên sâu về **đánh giá RAG**; đề xuất quy trình hợp nhất **AUEPORA** (A Unified Evaluation Process of RAG) và phân tích metric theo hai thành phần **Retrieval** và **Generation** cùng các benchmark hiện có. Bổ trợ trực tiếp cho RAGAs.

## Vai trò trong Capstone
- Tiêu chí phục vụ: **toàn bộ 6 tiêu chí** — khung phân loại metric để thiết kế experiment so sánh.
- Dùng ở **Methodology** để biện minh việc chọn metric (retrieval vs generation).

## Key Contributions
- Đề xuất **AUEPORA**: quy trình đánh giá thống nhất (xác định đối tượng đo → dataset → metric → so sánh output vs ground truth).
- Hệ thống hóa metric cho retrieval (relevance, accuracy) và generation (faithfulness, relevance, accuracy).
- Tổng hợp & so sánh các benchmark/tool đánh giá RAG.

## Methodology
- Review tài liệu, đề xuất taxonomy quy trình đánh giá; không thực nghiệm gốc.

## Results & Findings
- Đánh giá RAG khó do **cấu trúc lai** (retrieval + generation) và phụ thuộc **nguồn tri thức động**.
- Cung cấp bản đồ metric–benchmark giúp chọn đúng công cụ theo mục tiêu đo.

## Limitations
- Là khảo sát; cần kết hợp framework thực thi (RAGAs/ARES/RAGChecker) để chạy số.

## Related Works
- [[06 - Es 2024 - RAGAs]] · [[18 - Friel 2024 - RAGBench]] · [[19 - Saad-Falcon 2024 - ARES]] · [[20 - Ru 2024 - RAGChecker]] · [[_Sources Master List]] · [[Smart Solar Platform - Capstone 2026]]

## My Notes & Critiques
- Dùng AUEPORA làm xương sống mô tả quy trình đánh giá trong paper capstone.

## Quotes
> "Evaluating these RAG systems poses unique challenges due to their hybrid structure and reliance on dynamic knowledge sources."
> "We examine and compare several quantifiable metrics of the Retrieval and Generation components."

## References
Yu, H., Gan, A., Zhang, K., Tong, S., Liu, Q. & Liu, Z. (2024). *Evaluation of Retrieval-Augmented Generation: A Survey*. arXiv:2405.07437.
