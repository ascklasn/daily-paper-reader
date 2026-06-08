---
title: Morphology-robust quantification of subcellular organization in complex cells
title_zh: 复杂细胞中亚细胞组织的形态鲁棒定量分析
authors: "Hu, R., Naseri, N. N., Shalem, O., Camara, P. G."
date: 2026-06-01
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.28.728543v1.full.pdf"
tags: ["query:spatialprot"]
score: 8.0
evidence: 形态鲁棒的亚细胞蛋白组织定量
tldr: 对于形态复杂的细胞如神经元，传统亚细胞蛋白定位量化受形态变异影响。CellAligner基于非平衡Gromov-Wasserstein最优传输，将不同形态细胞的蛋白分布对齐到统一锚点细胞上，消除形态混淆。应用于神经元图像，使现有方法的多类定位分类MCC提升约两倍，并揭示了药物诱导的溶酶体缺陷。此外，深度学习的加速版本dCellAligner-OT支持大规模分析。
source: biorxiv
selection_source: fresh_fetch
motivation: 形态复杂细胞中，亚细胞蛋白定位分析受细胞形态差异干扰，现有方法难以鲁棒识别定位模式。
method: 提出CellAligner，利用非平衡Gromov-Wasserstein耦合适配将蛋白分布映射到共享锚点细胞几何。
result: 在神经元成像中，使用锚点细胞表示提升现有方法多类定位分类MCC约两倍，并发现药物诱导的溶酶体缺陷。
conclusion: CellAligner提供通用框架，实现形态鲁棒的亚细胞组织量化，加速版本支持大规模分析。
---

## 摘要
亚细胞蛋白质组织的定量分析常常因细胞形态的变异而受到干扰，从而限制了从形态复杂的细胞（如神经元和胶质细胞）的荧光显微镜数据中识别和解释定位模式。我们提出了CellAligner，这是一个无监督框架，利用融合非平衡Gromov-Wasserstein耦合将来自形态不同细胞的蛋白质分布映射到共享的锚细胞几何结构，从而实现亚细胞定位的形态鲁棒比较。在神经元成像基准测试中，将当前的图像分析方法（CellProfiler、Cytoself、Paired Cell Inpainting）应用于CellAligner的锚细胞表示，显著减少了形态相关的混杂因素，同时将其定位分类的多类MCC大约翻倍。我们通过识别U18666A诱导的人iPSC衍生神经元中的溶酶体运输缺陷来证明其生物学实用性。为了扩展该方法，我们开发了dCellAligner-OT，这是一个快速深度度量学习模型，近似于CellAligner的最优传输距离和锚细胞表示，支持图谱规模的分析。CellAligner为复杂细胞系统中亚细胞组织的形态鲁棒分析提供了一个通用框架。

## Abstract
Quantitative analysis of subcellular protein organization is often confounded by variation in cell morphology, limiting the identification and interpretation of localization patterns in fluorescence microscopy data from morphologically complex cells, such as neurons and glia. We introduce CellAligner, an unsupervised framework that uses fused unbalanced Gromov-Wasserstein couplings to map protein distributions from morphologically distinct cells into shared anchor-cell geometries, enabling morphology-robust comparison of subcellular localization. In neuronal imaging benchmarks, applying current image-analysis methods (CellProfiler, Cytoself, Paired Cell Inpainting) to CellAligners anchor-cell representations substantially reduced morphology-associated confounding while approximately doubling their multiclass MCC for localization classification. We demonstrate its biological utility by identifying U18666A-induced lysosomal trafficking defects in human iPSC-derived neurons. To scale the approach, we developed dCellAligner-OT, a fast deep metric learning model that approximates CellAligners optimal transport distances and anchor-cell representations, enabling atlas-scale analyses. CellAligner provides a general framework for morphology-robust analysis of subcellular organization in complex cellular systems.