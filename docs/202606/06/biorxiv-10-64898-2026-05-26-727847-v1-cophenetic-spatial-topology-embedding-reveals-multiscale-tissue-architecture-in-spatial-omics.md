---
title: Cophenetic Spatial Topology Embedding reveals multiscale tissue architecture in spatial omics
title_zh: 共表型空间拓扑嵌入揭示空间组学中的多尺度组织结构
authors: "Long, M., Hu, T., Sountoulidis, A., Samakovlis, C., Nilsson, M."
date: 2026-05-29
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.26.727847v1.full.pdf"
tags: ["query:spatialprot"]
score: 6.0
evidence: 适用于空间蛋白质组学的多尺度组织架构计算框架
tldr: 针对当前空间组学分析侧重于局部邻域而忽略整体组织架构的问题，本文提出Cophenetic Spatial Topology Embedding (COSTE)框架。该方法无需定义空间半径或邻域阈值，通过嵌入有向最近邻距离轮廓到层次度量空间来量化多尺度组织拓扑，可处理细胞级和单转录本数据，无需细胞分割。COSTE输出空间分离分数SSS，在肺纤维化和三阴性乳腺癌数据集上成功刻画组织结构、定义空间细胞状态，并发现局部邻域分析难以捕获的疾病或治疗相关架构模式，为空间组学提供了可解释的组织架构探索工具。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有空间组学分析工具多聚焦局部邻域，难以揭示多尺度的整体组织架构，缺乏无需预设空间参数的全局量化方法。
method: COSTE通过构建细胞群间的有向最近邻距离轮廓，利用层次聚类嵌入到层次度量空间，输出样本归一化的空间分离分数SSS，无需定义空间半径。
result: 在肺纤维化和三阴性乳腺癌数据中，COSTE清晰刻画了组织区域、识别空间定义的细胞状态，并捕获了局部邻域分析遗漏的疾病与治疗相关的组织模式。
conclusion: COSTE作为一种无需半径阈值的可解释框架，为探索空间组学中多尺度组织架构和细胞空间关系提供了有效手段。
---

## 摘要
组织的空间结构源于细胞在多个尺度上的相互作用，然而当前的空间组学分析工具通常侧重于局部邻域，可能无法概括更广泛的组织结构。本文介绍了共表型空间拓扑嵌入（COSTE），这是一种计算框架，可将有向最近邻距离分布嵌入到层次度量空间中，无需用户定义空间半径或邻域截断。COSTE可应用于细胞水平和单转录本输入，无需细胞分割。它构建细胞群体之间的有向距离分布，并使用层次聚类量化组织拓扑结构。由此产生空间分离评分（SSS），这是一个从0到1的样本标准化评分，用于总结分析组织中相对空间分离程度。我们将COSTE应用于肺纤维化和三阴性乳腺癌（TNBC）的空间转录组数据集，它能够描绘组织结构、提名空间定义的细胞状态，并突出显示基于局部邻域分析难以捕捉到的疾病或治疗相关结构模式。我们的方法为探索空间组学数据中的组织结构及细胞间空间关系提供了一个可解释的框架。

## Abstract
The spatial organization of tissues emerges from cell interactions across multiple scales, yet current spatial omics analysis tools often emphasize local neighborhoods and may not summarize broader tissue architecture. Here we introduce Cophenetic Spatial Topology Embedding (COSTE), a computational framework that embeds directed nearest-neighbor distance profiles into a hierarchical metric space without requiring the user to define a spatial radius or neighborhood cutoff. COSTE can be applied to cell-level and single-transcript inputs without requiring cell segmentation. It constructs directed distance profiles between cell populations and uses hierarchical clustering to quantify tissue topology. This yields a Spatial Separation Score (SSS), a sample-normalized score from 0 to 1 that summarizes relative spatial separation within an analyzed tissue. We apply COSTE to spatial transcriptomics datasets of pulmonary fibrosis and triple-negative breast cancer (TNBC), where it delineates tissue structures, nominates spatially defined cell states, and highlights disease-or treatment-associated architectural patterns that are not readily captured by local neighborhood-based analyses. Our approach provides an interpretable framework for exploring tissue architecture and cell-cell spatial relationships in spatial omics data.