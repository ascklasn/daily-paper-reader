---
title: "TIDEST: post-imputation differential expression testing for spatial transcriptomics data"
title_zh: TIDEST：空间转录组数据插补后的差异表达检验
authors: "Roeder, K., Lei, J., Testa, L."
date: 2026-06-24
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.19.733432v1.full.pdf"
tags: ["query:spatialprot"]
score: 6.0
evidence: 空间转录组数据插补后的差异表达深度学习框架
tldr: 空间转录组学高分辨率平台只测量有限基因，插补重建后的差异表达分析因忽略预测不确定性和空间结构变异而不可靠。TIDEST利用测量基因信息校正系统误差并调整空间变异，在模拟中显著降低假阳性且保持统计功效。应用于小鼠脑、人胶质母细胞瘤和乳腺癌数据，恢复被传统分析遗漏的生物学差异信号。
source: biorxiv
selection_source: fresh_fetch
motivation: 空间转录组插补后的差异表达分析因预测不确定性及空间结构变异导致假阳性高、估计算法有偏，需校正误差的统计方法。
method: TIDEST通过构建基于测量基因的校正模型消除系统误差，并引入潜在空间变异协变量调整组织结构和细胞组成的影响。
result: 在仿真中误差控制优于现有方法，真实数据（小鼠脑、胶质母细胞瘤、乳腺癌）检测到传统分析遗漏的差异表达基因。
conclusion: TIDEST为插补空间转录组提供可靠的差异表达检验框架，避免失真推断，提升生物学发现能力。
---

## 摘要
空间转录组学能够原位研究组织结构，但许多高分辨率平台仅测量有限的基因面板，导致大部分转录组未被观测。尽管深度学习方法可以从匹配的单细胞参考中重建缺失基因，但下游差异表达（DE）分析仍不可靠，因为预测不确定性和空间结构化变异来源通常被忽略。这些因素可能偏倚效应估计并增加假阳性发现。我们提出TIDEST，一个用于空间转录组插补后DE检验的框架。TIDEST利用测量基因的信息校正重建表达中的系统误差，并调整潜在的时空变异（如组织结构或细胞类型组成），这些变异可能在生物学组之间产生虚假差异。在大量模拟中，TIDEST在保持效力的同时，比现有方法具有显著更好的误差控制。应用于小鼠大脑、人胶质母细胞瘤和人乳腺癌数据，TIDEST恢复了被常规分析遗漏或扭曲的生物学意义DE信号。TIDEST为重建空间转录组的DE分析提供了原则性框架。

## Abstract
Spatial transcriptomics enables the study of tissue organization in situ, but many high-resolution platforms measure only a limited gene panel, leaving much of the transcriptome unobserved. Although deep learning methods can reconstruct missing genes from matched single-cell references, downstream differential expression (DE) analysis remains unreliable because prediction uncertainty and spatially structured sources of variation are typically ignored. These factors can bias effect estimates and inflate false discoveries. We present TIDEST, a framework for DE testing after spatial transcriptomic imputation. TIDEST uses information from measured genes to correct systematic errors in reconstructed expression and adjusts for latent spatial variation, such as tissue architecture or cell-type composition, that can create spurious differences between biological groups. Across extensive simulations, TIDEST maintains substantially better error control than existing approaches while preserving power. Applications to mouse brain, human glioblastoma, and human breast cancer data recover biologically meaningful DE signals that are missed or distorted by conventional analyses. TIDEST provides a principled framework for DE analysis on reconstructed spatial transcriptomes.