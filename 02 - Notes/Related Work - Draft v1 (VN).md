---
title: Related Work — Draft v1 (Tiếng Việt, 30 nguồn)
tags: [note, paper, related-work]
status: draft
created: 2026-06-29
---

# Related Work — Draft v1 (Tiếng Việt)

> Bản tiếng Việt, tổng hợp từ **30 nguồn** đã đọc & verify trong [[_Sources Master List]] (citation `[n]` khớp số thứ tự ở đó). Viết theo lối **diễn giải** để giảm rủi ro đạo văn; dịch sang tiếng Anh **sau** khi rà & check plagiarism.
> Nối tiếp [[Related Work - Draft v0]] (bản tiếng Anh, [1]–[16]) — bản v1 này mở rộng thêm [17]–[30] và đào sâu phần đánh giá/traceability/chi phí đúng trọng tâm đề tài.
> ⚠️ Số liệu thí nghiệm của *hệ thống team* không nằm ở đây — Related Work chỉ tổng hợp công trình trước. Chỗ cần dữ liệu thật được đánh dấu `⚠️`.

> ✅ **TRẠNG THÁI VERIFY (cập nhật 2026-06-29).** 4 con số RAG-side đã đối chiếu **trực tiếp với nguồn gốc** — an toàn để cite:
> - DPR **9–19% absolute** top-20 (§A, [2]) — ✅ verbatim abstract arXiv:2004.04906
> - Chunking nDCG@5 **0.459 vs <0.244** (§C, [8]) — ✅ verbatim abstract arXiv:2603.06976 (paper CÓ THẬT; bổ sung Precision@1≈24%, Hit@5≈59%)
> - RAPTOR **+20% absolute** QuALITY (§B, [29]) — ✅ verbatim abstract arXiv:2401.18059 (là RAPTOR **+ GPT-4**)
> - AIS retrieve-then-read **65.5±1.5%** (§F, [23]) — ✅ Table 1 **full-text** arXiv:2212.08037 (KHÔNG có ở abstract; là "Best RTR" = GTR + NQ-reranker + FID). Đã sửa "~65.5%" → "65.5±1.5%".
>
> 🟡 **CÒN PHẢI VERIFY (ngoài phạm vi RAG / grey-lit) — kiểm khi viết tài liệu module CV:**
> - YOLOv8 mAP₅₀ **93.5%** PVEL-AD (§H, [12]) · recall **79.2%** / YOLOv11 mAP@0.5 **93.4%** (§H, [13], là *preprint* Preprints.org) · PV-YOLOv12n mAP@50 **0.91** (§H, [14]) — khớp note nội bộ, **chưa** đối chiếu full-text.
> - Thị trường solar **$189.6M→$895.6M, CAGR 8.5%** (§I, [15]) — **grey literature blog Depex, không bình duyệt**: tìm báo cáo gốc (Grand View / Verified Market) hoặc bỏ vai trò luận cứ định lượng.
>
> 📌 **Phạm vi baseline (để Methodology nhất quán).** Bài báo **chỉ chạy** 2 baseline có kiểm soát: **Plain LLM** + **Naive RAG**. Các kiến trúc nâng cao ở §B (Self-RAG [4], CRAG [30], GraphRAG [28], RAPTOR [29]) là **"discussed, not benchmarked"** — dùng để *định vị* đóng góp, KHÔNG tuyên bố đã so sánh đối chứng.
>
> 📌 **§H (Computer Vision) — NGOÀI PHẠM VI bài báo RAG này.** Giữ lại làm nền cho *module/demo riêng*; không phải đóng góp khoa học của bài. Xem [[Smart Solar Platform - Capstone 2026]] → Scope.

## Bản đồ 6 tiêu chí Research Question → nguồn chính

| Tiêu chí (RQ) | Nguồn nền tảng | Nguồn đo lường |
|---|---|---|
| Accuracy / Relevance | [1][2][3] | [6][17][18][19][20] |
| Hallucination | [7] | [6][21][22][30] |
| Source Traceability | [1] | [23][24][22] |
| Response Time | [2][8][29] | [25] |
| Cost | — | [25][9][26][18] |
| Custom vs Existing | [4] | [25][28][29][30][9] |

---

## A. Nền tảng Retrieval-Augmented Generation

Retrieval-Augmented Generation (RAG) được Lewis và cộng sự [1] giới thiệu, kết hợp **bộ nhớ tham số** (tri thức trong trọng số mô hình) với **bộ nhớ phi tham số** (chỉ mục vector có thể cập nhật). Kiến trúc gốc ghép một Dense Passage Retriever trên chỉ mục Wikipedia với bộ sinh BART, ở hai biến thể RAG-Sequence và RAG-Token; RAG sinh văn bản đúng sự thật và đặc thù hơn baseline chỉ-tham-số, đồng thời đặt SOTA trên ba tác vụ open-domain QA. Quan trọng cho đề tài: ngay từ paper gốc, hai bài toán **truy vết nguồn (provenance)** và **cập nhật tri thức** đã được nêu là thách thức mở — chính là động lực của tiêu chí *source traceability*.

Xương sống truy hồi dựa trên Dense Passage Retrieval (DPR) [2]: dual-encoder BERT nhúng câu hỏi và đoạn văn vào cùng không gian, vượt BM25 **9–19%** tuyệt đối ở top-20 retrieval accuracy — cơ chế nền của vector search trong RAG hiện đại. Survey của Gao và cộng sự [3] hệ thống hóa lĩnh vực theo tiến trình **Naive → Advanced → Modular RAG** và ba trụ cột (retrieval, generation, augmentation), khung lý thuyết để định vị pipeline tùy chỉnh của chúng tôi (thuộc nhóm Advanced/Modular). Gupta và cộng sự [5] cập nhật bức tranh mới nhất, đặt RAG chuyên ngành và cập-nhật-liên-tục làm xu hướng trọng tâm — trực tiếp liên quan đến trợ lý tri thức cho tài liệu dự án.

## B. RAG nâng cao, tự sửa lỗi & các "existing solution" để so sánh

Phần này điểm các kiến trúc RAG tiên tiến để **định vị** đóng góp của pipeline tùy chỉnh. ⚠️ *Lưu ý phạm vi:* trong bài báo này chúng được **thảo luận chứ không chạy đối chứng** ("discussed, not benchmarked"); baseline thực nghiệm thực sự là **Plain LLM + Naive RAG** (xem [[Design & Evaluation Protocol - v2]]). Chạy Self-RAG/CRAG đúng chuẩn cần checkpoint/GPU/reproduce — để *future work*.

- **Self-RAG [4]** trang bị *reflection token* cho một LM duy nhất, cho phép (i) truy hồi theo nhu cầu thay vì cố định, và (ii) tự phê bình đoạn truy hồi lẫn phần sinh; báo cáo vượt ChatGPT và Llama2-chat tăng cường truy hồi, cải thiện factuality và độ chính xác trích dẫn cho văn bản dài.
- **Corrective RAG (CRAG) [30]** thêm một *retrieval evaluator* nhẹ chấm chất lượng tài liệu → ba hành động {Correct, Incorrect, Ambiguous}, kích hoạt web search và thuật toán decompose-then-recompose để lọc nhiễu; tăng *robustness* khi truy hồi sai. Là module plug-and-play, ghép được vào pipeline tùy chỉnh.
- **GraphRAG [28]** (Microsoft) chỉ ra RAG vector thường **thất bại với câu hỏi toàn cục** ("các chủ đề chính của bộ tài liệu là gì?"); giải pháp dùng knowledge graph + tóm tắt cộng đồng, cải thiện rõ tính bao quát & đa dạng cho câu hỏi tổng hợp trên corpus cỡ triệu token.
- **RAPTOR [29]** dựng cây tóm tắt đệ quy (embed → cluster → tóm tắt) để truy hồi xuyên nhiều mức trừu tượng; ghép với GPT-4 cải thiện **+20% absolute** trên QuALITY — phù hợp tài liệu kỹ thuật dài.

Bốn hướng trên (đặc biệt Self-RAG và CRAG — hai cơ chế *self-correcting*) là **bối cảnh định vị** đóng góp của pipeline tùy chỉnh; chúng *không* được chạy làm baseline đối chứng trong bài (xem lưu ý phạm vi ở đầu mục).

## C. Chunking, embedding & truy hồi cho tài liệu dự án

Chất lượng truy hồi phụ thuộc mạnh vào cách **chunk** tài liệu và **embedding**. Shaukat và cộng sự [8] khảo sát 36 phương pháp tách trên 6 lĩnh vực × 5 embedding model: **chunking theo nội dung** vượt rõ tách độ dài cố định (Paragraph Group Chunking nDCG@5 ≈ 0.459 so với < 0.244 của tách ký tự), và chiến lược tối ưu **phụ thuộc lĩnh vực** — hàm ý cần tinh chỉnh trên tài liệu dự án thay vì dùng cấu hình mặc định. Với tài liệu **tiếng Việt**, Nguyen Ba và cộng sự [27] xử lý các thách thức đặc thù (token quá dài, ensemble thiếu ổn định) bằng tiền xử lý dữ liệu, **Reciprocal Rank Fusion chuẩn hóa thứ tự** (kết hợp keyword + vector), và re-ranking bằng Active Retrieval — tham chiếu kỹ thuật sát nếu tài liệu dự án bằng tiếng Việt.

## D. Đánh giá RAG (cốt lõi của Research Question)

**RAGAS [6]** cung cấp bộ đo **không cần ground-truth (reference-free)** trên ba trục: chất lượng ngữ cảnh truy hồi, mức trung thành của phần sinh (faithfulness), và độ liên quan câu trả lời — ánh xạ trực tiếp vào các tiêu chí accuracy/relevance/hallucination/traceability. Để chọn metric có hệ thống, Yu và cộng sự [17] đề xuất quy trình hợp nhất **AUEPORA** và phân loại metric theo hai thành phần retrieval/generation.

Ba framework bổ trợ mở rộng khả năng đo:
- **RAGBench [18]**: benchmark 100k ví dụ từ 5 domain công nghiệp + bộ metric **TRACe** (Context Relevance, Context Utilization, Adherence, Completeness) giải thích được; đáng chú ý, một mô hình RoBERTa fine-tuned **vượt** các phương pháp LLM-judge ⇒ gợi ý hướng đánh giá rẻ hơn.
- **ARES [19]**: tự sinh dữ liệu synthetic để fine-tune LM judge nhẹ, dùng prediction-powered inference để giảm sai số chỉ với vài trăm nhãn người; **bền vững khi domain shift** — hữu ích khi chuyển sang tài liệu dự án.
- **RAGChecker [20]**: bộ metric chẩn đoán **chi tiết, tách bạch lỗi retriever vs generator** ở mức claim, tương quan với phán đoán con người cao hơn các metric cũ — công cụ "mổ xẻ" pipeline tùy chỉnh.

> ⚠️ Khi viết Methodology/Evaluation: chốt công thức cụ thể của Faithfulness / Answer Relevancy / Context Precision [6] và định nghĩa TRACe [18] từ full-text trước khi báo cáo.

## E. Hallucination & độ tin cậy

Cơ sở lý thuyết là survey của Ji và cộng sự [7], chuẩn hóa phân biệt **intrinsic** (mâu thuẫn nguồn) vs **extrinsic** (không kiểm chứng được) và tổng hợp metric/biện pháp giảm thiểu — dùng để định nghĩa *hallucination rate*. Để đo thực nghiệm, **RAGTruth [21]** cung cấp corpus ~18.000 câu trả lời RAG gán nhãn hallucination **ở mức từ**, và cho thấy có thể fine-tune một LLM nhỏ đạt mức phát hiện cạnh tranh GPT-4 (rẻ hơn). Ở tầm hệ thống, survey **Trustworthiness in RAG [22]** mở rộng thành **6 chiều** (factuality, robustness, fairness, transparency, accountability, privacy) kèm khung Trust-RAG Compass — khung trình bày "độ tin cậy & truy vết" của pipeline trong phần Discussion. Một thông điệp xuyên suốt [21][22]: **dù có RAG, mô hình vẫn có thể đưa tuyên bố không được ngữ cảnh hỗ trợ** ⇒ cần đo nhiều chiều, không chỉ accuracy.

## F. Truy vết nguồn & gán nguồn (Source Traceability)

Đây là tiêu chí vault trước đây thiếu nền tảng, nay được bổ sung. Bohnet và cộng sự [23] hình thức hóa **Attributed QA** và metric **AIS** (Attributable to Identified Sources), chỉ ra ngay hệ retrieve-then-read tốt nhất chỉ đạt **65.5±1.5% AIS** (Best RTR, Table 1), và quan trọng: **correctness ≠ attribution** (đúng nhưng không quy được về nguồn, hoặc ngược lại). MIRAGE [24] đề xuất gán nguồn **dựa trên nội tại model** (saliency) thay cho self-citation hay sai định dạng/bịa nguồn, đạt độ trung thực cao trên QA đa ngữ. Hai công trình này cung cấp **metric (AIS)** và **kỹ thuật (model-internals)** để hiện thực & đo *source traceability* cho pipeline tùy chỉnh; lưu ý MIRAGE cần model mở.

## G. Chi phí, độ trễ & so sánh với giải pháp có sẵn

Li và cộng sự [25] so sánh trực tiếp RAG với **Long-Context LLM** (Gemini-1.5, GPT-4): LC vượt accuracy khi đủ tài nguyên, nhưng **RAG rẻ hơn rõ rệt**; họ đề xuất Self-Route định tuyến động RAG↔LC để đạt accuracy gần LC với chi phí thấp — chính là trục *cost vs accuracy* để đối chiếu pipeline tùy chỉnh với "existing LLM/long-context". Ở góc độ domain-specific, nghiên cứu trên dữ liệu hạt nhân [9] là **mẫu hình phương pháp** "RAG vs plain LLM" (đánh giá kép người + LLM) rất sát với so sánh trên dữ liệu solar. Cuối cùng, nghiên cứu phỏng vấn công nghiệp [26] (13 practitioner, KDIR 2025) xác nhận: ứng dụng RAG chủ yếu là **QA chuyên ngành** còn ở mức prototype, **tiền xử lý dữ liệu** là rào cản lớn nhất, và **đánh giá vẫn chủ yếu thủ công** dù đã có nhiều framework tự động — hậu thuẫn mạnh cho động lực của đề tài (custom pipeline + đánh giá tự động trên tài liệu dự án).

## H. Computer Vision phát hiện lỗi tấm pin

> ⚠️ **NGOÀI PHẠM VI bài báo RAG này.** Phần này là nền tham khảo cho *module/demo CV riêng*, không phải đóng góp của bài báo. Các con số mAP/recall dưới đây trích từ abstract — cần verify full-text nếu dùng cho tài liệu module CV.

YOLO là bộ phát hiện single-stage chủ đạo; Terven và cộng sự [10] tổng quan tiến hóa (v1→v8, YOLO-NAS), biện minh YOLOv8 ở khía cạnh cân bằng tốc độ/độ chính xác. Hussain & Khanam [11] khảo sát YOLOv1–v10 **chuyên cho phát hiện lỗi PV** — công trình gần nhất với module CV. Các nghiên cứu ứng dụng: YOLOv8 cải tiến trên ảnh hồng ngoại (MCSE + GhostConv/BoTNet + Focaler-CIoU) đạt mAP₅₀ tới 93.5% trên PVEL-AD [12]; nghiên cứu so sánh báo cáo YOLOv8 recall 79.2% (bird drops) và YOLOv11 mAP@0.5 = 93.4% [13]; và PV-YOLOv12n tối ưu cho ảnh điện phát quang (EL) đạt mAP@50 0.91 [14] — định hướng pipeline xử lý ảnh.

## I. Bối cảnh số hóa ngành điện mặt trời

Thị trường phần mềm solar được dự báo tăng từ $189.6M (2023) lên $895.6M (2031), CAGR 8.5% [15], thúc đẩy các nền tảng số cho lắp đặt–giám sát–bảo trì. Hệ thống quản lý năng lượng (EMS) điều khiển bằng AI cho microgrid [16] cung cấp bối cảnh cho thành phần giám sát/dashboard của platform. (Lưu ý [15] là tài liệu ngành không bình duyệt — chỉ dùng làm context, nên đối chiếu báo cáo thị trường gốc khi cite.)

## J. Khoảng trống nghiên cứu → Đóng góp

Công trình trước xử lý **chất lượng RAG** [1–9, 17–30] và **phát hiện lỗi PV** [10–14] một cách **tách rời**. Chưa có giải pháp nào tích hợp một trợ lý tri thức RAG **tinh chỉnh theo tài liệu dự án** với module CV phát hiện lỗi trong **một** platform solar (install/monitor/maintain), cũng chưa benchmark pipeline tùy chỉnh đó với các baseline self-reflective/self-correcting [4][30] và kiến trúc nâng cao [28][29] bằng **giao thức reference-free** [6] cùng các metric traceability [23][24] và chi phí/độ trễ [25] **trên dữ liệu solar**. Đây là khoảng trống mà đề tài hướng tới (xem [[Paper Outline - Smart Solar Capstone]]).

> ⚠️ Đóng góp & kết quả định lượng (RAGAS scores, response time, cost, mAP/recall) phải đến từ **hệ thống thật của team** — Related Work không thay thế phần Results.

## References
Xem đầy đủ [[_Sources Master List]] ([1]–[30]). Mỗi nguồn có note chi tiết trong [01 - Literature/](01%20-%20Literature/).
