---
title: Deciphering shared and divergent tissue architectures from cross-species spatial transcriptomics
title_zh: 从跨物种空间转录组学中解读共享与差异的组织结构
authors: "Zhang, B., Zhou, X., Zhang, S."
date: 2026-06-18
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.16.732760v1.full.pdf"
tags: ["query:spatialprot"]
score: 6.0
evidence: 空间转录组整合方法可迁移至空间蛋白组学
tldr: 跨物种空间转录组学整合因分子与解剖差异而极具挑战。本文提出STACAME框架，采用图注意力自编码器显式建模直系同源与物种特异性基因，实现空间感知的切片对齐与域识别。在人类、猕猴、狨猴、小鼠、斑马鱼的海马、皮层、胚胎、乳腺、肝脏及小脑等组织中验证，支持跨物种空间域对齐、共享与差异可变基因检测、发育比较及3D整合。该框架为跨物种空间转录组研究提供统一计算平台，促进模式生物向人类转化。
source: biorxiv
selection_source: fresh_fetch
motivation: 跨物种空间转录组学整合对比较与转化研究至关重要，但分子差异和解剖差异使得对齐与比较极为困难。
method: 基于图注意力自编码器，显式建模直系同源与物种特异性基因，实现空间感知的切片对齐及同源/物种特异性域识别。
result: 在多种组织（海马、皮层、胚胎、乳腺、肝、小脑）和物种（人、猴、小鼠、斑马鱼）中验证，支持域对齐、差异基因检测、发育对齐及3D整合。
conclusion: 为跨物种空间转录组学提供统一计算平台，有效促进模式生物研究成果向人类的转化。
---

## 摘要
跨物种空间转录组学数据的整合对于跨物种和转化研究至关重要，但由于生物体之间的分子差异和解剖学差异，这仍然具有挑战性。我们提出了STACAME，一个基于图注意力自编码器的框架，通过显式建模直系同源基因和物种特异性基因，从跨物种空间转录组数据中解读共享与差异的组织结构。STACAME以空间感知方式对齐空间转录组切片，识别同源和物种特异性结构域，并支持一系列下游比较分析。我们通过整合来自多种组织（包括海马体、等皮层、胚胎、乳腺、肝脏和小脑）以及多个物种（如人类、猕猴、狨猴、小鼠和斑马鱼）的空间转录组数据集，展示了其实用性。STACAME支持跨物种空间结构域对齐、共享和差异空间可变基因的检测、发育对齐与比较，以及组织结构的3D整合。这种灵活的方法促进了从模式生物到人类的发现转化，为跨物种空间转录组学提供了一个统一的计算平台。

## Abstract
The integration of spatial transcriptomics (ST) data across species is essential for cross-species and translational studies, but remains challenging due to molecular divergence and anatomical differences between organisms. We present STACAME, a graph attention autoencoder-based framework to decipher shared and divergent tissue architectures from cross-species ST data by explicitly modeling both orthologous and species-specific genes. STACAME aligns ST slices in a spatially aware manner, identifies homologous and species-specific domains, and enables a suite of downstream comparative analyses. We demonstrate its utility by integrating ST datasets from diverse tissues, including hippocampus, isocortex, embryo, breast, liver, and cerebellum, across multiple species such as human, macaque, marmoset, mouse, and zebrafish. STACAME supports cross-species spatial domain alignment, the detection of shared and divergent spatially variable genes, development alignment and comparison, and the 3D integration of tissue architecture. This flexible approach facilitates the translation of findings from model organisms to humans, providing a unified computational platform for cross-species spatial transcriptomics.