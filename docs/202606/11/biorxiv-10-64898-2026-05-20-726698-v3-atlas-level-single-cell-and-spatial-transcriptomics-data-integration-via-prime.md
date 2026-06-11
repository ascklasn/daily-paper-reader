---
title: Atlas-Level Single-Cell and Spatial Transcriptomics Data Integration via PRIME
title_zh: 通过PRIME实现图谱级别的单细胞和空间转录组学数据整合
authors: "Wu, X., Wang, X., Wang, J., Wan, S."
date: 2026-06-04
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.20.726698v3.full.pdf"
tags: ["query:spatialprot"]
score: 7.0
evidence: 大规模单细胞与空间转录组数据整合方法
tldr: 单细胞RNA测序和空间转录组学数据整合面临异构数据源、批次效应和细胞类型不平衡的挑战。PRIME框架通过随机投影共识锚定、图拉普拉斯校正和空间邻域正则化，在多次投影中通过共识投票减少假锚点，并统一目标函数实现跨批次对齐和空间一致性。在多个基准测试中，PRIME在批次校正和生物学保留上优于现有方法，能保持造血发育轨迹、皮层分层结构并恢复药物靶点关系。PRIME为大规模整合提供了通用且可扩展的解决方案。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有方法在批次混合和局部结构保留间权衡，且大多无法处理空间坐标，亟需可协调异构批次效应并保持生物学变异的大规模整合方法。
method: PRIME结合随机投影共识锚定、图拉普拉斯校正和空间邻域正则化，通过多次投影的共识投票减少假锚点，并统一目标函数实现跨批次对齐和空间一致性。
result: 在造血数据集、空间转录组和百万级扰动图谱中，PRIME优于现有方法，保持发育轨迹、皮层结构并抑制批次混杂。
conclusion: PRIME是适用于单细胞和空间转录组大规模整合的通用、可扩展框架。
---

## 摘要
单细胞RNA测序（scRNA-seq）和空间转录组学（ST）已实现图谱规模的细胞制图，联盟工作现正跨组织、供体和多种技术组装数百万个细胞，以构建用于细胞识别和疾病机制的全面参考，但这些图谱的科学价值取决于对异质性数据源的稳健计算整合。与成对批次校正不同，图谱级别整合必须共同协调许多数据集中异质且通常分层嵌套的批次效应，这些数据集的细胞类型组成高度不平衡，同时保留微妙的生物学变异，并在数百万个细胞的规模上保持计算可行性。现有方法通常优先考虑批次混合或局部生物学结构的保留，且大多数无法原生处理空间坐标。本文提出PRIME（基于投影的流形嵌入稳健整合），这是一种集成整合框架，结合了基于随机投影的共识锚定、图拉普拉斯校正和可选的空间邻域正则化。在表达流形的多次随机投影中，PRIME使用共识投票仅保留重复匹配的细胞对，从而减少由投影特定失真引起的假锚点。对于ST，PRIME将此基于表达的锚定图与坐标衍生的空间邻域图结合，形成一个具有闭合解的统一图拉普拉斯目标函数，实现跨批次对齐和局部空间连贯性。基于涵盖多个数据集的广泛基准测试，我们显示PRIME在scRNA-seq和ST整合场景以及下游任务（包括轨迹推断、空间域保留和扰动响应分析）中，在批次校正和生物学保留方面始终优于最先进方法。特别是在整合一个涵盖八名供体约33,000个细胞的人类造血基准时，PRIME保留了人类造血中生物学上一致的发育轨迹。它还在ST数据集的背外侧前额叶皮层切片中维持了皮质层状结构，并在超过100万个细胞的扰动图谱中恢复了已知的药物-靶标关系，同时抑制了批次相关的混杂因素。总之，这些结果确立了PRIME作为一种多功能且可扩展的框架，用于跨多种生物学应用的scRNA-seq和ST图谱级别整合。

## Abstract
Single-cell RNA sequencing (scRNA-seq) and spatial transcriptomics (ST) have enabled atlas-scale cellular cartography, with consortium efforts now assembling millions of cells across diverse tissues, donors, and technologies to build comprehensive references for cell identify and disease mechanism, yet the scientific value of these atlases hinges on robust computational integration across heterogeneous data sources. Unlike pairwise batch correction, atlas-level integration must jointly reconcile heterogeneous and often hierarchically nested batch effects across many datasets whose cell-type compositions are highly imbalanced, all while preserving subtle biological variation and remaining computationally tractable at the scale of millions of cells. Existing approaches often prioritize either batch mixing or preservation of local biological structure, and most cannot natively accommodate spatial coordinates. Here we introduce PRIME (Projection-based Robust Integration via Manifold Embedding), an ensemble integration framework that combines random-projection-based consensus anchoring, graph-Laplacian correction, and optional spatial-neighborhood regularization. Across multiple random projections of the expression manifold, PRIME uses consensus voting to keep only cell pairs that repeatedly matched, reducing false anchors caused by projection-specific distortions. For ST, PRIME couples this expression-based anchor graph with a coordinate-derived spatial neighborhood graph in a unified graph-Laplacian objective with closed-form solution, enabling simultaneous cross-batch alignment and local spatial coherence. Based on extensive benchmarking spanning diverse datasets, we show that PRIME consistently outperforms state-of-the-art methods in both batch correction and biological conservation across scRNA-seq and ST integration scenarios and downstream tasks including trajectory inference, spatial-domain preservation, and perturbation-response analysis. Particularly, when integrating a human hematopoiesis benchmark spanning eight donors and approximately 33,000 cells, PRIME preserves biologically coherent developmental trajectories in human hematopoiesis. It also maintains cortical laminar architecture across dorsolateral prefrontal cortex sections in a ST dataset and recovers known drug-target relationships in a perturbation atlas of more than 1 million cells while suppressing batch-associated confounders. Together, these results establish PRIME as a versatile and scalable framework for atlas-level integration of scRNA-seq and ST across diverse biological applications.