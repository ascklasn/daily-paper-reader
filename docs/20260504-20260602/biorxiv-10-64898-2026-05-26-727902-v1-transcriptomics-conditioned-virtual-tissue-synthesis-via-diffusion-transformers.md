---
title: Transcriptomics-Conditioned Virtual Tissue Synthesis via Diffusion Transformers
title_zh: 通过扩散变换器实现转录组条件化的虚拟组织合成
authors: "Vlachas, P., Nonchev, K., Koelzer, V., Ratsch, G."
date: 2026-05-29
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.26.727902v1.full.pdf"
tags: ["query:spatialprot"]
score: 8.0
evidence: 空间转录组条件化的虚拟组织生成
tldr: 空间转录组学关联组织形态与基因表达，但缺乏从转录组生成组织图像的模型。本文提出STMDiT扩散变换器，融合形态嵌入和基因表达条件，通过双重无分类器引导和预测转录组伪标签训练，在黑色素瘤数据上显著提升图像质量和转录组保真度，并实现零样本迁移到外部分布队列。该方法支持虚拟组织合成，为计算病理学假设检验提供新工具。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有生成模型无法从转录组数据合成组织图像，限制了空间转录组学在虚拟组织模拟中的应用。
method: 基于PixCell扩散变换器，通过自适应层归一化和交叉注意力整合基因表达，采用双重无分类器引导训练，并用DeepSpots预测伪标签实现零样本迁移。
result: 在Visium队列中，FID从330.7降至252.9，AUC从0.229升至0.267；零样本迁移到TCGA SKCM时FID提升57点。
conclusion: "基因表达条件能生成形态不同的组织图像，首次实现从转录组到H&E的虚拟合成，助力计算病理学假设检验。"
---

## 摘要
空间转录组学将苏木精-伊红（H&E）组织形态与空间分辨基因表达（GE）相结合。然而，利用这种耦合从转录组图谱合成组织图像的生成模型仍然稀缺。我们提出了STMDiT（空间转录组学与形态扩散变换器），这是一种扩散变换器，能根据形态嵌入和转录组图谱联合条件，合成H&E组织病理学切片。基于PixCell（Yellapragada等人，2025），我们通过自适应层归一化和逐块交叉注意力，整合了来自冻结的CancerFoundation编码器（Theus等人，2024）的基因表达，并在双无分类器引导下进行独立模态丢弃训练。在10x TuPro Visium黑色素瘤队列中，GE条件化改善了图像质量（最佳FID从330.7降至252.9）和转录组保真度（最佳AUC从0.229升至0.267，达到真实切片上限的82%）。使用DeepSpots预测转录组伪标签（PTPL）进行训练，能零样本迁移至TCGA SKCM（一个分布外（OOD）的仅H&E黑色素瘤队列）：PTPL-XAttn-PMA-B达到FID=690.0，比无GE基线（747.1）改善了57个点，且模型内GE消融效应为ΔOOD=+309.5，从而能够超越原生空间转录组覆盖范围进行虚拟组织合成。我们的结果表明，基因表达条件化能产生形态上独特的组织图像，并支持计算病理学中假设检验的虚拟组织模拟。

## Abstract
Spatial transcriptomics couples hematoxylin and eosin (H&E) tissue morphology with spatially resolved gene expression (GE). However, generative models that exploit this coupling to synthesize tissue images from transcriptomic profiles remain scarce. We present STMDiT (Spatial Transcriptomics and Morphology Diffusion Transformer), a diffusion transformer that synthesizes H&E histopathology patches conditioned jointly on morphological embeddings and transcriptomic profiles. Building on PixCell (Yellapragada et al., 2025), we integrate gene expression from a frozen CancerFoundation encoder (Theus et al., 2024) through adaptive layer normalization and per-block cross-attention, and we train under dual classifier-free guidance with independent modality dropout. On the 10x TuPro Visium melanoma cohort, GE conditioning improves both image quality over the no-GE PixCell-B baseline (best FID = 252.9 vs 330.7) and transcriptomic fidelity (best AUC = 0.267 vs 0.229, reaching 82% of the real-tile ceiling). Training with DeepSpots predicted-transcriptomics pseudo-labels (PTPL) uniquely transfers zero-shot to TCGA SKCM, an out-of-distribution (OOD) H&E-only melanoma cohort: PTPL-XAttn-PMA-B reaches FID = 690.0, a 57-point improvement over the no-GE baseline (747.1), with a within-model GE-ablation effect of {Delta}OOD = +309.5, enabling virtual tissue synthesis beyond native spatial-transcriptomics coverage. Our results indicate that gene-expression conditioning produces morphologically distinct tissue images and supports virtual tissue simulation for hypothesis testing in computational pathology.