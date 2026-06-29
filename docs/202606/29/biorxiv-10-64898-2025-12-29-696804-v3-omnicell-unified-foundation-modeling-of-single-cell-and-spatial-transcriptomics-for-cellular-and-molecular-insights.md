---
title: "OmniCell: Unified Foundation Modeling of Single-Cell and Spatial Transcriptomics for Cellular and Molecular Insights"
title_zh: OmniCell：单细胞与空间转录组学的统一基础建模用于细胞与分子洞察
authors: "Pang, J., Qiu, P., He, Y., Deng, Y., Tang, W., Zhi, H., Yan, J., Li, B., Lin, A., Cao, L., Teng, F., Fang, S., Li, S., Deng, Z., Zhang, Y., Li, Y., Xu, X."
date: 2026-06-23
pdf: "https://www.biorxiv.org/content/10.64898/2025.12.29.696804v3.full.pdf"
tags: ["query:spatialprot"]
score: 6.0
evidence: 整合组织上下文的空间转录组基础模型
tldr: 单细胞与空间转录组数据缺乏统一建模，细胞转录程序受组织环境调控。OmniCell基于6700万细胞及空间图谱预训练，整合基因身份、表达量及组织上下文，构建统一基础模型。该模型实现了分子、细胞到组织尺度的跨层次转录组组织，提升了空间细胞身份、解剖域及细胞类型组成的重建精度。通过肝癌数据揭示了肿瘤-过渡区分子特征，并证明基因功能在不同组织微环境中存在差异，确立了组织上下文作为转录组表示的核心维度。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有单细胞及空间转录组方法未能统一整合基因表达与组织微环境，导致细胞程序在完整组织中的功能理解受限。
method: OmniCell基于6700万单细胞与空间图谱进行预训练，通过联合基因身份、表达量及空间上下文构建组织上下文转录组基础模型。
result: 模型恢复细胞类型程序、跨批次稳健结构，提升空间细胞身份重建；在肝癌数据中精确定位肿瘤-过渡区，揭示组织依赖性基因功能变异。
conclusion: 组织上下文是转录组表示的主要轴，为研究细胞程序在完整组织中的生物学意义提供了新框架。
---

## 摘要
细胞的转录程序并非仅由基因表达完全定义，还受该程序实施的组织环境所影响。单细胞RNA测序在解离后解析分子身份，而空间转录组学保留组织结构但受限于实验特异性的稀疏性和基因覆盖度。在此，我们提出OmniCell，一个基于6700万个解离和空间解析图谱预训练的组织情境转录组基础模型。通过整合基因身份、表达量级和组织环境，OmniCell将转录程序与其运作的细胞邻域和解剖背景联系起来。OmniCell跨分子、细胞和组织尺度组织转录组。它恢复了细胞类型特异程序和组织对齐的基因模块，保留了跨批次、物种和稀有群体的稳健细胞状态结构，并改进了空间细胞身份、解剖区域和细胞类型组成的重建。在人类肝癌Stereo-seq数据中，OmniCell解析了一个以免疫浸润、急性期炎症、凝血/补体活性和金属硫蛋白相关金属离子解毒为特征的肿瘤-边缘过渡区。情境基因嵌入相似性分析显示，基因关系在肿瘤核心、过渡区和瘤旁/邻近非恶性微环境中存在差异，表明OmniCell捕获组织依赖的基因功能而非仅表达相似性。在小鼠大脑发育和猕猴皮层中，空间虚拟扰动将调控基因映射到阶段和区域特异的解剖程序上。总之，这些结果确立了组织环境作为转录组表征的主轴，并为研究细胞程序如何在完整组织中获取情境依赖的生物意义提供了框架。

## Abstract
A cells transcriptional programme is not fully defined by gene expression alone, but by the tissue context in which that programme is enacted. Single-cell RNA sequencing resolves molecular identity after dissociation, whereas spatial transcriptomics preserves tissue architecture but remains constrained by assay-specific sparsity and gene coverage. Here we present OmniCell, a tissue-contextual transcriptomic foundation model pretrained on 67 million dissociated and spatially resolved profiles. By integrating gene identity, expression magnitude and tissue context, OmniCell links transcriptional programmes to the cellular neighbourhoods and anatomical contexts in which they operate. OmniCell organised transcriptomes across molecular, cellular and tissue scales. It recovered cell-type-specific programmes and tissue-aligned gene modules, preserved robust cell-state structure across batches, species and rare populations, and improved the reconstruction of spatial cell identity, anatomical domains and cell-type composition. In human liver cancer Stereo-seq data, OmniCell resolved a tumour-margin transition zone characterised by immune infiltration, acute-phase inflammation, coagulation/complement activity and metallothionein-linked metal-ion detoxification. Contextual gene-embedding similarity analysis showed that gene relationships differed across tumour core, transition-zone and paratumour/adjacent non-malignant niches, indicating that OmniCell captures tissue-dependent gene function rather than expression similarity alone. In mouse brain development and macaque cortex, spatial virtual perturbations mapped regulatory genes onto stage- and region-specific anatomical programmes. Together, these results establish tissue context as a primary axis of transcriptomic representation and provide a framework for studying how cellular programmes acquire context-dependent biological meaning in intact tissues.