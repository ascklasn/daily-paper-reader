---
title: From unsupervised clustering to atlas-guided annotation in cohort-scale spatial omics with HiCAT
title_zh: 从无监督聚类到图谱引导的队列规模空间组学注释：HiCAT
authors: "Huang, J., Shen, X., Smith, Y., Harik, L., Wang, L., Yu, J., Epstein, M., Hu, J."
date: 2026-05-31
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.27.728266v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 空间组学注释框架
tldr: "空间组学数据缺乏大规模病理注释，且传统注释仅基于形态学，忽略分子定义区域。HiCAT框架通过无监督聚类和图谱引导自动生成高精度区域注释，在7个数据集上中位准确率提升107%，并发现临床相关的肿瘤亚区和脑区时空进展异质性。该方法为大规模队列分析提供一致、高分辨率的生物学注释，并为空间生物学基础模型提供训练标签。"
source: biorxiv
selection_source: fresh_fetch
motivation: 病理注释费时且仅基于形态学，忽略分子定义区域和样本内异质性。
method: HiCAT结合无监督聚类与图谱引导，自动生成病理学家级别的区域注释。
result: "在7个数据集上中位准确率提升107%，并发现临床相关的肿瘤和脑区亚型。"
conclusion: HiCAT提供可扩展、高分辨率的区域注释，支持下游分析与基础模型训练。
---

## 摘要
病理学家注释的组织区域为检查空间组学数据提供了基本参考，但由于需要大量人工努力，此类注释仅适用于有限数量的样本。此外，这些注释源于单个组织学图像中的形态学，可能忽略分子定义的区域并掩盖样本内异质性。为解决这些局限性，我们提出了HiCAT，这是一个机器学习框架，可自动生成基于病理学家知识的区域注释并表征空间组学数据中的区域异质性。在七个数据集上，HiCAT始终优于最先进的方法，准确率中位数相对提高107%。除了迁移病理学家的注释外，HiCAT还揭示了原始注释未捕获的分子层面区域异质性，包括与临床结果相关的肿瘤亚区和与时空疾病进展一致的大脑亚区。通过在大规模队列中生成一致、高度精细且具有生物学信息的区域注释，HiCAT实现了可扩展的下游分析，并为空间生物学的基础模型提供了训练标签。

## Abstract
Pathologist-annotated tissue regions provide a fundamental reference for examining spatial omics data, yet such annotations are available for a limited number of samples due to the substantial manual effort required. Moreover, these annotations are derived from morphology within individual histology images, which can overlook molecularly defined regions and obscure intra-sample heterogeneity. To address these limitations, we present HiCAT, a machine-learning framework that automatically generates pathologist-informed region annotations and characterizes regional heterogeneity in spatial omics data. Across seven datasets, HiCAT consistently outperforms state-of-the-art methods, achieving a median relative improvement of 107% in accuracy. Beyond transferring pathologist annotations, HiCAT uncovers molecularly informed regional heterogeneity not captured by original annotations, including tumor subregions associated with clinical outcomes and brain subregions aligned with spatiotemporal disease progression. By generating consistent, highly granular, and biologically informative region annotations across large cohorts, HiCAT enables scalable downstream analysis and provides training labels for foundation models in spatial biology.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：空间组学数据通常依赖病理学家手动注释组织区域，但人工注释成本高昂、仅限于少量样本，且仅基于组织学形态，可能忽略分子定义的区域，掩盖样本内的异质性。
- **研究动机**：开发一个自动化的、可扩展的框架，能够生成病理学家水平的区域注释，同时揭示分子层面的区域异质性，以支持大规模队列分析和空间生物学基础模型训练。
- **整体意义**：HiCAT 通过无监督聚类与图谱引导的结合，将注释从人工、形态学依赖转变为自动化、分子信息增强的过程，显著提升注释的一致性和分辨率。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：HiCAT 是一个机器学习框架，将无监督聚类与图谱引导的迁移学习相结合，自动生成具有病理学知识的区域注释，并表征区域异质性。
- **关键技术细节**（基于摘要推测，原文未提供完整流程）：
  - 首先对空间组学数据进行无监督聚类（如使用空间转录组或蛋白质组特征），识别分子层面定义的区域。
  - 然后利用来自少量人工注释样本的病理学知识图谱，将聚类结果映射到可解释的病理区域标签。
  - 框架可能包含空间隐式正则化或图神经网络以保留空间邻近性。
  - 最终输出高分辨率、一致的区域注释，同时检测原始注释未覆盖的亚区。
- **公式或算法流程**：未在摘要中给出具体公式，仅描述为“结合无监督聚类与图谱引导”。

## 3. 实验设计

- **数据集/场景**：涉及 **7 个数据集**，涵盖肿瘤和脑组织等不同空间组学平台（具体名称未列出）。
- **Benchmark**：与多种“最先进方法”比较（具体方法名称未给出）。
- **对比方法**：未详细说明，但声明中位准确率相对提升 **107%**。
- **评价指标**：主要使用准确率（accuracy），可能还包括其他区域一致性指标。

## 4. 资源与算力

- 原文摘要及元数据中**未明确说明**使用的 GPU 型号、数量、训练时长等算力信息。因此无法总结该部分内容。

## 5. 实验数量与充分性

- **实验组数**：在 7 个数据集上进行了主实验（每个数据集可能包含多个样本和不同注释任务）。此外提及“发现临床相关的肿瘤亚区和脑区时空进展异质性”，暗示有下游分析实验。
- **充分性与公平性**：
  - **优点**：涵盖多种组织类型（肿瘤、脑）和多个数据集，增强了泛化性。
  - **不足**：未报告详细的交叉验证、统计显著检验、消融实验或与人类专家的一致性评估（如 Cohen's Kappa）。缺乏对方法超参数敏感性的分析。由于对比方法名称未公布，无法判断是否包含足够强的基线。总体而言，实验数量足够但细节缺失，公平性依赖未公开信息。

## 6. 主要结论与发现

- **性能提升**：在 7 个数据集上中位准确率相对提升 107%，持续优于现有方法。
- **发现新区域**：HiCAT 揭示了原始人工注释未捕获的分子层面区域异质性：
  - 肿瘤样本中发现了与临床结果相关的亚区。
  - 大脑样本中发现了与时空疾病进展一致的亚区。
- **可扩展性**：可用于大规模队列生成一致注释，为空间生物学基础模型提供训练标签。

## 7. 优点

- **自动化程度高**：无需密集的人工注释，即可生成病理学家级别的区域标签。
- **分子-形态融合**：超越纯形态学，整合分子信息（如基因表达或蛋白丰度），发现新的生物学相关亚区。
- **一致性**：跨样本、跨队列生成统一标准的区域注释，适合下游批量分析。
- **通用性**：在 7 个不同数据集上验证，覆盖多组织和平台。

## 8. 不足与局限

- **方法细节披露不足**：原文仅提供摘要，核心算法（如具体聚类方法、图谱构建方式、损失函数等）未公开，难以复现和评估。
- **算力资源未报告**：无法判断方法的计算开销和可部署性。
- **实验完整性欠缺**：缺少消融实验、与人类专家的一致性评估（如 Kappa 值）、统计显著检验、超参数分析、失败案例分析。
- **对比方法不明确**：未列出具体基线方法及参数设置，难以判断比较的公平性。
- **偏差风险**：可能依赖特定病理知识图谱的领域，图谱偏差会直接影响结果；未讨论对罕见区域的识别能力。
- **应用限制**：仅基于摘要，未提及对不同空间分辨率的适应性、对噪声数据的鲁棒性，以及需要多少人工注释种子样本。

（完）
