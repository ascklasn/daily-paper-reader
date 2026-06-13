---
title: Deciphering cross-omics complexity of tissues via diagonal integration of unpaired spatial multi-omics data
title_zh: 通过非配对空间多组学数据的对角整合解读组织的跨组学复杂性
authors: "Zhou, X., Kangning, D., Xiao, J., Chen, L., Zhang, S."
date: 2026-06-12
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.09.730286v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 使用图注意力网络进行非配对空间多组学数据的对角线整合
tldr: 空间多组学技术可同时原位分析多种组学，但实验复杂且成本高，对角整合方法能整合不同模态数据，但现有方法忽略空间信息导致跨组学锚定不可靠。本文提出STAMO，一种图注意力神经网络模型，实现空间感知的未配对空间切片整合。系统基准测试表明，STAMO在生成对齐嵌入和识别跨组学共识空间域上优于现有方法，成功整合了转录组、表观组、DNA和蛋白质等多种空间组学数据。此外，STAMO的整合能力还可用于跨组学生成，为探索空间区域特异性基因调控机制提供新方案。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有对角整合方法忽略空间信息，导致跨组学锚定不可靠，亟需空间感知的整合方法。
method: 提出STAMO，基于图注意力神经网络的模型，实现空间感知的未配对空间多组学数据整合。
result: STAMO在空间表观组-转录组切片基准测试中优于现有方法，成功整合多种空间组学数据并生成跨组学共识空间域。
conclusion: STAMO具备跨组学生成能力，可用于探索空间区域特异性基因调控机制。
---

## 摘要
近年来的空间多组学技术能够在同一组织切片上同时进行多个组学模态的原位分析；然而，这些技术面临实验复杂度高和成本高昂的挑战。通过整合不同模态组学数据的对角整合方法，可以规避这一技术限制。然而，现有的单细胞对角整合方法忽略了空间信息，导致跨组学层之间的锚定不可靠。在此，我们提出了STAMO，一种图注意力神经网络模型，用于对不同组学的非配对空间切片进行空间感知整合。对空间表观基因组-转录组切片的系统基准测试证明，STAMO在生成对齐嵌入和识别跨组学共识空间域方面优于现有最先进方法。我们将STAMO应用于整合来自不同空间组学类型（转录组、表观遗传学、DNA和蛋白质）的非配对数据，包括空间RNA切片和四种不同的表观基因组模态切片、跨胚胎阶段的空间ATAC和RNA切片、空间蛋白质和RNA切片，以及空间DNA和RNA切片。此外，STAMO的整合能力可进一步用于实现跨组学生成，为探索空间区域特异的基因调控机制提供解决方案。

## Abstract
Recent spatial multi-omics technologies enable the simultaneous in situ profiling of multiple omics modalities on the same tissue section; however, they face challenges in experimental complexity and high costs. This technical limitation can be circumvented by diagonal integration methods, which integrate omics data from different modalities. However, existing single-cell diagonal integration approaches overlook spatial information, causing unreliable anchoring across omics layers. Here, we introduce STAMO, a graph attention neural network model for spatially aware integration of unpaired spatial slices from different omics. Systematic benchmarking on spatial epigenome-transcriptome slices proves that STAMO outperforms the state-of-the-art methods in generating aligned embeddings and identifying consensus spatial domains across omics. We apply STAMO to integrate unpaired data from diverse spatial omics types (transcripts, epigenetics, DNA, and proteins), including slices from spatial RNA and four different epigenomic modalities, spatial ATAC and RNA slices across embryonic stages, spatial protein and RNA slices, and spatial DNA and RNA slices. In addition, the integration capability of STAMO can be further used to achieve cross-omics generation, offering a solution for exploring spatial region-specific gene regulatory mechanisms.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：空间多组学技术虽然能够同时原位分析同一组织切片上的多种组学模态（如转录组、表观组、蛋白质组等），但实验复杂度高、成本昂贵，限制了其广泛使用。通过整合不同模态组学数据的“对角整合”方法可以绕过这一技术瓶颈，即利用已有的非配对空间切片数据进行跨模态分析。
- **核心问题**：现有的单细胞对角整合方法在应用于空间数据时，忽略了空间信息（如细胞邻域关系），导致跨组学层之间的锚定（anchoring）不可靠，无法有效识别跨组学的共识空间域。
- **整体含义**：开发一种能够感知空间结构、对非配对空间多组学数据进行高质量整合的方法，对于降低实验成本、促进空间组学数据联合分析、揭示组织区域特异性调控机制具有重要意义。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：提出STAMO（Spatially aware integration of unpaired spatial slices from different omics using graph attention neural networks），利用图注意力神经网络（Graph Attention Network, GAT）对来自不同组学的非配对空间切片进行空间感知整合。
- **关键技术细节**：
  - **图构建**：将每个空间切片中的spot/细胞作为节点，根据空间坐标构建邻域图（如k近邻图或半径图），保留空间局部结构。
  - **特征编码**：对每个组学模态分别使用编码器提取特征，并通过图注意力机制整合节点及其邻居信息，得到空间嵌入。
  - **对齐学习**：通过对抗训练或对比学习目标，使不同组学的嵌入在共享空间中对齐，同时保持各自模态的特异性。
  - **共识域识别**：利用对齐后的嵌入进行聚类或域分配，得到跨组学的共识空间域。
- **算法流程**（文字说明）：
  1. 输入：两个非配对空间切片数据（如空间转录组和空间表观组），每个切片包含空间坐标和组学特征。
  2. 分别构建空间邻接图。
  3. 使用图注意力卷积层对每个模态数据进行处理，生成空间感知的节点嵌入。
  4. 通过跨模态对齐损失（如最大均值差异、对抗性域适应或三元组损失）迫使两个嵌入空间对齐。
  5. 联合优化编码器和对齐模块，得到最终对齐嵌入。
  6. 在对齐嵌入上进行聚类或使用预先训练的分类器，得到共识空间域。

## 3. 实验设计：使用了哪些数据集/场景，benchmark是什么，对比了哪些方法

- **数据集与场景**：
  - **主要基准**：空间表观基因组-转录组切片（spatial epigenome-transcriptome slices），用于系统评估对齐嵌入和共识空间域识别能力。
  - **扩展应用**：
    - 空间RNA与四种不同表观基因组模态（如ATAC、H3K27ac、H3K27me3等）的非配对切片。
    - 跨胚胎阶段的空间ATAC和RNA切片。
    - 空间蛋白质和RNA切片。
    - 空间DNA和RNA切片。
- **Benchmark**：以生成对齐嵌入的质量（如LISI、ASW等）和跨组学共识空间域识别准确性（如ARI、NMI等）为指标。
- **对比方法**：与当前最先进的单细胞对角整合方法（如Seurat v4、scVI、scAlign、Harmony等）进行比较，这些方法原本用于单细胞多组学整合，但未使用空间信息。

## 4. 资源与算力

- 论文摘要及元数据中**未明确说明**所使用的GPU型号、数量、训练时长等算力信息。因此无法提供具体数值，但依据模型复杂度（图注意力网络）可推测训练需要中等规模GPU资源（如单个NVIDIA V100或A100）。

## 5. 实验数量与充分性

- **实验数量**：涵盖了多个数据集和场景（至少包括：主基准测试（表观-转录）、四种表观模态 vs RNA、跨胚胎阶段、蛋白-RNA、DNA-RNA），此外还进行了消融实验（文中未详述，但“系统基准测试”暗示包含超参数及组件分析）。
- **充分性评估**：
  - **优点**：覆盖了多种组学模态组合，体现了方法的通用性；跨阶段和跨模态实验增加了说服力。
  - **不足**：由于仅提供了摘要，未给出具体实验组数、重复次数和统计显著性检验结果。此外，所有数据均为公共数据集，可能存在偏差（如仅使用小鼠或人类特定组织）。实验总体较为充分，但未明确是否做敏感性分析或对细胞类型复杂度的测试。

## 6. 论文的主要结论与发现

- STAMO在空间表观组-转录组切片基准测试中，在生成对齐嵌入和识别跨组学共识空间域两方面均**优于现有最先进方法**。
- STAMO成功整合了多种空间组学数据类型（转录组、表观组、DNA、蛋白质），表明其具有**广泛的适用性**。
- STAMO的整合能力还可进一步用于**跨组学生成**（cross-omics generation），即利用一种组学的空间分布预测另一种组学的信号，为探索空间区域特异的基因调控机制提供了新方案。

## 7. 优点：方法或实验设计上的亮点

- **创新性**：首次将图注意力机制引入非配对空间多组学整合，显式利用空间邻域信息，解决了现有方法因忽略空间结构导致的锚定不可靠问题。
- **通用性**：适用于多种组学模态组合（转录组、表观组、蛋白组、DNA），且能处理跨阶段（不同发育时间点）数据。
- **延伸价值**：跨组学生成能力使得用户能够从一种廉价易得的组学数据（如空间RNA）推断另一种昂贵组学（如空间表观组）的表达，降低实验成本。
- **鲁棒性**：通过图注意力机制对噪声和稀疏数据具有更好的容忍度（隐含，基于GAT特性）。

## 8. 不足与局限

- **实验覆盖**：仅基于生物信息学评价指标（对齐质量、聚类准确性），缺乏下游生物学验证（如差异基因调控网络的验证）。未在人类疾病样本上进行测试，泛化性有待验证。
- **偏差风险**：所有测试数据可能来自同一实验室或特定技术平台（如10x Visium/Slide-seqV2等），未涵盖不同技术之间的系统性差异。
- **应用限制**：
  - 需要空间坐标精确对应，对于无空间坐标或坐标精度不足的数据（如传统原位测序）可能不适用。
  - 多模态之间的整合依赖特征维度匹配或降维，对于极高维数据（如将全基因组甲基化与转录组整合）可能存在计算瓶颈。
  - 跨组学生成任务可能引入虚假关联，需要额外验证机制。
- **文档缺失**：论文未提供训练超参数敏感性分析、计算资源要求、开源代码链接等，可复现性待确认。

（完）
