---
title: "NaVis: a virtual microscopy framework for interactive histological interrogation of spatial transcriptomics data"
title_zh: NaVis：一种用于空间转录组数据交互式组织学查询的虚拟显微镜框架
authors: "Oshinjo, A., Wu, J., Petrov, P., Hashmi, A., Englund, J. I., Izzi, V."
date: 2026-06-09
pdf: "https://www.biorxiv.org/content/10.64898/2026.02.18.706509v2.full.pdf"
tags: ["query:spatialprot"]
score: 7.0
evidence: 用于空间转录组的虚拟显微框架
tldr: 空间转录组学分析通常需要跨多个计算框架，技术门槛高。NaVis作为点选式虚拟显微镜框架，将分析转化为交互式图像体验，能从低分辨率平台快速推断高分辨转录组，并分解组织图像为核区、纤维基质和软组织等定量先验。它支持区室富集、边界一致性、空间交叉相关、形态模式分析及转录组空间相似性计算。该框架将ST从静态工作流转变为交互探索模式，极大提升了可访问性和生物学发现潜力。
source: biorxiv
selection_source: fresh_fetch
motivation: 降低空间转录组学分析门槛，将静态计算流程转化为交互式图像体验，整合形态与转录组信息。
method: 基于点选式虚拟显微镜，从低分辨率时空数据快速推断高分辨影像，并分解组织图像为三类形态学先验，实现基因表达与局部形态的直接整合。
result: 生成显微级可视化，支持区室富集、边界一致性、空间交叉相关、形态模式及转录组空间相似性等多种分析。
conclusion: NaVis将空间转录组学转变为交互探索工具，拓宽了其可访问性和生物发现潜力。
---

## 摘要
尽管空间转录组学（ST）已被广泛采用，但揭示转录层与组织形态之间的对齐在技术上仍然要求很高，通常需要熟练掌握多种计算框架，从而限制了生物医学界相当一部分人的可及性。在此，我们介绍NaVis（https://github.com/Izzilab/NaVis），一种点击式虚拟显微镜框架，它将ST分析重新定义为一种交互式、以图像为中心的体验。NaVis能够从低分辨率全转录组平台快速进行高分辨率推断，生成类显微镜可视化，同时保留全转录组覆盖。它进一步将组织学图像分解为定量组织结构先验——富核区域、纤维状细胞外基质和软组织——从而允许基因表达与局部形态的直接整合。这种统一表示支持区室富集、边界一致性、空间互相关、形态模式、组织学-表达解耦以及全转录组空间相似性的分析。通过将转录组和图像衍生信息耦合在一个交互式框架内，NaVis将ST从静态计算工作流转变为一种探索性模式，拓宽了其可及性、概念范围以及生物学发现的潜力。

## Abstract
Despite the widespread adoption of spatial transcriptomics (ST), revealing the alignment between transcriptional layers and tissue morphology remains technically demanding, typically requiring proficiency across multiple computational frameworks and thereby limiting accessibility for a substantial fraction of the biomedical community. Here, we introduce NaVis (https://github.com/Izzilab/NaVis), a point-and-click virtual microscopy framework that redefines ST analysis as an interactive, image-centric experience. NaVis enables rapid high-resolution inference from low-resolution whole-transcriptome platforms, producing microscopy-like visualizations while preserving transcriptome-wide coverage. It further decomposes histological images into quantitative tissue architecture priors - nuclei-rich regions, fibrillar extracellular matrix, and soft tissue - allowing direct integration of gene expression with local morphology. This unified representation supports analyses of compartment enrichment, boundary concordance, spatial cross-correlation, morphological patterning, histology-expression decoupling, and transcriptome-wide spatial similarity. By coupling transcriptomic and image-derived information within an interactive framework, NaVis shifts ST from static computational workflows to an exploratory modality, broadening its accessibility, conceptual reach and potential for biological discoveries.