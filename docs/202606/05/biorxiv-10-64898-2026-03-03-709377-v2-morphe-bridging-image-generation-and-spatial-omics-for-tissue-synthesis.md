---
title: "MORPHE: Bridging Image Generation and Spatial Omics for Tissue Synthesis"
title_zh: MORPHE：连接图像生成与空间组学的组织合成
authors: "Feng, Y., Robers, Z., Rasheed, L., Miao, Y., Wen, S., Lee, K., Sohigian, J., Brbic, M., Hickey, J. W."
date: 2026-05-28
pdf: "https://www.biorxiv.org/content/10.64898/2026.03.03.709377v2.full.pdf"
tags: ["query:spatialprot"]
score: 8.0
evidence: 基于空间组学数据合成组织架构的AI框架
tldr: 空间组学技术虽能解析单细胞组织架构，但存在成本高、覆盖不全、仅二维等问题。为此提出MORPHE框架，将离散细胞身份和空间关系编码为连续RGB-like潜空间，利用扩散模型生成单细胞分辨率的组织图像。在肠和脑的百万级细胞数据上验证，实现了外推、修复和跨组织填充，2D/3D均可。该方法为空间组学数据合成开辟了新路径。
source: biorxiv
selection_source: fresh_fetch
motivation: 空间组学技术受限于成本、覆盖不全和二维成像，需要计算方法在计算机中重建或扩展组织上下文。
method: 提出MORPHE，通过图信息概率嵌入将细胞身份与空间关系映射到RGB-like隐空间，利用预训练扩散模型生成，解码回单细胞分辨率组织。
result: 在肠和脑的大规模单细胞蛋白组/转录组数据上，成功实现视野外推、缺失区域修复和跨组织连接，支持2D和3D。
conclusion: MORPHE代表了一类新的组织生成算法，有助于解决空间组学数据集当前面临的限制和挑战。
---

## 摘要
空间分辨组学技术以单细胞分辨率揭示组织结构，但仍受限于实验成本、空间覆盖不完整、仅二维成像以及实验伪影。这些因素促使我们需要发展计算方法，以重建或扩展当前空间测量所无法提供的组织环境。我们提出了MORPHE（结构化空间高维嵌入建模），这是一个人工智能框架，能够直接从空间组学数据中学习并合成生物学上真实的组织结构。MORPHE引入了一种图感知的概率嵌入方法，将离散的细胞身份及其空间关系映射到与扩散模型兼容的连续RGB样潜在空间中。这种表示桥梁使得空间细胞图谱能够利用预训练的大型图像生成模型，同时在解码时保持生物可解释性。通过将细胞建模为生成的基本单元，并学习它们的身份和空间关系如何共同形成大规模组织结构，MORPHE能够以单细胞分辨率生成和重建组织结构。我们将该方法应用于来自肠道的大规模单细胞蛋白质组数据集和来自大脑的单细胞转录组数据集，展示了在数百万个细胞上的计算可扩展性。我们利用MORPHE在这些数据集上进行外推（超出实验限制的视野）、修复（填补缺失或实验损伤的组织区域）以及跨组织插补（将分离的组织区域连接成单个连续样本，包括二维和三维）。MORPHE代表了一类新的组织生成算法，将有助于解决当前单细胞空间组学数据集的局限性和挑战。

## Abstract
Spatially resolved omics technologies reveal tissue organization at single-cell resolution but remain limited by the cost of the assays, incomplete spatial coverage, 2D-only imaging, and experimental artifacts. These factors motivate the need for in silico methods that can reconstruct or extend tissue context beyond what current spatial measurements provide. We present MORPHE (MOdeling of stRuctured sPatial High-dimensional Embeddings), an AI framework that learns to synthesize biologically faithful tissue architecture directly from spatial-omics data. MORPHE introduces a graph-informed probabilistic embedding that maps discrete cell identities and their spatial relationships into a continuous RGB-like latent space compatible with diffusion modeling. This representational bridge enables spatial cellular maps to leverage large pre-trained image-generative models while preserving biological interpretability upon decoding. By modeling cells as the fundamental units of generation and learning how their identities and spatial relationships collectively give rise to large-scale tissue structure, MORPHE enables generation and reconstruction of tissue architecture at single-cell resolution. We applied the method across large-scale single-cell proteomic datasets from the intestine and single-cell transcriptomic datasets from the brain, showing computational scalability acrosss millions of cells. We used MORPHE on these datasets to outpaint beyond experimentally restricted fields of view, inpaint missing or experimentally damaged tissue regions, and perform cross-tissue imputation, connecting separated tissue regions into a single contiguous sample in both 2D and 3D. MORPHE represents a new class of tissue generation algorithms that will help solve current limitations and challenges with single-cell spatial-omics datasets.