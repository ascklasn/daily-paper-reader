---
title: From unsupervised clustering to atlas-guided annotation in cohort-scale spatial omics with HiCAT
title_zh: 从无监督聚类到图集引导注释：HiCAT在队列规模空间组学中的应用
authors: "Huang, J., Shen, X., Smith, Y., Harik, L., Wang, L., Yu, J., Epstein, M., Hu, J."
date: 2026-05-31
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.27.728266v1.full.pdf"
tags: ["query:spatialprot"]
score: 7.0
evidence: 空间组学区域标注的机器学习框架
tldr: "当前空间组学数据分析依赖病理学家手工标注，费时且仅基于形态学，忽略分子定义区域。HiCAT基于无监督聚类和参考图谱引导的机器学习框架，自动生成高精度区域注释。在七个数据集上中位数准确率相对提升107%，能发现原始标注未捕获的分子亚区域，如肿瘤和脑亚区。该方法为大规模空间组学分析提供一致、高粒度的标注，并为基础模型提供训练标签。"
source: biorxiv
selection_source: fresh_fetch
motivation: 克服病理学家手工标注的局限，自动生成分子信息丰富的区域注释以揭示空间异质性。
method: 结合无监督聚类和参考图谱引导的机器学习框架，自动将病理学家知识迁移至新样本。
result: "七个数据集上中位数准确率相对提升107%，并发现临床相关的肿瘤亚区和疾病进展脑亚区。"
conclusion: HiCAT为大规模空间组学提供一致、高粒度的生物信息区域注释，支撑下游分析与基础模型训练。
---

## 摘要
病理学家注释的组织区域为检查空间组学数据提供了基本参考，但由于需要大量人工操作，此类注释仅适用于有限数量的样本。此外，这些注释源自单个组织学图像中的形态，可能忽略分子定义的区域并掩盖样本内异质性。为解决这些限制，我们提出了HiCAT，这是一个机器学习框架，可自动生成基于病理学知识的区域注释，并表征空间组学数据中的区域异质性。在七个数据集中，HiCAT始终优于最先进的方法，准确率中位数相对提升107%。除了转移病理学家的注释，HiCAT还揭示了原始注释未捕获的分子定义的区域异质性，包括与临床结果相关的肿瘤亚区和与时空疾病进展一致的大脑亚区。通过在大型队列中生成一致、高粒度且具有生物学意义的区域注释，HiCAT实现了可扩展的下游分析，并为空间生物学的基础模型提供了训练标签。

## Abstract
Pathologist-annotated tissue regions provide a fundamental reference for examining spatial omics data, yet such annotations are available for a limited number of samples due to the substantial manual effort required. Moreover, these annotations are derived from morphology within individual histology images, which can overlook molecularly defined regions and obscure intra-sample heterogeneity. To address these limitations, we present HiCAT, a machine-learning framework that automatically generates pathologist-informed region annotations and characterizes regional heterogeneity in spatial omics data. Across seven datasets, HiCAT consistently outperforms state-of-the-art methods, achieving a median relative improvement of 107% in accuracy. Beyond transferring pathologist annotations, HiCAT uncovers molecularly informed regional heterogeneity not captured by original annotations, including tumor subregions associated with clinical outcomes and brain subregions aligned with spatiotemporal disease progression. By generating consistent, highly granular, and biologically informative region annotations across large cohorts, HiCAT enables scalable downstream analysis and provides training labels for foundation models in spatial biology.