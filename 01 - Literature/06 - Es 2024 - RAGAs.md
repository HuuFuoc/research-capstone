---
title: "RAGAs: Automated Evaluation of Retrieval Augmented Generation"
authors: Es, S., James, J., Espinosa-Anke, L. & Schockaert, S.
year: 2024
venue: EACL 2024 System Demos (pp. 150-158)
tags: [literature, rag-evaluation, framework]
status: unread
url: https://aclanthology.org/2024.eacl-demo.16
ref: 6
---

# RAGAs: Automated Evaluation of Retrieval Augmented Generation

## Summary
**Framework đánh giá chính** của đề tài: bộ metric **không cần ground-truth (reference-free)** đo nhiều chiều của pipeline RAG — đặc biệt Faithfulness, Answer Relevance, Context Relevance — giúp rút ngắn chu kỳ đánh giá.

## Vai trò trong Capstone
- Tiêu chí phục vụ: **Accuracy/Relevance, Hallucination, Source Traceability, Response Time, Cost**.
- Cài đặt & chạy thử **trước** khi thiết kế experiment so sánh custom vs existing.

## Key Contributions
- Đề xuất **đánh giá RAG không cần nhãn người** (reference-free), dùng LLM làm giám khảo.
- Tách bạch ba chiều: chất lượng **truy hồi** (context), mức **trung thành với ngữ cảnh** (faithfulness), và chất lượng **sinh** (answer relevance).
- Cho phép vòng lặp đánh giá nhanh — quan trọng khi LLM được áp dụng rộng.

## Methodology
- **Faithfulness:** tách câu trả lời thành các "claim", kiểm tra tỉ lệ claim được ngữ cảnh truy hồi hỗ trợ (suy luận bằng LLM).
- **Answer Relevance:** sinh ngược các câu hỏi từ câu trả lời, đo độ tương đồng (embedding) với câu hỏi gốc.
- **Context Relevance:** ước lượng tỉ lệ câu trong ngữ cảnh thực sự liên quan đến câu hỏi.

## Results & Findings
- Các metric tương quan tốt với đánh giá của con người trên dữ liệu thử (WikiEval), cho thấy có thể thay thế chấm thủ công ở quy mô lớn.
- Là công cụ mã nguồn mở được áp dụng rộng để đo Faithfulness/Relevancy.

## Limitations
- Phụ thuộc LLM giám khảo → có thể lệch theo model & prompt; chi phí gọi LLM cho mỗi mẫu.
- "Context Relevance" nhạy với cách tách câu/đoạn.

## Related Works
- [[17 - Yu 2024 - Evaluation of RAG Survey]] · [[18 - Friel 2024 - RAGBench]] · [[19 - Saad-Falcon 2024 - ARES]] · [[_Sources Master List]] · [[Smart Solar Platform - Capstone 2026]]

## My Notes & Critiques
- Đây là bộ đo chủ lực để trả lời Research Question (accuracy/relevance/hallucination/traceability).

## Quotes
> "We introduce Ragas ... a framework for reference-free evaluation of Retrieval Augmented Generation (RAG) pipelines."
> "With Ragas, we put forward a suite of metrics which can be used to evaluate these different dimensions without having to rely on ground truth human annotations."

## References
Es, S., James, J., Espinosa-Anke, L. & Schockaert, S. (2024). *RAGAs: Automated Evaluation of Retrieval Augmented Generation*. EACL 2024 System Demonstrations, 150–158. arXiv:2309.15217.
