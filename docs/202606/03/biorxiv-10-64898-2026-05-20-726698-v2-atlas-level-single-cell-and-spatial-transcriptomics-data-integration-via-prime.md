---
title: Atlas-Level Single-Cell and Spatial Transcriptomics Data Integration via PRIME
title_zh: 通过PRIME实现图谱级别的单细胞和空间转录组学数据整合
authors: "Wu, X., Wang, X., Wang, J., Wan, S."
date: 2026-05-28
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.20.726698v2.full.pdf"
tags: ["query:spatialprot"]
score: 6.0
evidence: 空间转录组整合方法
tldr: 大规模单细胞与空间转录组数据集成面临异质性批次效应和细胞类型不平衡等挑战。PRIME框架通过随机投影共识锚定、图拉普拉斯校正及空间邻域正则化，实现高效鲁棒的联合对齐。在多个基准测试中，PRIME优于现有方法，能保持发育轨迹、皮层层架构及药物-靶点关系。该工作建立了一个通用且可扩展的集成方案，适用于多种生物学应用。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有集成方法无法同时处理异质性批次效应和保持生物变异，且多数不支持空间数据，亟需一个统一、可扩展的框架。
method: PRIME采用随机投影共识锚定减少误匹配，结合图拉普拉斯校正和可选空间正则化进行联合流形对齐。
result: 在多个数据集上，PRIME在批次校正和生物保守性方面均优于现有方法，成功恢复造血轨迹、皮层层结构和药物靶点关系。
conclusion: PRIME为大规模单细胞和空间转录组数据集成提供了通用、可扩展的解决方案，适用于多种下游分析。
---

## 摘要
单细胞RNA测序和空间转录组学已经实现了图谱规模的细胞绘图，联盟努力现在正在跨不同组织、供体和技术组装数百万个细胞，以构建用于细胞身份和疾病机制的全面参考，然而这些图谱的科学价值取决于跨异构数据源的稳健计算整合。与成对批次校正不同，图谱级别整合必须共同协调跨许多数据集的异质且通常是分层嵌套的批次效应，这些数据集的细胞类型组成高度不平衡，同时保留微妙的生物学变异并在百万级细胞规模上保持计算可行性。现有方法通常优先考虑批次混合或局部生物结构保留，而且大多数不能原生适应空间坐标。在这里，我们介绍PRIME（基于流形嵌入的投影稳健整合），这是一种集成整合框架，结合了基于随机投影的共识锚定、图拉普拉斯校正和可选的空间邻域正则化。在表达流形的多个随机投影上，PRIME使用共识投票仅保留重复匹配的细胞对，减少了由投影特定失真引起的假锚点。对于空间转录组学，PRIME将这种基于表达的锚图与坐标导出的空间邻域图耦合在一个统一的图拉普拉斯目标中，该目标具有封闭形式的解，从而能够同时进行跨批次对齐和局部空间一致性。基于涵盖不同数据集的广泛基准测试，我们表明PRIME在批次校正和生物学保存方面始终优于最先进的方法，涵盖单细胞RNA测序和空间转录组学整合场景以及下游任务，包括轨迹推断、空间域保留和扰动响应分析。特别是，在整合一个涵盖八个供体和约33,000个细胞的人类造血基准时，PRIME保留了人类造血中生物学上一致的发育轨迹。它还在一个空间转录组学数据集的背外侧前额叶皮层切片中维持了皮层分层结构，并在一个超过100万个细胞的扰动图谱中恢复了已知的药物-靶点关系，同时抑制了与批次相关的混杂因素。总之，这些结果确立了PRIME作为跨不同生物学应用的单细胞RNA测序和空间转录组学图谱级别整合的多功能且可扩展的框架。

## Abstract
Single-cell RNA sequencing (scRNA-seq) and spatial transcriptomics (ST) have enabled atlas-scale cellular cartography, with consortium efforts now assembling millions of cells across diverse tissues, donors, and technologies to build comprehensive references for cell identify and disease mechanism, yet the scientific value of these atlases hinges on robust computational integration across heterogeneous data sources. Unlike pairwise batch correction, atlas-level integration must jointly reconcile heterogeneous and often hierarchically nested batch effects across many datasets whose cell-type compositions are highly imbalanced, all while preserving subtle biological variation and remaining computationally tractable at the scale of millions of cells. Existing approaches often prioritize either batch mixing or preservation of local biological structure, and most cannot natively accommodate spatial coordinates. Here we introduce PRIME (Projection-based Robust Integration via Manifold Embedding), an ensemble integration framework that combines random-projection-based consensus anchoring, graph-Laplacian correction, and optional spatial-neighborhood regularization. Across multiple random projections of the expression manifold, PRIME uses consensus voting to keep only cell pairs that repeatedly matched, reducing false anchors caused by projection-specific distortions. For ST, PRIME couples this expression-based anchor graph with a coordinate-derived spatial neighborhood graph in a unified graph-Laplacian objective with closed-form solution, enabling simultaneous cross-batch alignment and local spatial coherence. Based on extensive benchmarking spanning diverse datasets, we show that PRIME consistently outperforms state-of-the-art methods in both batch correction and biological conservation across scRNA-seq and ST integration scenarios and downstream tasks including trajectory inference, spatial-domain preservation, and perturbation-response analysis. Particularly, when integrating a human hematopoiesis benchmark spanning eight donors and approximately 33,000 cells, PRIME preserves biologically coherent developmental trajectories in human hematopoiesis. It also maintains cortical laminar architecture across dorsolateral prefrontal cortex sections in a ST dataset and recovers known drug-target relationships in a perturbation atlas of more than 1 million cells while suppressing batch-associated confounders. Together, these results establish PRIME as a versatile and scalable framework for atlas-level integration of scRNA-seq and ST across diverse biological applications.