---
title: Paper Outline — Smart Solar Capstone
tags: [note, paper, outline]
status: draft
created: 2026-06-24
---

# Paper Outline — Smart Solar Platform (Capstone 2026)

> Khung bài báo hướng tới **submit**. Mỗi mục ghi rõ: viết được từ literature (✅ tôi làm được) vs cần **dữ liệu/hệ thống thật của team** (⚠️ chỉ team cung cấp).
> Dự án: [[Smart Solar Platform - Capstone 2026]] · Nguồn: [[_Sources Master List]]

## ⚠️ Sự thật quan trọng về "bài báo nhận được submit"
Một bài báo được chấp nhận **không thể** viết hoàn toàn từ literature. Nó cần **đóng góp mới + kết quả thực nghiệm thật**. Tôi viết được: Introduction, Related Work, Methodology (thiết kế), Evaluation design. Tôi **không** bịa được: số liệu thí nghiệm, kết quả hệ thống thật — phần này team phải chạy và cung cấp. Bịa số liệu = gian lận nghiên cứu, paper sẽ bị reject/retract.

## Định hướng bài báo (đã chốt 2026-06-29)
- **Loại bài:** *Design & Evaluation* — trình bày **thiết kế pipeline + giao thức đánh giá** và (khi có) **kết quả sơ bộ**. KHÔNG viết như "hệ thống đã hoàn thiện".
- **Trọng tâm duy nhất:** RAG (chỉ RAG). **Module CV đã tách ra** khỏi bài báo này.
- **Baseline thực sự chạy:** Plain LLM + Naive RAG. (Self-RAG/CRAG/GraphRAG/RAPTOR = *discussed, not benchmarked*.)
- 3 mức trạng thái phải tách bạch trong bài: **[Proposed]** (đề xuất) · **[Plan]** (kế hoạch thực nghiệm) · **[Result]** (số liệu thật của team).
- Chi tiết RQ/Objectives/Methodology/Metrics: [[Design & Evaluation Protocol - v2]].

## Cấu trúc đề xuất (IEEE/ACM conference style — RAG-only)

> 📌 **Chuẩn trích dẫn đã chốt: Harvard (tác giả–năm)** theo [[References (Harvard) - Smart Solar (34 nguồn)]] — bài **không** dùng citation đánh số `[n]` kiểu IEEE; cụm "IEEE/ACM" ở đây chỉ nói về **bố cục/đánh số mục**. Nếu venue cuối yêu cầu IEEE numbered, chuyển đổi sau khi chốt venue.
>
> 📐 **Ánh xạ mục theo bản thảo hiện hành:** 1 Introduction · 2 Related Work · **3 Problem & RQ** · **4 System Design & Methodology (gộp)** · 5 Evaluation Setup · 6 Results & Discussion · 7 Limitations · 8 Conclusion (Abstract không đánh số). Bảng dưới là khung kế hoạch gốc.

| # | Section | Nguồn nội dung | Trạng thái |
|---|---------|----------------|-----------|
| 1 | **Abstract** | Tóm tắt sau khi có kết quả | ⚠️ cuối cùng |
| 2 | **Introduction** | Vấn đề (LLM bịa/không truy nguồn trong domain kỹ thuật), đóng góp | ✅ draft được |
| 3 | **Related Work** | [1]–[30] | ✅ [[Related Work - Draft v1 (VN)]] |
| 4 | **System Design [Proposed]** | Pipeline RAG (retriever + generator) | 🟡 design ✅ / config thật ⚠️ [team chốt] |
| 5 | **Methodology [Proposed/Plan]** | DPR [2], chunking [8], kiến trúc [3]; định nghĩa "custom" | 🟡 design ✅ / config thật ⚠️ |
| 6 | **Evaluation Setup [Plan]** | RAGAS [6], test set, baseline Plain LLM + Naive RAG | ✅ design được |
| 7 | **Results & Discussion [Result]** | Đo trên hệ thống thật | ⚠️ **team phải chạy — không bịa** |
| 8 | **Limitations** | N nhỏ, single-config, domain hẹp | ✅ viết được |
| 9 | **Conclusion & Future Work** | [5]; CV, baseline nâng cao, AIS | ✅ sau khi có results |

## Research Question (đã chỉnh)
So với **plain LLM** và **naive RAG**, một RAG pipeline **tinh chỉnh theo tài liệu O&M điện mặt trời** cải thiện **faithfulness, answer relevancy, context precision** (RAGAS [6]) đến mức nào, và đánh đổi **latency/cost** ra sao? (Sub-RQ: source traceability — định tính, tập nhỏ.) Đầy đủ: [[Design & Evaluation Protocol - v2]].

## Đóng góp (Contributions) — đã thu hẹp
- **C1 [Proposed]:** RAG pipeline tinh chỉnh cho domain điện mặt trời, với "custom" định nghĩa rõ (content-aware chunking + rerank + prompt domain).
- **C2 [Plan→Result]:** Giao thức đánh giá reference-free (RAGAS [6]) so pipeline với 2 baseline có kiểm soát trên test set domain.
- **C3 (tùy chọn) [Result]:** Test set Q&A domain solar (tiếng Việt) làm tài nguyên đánh giá.
- ~~CV module~~ → **đã tách**, không phải đóng góp của bài này.

## Việc cần team cung cấp để hoàn thiện paper
1. Mô tả kiến trúc hệ thống thật (sơ đồ; **[team chốt]** embedding model, vector DB, LLM, nguồn tài liệu).
2. Test set: số câu hỏi, ai tạo gold answer, quy trình đối chiếu (xem [[Design & Evaluation Protocol - v2]]).
3. Kết quả thí nghiệm: RAGAS scores (faithfulness/answer relevancy/context precision), latency p50/p95, token-cost.
4. Venue mục tiêu (hội nghị/tạp chí nào? IEEE? student track? hạn nộp?) → quyết định format & độ dài.

## Việc tôi (research) làm tiếp được ngay
- Verify full-text các con số trong Related Work (chống lỗi trích dẫn) → xem caveat trong [[Related Work - Draft v1 (VN)]].
- Viết Introduction draft theo khung problem→gap→contribution.

## Next actions
- [ ] Team cung cấp share-URL NotebookLM → nạp 16 nguồn → tổng hợp sâu Related Work
- [ ] Chốt venue mục tiêu & deadline
- [ ] Viết Introduction draft
