---
title: "SpatialDataAgent: Autonomous Spatial Omics Data Curation at Decade Scale"
title_zh: SpatialDataAgent：十年尺度上的自主空间组学数据整理
authors: "Ji, J.-H., Zou, Q., Cheng, J., She, Z., Hao, Y., Liu, W., Zhang, D., Wang, Z., Yu, J.-T., Yuan, Z."
date: 2026-05-30
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.27.727615v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 自主整理空间转录组与组织学数据，促进癌症研究中的空间多组学整合
tldr: "空间组学数据归档中元数据碎片化导致大量多模态分子-组织学数据成为暗数据，难以被复用。本文提出SpatialDataAgent，一种结合模式约束证据评估与自优化标准化agent的自主策展工作流，无需人工干预即可完成数据标准化。应用于十年GEO记录，该框架识别出769对H&E-ST配对数据集，使高置信度A类配对数增加141%，总体规模较现有基线扩大6.4倍，并构建包含2920万个空间点的标准化数据湖HESRT。该工作为大规模多模态生物医学档案的自主策展提供了基于证据的可复现蓝图。"
source: biorxiv
selection_source: fresh_fetch
motivation: 空间组学数据元数据碎片化导致大量多模态分子-组织学数据成为暗数据，亟需自主策展方法。
method: 提出SpatialDataAgent，结合模式约束证据评估与自优化标准化agent，实现自主空间组学数据策展。
result: "应用于十年GEO记录，识别769对H&E-ST数据集，规模扩大6.4倍，高置信度A类配对数增加141%，构建含2920万点的HESRT数据湖。"
conclusion: 建立基于证据的自主策展蓝图，为大规模多模态生物医学档案的复用提供可复现框架。
---

## 摘要
空间组学档案中的碎片化元数据使得大量多模态分子-组织学数据作为暗数据无法访问。在这里，我们介绍了SpatialDataAgent，一个用于自主空间组学数据整理的代理工作流，结合了模式约束的证据评估与自我完善标准化代理。应用于十年的GEO记录，SpatialDataAgent识别出769个配对的H&E-空间转录组学（ST）数据集，比现有手动整理基线扩展了6.4倍。在基准测试窗口内，该框架实现了高置信度A类配对数据集的141%增长。我们进一步将近期的高置信度子集组装成HESRT，一个包含2920万个斑点/细胞的标准化数据湖，为多模态生物医学档案的基于证据的自主整理建立了蓝图。

## Abstract
Fragmented metadata in spatial omics archives has rendered large volumes of multimodal molecular-histological data inaccessible as  dark data. Here, we introduce SpatialDataAgent, an agentic workflow for autonomous spatial omics data curation, combining schema-constrained evidence evaluation with a self-refining standardization agent. Applied to a decade of GEO records, SpatialDataAgent identified 769 paired H&E-spatial transcriptomics (ST) datasets, representing a 6.4-fold scale expansion over existing manually curated baselines. Within the benchmarking window, the framework achieved a 141% increase in high-confidence Class A paired datasets. We further assembled a recent high-confidence subset into HESRT, a standardized datalake containing 29.2 million spots/cells, establishing a blueprint for evidence-grounded autonomous curation of multimodal biomedical archives.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：空间组学数据档案（如 GEO）中元数据碎片化严重，导致大量多模态分子-组织学数据（如 H&E 染色与空间转录组学配对数据）成为“暗数据”，无法被有效检索和复用。
- **研究动机**：现有手动整理基线规模小、效率低，亟需自动化、可扩展的策展方法以解锁这些沉睡的数据资源。
- **整体含义**：本文提出一种自主策展工作流，能够在不依赖人工干预的条件下，从大规模公共档案中系统性地发现并标准化配对的多模态空间组学数据，为后续大规模多模态整合分析奠定数据基础。

## 2. 论文提出的方法论：核心思想、关键技术细节
- **方法论名称**：SpatialDataAgent
- **核心思想**：结合 **模式约束的证据评估** 与 **自优化标准化 agent** 的自主策展工作流，无需人工干预即可完成数据标准化。
- **关键技术细节**（基于摘要推断）：
  - **模式约束证据评估**：利用预定义的元数据模式（schema）约束，自动评估记录是否属于 H&E-ST 配对数据，可能涉及文本匹配、语义推理等。
  - **自优化标准化 agent**：一个能自我完善（self-refining）的智能体，负责将原始元数据映射到统一标准格式，并随时间迭代优化映射规则。
  - **工作流流程**：输入 GEO 记录 → 证据评估筛选出潜在配对 → 标准化 agent 格式化元数据 → 输出高置信度配对数据集列表 → 进一步组装为数据湖。
- **公式/算法**：论文未提供具体公式，但核心逻辑可概括为：
  - 元数据检索 → 特征提取 → 规则匹配/学习 → 置信度评分 → 自动化标准化。

## 3. 实验设计：数据集、基准、对比方法
- **数据集**：
  - **主要数据源**：十年间（约 2016-2026）的 GEO（Gene Expression Omnibus）记录。
  - **构建的数据湖**：HESRT，包含 2920 万个斑点/细胞的标准化数据湖。
- **基准（Benchmark）**：
  - **现有手动整理基线**：未具体命名，但提到“现有手动整理基线”，规模较小。
  - **基准测试窗口**：特定时间窗口（可能为近期数据）用于评估增量效果。
- **对比方法**：仅与现有手动整理基线对比，未提及其他自动化方法。
- **主要结果**：
  - 识别出 **769 对** H&E-ST 配对数据集，规模扩大 **6.4 倍**。
  - 在基准测试窗口内，高置信度 A 类配对数增加 **141%**。

## 4. 资源与算力
- **未明确说明**：论文摘要和元数据中并未提及使用的 GPU 型号、数量、训练时长或其他算力消耗信息。推测其主要为元数据处理的 NLP/规则工作流，计算需求较低，但精确细节缺失。

## 5. 实验数量与充分性
- **实验数量**：主要表现为单一大型实验（处理十年 GEO 记录），并给出了三个关键指标（总配对数、扩增倍数、A 类增比）。
- **充分性评估**：
  - **充分方面**：覆盖了十年数据，规模宏大；有明确的基准对比（手动基线），结果量化清晰。
  - **不充分/局限方面**：
    - 未提及消融实验（如不同证据评估策略的对比）。
    - 未提供多机构或多数据源的交叉验证（仅针对 GEO）。
    - 未展示不同物种、不同技术平台（如 10x Visium, Slide-seq 等）上的泛化性能。
    - 基准测试窗口内的 141% 增长率缺乏更细粒度的分解（不同年份、不同提交者的影响）。
  - **客观性/公平性**：对比手动基线是合理的，但缺乏与同类自动化工具（若存在）的横向比较。

## 6. 论文的主要结论与发现
- **主要结论**：SpatialDataAgent 能够自主、高效地从十年 GEO 档案中策展出大规模、高置信度的 H&E-ST 配对数据集，规模较手动基线扩大 6.4 倍，并成功构建了包含 2920 万点的标准化数据湖 HESRT。
- **核心发现**：该框架为大规模多模态生物医学档案的基于证据的自主整理建立了可复现的蓝图，证明元数据碎片化问题可通过 agent 工作流得到有效缓解。

## 7. 优点：方法或实验设计上的亮点
- **自主性与可扩展性**：无需人工干预，可处理十年级别的大规模记录，具有很强的可重复性和扩展能力。
- **证据驱动**：采用模式约束的证据评估，提升了配对识别的可信度（区分高置信度 A 类）。
- **自我完善机制**：标准化 agent 支持自优化，能适应元数据格式的变化，具有长期实用性。
- **数据湖构建**：将策展结果直接转化为标准化数据湖（HESRT），便于下游分析复用，价值高。
- **成果可复现**：公开了框架蓝图（可能包括代码/规则），有利于社区验证和应用。

## 8. 不足与局限
- **实验覆盖不全面**：
  - 仅基于 GEO 一个数据源，未验证在 ArrayExpress、SpatialDB 等其它档案上的效果。
  - 未对不同空间组学技术（如 10x Visium, MERFISH, STARmap）分别评估，可能存在技术偏好。
- **偏差风险**：
  - 依赖 GEO 元数据的完整性/规范性，若元数据格式极其混乱，可能漏检或误检。
  - A 类高置信度定义可能隐含人类标注者的主观标准（未公开具体规则）。
- **应用限制**：
  - 仅针对 H&E-ST 配对这种特定模态，对其他多模态（如 IF-ST, IHC-ST）未涉及。
  - 未提供下游整合分析验证（例如利用 HESRT 数据湖复现已知生物学结果），实用性证据仅停留在数量指标上。
- **详细技术细节缺失**：由于论文仅提供摘要，核心 agent 的架构、训练（若涉及模型）、规则库规模等关键技术细节未知，无法全面评估其创新性和鲁棒性。
- **算力/效率未报告**：无法判断处理十年 GEO 记录所需的时间和计算成本，不利于其他研究复现或规模化部署。

（完）
