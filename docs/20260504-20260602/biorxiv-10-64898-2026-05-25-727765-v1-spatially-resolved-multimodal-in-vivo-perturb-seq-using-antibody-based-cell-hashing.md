---
title: "Spatially resolved, multimodal in vivo Perturb-seq using antibody-based cell hashing"
title_zh: 基于抗体细胞哈希的空间解析、多模态体内Perturb-seq
authors: "Nevue, A. A., Hartoularos, G. C., De Valle, C., Ramachandran, K., Barron, J. J., Lee, H., Calleja Cervantes, M. E., Bowness, J., Velten, L., Ricci-Tam, C., Dobin, A., Levy, M., Ye, C. J., Averbukh, I., Lara-Astiaso, D."
date: 2026-05-26
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.25.727765v1.full.pdf"
tags: ["query:spatialprot"]
score: 8.0
evidence: 整合空间转录组学与表面蛋白质组学
tldr: 大规模体内扰动筛查虽揭示了基因-细胞内在功能关系，但基因如何塑造组织空间结构仍未知。为填补这一空白，我们开发了基于抗体细胞哈希的PerturbSpace，将CRISPR扰动与空间哈希单细胞多组学整合，首次实现体内高通量空间分辨Perturb-seq。我们将PerturbSpace应用于再生脾脏，成功绘制40个转录调控因子对菌落大小和谱系组成的影响；在肝脏中，解析了免疫细胞分泌细胞因子对邻近细胞的非细胞自主效应。PerturbSpace是一种可扩展、低成本的空间扰动分析方法，兼容表面蛋白和谱系条形码等多模态技术，为组织尺度的全细胞空间图谱研究开辟新途径。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有体内扰动筛选主要关注细胞内在功能，缺乏空间维度，难以解析基因如何调控组织架构和微环境互作。
method: PerturbSpace通过抗体细胞哈希实现空间分辨，融合CRISPR扰动与单细胞多组学，支持表面蛋白和谱系条形码等多模态。
result: 在脾脏再生造血中，鉴定40个转录调控因子影响菌落大小和谱系；在肝脏中，解析免疫细胞对邻近细胞的非细胞自主效应。
conclusion: PerturbSpace实现高通量空间Perturb-seq，兼容多模态，为解析组织架构的遗传决定因素提供可扩展工具。
---

## 摘要
大规模扰动筛选已开始绘制细胞内在基因-功能关系图，但基因如何塑造组织架构仍很大程度上未被探索。为填补这一空白，我们开发了PerturbSpace，一种将CRISPR扰动与空间哈希单细胞多组学整合的新方法。该方法首次实现了体内复杂组织架构上的高通量、空间解析Perturb-seq分析。值得注意的是，PerturbSpace能够在器官尺度上进行空间转录组范围的扰动读数，并可无缝整合正交模态。我们将PerturbSpace与表面蛋白质组学和表达谱系追踪条形码结合，展示了多模态兼容性。我们利用PerturbSpace研究组织架构的遗传决定因素。首先，我们绘制了40个转录调控因子在再生性造血过程中如何决定脾脏菌落大小和谱系组成。其次，通过剖析分泌细胞因子的免疫细胞对其邻近细胞的外在效应，我们表征了肝脏中的免疫-微环境相互作用。总的来说，我们的工作确立了PerturbSpace作为一种可扩展且经济高效的方法，用于全细胞转录组范围的空间分析，同时保持与该领域已大规模采用的多组学工作流程的兼容性。

## Abstract
Large-scale perturbation screens have begun to map cell intrinsic gene-function relationships, yet how genes shape tissue architecture remains largely unexplored. To address this gap, we developed PerturbSpace, a novel approach that integrates CRISPR perturbations with spatially hashed single-cell multiomics. This approach enables the first high-throughput, spatially resolved Perturb-seq analysis across complex tissue architecture in vivo. Notably, PerturbSpace enables spatial transcriptome-wide perturbation readouts at organ scale and can be seamlessly integrated with orthogonal modalities. We combine PerturbSpace with surface proteomics and expressed lineage tracing barcodes to demonstrate multimodal compatibility. We use PerturbSpace to study the genetic determinants of tissue architecture. First, we map how 40 transcriptional regulators determine the size and lineage composition of colonies in the spleen during regenerative hematopoiesis. Second, we characterize immune-niche interactions in the liver by dissecting the extrinsic effects mediated by cytokine-secreting immune cells on their neighboring cells. Collectively, our work establishes PerturbSpace as a scalable and cost-effective approach for transcriptome-wide spatial profiling of whole cells while remaining compatible with the single-cell multiomics workflows that the field has already adopted at scale.