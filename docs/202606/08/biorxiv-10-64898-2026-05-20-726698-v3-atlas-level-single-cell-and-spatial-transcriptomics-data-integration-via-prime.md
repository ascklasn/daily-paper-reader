---
title: Atlas-Level Single-Cell and Spatial Transcriptomics Data Integration via PRIME
title_zh: 通过PRIME实现图谱级单细胞与空间转录组数据整合
authors: "Wu, X., Wang, X., Wang, J., Wan, S."
date: 2026-06-04
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.20.726698v3.full.pdf"
tags: ["query:spatialprot"]
score: 6.0
evidence: 全图谱级别空间转录组数据整合方法，可迁移至蛋白组学
tldr: 单细胞与空间转录组学数据集成面临批次校正和生物结构保持的挑战。PRIME通过随机投影共识锚定、图拉普拉斯校正和空间邻域正则化，实现高效大规模集成。在造血发育、皮层层状结构和扰动图谱等数据集上优于现有方法，保持发育轨迹和空间结构。PRIME为多源异质数据集成提供了通用且可扩展的框架。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有方法难以同时实现批次混合与生物结构保持，且无法处理空间坐标和大规模数据。
method: PRIME结合随机投影共识锚定、图拉普拉斯校正与可选空间邻域正则化，通过集成多投影共识投票减少假锚点。
result: 在多个数据集上优于现有方法，保持造血发育轨迹、皮层层状结构，并在百万级细胞扰动图谱中抑制批次混杂。
conclusion: PRIME是通用且可扩展的框架，适用于大规模单细胞和空间转录组学数据集成。
---

## 摘要
单细胞RNA测序（scRNA-seq）和空间转录组学（ST）已实现图谱尺度的细胞制图，联盟项目正在跨不同组织、供体和技术组装数百万个细胞，以构建细胞身份和疾病机制的全面参考，然而这些图谱的科学价值依赖于对异质数据源的稳健计算整合。与成对批次校正不同，图谱级整合必须共同协调多个数据集之间的异质且通常层次嵌套的批次效应，这些数据集的细胞类型组成高度不平衡，同时保留细微生物学变异，并在数百万细胞规模下保持计算可行性。现有方法通常优先考虑批次混合或局部生物结构保留，且多数无法原生处理空间坐标。本文提出PRIME（基于投影的流形嵌入鲁棒整合），这是一种集成整合框架，结合了基于随机投影的共识锚定、图拉普拉斯校正和可选的空间邻域正则化。在表达流形的多次随机投影中，PRIME使用共识投票仅保留重复匹配的细胞对，减少了投影特异失真导致的假锚点。对于ST，PRIME将基于表达的锚定图与坐标衍生的空间邻域图耦合在一个具有封闭解的统一图拉普拉斯目标中，实现跨批次对齐和局部空间连贯性。基于涵盖多个数据集的广泛基准测试，我们表明PRIME在scRNA-seq和ST整合场景以及下游任务（包括轨迹推断、空间域保留和扰动响应分析）中的批次校正和生物保守性方面始终优于最先进方法。特别是在整合一个涵盖八个供体约33,000个细胞的人类造血基准时，PRIME保留了人类造血中生物学连贯的发育轨迹。它还在ST数据集的背外侧前额叶皮层切片中维持了皮层分层结构，并在包含超过100万个细胞的扰动图谱中恢复了已知的药物-靶点关系，同时抑制了批次相关的混杂因素。这些结果共同确立了PRIME作为适用于不同生物学应用的scRNA-seq和ST图谱级整合的通用可扩展框架。

## Abstract
Single-cell RNA sequencing (scRNA-seq) and spatial transcriptomics (ST) have enabled atlas-scale cellular cartography, with consortium efforts now assembling millions of cells across diverse tissues, donors, and technologies to build comprehensive references for cell identify and disease mechanism, yet the scientific value of these atlases hinges on robust computational integration across heterogeneous data sources. Unlike pairwise batch correction, atlas-level integration must jointly reconcile heterogeneous and often hierarchically nested batch effects across many datasets whose cell-type compositions are highly imbalanced, all while preserving subtle biological variation and remaining computationally tractable at the scale of millions of cells. Existing approaches often prioritize either batch mixing or preservation of local biological structure, and most cannot natively accommodate spatial coordinates. Here we introduce PRIME (Projection-based Robust Integration via Manifold Embedding), an ensemble integration framework that combines random-projection-based consensus anchoring, graph-Laplacian correction, and optional spatial-neighborhood regularization. Across multiple random projections of the expression manifold, PRIME uses consensus voting to keep only cell pairs that repeatedly matched, reducing false anchors caused by projection-specific distortions. For ST, PRIME couples this expression-based anchor graph with a coordinate-derived spatial neighborhood graph in a unified graph-Laplacian objective with closed-form solution, enabling simultaneous cross-batch alignment and local spatial coherence. Based on extensive benchmarking spanning diverse datasets, we show that PRIME consistently outperforms state-of-the-art methods in both batch correction and biological conservation across scRNA-seq and ST integration scenarios and downstream tasks including trajectory inference, spatial-domain preservation, and perturbation-response analysis. Particularly, when integrating a human hematopoiesis benchmark spanning eight donors and approximately 33,000 cells, PRIME preserves biologically coherent developmental trajectories in human hematopoiesis. It also maintains cortical laminar architecture across dorsolateral prefrontal cortex sections in a ST dataset and recovers known drug-target relationships in a perturbation atlas of more than 1 million cells while suppressing batch-associated confounders. Together, these results establish PRIME as a versatile and scalable framework for atlas-level integration of scRNA-seq and ST across diverse biological applications.