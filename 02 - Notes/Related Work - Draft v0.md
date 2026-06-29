---
title: Related Work — Draft v0
tags: [note, paper, related-work]
status: draft
created: 2026-06-24
---

# Related Work — Draft v0

> ⚠️ **Draft v0** dựng từ *abstract* các paper (web). Cần NotebookLM grounding trên full-text để xác minh số liệu & làm sâu. Citation [n] khớp [[_Sources Master List]].
> Viết bằng tiếng Anh để sẵn cho submit. Báo nếu bạn cần bản tiếng Việt.

## A. Retrieval-Augmented Generation: Foundations

Retrieval-Augmented Generation (RAG) was introduced by Lewis et al. [1], combining *parametric* memory (knowledge in model weights) with *non-parametric* memory (an explicit, updatable index). Their architecture couples a Dense Passage Retriever over a Wikipedia vector index with a BART seq2seq generator, in two variants — RAG-Sequence (same passages for the whole output) and RAG-Token (per-token passage selection). RAG produced "more specific, diverse and factual" text than parametric-only baselines and set state-of-the-art on three open-domain QA tasks. The retrieval backbone builds on Dense Passage Retrieval (DPR) [2], whose dual-encoder embeds questions and passages into a shared space for similarity search — the mechanism underpinning vector retrieval in modern RAG.

Gao et al.'s survey [3] organizes the field into a **Naive → Advanced → Modular RAG** progression and a tripartite view (retrieval, generation, augmentation). It frames RAG as a remedy for three LLM weaknesses: hallucination, outdated knowledge, and non-transparent/untraceable reasoning. Gupta et al. [5] extend this with the most recent landscape and future directions, situating domain-specific and continually-updated RAG as key trends — directly relevant to a solar-maintenance knowledge assistant.

## B. Advanced RAG and Self-Reflection

Self-RAG [4] augments a single LM with *reflection tokens*, enabling (i) retrieve-on-demand instead of fixed retrieval, and (ii) self-critique of retrieved passages and generated spans. Reported gains include outperforming ChatGPT and retrieval-augmented Llama2-chat on QA, reasoning, and fact verification, with notable improvements in factuality and citation accuracy for long-form generation. We adopt Self-RAG as a **baseline** against which our custom pipeline is compared.

## C. Evaluating RAG Systems

RAGAS [6] provides a **reference-free** evaluation suite — no ground-truth annotations required — across three axes: context/retrieval quality, generation faithfulness (use of retrieved context without hallucination), and answer quality. These map onto our research-question criteria (accuracy, relevance, hallucination, traceability). Hallucination itself is grounded in Ji et al.'s survey [7], which taxonomizes intrinsic vs. extrinsic hallucination and surveys metrics and mitigation across NLG tasks; we use it to define our hallucination-rate metric. Retrieval quality is further shaped by chunking and embedding choices [8], which trade off retrieval accuracy against latency, and by domain-specific evaluations such as RAG-vs-plain-LLM on nuclear data [9] — a methodological template for our solar-domain comparison.

> ⚠️ TODO (NotebookLM): xác minh định nghĩa chính xác của Faithfulness / Answer Relevancy / Context Precision trong [6]; lấy công thức & ngưỡng. Lấy taxonomy intrinsic/extrinsic chính xác từ [7].

## D. Computer Vision for Photovoltaic Defect Detection

YOLO has become the dominant single-stage detector; Terven et al. [10] review its evolution (v1→v8, YOLO-NAS), motivating YOLOv8 as a speed/accuracy trade-off. Hussain & Khanam [11] survey YOLOv1–v10 specifically for **photovoltaic defect detection** — the closest prior work to our CV module. Application studies show improved YOLOv8 on infrared imagery detecting defects such as scratches and black-core [12], a comparative study reporting YOLOv8 recall 79.2% (bird drops) and YOLOv11 mAP@0.5 = 93.4% [13], and an optimized YOLO for electroluminescence (EL) images [14] that informs our image-processing pipeline.

> ⚠️ TODO (NotebookLM/full-text): paper [11] bị chặn web — cần nạp vào NotebookLM để trích defect types, datasets, và benchmark cụ thể.

## E. Solar Digitalization Context

The solar software market is projected to grow from $189.6M (2023) to $895.6M (2031), CAGR 8.5% [15], motivating digital platforms for installation, monitoring, and maintenance. AI-driven energy management systems for microgrids [16] provide context for the monitoring/dashboard component of our platform.

## F. Research Gap → Our Contribution

Prior work treats RAG quality [1–9] and PV defect detection [10–14] **separately**. No existing solution integrates a domain-tuned RAG knowledge assistant with a CV defect-detection module inside a single solar install/monitor/maintain platform, nor benchmarks such a custom pipeline against self-reflective baselines [4] using a reference-free protocol [6] on solar-domain data. This is the gap our work addresses (see [[Paper Outline - Smart Solar Capstone]]).

## References
Xem đầy đủ [[_Sources Master List]] ([1]–[16]).
