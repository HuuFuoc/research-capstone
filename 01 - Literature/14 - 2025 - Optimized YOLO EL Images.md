---
title: "Optimized YOLO based model for photovoltaic defect detection in electroluminescence images"
authors: Achit Mohamed, Yassa Nacera, Bouzida Ahcene, Ali Teta, El Ouanas Belabbaci, Abdelaziz Rabehi, Yousef A. Alsabah, Mohamed Benghanem
year: 2025
venue: Scientific Reports 15:32955 (Nature) — DOI 10.1038/s41598-025-13956-7
tags: [literature, computer-vision]
status: unread
url: https://www.nature.com/articles/s41598-025-13956-7
ref: 14
---

# Optimized YOLO Based Model for PV Defect Detection in Electroluminescence Images

## Summary
Giới thiệu **PV-YOLOv12n** — biến thể tối ưu của **YOLOv12n** cho phát hiện lỗi trên **ảnh điện phát quang (EL)** của tấm pin. Thêm module **A2C2f tại tầng P5** để ưu tiên vùng lỗi quan trọng, tăng recall/precision cho vết nứt lớn, lệch vị trí và bất nhất vật liệu.

## Vai trò trong Capstone
- Methodology cho pipeline xử lý ảnh EL (kiến trúc YOLO mới + module attention/feature).

## Key Contributions
- Đề xuất PV-YOLOv12n: tinh chỉnh YOLOv12n cho domain EL.
- Module **A2C2f** ở P5 (1024, True) tăng trích đặc trưng, tập trung vùng lỗi.

## Methodology
- Nền YOLOv12n + A2C2f; huấn luyện/đánh giá trên **PVEL-AD** và một bộ **Roboflow**.

## Results & Findings
- PV-YOLOv12n đạt **mAP@50 = 0.91** trên cả PVEL-AD và Roboflow.
- Vượt baseline YOLOv12n (mAP@50 0.90 trên PVEL-AD, 0.88 trên Roboflow).

## Limitations
- Cải thiện so với baseline còn khiêm tốn (+0.01–0.03 mAP); gắn với đặc thù ảnh EL.

## Related Works
- [[12 - 2025 - PV Defect Infrared YOLOv8]] · [[11 - Hussain Khanam 2024 - YOLO for PV Defect]] · [[_Sources Master List]] · [[Smart Solar Platform - Capstone 2026]]

## My Notes & Critiques
- ⚠️ Tên người Algeria: rà lại thứ tự **họ/tên** (given/family) theo metadata Nature trước khi format citation (vd. tác giả đầu có thể là *Mohamed, A.*).
- Cho thấy xu hướng dùng YOLOv12 + module attention cho EL.

## Quotes
> "PV-YOLOv12n ... incorporates an A2C2f module at the P5 scale, which enhances feature extraction by prioritizing critical defect regions."

## References
Achit, M., Yassa, N., Bouzida, A., Teta, A., Belabbaci, E. O., Rabehi, A., Alsabah, Y. A. & Benghanem, M. (2025). *Optimized YOLO based model for photovoltaic defect detection in electroluminescence images*. Scientific Reports, 15, 32955. DOI:10.1038/s41598-025-13956-7. [⚠️ rà thứ tự họ/tên khi cite]
