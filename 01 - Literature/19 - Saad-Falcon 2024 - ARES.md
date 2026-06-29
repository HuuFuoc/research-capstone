---
title: "ARES: An Automated Evaluation Framework for Retrieval-Augmented Generation Systems"
authors: Saad-Falcon, J., Khattab, O., Potts, C. & Zaharia, M.
year: 2024
venue: NAACL 2024
tags: [literature, rag-evaluation, framework]
status: unread
url: https://arxiv.org/abs/2311.09476
ref: 19
---

# ARES: An Automated Evaluation Framework for Retrieval-Augmented Generation Systems

## Summary
Khung **tự động đánh giá** RAG theo 3 chiều: **context relevance, answer faithfulness, answer relevance**. ARES tự sinh dữ liệu synthetic để fine-tune **LM judge nhẹ**, rồi dùng **prediction-powered inference (PPI)** với ít nhãn người để hiệu chỉnh sai số.

## Vai trò trong Capstone
- Tiêu chí phục vụ: **Accuracy/Relevance, Hallucination (Faithfulness)** — đánh giá nhiều pipeline với chi phí gán nhãn thấp.
- So sánh phương pháp đánh giá với RAGAs (ARES định lượng & robust hơn khi đổi domain).

## Key Contributions
- Đánh giá tự động chỉ cần **vài trăm nhãn người**.
- LM judge nhẹ được fine-tune trên dữ liệu synthetic; **PPI** giảm sai lệch dự đoán.
- **Bền vững khi domain shift** (đổi loại truy vấn/tài liệu).

## Methodology
- Sinh câu hỏi/đáp synthetic từ corpus → fine-tune judge cho từng chiều → chấm hệ RAG → hiệu chỉnh bằng PPI với tập nhỏ nhãn người.
- Thử nghiệm trên 8 tác vụ knowledge-intensive (KILT, SuperGLUE, AIS).

## Results & Findings
- Đánh giá **chính xác trên 8 tác vụ** chỉ với vài trăm annotation; judge vẫn hiệu quả sau domain shift.

## Limitations
- Phụ thuộc chất lượng dữ liệu synthetic & tập PPI; vẫn cần một ít nhãn người.

## Related Works
- [[06 - Es 2024 - RAGAs]] · [[18 - Friel 2024 - RAGBench]] · [[20 - Ru 2024 - RAGChecker]] · [[_Sources Master List]] · [[Smart Solar Platform - Capstone 2026]]

## My Notes & Critiques
- Tính "bền với domain shift" rất hợp khi chuyển sang tài liệu dự án; cân nhắc ARES cho đánh giá tự động chi phí thấp.

## Quotes
> "ARES finetunes lightweight LM judges to assess the quality of individual RAG components."
> "ARES judges remain effective across domain shifts."

## References
Saad-Falcon, J., Khattab, O., Potts, C. & Zaharia, M. (2024). *ARES: An Automated Evaluation Framework for Retrieval-Augmented Generation Systems*. NAACL 2024. arXiv:2311.09476.
