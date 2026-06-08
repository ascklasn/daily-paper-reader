---
title: Topology-aware reconstruction of cellular state landscapes from microscopy using self-supervised learning
title_zh: 利用自监督学习从显微镜图像中进行拓扑感知的细胞状态景观重建
authors: "Messori, E., Taha, D. M., Fournier, L., Foix Romero, A., Uhlmann, V., Frossard, P., Vincent-Cuaz, C., Patani, R., Luisier, R."
date: 2026-06-03
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.30.728966v1.full.pdf"
tags: ["query:spatialprot"]
score: 6.0
evidence: 具有空间感知的自监督学习用于从显微图像重建细胞状态景观，可应用于空间蛋白组学分析
tldr: 从显微图像中重建连续细胞状态景观面临挑战，尤其在密集培养中。本文提出SI-SimCLR，一种空间感知的自监督学习框架，无需分割或标注，结合图部分最优传输，从静态图像中重建细胞表型景观。在人类iPSC源星形胶质细胞数据上，该方法解析出与疾病和炎症相关的不同亚状态，ALS细胞形态域受限。该框架为分析细胞异质性和表型景观连通性提供了可扩展的免标注策略。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有方法难以从显微图像重建连续细胞表型景观，缺乏免分割标注且能保持拓扑结构的学习框架。
method: 提出SI-SimCLR自监督学习框架，利用空间上下文学习表征，结合图部分最优传输重建细胞状态景观。
result: 在星形胶质细胞数据中识别出与ALS和炎症相关的不同亚状态，ALS细胞形态域受限，形态与转录组互补。
conclusion: 该框架为显微数据重建细胞表型景观提供免标注策略，揭示了形态与转录组的互补性及景观连通性。
---

## 摘要
形态学和空间组织提供了细胞状态的互补读数。然而，从成像数据重建连续的细胞状态景观仍然具有挑战性，特别是在密集的生物培养中。在此，我们提出了SI-SimCLR，一种空间信息的自监督学习框架，它直接从荧光显微镜图像中学习具有生物学意义的表示，无需分割或手动注释。结合基于图的偏最优传输框架，SI-SimCLR能够从静态成像数据重建细胞表型景观，揭示表型亚状态的组织和连接方式。为了建立和验证这一框架，我们使用高内涵成像和匹配的批量转录组学生成了人类iPSC衍生星形胶质细胞的多模态数据集。SI-SimCLR解析了与疾病和炎症状态相关的不同相互连接的星形胶质细胞亚状态。ALS星形胶质细胞占据了形态景观的受限区域。值得注意的是，形态学和转录组学捕获了星形胶质细胞状态变化的独特且互补的方面。总之，我们的框架建立了一种可扩展且无需注释的策略，用于从显微镜数据重建细胞表型景观，能够分析跨生物系统的细胞异质性、景观连接性和表型反应。

## Abstract
Morphology and spatial organisation provide complementary readouts of cellular state. However, reconstructing continuous cellular state landscapes from imaging data remains challenging, particularly in dense biological cultures. Here we present SI-SimCLR, a spatially informed self-supervised learning framework that learns biologically informative representations directly from fluorescence microscopy images without requiring segmentation or manual annotation. Combined with a graph-based partial optimal transport framework, SI-SimCLR enables reconstruction of cellular phenotypic landscapes from static imaging data, revealing how phenotypic substates are organised and connected. To establish and validate this framework, we generated a multimodal dataset of human iPSC-derived astrocytes using high-content imaging and matched bulk transcriptomics. SI-SimCLR resolved distinct interconnected astrocyte substates associated with disease and inflammatory states. ALS astrocytes occupied constrained regions of the morphological landscape. Strikingly, morphology and transcriptomics captured distinct and complementary aspects of astrocyte state variation.Together, our framework establishes a scalable and annotation-free strategy for reconstructing cellular phenotypic landscapes from microscopy data, enabling analysis of cellular heterogeneity, landscape connectivity and phenotypic responses across biological systems.