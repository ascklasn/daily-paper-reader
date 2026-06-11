---
title: "NaVis: a virtual microscopy framework for interactive histological interrogation of spatial transcriptomics data"
title_zh: NaVis：一个用于空间转录组数据交互式组织学探查的虚拟显微镜框架
authors: "Oshinjo, A., Wu, J., Petrov, P., Hashmi, A., Englund, J. I., Izzi, V."
date: 2026-06-09
pdf: "https://www.biorxiv.org/content/10.64898/2026.02.18.706509v2.full.pdf"
tags: ["query:spatialprot"]
score: 7.0
evidence: 交互式虚拟显微镜用于空间转录组学，可促进与蛋白质组学的整合
tldr: 空间转录组学分析需跨多个计算框架，限制可访问性。NaVis作为点选式虚拟显微镜框架，从低分辨率全转录组数据快速推断高分辨率显微镜样可视化，并分解组织学图像为定量先验（核、纤维基质、软组织）。支持隔室富集、边界一致性、空间互相关等分析，实现转录组与形态直接整合。将ST从静态工作流转变为交互式探索，拓宽可访问性与生物学发现潜力。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有ST分析需多框架协作，操作复杂，阻碍生物医学社区广泛使用。
method: NaVis采用点选式界面，通过低分辨率数据生成高分辨率显微镜样图像，并利用组织学分解先验实现转录组-形态整合。
result: 支持隔室富集、边界一致性、空间互相关、形态模式等多种分析，提供统一交互式探索。
conclusion: NaVis将ST转化为交互式图像模态，降低使用门槛，促进生物学发现。
---

## 摘要
尽管空间转录组学（ST）已被广泛采用，但揭示转录层与组织形态之间的对齐在技术层面仍然要求很高，通常需要熟练掌握多个计算框架，从而限制了生物医学界相当一部分人群的可及性。在此，我们介绍了NaVis（https://github.com/Izzilab/NaVis），一个点击式虚拟显微镜框架，它将ST分析重新定义为交互式的、以图像为中心的体验。NaVis能够从低分辨率全转录组平台进行快速高分辨率推断，生成类似显微镜的可视化效果，同时保持全转录组的覆盖率。它进一步将组织学图像分解为定量的组织架构先验（富核区域、纤维状细胞外基质和软组织），从而允许基因表达与局部形态的直接整合。这种统一表示支持对隔室富集、边界一致性、空间互相关、形态模式、组织学/表达解耦以及全转录组空间相似性进行分析。通过将转录组和图像衍生信息耦合在交互式框架内，NaVis将ST从静态计算工作流转变为探索性模式，拓宽了其可及性、概念范围以及生物发现的潜力。

## Abstract
Despite the widespread adoption of spatial transcriptomics (ST), revealing the alignment between transcriptional layers and tissue morphology remains technically demanding, typically requiring proficiency across multiple computational frameworks and thereby limiting accessibility for a substantial fraction of the biomedical community. Here, we introduce NaVis (https://github.com/Izzilab/NaVis), a point-and-click virtual microscopy framework that redefines ST analysis as an interactive, image-centric experience. NaVis enables rapid high-resolution inference from low-resolution whole-transcriptome platforms, producing microscopy-like visualizations while preserving transcriptome-wide coverage. It further decomposes histological images into quantitative tissue architecture priors (nuclei-rich regions, fibrillar extracellular matrix, and soft tissue) allowing direct integration of gene expression with local morphology. This unified representation supports analyses of compartment enrichment, boundary concordance, spatial cross-correlation, morphological patterning, histology/expression decoupling, and transcriptome-wide spatial similarity. By coupling transcriptomic and image-derived information within an interactive framework, NaVis shifts ST from static computational workflows to an exploratory modality, broadening its accessibility, conceptual reach and potential for biological discoveries.