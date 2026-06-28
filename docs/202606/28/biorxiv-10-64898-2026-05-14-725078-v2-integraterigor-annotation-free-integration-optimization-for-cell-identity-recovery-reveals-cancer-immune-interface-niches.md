---
title: "IntegrateRigor: annotation-free integration optimization for cell identity recovery reveals cancer-immune interface niches"
title_zh: IntegrateRigor：无注释整合优化用于细胞身份恢复揭示癌症-免疫界面微环境
authors: "Zhai, Z., Wang, C., Jiang, C., Rong, Z., Li, J. J."
date: 2026-06-27
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.14.725078v2.full.pdf"
tags: ["query:spatialprot"]
score: 6.0
evidence: 空间转录组整合用于癌症细胞身份恢复
tldr: 单细胞和空间转录组数据整合中，去除批次效应与保留细胞身份常冲突，现有方法缺乏无标注的优化指标，易导致过度或欠整合。IntegrateRigor提出基于基因批次稳定性的特征选择和平衡批次去除与身份保留的整合评分，无需注释即可自动寻优。在结直肠癌数据中，它发现了被先前过度或欠整合掩盖的癌症-免疫界面生态位。该方法将整合从启发式预处理转变为统计原则的自适应流程，提升了大规模分析的重现性和生物学发现能力。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有整合方法缺乏无标注的优化指标，导致过度或欠整合，损害细胞身份恢复。
method: IntegrateRigor通过基因批次稳定性评分选择特征，并定义平衡批次去除与身份保留的整合评分，自动优化配置。
result: 在结直肠癌数据中揭示了被掩盖的癌症-免疫界面生态位，并在多种数据集上一致提升细胞身份恢复。
conclusion: 将整合转变为统计原则的自适应流程，提高大规模单细胞和空间转录组分析的可重复性和生物学发现能力。
---

## 摘要
整合跨批次的单细胞和空间转录组数据对于恢复可比较的细胞身份（包括细胞类型、亚型和状态）至关重要，这是多条件和大规模研究中进行下游分析的前提。这项任务仍然具有挑战性，因为批次间变异去除通常与细胞身份保留相冲突，而当前方法通常依赖于通用的高度可变基因选择，并且在缺乏细胞身份注释时缺乏用于超参数调优的原则性指标。这些限制共同导致过度整合（合并生物学上不同的细胞身份）或欠整合（细胞按批次而非身份分离）。这里我们介绍IntegrateRigor，一个数据驱动、无注释、方法无关的框架，专门为跨批次可靠恢复细胞身份而优化整合。IntegrateRigor首先使用基于基因的似然批次稳定性评分选择表达模式在批次间稳定的基因，排除可能歪曲整合过程中细胞身份对齐的批次敏感基因。然后，通过定义一个数据集级别的整合评分，明确平衡批次间变异去除与细胞身份保留，无需先验注释，从而识别跨方法和超参数的最优整合配置。在一个结直肠癌单细胞和空间转录组数据集中，IntegrateRigor揭示了肿瘤微环境中先前未表征的癌症-免疫界面微环境，这些微环境在默认设置下因欠整合而被掩盖，在先前文献中则因过度整合而被掩盖。在涵盖多个批次间变异来源的多样数据集中，IntegrateRigor通过减轻五种最先进方法的过度整合和欠整合，持续改善了细胞身份恢复。通过将整合从启发式预处理步骤转变为用于细胞身份恢复的统计原则性、数据集自适应程序，IntegrateRigor提高了大规模单细胞和空间转录组分析的可重复性和生物学发现能力。

## Abstract
Integrating single-cell and spatial transcriptomics data across batches is essential for recovering comparable cell identities (including cell types, subtypes, and states) as a prerequisite for downstream analyses in multi-condition and large-scale studies. This task remains challenging because between-batch variation removal often conflicts with cell identity preservation, and current methods typically rely on generic highly variable gene selection and lack principled metrics for hyperparameter tuning when cell identity annotations are unavailable. Together, these limitations often lead to over-integration, which merges biologically distinct cell identities, or under-integration, which leaves cells separated by batch rather than identity. Here we introduce IntegrateRigor, a data-driven, annotation-free, method-agnostic framework that optimizes integration specifically for reliable cell identity recovery across batches. IntegrateRigor first selects genes whose expression patterns are stable across batches using a gene-wise likelihood- based batch stability score, excluding batch-sensitive genes that can bias cell identity alignment during integration. It then identifies the optimal integration configuration across methods and hyperparameters by defining a dataset-level integration score that explicitly balances between-batch variation removal against cell identity preservation, without requiring prior annotations. In a colorectal cancer single-cell and spatial transcriptomics dataset, IntegrateRigor revealed previously uncharacterized cancer-immune interface niches in the tumor microenvironment that were masked by under-integration under default settings and by over-integration in previous literature. Across diverse datasets spanning multiple sources of between-batch variation, IntegrateRigor consistently improved cell identity recovery by mitigating both over-integration and under-integration across five state-of-the-art methods. By transforming integration from a heuristic preprocessing step into a statistically principled, dataset-adaptive procedure for cell identity recovery, IntegrateRigor improves the reproducibility and biological discovery power of large-scale single-cell and spatial transcriptomics analyses.