---
title: "HESTIA: Scalable Multimodal Integration of Histology and High-Resolution Spatial Transcriptomics for Robust Spatial Domain Identification"
title_zh: HESTIA：组织学与高分辨率空间转录组学的可扩展多模态整合，用于稳健的空间域识别
authors: "Zhong, Z., Zhu, X., Guo, J., Liao, S., Chen, A."
date: 2026-05-18
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.14.723098v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 组织学与空间转录组多模态整合用于空间域识别
tldr: 空间组学向亚细胞分辨率发展带来数据规模大和转录组稀疏性挑战，现有分析方法难以处理。HESTIA算法通过避免内存密集型计算实现了大规模高分辨率空间组数据的高效多模态整合，在聚类准确性和空间连续性上优于现有方法。该方法成功应用于肺癌和结直肠癌样本，精确描绘了临床相关的瘤内异质性和免疫微环境。HESTIA为利用全切片级病理图像与高分辨率空间转录组数据识别空间域提供了可扩展的解决方案。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有多模态分析方法难以处理亚细胞分辨率空间组学产生的大规模数据和严重稀疏性。
method: HESTIA通过规避内存密集型计算，高效整合组织学图像和高分辨率空间转录组数据。
result: 在聚类准确性和空间连续性上优于当前方法，准确划分精细结构边界，成功解析临床相关瘤内异质性。
conclusion: HESTIA为大规模高分辨率空间组数据提供了稳健可扩展的多模态整合框架。
---

## 摘要
空间组学通过提供关于原生组织微环境如何调控细胞功能和疾病机制的宝贵见解，彻底改变了分子生物学。准确捕捉这种结构复杂性并解码潜在的生物学过程，需要有效整合来自多种模态的数据。然而，过渡到亚细胞分辨率带来了巨大的数据规模和严重的转录组稀疏性，这对当前的分析框架构成了挑战。为此，我们提出了HESTIA（组织学增强的可扩展交叉分辨率整合用于空间转录组学），这是一种高效的多模态算法，旨在识别大规模、高分辨率空间组学数据中的空间域。通过规避内存密集型计算，HESTIA轻松处理现有算法因内存限制而无法处理的大规模数据集。HESTIA在聚类准确性和空间连续性方面优于当前的多模态方法，能够精确描绘精细的结构边界。此外，将HESTIA应用于大规模病理样本，成功解析了临床相关的肿瘤内异质性，并绘制了肺癌和结直肠癌中不同的免疫微环境图谱。

## Abstract
Spatial omics has revolutionized molecular biology by providing invaluable insights into how native tissue microenvironments regulate cellular functions and disease mechanisms. Accurately capturing this structural complexity and decoding the underlying biological processes requires effectively integrating data from multiple modalities. However, transitioning to subcellular resolutions introduces massive data scales and severe transcriptomic sparsity, which challenge current analytical frameworks. To address this, we present HESTIA (Histology-Enhanced Scalable cross-Resolution inTegration for spatial trAnscriptomics), a highly efficient multimodal algorithm designed for identifying spatial domains in large-scale, high-resolution spatial omics data. By circumventing memory-intensive computations, HESTIA effortlessly processes massive datasets that existing algorithms fail due to memory constraints. HESTIA outperforms current multimodal methods in clustering accuracy and spatial continuity, accurately delineating fine structural boundaries. Furthermore, applying HESTIA to large-scale pathological samples successfully dissects clinically relevant intratumoral heterogeneity and maps distinct immune microenvironments in lung and colorectal cancers.