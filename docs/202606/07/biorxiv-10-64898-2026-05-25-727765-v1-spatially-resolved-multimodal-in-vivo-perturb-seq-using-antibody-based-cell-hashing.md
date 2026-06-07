---
title: "Spatially resolved, multimodal in vivo Perturb-seq using antibody-based cell hashing"
title_zh: 基于抗体细胞哈希的空间分辨多模态体内Perturb-seq技术
authors: "Nevue, A. A., Hartoularos, G. C., De Valle, C., Ramachandran, K., Barron, J. J., Lee, H., Calleja Cervantes, M. E., Bowness, J., Velten, L., Ricci-Tam, C., Dobin, A., Levy, M., Ye, C. J., Averbukh, I., Lara-Astiaso, D."
date: 2026-05-26
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.25.727765v1.full.pdf"
tags: ["query:spatialprot"]
score: 8.0
evidence: 空间分辨Perturb-seq整合表面蛋白质组和转录组
tldr: 大规模扰动筛选缺乏空间分辨率，难以解析基因如何塑造组织架构。本文提出PerturbSpace，通过抗体细胞哈希整合CRISPR扰动与空间单细胞多组学，在体内实现高吞吐量空间分辨Perturb-seq。在脾脏再生造血中，成功绘制40个转录调节因子对集落大小和谱系组成的影响；在肝脏中，表征了免疫细胞分泌细胞因子对邻近细胞的外源效应。PerturbSpace是一种可扩展、经济的全细胞空间转录组分析方法，兼容现有单细胞多组学流程。
source: biorxiv
selection_source: carryover_cache
motivation: 现有扰动筛选缺乏空间分辨率，无法研究基因如何影响组织架构。
method: 将CRISPR扰动与基于抗体的细胞哈希结合，实现空间解析的单细胞多组学Perturb-seq。
result: 在脾脏再生造血中绘制40个转录调节因子的空间功能，在肝脏中揭示免疫细胞对邻近细胞的外源效应。
conclusion: 建立可扩展经济的空间扰动筛选方法，兼容多模态单细胞分析。
---

## 摘要
大规模扰动筛选已开始揭示细胞内在的基因-功能关系，但基因如何塑造组织结构仍鲜有探索。为弥补这一空白，我们开发了PerturbSpace——一种将CRISPR扰动与空间哈希单细胞多组学相结合的新方法。该方法首次实现了跨复杂组织结构的体内高通量空间分辨Perturb-seq分析。值得注意的是，PerturbSpace能够在器官尺度上实现空间转录组范围的扰动读取，并可无缝整合正交模态。我们将PerturbSpace与表面蛋白质组学和表达的谱系追踪条形码结合，展示了其多模态兼容性。我们利用PerturbSpace研究组织结构的遗传决定因素。首先，我们绘制了40个转录调控因子在再生造血过程中如何决定脾脏集落大小和谱系组成。其次，通过解析分泌细胞因子的免疫细胞对邻近细胞的外源性效应，我们表征了肝脏中的免疫微环境互作。总之，我们的工作将PerturbSpace确立为一种可扩展且经济高效的方法，用于全细胞的转录组范围空间分析，同时保持与该领域已大规模采用的单细胞多组学工作流程的兼容性。

## Abstract
Large-scale perturbation screens have begun to map cell intrinsic gene-function relationships, yet how genes shape tissue architecture remains largely unexplored. To address this gap, we developed PerturbSpace, a novel approach that integrates CRISPR perturbations with spatially hashed single-cell multiomics. This approach enables the first high-throughput, spatially resolved Perturb-seq analysis across complex tissue architecture in vivo. Notably, PerturbSpace enables spatial transcriptome-wide perturbation readouts at organ scale and can be seamlessly integrated with orthogonal modalities. We combine PerturbSpace with surface proteomics and expressed lineage tracing barcodes to demonstrate multimodal compatibility. We use PerturbSpace to study the genetic determinants of tissue architecture. First, we map how 40 transcriptional regulators determine the size and lineage composition of colonies in the spleen during regenerative hematopoiesis. Second, we characterize immune-niche interactions in the liver by dissecting the extrinsic effects mediated by cytokine-secreting immune cells on their neighboring cells. Collectively, our work establishes PerturbSpace as a scalable and cost-effective approach for transcriptome-wide spatial profiling of whole cells while remaining compatible with the single-cell multiomics workflows that the field has already adopted at scale.