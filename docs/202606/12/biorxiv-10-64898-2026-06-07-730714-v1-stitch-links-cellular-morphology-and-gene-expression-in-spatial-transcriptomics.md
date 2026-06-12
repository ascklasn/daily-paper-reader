---
title: STITCH links cellular morphology and gene expression in spatial transcriptomics
title_zh: STITCH将空间转录组学中的细胞形态与基因表达联系起来
authors: "Kumar, S., Shi, Y., Vallius, T., Day, C.-P., Absil, P.- A., Srivastava, A., Hannenhalli, S., Gopalan, V."
date: 2026-06-11
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.07.730714v1.full.pdf"
tags: ["query:spatialprot"]
score: 8.0
evidence: 通过形状分析连接空间转录组中细胞形态与基因表达
tldr: 空间转录组学中细胞形态与基因表达的共变分析缺乏可解释的形态表示，现有深度学习方法混淆了形状与大小。本文提出基于Kendall形状流形的切线主成分分析(TPCA)，提取尺寸无关的细胞轮廓特征，并开发STITCH框架揭示形态-基因表达关联。STITCH在RNAi筛选中优于以往方法，在Xenium和CosMx数据集中优于深度学习，并独立验证黑色素瘤间充质样细胞状态与细胞面积增加的关系。该方法提供了跨平台、跨细胞类型的可解释形态-转录组分析工具。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有空间转录组学中缺乏既能解耦形状与大小、又具有可解释性的细胞形态表示方法。
method: 基于Kendall形状流形的切线主成分分析(TPCA)提取尺寸无关的细胞轮廓特征，并开发STITCH框架揭示形态与基因表达的共变关系。
result: STITCH在RNAi筛选中优于以往方法，在Xenium和CosMx数据集中优于深度学习，并独立验证黑色素瘤间充质样细胞状态与细胞面积增加的相关性。
conclusion: STITCH提供了可解释的形态-转录组关系，可跨细胞类型、患者和平台应用，助力空间转录组功能解析。
---

## 摘要
原位空间测序可以揭示体内细胞形态与基因表达之间的共变关系。然而，目前尚未有基于原则且可解释的形态学数学表示方法应用于此。特别是，当前基于深度学习的细胞图像表示方法混淆了细胞的形状和大小。我们提出了一种基于Kendall形状流形上的切线主成分分析（TPCA）的可解释细胞边界轮廓表示方法，该方法能捕捉与大小无关的轮廓形状特征。与之前的度量几何方法相比，该方法在RNAi筛选中成功恢复了影响形状的基因。我们在TPCA基础上开发了STITCH（形状-转录组相关性与协调），一种揭示ISS数据集中细胞形态与基因表达共变关系的方法。在Xenium数据集中，STITCH在恢复角质形成细胞的分层组织和核偏心率的空间梯度方面优于基于深度学习的方法。在黑色素瘤CosMx数据集的样本中，STITCH可重复地将拉长和三角形的成纤维细胞与恶性细胞邻近性及肌成纤维细胞样转录程序关联起来。最后，STITCH在两个黑色素瘤队列中独立恢复了间充质样恶性细胞状态与细胞面积增加之间的已知联系。因此，STITCH可以在不同细胞类型、患者和空间转录组学平台之间产生可解释的形态-转录组关系。

## Abstract
In situ spatial (ISS) sequencing can uncover co-variation between cellular morphology and gene expression in vivo. However, a principled and interpretable mathematical representation of morphology has not yet been applied in this context. In particular, current deep learning-based representations of cell images confound a cell's shape with its size. We present an interpretable representation of cellular boundary contours, based on tangent principal component analysis (TPCA) in a Kendall shape manifold, that captures size-independent contour shape features. This approach successfully recovers shape-perturbing genes in an RNAi screen than a previous metric geometry-based approach. We build on TPCA to develop STITCH (Shape-TranscriptomIc Correlation and Harmonization), an approach to reveal covariation between cell morphology with gene expression in ISS datasets. In a Xenium dataset, STITCH outperforms a deep learning-based approach in both recovering the layered organization of keratinocytes and a spatial gradient in nuclear eccentricity. Across samples in a melanoma CosMx dataset, STITCH reproducibly associates elongated and triangular fibroblasts with proximity to malignant cells and myofibroblast-like transcriptional program. Finally, STITCH independently recovers a known link between mesenchymal-like malignant cell states and increased cell area in two melanoma cohorts. STITCH can thus yield interpretable morphology-transcriptome relationships across cell types, patients, and spatial transcriptomics platforms.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：空间转录组学（ISS）技术可以同时获取细胞的基因表达和形态图像，但现有方法缺乏可解释的数学表示来关联细胞形态与基因表达。尤其是深度学习模型混淆了细胞的形状（shape）与大小（size），无法独立分析形状对基因表达的影响。
- **整体含义**：作者旨在提出一种能解耦形状与大小、且具有可解释性的形态表示方法，并建立形态-转录组关联框架，从而在单细胞水平揭示不同细胞类型、患者及平台间的形态-基因表达共变关系，推动空间转录组功能解析。

### 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：利用Kendall形状流形上的切线主成分分析（TPCA）提取与尺寸无关的细胞轮廓形状特征，在此基础上构建STITCH（Shape-TranscriptomIc Correlation and Harmonization）框架，实现形态与基因表达的联合分析。
- **关键技术细节**：
  - **细胞轮廓表示**：将每个细胞的封闭轮廓点集通过Procrustes对齐映射到Kendall形状流形，在切空间中计算主成分，得到一组正交的形状模式（shape modes），这些模式仅描述轮廓形状，不含大小信息。
  - **STITCH框架**：将TPCA得到的形状模式与基因表达数据（如UMI计数）进行相关性分析（Pearson相关），识别与特定形状模式显著相关的基因；同时可进行跨样本、跨平台的一致性整合（harmonization）。
  - **对比方法**：与传统度量几何方法（如ShapeDNA）和深度学习基线（如细胞图像自动编码器）进行对比。

### 3. 实验设计：使用了哪些数据集/场景、benchmark、对比方法
- **数据集与场景**：
  - **RNAi筛选数据集**：用于验证TPCA能否恢复已知的形态相关基因（如影响细胞形状的基因）。
  - **Xenium数据集**（10x Genomics）：包含角质形成细胞，用于评估STITCH能否恢复角质形成细胞的分层组织以及核偏心率的空间梯度。
  - **CosMx数据集**（NanoString）：包含黑色素瘤样本，用于分析成纤维细胞形态与恶性细胞邻近性及肌成纤维细胞样转录程序的关系；还用于验证间充质样恶性细胞状态与细胞面积增加之间的联系（两个独立黑色素瘤队列）。
- **Benchmark和对比方法**：
  - 对比方法包括：基于度量几何的ShapeDNA、深度学习方法（如细胞图像自动编码器）等。
  - 在RNAi筛选中，STITCH（基于TPCA）优于之前的度量几何方法。
  - 在Xenium数据集中，STITCH优于深度学习基线，能够更好地恢复组织结构和核偏心率的空间梯度。

### 4. 资源与算力
- **文中未明确说明**：摘要和元数据中未提及任何GPU型号、数量、训练时长或算力资源。因此，无法总结具体的计算资源使用情况。

### 5. 实验数量与充分性
- **实验数量**：至少涉及三个主要数据集/场景：RNAi筛选、Xenium（角质形成细胞）、CosMx（黑色素瘤，含不同样本及两个独立队列）。每个场景下都进行了与基线方法的定量对比。
- **充分性评价**：实验覆盖了验证方法效果（恢复已知基因）、跨平台（Xenium、CosMx）和跨细胞类型（角质形成细胞、成纤维细胞、恶性细胞）的测试，以及独立队列验证。整体较为充分。但未提及消融实验（如对TPCA不同参数的影响）或更多统计检验细节（如多重假设校正方法），略有限制。

### 6. 论文的主要结论与发现
- **主要结论**：STITCH能够提供可解释的形态-转录组关系，且可跨细胞类型、患者和空间转录组平台应用。
- **具体发现**：
  - 在RNAi筛选中，TPCA恢复了已知影响细胞形状的基因，优于之前的度量几何方法。
  - 在Xenium数据集中，STITCH成功恢复角质形成细胞的分层组织以及核偏心率的空间梯度，表现优于深度学习。
  - 在CosMx黑色素瘤样本中，STITCH可重复地关联拉长和三角形的成纤维细胞与恶性细胞邻近性及肌成纤维细胞样转录程序。
  - 在两个黑色素瘤队列中，独立验证了间充质样恶性细胞状态与细胞面积增加之间的已知联系。

### 7. 优点：方法或实验设计上的亮点
- **方法学亮点**：
  - 引入Kendall形状流形上的TPCA，首次将流形学习引入空间转录组形态分析，实现形状与大小的严格解耦。
  - STITCH框架可解释性强：每个形状模式对应具体的轮廓形状变化，可直接用于与基因表达的相关性分析。
- **实验设计亮点**：
  - 跨平台（Xenium、CosMx）、跨细胞类型（角质形成细胞、成纤维细胞、恶性细胞）验证了方法的通用性。
  - 使用独立队列进行外部验证（如两个黑色素瘤队列中的间充质样细胞-面积关联），增强了结论的可靠性。
  - 与深度学习和传统几何方法进行公平对比，突出了TPCA的优越性。

### 8. 不足与局限
- **实验覆盖**：未提供消融实验（如使用其他形状表示方法、不同轮廓点采样等），也未详细说明统计显著性阈值或矫正方法。
- **偏差风险**：摘要未明确提及如何处理批次效应或平台差异，STITCH的“协调”可能依赖手动或经验性校正；对于不同细胞类型的手动形态分类可能存在主观偏差。
- **应用限制**：该方法依赖于完整的细胞轮廓数据（如通过分割获得），若分割不准确或细胞边界模糊则可能影响结果；对核形状分析（如核偏心率）仅适用于分割可用的场景。此外，当前验证仅限于皮肤和黑色素瘤组织，对其他组织（如脑、肠道）的适用性未知。

（完）
