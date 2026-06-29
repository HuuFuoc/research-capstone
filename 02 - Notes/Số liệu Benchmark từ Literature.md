---
title: Số liệu Benchmark từ Literature (reference/baseline)
tags: [note, paper, data, benchmark]
status: reference
created: 2026-06-29
---

# Số liệu Benchmark từ Literature (mốc tham chiếu)

> ⚠️ **ĐỌC TRƯỚC:** Đây là **số liệu ĐÃ CÔNG BỐ trong các paper** — dùng làm **mốc so sánh / đặt kỳ vọng (baseline)**, **KHÔNG phải** kết quả hệ thống của team. Số thật của hệ team (RAGAS score, response time, cost, mAP…) **phải tự chạy mới có** — xem template ở [[Khung đo & Template kết quả (cho team)]] (deliverable B).
> Citation `[n]` khớp [[_Sources Master List]]. Mỗi số đều trích từ note tương ứng trong [01 - Literature/](01%20-%20Literature/).

## Bảng 1 — RAG: số liệu theo 6 tiêu chí Research Question

| Tiêu chí (RQ) | Số liệu / phát hiện đã công bố | Nguồn |
|---|---|---|
| **Retrieval accuracy** | Dense retrieval (DPR) vượt BM25 **+9–19%** tuyệt đối ở top-20 retrieval accuracy | [2] |
| | Chunking theo nội dung: Paragraph Group **nDCG@5 ≈ 0.459** vs tách ký tự **< 0.244** | [8] |
| | ColBERT (late interaction): nhanh hơn reranker BERT **~2 bậc độ lớn**, độ chính xác cạnh tranh | [34] |
| | FreshStack: mô hình retrieval "out-of-the-box" **thua oracle ở cả 5/5 chủ đề**; reranker **không cải thiện ở 2/5** | [31] |
| **Accuracy / Relevance (end-to-end)** | RAPTOR + GPT-4: **+20% absolute accuracy** trên QuALITY (multi-step QA) | [29] |
| | GraphRAG: cải thiện rõ **comprehensiveness & diversity** cho câu hỏi toàn cục (corpus ~1M token) | [28] |
| | MultiHop-RAG: RAG hiện tại **chưa đạt** với câu hỏi đa bước (cả retrieval lẫn reasoning) | [32] |
| **Hallucination** | RAGTruth: corpus **~18.000** câu trả lời, nhãn **mức từ**; detector nhỏ fine-tuned ≈ **GPT-4 prompt-based** | [21] |
| | Domain hạt nhân: RAG **giảm hallucination** & tăng độ chính xác so với ChatGPT thuần (đánh giá người + LLM) | [9] |
| | RAGAS đo **Faithfulness** reference-free; tương quan tốt với người (WikiEval) | [6] |
| **Source Traceability** | Attributed QA: hệ retrieve-then-read tốt nhất chỉ đạt **~65.5% AIS**; *correctness ≠ attribution* | [23] |
| | MIRAGE (model-internals): chất lượng trích dẫn **≈ self-citation** nhưng trung thực hơn, kiểm soát mịn hơn | [24] |
| **Response Time / Latency** | ColBERT pre-compute vector doc → tăng tốc truy vấn **~100×** so với cross-encoder | [34] |
| | Long-context LLM: context lớn **tăng độ trễ, giảm throughput**; RAG nhẹ hơn | [25] |
| **Cost** | RAG **rẻ hơn rõ rệt** long-context LLM ở cùng tác vụ; Self-Route đạt accuracy ~LC với cost thấp | [25] |
| | RAGBench: **RoBERTa fine-tuned > LLM-judge** ở tác vụ đánh giá → đánh giá rẻ hơn | [18] |
| | RAGTruth: fine-tune model nhỏ thay GPT-4 cho hallucination detection → giảm cost | [21] |
| **Custom vs Existing (baseline)** | Self-RAG (7B/13B) vượt ChatGPT & Llama2-chat tăng cường truy hồi trên QA/reasoning/fact-check | [4] |
| | CRAG cải thiện đáng kể các phương pháp RAG nền trên **4 dataset** (sinh ngắn & dài) | [30] |

## Bảng 2 — Đánh giá & độ tin cậy của phương pháp đo

| Vấn đề | Phát hiện | Nguồn |
|---|---|---|
| LLM-as-a-judge có thiên kiến | **position / verbosity / self-enhancement bias** → cần kiểm soát khi dùng RAGAS/ARES | [33] |
| Framework đánh giá | RAGAS (reference-free) [6]; AUEPORA (khung hợp nhất) [17]; ARES (ít nhãn, robust domain-shift) [19]; RAGChecker (tách lỗi retriever/generator, tương quan người cao) [20] | [6][17][19][20] |
| Trustworthiness | 6 chiều: factuality, robustness, fairness, transparency, accountability, privacy | [22] |
| Thực tế công nghiệp | 13 practitioner: ứng dụng chủ yếu QA chuyên ngành, **đánh giá vẫn chủ yếu thủ công** | [26] |

## Bảng 3 — Module Computer Vision (phát hiện lỗi tấm pin)

| Mô hình / nghiên cứu | Số liệu chính | Nguồn |
|---|---|---|
| YOLOv8 cải tiến (ảnh hồng ngoại) | PVEL-AD **mAP₅₀ 93.5%** (+19.5%), Recall 89.9%; PV-Multi mAP₅₀ 86.1% | [12] |
| So sánh v5/v8/v11 | v5 nhanh nhất **7.1 ms/ảnh**, precision 94.1% (nứt); v8 recall **79.2%** (bird drops); v11 **mAP@0.5 93.4%** | [13] |
| PV-YOLOv12n (ảnh EL) | **mAP@50 0.91** (PVEL-AD & Roboflow), nhỉnh hơn baseline YOLOv12n | [14] |

---

## Cách dùng các con số này trong paper
- Đặt ở **Related Work / Background** làm mốc "state-of-the-art hiện tại".
- Trong **Results**, đối chiếu số của hệ team với các mốc này (vd. "pipeline của chúng tôi đạt Faithfulness X, so với mốc tham chiếu của RAGBench…").
- **Tuyệt đối không** trình bày các số này như **kết quả của hệ team** — chúng là của paper khác, phải ghi `[n]`.

> ➡️ Bước tiếp: deliverable **B** — [[Khung đo & Template kết quả (cho team)]] (công thức metric + bảng trống để team chạy & điền số thật).
