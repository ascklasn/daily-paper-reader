---
title: Atlas-Level Single-Cell and Spatial Transcriptomics Data Integration via PRIME
title_zh: 基于PRIME的图谱级单细胞与空间转录组学数据集成
authors: "Wu, X., Wang, X., Wang, J., Wan, S."
date: 2026-06-04
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.20.726698v3.full.pdf"
tags: ["query:spatialprot"]
score: 6.0
evidence: 整合空间转录组与单细胞数据，与空间转录组-蛋白组整合相关
tldr: 单细胞与空间转录组图谱整合面临批次效应、细胞类型不平衡和计算可扩展性挑战。PRIME通过随机投影共识投票和图拉普拉斯校正，结合空间邻域正则化，实现鲁棒整合。在造血发育、皮层结构及超百万细胞扰动图谱中保持生物学结构并消除批次噪声。该框架为大规模多来源数据整合提供了高效、兼容空间信息的解决方案。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有整合方法难以同时处理大规模异质性批次效应和空间信息，且计算可扩展性不足。
method: PRIME结合随机投影共识锚定、图拉普拉斯校正和空间邻域正则化，实现高效鲁棒整合。
result: 在多项基准测试中优于现有方法，保留发育轨迹、层状结构和药物关系，有效抑制批次效应。
conclusion: PRIME为百万级细胞和空间转录组数据整合提供了可扩展、多功能的框架。
---

## 摘要
单细胞RNA测序（scRNA-seq）和空间转录组学（ST）技术实现了图谱级别的细胞制图，联盟项目现已跨组织、供体和平台组装了数百万个细胞，以构建细胞身份和疾病机制的全面参考。然而，这些图谱的科学价值依赖于跨异质数据源的鲁棒计算整合。与两两批次校正不同，图谱级整合必须协调来自多个数据集的异质且往往层次嵌套的批次效应，这些数据集的细胞类型组成高度不平衡，同时需保留细微的生物学变异，并在数百万细胞规模下保持计算可行性。现有方法通常优先考虑批次混合或局部生物学结构保留，且大多数无法原生处理空间坐标。在此，我们提出PRIME（基于投影的流形嵌入鲁棒整合），这是一种集成整合框架，结合了基于随机投影的共识锚定、图拉普拉斯校正和可选的空间邻域正则化。在表达流形的多次随机投影中，PRIME使用共识投票仅保留重复匹配的细胞对，从而减少由投影特定失真引起的虚假锚点。对于ST，PRIME将基于表达的锚定图与坐标导出的空间邻域图耦合，形成具有封闭形式解的统一图拉普拉斯目标，从而同时实现跨批次对齐和局部空间连贯性。基于涵盖多种数据集的广泛基准测试，我们证明PRIME在scRNA-seq和ST整合场景以及下游任务（包括轨迹推断、空间域保留和扰动响应分析）中，在批次校正和生物学保留方面均持续优于最先进方法。特别地，在整合一个涵盖8个供体约33,000个细胞的人类造血基准时，PRIME在人类造血过程中保留了生物学上一致的发育轨迹。它还在ST数据集的背外侧前额叶皮层切片中维持了皮层板层结构，并在超过100万个细胞的扰动图谱中恢复了已知的药物-靶点关系，同时抑制了批次相关的混杂因素。综上所述，这些结果确立了PRIME作为一个适用于多种生物学应用的scRNA-seq和ST图谱级整合的通用且可扩展框架。

## Abstract
Single-cell RNA sequencing (scRNA-seq) and spatial transcriptomics (ST) have enabled atlas-scale cellular cartography, with consortium efforts now assembling millions of cells across diverse tissues, donors, and technologies to build comprehensive references for cell identify and disease mechanism, yet the scientific value of these atlases hinges on robust computational integration across heterogeneous data sources. Unlike pairwise batch correction, atlas-level integration must jointly reconcile heterogeneous and often hierarchically nested batch effects across many datasets whose cell-type compositions are highly imbalanced, all while preserving subtle biological variation and remaining computationally tractable at the scale of millions of cells. Existing approaches often prioritize either batch mixing or preservation of local biological structure, and most cannot natively accommodate spatial coordinates. Here we introduce PRIME (Projection-based Robust Integration via Manifold Embedding), an ensemble integration framework that combines random-projection-based consensus anchoring, graph-Laplacian correction, and optional spatial-neighborhood regularization. Across multiple random projections of the expression manifold, PRIME uses consensus voting to keep only cell pairs that repeatedly matched, reducing false anchors caused by projection-specific distortions. For ST, PRIME couples this expression-based anchor graph with a coordinate-derived spatial neighborhood graph in a unified graph-Laplacian objective with closed-form solution, enabling simultaneous cross-batch alignment and local spatial coherence. Based on extensive benchmarking spanning diverse datasets, we show that PRIME consistently outperforms state-of-the-art methods in both batch correction and biological conservation across scRNA-seq and ST integration scenarios and downstream tasks including trajectory inference, spatial-domain preservation, and perturbation-response analysis. Particularly, when integrating a human hematopoiesis benchmark spanning eight donors and approximately 33,000 cells, PRIME preserves biologically coherent developmental trajectories in human hematopoiesis. It also maintains cortical laminar architecture across dorsolateral prefrontal cortex sections in a ST dataset and recovers known drug-target relationships in a perturbation atlas of more than 1 million cells while suppressing batch-associated confounders. Together, these results establish PRIME as a versatile and scalable framework for atlas-level integration of scRNA-seq and ST across diverse biological applications.