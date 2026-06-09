---
title: "Multivariate integration of histological images and gene expression data: a comparative review"
title_zh: 组织学图像与基因表达数据的多变量整合：比较综述
authors: "Ma, C., Mao, J., Le Cao, K.-A."
date: 2026-06-06
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.02.729734v1.full.pdf"
tags: ["query:spatialprot"]
score: 6.0
evidence: 整合组织学图像与基因表达，可用于空间蛋白组学整合
tldr: 组织学图像与基因表达数据的整合面临高维度、跨模态异质性和可解释性不足的挑战。采用Sparse CCA、Joint NMF和AJIVE等多变量方法降维并提取潜在因子。在乳腺癌数据中对比发现，各方法捕捉到不同但互补的生物学信息。本研究系统评估了方法学特性与可解释性，为成像-组学整合研究提供了方法选择指导。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有整合方法缺乏系统比较，用户难以根据建模假设合理选择。
method: "以乳腺癌H&E图像和基因表达数据为例，比较Sparse CCA、Joint NMF和AJIVE的降维与特征识别能力。"
result: 三种方法分别捕捉互补的生物学信息，在疾病亚型识别上表现各异。
conclusion: 各方法各有优劣，未来应结合多种方法提高整合分析的全面性。
---

## 摘要
将组织学图像与基因表达数据相结合，为连接组织形态学与分子特征并改进疾病亚型分类提供了一种有前景的方法。然而，由于这些数据集的高维性、跨模态异质性和有限的可解释性，这种整合仍然具有挑战性。诸如稀疏典型相关分析（Sparse CCA）、联合非负矩阵分解（Joint NMF）和基于角度的联合与个体变异解释（AJIVE）等多变量方法已被用于应对这些挑战，通过降维同时识别与潜在因子相关的特征，从而增强生物学可解释性。尽管在影像组学研究中应用日益增多，但对其方法特性的系统比较仍然有限。因此，用户在实践中往往缺乏如何恰当选择这些方法的指导，并且这些方法尽管建模假设不同，却常被视为可互换。本文以乳腺癌的配对H&E图像和基因表达数据作为代表性案例研究，考察了这些整合方法的方法特性、可解释性和互补性。结果表明，每种方法捕捉了底层信息的不同但互补的方面。尽管生物学发现来自TCGA-BRCA数据集，但本文识别的方法学见解更广泛地适用于影像组学整合研究。总体而言，本比较综述强调了每种方法的优势和局限性，并概述了未来方法学发展的考虑事项。

## Abstract
Integrating histological images with gene expression data offers a promising approach for linking tissue morphologies to molecular signatures and improving disease subtyping. However, such integration remains challenging due to the high dimensionality of these datasets, cross-modal heterogeneity, and limited interpretability. Multivariate methods such as Sparse Canonical Correlation Analysis (Sparse CCA), Joint Nonnegative Matrix Factorisation (Joint NMF), and Angle-based Joint and Individual Variation Explained (AJIVE), have been used to address these challenges by reducing dimensionality while identifying features associated with latent factors, thereby enhancing biological interpretability. Despite increasing application in imaging-omics research, systematic comparisons of their methodological properties remain limited. Consequently, users often lack guidance on how to appropriately select these methods in practice, and these approaches are frequently treated as interchangeable despite differing modelling assumptions. Here, we use paired H\&E images and gene expression data from breast cancer as a representative case study to examine the methodological characteristics, interpretability, and complementary properties of these integration approaches. Our results show that each method captures distinct yet complementary aspects of the underlying information. Although the biological findings are derived from the TCGA-BRCA datasets, the methodological insights identified here extend more broadly to imaging-omics integration studies. Overall, this comparative review highlights the strengths and limitations of each approach and outlines considerations for future methodological development.