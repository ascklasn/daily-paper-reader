---
title: Spatial Gene Set Enrichment Analysis with Applications to Spatially Resolved Transcriptomic Data
title_zh: 空间基因集富集分析及其在空间分辨转录组数据中的应用
authors: "Xie, Z., Guo, Y., Li, Q., Ma, Y."
date: 2026-06-04
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.01.729158v1.full.pdf"
tags: ["query:spatialprot"]
score: 8.0
evidence: 空间基因集富集分析方法，适用于空间转录组数据
tldr: 空间转录组学中，现有基因集富集分析忽略基因空间依赖性，降低了检测空间组织通路的功效。为此，提出spaGSE贝叶斯分层模型，通过高斯混合框架建模空间可变基因信号，结合逻辑回归关联基因集，并引入spike-and-slab先验进行稳健推断。模拟和四个公共数据集表明，spaGSE在控制假阳性率的同时具有更高统计功效。实际应用中，spaGSE识别出具有协调空间组织的生物学通路，证明了整合空间信息进行通路级推断的价值。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有基因集富集分析忽略空间依赖性，降低检测空间组织通路的功效和可解释性。
method: 提出spaGSE贝叶斯分层模型，结合高斯混合与逻辑回归，施加spike-and-slab先验。
result: 模拟和四个SRT数据集显示spaGSE比现有方法更高效，且控制假阳性率。
conclusion: spaGSE识别具有协调空间组织的通路，证明整合空间信息在通路推断中的价值。
---

## 摘要
空间分辨转录组学能够系统地表征组织切片上的空间基因表达变化。同一生物通路中的空间可变基因通常表现出相似的空间表达模式，反映了它们共享的生物学功能和组织结构。然而，现有的基因集富集分析方法通常忽略这种空间依赖性，这可能降低检测空间组织化通路的能力，并限制通路层面结果的可解释性。为解决这一局限，我们提出了spaGSE，一种用于空间通路富集分析的贝叶斯分层模型，该模型整合了来自空间表达分析的基因级汇总统计量与预定义的基因集注释。spaGSE通过高斯混合框架对潜在的空间可变基因信号进行建模，并利用逻辑回归将空间变异与基因集成员关系联系起来。为了支持稳健且可解释的推断，我们对富集系数施加了尖峰-平板先验。通过模拟研究和四个公开SRT数据集的分析，我们证明了spaGSE具有可扩展性，并且在保持假阳性率控制的同时，比现有方法具有更高的统计功效。在实际数据应用中，spaGSE识别出在癌症和发育组织中具有协调空间组织的生物学相关通路，展示了将空间信息纳入空间转录组学通路层面推断的价值。

## Abstract
Spatially resolved transcriptomics enables the systematic characterization of spatial gene expression variation across tissue sections. Spatially variable genes within the same biological pathway often exhibit similar spatial expression patterns, reflecting shared biological functions and tissue organization. However, existing gene set enrichment analysis methods typically ignore this spatial dependence, which may reduce power to detect spatially organized pathways and limit the interpretability of pathway-level findings. To address this limitation, we propose spaGSE, a Bayesian hierarchical model for spatial pathway enrichment analysis that integrates genelevel summary statistics from spatial expression analysis with predefined gene set annotations. spaGSE models latent spatially variable gene signals through a Gaussian mixture framework and links spatial variation to gene set membership using logistic regression. To support robust and interpretable inference, we impose a spike-and-slab prior on the enrichment coefficient. Through simulation studies and analyses of four public SRT datasets, we show that spaGSE is scalable and achieves higher power while maintaining false positive rate control compared with existing approaches. In real-data applications, spaGSE identifies biologically relevant pathways with coordinated spatial organization across cancer and developmental tissues, demonstrating the value of incorporating spatial information into pathway-level inference for spatial transcriptomics.