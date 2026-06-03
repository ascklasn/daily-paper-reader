---
title: "MORPHE: Bridging Image Generation and Spatial Omics for Tissue Synthesis"
title_zh: MORPHE：连接图像生成与空间组学实现组织合成
authors: "Feng, Y., Robers, Z., Rasheed, L., Miao, Y., Wen, S., Lee, K., Sohigian, J., Brbic, M., Hickey, J. W."
date: 2026-05-28
pdf: "https://www.biorxiv.org/content/10.64898/2026.03.03.709377v2.full.pdf"
tags: ["query:spatialprot"]
score: 8.0
evidence: 从空间组学数据合成组织结构的AI框架
tldr: 空间组学技术受限于成本、不完全覆盖、2D成像和实验伪影。MORPHE通过图信息概率嵌入将细胞身份与空间关系映射为类RGB潜空间，利用扩散模型以单细胞精度生成组织结构。在肠和脑的百万级细胞数据上实现空间外推、受损修复及跨组织3D插补。该方法为单细胞空间组学提供高效计算解决方案。
source: biorxiv
selection_source: fresh_fetch
motivation: 空间组学成本高、覆盖不全、2D限制和伪影问题急需计算重建方法。
method: 利用图信息概率嵌入将细胞映射到RGB潜空间，结合扩散模型实现以细胞为单位的组织生成。
result: 在肠和脑的百万级细胞数据上实现空间外推、修复及跨组织3D插补。
conclusion: 提出新型组织生成算法，有效解决单细胞空间组学数据集局限。
---

## 摘要
空间分辨组学技术以单细胞分辨率揭示组织结构，但仍受限于分析成本、空间覆盖不完全、仅二维成像以及实验伪影等问题。这些因素促使我们需要计算方法来重建或扩展当前空间测量所未能提供的组织背景。我们提出了MORPHE（结构化空间高维嵌入建模），这是一个AI框架，能够直接从空间组学数据学习合成生物上保真的组织结构。MORPHE引入了一种图引导的概率嵌入，将离散的细胞身份及其空间关系映射到一个与扩散建模兼容的连续RGB式潜在空间。这种表征桥梁使得空间细胞图谱能够利用大型预训练图像生成模型，同时在解码时保持生物学可解释性。通过将细胞建模为生成的基本单位，并学习其身份和空间关系如何共同形成大规模组织结构，MORPHE能够以单细胞分辨率生成和重建组织结构。我们将该方法应用于来自肠道的规模性单细胞蛋白质组数据集和来自大脑的单细胞转录组数据集，展示了其在数百万细胞上的计算可扩展性。我们使用MORPHE对这些数据集进行超出实验受限视野的外推、填补缺失或实验损伤的组织区域，并执行跨组织插补，将分离的组织区域连接成一个连续的二维和三维样本。MORPHE代表了一类新的组织生成算法，将有助于解决当前单细胞空间组学数据集的局限性和挑战。

## Abstract
Spatially resolved omics technologies reveal tissue organization at single-cell resolution but remain limited by the cost of the assays, incomplete spatial coverage, 2D-only imaging, and experimental artifacts. These factors motivate the need for in silico methods that can reconstruct or extend tissue context beyond what current spatial measurements provide. We present MORPHE (MOdeling of stRuctured sPatial High-dimensional Embeddings), an AI framework that learns to synthesize biologically faithful tissue architecture directly from spatial-omics data. MORPHE introduces a graph-informed probabilistic embedding that maps discrete cell identities and their spatial relationships into a continuous RGB-like latent space compatible with diffusion modeling. This representational bridge enables spatial cellular maps to leverage large pre-trained image-generative models while preserving biological interpretability upon decoding. By modeling cells as the fundamental units of generation and learning how their identities and spatial relationships collectively give rise to large-scale tissue structure, MORPHE enables generation and reconstruction of tissue architecture at single-cell resolution. We applied the method across large-scale single-cell proteomic datasets from the intestine and single-cell transcriptomic datasets from the brain, showing computational scalability acrosss millions of cells. We used MORPHE on these datasets to outpaint beyond experimentally restricted fields of view, inpaint missing or experimentally damaged tissue regions, and perform cross-tissue imputation, connecting separated tissue regions into a single contiguous sample in both 2D and 3D. MORPHE represents a new class of tissue generation algorithms that will help solve current limitations and challenges with single-cell spatial-omics datasets.