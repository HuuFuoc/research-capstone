---
title: "Verify Log — NotebookLM (grounded)"
tags: [note, paper, verification, log]
status: reference
created: 2026-06-29
updated: 2026-06-30
---

# Verify Log — NotebookLM (grounded на 35 nguồn)

> Đối chiếu các claim/số liệu trong [[Bản đọc thử - Paper Draft (Smart Solar RAG)]] với nguồn gốc, **grounded qua NotebookLM** (Gemini 2.5, trích nguyên văn từ tài liệu đã nạp). Mỗi dòng: claim → nguồn `[n]` (theo [[_Sources Master List]]) → trích nguyên văn → trạng thái.
> Quy trình: [[Plan - NotebookLM Research+Verify Pass (2026-06-29)]].

## ⚠️ Giới hạn phương pháp (đọc trước)
- Notebook ban đầu chỉ có **26/34 nguồn**; đã nạp bổ sung → **35 nguồn** (2026-06-30). 7 paper RAG còn thiếu ([28]–[34]) nay đã vào.
- Các nguồn được nạp dưới dạng **trang abstract (arXiv `/abs/`, ACL, …)** ⇒ NotebookLM chỉ "thấy" **mức abstract**. Vì vậy:
  - ✅ Verify tốt các số nằm **trong abstract**.
  - ⚠️ **KHÔNG** verify được số nằm **trong bảng/thân bài** (vd AIS 65.5% ở Table 1 [23]); các số này giữ theo **đối chiếu full-text trước đó của vault** — không coi "NotebookLM không thấy" = "số sai".
- 1 nguồn bị crawl hỏng (trang *"Checking your browser – reCAPTCHA"*); vài nguồn CV ([11][12][16]) chưa vào — **ngoài phạm vi bài RAG**, không ảnh hưởng.

## Bảng verify

| # | Claim trong bài | Nguồn | Trích nguyên văn (grounded) | Trạng thái |
|---|---|---|---|---|
| 1 | DPR vượt BM25 **9–19% absolute** top-20 | [2] | "our dense retriever outperforms a strong Lucene-BM25 system greatly by **9%-19% absolute** in terms of top-20 passage retrieval accuracy" | ✅ Abstract. Dataset nêu chung: "a wide range of open-domain QA datasets" |
| 2 | Content-aware chunking **nDCG@5 ≈0.459** vs **<0.244** | [8] | "Paragraph Group Chunking, achieved the highest overall accuracy (**mean nDCG@5 ≈ 0.459**) and substantially better top-rank hit rates (**Precision@1 ≈ 24%, Hit@5 ≈ 59%**). In contrast, simple fixed-size character chunking … performed poorly (**nDCG@5 < 0.244, Precision@1 ≈ 2-3%**)" | ✅ Bổ sung: FCC nDCG@5=0.244; next-best Dynamic Token 0.441; UltraDomain, 6 domains, 36 methods × 5 embeddings |
| 3 | RAPTOR **+20% absolute** QuALITY (**+ GPT-4**) | [29] | "by **coupling RAPTOR retrieval with the use of GPT-4**, we can improve the best performance on the QuALITY benchmark by **20% in absolute accuracy**" | ✅ Abstract (sau khi nạp nguồn) |
| 4 | AIS best retrieve-then-read **65.5±1.5%** (Table 1) | [23] | *(không có trong text được index — Bohnet chỉ có abstract)* | ⚠️ NotebookLM **không xác nhận được** (abstract-only). Giữ theo verify full-text Table 1 trước đó của vault. "correctness ≠ attribution" cũng ở thân bài, không có ở abstract |
| 5 | RAGBench **100k**, **5 domains**; **RoBERTa > LLM-judge** | [18] | "the first comprehensive, large-scale RAG benchmark dataset of **100k examples**. It covers **five unique industry-specific domains**…"; "LLM-based RAG evaluation methods **struggle to compete with a finetuned RoBERTa model**" | ✅. Tên 4 thành phần **TRACe** (Context Relevance/Utilization/Adherence/Completeness) ⚠️ ở thân bài, không có ở abstract |
| 6 | RAGTruth **~18.000** câu, **word-level**; small LLM ~ GPT-4 | [21] | "RAGTruth comprises **nearly 18,000** naturally generated responses … annotations at both the individual cases and **word levels**"; "finetune a **relatively small LLM** and achieve a **competitive** level of performance … compared to … **GPT-4**" | ✅ |
| 7 | LC > RAG accuracy; **RAG rẻ hơn**; Self-Route | [25] | "when resourced sufficiently, **LC consistently outperforms RAG** … However, **RAG's significantly lower cost remains a distinct advantage** … we propose **Self-Route**" | ✅ |
| 8 | ColBERT *late interaction*; **nhanh 2 bậc**, ít FLOPs **4 bậc** | [34] | "ColBERT's effectiveness is competitive with existing BERT-based models (and outperforms every non-BERT baseline), while executing **two orders-of-magnitude faster** and requiring **four orders-of-magnitude fewer FLOPs per query**" | ✅ |
| 9 | FreshStack: retriever out-of-the-box **<< oracle** | [31] | "existing retrieval models, when applied out-of-the-box, **significantly underperform oracle approaches on all five topics**, denoting plenty of headroom to improve IR quality" | ✅ (+ rerankers không cải thiện ở 2/5 topic) |
| 10 | MultiHop-RAG: RAG **kém trên multi-hop** | [32] | "existing RAG systems are **inadequate in answering multi-hop queries**, which require retrieving and reasoning over multiple pieces of supporting evidence" | ✅ KB = news; thử GPT-4/PaLM/Llama2-70B "unsatisfactorily" |
| 11 | LLM-as-judge: taxonomy + thiên kiến | [33] | "a systematic taxonomy … **what to judge, how to judge, and how to benchmark**"; "Traditional methods … often **fall short in open-ended and dynamic scenarios**" | ✅ (thiên kiến cụ thể nằm ở thân bài) |
| 12 | RAGAS **reference-free**, không cần ground-truth | [6] | "a framework for **reference-free** evaluation of Retrieval Augmented Generation (RAG) pipelines"; "**without relying on ground truth human annotations**" | ✅. **Công thức** 3 metric ⚠️ **không có trong abstract** → giữ caveat "operational definition, lấy full-text" |
| 13 | Trustworthiness **6 chiều** | [22] | "**Trust-RAG Compass**, that assesses the trustworthiness of RAG systems across **six key dimensions: factuality, robustness, fairness, transparency, accountability, and privacy**" | ✅ (+ TRC Bench) |
| 14 | Vietnamese IR: **RRF chuẩn hóa** + **Active Retrieval rerank** | [27] | "enhance **Reciprocal Rank Fusion by normalizing order** to combine results from keyword and vector searches"; "meticulously **re-rank** … with **Active Retrieval**"; thách thức: "excessive token length or overly simplistic ensemble techniques" | ✅ |

### Đợt 2 — verify thêm các claim đang có trong manuscript (2026-06-30)

| # | Claim trong bài | Nguồn | Trích nguyên văn (grounded) | Trạng thái |
|---|---|---|---|---|
| 15 | Gao: tiến trình **Naive → Advanced → Modular RAG** | [3] | "the progression of RAG paradigms, encompassing the **Naive RAG, the Advanced RAG, and the Modular RAG**"; "(LLMs) … encounter challenges like **hallucination, outdated knowledge, and non-transparent, untraceable reasoning** … RAG has emerged as a promising solution" | ✅ ("parametric/non-parametric memory" là chữ của Lewis [1], không phải Gao — bài đang gán đúng cho [1] ở §1) |
| 16 | Ji: phân biệt **intrinsic** vs **extrinsic** hallucination | [7] | "**Intrinsic hallucinations**: The generated output that **contradicts the source content**."; "**Extrinsic hallucinations**: … **cannot be verified from the source content** (neither supported nor contradicted)" | ✅ |
| 17 | Self-RAG: **reflection token**, retrieve on-demand + tự phê bình | [4] | "trains a single arbitrary LM that **adaptively retrieves passages on-demand**, and generates and **reflects** on retrieved passages and its own generations using **special tokens, called reflection tokens**" | ✅ |
| 18 | CRAG: **retrieval evaluator** chấm chất lượng truy hồi | [30] | "a **lightweight retrieval evaluator** is designed to **assess the overall quality of retrieved documents** for a query, returning a **confidence degree** based on which different knowledge retrieval actions can be triggered" | ✅ |
| 19 | GraphRAG: **câu hỏi toàn cục** + **community summaries** | [28] | "RAG **fails on global questions** directed at an entire text corpus … derive an **entity knowledge graph** … **pregenerate community summaries** … substantial improvements … **comprehensiveness and diversity**" | ✅ |

## Kết luận verify
- **✅ 17/19** claim được xác nhận **nguyên văn** từ abstract (an toàn để cite) — gồm cả Gao taxonomy [3], Ji intrinsic/extrinsic [7], Self-RAG [4], CRAG [30], GraphRAG [28].
- **⚠️ Còn theo full-text vault (NotebookLM không phủ được):** AIS 65.5% Table 1 [23]; tên 4 thành phần TRACe [18]; công thức 3 metric RAGAS [6]; "correctness ≠ attribution" [23].
- Khuyến nghị: với 4 mục ⚠️, giữ nguyên footnote "đối chiếu full-text" và (nếu cần chắc tuyệt đối) upload **PDF** các nguồn này lên NotebookLM để verify lại số trong bảng.

## Liên kết
[[Bản đọc thử - Paper Draft (Smart Solar RAG)]] · [[Related Work - Draft v1 (VN)]] · [[Design & Evaluation Protocol - v2]] · [[_Sources Master List]] · [[Plan - NotebookLM Research+Verify Pass (2026-06-29)]]
