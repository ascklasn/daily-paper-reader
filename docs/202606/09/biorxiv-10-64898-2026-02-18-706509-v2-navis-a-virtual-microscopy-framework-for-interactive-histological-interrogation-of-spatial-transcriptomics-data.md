---
title: "NaVis: a virtual microscopy framework for interactive histological interrogation of spatial transcriptomics data"
title_zh: NaVis：用于空间转录组数据交互式组织学探究的虚拟显微镜框架
authors: "Oshinjo, A., Wu, J., Petrov, P., Hashmi, A., Englund, J. I., Izzi, V."
date: 2026-06-09
pdf: "https://www.biorxiv.org/content/10.64898/2026.02.18.706509v2.full.pdf"
tags: ["query:spatialprot"]
score: 7.0
evidence: 空间转录组虚拟显微镜框架，实现高分辨率推断和交互式组织学探索
tldr: 空间转录组学分析需跨多种计算工具，操作复杂。NaVis作为点击式虚拟显微镜框架，将分析转化为交互式图像中心体验，可从低分辨率数据快速生成高分辨率显微镜级可视化，并分解组织学图像为定量架构先导，直接整合基因表达与局部形态。该框架支持多种空间分析，使ST从静态流程转向探索性模态。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有ST分析需跨框架技术，限制生物医学社区可及性，需要简化交互工具。
method: NaVis提供点击式虚拟显微镜框架，集成图像与转录组，实现高分辨率推断和组织定量分解。
result: 快速从低分辨率数据生成显微镜级可视化，并分解组织图像为三种先验，支持多种空间分析。
conclusion: NaVis将ST从静态计算转变为交互探索模态，拓宽可及性和发现潜力。
---

## 摘要
尽管空间转录组学（ST）已得到广泛采用，但揭示转录层与组织形态之间的对齐在技术上仍具有挑战性，通常需要熟练掌握多种计算框架，从而限制了生物医学领域中相当大一部分研究者的可及性。在此，我们介绍NaVis（https://github.com/Izzilab/NaVis），一个点击式虚拟显微镜框架，它将ST分析重新定义为一种交互式、以图像为中心的体验。NaVis能够从低分辨率全转录组平台快速进行高分辨率推断，生成类似显微镜的可视化结果，同时保留全转录组覆盖。它进一步将组织学图像分解为定量组织结构先验（富含细胞核的区域、纤维状细胞外基质和软组织），从而允许基因表达与局部形态的直接整合。这种统一表示支持区间富集、边界一致性、空间互相关、形态模式、组织学/表达解耦以及全转录组空间相似性的分析。通过将转录组信息和图像衍生信息耦合在一个交互式框架中，NaVis将ST从静态计算工作流转变为一种探索性模式，拓宽了其可及性、概念范围以及生物发现的潜力。

## Abstract
Despite the widespread adoption of spatial transcriptomics (ST), revealing the alignment between transcriptional layers and tissue morphology remains technically demanding, typically requiring proficiency across multiple computational frameworks and thereby limiting accessibility for a substantial fraction of the biomedical community. Here, we introduce NaVis (https://github.com/Izzilab/NaVis), a point-and-click virtual microscopy framework that redefines ST analysis as an interactive, image-centric experience. NaVis enables rapid high-resolution inference from low-resolution whole-transcriptome platforms, producing microscopy-like visualizations while preserving transcriptome-wide coverage. It further decomposes histological images into quantitative tissue architecture priors (nuclei-rich regions, fibrillar extracellular matrix, and soft tissue) allowing direct integration of gene expression with local morphology. This unified representation supports analyses of compartment enrichment, boundary concordance, spatial cross-correlation, morphological patterning, histology/expression decoupling, and transcriptome-wide spatial similarity. By coupling transcriptomic and image-derived information within an interactive framework, NaVis shifts ST from static computational workflows to an exploratory modality, broadening its accessibility, conceptual reach and potential for biological discoveries.