---
title: "NaVis: a virtual microscopy framework for interactive histological interrogation of spatial transcriptomics data"
title_zh: NaVis：用于空间转录组数据交互式组织学探查的虚拟显微镜框架
authors: "Oshinjo, A., Wu, J., Petrov, P., Hashmi, A., Englund, J. I., Izzi, V."
date: 2026-06-09
pdf: "https://www.biorxiv.org/content/10.64898/2026.02.18.706509v2.full.pdf"
tags: ["query:spatialprot"]
score: 6.0
evidence: 空间转录组虚拟显微镜方法，可迁移至空间蛋白组学
tldr: 空间转录组数据分析需跨平台技能，限制广泛使用。NaVis虚拟显微镜框架通过点选式交互实现高分辨率图像级分析，从低分辨率数据生成类显微镜可视化，并分解组织学图像为细胞核、纤维基质和软组织先验，支持基因表达与形态的深度整合。该方法将ST转变为交互式探索，提升了可及性和发现潜力。
source: biorxiv
selection_source: fresh_fetch
motivation: 解决空间转录组分析需跨平台技能、难以直观揭示转录层与组织形态对应关系的问题。
method: 开发NaVis框架，通过点选式交互从低分辨率数据推断高分辨率类显微镜可视化，并分解组织学图像为三种定量组织先验。
result: 实现快速高分辨率推断与转录组全覆盖，支持compartment enrichment、边界一致性、空间相关性等组织学-转录组联合分析。
conclusion: NaVis将空间转录组从静态计算流程转变为交互式探索模态，扩宽了可及性和生物学发现潜力。
---

## 摘要
尽管空间转录组学（ST）已被广泛采用，但揭示转录层与组织形态之间的对齐在技术上仍然具有挑战性，通常需要熟练掌握多个计算框架，从而限制了生物医学界相当一部分研究人员的可及性。在此，我们介绍NaVis（https://github.com/Izzilab/NaVis），一个点击式虚拟显微镜框架，它将ST分析重新定义为一种交互式的、以图像为中心的体验。NaVis能够从低分辨率全转录组平台快速推断高分辨率信息，生成类似显微镜的可视化结果，同时保留全转录组的覆盖范围。它进一步将组织学图像分解为定量组织架构先验——富含细胞核的区域、纤维状细胞外基质和软组织——从而允许基因表达与局部形态的直接整合。这种统一表示支持区室富集、边界一致性、空间互相关、形态模式、组织学-表达解耦以及全转录组空间相似性分析。通过在交互式框架内耦合转录组和图像衍生信息，NaVis将ST从静态计算工作流程转变为一种探索性模式，拓宽了其可访问性、概念范围以及生物学发现的潜力。

## Abstract
Despite the widespread adoption of spatial transcriptomics (ST), revealing the alignment between transcriptional layers and tissue morphology remains technically demanding, typically requiring proficiency across multiple computational frameworks and thereby limiting accessibility for a substantial fraction of the biomedical community. Here, we introduce NaVis (https://github.com/Izzilab/NaVis), a point-and-click virtual microscopy framework that redefines ST analysis as an interactive, image-centric experience. NaVis enables rapid high-resolution inference from low-resolution whole-transcriptome platforms, producing microscopy-like visualizations while preserving transcriptome-wide coverage. It further decomposes histological images into quantitative tissue architecture priors - nuclei-rich regions, fibrillar extracellular matrix, and soft tissue - allowing direct integration of gene expression with local morphology. This unified representation supports analyses of compartment enrichment, boundary concordance, spatial cross-correlation, morphological patterning, histology-expression decoupling, and transcriptome-wide spatial similarity. By coupling transcriptomic and image-derived information within an interactive framework, NaVis shifts ST from static computational workflows to an exploratory modality, broadening its accessibility, conceptual reach and potential for biological discoveries.