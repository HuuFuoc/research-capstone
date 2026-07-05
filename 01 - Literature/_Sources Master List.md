---
title: Sources Master List — Smart Solar Capstone 2026
tags: [literature, index, moc]
year: 2026
status: reference
---

# Sources Master List — Smart Solar Capstone 2026

> Dự án: [[Smart Solar Platform - Capstone 2026]]
> 34 nguồn, chia 6 nhóm. Block URL ở cuối file sẵn sàng nạp vào NotebookLM (`add_source`).
> 📖 Thuật ngữ khó hiểu? Xem [[Bảng thuật ngữ (Glossary)]].

## 🔬 Nhóm 1 — Nền tảng RAG (bắt buộc đọc & cite)

| # | Tài liệu | Link | Mục đích |
|---|----------|------|----------|
| 1 | Lewis, P. et al. (2020). *Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks*. NeurIPS 2020. | https://arxiv.org/abs/2005.11401 | Paper gốc định nghĩa RAG — cite bắt buộc cho Introduction & Related Works |
| 2 | Karpukhin, V. et al. (2020). *Dense Passage Retrieval for Open-Domain QA*. EMNLP 2020. | https://aclanthology.org/2020.emnlp-main.550 | Nền tảng Dense Retrieval — embedding & vector search |
| 3 | Gao, Y. et al. (2024). *Retrieval-Augmented Generation for LLMs: A Survey*. arXiv:2312.10997. | https://arxiv.org/abs/2312.10997 | Survey toàn cảnh — phân loại Naive/Advanced/Modular RAG |
| 4 | Asai, A. et al. (2023). *Self-RAG: Learning to Retrieve, Generate, and Critique*. ICLR 2024. | https://arxiv.org/abs/2310.11511 | Kiến trúc self-reflective để **định vị** đóng góp (discussed, not benchmarked — baseline thực = Plain LLM + Naive RAG) |
| 5 | Gupta, S., Ranjan, R. & Singh, S. N. (2024). *A Comprehensive Survey of RAG*. arXiv:2410.12837. | https://arxiv.org/abs/2410.12837 | Survey mới nhất — xu hướng & tương lai RAG |

## 📏 Nhóm 2 — Đánh giá RAG (phục vụ Research Question)

| # | Tài liệu | Link | Tiêu chí đo |
|---|----------|------|-------------|
| 6 | Es, S. et al. (2024). *RAGAs: Automated Evaluation of RAG*. EACL 2024 Demos. | https://aclanthology.org/2024.eacl-demo.16 | Framework chính: Faithfulness, Answer Relevancy, Context Precision |
| 7 | Ji, Z. et al. (2023). *Survey of Hallucination in NLG*. ACM Computing Surveys 55(12). | https://dl.acm.org/doi/10.1145/3571730 | Cơ sở lý thuyết cho hallucination rate |
| 8 | Shaukat, M. A., Adnan, M. & Kuhn, C. C. N. (2026). *A Systematic Investigation of Document Chunking Strategies and Embedding Sensitivity*. arXiv:2603.06976. | https://arxiv.org/abs/2603.06976 | Tối ưu chunking & embedding → response time, retrieval accuracy |
| 9 | Anwar, M., de Costa, M., Hammad, I. & Lau, D. (2024). *Evaluating ChatGPT on Nuclear Domain-Specific Data*. arXiv:2409.00090. | https://arxiv.org/abs/2409.00090 | Case study RAG vs. plain LLM trong domain-specific |

## 🔍 Nhóm 3 — Computer Vision & Phát hiện lỗi tấm pin

| # | Tài liệu | Link | Mục đích |
|---|----------|------|----------|
| 10 | Terven, J. et al. (2023). *A Comprehensive Review of YOLO Architectures (v1→v8, YOLO-NAS)*. MAKE 5. | https://www.mdpi.com/2504-4990/5/4/83 | Overview YOLO — justify chọn YOLOv8 |
| 11 | Hussain, M. & Khanam, R. (2024). *In-Depth Review of YOLOv1 to YOLOv10 Variants for Enhanced Photovoltaic Defect Detection*. Solar 4(3):16. | https://www.mdpi.com/2673-9941/4/3/16 | Survey YOLO cho PV — liên quan trực tiếp nhất |
| 12 | Wang, J. & Cheng, Z. (2025). *Photovoltaic panel defect detection algorithm based on infrared imaging and improved YOLOv8*. PeerJ CS 11:e2776. | https://pmc.ncbi.nlm.nih.gov/articles/PMC12190611 | Detect scratches, black_core với YOLOv8 — kết quả thực nghiệm |
| 13 | Khanam, R., Asghar, T. & Hussain, M. (2025). *Comparative Evaluation of YOLOv5/v8/v11 for Solar Panel Defect Detection*. Solar 5(1):6 (MDPI). | https://www.mdpi.com/2673-9941/5/1/6 | So sánh model: YOLOv8 recall 79.2% (bird drops), YOLOv11 mAP@0.5=93.4% |
| 14 | Mohamed, A. et al. (2025). *Optimized YOLO (PV-YOLOv12n) for PV defect detection in EL images*. Scientific Reports 15:32955 (Nature). | https://www.nature.com/articles/s41598-025-13956-7 | Detect lỗi trên EL images — mAP@50 0.91 (PVEL-AD/Roboflow) |

## ⚡ Nhóm 4 — Bối cảnh ngành Solar & Digitalization

| # | Tài liệu | Link | Mục đích |
|---|----------|------|----------|
| 15 | Depex Technologies (2025). *Solar Energy Management Software Solutions: A Complete Guide*. | https://depextechnologies.com/blog/solar-energy-management-software-solutions-a-complete-guide | Thị trường $189.6M (2023) → $895.6M (2031), CAGR 8.5% — justify context |
| 16 | Bhardwaj, D. et al. (2024). *AI-Driven Energy Management Systems for Microgrids*. E3S Web Conf. 591, 01005 (ICRERA 2024). | https://www.e3s-conferences.org/articles/e3sconf/abs/2024/121/e3sconf_icrera2024_01005/e3sconf_icrera2024_01005.html | Nền tảng EMS + AI — context cho monitoring dashboard |

## 🆕 Nhóm 5 — RAG nâng cao: Đánh giá, Traceability & So sánh (bổ sung 2026-06, đúng đề tài custom RAG pipeline)

| # | Tài liệu | Link | Tiêu chí / Mục đích |
|---|----------|------|---------------------|
| 17 | Yu, H. et al. (2024). *Evaluation of RAG: A Survey*. | https://arxiv.org/abs/2405.07437 | Survey đánh giá RAG — khung phân loại metric |
| 18 | Friel, R. et al. (2024). *RAGBench: Explainable Benchmark (TRACe)*. | https://arxiv.org/abs/2407.11005 | Benchmark 100k + metric TRACe |
| 19 | Saad-Falcon, J. et al. (2024). *ARES: Automated Evaluation Framework*. NAACL. | https://arxiv.org/abs/2311.09476 | Tự động hóa đánh giá, ít nhãn người |
| 20 | Ru, D. et al. (2024). *RAGChecker: Fine-grained Diagnosing*. NeurIPS. | https://arxiv.org/abs/2408.08067 | Tách lỗi retriever vs generator |
| 21 | Niu, C. et al. (2024). *RAGTruth: Hallucination Corpus*. ACL. | https://arxiv.org/abs/2401.00396 | Đo hallucination rate (18k nhãn cấp từ) |
| 22 | Zhou, Y. et al. (2024). *Trustworthiness in RAG: A Survey*. | https://arxiv.org/abs/2409.10102 | Factuality + traceability + transparency |
| 23 | Bohnet, B. et al. (2022). *Attributed QA: Evaluation & Modeling*. | https://arxiv.org/abs/2212.08037 | Metric AIS — source traceability gốc |
| 24 | Qi, J. et al. (2024). *MIRAGE: Model Internals Answer Attribution*. EMNLP. | https://arxiv.org/abs/2406.13663 | Kỹ thuật truy vết trích dẫn |
| 25 | Li, Z. et al. (2024). *RAG or Long-Context LLMs? Study + Hybrid*. EMNLP. | https://arxiv.org/abs/2407.16833 | So sánh cost/accuracy với existing solution |
| 26 | Brehme, L. et al. (2025). *RAG in Industry: An Interview Study*. KDIR 2025. | https://arxiv.org/abs/2508.14066 | Use case/requirements doanh nghiệp (13 practitioners) |
| 27 | Nguyen Ba, T. et al. (2024). *Vietnamese Legal Information Retrieval in QA*. | https://arxiv.org/abs/2409.13699 | RAG tiếng Việt — domain-specific |
| 28 | Edge, D. et al. (2024). *From Local to Global: A Graph RAG Approach* (GraphRAG, Microsoft). | https://arxiv.org/abs/2404.16130 | Kiến trúc nâng cao — global query, existing solution |
| 29 | Sarthi, P. et al. (2024). *RAPTOR: Recursive Abstractive Tree Retrieval*. ICLR. | https://arxiv.org/abs/2401.18059 | Chunking/indexing nâng cao, tài liệu dài |
| 30 | Yan, S.-Q. et al. (2024). *Corrective RAG (CRAG)*. | https://arxiv.org/abs/2401.15884 | Self-correcting, robustness — existing solution |

## 🧩 Nhóm 6 — Retrieval & Đánh giá bổ sung (2026-06, đợt 2)

| # | Tài liệu | Link | Tiêu chí / Mục đích |
|---|----------|------|---------------------|
| 31 | Thakur, N. et al. (2025). *FreshStack: Realistic Benchmarks for Retrieval on Technical Documents*. | https://arxiv.org/abs/2504.13128 | Benchmark retrieval trên **tài liệu kỹ thuật** (rất sát đề tài) |
| 32 | Tang, Y. & Yang, Y. (2024). *MultiHop-RAG: Benchmarking RAG for Multi-Hop Queries*. | https://arxiv.org/abs/2401.15391 | Test câu hỏi đa bước (ghép nhiều bằng chứng) |
| 33 | Li, D. et al. (2024). *From Generation to Judgment: LLM-as-a-judge*. EMNLP 2025. | https://arxiv.org/abs/2411.16594 | Thiên kiến của LLM-judge → đánh giá đáng tin |
| 34 | Khattab, O. & Zaharia, M. (2020). *ColBERT: Late Interaction over BERT*. SIGIR. | https://arxiv.org/abs/2004.12832 | Retriever/reranker hiệu quả (tốc độ ↔ chính xác) |

> ✅ Tất cả 34 ID arXiv/DOI + tác giả đã được xác minh từ nguồn gốc (2026-06). Lưu ý mục **14** (tên Algeria): rà thứ tự **họ/tên** khi format citation.

---

## 📋 URL block — nạp vào NotebookLM (`add_source`)

```
https://arxiv.org/abs/2005.11401
https://aclanthology.org/2020.emnlp-main.550
https://arxiv.org/abs/2312.10997
https://arxiv.org/abs/2310.11511
https://arxiv.org/abs/2410.12837
https://aclanthology.org/2024.eacl-demo.16
https://dl.acm.org/doi/10.1145/3571730
https://arxiv.org/abs/2603.06976
https://arxiv.org/abs/2409.00090
https://www.mdpi.com/2504-4990/5/4/83
https://www.mdpi.com/2673-9941/4/3/18
https://pmc.ncbi.nlm.nih.gov/articles/PMC12190611
https://www.preprints.org/manuscript/202501.0788
https://www.nature.com/articles/s41598-025-13956-7
https://depextechnologies.com/blog/solar-energy-management-software-solutions-a-complete-guide
https://www.e3s-conferences.org/articles/e3sconf/abs/2024/121/e3sconf_icrera2024_01005/e3sconf_icrera2024_01005.html
https://arxiv.org/abs/2405.07437
https://arxiv.org/abs/2407.11005
https://arxiv.org/abs/2311.09476
https://arxiv.org/abs/2408.08067
https://arxiv.org/abs/2401.00396
https://arxiv.org/abs/2409.10102
https://arxiv.org/abs/2212.08037
https://arxiv.org/abs/2406.13663
https://arxiv.org/abs/2407.16833
https://arxiv.org/abs/2508.14066
https://arxiv.org/abs/2409.13699
https://arxiv.org/abs/2404.16130
https://arxiv.org/abs/2401.18059
https://arxiv.org/abs/2401.15884
https://arxiv.org/abs/2504.13128
https://arxiv.org/abs/2401.15391
https://arxiv.org/abs/2411.16594
https://arxiv.org/abs/2004.12832
```

> ✅ Đã xác minh: **2603.06976** (Shaukat et al., 2026) và **2409.00090** (Anwar et al., 2024) đều là paper hợp lệ.

---

## 📊 Tiến độ đọc (Dataview)

```dataview
TABLE WITHOUT ID ref AS "#", file.link AS "Paper", status AS "Status", join(filter(tags, (t) => t != "literature"), ", ") AS "Nhóm"
FROM "01 - Literature"
WHERE contains(tags, "literature") AND ref
SORT ref ASC
```
