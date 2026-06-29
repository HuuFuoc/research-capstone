---
title: "Survey of Hallucination in Natural Language Generation"
authors: Ji, Z. et al.
year: 2023
venue: ACM Computing Surveys 55(12), Article 248 — DOI 10.1145/3571730
tags: [literature, rag-evaluation]
status: unread
url: https://dl.acm.org/doi/10.1145/3571730
ref: 7
---

# Survey of Hallucination in Natural Language Generation

## Summary
Khảo sát nền tảng về **hallucination trong NLG**: tổng hợp định nghĩa, phân loại (intrinsic vs extrinsic), nguyên nhân, **metric đo** và **phương pháp giảm thiểu** xuyên nhiều tác vụ. Cơ sở lý thuyết để xây tiêu chí *hallucination rate* đúng chuẩn.

## Vai trò trong Capstone
- Tiêu chí phục vụ: **Hallucination Reduction** — định nghĩa và đo lường đúng.
- Khung phân loại để phân tích loại lỗi của custom pipeline.

## Key Contributions
- Bài review **toàn diện đầu tiên** về đo lường & giảm thiểu hallucination trong NLG.
- Tổ chức theo: (1) tổng quan metric/mitigation/định hướng; (2) tiến bộ theo tác vụ (tóm tắt, hội thoại, QA sinh, data-to-text, dịch máy, thị giác–ngôn ngữ); (3) hallucination trong LLM.

## Methodology
- Review hệ thống tài liệu; chuẩn hóa khái niệm **intrinsic** (mâu thuẫn với nguồn) vs **extrinsic** (không kiểm chứng được từ nguồn) và tổng hợp các họ metric (thống kê n-gram, dựa mô hình, dựa QA/entailment).

## Results & Findings
- Sinh dựa deep learning **dễ hallucinate**, làm giảm hiệu năng và không đạt kỳ vọng người dùng ở nhiều tình huống thực tế.
- Mitigation chia thành nhóm theo dữ liệu (data-related) và theo mô hình/giải mã (modeling & inference).

## Limitations
- Là khảo sát đến ~2022; phần LLM còn sơ khởi so với hiện nay → bổ sung bằng [[21 - Niu 2024 - RAGTruth]], [[22 - Zhou 2024 - Trustworthiness in RAG Survey]].

## Related Works
- [[21 - Niu 2024 - RAGTruth]] · [[22 - Zhou 2024 - Trustworthiness in RAG Survey]] · [[06 - Es 2024 - RAGAs]] · [[_Sources Master List]] · [[Smart Solar Platform - Capstone 2026]]

## My Notes & Critiques
- Dùng định nghĩa intrinsic/extrinsic để diễn giải kết quả hallucination rate trong thực nghiệm.

## Quotes
> "It is also apparent that deep learning based generation is prone to hallucinate unintended text, which degrades the system performance and fails to meet user expectations in many real-world scenarios."
> "In this survey, we ... provide a broad overview of the research progress and challenges in the hallucination problem in NLG."

## References
Ji, Z., Lee, N., Frieske, R., Yu, T., Su, D., Xu, Y., Ishii, E., Bang, Y., Dai, W., Madotto, A. & Fung, P. (2023). *Survey of Hallucination in Natural Language Generation*. ACM Computing Surveys, 55(12), Article 248. DOI:10.1145/3571730. arXiv:2202.03629.
