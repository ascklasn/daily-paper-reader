---
title: Transferable spatial omics deconvolution with SpaRank
title_zh: 可迁移的空间组学反卷积方法SpaRank
authors: "Yan, X., Zheng, R., Chen, J., Li, M., Lan, W."
date: 2026-05-13
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.09.723936v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 使用基于排名的编码的可迁移空间组学反卷积方法
tldr: 空间组学反卷积受批次效应影响，现有方法需为每个新上下文重训练。本文提出SpaRank，将空间点表示为排序特征序列，利用基于排序的单细胞基础模型嵌入，对技术变异鲁棒，支持预训练-迁移范式。在模拟和实验数据上，预训练模型可泛化至不同组织、平台和疾病状态，并自然扩展到多模态反卷积。SpaRank建立了可迁移的反卷积范式，通过统一细胞图谱实现跨上下文直接推断。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有空间反卷积方法对单细胞参考与空间数据间的批次效应敏感，需重新训练，缺乏迁移能力。
method: SpaRank将空间点表示为排序特征序列，适配单细胞基础模型的排序编码，采用预训练-迁移范式进行反卷积。
result: 在模拟基准上精度高、对表达扰动鲁棒；实验数据上预训练模型可跨组织、平台和疾病状态泛化，多模态融合进一步提升精度。
conclusion: SpaRank建立了可迁移的空间反卷积框架，支持统一细胞图谱在不同上下文和模态中的直接推断。
---

## 摘要
通过从多细胞空间测量中解析细胞类型组成，反卷积是解析复杂组织细胞景观的核心。现有反卷积方法拟合连续表达值，因此对单细胞参考与空间数据之间的批次效应敏感，需要针对每个新情境重新训练。在此我们提出SpaRank，一种情境感知框架，通过将斑点表示为排序特征序列来进行空间反卷积。采用单细胞基础模型的基于排序的编码，这种公式对技术变异具有内在鲁棒性，实现了预训练-迁移范式。在模拟基准测试中，SpaRank展现出强大的反卷积精度、对表达扰动的鲁棒性以及显著的计算效率。在实验数据集上，预训练模型能够跨不同生物学情境泛化：在多器官淋巴图谱上预训练的模型准确解析了不同组织和测序平台上的细胞类型分布；同样，在综合乳腺图谱上预训练的模型描绘了正常和恶性疾病状态下的细胞类型组成。此外，该框架通过采用门控融合自适应整合多种组学信号，自然地扩展到多模态空间反卷积，相比单模态方法提高了精度。总体而言，SpaRank建立了一种可迁移的反卷积范式，使得统一的细胞图谱能够支持跨不同生物学状态和分析模式的直接、情境感知推理。

## Abstract
By resolving cell-type compositions from multi-cellular spatial measurements, deconvolution is central to resolving the cellular landscape of complex tissues. Existing deconvolution methods fit continuous expression values and are therefore sensitive to batch effects between single-cell references and spatial data, requiring retraining for each new context. Here we present SpaRank, a context-aware framework that performs spatial deconvolution by representing spots as ranked feature sequences. Adapting the rank-based encodings of single-cell foundation models, this formulation is inherently robust to technical variation, enabling a pretrain-transfer paradigm. On simulated benchmarks, SpaRank achieves strong deconvolution accuracy, robustness to expression perturbations, and substantial computational efficiency. On experimental datasets, pretrained models generalize across diverse biological contexts: a model pretrained on a multi-organ lymphoid atlas accurately resolved cell-type distributions across distinct tissues and sequencing platforms; likewise, a model pretrained on an integrated breast atlas delineated cell-type compositions across normal and malignant disease states. Furthermore, the framework naturally extends to multimodal spatial deconvolution by employing gated fusion to adaptively integrate diverse omics signals, improving accuracy over single-modality approaches. Overall, SpaRank establishes a transferable deconvolution paradigm, enabling unified cellular atlases to support direct, context-aware inference across diverse biological states and profiling modalities.