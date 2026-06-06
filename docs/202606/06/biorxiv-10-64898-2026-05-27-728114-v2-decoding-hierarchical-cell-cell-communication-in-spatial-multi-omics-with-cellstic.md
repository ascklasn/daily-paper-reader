---
title: Decoding Hierarchical Cell-Cell Communication in Spatial Multi-Omics with CellSTIC
title_zh: 利用CellSTIC解码空间多组学中的层级细胞间通讯
authors: "Wang, S., Wang, J., Yuan, Z., Xu, Y."
date: 2026-06-05
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.27.728114v2.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 整合转录组和蛋白组的空间多组学细胞通讯框架
tldr: 组织微环境中的细胞间通讯受空间结构调控，但单细胞转录组丢失空间信息，现有空间方法难以整合异质数据且结果不直观。CellSTIC通过整合局部邻域多模态证据，构建可追溯至分子的分层语义通讯程序，支持从配体-受体对到功能模块的分析。在模拟及多组织数据集中，CellSTIC恢复了免疫、脑、发育等空间通讯域。该方法为从原位多组学中生成机制性假设提供了通用框架。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有空间细胞通讯方法难以整合多模态空间数据且输出结果缺乏可解释性，无法有效利用组织架构信息。
method: CellSTIC整合局部微环境多模态证据，构建可追溯至潜在分子的分层语义通讯表示，形成结构化程序。
result: 在模拟及多种真实组织数据中，CellSTIC恢复了空间一致的通讯域，并揭示了免疫、脑、发育等程序。
conclusion: CellSTIC为原位解析组织通讯提供了通用框架，支持跨组织比较和机制假设生成。
---

## 摘要
细胞间通讯协调组织发育、稳态和免疫，但在完整组织中定义信号相互作用仍然具有挑战性。单细胞转录组学能够进行系统的配体-受体推断，但组织解离会去除空间背景并掩盖局部和区域特异性信号。空间转录组学和空间多组学可以原位恢复通讯，尽管现有方法往往不能完全整合异质性数据或产生难以解释的配体-受体列表。在此，我们提出CellSTIC，一个将空间多组学中的细胞间通讯解析为基于组织架构的结构化程序的框架。CellSTIC整合来自局部邻域的多模态证据，并将相互作用组织成可追溯到潜在分子的层级语义表示。这使得从单个配体-受体对到跨组织、区域和状态可比较的功能模块的分析成为可能。在模拟和多样化的组织数据集中，CellSTIC恢复了空间上一致的通讯结构和域，揭示了免疫、大脑、发育和再生程序，并提供了一种在原位产生机制性假设的通用方法。

## Abstract
Cell-cell communication coordinates tissue development, homeostasis, and immunity, yet defining signaling interactions within intact tissues remains challenging. Single-cell transcriptomics enables systematic ligand-receptor inference, but tissue dissociation removes spatial context and obscures local and region-specific signaling. Spatial transcriptomics and spatial multi-omics can recover communication in situ, although existing methods often incompletely integrate heterogeneous data or produce poorly interpretable ligand-receptor lists. Here, we present CellSTIC, a framework that resolves cell-cell communication in spatial multi-omics as structured programs grounded in tissue architecture. CellSTIC integrates multimodal evidence from local neighborhoods and organizes interactions into a hierarchical semantic representation that remains traceable to underlying molecules. This enables analysis from individual ligand-receptor pairs to functional modules comparable across tissues, regions, and states. In simulations and diverse tissue datasets, CellSTIC recovered spatially coherent communication structures and domains, revealing immune, brain, developmental, and regenerative programs, and providing a general approach for generating mechanistic hypotheses in situ.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：组织微环境中细胞间通讯（如配体-受体相互作用）受空间结构调控，但传统单细胞转录组学在组织解离后丢失空间背景，无法捕捉局部和区域特异性信号。现有空间组学方法（如空间转录组学、空间多组学）虽可原位重建通讯，但存在两大不足：
  - 无法有效整合异质多模态数据（如转录组+蛋白组）；
  - 输出结果往往是一长串难以解释的配体-受体列表，缺乏可解释性和结构化组织。
- **核心问题**：如何从空间多组学数据中提取具有高度可解释性、层级化且可追溯至分子的细胞通讯程序，以生成机制性假设并实现跨组织/区域/状态的比较。

### 2. 论文提出的方法论：核心思想、关键技术细节、算法流程

- **核心思想**：提出 CellSTIC 框架，将空间多组学中的细胞间通讯解析为**基于组织架构的结构化程序**。其关键在于整合局部邻域的多模态证据，并将相互作用组织成**层级语义表示**，保留对底层分子的可追溯性。
- **关键技术细节**：
  - **多模态证据整合**：在局部邻域（如每个细胞的邻近细胞群）内，整合来自空间转录组、空间蛋白组等多种数据模态的信号（如基因表达、蛋白质丰度）。
  - **层级语义表示**：将配体-受体对逐步聚合成更高层次的语义单元（如功能模块、通程），形成树状结构。每个层级均可追溯至原始分子，保证解释性。
  - **结构化通讯程序**：最终输出从单个配体-受体对到功能模块的分层程序，支持在不同组织、区域和细胞状态之间进行比对和比较。
- **算法流程**（文字描述）：
  1. 对空间多组学数据进行预处理，定义每个细胞的局部邻域（基于空间坐标或组织学图像）。
  2. 在每个邻域内，计算多模态证据（如配体-受体共表达、空间接近性、蛋白质互作证据）。
  3. 构建层次语义树：从底层配体-受体对开始，通过语义相似性或功能富集逐步合并，形成中层子程序（如免疫激活、发育调控）和顶层程序。
  4. 输出可追溯的层级表示，并支持跨样本/区域的比较分析。

### 3. 实验设计：使用的数据集/场景、基准测试、对比方法

- **数据集与场景**：
  - 模拟数据集（用于验证方法有效性）。
  - 多种真实组织数据集：免疫组织、脑组织、发育组织、再生组织等。
- **基准测试**：未明确列出具体基准（如空间通讯推断黄金标准），但通过恢复空间一致的结构和域来评估。
- **对比方法**：文中未详细列出对比方法名称，仅指出“现有方法往往不能完全整合异质性数据或产生难以解释的配体-受体列表”，暗示 CellSTIC 在解释性和多模态整合方面优于现有方法。

### 4. 资源与算力

- **文中未明确说明**：摘要和元数据中没有提及使用的 GPU 型号、数量、训练时长或任何计算资源信息。因此无法总结。

### 5. 实验数量与充分性

- **实验数量**：从摘要可见，实验包括：
  - 模拟数据集实验。
  - 多种真实组织（免疫、脑、发育、再生）数据集实验，至少涉及四个不同组织场景。
- **充分性与客观性**：
  - 实验覆盖了多种组织类型，具有一定多样性，但未提及消融实验、参数敏感性分析、统计显著性检验等。
  - 对比方法未具体列出，缺少定量性能指标（如 AUC、F1、一致性系数等），评估标准较模糊（“恢复了空间一致的通讯结构”），客观性有待加强。
  - 总体而言，实验设计初步证明了方法有效性，但充分性一般，需要更多定量 benchmark。

### 6. 论文的主要结论与发现

- CellSTIC 能够在模拟和多样化真实组织中**恢复空间上一致的通讯结构域**。
- 揭示了**免疫、大脑、发育和再生**等关键生物学程序中的层级通讯模式。
- 提供了一个**通用框架**，用于从原位多组学数据中生成机制性假设，并支持跨组织/区域/状态的比较分析。

### 7. 优点：方法或实验设计上的亮点

- **多模态整合**：能同时整合转录组和蛋白组等空间多组学数据，充分利用互补信息。
- **层级可解释性**：输出从分子到功能模块的分层语义结构，避免了“配体-受体列表”的不可读性，便于生物学解读。
- **跨可比性**：支持不同组织、区域和细胞状态之间的通讯程序比较，有助于发现保守或特异性机制。
- **通用性**：适用于多种组织类型（免疫、神经、发育、再生），展示出广泛适用性。

### 8. 不足与局限

- **实验验证不够全面**：缺少与传统/最新方法的定量对比（如CellChat、NicheNet、SPOTlight等），未报告性能指标（精度、召回率等），结论主要基于定性观察。
- **计算资源未报告**：无法评估可重现性和实际应用成本。
- **未讨论数据质量影响**：空间多组学数据通常是稀疏、有噪声的，方法对噪声和缺失值的鲁棒性未提及。
- **应用限制**：框架依赖局部邻域定义，邻域大小的选择可能影响结果，文中未讨论该超参数敏感性。
- **生物学验证不足**：虽然称“恢复通讯结构域”，但缺乏功能实验或独立数据集的验证，结论仍为假设生成层面。

（完）
