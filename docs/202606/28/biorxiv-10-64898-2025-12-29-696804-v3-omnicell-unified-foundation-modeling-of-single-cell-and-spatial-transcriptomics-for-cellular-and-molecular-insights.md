---
title: "OmniCell: Unified Foundation Modeling of Single-Cell and Spatial Transcriptomics for Cellular and Molecular Insights"
title_zh: OmniCell：单细胞与空间转录组学的统一基础建模，用于细胞与分子洞察
authors: "Pang, J., Qiu, P., He, Y., Deng, Y., Tang, W., Zhi, H., Yan, J., Li, B., Lin, A., Cao, L., Teng, F., Fang, S., Li, S., Deng, Z., Zhang, Y., Li, Y., Xu, X."
date: 2026-06-23
pdf: "https://www.biorxiv.org/content/10.64898/2025.12.29.696804v3.full.pdf"
tags: ["query:spatialprot"]
score: 7.0
evidence: 连接组织上下文的单细胞和空间转录组基础模型
tldr: 单细胞和空间转录组学数据缺乏整合组织背景的统一表示。OmniCell基于6700万单细胞和空间转录组图谱预训练，融合基因身份、表达量和组织背景，构建跨分子、细胞和组织尺度的统一模型。在人类肝癌Stereo-seq数据中，OmniCell精准识别肿瘤-边缘过渡区的免疫浸润和解毒程序；在小鼠大脑发育和猕猴皮层中，空间虚拟扰动成功映射调控基因的时空功能。该工作证实组织背景是转录组表示的核心维度，为解析细胞程序的上下文依赖功能提供了计算框架。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有转录组模型忽略组织背景，无法捕捉细胞程序在空间和微环境中的功能变化。
method: 预训练OmniCell，联合67M单细胞与空间转录组，通过基因-表达-背景三元组学习统一表示。
result: OmniCell恢复细胞类型程序、跨批次和物种稳健性，精准重建空间结构，并在肝癌中发现肿瘤边缘过渡区的特征。
conclusion: 组织背景是转录组表示的关键轴，OmniCell为研究语境依赖的基因功能提供新框架。
---

## 摘要
细胞的转录程序并不仅仅由基因表达决定，还由该程序得以执行的组织背景所决定。单细胞RNA测序在解离后解析分子身份，而空间转录组学保留组织结构，但仍受限于测定特有的稀疏性和基因覆盖度。在此，我们提出OmniCell，一个基于6700万个解离和空间解析图谱预训练的组织背景转录组基础模型。通过整合基因身份、表达水平与组织背景，OmniCell将转录程序与其运作的细胞邻域和解剖背景联系起来。OmniCell在分子、细胞和组织尺度上组织转录组。它恢复了细胞类型特异性程序和组织对齐的基因模块，在批次、物种和稀有群体中保持了稳健的细胞状态结构，并改进了空间细胞身份、解剖区域和细胞类型组成的重构。在人肝癌Stereo-seq数据中，OmniCell解析了一个肿瘤边缘过渡区，其特征包括免疫浸润、急性期炎症、凝血/补体活性以及金属硫蛋白相关的金属离子解毒作用。上下文基因嵌入相似性分析显示，基因关系在肿瘤核心、过渡区和瘤旁/相邻非恶性微环境中存在差异，表明OmniCell捕捉的是组织依赖的基因功能，而不仅仅是表达相似性。在小鼠大脑发育和猕猴皮层中，空间虚拟扰动将调控基因映射到阶段和区域特异性的解剖程序中。总之，这些结果确立了组织背景作为转录组表征的一个主要轴，并提供了一个框架，用于研究细胞程序如何在完整组织中获取依赖环境的生物学意义。

## Abstract
A cells transcriptional programme is not fully defined by gene expression alone, but by the tissue context in which that programme is enacted. Single-cell RNA sequencing resolves molecular identity after dissociation, whereas spatial transcriptomics preserves tissue architecture but remains constrained by assay-specific sparsity and gene coverage. Here we present OmniCell, a tissue-contextual transcriptomic foundation model pretrained on 67 million dissociated and spatially resolved profiles. By integrating gene identity, expression magnitude and tissue context, OmniCell links transcriptional programmes to the cellular neighbourhoods and anatomical contexts in which they operate. OmniCell organised transcriptomes across molecular, cellular and tissue scales. It recovered cell-type-specific programmes and tissue-aligned gene modules, preserved robust cell-state structure across batches, species and rare populations, and improved the reconstruction of spatial cell identity, anatomical domains and cell-type composition. In human liver cancer Stereo-seq data, OmniCell resolved a tumour-margin transition zone characterised by immune infiltration, acute-phase inflammation, coagulation/complement activity and metallothionein-linked metal-ion detoxification. Contextual gene-embedding similarity analysis showed that gene relationships differed across tumour core, transition-zone and paratumour/adjacent non-malignant niches, indicating that OmniCell captures tissue-dependent gene function rather than expression similarity alone. In mouse brain development and macaque cortex, spatial virtual perturbations mapped regulatory genes onto stage- and region-specific anatomical programmes. Together, these results establish tissue context as a primary axis of transcriptomic representation and provide a framework for studying how cellular programmes acquire context-dependent biological meaning in intact tissues.