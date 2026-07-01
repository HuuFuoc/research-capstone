# CLAUDE.md — Smart Solar Capstone (research vault)

Obsidian vault cho **capstone FPT 2026**. Đây là **dự án viết nghiên cứu** (Markdown),
không phải code — không có lệnh build/test/deploy. Sản phẩm: bài báo khoa học về trợ lý
**RAG tùy biến theo miền** cho vận hành–bảo trì (O&M) điện mặt trời.

## Phạm vi
- Bài báo **chỉ RAG**. Module thị giác máy tính (YOLO phát hiện lỗi tấm pin) đã **tách ra**,
  không thuộc bài này (nguồn [10]–[14] còn trong master list nhưng không cite).
- Loại bài: **Design & Evaluation** (đề xuất pipeline + giao thức đánh giá), không viết như
  "hệ thống đã hoàn thiện".

## Cấu trúc vault
- `00 - Index/` — home/MOC
- `01 - Literature/` — mỗi nguồn 1 note, đánh số `01`–`34`; index: `_Sources Master List.md`
- `02 - Notes/` — bài báo + tài liệu làm việc (draft, references, outline, protocol, verify log)
- `03 - Projects/`, `04 - Resources/`, `Templates/`

## File chủ chốt
- Bài báo: `02 - Notes/Bản đọc thử - Paper Draft (Smart Solar RAG).md`
- References (Harvard, 34 nguồn): `02 - Notes/References (Harvard) - Smart Solar (34 nguồn).md`
- Master source list: `01 - Literature/_Sources Master List.md`
- Outline: `02 - Notes/Paper Outline - Smart Solar Capstone.md`
- Giao thức đánh giá: `02 - Notes/Design & Evaluation Protocol - v2.md`

## Quy ước (bắt buộc theo)
- **Citation = Harvard (tác giả–năm)**, KHÔNG dùng IEEE đánh số `[n]`. Danh mục: ≤3 tác giả
  liệt kê đủ, ≥4 dùng `et al.` In-text: 1–2 tác giả nêu tên, ≥3 dùng `et al.` Trùng họ phải
  kèm initial (`Li, D.` vs `Li, Z.`).
- Giữ **tách bạch** nhãn trạng thái **[Proposed] / [Plan] / [Result]** trong bài — không gộp,
  không xoá cho tới bản nộp cuối.
- Ngôn ngữ: thân bài tiếng Việt + một Abstract tiếng Anh.

## Gotcha
- **Không bao giờ bịa số liệu nghiên cứu.** Results (§6) và mọi cấu hình `[team chốt]` để trống
  có chủ đích tới khi team chạy hệ thống thật. Bịa số = gian lận → bị reject/retract.
- Có **nhiều vault Obsidian lồng nhau** — luôn làm trong vault `research-capstone`.
- Plugin **Dataview** + **Copilot** cài thủ công; một số note dùng khối mã `dataview` (đừng xoá).
- **NotebookLM MCP**: `ask_question` chạy tốt (grounded); `add_source` hỏng → thêm nguồn thủ công.
- **Venue mục tiêu chưa chốt**; nếu venue yêu cầu IEEE numbered thì phải convert references Harvard.

## Git
- Repo cá nhân; lịch sử commit trực tiếp vào `main`.
