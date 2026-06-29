---
title: Smart Solar Installation, Monitoring and Maintenance Platform
tags: [moc, project, capstone]
year: 2026
institution: FPT University
team: [SE180466, SE180579, SE184144, SE180271]
status: active
---

# Smart Solar Installation, Monitoring and Maintenance Platform

> Capstone Project 2026 — FPT University
> Team: SE180466, SE180579, SE184144, SE180271

## Research Question

> ⚠️ Phiên bản đã chỉnh (2026-06-29): chuyển từ "so sánh/chứng minh" → "thiết kế & đánh giá"; định nghĩa rõ "custom"; chốt baseline cụ thể; chuẩn hóa thuật ngữ theo RAGAS. Bản gốc xem lịch sử git. Chi tiết: [[Design & Evaluation Protocol - v2]].

**RQ chính:** So với (i) **plain LLM** (không retrieval) và (ii) **naive RAG** (chunk cố định, không rerank), một **RAG pipeline tinh chỉnh theo tài liệu O&M điện mặt trời** cải thiện **faithfulness, answer relevancy và context precision** (đo bằng RAGAS [6]) đến mức nào, và đánh đổi **độ trễ / chi phí** ra sao?

**Sub-RQ (tùy chọn):** mức độ **truy nguồn (source traceability)** của pipeline tinh chỉnh — đo định tính trên tập nhỏ.

> "Custom" được **định nghĩa cụ thể** trong Methodology (content-aware chunking [8] + rerank + prompt theo domain), không dùng chung chung.

### Phạm vi (Scope)
- **Trọng tâm bài báo:** RAG knowledge assistant cho lắp đặt / vận hành / bảo trì điện mặt trời.
- **Ngoài phạm vi bài báo này:** Module **Computer Vision** (Python + OpenCV + YOLOv8 phát hiện lỗi bề mặt tấm pin) — phát triển như **module/demo sản phẩm riêng**, *không* tính là đóng góp khoa học của bài báo RAG này. Nền tảng tham khảo: [[Related Work - Draft v1 (VN)]] §H.

## Nguồn tài liệu — tổng quan

Chi tiết đầy đủ: [[_Sources Master List]] (trong `01 - Literature`).

| Nhóm | Chủ đề | Số nguồn |
|------|--------|----------|
| 1 | Nền tảng RAG (bắt buộc cite) | 5 |
| 2 | Đánh giá RAG (phục vụ Research Question) | 4 |
| 3 | Computer Vision — phát hiện lỗi tấm pin | 5 |
| 4 | Bối cảnh ngành Solar & Digitalization | 2 |

## Ánh xạ: Tiêu chí đánh giá → Nguồn

> Thuật ngữ đã chuẩn hóa theo RAGAS [6] — bỏ "accuracy" lỏng lẻo cho RAG QA. "Hallucination reduction" diễn đạt lại thành **faithfulness** (đo trực tiếp được), tránh ngụ ý có before/after.

| Tiêu chí (đo được) | Nguồn chính |
|------------------|-------------|
| Faithfulness (chống bịa) | RAGAS [6], Ji et al. [7] |
| Answer Relevancy | RAGAS [6], Gao et al. Survey [3] |
| Context Precision / Recall | RAGAS [6], DPR [2], Chunking [8] |
| Source Traceability (định tính, tập nhỏ) | Bohnet [23] (AIS), Lewis [1] |
| Response Time (latency p50/p95) | đo trực tiếp; bối cảnh [8] |
| Cost (ước tính token × giá API) | đo trực tiếp; bối cảnh [25] |
| Baseline so sánh | **Plain LLM + Naive RAG** (có kiểm soát) |

> Module CV (Hussain & Khanam [11], YOLOv8 IR [12], so sánh model [13]) — **ngoài phạm vi bài báo RAG**, làm như module riêng.

## Thứ tự ưu tiên đọc

**Bước 1 — Nền tảng RAG (cả team)**
- Lewis et al. [1] — RAG gốc hoạt động thế nào
- Gao et al. Survey [3] — phân biệt Naive / Advanced / Modular RAG
- Karpukhin et al. [2] — Dense Retrieval & dual-encoder

**Bước 2 — Đánh giá & so sánh (người làm research)**
- RAGAS [6] — cài đặt & chạy thử trước khi design experiment
- Ji et al. [7] — hiểu hallucination để định nghĩa faithfulness đúng
- Self-RAG [4] — đọc để **định vị** đóng góp (kiến trúc self-reflective); ⚠️ *không* chạy làm baseline trong bài này (baseline thực = Plain LLM + Naive RAG). Self-RAG là "discussed, not benchmarked".

**Bước 3 — Computer Vision (team CV, MODULE RIÊNG — ngoài bài báo RAG)**
- Hussain & Khanam [11] — survey đủ để justify chọn YOLOv8
- PeerJ paper [12] — methodology & dataset reference cụ thể
- So sánh model [13] — benchmark để set expectation

## Quy trình NotebookLM (tổng hợp tài liệu)

> Tool `mcp__notebooklm__*` chỉ hoạt động sau khi **reload Claude Code + `setup_auth`**.

- [ ] Reload Claude Code để nạp tool NotebookLM MCP
- [ ] Chạy `setup_auth` — đăng nhập Google/NotebookLM 1 lần
- [ ] Tạo notebook rỗng trong web NotebookLM → copy share-URL
- [ ] `add_notebook <share-url>` → import vào library
- [ ] `add_source` từng URL trong [[_Sources Master List]] (16 nguồn)
- [ ] `ask_question` để tổng hợp theo từng nhóm tiêu chí
- [ ] Viết synthesis note vào `02 - Notes`

## Liên kết

- Nguồn: [[_Sources Master List]]
- Quay lại: [[Home]]
