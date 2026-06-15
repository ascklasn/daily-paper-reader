---
title: "HoloCell: A Generative Foundation Model for Holistic Cellular Modeling"
title_zh: HoloCell：用于整体细胞建模的生成基础模型
authors: "Jiang, Q., Li, Z., Hu, B., Bie, Y., Li, K., Li, Q., Jin, P., He, Y., Deng, P., Wang, Z., Chen, X., Qin, T., Liu, H., Jiang, R., Yin, Q."
date: 2026-06-11
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.07.730684v1.full.pdf"
tags: ["query:spatialprot"]
score: 6.0
evidence: 单细胞多组学整合包括蛋白质组学
tldr: 单细胞多组学数据整合面临模态异构和缺失问题，现有方法依赖配对样本且通用性不足。HoloCell提出层次化tokenization策略，将顺式调控元件、基因和蛋白质编码为结构化token，基于8.6亿参数在4.68亿单细胞图谱上预训练，并通过迭代扩散与重遮罩实现跨模态生成。该模型在表示学习、多组学整合及生成任务中显著优于现有方法，为虚拟细胞提供了统一的数字映射与模拟框架。
source: biorxiv
selection_source: fresh_fetch
motivation: 解决单细胞多组学模态异构和缺失问题，建立统一且鲁棒的联合建模框架。
method: 提出层次化tokenization编码三类生物特征，结合迭代扩散与重遮罩实现跨模态生成。
result: 在单组学表示学习、多组学整合及跨模态生成任务中均取得最优性能。
conclusion: HoloCell作为虚拟细胞基础模型，实现系统性表征与生成模拟。
---

## 摘要
单细胞多组学技术近期取得了进展，能够对单个细胞内的表观基因组、转录组和蛋白质组层进行剖析，为将细胞状态作为整合的生物系统进行表征提供了新机遇。然而，开发一个能够无缝整合多种组学模式并稳健应对异质性模式缺失的统一框架仍然具有挑战性。现有方法通常针对特定模式或模式对设计，依赖于数据集特定的训练或配对测量。在此，我们提出HoloCell，据我们所知，这是首个用于三大主要单细胞组学模式（即表观基因组学、转录组学和蛋白质组学）联合表示学习和生成建模的生成基础模型。HoloCell包含超过8.6亿个参数，并在人类多组学语料库（Human-Multi-Omics-Corpus）上进行了预训练，该语料库包含约4.68亿个跨这三个组学层的单细胞图谱，对应超过4250亿个token。HoloCell引入了一种简单但具有生物学基础的分层分词化策略，将顺式调控元件、基因和蛋白质编码为共享建模框架内的结构化token。我们通过单组学表示学习、配对多组学整合、非配对多组学对齐以及通过迭代扩散和重新掩码的跨模态生成对HoloCell进行了评估，展示了其在多种组学任务中的卓越性能和灵活性。从表示角度看，HoloCell提供了跨多个组学层的细胞状态统一数字映射，将细胞异质性捕捉为一个整合系统。从生成角度看，其迭代扩散和重新掩码框架考虑了生物特征固有的无序性，实现了多组学信息流的计算机模拟。综合这些能力，HoloCell作为一个多功能基础模型，朝着虚拟细胞这一新兴概念迈进，在统一框架内提供细胞系统的系统性表征和生成性模拟。

## Abstract
Single-cell multi-omics technologies have recently advanced to enable the profiling of epigenomic, transcriptomic, and proteomic layers within individual cells, offering new opportunities to characterize cellular states as integrated biological systems. However, developing a unified framework that can seamlessly integrate diverse omics modalities and remain robust to heterogeneous modality missingness remains challenging. Existing methods are often designed for specific modalities or modality pairs, relying on dataset-specific training or paired measurements. Here we present HoloCell, to our knowledge the first generative foundation model for joint representation learning and generative modeling across all three major single-cell omics modalities,i.e., epigenomics, transcriptomics, and proteomics. HoloCell contains over 860 million parameters and is pretrained on the Human-Multi-Omics-Corpus, which comprises approximately 468 million single-cell profiles across these three omics layers, corresponding to over 425 billion tokens. HoloCell introduces a a simple yet biologically grounded hierarchical tokenization strategy that encodes cis-regulatory elements, genes, and proteins as structured tokens within a shared modeling framework. We evaluated HoloCell across single-omics representation learning, paired multi-omics integration, unpaired multi-omics alignment, and cross-modal generation via iterative diffusion and remasking, demonstrating its superior performance and flexibility across diverse omics tasks. From a representation perspective, HoloCell provides a unified digital mapping of cellular states across multiple omics layers, capturing cell heterogeneity as an integrated system. From a generation perspective, its iterative diffusion and remasking framework accounts for the inherently unordered nature of biological features, enabling in silico simulation of multi-omics information flow. Together, these capabilities position HoloCell as a versatile foundation model toward the emerging concept of a virtual cell, offering both systematic characterization and generative simulation of cellular systems within a unified framework.