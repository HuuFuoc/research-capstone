---
title: "Comparative Performance Evaluation of YOLOv5, YOLOv8, and YOLOv11 for Solar Panel Defect Detection"
authors: Khanam, R., Asghar, T. & Hussain, M.
year: 2025
venue: Solar 5(1):6 (MDPI) — bản preprint Preprints.org 202501.0788
tags: [literature, computer-vision, benchmark]
status: unread
url: https://www.preprints.org/manuscript/202501.0788
ref: 13
---

# Comparative Evaluation of YOLOv5 / v8 / v11 for Solar Panel Defect Detection

## Summary
So sánh trực tiếp **YOLOv5 / v8 / v11** trên tập lỗi tấm pin (bird droppings, cracks, dust): mỗi model có thế mạnh riêng — v5 nhanh nhất, v8 mạnh recall lỗi hiếm, v11 mAP cao & cân bằng nhất.

## Vai trò trong Capstone
- Benchmark để đặt kỳ vọng (expectation) và chọn model cho module CV.

## Key Contributions
- Đánh giá so sánh ba thế hệ YOLO trên cùng dataset & cùng metric (mAP, precision, recall, tốc độ).
- Chỉ ra tác động của **mất cân bằng dữ liệu** đến lỗi hiếm (bird drops).

## Methodology
- Huấn luyện/đo cùng dataset lỗi solar; báo cáo mAP@0.5, recall/precision theo lớp và thời gian suy luận.

## Results & Findings
- **YOLOv5:** suy luận nhanh nhất **7.1 ms/ảnh**, precision **94.1%** cho panel nứt.
- **YOLOv8:** recall lỗi hiếm tốt nhất — **bird drops 79.2%**.
- **YOLOv11:** **mAP@0.5 = 93.4%** (cao nhất, cân bằng); TP dusty 94%, panel 96%, cracked 92%.
- Lỗi phổ biến (dusty) đạt mAP@0.5 > 98%; **bird drops khó** do mất cân bằng dữ liệu.

## Limitations
- Dataset mất cân bằng theo lớp; kết quả phụ thuộc bộ dữ liệu & cấu hình huấn luyện cụ thể.

## Related Works
- [[11 - Hussain Khanam 2024 - YOLO for PV Defect]] · [[12 - 2025 - PV Defect Infrared YOLOv8]] · [[_Sources Master List]] · [[Smart Solar Platform - Capstone 2026]]

## My Notes & Critiques
- Gợi ý: dùng v11 cho mAP tổng thể, cân nhắc v8 nếu ưu tiên recall lỗi hiếm.

## Quotes
> "YOLOv8 excelled in recall for rare defects, such as bird drops (79.2%) ... YOLOv11 delivered the highest mAP@0.5 (93.4%)."

## References
Khanam, R., Asghar, T. & Hussain, M. (2025). *Comparative Performance Evaluation of YOLOv5, YOLOv8, and YOLOv11 for Solar Panel Defect Detection*. Solar, 5(1), 6. MDPI. Preprint: Preprints.org 202501.0788 (DOI:10.20944/preprints202501.0788.v1).
