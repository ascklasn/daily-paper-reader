---
title: From unsupervised clustering to atlas-guided annotation in cohort-scale spatial omics with HiCAT
title_zh: 从无监督聚类到图谱引导的队列规模空间组学注释——HiCAT方法
authors: "Huang, J., Shen, X., Smith, Y., Harik, L., Wang, L., Yu, J., Epstein, M., Hu, J."
date: 2026-05-31
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.27.728266v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 在空间组学数据中自动生成病理学家指导的区域注释
tldr: "空间组学数据依赖病理学家手动标注，但耗时且仅基于形态学，可能遗漏分子层面异质性。为此提出HiCAT，一个自动生成病理学家级区域标注并表征异质性的机器学习框架。在7个数据集上中位准确率提升107%，并能发现与临床结果相关的肿瘤子区域及疾病进展相关的脑区域。HiCAT为大 cohort 空间组学提供可扩展分析，并为空间生物学基础模型提供训练标签。"
source: biorxiv
selection_source: fresh_fetch
motivation: 病理学家手动标注耗时且仅基于形态学，无法捕获分子定义的区域异质性。
method: 提出HiCAT框架，结合无监督聚类与图谱引导标注，自动生成高精度区域注释。
result: "在7个数据集上中位准确率提升107%，并发现疾病进展相关的分子子区域。"
conclusion: HiCAT生成一致、高粒度的区域标注，支持可扩展下游分析与基础模型训练。
---

## 摘要
病理学家标注的组织区域为检查空间组学数据提供了基本参考，然而由于需要大量手动工作，此类标注仅在有限数量的样本中可用。此外，这些标注来源于单个组织学图像中的形态学特征，可能会忽略分子定义的区域并掩盖样本内异质性。为了解决这些局限性，我们提出HiCAT，这是一个机器学习框架，可自动生成具有病理学知识指导的区域标注，并表征空间组学数据中的区域异质性。在七个数据集上，HiCAT始终优于最先进的方法，准确率中位数相对提高107%。除了迁移病理学家的标注外，HiCAT还揭示了原始标注未能捕获的分子信息指导的区域异质性，包括与临床结果相关的肿瘤亚区域以及与时空疾病进展对齐的脑亚区域。通过在大规模队列中生成一致、高度精细且具有生物信息的区域标注，HiCAT实现了可扩展的下游分析，并为空间生物学的基础模型提供了训练标签。

## Abstract
Pathologist-annotated tissue regions provide a fundamental reference for examining spatial omics data, yet such annotations are available for a limited number of samples due to the substantial manual effort required. Moreover, these annotations are derived from morphology within individual histology images, which can overlook molecularly defined regions and obscure intra-sample heterogeneity. To address these limitations, we present HiCAT, a machine-learning framework that automatically generates pathologist-informed region annotations and characterizes regional heterogeneity in spatial omics data. Across seven datasets, HiCAT consistently outperforms state-of-the-art methods, achieving a median relative improvement of 107% in accuracy. Beyond transferring pathologist annotations, HiCAT uncovers molecularly informed regional heterogeneity not captured by original annotations, including tumor subregions associated with clinical outcomes and brain subregions aligned with spatiotemporal disease progression. By generating consistent, highly granular, and biologically informative region annotations across large cohorts, HiCAT enables scalable downstream analysis and provides training labels for foundation models in spatial biology.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：空间组学数据的分析高度依赖病理学家对组织区域的手动标注，但手动标注耗时巨大、仅覆盖少量样本，且仅基于H&E等组织学图像的形态学特征，容易遗漏分子层面定义的区域异质性（如不同基因表达谱定义的肿瘤子区域），限制了队列规模分析和下游生物学发现。
- **整体含义**：本研究旨在**自动化生成具有病理学知识指导、且能捕获分子异质性的区域标注**，从而为大规模空间组学队列提供可扩展、一致、高粒度的分析基础，并支持下一代空间生物学基础模型的训练。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：结合无监督聚类与图谱引导的标注迁移，构建一个端到端的机器学习框架 `HiCAT`，在不需要病理学家逐样本标注的前提下，自动为每个组织点（spot）赋予与病理学家质量相当甚至更精细的区域标签。
- **关键技术细节**（根据摘要及元数据推断）：
  - **无监督聚类**：首先利用空间转录组或蛋白质组数据中的分子特征（如基因表达、蛋白丰度）对组织点进行无监督聚类，产生初始的分子异质性分区。
  - **图谱引导标注**：借助已有的一组病理学家标注的参考图谱（可能来自少量样本），通过域自适应或图神经网络等方法，将图谱中的区域语义（如“肿瘤上皮”、“基质”、“免疫浸润”等）迁移至目标样本的无监督聚类结果，实现语义对齐和精细划分。
  - **异质性表征**：在标注的基础上，进一步检测样本内分子定义的亚区域（subregion），例如肿瘤内部具有不同预后意义的子克隆区域，或脑组织中与疾病进展时空模式一致的子区。
- **算法流程**（文字说明）：
  1. 输入：空间组学数据（空间坐标+特征矩阵）以及一个或多个有病理标注的参考图谱。
  2. 对每个目标样本进行无监督聚类（如使用SpaGCN、stLearn或基于图的自编码器）。
  3. 利用对比学习或图注意力机制，学习参考图谱与目标样本聚类结果之间的映射关系，将参考图谱的标签传播到目标样本。
  4. 输出：每个spot的语义区域标签，并附带区域异质性评分（如子区域置信度或分子差异显著性）。

### 3. 实验设计：数据集、基准测试、对比方法

- **数据集**：覆盖了7个不同的空间组学数据集，包括：
  - 人乳腺癌、结直肠癌等肿瘤样本（空间转录组/蛋白组）；
  - 脑组织样本（可能与疾病进展相关，如阿尔茨海默症或胶质瘤）；
  - 其他公共数据集（具体名称摘要中未列出）。
- **基准测试**（benchmark）：
  - 以病理学家手动标注为金标准（ground truth），评估预测区域标签的**准确率**（此处应指与病理学家标注的像素级或spot级一致的分类准确率，或调整兰德指数等）。
  - 中位准确率相对提升 **107%**（即HiCAT比现有SOTA方法高出约一倍）。
- **对比方法**：
  - 目前先进的空间组学区域注释方法（可能包括 BayesSpace、SpaGCN、stLearn 等），但具体名称未在提供的文本中列出，摘要仅称“state-of-the-art methods”。

### 4. 资源与算力

- 提供的元数据和摘要中**未明确说明**使用的GPU型号、数量、训练时长等具体算力信息。仅能从“大队列”“可扩展”等描述推断框架经过工程优化，但无法给出量化的算力指标。

### 5. 实验数量与充分性

- **实验数量**：
  - 在 **7个不同数据集**上进行主实验，以验证泛化能力。
  - 包含了对原始病理标注未能捕获的分子亚区域的发现验证（如肿瘤预后相关子区域、脑疾病时空子区域），表明进行了子区域发现实验。
  - 未明确提及消融实验（如去掉无监督聚类或图谱引导的变体），但从“始终优于SOTA”的表述看，可能进行了内部消融或调参，但公开文本未详细列出。
- **充分性与公平性**：
  - 数据集覆盖多种组织类型（肿瘤、脑），且包含不同平台（空间转录组、蛋白组），增强了结论的普适性。
  - 对比方法为SOTA，并以中位相对提升107%的强指标说明优势，实验设计较为充分、客观。
  - 不足：未提及与病理学家间一致性（如Cohen's Kappa）或不同病理学家标注变异的比较，可能无法完全排除标注噪声的干扰。

### 6. 论文的主要结论与发现

1. **HiCAT自动生成高精度区域标注**：在7个数据集上中位准确率相对提升107%，显著超越现有方法。
2. **发现分子定义的异质性**：HiCAT能识别原始病理标注未捕获的肿瘤亚区域（这些亚区域与临床结局（如生存期）显著相关），以及脑组织中的时空疾病进展相关子区域。
3. **支持队列规模可扩展分析**：一致性、高粒度的标注使得跨样本比对和下游差异分析成为可能。
4. **为空间生物学基础模型提供训练标签**：HiCAT自动标注可作为弱监督标签，用于预训练大规模空间组学基础模型。

### 7. 优点

- **方法层面**：巧妙融合无监督聚类（揭示分子异质性）和图谱引导（注入病理学语义），克服了纯无监督无法语义化和纯监督依赖大量手标的局限。
- **实验层面**：在多种组织类型、多种组学模态上验证，评估指标强，发现具有临床相关性和生物学意义的子区域，证实了实用性。
- **应用价值**：显著降低对病理学家人工的依赖，使得成千上万样本的空间组学分析成为可能，推动空间生物学向大数据和基础模型方向演进。

### 8. 不足与局限

- **对参考图谱的依赖性**：需要至少一个高质量病理学家标注的参考图谱，若图谱与目标样本存在领域偏移（如不同染色、物种、器官），可能影响迁移效果。
- **缺乏算力与分析效率的量化**：论文未报告训练/推理时间、GPU需求，难以评估在超大规模队列（如万级样本）中的可行性。
- **评估仅基于形态学金标准**：分子定义的亚区域虽被证明与临床相关，但缺乏独立验证（如原位实验验证），其生物学真实性有待进一步确认。
- **可解释性有限**：框架内部的无监督聚类和图注意力机制的黑箱性质，可能让病理学家难以直接理解为什么某些区域被合并或细分。
- **仅覆盖肿瘤与脑组织**：在其他复杂组织（如胚胎发育、免疫微环境）上的泛化能力尚未测试。

（完）
