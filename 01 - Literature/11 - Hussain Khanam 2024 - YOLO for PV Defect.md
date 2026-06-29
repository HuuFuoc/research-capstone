---
title: "In-Depth Review of YOLOv1 to YOLOv10 Variants for Enhanced Photovoltaic Defect Detection"
authors: Hussain, M. & Khanam, R.
year: 2024
venue: Solar 4, 351-386 (MDPI)
tags: [literature, computer-vision, key]
status: unread
url: https://www.mdpi.com/2673-9941/4/3/18
ref: 11
---

# In-Depth Review of YOLOv1 → YOLOv10 for Photovoltaic Defect Detection

## Summary
Review chuyên sâu YOLOv1→**YOLOv10** với trọng tâm **kiểm tra chất lượng tấm pin (PV)**: chỉ ra động lực thành công của từng biến thể (PAN, GELAN, PGI ở YOLOv10 ra mắt 5/2024) và dự báo xu hướng dùng **cơ chế attention** cho lỗi tinh vi. **Liên quan trực tiếp nhất** với module CV của đề tài.

## Vai trò trong Capstone
- Tiêu chí phục vụ: **Computer Vision Module** — survey đủ để biện minh chọn YOLOv8 và định vị so với v9/v10.

## Key Contributions
- Khảo sát tiến hóa YOLO gắn riêng với bài toán phát hiện lỗi PV.
- Hệ thống đóng góp kiến trúc từng phiên bản (path aggregation network → GELAN → programmable gradient information).
- Dự báo hướng nghiên cứu: mở rộng nhiều loại lỗi PV + tích hợp attention.

## Methodology
- Review tài liệu; phân tích so sánh đặc tính kiến trúc và phù hợp với đặc thù ảnh PV.

## Results & Findings
- Cách tiếp cận **single-stage** của YOLO được ưa chuộng nhờ hiệu quả (tốc độ) cho kiểm tra PV.
- Attention mechanism được kỳ vọng nâng khả năng phát hiện lỗi nhỏ/tinh vi.

## Limitations
- Là review (không thực nghiệm thống nhất); cập nhật đến YOLOv10 (5/2024).

## Related Works
- [[10 - Terven 2023 - YOLO Architectures Review]] · [[12 - 2025 - PV Defect Infrared YOLOv8]] · [[13 - 2025 - Comparative YOLOv5 v8 v11]] · [[_Sources Master List]] · [[Smart Solar Platform - Capstone 2026]]

## My Notes & Critiques
- Nguồn chủ lực cho phần "lý do chọn YOLO cho PV" trong Related Work của module CV.

## Quotes
> "YOLO's single-stage approach to object detection has made it a preferred option due to its efficiency [for PV quality inspection]."

## References
Hussain, M. & Khanam, R. (2024). *In-Depth Review of YOLOv1 to YOLOv10 Variants for Enhanced Photovoltaic Defect Detection*. Solar, 4(3), 351–386. MDPI.
