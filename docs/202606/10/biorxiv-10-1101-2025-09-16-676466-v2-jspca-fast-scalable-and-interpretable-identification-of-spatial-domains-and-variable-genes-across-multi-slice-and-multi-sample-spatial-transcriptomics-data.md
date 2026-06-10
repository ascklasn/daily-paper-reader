---
title: "jsPCA: fast, scalable, and interpretable identification of spatial domains and variable genes across multi-slice and multi-sample spatial transcriptomics data"
title_zh: jsPCA：面向多切片与多样本空间转录组数据中空间域和可变基因的快速、可扩展且可解释的识别方法
authors: "Assali, I., Escande, P., Picard, F., Villoutreix, P."
date: 2026-06-10
pdf: "https://www.biorxiv.org/content/10.1101/2025.09.16.676466v2.full.pdf"
tags: ["query:spatialprot"]
score: 8.0
evidence: 空间转录组数据中空间域和可变基因的快速可扩展识别方法
tldr: 空间转录组学数据规模庞大，现有方法计算效率低且可解释性不足。jsPCA通过构建空间协方差矩阵并利用联合对角化实现多切片联合分析，无需空间对齐。该方法采用稀疏非凸优化加速，可在数秒至数分钟内完成。在人类背外侧前额叶皮层和小鼠胚胎发育数据集上，jsPCA性能与SpatialPCA等最先进方法相当或更优，同时计算速度更快且更具可解释性。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有空间转录组分析方法在大规模多切片数据上计算慢、可解释性差，需要快速可扩展且可解释的方法。
method: jsPCA基于基因表达协方差与空间自相关的乘积构建空间协方差，通过联合对角化实现多切片联合建模，利用稀疏非凸优化提升计算效率。
result: 在人类背外侧前额叶皮层和小鼠胚胎发育数据集上，jsPCA性能与SpatialPCA等10种方法相当或更优，计算时间从数秒到数分钟。
conclusion: jsPCA提供快速、可扩展且可解释的空间域和可变基因识别，适用于大规模多切片空间转录组数据。
---

## 摘要
组织内空间结构化的细胞异质性对器官健康功能至关重要，这种异质性通过不同空间位置的差异基因表达活性得以体现。空间转录组技术以高空间分辨率在整体组织尺度上记录全基因组范围的基因表达测量。虽然这些技术革新了我们对组织结构的定量理解，但其生成的数据集规模庞大且维度极高（涵盖数万个空间位置记录的數万基因），需要高效的自动化分析方法。本研究提出联合空间PCA（jsPCA）方法，这是一种新颖、快速、可扩展且可解释的方法，用于自动识别多切片与多样本空间转录组数据中的空间域和可变基因。jsPCA基于空间协方差的简单数学公式，该协方差定义为基因表达协方差与空间自相关的乘积。该空间协方差的主成分能够产生具有生物学意义的低维表示，通过简单聚类即可从中推导出空间域。此外，可直接从主成分系数中识别空间可变基因。该方法还能联合表示多个切片和样本（常见实验设置），无需空间对齐即可通过对每个切片获得的空间协方差矩阵集进行联合对角化计算公共主成分。通过利用稀疏性和流形上的非凸优化，jsPCA的计算时间仅需数秒至数分钟，显著优于现有方法。我们在人类背外侧前额叶皮层的Visium 10x数据集和小鼠胚胎发育的Stereo-seq MOSTA数据集上，将jsPCA与10种最新方法（如SpatialPCA、BASS、GraphPCA、Stagate）进行基准测试，结果显示其性能优异，与最新方法相当或更优，同时速度更快、可解释性更强，且能扩展到超大规模数据集。

## Abstract
Spatially structured cell heterogeneity within tissues is essential for healthy organ function. This heterogeneity is reflected by differential gene expression activity at various spatial location. Spatial transcriptomics technologies record genome-wide measurements of gene expression at the scale of entire tissues with high spatial resolution. While they have revolutionized our quantitative understanding of tissue architecture, these technologies generate large and high dimensional datasets encompassing tens of thousands of genes recorded at tens of thousands of spatial locations, requiring efficient automated methods for their analysis. In this study we introduce joint spatial PCA (jsPCA), a novel, fast, scalable and interpretable method for the automatic identification of spatial domains and variable genes in multi-slice and multi-sample spatial transcriptomics data. jsPCA relies on a simple mathematical formulation of a spatial covariance defined as the product of the gene expression covariance with the spatial autocorrelation. The principal components of this spatial covariance yield a biologically meaningful low-dimensional representation. From this representation, we can derive spatial domains by simple clustering. In addition, spatially variable genes can be identified directly from the principal components coefficients. Moreover, this approach enables the joint representation of multiple slices and samples, a frequent experimental setting. This joint representation is obtained without spatial alignment by computing common principal components via joint diagonalization of the set of spatial covariance matrices obtained for each slice. By leveraging sparsity and non-convex optimization on manifold, jsPCA leads to computing time in the order of seconds to minutes, substantially outperforming state-of-the-art approaches. We benchmarked jsPCA on the Visium 10x dataset of human dorsolateral prefrontal cortex and the Stereo-seq MOSTA dataset of mouse embryonic development against 10 state-of-the-art methods. Our approach demonstrated excellent performances, comparable or better than state-of-the-art methods, such as SpatialPCA, BASS, GraphPCA or Stagate, while being much faster, interpretable, and scalable to very large datasets.