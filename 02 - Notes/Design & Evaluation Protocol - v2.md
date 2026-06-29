---
title: Design & Evaluation Protocol — v2 (Custom RAG, Smart Solar)
tags: [note, paper, methodology, protocol]
status: draft
created: 2026-06-29
---

# Design & Evaluation Protocol — v2

> Phiên bản đã sửa sau review học thuật (2026-06-29). Thay thế cách phát biểu cũ ("so sánh/chứng minh custom RAG vs existing solutions") bằng khung **thiết kế + đánh giá** chặt chẽ, khả thi cho nhóm sinh viên mới.
> Dự án: [[Smart Solar Platform - Capstone 2026]] · Khung bài: [[Paper Outline - Smart Solar Capstone]] · Nguồn: [[_Sources Master List]]

> **3 nhãn trạng thái** dùng xuyên suốt — không được lẫn lộn:
> - **[Proposed]** = đề xuất/thiết kế (viết được từ literature).
> - **[Plan]** = kế hoạch thực nghiệm (cách sẽ đo).
> - **[Result]** = số liệu thật của team (⚠️ **chỉ điền sau khi chạy — tuyệt đối không bịa**).

---

## 1. Research Problem

Tài liệu lắp đặt – vận hành – bảo trì (O&M) điện mặt trời nằm rải rác trong nhiều sổ tay kỹ thuật dài. LLM thường trả lời trôi chảy nhưng **dễ đưa thông tin không được nguồn hỗ trợ (hallucination)** và **không truy được về nguồn (no traceability)** — rủi ro cao trong ngữ cảnh kỹ thuật, nơi câu trả lời sai có thể dẫn tới lắp/vận hành sai. RAG được kỳ vọng giảm các vấn đề này [1][3][7], nhưng **chưa rõ** một pipeline RAG **tinh chỉnh theo tài liệu dự án** cải thiện *bao nhiêu* về độ trung thực và truy nguồn so với (a) LLM thường và (b) RAG mặc định, **trên dữ liệu solar (ưu tiên tiếng Việt)**, và với **đánh đổi chi phí/độ trễ** ra sao.

## 2. Research Question

**RQ (chính):** So với (i) **plain LLM** (không retrieval) và (ii) **naive RAG** (chunk cố định, không rerank), một **RAG pipeline tinh chỉnh** theo tài liệu O&M điện mặt trời cải thiện **faithfulness, answer relevancy và context precision** (đo bằng RAGAS [6]) đến mức nào, và đánh đổi **latency / cost** ra sao?

**Sub-RQ (tùy chọn):** Pipeline tinh chỉnh đạt mức **source traceability** thế nào (đo định tính trên tập nhỏ, khung AIS [23])?

> Lưu ý phát biểu: dùng **"evaluate / investigate"**, KHÔNG dùng "prove". Đây là câu hỏi *đo lường có kiểm soát*, không phải tuyên bố thắng/thua.

## 3. Định nghĩa "Custom" (chống mơ hồ)

"Custom RAG" = naive RAG **cộng** các thay đổi cụ thể, mỗi thay đổi truy nguồn được về literature:

| Thành phần | Naive (baseline) | Custom (đề xuất) | Căn cứ |
|---|---|---|---|
| Chunking | Cố định ~512 token | **Content-aware** (theo cấu trúc tài liệu) | [8] |
| Retrieval | Vector top-k đơn | Vector + **re-rank** (và/hoặc hybrid keyword) | [2][27] |
| Prompt | Chung | **Prompt theo domain** O&M solar | [3] |
| (tùy chọn) Truy nguồn | Không | Trả về **trích dẫn nguồn** kèm câu trả lời | [1][23] |

> ⚠️ Phải **cố định** đúng các khác biệt này; mọi yếu tố khác (LLM, tài liệu, top-k cuối, test set) **giữ giống nhau** giữa các nhánh để so sánh công bằng.

## 4. Research Objectives (đo được)

- **O1 [Proposed]** — Thiết kế & hiện thực RAG pipeline tinh chỉnh (mục 3) cho corpus O&M solar.
- **O2 [Plan]** — Xây **test set** Q&A domain (mục 6) có câu trả lời tham chiếu do team đối chiếu.
- **O3 [Plan→Result]** — Đánh giá pipeline vs **Plain LLM** + **Naive RAG** bằng RAGAS [6] (faithfulness, answer relevancy, context precision) + latency + cost.
- **O4 (tùy chọn) [Result]** — Phân tích lỗi retriever vs generator bằng RAGChecker [20]; đánh giá traceability định tính (sub-RQ).

> Ánh xạ kiểm tra nhất quán: O1→C1, O2/O3→C2, O4→C3. Mỗi Objective có ≥1 metric ở mục 5.

## 5. Evaluation Metrics

| Metric | Đo bằng | Trả lời tiêu chí | Khả thi |
|---|---|---|---|
| **Faithfulness** | RAGAS [6] | chống bịa (hallucination) | ✅ chạy được |
| **Answer Relevancy** | RAGAS [6] | relevance | ✅ |
| **Context Precision / Recall** | RAGAS [6] | chất lượng retrieval | ✅ |
| **Latency** (p50 / p95) | log thời gian end-to-end | response time | ✅ |
| **Cost** | đếm token × giá API | cost | ✅ (ước tính) |
| Source Traceability (AIS) | gán nhãn định tính, tập nhỏ [23] | traceability | 🟡 future / tập nhỏ |
| Hallucination rate (người gán) | annotate ~30–50 câu | bổ trợ faithfulness | 🟡 nếu đủ thời gian |

> ⚠️ Trước khi báo cáo: lấy **công thức chính xác** của Faithfulness / Answer Relevancy / Context Precision từ full-text RAGAS [6]; ghi rõ phiên bản thư viện & model dùng làm "judge".
> ⚠️ MIRAGE [24] cần **model mở** — chỉ áp dụng nếu pipeline dùng open LLM; nếu dùng API đóng thì traceability đo bằng cách khác (self-citation + kiểm thủ công).

## 6. Test Set [Plan] — điều kiện tiên quyết của mọi con số

- **Nguồn:** corpus tài liệu O&M solar của team ([team chốt nguồn & số tài liệu]).
- **Kích thước:** 50–100 câu Q&A (bắt đầu 50). Lý do nhỏ: nhóm mới, đảm bảo chất lượng nhãn.
- **Gold answer:** team viết/đối chiếu, ghi rõ **đoạn nguồn** chứa đáp án (phục vụ context precision & traceability).
- **Phân loại câu hỏi:** factoid / quy trình / đa-đoạn (multi-hop) — báo cáo theo nhóm nếu đủ mẫu.
- **Quy trình:** ≥2 người soạn độc lập rồi đối chiếu; ghi lại bất đồng. Đây là **dữ liệu thật**, không sinh bịa.

## 7. Methodology — Thiết kế thực nghiệm [Proposed/Plan]

**Cấu hình hệ thống ([team chốt] — để placeholder, không bịa):**

| Thành phần | Lựa chọn | Trạng thái |
|---|---|---|
| Embedding model | `[team chốt — vd model đa ngữ hỗ trợ tiếng Việt]` | ⚠️ chưa chốt |
| Vector DB | `[team chốt]` | ⚠️ chưa chốt |
| LLM sinh | `[team chốt — open hay API]` | ⚠️ chưa chốt |
| Re-ranker | `[team chốt / hoặc bỏ]` | ⚠️ chưa chốt |
| Corpus tài liệu | `[team chốt — số trang, ngôn ngữ]` | ⚠️ chưa chốt |

**Nhánh so sánh (cùng LLM, cùng corpus, cùng test set):**
1. **B0 — Plain LLM:** trả lời trực tiếp, không retrieval.
2. **B1 — Naive RAG:** chunk cố định 512, vector top-k, không rerank, prompt chung.
3. **P — Custom RAG:** thay đổi theo mục 3.

**Quy trình [Plan]:** chạy cả 3 nhánh trên cùng test set → thu RAGAS scores + latency + cost → báo cáo **trung bình ± độ lệch** trên test set; nếu đủ mẫu, kiểm định ý nghĩa thống kê (vd paired test). Nêu rõ **N nhỏ** là hạn chế.

**Reproducibility:** cố định seed/nhiệt độ LLM, ghi phiên bản thư viện, log prompt — để kết quả lặp lại được.

## 8. Results & Discussion [Result]

> ⚠️ **TRỐNG cho đến khi team chạy.** Không viết một con số nào ở đây trước khi có dữ liệu thật. Bịa số liệu = gian lận nghiên cứu → reject/retract.

Khung bảng sẽ điền (ví dụ cấu trúc, **chưa có số**):

| Nhánh | Faithfulness | Answer Rel. | Context Prec. | Latency p95 | Cost/query |
|---|---|---|---|---|---|
| B0 Plain LLM | — | — | — | — | — |
| B1 Naive RAG | — | — | — | — | — |
| P Custom RAG | — | — | — | — | — |

## 9. Limitations (viết được ngay — tăng độ tin cậy)

- Test set nhỏ (N=50–100), một domain, có thể ưu tiên tiếng Việt → **không khái quát hóa** ra mọi domain.
- Chỉ 2 baseline có kiểm soát; chưa đối chứng kiến trúc self-correcting (Self-RAG/CRAG) → *future work*.
- Một cấu hình "custom" duy nhất; chưa ablation từng thành phần.
- Đánh giá phụ thuộc LLM-as-judge của RAGAS → có thiên lệch; giảm thiểu bằng kiểm thủ công mẫu nhỏ [33].
- Traceability đo định tính, tập nhỏ.

## 10. Conclusion (mẫu an toàn — KHÔNG vượt kết quả)

> "Bài báo trình bày **thiết kế** một RAG pipeline tinh chỉnh cho domain O&M điện mặt trời và **một giao thức đánh giá reference-free** so với hai baseline có kiểm soát (plain LLM, naive RAG). [Khi có kết quả:] Trên test set N=…, pipeline cho thấy [xu hướng X về faithfulness/relevancy], với đánh đổi [latency/cost]. **Chúng tôi chưa khẳng định** ưu thế tổng quát; đánh giá với nhiều baseline, tập lớn hơn và đa domain là hướng tiếp theo. Module phát hiện lỗi tấm pin bằng thị giác máy tính được phát triển song song như một hướng mở rộng."

## 11. Checklist nhất quán (tự kiểm trước khi nộp)

- [ ] RQ (mục 2) ↔ Objectives (mục 4) ↔ Metrics (mục 5): mỗi tiêu chí trong RQ có đúng 1 metric đo được.
- [ ] Mọi baseline nêu trong bài = baseline **thực sự chạy** (B0, B1). Cái khác ghi rõ "discussed, not benchmarked".
- [ ] Không có số liệu nào ở §8 trước khi có dữ liệu thật.
- [ ] Conclusion không chứa từ "prove/chứng minh/tốt hơn" nếu chưa có kiểm định.
- [ ] Mọi con số trích từ literature đã verify full-text (xem checklist trong [[Related Work - Draft v1 (VN)]]).

## Liên kết
- [[Smart Solar Platform - Capstone 2026]] · [[Paper Outline - Smart Solar Capstone]] · [[Related Work - Draft v1 (VN)]] · [[_Sources Master List]]
