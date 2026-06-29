---
title: "A Comprehensive Review of YOLO Architectures: From YOLOv1 to YOLOv8 and YOLO-NAS"
authors: Terven, J., Córdova-Esparza, D.-M. & Romero-González, J.-A.
year: 2023
venue: Machine Learning and Knowledge Extraction 5, 1680-1716
tags: [literature, computer-vision]
status: unread
url: https://www.mdpi.com/2504-4990/5/4/83
ref: 10
---

# A Comprehensive Review of YOLO Architectures (YOLOv1 → YOLOv8, YOLO-NAS)

## Summary
Tổng quan tiến hóa kiến trúc YOLO từ v1 đến v8, **YOLO-NAS** và YOLO kết hợp Transformer; bắt đầu từ metric chuẩn (IoU, mAP) và hậu xử lý (NMS), rồi phân tích thay đổi kiến trúc + mẹo huấn luyện qua từng phiên bản. Dùng để **biện minh việc chọn YOLOv8**.

## Vai trò trong Capstone
- Module Computer Vision — cơ sở lý do chọn YOLOv8 (cân bằng tốc độ/độ chính xác).

## Key Contributions
- Review có hệ thống toàn dòng YOLO, chuẩn hóa cách trình bày metric & postprocessing.
- Phân tích đổi mới kiến trúc và training tricks ở từng phiên bản.
- Thảo luận đánh đổi **tốc độ ↔ độ chính xác (mAP trên COCO)** giữa các biến thể.

## Methodology
- Dạng review tài liệu, không thực nghiệm gốc; hệ thống hóa theo dòng thời gian kiến trúc.

## Results & Findings
- YOLO trở thành hệ phát hiện đối tượng **thời gian thực** trung tâm cho robotics, xe tự lái, giám sát video.
- Mỗi phiên bản cải thiện đánh đổi tốc độ–độ chính xác nhờ thay đổi backbone/neck/head và training tricks.

## Limitations
- Cập nhật đến 2023 (chưa bao gồm YOLOv9/v10/v11/v12) → bổ sung bằng [[11 - Hussain Khanam 2024 - YOLO for PV Defect]].

## Related Works
- [[11 - Hussain Khanam 2024 - YOLO for PV Defect]] · [[_Sources Master List]] · [[Smart Solar Platform - Capstone 2026]]

## My Notes & Critiques
- Dùng để mô tả bối cảnh & lý do chọn YOLOv8 trong phần CV của paper.

## Quotes
> "YOLO has become a central real-time object detection system for robotics, driverless cars, and video monitoring applications."

## References
Terven, J., Córdova-Esparza, D.-M. & Romero-González, J.-A. (2023). *A Comprehensive Review of YOLO Architectures in Computer Vision: From YOLOv1 to YOLOv8 and YOLO-NAS*. Machine Learning and Knowledge Extraction, 5(4), 1680–1716. arXiv:2304.00501.
