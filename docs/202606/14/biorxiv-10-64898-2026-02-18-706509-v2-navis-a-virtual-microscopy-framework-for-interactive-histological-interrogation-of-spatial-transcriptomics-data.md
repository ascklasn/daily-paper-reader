---
title: "NaVis: a virtual microscopy framework for interactive histological interrogation of spatial transcriptomics data"
title_zh: NaVis：一个用于空间转录组数据交互式组织学查询的虚拟显微镜框架
authors: "Oshinjo, A., Wu, J., Petrov, P., Hashmi, A., Englund, J. I., Izzi, V."
date: 2026-06-09
pdf: "https://www.biorxiv.org/content/10.64898/2026.02.18.706509v2.full.pdf"
tags: ["query:spatialprot"]
score: 6.0
evidence: 空间转录组可视化框架，支持高分辨率推断，与空间蛋白组学整合相关
tldr: 空间转录组数据与组织形态的整合依赖多计算框架，技术门槛高。NaVis提出点按式虚拟显微镜框架，将ST分析转化为交互式图像中心体验。它从低分辨率平台快速推断高分辨率图像并保留全转录组覆盖，同时分解组织学图像为核、胞外基质等先验信息。该框架统一了转录组与形态信息，使ST从静态计算转向探索性模态，提升可及性与发现潜力。
source: biorxiv
selection_source: fresh_fetch
motivation: 突破ST数据与组织形态整合的技术壁垒，降低对多计算框架的依赖，提升生物医学社区的可用性。
method: 采用点按式虚拟显微镜框架，整合转录组与图像信息，进行高分辨率推断和图像分解，支持交互式分析。
result: 从低分辨率平台快速推断高分辨率表达图，分解出组织形态先验，实现区室富集、边界一致性、空间交叉相关等分析。
conclusion: NaVis将ST从静态计算转变为交互式探索，拓宽了可及性和生物学发现能力。
---

## 摘要
尽管空间转录组学（ST）已被广泛采用，但揭示转录层与组织形态之间的对齐仍然在技术上具有挑战性，通常需要熟练使用多个计算框架，从而限制了生物医学界相当一部分人群的可及性。在此，我们介绍NaVis（https://github.com/Izzilab/NaVis），一个点击式的虚拟显微镜框架，它将ST分析重新定义为一种以图像为中心的交互式体验。NaVis能够从低分辨率全转录组平台快速推断高分辨率结果，生成类似显微镜的可视化图像，同时保持全转录组覆盖。它进一步将组织学图像分解为定量组织架构先验——富核区域、纤维状细胞外基质和软组织——从而允许基因表达与局部形态的直接整合。这种统一表示支持区室富集分析、边界一致性、空间互相关、形态模式、组织学-表达解耦以及全转录组空间相似性分析。通过将转录组和图像衍生信息结合在一个交互式框架中，NaVis将ST从静态计算工作流转变为一种探索性模式，拓宽了其可及性、概念范围和生物学发现的潜力。

## Abstract
Despite the widespread adoption of spatial transcriptomics (ST), revealing the alignment between transcriptional layers and tissue morphology remains technically demanding, typically requiring proficiency across multiple computational frameworks and thereby limiting accessibility for a substantial fraction of the biomedical community. Here, we introduce NaVis (https://github.com/Izzilab/NaVis), a point-and-click virtual microscopy framework that redefines ST analysis as an interactive, image-centric experience. NaVis enables rapid high-resolution inference from low-resolution whole-transcriptome platforms, producing microscopy-like visualizations while preserving transcriptome-wide coverage. It further decomposes histological images into quantitative tissue architecture priors - nuclei-rich regions, fibrillar extracellular matrix, and soft tissue - allowing direct integration of gene expression with local morphology. This unified representation supports analyses of compartment enrichment, boundary concordance, spatial cross-correlation, morphological patterning, histology-expression decoupling, and transcriptome-wide spatial similarity. By coupling transcriptomic and image-derived information within an interactive framework, NaVis shifts ST from static computational workflows to an exploratory modality, broadening its accessibility, conceptual reach and potential for biological discoveries.