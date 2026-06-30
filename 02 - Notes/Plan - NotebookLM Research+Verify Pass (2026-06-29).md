---
title: "Plan — NotebookLM Research + Verify Pass"
tags: [note, plan, process]
status: in-progress
created: 2026-06-29
---

# Plan — NotebookLM Research + Verify Pass (2026-06-29)

> Kế hoạch thực thi (chiến lược **Hybrid có kiểm soát**) cho 3 mục tiêu: **đào sâu research qua NotebookLM**, **verify trích dẫn/số liệu**, **gộp vào manuscript**. Đầu ra cập nhật in-place vào [[Bản đọc thử - Paper Draft (Smart Solar RAG)]] + log verify riêng.
> Notebook: Smart Solar Capstone 2026 (v2) — 34 nguồn. Budget ≈ 19 query / 1 session.

## Guardrails
- KHÔNG bịa số liệu kết quả/cấu hình hệ thống. Mục §6 Kết quả **để trống**; `[team chốt]` giữ nguyên.
- Verify = bắt NotebookLM **trích nguyên văn + tên nguồn**. Số không xác nhận được → ⚠️, báo user.
- Giữ nhãn [Proposed]/[Plan]/[Result]; giữ caveat grey-lit [15].
- Mọi claim mới trong Related Work phải có dòng verify trong log.

## Query plan (≈19)

### Nhóm A — Verify nguyên văn (7)
- A1 DPR [2]: 9–19% absolute top-20 vs BM25 — dataset nào.
- A2 Chunking [8]: nDCG@5 Paragraph Group ≈0.459 vs <0.244; Precision@1≈24%, Hit@5≈59%.
- A3 RAPTOR [29]: +20% absolute QuALITY (xác nhận "+ GPT-4").
- A4 AIS [23]: Best RTR 65.5±1.5% (Table 1) + "correctness ≠ attribution".
- A5 RAGBench [18]: 4 thành phần TRACe + claim RoBERTa fine-tuned > LLM-judge.
- A6 RAGTruth [21]: ~18k responses, word-level labels; small LLM ~ GPT-4.
- A7 Li [25]: LC accuracy cao hơn / RAG rẻ hơn / Self-Route.

### Nhóm B — Đào sâu + nguồn chưa dùng (8)
- B1 FreshStack [31] · B2 MultiHop-RAG [32] · B3 ColBERT [34] · B4 LLM-as-judge [33]
- B5 Vietnamese legal IR [27] · B6 Self-RAG [4]/CRAG [30] positioning · B7 Trustworthiness [22] · B8 ARES [19]

### Nhóm C — Công thức/định nghĩa (4)
- C1 RAGAS [6] công thức Faithfulness/Answer Relevancy/Context Precision + judge model.
- C2 Ji [7] intrinsic vs extrinsic · C3 Gao [3] Naive/Advanced/Modular · C4 Nuclear [9] phương pháp RAG-vs-plainLLM.

## Đầu ra
1. Cập nhật in-place [[Bản đọc thử - Paper Draft (Smart Solar RAG)]] (Related Work sâu hơn + [31][32][34][33][27]; siết §5.2; mở rộng "Khoảng trống"). §6 trống.
2. [[Verify Log - NotebookLM (2026-06-29)]] — bảng Claim → Nguồn → trích nguyên văn → ✅/⚠️/❌.

## Liên kết
[[Smart Solar Platform - Capstone 2026]] · [[Paper Outline - Smart Solar Capstone]] · [[Design & Evaluation Protocol - v2]] · [[Related Work - Draft v1 (VN)]]
