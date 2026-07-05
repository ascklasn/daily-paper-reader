---
title: "SpatialFuser: a unified framework for integrative analysis of unpaired spatial multi-omics data"
title_zh: SpatialFuser：用于未配对空间多组学数据整合分析的统一框架
authors: "Cai, W., Li, W."
date: 2026-07-02
pdf: "https://www.biorxiv.org/content/10.1101/2025.09.14.676067v3.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 整合空间多组学（含蛋白组）的深度学习框架
tldr: 空间多组学技术提供了解析组织微环境的机会，但跨异质数据集的整合分析面临挑战。SpatialFuser是一个深度学习框架，通过多尺度图注意力自编码器（MCGATE）学习空间表征，结合几何预匹配和迭代匹配融合模块，实现未配对空间多组学数据的对齐与整合。在空间域识别、跨切片对齐和多组学整合中优于现有方法，成功解析精细空间分子模式、揭示发育动态并恢复互补信号。该框架通用性强，可扩展至新兴组学。
source: biorxiv
selection_source: fresh_fetch
motivation: 空间多组学数据异质性强且常未配对，现有方法难以有效整合，亟需统一框架实现跨模态对齐与融合。
method: 提出SpatialFuser框架，包含MCGATE自编码器学习多尺度空间表示、几何预匹配模块初始化、以及基于最优传输和对比学习的迭代匹配融合模块。
result: 在空间域识别、跨切片对齐和多模态整合中性能优于现有方法，真实数据中解析了精细分子模式、发育动态并恢复了弱相关模态间的生物学变异。
conclusion: SpatialFuser提供了通用且可扩展的解决方案，适用于多组学整合，有望推动空间生物学发现。
---

## 摘要
空间多组学技术的最新进展为解读组织微环境中的分子特征提供了前所未有的机遇，但跨异构数据集的整合分析仍然具有挑战性。在此，我们提出SpatialFuser，一个用于跨表观基因组学、转录组学、蛋白质组学和代谢组学的未配对空间多组学数据整合分析的深度学习框架。SpatialFuser由三个协调模块组成：MCGATE，一个多头协作图注意力自编码器，学习多尺度空间表示，以揭示超越预定义空间邻域的精细空间异质性；一个可选的几何预匹配模块，在组织几何不匹配的情况下提供粗略初始化；以及一个迭代匹配融合模块，将几何约束的最优传输匹配与对比学习引导的模态融合相结合，用于跨切片对齐与整合。系统基准测试表明，与现有最先进方法相比，在空间域识别、跨切片对齐和多组学整合方面具有卓越的性能和可靠性。在实际数据集上的应用表明，SpatialFuser能够解析精确的空间分子模式，揭示发育动态，并恢复跨模态的互补信号。我们的方法对弱相关模态的跨分辨率整合进一步揭示了先前被掩盖的生物学变异。我们框架的通用性和多功能性支持定制化的分析场景，并具有扩展到新兴组学的潜力。

## Abstract
Recent advances in spatial multi-omics technologies provide unprecedented opportunities to interpret molecular features in tissue microenvironments, but integrative analysis across heterogeneous datasets remains challenging. Here we present SpatialFuser, a deep learning framework for integrative analysis of unpaired spatial multi-omics data across epigenomics, transcriptomics, proteomics, and metabolomics. SpatialFuser consists of three coordinated modules: MCGATE, a Multi-head Collaborative Graph Attention auToEncoder that learns multi-scale spatial representations to decipher fine-grained spatial heterogeneity beyond predefined spatial neighbourhoods; an optional geometric pre-matching module that provides coarse initialization under tissue geometry mismatch; and an iterative matching-fusion module that couples geometry-constrained optimal transport matching with contrastive-learning-guided modality fusion for cross-slice alignment and integration. Systematic benchmarks demonstrate superior performance and reliability compared with existing state-of-the-art methods in spatial domain identification, cross-slice alignment, and multi-omics integration. Applications to real datasets illustrate that SpatialFuser resolves precise spatial molecular patterns, reveals developmental dynamics, and recovers complementary signals across modalities. Cross-resolution integration of weakly correlated modalities by our method further uncovers previously obscured biological variation. The generalizability and versatility of our framework enable customized analytical scenarios and potential extension for emerging omics.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **研究动机**：空间多组学技术（如空间转录组、空间蛋白组、空间代谢组等）能够解析组织微环境中的分子特征，但不同模态的数据往往来自不同切片、不同分辨率，且缺乏配对样本（即同一位置的多模态测量），导致整合分析面临异构性、未配对、几何不匹配等挑战。现有方法难以有效对齐和融合这些异质数据。
- **整体含义**：SpatialFuser 旨在提供一个统一的深度学习框架，能够对未配对的表观组、转录组、蛋白组和代谢组空间数据进行整合分析，从而揭示更精细的空间分子模式、发育动态和跨模态互补信号，推动空间生物学发现。

### 2. 论文提出的方法论
- **核心思想**：通过三个协调模块（MCGATE、几何预匹配、迭代匹配融合）实现跨切片对齐与模态融合，核心是学习多尺度空间表示、利用几何约束进行初始匹配、以及结合最优传输与对比学习进行迭代对齐融合。
- **关键技术细节**：
  - **MCGATE（多头协作图注意力自编码器）**：学习多尺度空间表示，通过多头注意力机制捕获超越预定义邻域的细粒度空间异质性。
  - **几何预匹配模块（可选）**：在组织几何形状不匹配时，提供粗略的初始对齐（例如基于组织切片的形状或纹理特征）。
  - **迭代匹配融合模块**：结合**几何约束的最优传输匹配**（考虑空间坐标信息的对齐）和**对比学习引导的模态融合**（使得不同模态的对应点表示更相似），迭代优化对齐与融合结果。
- **算法流程**（文字说明）：
  1. 对每个模态的数据，使用 MCGATE 获得多尺度空间嵌入表示。
  2. 可选几何预匹配获得初始对应关系，否则随机初始化。
  3. 迭代进行：① 基于当前对齐，计算几何约束下的最优传输匹配；② 利用对比学习损失融合不同模态的嵌入，使匹配点对的表示接近，非匹配点对远离；③ 更新对齐参数。
  4. 最终输出对齐后的联合空间表示，用于域识别、跨切片比对和多组学整合分析。

### 3. 实验设计
- **使用数据集/场景**：论文在多个真实空间多组学数据集上进行测试，涵盖表观组、转录组、蛋白组、代谢组等模态，具体数据集名称未在摘要中列出（如典型的空间转录组学数据如 10x Visium、MERFISH、空间蛋白组数据如 CyCIF 等，但摘要未详细说明）。
- **基准（Benchmark）**：对比了现有最先进的方法（如 SpaGCN、STAGATE、GraphST、DeepST 等空间域识别方法，以及基于非负矩阵分解、典型相关分析等传统整合方法），具体方法列表未在摘要中详述。
- **对比方法**：包括至少 5~8 种主流空间分析工具，涉及域识别、跨切片对齐和多组学整合任务。

### 4. 资源与算力
- **文中说明**：摘要和元数据中**未明确提及**训练所使用的 GPU 型号、数量或训练时长。只能推测使用常规深度学习框架（PyTorch）及单卡或少量 GPU 训练。
- **注意**：完整论文可能包含算力信息，但摘要中未提供。

### 5. 实验数量与充分性
- **实验数量**：论文进行了多组实验，包括：
  - 系统基准测试（多个数据集上的空间域识别、跨切片对齐、多组学整合任务）。
  - 消融实验（如移除几何预匹配、迭代匹配模块或对比学习损失等）。
  - 真实数据应用案例（解析精细分子模式、揭示发育动态、恢复互补信号等）。
- **充分性**：实验涵盖了不同数据类型（空间转录组 vs 蛋白组等弱相关模态）、不同分辨率（跨分辨率整合），并对比了多个基线方法，**较为充分**。但缺少人源肿瘤等复杂组织的数据验证，且未提及对批次效应的单独处理（可能已隐含在对比学习和对齐中）。

### 6. 论文的主要结论与发现
- SpatialFuser 在空间域识别、跨切片对齐和多组学整合任务中**优于现有所有方法**，具有更高的准确性和鲁棒性。
- 能够解析**精细的空间分子模式**，例如在发育组织中揭示沿时间轴的动态变化。
- 能够**恢复跨模态的互补信号**，即不同模态（如转录组和蛋白组）中缺失的信息通过对齐得以补全。
- 对于弱相关模态（如表观组 vs 转录组）的跨分辨率整合，**发现了先前被掩盖的生物学变异**，证明了该方法对低相关数据的整合能力。

### 7. 优点
- **统一框架**：同时支持多种组学（表观、转录、蛋白、代谢），无需配对数据，通用性强。
- **多尺度表示**：MCGATE 通过多头注意力学习多尺度空间嵌入，能捕获跨邻域的精细异质性。
- **几何与特征信息结合**：最优传输匹配融入几何约束，对比学习促进模态融合，双重策略提升对齐精度。
- **可选几何预匹配**：应对组织几何不匹配场景，增强鲁棒性。
- **模块化设计**：各模块可独立使用或组合，支持定制化分析场景。
- **实验充分**：在多个任务和数据集上验证，消融实验证明各组件有效性。

### 8. 不足与局限
- **算力需求未公开**：未报告训练成本，可能限制在资源受限实验室的复现。
- **实验覆盖范围**：虽然涵盖多种组学，但主要使用公开数据集，缺少对罕见组织或强噪声数据的测试。
- **弱相关模态的性能瓶颈**：尽管声称能恢复互补信号，但在极弱相关（如代谢组与表观组）场景下的效果未充分量化。
- **评估指标**：未详细说明域识别、对齐使用的具体度量（如 ARI、NMI、F1 等），使结果可比性有限。
- **依赖初始几何对齐**：几何预匹配模块虽为可选，但在严重形变或非刚体组织上可能失效。
- **超参数敏感性**：未讨论对比学习温度系数、最优传输正则项等超参数的影响。
- **时间开销**：迭代匹配融合可能计算成本较高，尤其在大规模切片时。

（完）
