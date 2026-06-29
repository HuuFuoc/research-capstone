---
title: Bảng thuật ngữ — RAG & Capstone (Việt - Anh)
tags: [note, glossary, reference]
status: reference
created: 2026-06-29
---

# Bảng thuật ngữ (Glossary) — giải thích tiếng Việt dễ hiểu

> Tra cứu nhanh các từ chuyên ngành xuất hiện trong [[Related Work - Draft v1 (VN)]] và [01 - Literature/](01%20-%20Literature/). Giải thích theo lối đơn giản, không hàn lâm.

## 1. Khái niệm RAG cốt lõi

| Thuật ngữ (EN) | Giải thích tiếng Việt |
|---|---|
| **RAG** (Retrieval-Augmented Generation) | "Sinh văn bản có tra cứu". LLM **tìm tài liệu liên quan trước**, rồi mới dựa vào đó để trả lời → bớt bịa, dễ dẫn nguồn. |
| **LLM** (Large Language Model) | Mô hình ngôn ngữ lớn (vd. GPT-4, Gemini) — sinh văn bản dựa trên xác suất từ. |
| **Parametric memory** | "Bộ nhớ tham số" — kiến thức **nằm sẵn trong trọng số** của mô hình (học lúc train). |
| **Non-parametric memory** | "Bộ nhớ ngoài" — kho tài liệu/chỉ mục **bên ngoài**, tra cứu được và cập nhật được. |
| **Retriever** | Bộ **truy hồi**: tìm ra các đoạn văn liên quan nhất với câu hỏi. |
| **Generator** | Bộ **sinh**: LLM viết câu trả lời dựa trên câu hỏi + đoạn truy hồi. |
| **Knowledge-intensive task** | Tác vụ **cần nhiều kiến thức** (vd. hỏi-đáp chuyên ngành) mà LLM dễ trả lời sai nếu không tra cứu. |
| **Pipeline** | "Dây chuyền xử lý": chuỗi bước nối tiếp (tiền xử lý → chunk → embed → lưu vector → truy hồi → sinh). |

## 2. Truy hồi & embedding

| Thuật ngữ (EN) | Giải thích tiếng Việt |
|---|---|
| **Embedding** | "Vector hoá": biến đoạn text thành **dãy số (vector)** sao cho ý nghĩa giống nhau thì vector gần nhau. |
| **Vector / Vector search** | Tìm kiếm bằng cách so **độ gần của vector** (ngữ nghĩa), thay vì so từ khóa. |
| **Vector database / index** | Kho lưu vector + cấu trúc giúp tìm vector gần nhau nhanh (vd. FAISS). |
| **Dense retrieval** | Truy hồi **"dày"** — dùng embedding ngữ nghĩa (hiểu nghĩa). |
| **Sparse retrieval / BM25 / TF-IDF** | Truy hồi **"thưa"** — dựa trên **từ khóa** trùng khớp. BM25 là công thức kinh điển. |
| **Hybrid retrieval** | **Kết hợp** dense + sparse để lấy ưu điểm cả hai. |
| **Dual-encoder (bi-encoder)** | Hai bộ mã hoá **riêng** cho câu hỏi và đoạn văn → nhanh (tính trước được vector tài liệu). |
| **Cross-encoder** | Bộ mã hoá **ghép chung** câu hỏi + đoạn → chính xác hơn nhưng **chậm**, thường dùng để rerank. |
| **Late interaction (ColBERT)** | "Tương tác trễ": mã hoá riêng query/doc rồi **so khớp chi tiết ở cuối** → vừa nhanh vừa khá chính xác. |
| **Reranking** | **Sắp xếp lại** danh sách tài liệu truy hồi để đưa cái liên quan nhất lên đầu. |
| **RRF** (Reciprocal Rank Fusion) | Cách **gộp thứ hạng** từ nhiều bộ tìm kiếm (keyword + vector) thành một bảng xếp hạng chung. |
| **Chunking** | **Cắt tài liệu** thành đoạn nhỏ (chunk) để embed & truy hồi. |
| **Fixed-length / content-aware chunking** | Cắt theo **độ dài cố định** vs cắt **theo nội dung/ngữ nghĩa** (thông minh hơn). |
| **Top-k** | Lấy **k tài liệu** điểm cao nhất khi truy hồi. |
| **Multi-hop query** | Câu hỏi cần **ghép nhiều mẩu bằng chứng** (nhiều bước suy luận) mới trả lời được. |

## 3. Đánh giá (Evaluation)

| Thuật ngữ (EN) | Giải thích tiếng Việt |
|---|---|
| **Benchmark** | **Bộ dữ liệu chuẩn** để đo và so sánh các hệ thống công bằng. |
| **Metric** | **Chỉ số đo** (vd. độ chính xác, độ liên quan). |
| **Reference-free** | Đánh giá **không cần đáp án mẫu** do người soạn trước (đỡ tốn công gán nhãn). |
| **Ground truth** | "Đáp án chuẩn" do con người xác định để đối chiếu. |
| **Faithfulness** | **Độ trung thành**: câu trả lời có **bám đúng** tài liệu truy hồi không (không bịa thêm). |
| **Answer Relevance** | **Độ liên quan** của câu trả lời với câu hỏi. |
| **Context Relevance / Precision** | Đoạn truy hồi có **đúng/đủ liên quan** với câu hỏi không. |
| **Context Utilization** | Mức câu trả lời **thực sự dùng** thông tin trong ngữ cảnh truy hồi. |
| **LLM-as-a-judge** | Dùng **một LLM làm "giám khảo"** chấm điểm câu trả lời (thay người) — nhanh, rẻ nhưng có thiên kiến. |
| **Position / verbosity / self-enhancement bias** | Thiên kiến của LLM giám khảo: thích câu **ở vị trí đầu/cuối**, thích câu **dài**, hoặc thích **output giống chính nó**. |
| **PPI** (Prediction-Powered Inference) | Kỹ thuật dùng **ít nhãn người** để hiệu chỉnh sai số của chấm điểm tự động. |
| **Meta-evaluation** | "Đánh giá cái đánh giá": kiểm xem metric **có khớp với phán đoán con người** không. |
| **nDCG@k** | Chỉ số đo **chất lượng xếp hạng** top-k (càng cao càng tốt, tối đa 1.0). |

## 4. Hallucination & độ tin cậy

| Thuật ngữ (EN) | Giải thích tiếng Việt |
|---|---|
| **Hallucination** | "Ảo giác": mô hình **bịa ra** thông tin sai hoặc không có trong nguồn. |
| **Intrinsic hallucination** | Bịa **mâu thuẫn trực tiếp** với tài liệu nguồn. |
| **Extrinsic hallucination** | Bịa thông tin **không kiểm chứng được** từ nguồn. |
| **Robustness** | **Độ bền**: hệ vẫn chạy tốt khi truy hồi sai/dữ liệu nhiễu. |
| **Trustworthiness** | **Độ đáng tin** tổng thể (đúng sự thật, công bằng, minh bạch, bảo mật...). |
| **Word-level annotation** | Gán nhãn **ở mức từng từ** (vd. từ nào bị bịa) — chi tiết hơn mức cả câu. |

## 5. Truy vết nguồn (Attribution / Traceability)

| Thuật ngữ (EN) | Giải thích tiếng Việt |
|---|---|
| **Source traceability** | **Truy vết nguồn**: chỉ rõ câu trả lời dựa trên tài liệu/đoạn nào. |
| **Attribution** | **Gán nguồn** cho từng phần câu trả lời. |
| **AIS** (Attributable to Identified Sources) | Chỉ số đo **tỉ lệ câu trả lời quy được về nguồn xác định**. |
| **Self-citation** | LLM **tự chèn trích dẫn** — nhưng hay sai định dạng hoặc bịa nguồn. |
| **Saliency / model internals** | Dùng **tín hiệu bên trong mô hình** để biết token nào dựa vào tài liệu nào (cách MIRAGE làm). |
| **Provenance** | "Xuất xứ" — vết nguồn của một thông tin/quyết định. |

## 6. Kiến trúc RAG nâng cao

| Thuật ngữ (EN) | Giải thích tiếng Việt |
|---|---|
| **Naive / Advanced / Modular RAG** | Ba mức tiến hóa: cơ bản → tối ưu thêm bước (rewrite, rerank) → ghép module linh hoạt. |
| **Reflection tokens (Self-RAG)** | "Token tự phản ánh": ký hiệu đặc biệt giúp mô hình **tự quyết khi nào tra cứu** và **tự chấm** phần trả lời. |
| **Retrieval evaluator (CRAG)** | Bộ **chấm chất lượng tài liệu** truy hồi → quyết định dùng, bỏ, hay đi tìm web. |
| **GraphRAG** | RAG dựa **đồ thị tri thức** (knowledge graph) + tóm tắt cộng đồng → trả lời câu hỏi **tổng hợp toàn corpus**. |
| **Knowledge graph** | "Đồ thị tri thức": mạng các **thực thể** và **quan hệ** giữa chúng. |
| **RAPTOR** | Dựng **cây tóm tắt nhiều tầng** từ tài liệu để truy hồi ở nhiều mức trừu tượng. |
| **Long-context LLM** | LLM có **cửa sổ ngữ cảnh rất dài** — nhét thẳng nhiều tài liệu vào prompt (thay vì truy hồi). |
| **Latency / Response time** | **Độ trễ / thời gian phản hồi** của hệ thống. |
| **Cost** | **Chi phí** (token API, tính toán) cho mỗi truy vấn. |

## 7. Computer Vision (module CV của platform)

| Thuật ngữ (EN) | Giải thích tiếng Việt |
|---|---|
| **YOLO** (You Only Look Once) | Họ mô hình **phát hiện vật thể** thời gian thực (nhanh). |
| **PV / Photovoltaic** | **Quang điện** — tấm pin mặt trời. |
| **Defect detection** | **Phát hiện lỗi** (nứt, xước, black-core...) trên tấm pin. |
| **EL image (Electroluminescence)** | Ảnh **điện phát quang** — chụp pin dưới dòng điện để lộ vết nứt vi mô. |
| **mAP / mAP@0.5** | "Mean Average Precision": chỉ số **độ chính xác phát hiện** tổng hợp (cao = tốt). |
| **Precision / Recall** | **Độ chính xác** (báo đúng) / **độ phủ** (bắt được bao nhiêu lỗi thật). |
| **Single-stage detector** | Bộ phát hiện **một giai đoạn** (nhanh, như YOLO) so với hai giai đoạn. |
| **EMS** (Energy Management System) | Hệ **quản lý năng lượng** cho microgrid/điện mặt trời. |

> 🔗 Thiếu từ nào khó hiểu, nhắn tôi bổ sung vào bảng này.
