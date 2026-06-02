---
title: "CLEAR-HPV: Interpretable Concept Discovery for HPV-Associated Morphology in Whole-Slide Histology"
title_zh: CLEAR-HPV：全切片组织学中HPV相关形态的可解释概念发现
authors: "Qin, W., Liu-Swetz, Y., Tan, S., Wang, H."
date: 2026-05-15
pdf: "https://www.biorxiv.org/content/10.64898/2026.02.04.703870v3.full.pdf"
tags: ["query:pm"]
score: 8.0
evidence: 全切片组织学概念发现用于HPV状态分析
tldr: 针对HPV相关全切片病理学中注意力MIL模型缺乏形态学可解释性的问题，提出CLEAR-HPV框架，在注意力加权潜在空间中自动发现角化、基底样等形态学概念，无需概念标签。该方法将高维特征降至10个可解释概念，保留预测信息，并在多个数据集上验证了概念结构的一致性。CLEAR-HPV为基于注意力的MIL模型提供了通用、紧凑的概念级可解释性。
source: biorxiv
selection_source: fresh_fetch
motivation: 当前注意力MIL模型在HPV相关病理切片预测中缺乏形态学概念层面的可解释性。
method: 利用注意力加权潜在空间，自动发现形态学概念并生成紧凑的概念分数向量。
result: 将1536维特征降至10个可解释概念，保持预测性能，在三个数据集上概念结构一致。
conclusion: CLEAR-HPV为注意力MIL模型提供了通用、骨干无关的概念级可解释框架。
---

## 摘要
人乳头瘤病毒（HPV）状态是头颈癌和宫颈癌预后和治疗反应的关键决定因素。尽管基于注意力的多实例学习（MIL）在HPV相关全切片组织病理学中实现了强的切片级预测，但其形态学可解释性有限。为了解决这一限制，我们引入了CLEAR-HPV（面向HPV的概念级可解释注意力引导表示），这是一个利用注意力重构MIL潜在空间以在训练期间无需概念标签即可实现概念发现的框架。在注意力加权的潜在空间中运行，CLEAR-HPV自动发现角化型、基底细胞样型和间质形态概念，生成空间概念图，并使用紧凑的概念分数向量表示每个切片。CLEAR-HPV的概念分数向量保留了原始MIL嵌入的预测信息，同时将高维特征空间（例如1536维）减少到仅10个可解释概念。CLEAR-HPV在TCGA-HNSCC、TCGA-CESC和CPTAC-HNSCC中展示了一致的概念结构，通过一个通用的、与骨干网络无关的框架为基于注意力的MIL全切片组织病理学模型提供了紧凑的概念级可解释性。所有原始代码、预处理脚本和训练好的模型检查点均可从GitHub获取（https://github.com/Wang-ML-Lab/CLEAR-HPV）。

## Abstract
Human papillomavirus (HPV) status is a critical determinant of prognosis and treatment response in head and neck and cervical cancers. Although attention-based multiple instance learning (MIL) achieves strong slide-level prediction for HPV-related whole-slide histopathology, it provides limited morphologic interpretability. To address this limitation, we introduce Concept-Level Explainable Attention-guided Representation for HPV (CLEAR-HPV), a framework that restructures the MIL latent space using attention to enable concept discovery without requiring concept labels during training. Operating in an attention-weighted latent space, CLEAR-HPV automatically discovers keratinizing, basaloid, and stromal morphologic concepts, generates spatial concept maps, and represents each slide using a compact concept-fraction vector. CLEAR-HPVs concept-fraction vectors preserve the predictive information of the original MIL embeddings while reducing the high-dimensional feature space (e.g., 1536 dimensions) to only 10 interpretable concepts. CLEAR-HPV demonstrates consistent concept structure across TCGA-HNSCC, TCGA-CESC, and CPTAC-HNSCC, providing compact, concept-level interpretability through a general, backbone-agnostic framework for attention-based MIL models of whole-slide histopathology. All original code, preprocessing scripts, and trained model checkpoints are available on GitHub (https://github.com/Wang-ML-Lab/CLEAR-HPV))