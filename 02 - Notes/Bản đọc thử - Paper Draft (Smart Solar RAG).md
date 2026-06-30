---
title: "Bản đọc thử — Paper Draft (Smart Solar RAG)"
tags: [note, paper, draft, reading-copy]
status: draft
created: 2026-06-29
---

> 📖 **Bản đọc thử** — gom các phần đã sửa thành một mạch bài báo (dạng LaTeX/IEEE), tiếng Việt, để bạn đọc kiểm tra dòng chảy lập luận. Công thức viết bằng MathJax (Obsidian render được).
> ⚠️ Đây **chưa phải bản nộp**: phần **Kết quả để trống** (chờ team chạy), và chỗ cấu hình hệ thống là `[team chốt]`. Nhãn trạng thái: **[Proposed]** đề xuất · **[Plan]** kế hoạch đo · **[Result]** số liệu thật.
> Nguồn nội dung: [[Design & Evaluation Protocol - v2]] · [[Related Work - Draft v1 (VN)]] · [[Paper Outline - Smart Solar Capstone]].

---

<div align="center">

# Trợ lý tri thức dựa trên RAG tinh chỉnh theo miền cho Vận hành và Bảo trì Điện mặt trời: Thiết kế và Đánh giá Reference-Free

**Nhóm Capstone 2026 — Đại học FPT**
SE180466 · SE180579 · SE184144 · SE180271

*Bản thảo — 2026*

</div>

---

## Tóm tắt (Abstract) — *[Proposed/Plan]*

Các trợ lý hỏi–đáp dùng mô hình ngôn ngữ lớn (LLM) trả lời trôi chảy nhưng dễ đưa ra thông tin không được nguồn hỗ trợ (*hallucination*) và khó truy vết về tài liệu gốc — rủi ro lớn trong miền kỹ thuật như lắp đặt, vận hành và bảo trì (O&M) điện mặt trời. Truy hồi tăng cường sinh (Retrieval-Augmented Generation — RAG) được kỳ vọng giảm các vấn đề này, nhưng *mức cải thiện thực tế* của một pipeline RAG **tinh chỉnh theo tài liệu dự án** so với LLM thường và RAG mặc định trên dữ liệu O&M điện mặt trời vẫn chưa được định lượng rõ. Bài báo này **đề xuất thiết kế** một pipeline RAG tinh chỉnh cho miền điện mặt trời và **một giao thức đánh giá reference-free** dựa trên RAGAS, so sánh có kiểm soát với hai baseline (plain LLM và naive RAG) theo *faithfulness, answer relevancy, context precision*, cùng *độ trễ* và *chi phí*. ⚠️ *Kết quả thực nghiệm sẽ được bổ sung sau khi hoàn tất chạy hệ thống; bản thảo này tập trung vào thiết kế và giao thức.*

**Từ khóa:** Retrieval-Augmented Generation; đánh giá RAG; faithfulness; điện mặt trời; hỏi–đáp miền hẹp.

---

## 1. Giới thiệu (Introduction)

Số hóa ngành điện mặt trời đang tăng nhanh, kéo theo nhu cầu về các nền tảng phần mềm hỗ trợ lắp đặt–giám sát–bảo trì [15].¹ Tài liệu O&M (sổ tay kỹ thuật, hướng dẫn lắp đặt, quy trình bảo trì) thường dài và phân mảnh, khiến kỹ thuật viên khó tra cứu nhanh. LLM có thể tổng hợp câu trả lời tức thì, nhưng trong ngữ cảnh kỹ thuật, **một câu trả lời sai hoặc không truy được nguồn có thể dẫn tới thao tác sai**, gây rủi ro an toàn và chi phí.

RAG [1] giảm thiểu các điểm yếu cốt lõi của LLM — hallucination, tri thức lỗi thời, và suy luận thiếu minh bạch [3] — bằng cách ghép **bộ nhớ tham số** (trọng số mô hình) với **bộ nhớ phi tham số** (chỉ mục tài liệu cập nhật được). Tuy nhiên, chất lượng RAG phụ thuộc mạnh vào lựa chọn *chunking*, *embedding* và *retrieval* [8][2], và **không có cấu hình mặc định nào tối ưu cho mọi miền** [8]. Câu hỏi đặt ra: với tài liệu O&M điện mặt trời, một pipeline RAG **được tinh chỉnh** cải thiện bao nhiêu so với cách dùng LLM thường hoặc RAG mặc định?

**Đóng góp của bài báo:**
- **C1 [Proposed].** Thiết kế một pipeline RAG tinh chỉnh cho miền O&M điện mặt trời, với khái niệm "tinh chỉnh" được định nghĩa cụ thể (Mục 4).
- **C2 [Plan→Result].** Một giao thức đánh giá reference-free so sánh pipeline với hai baseline có kiểm soát (plain LLM, naive RAG) theo các tiêu chí đo được (Mục 5).
- **C3 (tùy chọn) [Result].** Một test set hỏi–đáp miền điện mặt trời (ưu tiên tiếng Việt) làm tài nguyên đánh giá.

> ¹ Lưu ý: [15] là tài liệu ngành **không bình duyệt**; chỉ dùng làm bối cảnh, không làm luận cứ định lượng (sẽ thay bằng báo cáo thị trường gốc ở bản nộp).

---

## 2. Công trình liên quan (Related Work)

**Nền tảng RAG.** RAG được Lewis và cộng sự [1] giới thiệu; xương sống truy hồi dựa trên Dense Passage Retrieval (DPR) [2], với dual-encoder vượt BM25 **9–19% tuyệt đối** ở top-20 retrieval accuracy.² Survey của Gao và cộng sự [3] hệ thống hóa lĩnh vực theo tiến trình *Naive → Advanced → Modular RAG* — khung để định vị pipeline của chúng tôi (nhóm Advanced/Modular).

**Chunking & embedding.** Chất lượng truy hồi phụ thuộc cách tách tài liệu: Shaukat và cộng sự [8] khảo sát 36 phương pháp trên 6 miền × 5 embedding model, cho thấy *content-aware chunking* (Paragraph Group, nDCG@5 ≈ **0.459**) vượt xa tách ký tự cố định (nDCG@5 **< 0.244**), và chiến lược tối ưu **phụ thuộc miền** — cơ sở để tinh chỉnh trên tài liệu dự án thay vì dùng mặc định.²

**Xếp hạng hiệu quả & truy hồi tiếng Việt.** Ở tầng xếp hạng, ColBERT [34] đề xuất *late interaction*: mã hóa độc lập câu hỏi và tài liệu bằng BERT rồi so khớp token mịn (MaxSim), cho phép tiền-tính biểu diễn tài liệu offline — hiệu quả cạnh tranh các mô hình dựa trên BERT nhưng **nhanh hơn hai bậc độ lớn và dùng ít hơn bốn bậc độ lớn FLOPs mỗi truy vấn**,² một cơ chế re-rank khả thi cho pipeline tùy chỉnh. Với corpus **tiếng Việt**, Nguyen Ba và cộng sự [27] xử lý các thách thức đặc thù (token quá dài, ensemble thiếu ổn định, thứ tự tài liệu tham chiếu bị bỏ qua) bằng tiền xử lý dữ liệu, **Reciprocal Rank Fusion chuẩn hóa thứ tự** (ghép keyword + vector) và **re-rank bằng Active Retrieval**² — tham chiếu kỹ thuật sát nếu tài liệu O&M của dự án bằng tiếng Việt.

**Đánh giá truy hồi trên tài liệu kỹ thuật & câu hỏi đa đoạn.** Hai benchmark gần đây làm rõ độ khó đúng bối cảnh đề tài: FreshStack [31] dựng benchmark truy hồi *thực tế, không nhiễm dữ liệu* trên tài liệu kỹ thuật/mã nguồn và cho thấy các retriever hiện tại **kém xa phương pháp oracle trên cả năm chủ đề**;² MultiHop-RAG [32] chỉ ra **các hệ RAG hiện tại trả lời chưa thỏa đáng các câu hỏi đa đoạn** cần ghép nhiều mảnh bằng chứng.² Hai kết quả này thúc đẩy việc phân loại câu hỏi *factoid / quy trình / đa-đoạn* trong test set của chúng tôi (Mục 5.1) và đặt kỳ vọng thực tế cho retriever trên tài liệu O&M dài, chuyên ngành.

**RAG nâng cao (để định vị, không chạy đối chứng).** Các kiến trúc self-reflective/self-correcting như Self-RAG [4] (reflection token, tự phê bình) và Corrective RAG [30] (đánh giá chất lượng truy hồi) cải thiện độ tin cậy; GraphRAG [28] và RAPTOR [29] (cây tóm tắt đệ quy, +20% absolute trên QuALITY khi ghép GPT-4)² xử lý tài liệu dài/câu hỏi tổng hợp. Trong bài này, các kiến trúc trên được **thảo luận để định vị đóng góp, không dùng làm baseline đối chứng** (xem Mục 4).

**Đánh giá RAG.** RAGAS [6] cung cấp bộ đo **reference-free** (không cần ground-truth) trên ba trục: chất lượng ngữ cảnh, độ trung thực phần sinh (*faithfulness*), và độ liên quan câu trả lời — ánh xạ trực tiếp vào tiêu chí của chúng tôi; nhóm tác giả mô tả đây là *"a framework for reference-free evaluation … without relying on ground truth human annotations"*.² Vì RAGAS dựa trên **LLM-as-judge**, độ tin cậy của nó chịu các thiên kiến mà Li và cộng sự [33] hệ thống hóa (khung *what / how to judge, how to benchmark*) — lý do chúng tôi bổ sung kiểm thủ công mẫu nhỏ (Mục 7). Các framework bổ trợ mở rộng khả năng đo: RAGBench [18] (**100k** ví dụ, **năm** miền công nghiệp; một RoBERTa fine-tuned **vượt** các phương pháp LLM-judge)² và RAGTruth [21] (**~18.000** câu trả lời gán nhãn hallucination **ở mức từ**)²; ở tầm hệ thống, Zhou và cộng sự [22] đề xuất khung **Trust-RAG Compass** với **sáu chiều** *factuality, robustness, fairness, transparency, accountability, privacy*² để trình bày độ tin cậy/truy vết trong phần Thảo luận. Cơ sở lý thuyết về hallucination lấy từ survey của Ji và cộng sự [7] (phân biệt *intrinsic* vs *extrinsic*).

**Truy vết nguồn.** Bohnet và cộng sự [23] hình thức hóa *Attributed QA* và metric AIS; ngay hệ retrieve-then-read tốt nhất chỉ đạt **65.5±1.5% AIS**,² và nhấn mạnh *correctness ≠ attribution*.

**Khoảng trống.** Các công trình trên xử lý chất lượng RAG, hiệu quả truy hồi [2][34], đánh giá [6][18][21][33] và benchmark trên tài liệu kỹ thuật/đa đoạn [31][32] một cách **tổng quát**, trong khi so sánh RAG với long-context LLM cho thấy ưu thế **chi phí** rõ rệt của RAG [25]; song chưa có nghiên cứu **tinh chỉnh RAG theo tài liệu O&M điện mặt trời (ưu tiên tiếng Việt)** kèm **đánh giá định lượng reference-free** so với baseline có kiểm soát trên dữ liệu miền này. Đây là khoảng trống bài báo hướng tới.

> ² Các con số/claim đánh dấu ² đã được **đối chiếu nguyên văn với nguồn gốc** (grounded qua NotebookLM trên 35 nguồn, 2026-06-30): DPR 9–19% [2], chunking 0.459/<0.244 [8], RAPTOR +20% *chỉ khi ghép GPT-4* [29], ColBERT nhanh 2 bậc/ít FLOPs 4 bậc [34], RRF+Active Retrieval [27], FreshStack [31], MultiHop-RAG [32], RAGBench 100k/RoBERTa>LLM-judge [18], RAGTruth ~18k mức từ [21], RAGAS reference-free [6], Trust-RAG 6 chiều [22], RAG rẻ hơn LC [25], LLM-as-judge [33]. **Chưa phủ được** (giữ theo đối chiếu full-text trước đó của vault): AIS 65.5% ở Table 1 [23], tên 4 thành phần TRACe [18], công thức 3 metric RAGAS [6]. Chi tiết: [[Verify Log - NotebookLM (2026-06-29)]] · [[Related Work - Draft v1 (VN)]].

---

## 3. Phát biểu bài toán & Câu hỏi nghiên cứu

**Bài toán.** Cho corpus tài liệu O&M điện mặt trời $D$ và một câu hỏi $q$, cần sinh câu trả lời $a$ vừa *đúng*, vừa *trung thực với tài liệu* (mọi khẳng định được $D$ hỗ trợ), vừa *truy được nguồn*, trong giới hạn chi phí và độ trễ chấp nhận được.

**Câu hỏi nghiên cứu (RQ).** *So với (i) plain LLM (không truy hồi) và (ii) naive RAG (chunk cố định, không rerank), một pipeline RAG tinh chỉnh theo tài liệu O&M điện mặt trời cải thiện faithfulness, answer relevancy và context precision (đo bằng RAGAS [6]) đến mức nào, và đánh đổi độ trễ/chi phí ra sao?*

**Sub-RQ (tùy chọn).** Pipeline tinh chỉnh đạt mức *source traceability* nào (đo định tính trên tập nhỏ, khung AIS [23])?

---

## 4. Thiết kế hệ thống & Phương pháp *[Proposed]*

### 4.1 Kiến trúc tổng thể

Pipeline gồm bốn khối: (1) tiền xử lý & *chunking* tài liệu; (2) *embedding* + chỉ mục vector; (3) *retrieval* (+ re-rank); (4) *generation* có kèm trích dẫn nguồn. Cấu hình cụ thể để **placeholder** — team chốt trước khi chạy:

| Thành phần | Lựa chọn | Trạng thái |
|---|---|---|
| Embedding model | `[team chốt — model đa ngữ hỗ trợ tiếng Việt]` | ⚠️ chưa chốt |
| Vector database | `[team chốt]` | ⚠️ chưa chốt |
| LLM sinh | `[team chốt — open hay API]` | ⚠️ chưa chốt |
| Re-ranker | `[team chốt / hoặc bỏ]` | ⚠️ chưa chốt |
| Corpus | `[team chốt — số trang, ngôn ngữ]` | ⚠️ chưa chốt |

### 4.2 Định nghĩa "tinh chỉnh" (custom)

"Custom RAG" = naive RAG **cộng** các thay đổi cụ thể, mỗi thay đổi truy nguồn được về tài liệu:

| Thành phần | Naive (baseline B1) | Custom (P) | Căn cứ |
|---|---|---|---|
| Chunking | Cố định ~512 token | Content-aware (theo cấu trúc) | [8] |
| Retrieval | Vector top-$k$ | Vector + re-rank (±hybrid keyword) | [2][34][27] |
| Prompt | Chung | Theo miền O&M điện mặt trời | [3] |
| Trích dẫn | Không | Trả về nguồn kèm câu trả lời | [1][23] |

### 4.3 Các nhánh so sánh

Giữ **cố định** mọi yếu tố khác (LLM, corpus, test set, top-$k$ cuối) để so sánh công bằng:
- **B0 — Plain LLM:** trả lời trực tiếp, không truy hồi.
- **B1 — Naive RAG:** chunk cố định 512, vector top-$k$, không rerank, prompt chung.
- **P — Custom RAG:** áp dụng các thay đổi ở §4.2.

---

## 5. Thiết lập đánh giá *[Plan]*

### 5.1 Test set (điều kiện tiên quyết)

50–100 cặp hỏi–đáp trích từ corpus O&M ([team chốt nguồn]); câu trả lời chuẩn (*gold*) do ≥2 thành viên soạn độc lập rồi đối chiếu, kèm **đoạn nguồn** chứa đáp án. Phân loại: factoid / quy trình / đa-đoạn. Đây là **dữ liệu thật**, không sinh tự động.

### 5.2 Độ đo (Metrics)

Ký hiệu: $q$ — câu hỏi; $a$ — câu trả lời sinh ra; $C=\{c_1,\dots,c_k\}$ — tập ngữ cảnh truy hồi.

**Faithfulness** — tỉ lệ khẳng định trong $a$ được $C$ hỗ trợ (chống hallucination):

$$
\mathrm{Faithfulness} = \frac{\big|\{\text{claim} \in a : \text{được } C \text{ hỗ trợ}\}\big|}{\big|\{\text{claim} \in a\}\big|}
$$

**Answer Relevancy** — độ liên quan của $a$ với $q$, ước lượng qua $n$ câu hỏi suy ngược $q_i$ sinh từ $a$:

$$
\mathrm{AnswerRelevancy} = \frac{1}{n}\sum_{i=1}^{n} \cos\!\big(\mathbf{e}_{q},\, \mathbf{e}_{q_i}\big)
$$

**Context Precision@k** — mức độ các đoạn *liên quan* được xếp hạng cao trong $C$:

$$
\mathrm{ContextPrecision@}k = \frac{\sum_{j=1}^{k}\big(\mathrm{Precision@}j \cdot \mathrm{rel}_j\big)}{\big|\{\text{đoạn liên quan trong top-}k\}\big|}
$$

**Độ trễ** báo cáo theo phân vị: $\mathrm{Latency}_{p50},\ \mathrm{Latency}_{p95}$.

**Chi phí** ước tính theo token:

$$
\mathrm{Cost} = \sum_{i} \big(\mathrm{tokens}_i \times \mathrm{price}_i\big)
$$

> ⚠️ Công thức trên là **định nghĩa thao tác (operational)** theo tinh thần RAGAS [6]. Đã xác nhận (grounded) RAGAS là bộ đo **reference-free, không cần ground-truth** và dựa trên **LLM-as-judge** — nên có thiên kiến, giảm thiểu bằng kiểm thủ công mẫu nhỏ [33] (xem [[Verify Log - NotebookLM (2026-06-29)]]). Tuy nhiên **công thức chính xác** của ba metric **không nằm trong abstract** — phải lấy từ full-text [6] kèm phiên bản thư viện và model làm "judge" trước khi báo cáo. *Source traceability* (sub-RQ) đo định tính theo khung AIS [23] trên tập nhỏ.

### 5.3 Quy trình

Chạy B0, B1, P trên cùng test set → thu metric §5.2 → báo cáo **trung bình ± độ lệch**; nếu đủ mẫu, kiểm định ý nghĩa (paired test). Cố định seed/nhiệt độ, ghi phiên bản thư viện và log prompt để tái lập.

---

## 6. Kết quả và Thảo luận *[Result]*

> ⚠️ **Để trống có chủ đích.** Không điền số liệu trước khi team chạy thật — bịa số liệu là gian lận nghiên cứu. Bảng dưới chỉ là khung sẽ điền:

| Nhánh | Faithfulness | Answer Rel. | Context Prec. | Latency p95 | Cost/query |
|---|---|---|---|---|---|
| B0 — Plain LLM | — | — | — | — | — |
| B1 — Naive RAG | — | — | — | — | — |
| P — Custom RAG | — | — | — | — | — |

*Thảo luận sẽ phân tích: (a) custom có cải thiện faithfulness/relevancy so với B0/B1 không; (b) đánh đổi latency/cost; (c) phân tích lỗi retriever vs generator (tùy chọn, dùng RAGChecker).*

---

## 7. Hạn chế (Limitations)

- Test set nhỏ ($N=50$–$100$), một miền, ưu tiên tiếng Việt → **không khái quát hóa** rộng.
- Chỉ 2 baseline có kiểm soát; chưa đối chứng kiến trúc self-correcting (Self-RAG/CRAG) → *future work*.
- Một cấu hình "custom" duy nhất; chưa *ablation* từng thành phần.
- Đánh giá phụ thuộc LLM-as-judge của RAGAS → có thiên lệch (xem khảo sát [33]); giảm thiểu bằng kiểm thủ công mẫu nhỏ.
- Truy vết nguồn đo định tính, tập nhỏ.

---

## 8. Kết luận và Hướng phát triển (Conclusion)

Bài báo **đề xuất thiết kế** một pipeline RAG tinh chỉnh cho miền O&M điện mặt trời và **một giao thức đánh giá reference-free** so với hai baseline có kiểm soát (plain LLM, naive RAG) theo faithfulness, answer relevancy, context precision, cùng độ trễ và chi phí. *[Khi có kết quả:]* trên test set $N=\dots$, pipeline cho thấy *[xu hướng]* với đánh đổi *[latency/cost]*. Chúng tôi **chưa khẳng định** ưu thế tổng quát; đánh giá với nhiều baseline, tập lớn hơn và đa miền là hướng tiếp theo. Module phát hiện lỗi tấm pin bằng thị giác máy tính (YOLOv8) được phát triển song song như một hướng mở rộng, ngoài phạm vi bài báo này.

---

## Tài liệu tham khảo (References)

> Trích dẫn `[n]` khớp [[_Sources Master List]]. Dưới đây liệt kê các nguồn được cite trong bản đọc thử; danh mục đầy đủ 34 nguồn xem master list.

[1] Lewis, P. *et al.* (2020). *Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks.* NeurIPS 2020. arXiv:2005.11401.
[2] Karpukhin, V. *et al.* (2020). *Dense Passage Retrieval for Open-Domain Question Answering.* EMNLP 2020, 6769–6781. arXiv:2004.04906.
[3] Gao, Y. *et al.* (2024). *Retrieval-Augmented Generation for LLMs: A Survey.* arXiv:2312.10997.
[4] Asai, A. *et al.* (2023). *Self-RAG: Learning to Retrieve, Generate, and Critique through Self-Reflection.* ICLR 2024. arXiv:2310.11511.
[6] Es, S. *et al.* (2024). *RAGAs: Automated Evaluation of Retrieval-Augmented Generation.* EACL 2024 Demos.
[7] Ji, Z. *et al.* (2023). *Survey of Hallucination in Natural Language Generation.* ACM Computing Surveys 55(12).
[8] Shaukat, M. A., Adnan, M. & Kuhn, C. C. N. (2026). *A Systematic Investigation of Document Chunking Strategies and Embedding Sensitivity.* arXiv:2603.06976.
[15] Depex Technologies (2025). *Solar Energy Management Software Solutions: A Complete Guide.* (grey literature — chỉ dùng làm bối cảnh).
[18] Friel, R., Belyi, M. & Sanyal, A. (2024). *RAGBench: Explainable Benchmark for Retrieval-Augmented Generation Systems.* arXiv:2407.11005.
[21] Niu, C. *et al.* (2024). *RAGTruth: A Hallucination Corpus for Developing Trustworthy Retrieval-Augmented Language Models.* ACL 2024. arXiv:2401.00396.
[22] Zhou, Y. *et al.* (2024). *Trustworthiness in Retrieval-Augmented Generation Systems: A Survey.* arXiv:2409.10102.
[23] Bohnet, B. *et al.* (2022). *Attributed Question Answering: Evaluation and Modeling for Attributed Large Language Models.* arXiv:2212.08037.
[25] Li, Z. *et al.* (2024). *Retrieval Augmented Generation or Long-Context LLMs? A Comprehensive Study and Hybrid Approach.* EMNLP 2024. arXiv:2407.16833.
[27] Nguyen Ba, T., Doan The, V., Pham Quang, T. & Tran Van, T. (2024). *Vietnamese Legal Information Retrieval in Question-Answering System.* arXiv:2409.13699.
[28] Edge, D. *et al.* (2024). *From Local to Global: A GraphRAG Approach to Query-Focused Summarization.* arXiv:2404.16130.
[29] Sarthi, P. *et al.* (2024). *RAPTOR: Recursive Abstractive Processing for Tree-Organized Retrieval.* ICLR 2024. arXiv:2401.18059.
[30] Yan, S.-Q. *et al.* (2024). *Corrective Retrieval-Augmented Generation.* arXiv:2401.15884.
[31] Thakur, N. *et al.* (2025). *FreshStack: Building Realistic Benchmarks for Evaluating Retrieval on Technical Documents.* arXiv:2504.13128.
[32] Tang, Y. & Yang, Y. (2024). *MultiHop-RAG: Benchmarking Retrieval-Augmented Generation for Multi-Hop Queries.* arXiv:2401.15391.
[33] Li, D. *et al.* (2024). *From Generation to Judgment: Opportunities and Challenges of LLM-as-a-judge.* arXiv:2411.16594.
[34] Khattab, O. & Zaharia, M. (2020). *ColBERT: Efficient and Effective Passage Search via Contextualized Late Interaction over BERT.* SIGIR 2020. arXiv:2004.12832.
