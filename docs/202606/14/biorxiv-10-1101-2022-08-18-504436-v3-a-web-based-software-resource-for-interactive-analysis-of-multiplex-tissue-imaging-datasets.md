---
title: A Web-based Software Resource for Interactive Analysis of Multiplex Tissue Imaging Datasets
title_zh: 一个基于网络的多重组织成像数据集交互分析软件资源
authors: "Creason, A. L., Watson, C., Gu, Q., Persson, D., Sargent, L. L., Chen, Y.-A., Lin, J.-R., Sivagnanam, S., Wünnemann, F., Nirmal, A. J., Chin, K., Feiler, H. S., Holly, H., Coussens, L. M., Schapiro, D., Grüning, B. A., Sorger, P. K., Sokolov, A., Goecks, J."
date: 2026-06-07
pdf: "https://www.biorxiv.org/content/10.1101/2022.08.18.504436v3.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 用于多重组织成像（空间蛋白质组学）分析的网络软件
tldr: 多重组织成像（MTI）可在原位解析单细胞空间蛋白表达，但数据分析复杂且缺乏易用工具。本文开发了Galaxy-ME，一个基于Web的交互式软件中心，集成了从数据预处理、单细胞分割到空间统计分析的完整流程。通过应用于CyTOF和CODEX等多种平台获取的正常和癌变组织数据，验证了其跨平台兼容性和实用性。Galaxy-ME作为公开资源，无需编程即可实现端到端分析，降低了空间蛋白质组学的研究门槛，有助于推动精准医学发现。
source: biorxiv
selection_source: fresh_fetch
motivation: MTI数据量大、格式多样，现有工具缺乏统一易用的Web平台，非计算专家难以独立完成数据分析。
method: Galaxy-ME提供基于Web的交互式界面，集成单细胞分割、聚类、表型鉴定及空间邻域分析等模块，支持端到端流程。
result: 成功应用于多种MTI平台（CyTOF、CODEX）的正常和肿瘤组织数据，高效识别细胞组成与空间分布差异。
conclusion: Galaxy-ME降低了MTI数据分析门槛，提供可复现的公共平台，促进空间蛋白质组学的广泛研究与应用。
---

## 摘要
高度多重组织成像（MTI）是强大的空间蛋白质组学技术，能够实现对组织的原位单细胞表征。然而，MTI数据集的分析和可视化仍然具有挑战性，我们开发了Galaxy-ME软件中心来应对这一挑战。Galaxy-ME是一个基于网络的交互式软件中心，能够实现对MTI数据集的端到端分析和可视化，并且对所有人开放。为了展示其效用，我们使用Galaxy-ME分析了从正常和癌变组织中多种MTI测定中获得的数据集。Galaxy-ME是一个公开可用的网络资源。

## Abstract
Highly multiplexed tissue imaging (MTI) are powerful spatial proteomics technologies that enable in situ single-cell characterization of tissues. However, analysis and visualization of MTI datasets remains challenging, and we developed the Galaxy-ME software hub to address this challenge. Galaxy-ME is a web-based, interactive software hub that enables end-to-end analysis and visualization of MTI datasets and is accessible to everyone. To demonstrate its utility, Galaxy-ME was used to analyze datasets obtained from multiple MTI assays in both normal and cancerous tissues. Galaxy-ME is a publicly available web resource.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：高度多重组织成像（MTI）是强大的空间蛋白质组学技术，能够在原位实现单细胞水平的组织表征。然而，MTI数据集的分析和可视化仍然面临挑战，缺乏统一、易用且无需编程的Web平台，非计算专家难以独立完成端到端分析。
- **整体含义**：开发并发布了一个名为**Galaxy-ME**的基于Web的交互式软件中心，旨在降低MTI数据分析门槛，推动空间蛋白质组学在精准医学中的广泛应用。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：提供一个公开可访问的Web资源，集成MTI数据从预处理到空间统计分析的完整工作流，实现端到端分析与可视化。
- **关键技术细节**（根据元数据中的`method`描述）：
  - 基于**Galaxy**平台（开源生物信息学工作流系统）构建，提供交互式Web界面。
  - 集成了**单细胞分割**、**聚类**、**表型鉴定**及**空间邻域分析**等模块。
  - 支持主流MTI平台（如CyTOF、CODEX）生成的数据。
  - 用户无需编程，通过浏览器即可完成全部分析流程，保证了可重复性。
- **公式或算法流程**：文中未给出具体公式或算法细节，仅描述了基于工作流的模块化设计。

## 3. 实验设计：使用的数据集、基准、对比方法

- **使用的数据集**：从**正常和癌变组织**中，使用**多种MTI测定**（包括CyTOF和CODEX）获得的数据集。具体样本数量、组织类型未详述。
- **基准（benchmark）**：未明确提及与现有工具进行量化对比。
- **对比方法**：未提供与其他软件（如HistoCAT、CellProfiler等）的直接比较，主要通过案例展示Galaxy-ME的实用性和跨平台兼容性。

## 4. 资源与算力

- **文中未明确说明**训练或分析所使用的GPU型号、数量、训练时长等算力信息。由于Galaxy-ME是一个基于Web的分析平台，通常不需要用户自己配置算力，但平台本身的部署资源未被提及。

## 5. 实验数量与充分性

- **实验数量**：根据摘要和元数据，仅描述了“使用Galaxy-ME分析了从正常和癌变组织中多种MTI测定获得的数据集”，未给出具体实验组数或消融实验。
- **充分性与客观性**：
  - 仅通过案例展示了基本功能和可行性，缺乏系统性的定量评估（如分割精度、聚类一致性、运行时间等）。
  - 未与现有方法进行基准对比，也未进行消融实验验证各模块的必要性。
  - 实验设计较为初步，充分性、客观性一般。

## 6. 论文的主要结论与发现

- Galaxy-ME成功应用于多种MTI平台（CyTOF、CODEX）的正常和肿瘤组织数据，能够高效识别细胞组成与空间分布差异。
- 作为公开可用的Web资源，Galaxy-ME降低了MTI数据分析门槛，使非计算专家也能独立完成分析，促进了空间蛋白质组学的广泛研究与应用。
- 平台支持端到端工作流，保证了可重复性和共享性。

## 7. 优点：方法或实验设计上的亮点

- **易用性**：基于Web的交互式界面，无需编程，对生物学家友好。
- **集成性**：将单细胞分割、聚类、表型鉴定和空间分析整合在一个平台内，避免了用户在不同工具间切换。
- **公开可访问**：作为公共资源，所有研究者均可免费使用，有利于研究的可重复性和协作。
- **跨平台兼容**：支持多种主流MTI技术（CyTOF、CODEX），具有较好的通用性。

## 8. 不足与局限

- **实验覆盖不足**：仅通过案例演示，未进行大规模、多对比的验证实验，缺乏定量性能评估。
- **偏差风险**：未与现有流行工具（如CellProfiler、HistoCAT、SpatialDE等）进行公平比较，难以客观评价其相对优势。
- **应用限制**：可能对超大规模数据集的处理性能（如内存、磁盘、运行时间）缺乏详细测试；未提及是否支持自定义分割算法或模型。
- **资源与算力信息缺失**：未报告平台运行所需的硬件配置或部署细节，用户无法评估实际使用成本。
- **算法透明度**：对于聚类、邻域分析等核心算法的具体参数和可选设置描述不足。

（完）
