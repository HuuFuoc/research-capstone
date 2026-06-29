---
title: Khung đo & Template kết quả (cho team chạy)
tags: [note, paper, evaluation, methodology, template]
status: template
created: 2026-06-29
---

# Khung đo & Template kết quả — để team chạy & điền số thật

> Mục đích: chuẩn hoá cách đo để trả lời Research Question (custom RAG vs existing). **Tôi thiết kế khung & để bảng trống; team chạy hệ thật rồi điền số** — số đo là đóng góp thực nghiệm, không được bịa.
> Thuật ngữ khó: xem [[Bảng thuật ngữ (Glossary)]]. Mốc tham chiếu: [[Số liệu Benchmark từ Literature]].

## 1. Các hệ thống đem so sánh (conditions)
| Ký hiệu | Hệ thống | Vai trò |
|---|---|---|
| **OURS** | Custom RAG pipeline (của team) | Hệ cần đánh giá |
| B1 | Plain LLM (không RAG) | Baseline thấp nhất [9] |
| B2 | Long-context LLM (nhồi tài liệu vào prompt) | Existing solution [25] |
| B3 | Self-RAG | Baseline self-reflective [4] |
| B4 | CRAG (Corrective RAG) | Baseline self-correcting [30] |

> Tối thiểu nên có **OURS + B1 + (B2 hoặc B3)**. Càng nhiều baseline càng thuyết phục.

## 2. Bộ dữ liệu test (team phải tạo)
- Tập **Q&A vàng (gold set)** trên tài liệu dự án: tối thiểu **50–100 câu hỏi**, mỗi câu có: câu hỏi, **đáp án chuẩn**, **đoạn nguồn (ground-truth context)**.
- Nên phủ nhiều loại: factoid (1 đoạn), tổng hợp (multi-hop [32]), câu "không trả lời được" (kiểm chống bịa).
- Tham khảo cách tự dựng benchmark trên tài liệu kỹ thuật: [31] (FreshStack).

## 3. Sáu tiêu chí → cách đo

| # | Tiêu chí | Metric cụ thể | Công cụ / công thức | Ghi chú |
|---|---|---|---|---|
| 1 | **Accuracy** | Answer Correctness | RAGAS *answer correctness*, hoặc LLM-judge/người chấm Đúng/Sai trên gold set | Nếu dùng LLM-judge: kiểm soát bias [33] |
| 2 | **Context Relevance** | Context Precision & Recall | RAGAS *context precision / recall* | Đo chất lượng retriever |
| 3 | **Hallucination** | Hallucination rate | = **1 − Faithfulness** (RAGAS), hoặc % câu có claim không được ngữ cảnh hỗ trợ (kiểu RAGTruth [21]) | Càng thấp càng tốt |
| 4 | **Source Traceability** | AIS / Citation precision-recall | % câu trả lời **quy đúng về nguồn** (AIS [23]); hoặc precision/recall của trích dẫn | Cần pipeline có xuất nguồn |
| 5 | **Response Time** | Latency (ms) | Đo **end-to-end** mỗi truy vấn: ghi mean **và p95**; lặp ≥3 lần | Ghi rõ phần cứng/model |
| 6 | **Cost** | $ / truy vấn | (tokens_in × giá_in + tokens_out × giá_out) + phí embedding/rerank | Quy về **$/100 truy vấn** cho dễ so |

## 4. TEMPLATE BẢNG KẾT QUẢ (team điền)

### Bảng chính — so sánh theo 6 tiêu chí
| Hệ thống | Accuracy ↑ | Context Precision ↑ | Faithfulness ↑ | Hallucination rate ↓ | Traceability (AIS) ↑ | Latency mean/p95 (ms) ↓ | Cost ($/100q) ↓ |
|---|---|---|---|---|---|---|---|
| **OURS** | | | | | | / | |
| B1 — Plain LLM | | | | | | / | |
| B2 — Long-context | | | | | | / | |
| B3 — Self-RAG | | | | | | / | |
| B4 — CRAG | | | | | | / | |

### Bảng phụ — cấu hình hệ OURS (ghi để tái lập)
| Thành phần | Lựa chọn (điền) |
|---|---|
| Embedding model | |
| Vector DB | |
| Chunking (loại + kích thước) | |
| Top-k / reranker | |
| LLM sinh | |
| Phần cứng đo latency | |

### Bảng module CV (nếu paper gộp) — mAP/Recall thực của team
| Model | mAP@0.5 ↑ | mAP@0.5:0.95 ↑ | Precision ↑ | Recall ↑ | Inference (ms) ↓ |
|---|---|---|---|---|---|
| (YOLO của team) | | | | | |

## 5. Quy trình chạy (gợi ý)
1. Chốt gold set (mục 2) + đóng băng phiên bản tài liệu.
2. Chạy từng hệ trên cùng gold set, **lặp ≥3 lần** lấy trung bình (cho latency/cost).
3. Tính metric bằng RAGAS (mục 3) + đo latency/cost thủ công.
4. Nếu dùng LLM-judge: tách *reasoning* khỏi *scoring*, cố định prompt, nêu rõ trong paper để chống nghi vấn bias [33].
5. Báo cáo cả **độ lệch** (std) và, nếu được, **kiểm định ý nghĩa thống kê** giữa OURS và baseline.

> ➡️ Điền xong bảng mục 4 → đó chính là phần **Results** của paper. Đối chiếu với mốc ở [[Số liệu Benchmark từ Literature]] trong phần Discussion.
