---
title: BART-spatial unravels biologically significant transcriptional regulators from spatial omics data
authors: "Wang, J., Zhang, H., Wang, Z., Zang, C."
date: 2026-08-20
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.05.723027v2.full.pdf"
tags: ["query:spatialprot"]
score: 6.0
evidence: 从空间转录组数据解析转录调控因子的空间组学计算方法
tldr: 空间组学技术能保留细胞位置与微环境信息，但从中识别功能性转录调控因子仍受限于低表达和活性与mRNA水平不直接相关等问题。本文提出BART-spatial方法，从空间转录组测序数据中解析具有生物学意义的转录调控因子。该方法能够克服上述挑战，识别与发育、组织结构和疾病相关的关键调控因子。它为空间组学研究提供了重要的计算工具，并有望扩展到空间蛋白组学等数据类型。
source: biorxiv
selection_source: fresh_fetch
motivation: 从空间转录组数据解析转录调控因子的空间组学计算方法。
method: 方法与实现细节请参考摘要与正文。
result: 结果与对比结论请参考摘要与正文。
conclusion: 总体而言，该工作在所述任务上展示了有效性，并提供了可复用的思路或工具。
---

## Abstract
Transcriptional regulators (TRs) are crucial regulators of cell fate decisions by activating or repressing lineage-specific genes and integrating environmental signals with intrinsic networks. Identifying functional TRs is essential for understanding development, tissue organization, and disease. Emerging spatial transcriptomics and epigenomics technologies now provide near-single-cell resolution mapping of genomic features while preserving information of each cell's physical location and microenvironment which influence TR activity. Despite these advances, identifying active TRs in spatial data remains challenging due to low TR expression and the fact that TR activity often does not correlate directly with mRNA levels. Moreover, existing tools mainly designed for non-spatial single-cell data overlook spatial heterogeneity. To bridge this gap, we developed BART-spatial (Binding Analysis for Regulation of Transcription for spatial omics data), an innovative computational method to infer functional TRs from spatial omics data. BART-spatial integrates spatial variability and pseudotemporal information with publicly available TR binding profiles. Applied to multiple spatial datasets from diverse platforms, including 10x Visium, Visium HD, Atera, and spatial RNA-ATAC-seq, BART-spatial consistently outperforms existing methods, identifying state-specific TRs and revealing regulators undetectable by expression alone. Its compatibility with spatial epigenomics data further strengthens its utility and enables cross-validation. Overall, BART-spatial provides a powerful and robust tool for decoding spatially resolved gene regulatory programs.