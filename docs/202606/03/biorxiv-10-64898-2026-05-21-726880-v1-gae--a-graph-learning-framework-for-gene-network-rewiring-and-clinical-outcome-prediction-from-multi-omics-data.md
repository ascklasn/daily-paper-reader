---
title: "GAE-Δ: A Graph-Learning Framework for Gene Network Rewiring and Clinical Outcome Prediction from Multi-Omics Data"
title_zh: GAE-Δ：用于基因网络重连和多组学数据临床结局预测的图学习框架
authors: "Tang, Z., Chen, Z., Chen, M., Wang, Y., Ennis, S., Niranjan, M., Ewing, R."
date: 2026-05-26
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.21.726880v1.full.pdf"
tags: ["query:spatialprot"]
score: 6.0
evidence: 多组学图学习用于癌症基因网络
tldr: 癌症进展常伴随多组学网络的重构。本文提出图自编码器框架GAE-Δ，针对两种表型组构建各组特异的基因图，联合训练一个自编码器产生共享隐空间的嵌入，通过对比嵌入位移表征基因网络角色变化。该位移用于基因优先级排序、多组学晚期融合和分类。在五个TCGA癌种中，GAE-Δ预测性能优于MOFA+等方法，且筛选的共识基因显著富集已知癌症驱动基因，捕获了线性方法遗漏的生物信号。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有方法难以捕捉多组学数据中表型特异性基因网络角色的非线性变化。
method: GAE-Δ构建组特异基因图并联合训练图自编码器，通过对比嵌入向量位移表征基因网络重连。
result: 在5个TCGA癌种中，GAE-Δ的AUC在3个数据集显著优于MOFA+，其余持平；共识基因富集已知驱动基因（3/5癌种p<0.01，富集倍数11-17x）。
conclusion: GAE-Δ实现了更优的预测性能与生物学发现，凸显深度图网络在整合多组学数据中的优势。
---

## 摘要
癌症的进展和结局部分由遗传和/或环境扰动导致的分子网络变化驱动。这些网络变化表现在多个相互连接的网络层次上，包括体细胞突变的积累、蛋白质-蛋白质相互作用的改变和基因表达的失调。本文描述了一种基于图自编码器的框架（Graph Autoencoder-Delta，GAE-Δ），用于在多组学数据中表征表型特异的基因角色转变。给定按两种对比表型分层的样本和一个先验基因相互作用网络，GAE-Δ为每个组学模态构建组特异基因图，并为每个模态训练一个单独的图自编码器，该自编码器同时在两个组图上联合训练，使得两个组条件嵌入共享一个共同的潜在空间。对比这些嵌入定义了每个基因的多组学嵌入偏移表示，反映了其网络角色如何在表型背景下重组。这些基因级别的偏移随后用于无监督基因优先级排序、多组学后期融合和样本级别分类。应用于五个以生存为终点的TCGA癌症类型，与经典的基于网络的方法和多组学矩阵分解方法（MOFA+、iNMF）相比，GAE-Δ实现了有竞争力或更优的预测性能，在五个队列中的三个队列中AUC显著优于MOFA+，其余两个队列统计上持平。除了预测性能外，共识偏移基因在五个队列中的三个队列中显著富集了已知的癌症驱动基因（超几何检验p<0.01；富集倍数11-17倍），而矩阵分解基线在五个队列中没有一个达到p<0.05（最佳每癌p=0.06），表明GAE-Δ捕获了线性因子方法遗漏的生物信号。总之，GAE-Δ方法通过基于深度网络的疾病相关多组学数据整合，既改进了结局分类，也促进了生物学和机制发现。

## Abstract
Cancer progression and outcomes are driven in part by changes to molecular networks that result from genetic and/or environmental perturbations. These network changes manifest across multiple interconnected network layers and include accumulation of somatic mutations, altered proteinprotein interactions and dysregulated gene-expression. Here we describe a graph autoencoder-based framework (Graph Autoencoder-Delta (GAE-{Delta})), for characterizing phenotype-specific gene role shifts across multi-omics data. Given samples stratified into two contrasting phenotypic groups and a prior gene interaction network, GAE-{Delta} constructs group-specific gene graphs for each omics modality and trains, for each modality, a single graph autoencoder jointly on both group graphs, so that the two group-conditional embeddings share a common latent space. Contrasting these embeddings defines a multi-omics embedding-shift representation for each gene that reflects how its network role reorganizes across phenotypic contexts. These gene-level shifts are subsequently used for unsupervised gene prioritization, multi-omics late fusion and sample-level classification. Applied to five TCGA cancer types with a survival endpoint, GAE-{Delta} achieves competitive or superior predictive performance compared with classical network-based methods and multi-omics matrix-factorisation methods (MOFA+, iNMF), with statistically significant AUC gains over MOFA+ in three of five cohorts and statistical ties on the remaining two. Beyond predictive performance, the consensus shift genes are significantly enriched for known cancer drivers in three of five cohorts (hypergeometric p < 0.01; 11-17x fold-enrichment), whereas matrix-factorisation baselines reach p < 0.05 in zero of five cohorts (best per-cancer p = 0.06), indicating that GAE-{Delta} captures biological signal that linear factor methods miss. In summary, the GAE-{Delta} approach provides for both improved outcome classification as well as for biological and mechanistic discovery through deep network-based integration of disease-associated multi-omics data.