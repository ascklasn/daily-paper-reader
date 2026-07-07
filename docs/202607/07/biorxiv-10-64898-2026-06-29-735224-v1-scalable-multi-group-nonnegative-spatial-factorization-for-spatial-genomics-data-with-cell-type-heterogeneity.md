---
title: Scalable multi-group nonnegative spatial factorization for spatial genomics data with cell-type heterogeneity
title_zh: 面向细胞类型异质性的空间基因组学数据的可扩展多组非负空间分解
authors: "Chumpitaz-Diaz, L., Shrestha, P., Engelhardt, B. E."
date: 2026-07-03
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.29.735224v1.full.pdf"
tags: ["query:spatialprot"]
score: 6.0
evidence: 空间基因组数据的可扩展因子分析方法，处理细胞类型异质性
tldr: 空间转录组学数据分析常忽略空间信息或混淆细胞类型差异与基因表达模式。本文提出可扩展多组非负空间因子分解（smNSF），利用多组高斯过程建模细胞类型特异的空间变化，并引入非负性增强可解释性。在七个数据集上，smNSF恢复出稀疏、可解释的空间因子，并能通过细胞类型条件后验区分细胞类型富集、特异和通用程序。其变分推断框架支持大规模优化，有助于解耦生物变异来源。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有方法无法有效区分空间基因模式与细胞类型差异驱动的表达变化，限制了生物学解释。
method: 结合空间坐标和细胞类型标签的多组高斯过程先验，并施加非负约束，通过变分推断实现可扩展优化。
result: 在多种组织数据中，细胞类型条件后验揭示了传统分析不可见的空间模式，并实现因子分解的组织。
conclusion: smNSF为空间转录组学提供了细胞类型感知的分解工具，支持解耦生物变异源并进行条件探索。
---

## 摘要
空间转录组学（ST）技术能够研究组织空间背景下的基因表达，为组织结构、细胞相互作用和疾病进展提供见解。然而，现有的降维方法往往忽略空间信息，或者难以区分空间基因模式与由细胞类型差异驱动的模式，从而因混淆基因表达模式差异与细胞类型比例差异而限制了生物学可解释性。为了解决这些挑战，我们引入了可扩展多组非负空间分解（smNSF），这是一个计算上可行的概率框架，将空间坐标和细胞类型标签整合到一个统一的矩阵分解模型中。通过使用多组高斯过程（MGGPs）作为先验，我们的模型以细胞类型特异的方式捕获复杂的空间变异，同时强制非负性以增强可解释性。我们为MGGPs开发了一个变分推理框架，支持可扩展优化并提高了smNSF的数值稳定性。在跨越多种技术和组织的七个空间转录组学数据集中，smNSF恢复了稀疏、可解释的空间因子，并通过其细胞类型条件后验，将它们组织为细胞类型富集、细胞类型特异和通用的空间程序，这些程序仅从边际因子分析中并不明显。给定ST数据中的细胞类型标签，smNSF能够进行细胞类型感知的空间分解，并支持细胞类型条件后验，用于计算机模拟探索空间模式与细胞身份之间的关系。

作者总结：目前大多数空间转录组学分析方法要么忽略空间结构，要么无法分离基因驱动的空间模式与细胞类型驱动的差异。在这项工作中，我们开发了一种同时使用空间坐标和细胞类型标签的方法，以更好地揭示基因表达模式。我们的方法——可扩展多组非负空间分解（smNSF）——使用高斯过程对空间结构进行建模，我们将其扩展，通过一个称为多组高斯过程的统一框架同时捕获空间结构和细胞类型。将smNSF应用于来自小鼠大脑和人类组织的空间转录组学数据集，我们发现以不同细胞类型为条件会揭示标准分析中不可见的空间模式：某些细胞类型抑制一种模式，其他细胞类型则强化它，还有一些模式仅在条件化后才显现结构。这有助于我们理解细胞类型特异的空间程序如何促进组织组织。为了使这种分析在现代空间实验的规模上易于处理，我们还引入了高斯过程的一种新的计算近似，该近似原则上可直接应用于其他潜在变量GP模型。这些工具共同帮助解开生物变异来源，并支持计算机模拟探索在不同组织或细胞类型组成下基因表达可能如何变化。

## Abstract
Spatial transcriptomics (ST) technologies enable the study of gene expression within the spatial context of tissues, providing insights into tissue structure, cellular interactions, and disease progression. However, existing dimension reduction methods often overlook spatial information or struggle to distinguish spatial gene patterns from those driven by cell-type differences, limiting biological interpretability by convolving differences in gene expression patterns with differences in cell-type proportions. To address these challenges, we introduce the scalable multi-group nonnegative spatial factorization (smNSF), a computationally-tractable probabilistic framework that integrates spatial coordinates and cell-type labels into a unified matrix factorization model. By using multi-group Gaussian processes (MGGPs) as priors, our model captures complex spatial variation in a cell-type specific way while enforcing nonnegativity to enhance interpretability. We develop a variational inference framework for MGGPs that supports scalable optimization and improves the numerical stability of smNSF. Across seven spatial transcriptomics datasets spanning diverse technologies and tissues, smNSF recovers sparse, interpretable spatial factors and, through its cell-type conditional posteriors, organizes them into cell-type enriched, cell-type specific, and universal spatial programs that are not apparent from marginal factors alone. Given cell-type labels in ST data, smNSF enables cell-type aware spatial decompositions and supports cell-type conditional posteriors for in silico exploration of relationships between spatial patterns and cellular identity.

Author summaryMost current analysis methods for spatial transcriptomics either ignore spatial structure or fail to separate gene-driven spatial patterns from cell-type driven differences. In this work, we develop a method that uses spatial coordinates and cell-type labels together to better uncover patterns of gene expression. Our approach, scalable multi-group nonnegative spatial factorization (smNSF), uses Gaussian processes to model spatial structure, which we extend to capture both spatial structure and cell type within a unified framework called multi-group Gaussian processes.

Applying smNSF to spatial transcriptomics datasets from mouse brain and human tissues, we find that conditioning on different cell types reveals spatial patterns that are invisible in standard analyses: some cell types suppress a pattern, others sharpen it, and some reveal structure that only emerges after conditioning. This helps us understand how cell-type specific spatial programs contribute to tissue organization.

To make this analysis tractable on the scale of modern spatial experiments, we also introduce a new computational approximation for Gaussian processes that is directly applicable in principle to other latent variable GP models. Together, these tools help disentangle biological sources of variation and support in silico exploration of how gene expression might change under different tissue or cell-type compositions.