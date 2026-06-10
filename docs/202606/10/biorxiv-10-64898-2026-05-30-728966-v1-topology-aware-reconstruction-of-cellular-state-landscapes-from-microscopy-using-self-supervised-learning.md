---
title: Topology-aware reconstruction of cellular state landscapes from microscopy using self-supervised learning
title_zh: 基于拓扑感知的显微图像细胞状态景观自监督学习重建
authors: "Messori, E., Taha, D. M., Fournier, L., Foix Romero, A., Uhlmann, V., Frossard, P., Vincent-Cuaz, C., Patani, R., Luisier, R."
date: 2026-06-03
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.30.728966v1.full.pdf"
tags: ["query:spatialprot"]
score: 6.0
evidence: 空间信息自监督学习框架用于从显微镜重建细胞状态景观
tldr: 从显微成像数据重建连续细胞状态景观因缺乏空间信息和依赖分割标注而困难。本文提出SI-SimCLR，一种空间感知自监督学习框架，无需分割或人工标注即可学习生物学表征。结合图部分最优传输，该框架从静态图像重建星形胶质细胞表型景观，揭示疾病和炎症相关亚状态。发现ALS星形胶质细胞形态景观受限，且形态与转录组互补。该方法为可扩展、免标注的细胞表型分析提供了新策略。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有方法难以从显微图像重建连续细胞状态，依赖分割和标注，且忽略空间组织信息。
method: 提出SI-SimCLR，利用空间邻近性进行自监督学习，结合图部分最优传输重建细胞表型景观。
result: 在iPSC星形胶质细胞中，SI-SimCLR区分疾病/炎症亚状态，ALS细胞形态受限，形态和转录组互补。
conclusion: 框架实现无需标注的显微图像细胞状态重建，适用于分析异质性和表型响应。
---

## 摘要
形态学和空间组织提供了细胞状态的互补读数。然而，从成像数据重建连续的细胞状态景观仍然具有挑战性，尤其是在密集的生物培养物中。本文提出SI-SimCLR，一种空间感知的自监督学习框架，它直接从荧光显微镜图像中学习具有生物学意义的表示，无需分割或手动标注。结合基于图的局部最优传输框架，SI-SimCLR能够从静态成像数据重建细胞表型景观，揭示表型子状态的组织和连接方式。为了建立并验证该框架，我们利用高内涵成像和匹配的批量转录组学，生成了人iPSC来源星形胶质细胞的多模态数据集。SI-SimCLR解析了与疾病和炎症状态相关的不同且相互连接的星形胶质细胞子状态。ALS星形胶质细胞占据形态学景观的受限区域。引人注目的是，形态学和转录组学捕捉到星形胶质细胞状态变异的独特且互补的方面。总之，我们的框架建立了一种从显微数据重建细胞表型景观的可扩展、无需标注的策略，能够分析跨生物系统的细胞异质性、景观连通性和表型响应。

## Abstract
Morphology and spatial organisation provide complementary readouts of cellular state. However, reconstructing continuous cellular state landscapes from imaging data remains challenging, particularly in dense biological cultures. Here we present SI-SimCLR, a spatially informed self-supervised learning framework that learns biologically informative representations directly from fluorescence microscopy images without requiring segmentation or manual annotation. Combined with a graph-based partial optimal transport framework, SI-SimCLR enables reconstruction of cellular phenotypic landscapes from static imaging data, revealing how phenotypic substates are organised and connected. To establish and validate this framework, we generated a multimodal dataset of human iPSC-derived astrocytes using high-content imaging and matched bulk transcriptomics. SI-SimCLR resolved distinct interconnected astrocyte substates associated with disease and inflammatory states. ALS astrocytes occupied constrained regions of the morphological landscape. Strikingly, morphology and transcriptomics captured distinct and complementary aspects of astrocyte state variation.Together, our framework establishes a scalable and annotation-free strategy for reconstructing cellular phenotypic landscapes from microscopy data, enabling analysis of cellular heterogeneity, landscape connectivity and phenotypic responses across biological systems.