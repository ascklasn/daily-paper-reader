---
title: Multi-resolution Spatial Graphical Regression Models for Hierarchical Spatial Transcriptomics Data
title_zh: 用于分层空间转录组数据的多分辨率空间图形回归模型
authors: "Chen, L., Acharyya, S., May, A. M., Udager, A. M., Keller, E. T., Baladandayuthapani, V."
date: 2026-06-01
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.12.724724v3.full.pdf"
tags: ["query:spatialprot"]
score: 8.0
evidence: 空间转录组层次化建模用于癌症
tldr: 空间转录组数据存在肿瘤内分层空间组织，但现有基因网络推断方法未能充分利用这一结构。本文提出贝叶斯多分辨率空间图形回归框架（mSGR），允许基因调控网络随分层空间域变化，通过空间结构边选择策略和GP先验建模网络异质性。模拟实验表明mSGR在恢复网络结构上优于现有方法。应用于肾癌多分辨率数据，发现上皮-间充质转化过渡区域调控连接增强，并识别沿肿瘤梯度的关键调控基因。该框架为理解肿瘤微环境空间组织提供了新工具。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有基因网络推断方法忽略肿瘤内分层空间组织，无法捕获沿病理梯度的基因调控变化。
method: 提出贝叶斯多分辨率空间图形回归，允许精度矩阵随分层区域变化，用空间边选择和GP先验建模异质性，通过变分贝叶斯实现高效推断。
result: 模拟中网络结构恢复优于对比方法；肾癌分析显示EMT过渡区调控连接增强并识别沿肿瘤梯度的hub基因。
conclusion: mSGR实现了空间分辨的基因网络推断，揭示了肿瘤微环境分层组织中的关键调控关系。
---

## 摘要
空间转录组学（ST）技术的进展使得对肿瘤微环境、肿瘤梯度和基因调控网络的系统性分子表征成为可能。已知癌症进展沿病理梯度变化，但现有的基因网络推断方法通常忽略肿瘤内的分层空间组织。我们开发了贝叶斯多分辨率空间图形回归（mSGR）框架，用于从多分辨率ST数据推断空间变化的基因网络。所提出的模型允许精度矩阵在分层结构的空间域之间变化，捕捉肿瘤内的局部和全局组织。为了识别空间变化的调控关系，我们引入了一种空间结构化的边选择策略，该策略根据空间邻近性和病理梯度跨区域借用强度，同时高斯过程先验灵活地建模边强度的空间变化。通过带有节点并行回归的增广平均场变分贝叶斯算法实现可扩展推理，从而在高维设置中实现高效估计。模拟研究表明，与竞争方法相比，网络结构的恢复有所改进。将mSGR应用于肾癌的多分辨率ST数据，揭示了上皮-间充质转化通路过渡区域中更强的调控连接性，并识别了沿肿瘤梯度的枢纽基因，说明了空间分辨网络分析如何为肿瘤微环境组织提供关键见解。

## Abstract
Advances in spatial transcriptomics (ST) technologies enable systematic molecular characterization of tumor microenvironment, tumor gradients and gene regulatory networks. Cancer progression is known to vary along pathological gradients, yet existing network approaches for gene network inference typically ignore hierarchical spatial organization across the tumor. We develop a Bayesian multi-resolution spatial graphical regression mSGR framework to infer spatially varying gene networks from multi-resolution ST data. The proposed model allows precision matrices to vary across hierarchically structured spatial domains, capturing both local and global organization within the tumor. To identify spatially varying regulatory relationships, we introduce a spatially structured edge selection strategy that borrows strength across regions according to spatial proximity and pathological gradients, while Gaussian-process priors flexibly model spatial variation in edge strengths. Scalable inference is achieved through an augmented mean-field variational Bayes algorithm with node-wise parallel regressions, enabling efficient estimation in high-dimensional settings. Simulation studies demonstrate improved recovery of network structures compared with competing approaches. Applying mSGR to multi-resolution ST data from kidney cancer reveals stronger regulatory connectivity in transitional regions of epithelial-mesenchymal transition pathway and identifies hub genes along the tumor gradient, illustrating how spatially resolved network analysis can provide key insights into tumor microenvironment organization.