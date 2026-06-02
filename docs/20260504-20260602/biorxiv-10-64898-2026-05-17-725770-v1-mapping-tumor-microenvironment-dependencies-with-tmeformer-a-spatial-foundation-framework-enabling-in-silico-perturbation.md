---
title: "Mapping Tumor-Microenvironment dependencies with TMEformer: A spatial foundation framework enabling in silico perturbation"
title_zh: 利用TMEformer绘制肿瘤-微环境依赖性图谱：一种实现原位扰动的空间基础框架
authors: "Chen, S., Zhu, G., Yang, L., Li, S., Liu, P., Chen, Q., Tang, Y., Luo, J., Huang, L., Chen, B., Ou, S., Jiang, J."
date: 2026-05-20
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.17.725770v1.full.pdf"
tags: ["query:spatialprot"]
score: 8.0
evidence: 肿瘤微环境空间基础模型，支持虚拟扰动
tldr: 现有虚拟扰动模型忽略空间背景，肿瘤微环境的空间结构对肿瘤进展至关重要。本文提出TMEformer，一种空间感知深度学习框架，利用高分辨率空间转录组学联合建模肿瘤内在程序与局部微环境信号。实验表明，TMEformer在捕获谱系可塑性和治疗耐药性等关键转变上优于大规模预训练基线。通过系统扰动分析，识别出驱动疾病进展的肿瘤内转录因子和微环境衍生配体，并发现新候选因子。TMEformer将肿瘤建模为空间耦合、可扰动的生态系统，为空间生物学提供了通用框架。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有虚拟扰动模型忽略肿瘤微环境的空间背景，而空间上下文对肿瘤进展至关重要。
method: 提出TMEformer，利用高分辨率空间转录组数据显式建模空间架构，联合学习肿瘤细胞程序与微环境信号。
result: TMEformer在捕获肿瘤关键转变如谱系可塑性和耐药性上优于大规模预训练基线；扰动分析识别了已知和新的调控因子及配体。
conclusion: TMEformer建立了将肿瘤建模为空间耦合、可扰动生态系统的通用框架，有助于理解肿瘤进展机制。
---

## 摘要
尽管空间背景在驱动肿瘤进展中起着基础性作用，但目前大多数用于虚拟扰动的计算模型在很大程度上忽视了其重要性。在此，我们介绍TMEformer，一种肿瘤微环境感知的深度学习框架，它利用高分辨率空间转录组学，通过显式整合空间架构来联合建模内在肿瘤细胞程序与局部微环境信号。在多种肿瘤空间转录组队列中验证后，TMEformer能够实现捕获局部细胞生态系统内功能依赖性的虚拟扰动。尽管仅在癌症特异性空间数据集上训练，TMEformer在捕捉关键肿瘤转变（包括谱系可塑性和治疗耐药性的出现）方面仍优于在大型语料库上预训练的基线模型。系统性扰动分析优先考虑了驱动疾病进展的肿瘤内在转录因子和源自TME的配体，恢复了已知调控因子并揭示了新的候选因子。此外，TME衍生的嵌入改善了肿瘤细胞的空间分层，并与病理结构更好地对齐。总之，TMEformer建立了一个将肿瘤建模为空间耦合、可扰动生态系统的一般框架。

## Abstract
Despite the fundamental role of spatial context in driving tumor progression, most current computational models for virtual perturbation have largely overlooked its importance. Here, we introduce TMEformer, a tumor microenvironment-aware deep learning framework that leverages high-resolution spatial transcriptomics to jointly model intrinsic tumor cell programs and local microenvironmental signals by explicitly incorporating spatial architecture. Validated across diverse tumor spatial transcriptomic cohorts, TMEformer enables virtual perturbations that capture functional dependencies within local cellular ecosystems. Despite being trained on cancer-specific spatial datasets, TMEformer outperforms baseline models pretrained on large-scale corpora in capturing key tumor transitions, including lineage plasticity and the emergence of therapy resistance. Systematic perturbation analyses prioritize tumor-intrinsic transcription factors and TME-derived ligands that drive disease progression, recovering established regulators and revealing novel candidates. Furthermore, TME-derived embeddings improve the spatial stratification of tumor cells and align more closely with pathological architecture. Together, TMEformer establishes a general framework for modeling tumors as spatially coupled, perturbable ecosystems.