---
title: Spatial Gene Set Enrichment Analysis with Applications to Spatially Resolved Transcriptomic Data
title_zh: 空间基因集富集分析及其在空间分辨转录组数据中的应用
authors: "Xie, Z., Guo, Y., Li, Q., Ma, Y."
date: 2026-06-04
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.01.729158v1.full.pdf"
tags: ["query:spatialprot"]
score: 7.0
evidence: 空间基因集富集方法可推广至空间蛋白质组学
tldr: 现有基因集富集分析忽略空间依赖性，导致检测空间组织通路的效力不足。为此提出spaGSE贝叶斯层次模型，通过高斯混合框架建模基因空间变异信号，并利用逻辑回归关联基因集，结合spike-and-slab先验实现稳健推断。模拟与四个真实空间转录组数据集验证表明，spaGSE在控制假阳性率的同时显著提高检测效力，成功识别出与癌症和发育组织协调空间分布相关的生物学通路。该工作为空间转录组学提供可解释的通路级分析工具。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有基因集富集分析忽略基因表达的空间依赖性，降低检测空间组织通路的效力与可解释性。
method: 提出spaGSE贝叶斯层次模型，以高斯混合建模空间变量基因信号，逻辑回归关联基因集，并采用spike-and-slab先验提升鲁棒性。
result: 模拟与四类空间转录组数据中，spaGSE实现更高检测功效并有效控制假阳性率，识别出协调空间分布的癌症与发育相关通路。
conclusion: 将空间信息纳入通路级推断能增强空间转录组学的生物学发现能力，spaGSE提供了有效且可扩展的解决方案。
---

## 摘要
空间分辨转录组学能够系统地表征跨组织切片的基因表达空间变异。同一生物通路内的空间变异基因通常表现出相似的空间表达模式，反映了共享的生物学功能和组织结构。然而，现有的基因集富集分析方法通常忽略这种空间依赖性，这可能降低检测空间组织化通路的能力，并限制通路水平发现的可解释性。为解决这一局限，我们提出spaGSE，一种用于空间通路富集分析的贝叶斯层次模型，该模型整合了来自空间表达分析的基因级汇总统计量与预定义的基因集注释。spaGSE通过高斯混合框架建模潜在的空间变异基因信号，并利用逻辑回归将空间变异与基因集成员关联起来。为支持稳健且可解释的推断，我们对富集系数施加spike-and-slab先验。通过模拟研究和四个公共SRT数据集的分析，我们证明spaGSE具有可扩展性，且在保持假阳性率控制的同时比现有方法更具统计功效。在实际数据应用中，spaGSE识别出在癌症和发育组织中具有协调空间组织的生物学相关通路，展示了将空间信息纳入空间转录组学通路水平推断的价值。

## Abstract
Spatially resolved transcriptomics enables the systematic characterization of spatial gene expression variation across tissue sections. Spatially variable genes within the same biological pathway often exhibit similar spatial expression patterns, reflecting shared biological functions and tissue organization. However, existing gene set enrichment analysis methods typically ignore this spatial dependence, which may reduce power to detect spatially organized pathways and limit the interpretability of pathway-level findings. To address this limitation, we propose spaGSE, a Bayesian hierarchical model for spatial pathway enrichment analysis that integrates genelevel summary statistics from spatial expression analysis with predefined gene set annotations. spaGSE models latent spatially variable gene signals through a Gaussian mixture framework and links spatial variation to gene set membership using logistic regression. To support robust and interpretable inference, we impose a spike-and-slab prior on the enrichment coefficient. Through simulation studies and analyses of four public SRT datasets, we show that spaGSE is scalable and achieves higher power while maintaining false positive rate control compared with existing approaches. In real-data applications, spaGSE identifies biologically relevant pathways with coordinated spatial organization across cancer and developmental tissues, demonstrating the value of incorporating spatial information into pathway-level inference for spatial transcriptomics.