---
title: "RAGBench: Explainable Benchmark for Retrieval-Augmented Generation Systems"
authors: Friel, R., Belyi, M. & Sanyal, A.
year: 2024
venue: arXiv:2407.11005
tags: [literature, rag-evaluation, benchmark]
status: unread
url: https://arxiv.org/abs/2407.11005
ref: 18
---

# RAGBench: Explainable Benchmark for Retrieval-Augmented Generation Systems

## Summary
**Benchmark RAG lớn đầu tiên**: 100k ví dụ trên 5 domain công nghiệp (nguồn từ user manual...). Đề xuất bộ metric **TRACe** (giải thích được, hành động được) áp dụng xuyên domain.

## Vai trò trong Capstone
- Tiêu chí phục vụ: **Accuracy/Relevance, Hallucination (Adherence), Source Traceability**.
- Chuẩn benchmark định lượng + nguồn dataset tham khảo cho tài liệu kiểu doanh nghiệp.

## Key Contributions
- **RAGBench**: dataset 100.000 ví dụ, 5 domain công nghiệp, nhiều loại tác vụ RAG.
- Hình thức hóa **TRACe**: Context **R**elevance, Context **U**tilization, **A**dherence (bám ngữ cảnh ⇒ chống hallucination), **C**ompleteness.
- Nhãn **giải thích được** → phản hồi hành động được để cải tiến hệ production.

## Methodology
- Thu thập từ corpora công nghiệp (user manuals...); gán nhãn theo TRACe; so sánh nhiều phương pháp đánh giá.

## Results & Findings
- Phương pháp **LLM-judge khó cạnh tranh với một mô hình RoBERTa fine-tuned** trên tác vụ đánh giá RAG → mô hình chuyên dụng nhỏ có thể tốt & rẻ hơn.

## Limitations
- Domain công nghiệp đặc thù (tiếng Anh); cần kiểm chứng trên tài liệu dự án/tiếng Việt.

## Related Works
- [[06 - Es 2024 - RAGAs]] · [[17 - Yu 2024 - Evaluation of RAG Survey]] · [[20 - Ru 2024 - RAGChecker]] · [[_Sources Master List]] · [[Smart Solar Platform - Capstone 2026]]

## My Notes & Critiques
- Gợi ý dùng "Adherence" làm proxy đo hallucination; cân nhắc fine-tune model nhỏ thay LLM-judge để giảm cost.

## Quotes
> "We introduce RAGBench: the first comprehensive, large-scale RAG benchmark dataset of 100k examples ... sourced from industry corpora such as user manuals."
> "LLM-based RAG evaluation methods struggle to compete with a finetuned RoBERTa model on the RAG evaluation task."

## References
Friel, R., Belyi, M. & Sanyal, A. (2024). *RAGBench: Explainable Benchmark for Retrieval-Augmented Generation Systems*. arXiv:2407.11005.
