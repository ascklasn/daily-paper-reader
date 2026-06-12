---
title: "NaVis: a virtual microscopy framework for interactive histological interrogation of spatial transcriptomics data"
title_zh: NaVis：用于空间转录组数据交互式组织学探查的虚拟显微镜框架
authors: "Oshinjo, A., Wu, J., Petrov, P., Hashmi, A., Englund, J. I., Izzi, V."
date: 2026-06-09
pdf: "https://www.biorxiv.org/content/10.64898/2026.02.18.706509v2.full.pdf"
tags: ["query:spatialprot"]
score: 6.0
evidence: 用于交互式空间转录组数据分析的虚拟显微镜框架
tldr: 空间转录组数据与组织形态的对齐分析通常需要跨多个计算框架，技术门槛高。NaVis提供点选式虚拟显微镜框架，从低分辨率全转录组平台快速推断高分辨率显微可视化，并分解组织学图像为核富集区、纤维细胞外基质等定量组织架构先导。该框架支持多种空间分析，使基因表达与局部形态直接整合，将空间转录组学从静态工作流转变为交互探索性模态，拓展了生物发现潜力。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有空间转录组分析方法需跨多个计算框架，技术门槛高，限制了生物医学界的可及性。
method: NaVis通过点选式交互，从低分辨率全转录组数据推断高分辨率显微可视化，并分解组织学图像为定量组织架构先导。
result: 快速生成显微级可视化并保留全转录组覆盖，支持多种空间分析，实现转录组与形态的直接整合。
conclusion: NaVis将空间转录组学转变为交互探索性模态，扩大了可访问性和概念范围，促进生物学发现。
---

## 摘要
尽管空间转录组学（ST）已被广泛采纳，但揭示转录层与组织形态之间的对应关系在技术上仍然具有挑战性，通常需要熟练掌握多种计算框架，这限制了生物医学界相当一部分研究人员的使用。在此，我们介绍NaVis（https://github.com/Izzilab/NaVis），一个即点即用的虚拟显微镜框架，它将ST分析重新定义为一种交互式、以图像为中心的体验。NaVis能够从低分辨率全转录组平台快速推断出高分辨率结果，生成类似显微镜的视觉图像，同时保持全转录组覆盖。它进一步将组织学图像分解为定量组织架构先验（富核区域、纤维状细胞外基质和软组织），从而将基因表达与局部形态直接整合。这种统一表示支持区室富集、边界一致性、空间交叉相关、形态模式、组织学/表达解耦以及全转录组空间相似性等分析。通过将转录组和图像衍生信息耦合在一个交互框架内，NaVis将ST从静态计算工作流程转变为探索性模式，拓宽了其可及性、概念范围以及生物学发现的潜力。

## Abstract
Despite the widespread adoption of spatial transcriptomics (ST), revealing the alignment between transcriptional layers and tissue morphology remains technically demanding, typically requiring proficiency across multiple computational frameworks and thereby limiting accessibility for a substantial fraction of the biomedical community. Here, we introduce NaVis (https://github.com/Izzilab/NaVis), a point-and-click virtual microscopy framework that redefines ST analysis as an interactive, image-centric experience. NaVis enables rapid high-resolution inference from low-resolution whole-transcriptome platforms, producing microscopy-like visualizations while preserving transcriptome-wide coverage. It further decomposes histological images into quantitative tissue architecture priors (nuclei-rich regions, fibrillar extracellular matrix, and soft tissue) allowing direct integration of gene expression with local morphology. This unified representation supports analyses of compartment enrichment, boundary concordance, spatial cross-correlation, morphological patterning, histology/expression decoupling, and transcriptome-wide spatial similarity. By coupling transcriptomic and image-derived information within an interactive framework, NaVis shifts ST from static computational workflows to an exploratory modality, broadening its accessibility, conceptual reach and potential for biological discoveries.