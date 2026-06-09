---
title: "STITCH: Spatial Transcriptomics Imputation via Flow Matching with Internal Learning"
title_zh: STITCH：基于流匹配与内部学习的空间转录组填补
authors: "Wang, S., Wang, X., Peng, Q., Li, T."
date: 2026-06-06
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.03.729557v1.full.pdf"
tags: ["query:spatialprot"]
score: 6.0
evidence: 空间转录组插补，与空间蛋白组数据分析相关
tldr: 空间转录组数据常因切片伪影、组织损伤和测序成本限制存在间隙和缺失区域。STITCH提出一种可扩展的生成式框架，通过解耦架构分离空间形态恢复与转录组生成：先利用空间感知图自编码器压缩高维转录组，再对3D跨切片间隙采用最优传输条件流匹配，对2D切片内损伤通过内部学习修复，最后在潜空间建立点态条件流匹配模型生成转录组。该方法实现线性复杂度，单GPU上5小时内重建超1100万细胞，并在多平台（单细胞和斑点级）上保持转录组身份、空间拓扑和解剖连续性。
source: biorxiv
selection_source: fresh_fetch
motivation: 解决空间转录组数据中空间间隙和缺失区域的重建问题，避免依赖外部参考图谱或组织学图像先验。
method: 采用解耦架构，先通过空间感知图自编码器压缩转录组为低维潜变量，再对3D间隙用最优传输条件流匹配、2D损伤用内部学习修复空间，最后在潜空间用点态条件流匹配生成转录组。
result: 达到线性计算复杂度，单GPU上5小时内重建超1100万细胞，跨平台验证一致保持转录组身份、空间拓扑和解剖连续性。
conclusion: 提供了可扩展、平台兼容的计算框架，用于高分辨率连续空间转录组图谱重建。
---

## 摘要
空间转录组数据集经常由于切片伪影、组织损伤以及测序成本高导致组织覆盖受限而出现空间间隙和缺失区域。我们提出了STITCH，一个用于多维虚拟空间转录组重建的可扩展且鲁棒的生成框架。STITCH直接从单个组织样本中建模内在的空间-转录组模式，无需外部参考图谱或匹配的组织学图像先验即可进行重建。该框架采用解耦架构，将空间形态恢复与转录组生成分开。STITCH首先通过空间感知图自编码器将高维转录组图谱压缩为低维潜在表示。对于三维跨切片间隙，STITCH使用最优传输条件流匹配进行空间重建，而二维切片内损伤则通过内部学习策略修复。为了生成相应的转录组图谱，STITCH进一步在潜在空间中建立逐点条件流匹配模型。该模块实现线性计算复杂度，能够在单个商用GPU上5小时内重建超过1100万个细胞的连续三维图谱。跨不同空间转录组平台（包括单细胞和点级技术）的广泛评估表明，STITCH始终保留转录组身份、空间拓扑和解剖连续性。总体而言，STITCH为重建高分辨率连续空间转录组图谱提供了一个可扩展且平台兼容的计算框架。

## Abstract
Spatial transcriptomics datasets frequently suffer from spatial gaps and missing regions due to sectioning artifacts, tissue damage, and the high cost of sequencing that limits tissue coverage. We present STITCH, a scalable and robust generative framework for multidimensional virtual spatial transcriptomics reconstruction. STITCH models intrinsic spatial-transcriptomic patterns directly from individual tissue samples, enabling reconstruction without requiring external reference atlases or matched histological image priors. The framework adopts a decoupled architecture that separates spatial morphology restoration from transcriptomic generation. STITCH first compresses high-dimensional transcriptomic profiles into a low-dimensional latent representation through a spatial-aware graph autoencoder. For 3D cross-slice gaps, STITCH employs optimal transport-conditioned flow matching for spatial reconstruction, whereas 2D in-slice damage is repaired through an internal learning strategy. To generate the corresponding transcriptomic profiles, STITCH further establishes a point-wise conditional flow matching model in the latent space. This module achieves linear computational complexity, enabling continuous 3D atlas reconstruction of over 11 million cells within 5 hours on a single commodity GPU. Extensive evaluations across diverse spatial transcriptomics platforms, spanning both single-cell and spot-level technologies, demonstrate that STITCH consistently preserves transcriptomic identities, spatial topologies, and anatomical continuity. Overall, STITCH provides a scalable and platform-compatible computational framework for reconstructing high-resolution continuous spatial transcriptomic atlases.