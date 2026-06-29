---
title: "Photovoltaic panel defect detection based on infrared imaging and improved YOLOv8"
authors: Wang, J. & Cheng, Z.
year: 2025
venue: PeerJ Computer Science
tags: [literature, computer-vision]
status: unread
url: https://pmc.ncbi.nlm.nih.gov/articles/PMC12190611
ref: 12
---

# Photovoltaic Panel Defect Detection Based on Infrared Imaging and Improved YOLOv8

## Summary
Cải tiến **YOLOv8** cho phát hiện lỗi tấm pin trên **ảnh hồng ngoại (infrared)** — xử lý nền phức tạp, đặc trưng lỗi mờ và mất cân bằng độ khó. Kết quả thực nghiệm mạnh trên hai bộ dữ liệu PV.

## Vai trò trong Capstone
- Methodology & dataset reference cụ thể cho module CV (kiến trúc cải tiến + loss + dataset chuẩn).

## Key Contributions
- **Multi-Channel Squeeze-and-Excitation (MCSE)** gắn vào neck → tăng trích đặc trưng.
- **GhostConv + BoTNet** trong backbone → giảm tham số mà vẫn tăng hiệu năng.
- **Focaler-CIoU** loss → xử lý mất cân bằng độ khó mẫu trong hồi quy bounding box.

## Methodology
- Nền YOLOv8 + ba cải tiến trên; huấn luyện/đánh giá trên 2 dataset PV (hồng ngoại + EL).

## Results & Findings
- **PVEL-AD** (4.997 ảnh, 11 lớp lỗi): mAP₅₀ **93.5%** (+19.5%), mAP₅₀₋₉₅ 68.0%, Precision 88.3%, Recall 89.9%.
- **PV-Multi-Defect** (1.106 ảnh, 5 lớp): mAP₅₀ **86.1%** (+4.8%), Recall 81.6% (+10.4%).
- Tăng độ chính xác trong khi giữ gần như nguyên số tham số.

## Limitations
- Tối ưu cho ảnh hồng ngoại/EL cụ thể; tổng quát sang điều kiện hiện trường khác cần kiểm chứng.

## Related Works
- [[11 - Hussain Khanam 2024 - YOLO for PV Defect]] · [[14 - 2025 - Optimized YOLO EL Images]] · [[_Sources Master List]] · [[Smart Solar Platform - Capstone 2026]]

## My Notes & Critiques
- Bộ dữ liệu PVEL-AD và các lớp lỗi (cracks, black core, finger...) là tham chiếu tốt cho dataset của capstone.

## Quotes
> "[The approach addresses] high missed detection rates, complex backgrounds, unclear defect features, and uneven difficulty levels in ... photovoltaic panel defect detection."

## References
Wang, J. & Cheng, Z. (2025). *Photovoltaic panel defect detection based on infrared imaging and improved YOLOv8*. PeerJ Computer Science. PMC12190611.
