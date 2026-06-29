---
title: "Retrieval-Augmented Generation in Industry: An Interview Study on Use Cases, Requirements, Challenges, and Evaluation"
authors: Brehme, L., Dornauer, B., Ströhle, T., Ehrhart, M. & Breu, R.
year: 2025
venue: KDIR 2025 (17th Int. Conf. on Knowledge Discovery and Information Retrieval)
tags: [literature, rag-industry, requirements, case-study]
status: unread
url: https://arxiv.org/abs/2508.14066
ref: 26
---

# Retrieval-Augmented Generation in Industry: An Interview Study

## Summary
Nghiên cứu phỏng vấn **13 chuyên gia doanh nghiệp** về **use case, yêu cầu, thách thức & cách đánh giá** RAG thực tế. Phát hiện: ứng dụng chủ yếu là **QA chuyên ngành** còn ở mức prototype; **tiền xử lý dữ liệu** là rào cản chính; **đánh giá vẫn do con người** là chủ đạo.

## Vai trò trong Capstone
- Tiêu chí phục vụ: **toàn bộ** — bằng chứng thực tiễn vì sao cần tùy chỉnh RAG theo tài liệu dự án.
- Dùng ở Introduction/Motivation để biện minh Research Problem (general-purpose chưa tối ưu cho doc dự án).

## Key Contributions
- Bức tranh thực địa về RAG trong công nghiệp: use case, yêu cầu, thách thức, thực hành đánh giá.
- Chỉ ra khoảng cách: **đánh giá tự động bị dùng dưới mức** dù có nhiều framework học thuật.

## Methodology
- Phỏng vấn định tính 13 practitioner; phân tích chủ đề (thematic analysis).

## Results & Findings
- Ứng dụng RAG **chủ yếu là QA domain-specific**, hệ thống còn ở giai đoạn prototype.
- **Tiền xử lý dữ liệu** là trở ngại lớn nhất; ưu tiên **bảo mật, bảo vệ dữ liệu, chất lượng dữ liệu** hơn là ethics/bias/scalability.
- **Đánh giá dựa trên con người chiếm ưu thế**; phương pháp tự động chưa được tận dụng.

## Limitations
- Mẫu nhỏ (13 người), định tính → khó tổng quát hóa định lượng.

## Related Works
- [[09 - 2024 - Evaluating ChatGPT Nuclear Domain]] · [[06 - Es 2024 - RAGAs]] · [[_Sources Master List]] · [[Smart Solar Platform - Capstone 2026]]

## My Notes & Critiques
- Hậu thuẫn mạnh cho motivation: tài liệu dự án + yêu cầu bảo mật/chất lượng → cần custom pipeline + đánh giá tự động (đóng góp của capstone).

## Quotes
> "Current RAG applications are mostly limited to domain-specific QA tasks, with systems still in prototype stages."
> "Data preprocessing remains a key challenge, and system evaluation is predominantly conducted by humans."

## References
Brehme, L., Dornauer, B., Ströhle, T., Ehrhart, M. & Breu, R. (2025). *Retrieval-Augmented Generation in Industry: An Interview Study on Use Cases, Requirements, Challenges, and Evaluation*. KDIR 2025. arXiv:2508.14066.
