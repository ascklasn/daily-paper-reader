---
title: Generalisable tissue-wide molecular reconstruction from histology
title_zh: 基于组织学实现可推广的全组织分子重建
authors: "Zhang, A., Yu, L., Bian, B., Cao, Y., Ye, S., Han, E., Robertson, H., Dong, Y., Mao, Y., Liu, B., Patrick, E., Kim, J., Yang, J. Y. H."
date: 2026-06-12
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.09.731252v1.full.pdf"
tags: ["query:spatialprot"]
score: 7.0
evidence: "从H&E组织学重建空间分子状态，应对稀疏空间分析"
tldr: "空间转录组学技术难以大规模应用，现有H&E预测基因表达方法受限于稀疏测量和异质性数据集。本文提出GHIST+框架，整合细胞形态、局部组织上下文与共享组织表示，从稀疏组织微阵列数据重建全组织分子图谱。在多种癌症和GTEx乳腺组织中，GHIST+保持空间结构和细胞类型组织，并捕获年龄相关状态，实现可扩展的分子重建。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有方法无法从稀疏、异质性的空间分子测量实现组织wide分子重建。
method: GHIST+整合细胞形态、局部组织上下文和共享表示，将稀疏分子测量扩展为全组织分子图谱。
result: 在多种癌症和GTEx乳腺组织中，成功重建组织wide分子组织，保持空间结构和细胞类型。
conclusion: 提供从稀疏空间实验进行大规模分子重建的可扩展框架。
---

## 摘要
空间转录组学技术可测量完整组织内的基因表达，但在大组织切片和患者队列中仍难以扩展。因此，许多研究依赖于组织微阵列（TMAs）或稀疏空间分析设计，仅对有限组织区域进行分子测量，且通常使用异质性基因面板生成。现有的H&E到空间基因表达预测方法仍面临稀疏分子测量、部分重叠基因面板以及跨异质性空间数据集的全组织重建等挑战。本文提出GHIST+框架，用于从H&E组织学重建单细胞分子状态的全组织图谱。GHIST+整合细胞形态、局部组织背景和共享组织表征，将稀疏分子测量扩展到跨异质性空间数据集的全组织分子图谱。在多种癌症类型和GTEx乳腺组织中，GHIST+从稀疏的TMA衍生测量中重建出具有生物学意义的全组织分子组织，同时保留癌症和非癌症环境中的空间组织结构、细胞类型组织及年龄相关组织状态。GHIST+建立了一个可扩展的框架，将稀疏空间分析实验转化为全组织分子图谱，从而在异质性空间转录组学背景下，从常规组织学实现队列规模的分子重建。

## Abstract
Spatial transcriptomics technologies measure gene expression within intact tissues but remain difficult to scale across large tissue sections and patient cohorts. Consequently, many studies rely on tissue microarrays (TMAs) or sparse spatial profiling designs, where molecular measurements are available for only limited tissue regions and are often generated using heterogeneous gene panels. Existing H&E to spatial gene expression prediction methods remain challenged by sparse molecular measurements, partially overlapping gene panels and tissue-wide reconstruction across heterogeneous spatial datasets. Here, we present GHIST+, a framework for tissue-wide reconstruction of single-cell molecular states from H&E histology. GHIST+ integrates cellular morphology, local tissue context and shared tissue representations to extend sparse molecular measurements into tissue-wide molecular maps across heterogeneous spatial datasets. Across multiple cancer types and GTEx breast tissues, GHIST+ reconstructs biologically meaningful tissue-wide molecular organisation from sparse TMA-derived measurements while preserving spatial tissue structure, cell-type organisation and age-associated tissue states across cancer and non-cancer settings. GHIST+ establishes a scalable framework for transforming sparse spatial profiling experiments into tissue-wide molecular maps, enabling cohort-scale molecular reconstruction from routine histology under heterogeneous spatial transcriptomic settings.