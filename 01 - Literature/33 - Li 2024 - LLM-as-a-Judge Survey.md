---
title: "From Generation to Judgment: Opportunities and Challenges of LLM-as-a-judge"
authors: Li, D., Jiang, B., Huang, L., Beigi, A., Zhao, C., Tan, Z., et al.
year: 2024
venue: EMNLP 2025 (arXiv:2411.16594)
tags: [literature, rag-evaluation, llm-judge, survey]
status: unread
url: https://arxiv.org/abs/2411.16594
ref: 33
---

# From Generation to Judgment: Opportunities and Challenges of LLM-as-a-judge

## Summary
Survey về **LLM-as-a-judge** (dùng một LLM làm "giám khảo" chấm điểm câu trả lời thay con người). Quan trọng vì RAGAs/ARES/RAGChecker đều dựa cơ chế này → cần hiểu **thiên kiến (bias)** của giám khảo để đánh giá đáng tin.

## Vai trò trong Capstone
- Tiêu chí phục vụ: **toàn bộ** — nền tảng phương pháp luận cho phần Evaluation (vì ta dùng LLM chấm điểm).
- Giúp **giảm rủi ro thiên kiến** khi báo cáo số đo accuracy/faithfulness.

## Key Contributions
- **Taxonomy 3 chiều**: *what to judge* (chấm cái gì), *how to judge* (chấm thế nào), *how to benchmark* (đo độ tin của giám khảo).
- Tổng hợp cơ hội & thách thức khi thay đánh giá truyền thống (BLEU/ROUGE) bằng LLM judge.

## Methodology
- Review hệ thống; phân loại phương pháp và chỉ ra các nguồn sai lệch.

## Results & Findings
- LLM judge **rẻ & co giãn tốt** nhưng có thiên kiến: **position bias** (thích câu ở đầu/cuối), **verbosity bias** (thích câu dài), **self-enhancement bias** (thích output giống chính nó).
- → Cần thiết kế prompt + quy trình (tách reasoning/scoring, polling) để đạt mức đồng thuận như người.

## Limitations
- Là khảo sát; biện pháp khử bias cụ thể tùy mô hình/tác vụ, cần thử nghiệm riêng.

## Related Works
- [[06 - Es 2024 - RAGAs]] · [[19 - Saad-Falcon 2024 - ARES]] · [[20 - Ru 2024 - RAGChecker]] · [[_Sources Master List]] · [[Bảng thuật ngữ (Glossary)]]

## My Notes & Critiques
- Khi dùng RAGAs (LLM judge) phải nêu rõ biện pháp kiểm soát bias trong paper, nếu không reviewer sẽ hỏi.

## Quotes
> "[We present] a systematic taxonomy to explore LLM-as-a-judge along three dimensions: what to judge, how to judge, and how to benchmark."

## References
Li, D., Jiang, B., Huang, L., Beigi, A., Zhao, C., Tan, Z., Bhattacharjee, A., Jiang, Y., Chen, C., Wu, T., Shu, K., Cheng, L. & Liu, H. (2024). *From Generation to Judgment: Opportunities and Challenges of LLM-as-a-judge*. EMNLP 2025. arXiv:2411.16594.
