---
title: "SubCell: Proteome-aware vision foundation models for microscopy capture single-cell biology"
title_zh: SubCell：面向显微成像的蛋白质组感知视觉基础模型，捕捉单细胞生物学
authors: "Gupta, A., Wefers, Z., Kahnert, K., Hansen, J. N., Misra, M. K., Leineweber, W. D., Cesnik, A., Lu, D., Axelsson, U., Ballllosera Navarro, F., Altman, R. B., Karaletsos, T., Lundberg, E."
date: 2026-06-08
pdf: "https://www.biorxiv.org/content/10.1101/2024.12.06.627299v3.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 蛋白组感知的视觉模型，用于捕捉显微镜图像中的蛋白质定位
tldr: 荧光显微镜图像可揭示细胞形态和蛋白质组织，但传统方法感知有限。本研究提出SubCell，一种蛋白质组感知的视觉基础模型，在Human Protein Atlas上训练，通过新颖学习目标准确捕获细胞形态和功能。SubCell在多项单细胞任务上超越现有方法，无需微调即可泛化至其他数据集，并构建了首个从图像直接学习的蛋白质组层次化图谱。结合蛋白质序列模型，SubCell实现多模态基因功能预测，优于单一模型。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有荧光显微镜图像分析方法难以充分捕获细胞形态、蛋白质定位及功能信息，需要能深入理解亚细胞组织的模型。
method: 在Human Protein Atlas全蛋白质组图像上，以蛋白质组感知为目标训练视觉基础模型SubCell，结合对比学习等策略。
result: SubCell在多种单细胞相关任务上超越先前方法，无需微调即可泛化；构建了从图像学习的蛋白质组层次化图谱，揭示蛋白质功能与动态行为；与序列模型融合提升基因功能预测。
conclusion: SubCell提供了深层图像驱动的细胞结构表示，可广泛应用于不同生物学场景和数据集。
---

## 摘要
细胞形态和亚细胞蛋白质组织为理解细胞功能和行为提供了重要见解。这些细胞特征可通过大规模荧光显微成像进行研究，而机器学习已成为解读所获图像以获取生物学洞察的强大工具。本文介绍SubCell，一种用于荧光显微成像的深度学习模型，旨在精准捕获细胞形态、蛋白质定位、细胞组织及生物学功能，其能力超越人类直接感知。SubCell基于人类蛋白质图谱的全蛋白质组图像集合，采用新颖的蛋白质组感知学习目标进行训练。在与单细胞生物学相关的多种任务中，SubCell优于现有最先进方法，并可泛化至其他荧光显微成像数据集而无需任何微调。此外，我们构建了首个直接从图像数据学习的全蛋白质组层次化组织图谱。这一基于视觉的多尺度细胞图谱定义了从细胞子系统到蛋白质复合物分辨率的层次结构，揭示具有相似功能的蛋白质，并区分细胞区室内的动态与稳定行为。最后，SubCell与蛋白质序列模型结合，可形成丰富的多模态方法，比单独使用视觉模型或序列模型能更好地捕获基因功能。总之，SubCell为细胞结构创造了深度、图像驱动的表征，可适用于多样化的生物学背景与数据集。

## Abstract
Cell morphology and subcellular protein organization provide important insights into cellular function and behavior. These cellular features can be studied using large-scale fluorescence microscopy, and machine learning has become a powerful tool to interpret the resulting images for biological insights. Here, we introduce SubCell, a deep learning model for fluorescence microscopy designed to accurately capture cellular morphology, protein localization, cellular organization, and biological function beyond what humans can readily perceive. SubCell was trained on the proteome-wide image collection from the Human Protein Atlas with a novel proteome-aware learning objective. SubCell outperforms state-of-the-art methods across a variety of tasks relevant to single-cell biology and generalizes to other fluorescence microscopy datasets without any fine-tuning. Additionally, we construct the first proteome-wide hierarchical map of proteome organization that is directly learned from image data. This vision-based multiscale cell map defines cellular subsystems down to protein complex resolution, reveals proteins with similar functions, and distinguishes dynamic and stable behaviors within cellular compartments. Finally, combining SubCell with a protein sequence model enables a rich multimodal approach to capture gene function better than either vision-only or sequence-only models alone. In conclusion, SubCell creates deep, image-driven representations of cellular architecture that are applicable across diverse biological contexts and datasets.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 核心问题与整体含义
- **研究动机**：荧光显微镜成像可揭示细胞形态和蛋白质亚细胞组织，但传统分析方法受限于人类直接感知能力，难以充分捕获蛋白质定位、细胞功能等深层信息。
- **背景**：大规模荧光成像（如人类蛋白质图谱）生成海量图像数据，机器学习尤其是视觉基础模型有望从中提取生物学洞察，但现有模型缺乏蛋白质组感知能力，且无法泛化到不同数据集。
- **整体含义**：本文提出SubCell模型，旨在构建一种深度、图像驱动的细胞结构表征，超越人类视觉感知，实现精准的细胞形态、蛋白质定位、组织及功能分析，并推动从图像到蛋白质功能预测的多模态融合。

## 2. 方法论核心思想与关键技术
- **核心思想**：在人类蛋白质图谱（Human Protein Atlas）的全蛋白质组图像集合上，训练一个蛋白质组感知的视觉基础模型，通过新颖的学习目标让模型理解蛋白质的亚细胞定位和组织模式。
- **关键技术**：
  - 采用对比学习等策略（具体算法未在摘要中详述，但提及“novel proteome-aware learning objective”）。
  - 模型架构为深度学习视觉模型（具体结构未提及）。
  - 可无需微调泛化至其他荧光显微镜数据集。
  - 与蛋白质序列模型（如ESM、ProtBERT等）结合，形成多模态方法，提升基因功能预测。
- **算法流程**（文字说明）：
  1. 输入：全蛋白质组荧光显微镜图像（Human Protein Atlas）。
  2. 训练：通过蛋白质组感知学习目标（可能包含对比学习、自监督或弱监督）优化模型参数。
  3. 输出：图像嵌入表示，可用于多个下游任务（如蛋白质定位分类、细胞形态分析、功能预测）。
  4. 扩展：利用学到的嵌入构建蛋白质组层次化图谱，并融合蛋白质序列嵌入进行多模态预测。

## 3. 实验设计
- **数据集**：
  - 主要：人类蛋白质图谱（Human Protein Atlas）的全蛋白质组图像集合。
  - 泛化：其他荧光显微镜成像数据集（未具体命名，但强调无需微调即可应用）。
- **Benchmark**：单细胞生物学相关的多项任务（未明确列出，但包括细胞形态、蛋白质定位、细胞组织、生物学功能等）。
- **对比方法**：现有最先进方法（state-of-the-art），具体名称未在摘要中给出。
- **评估指标**：未在摘要中说明，但声称SubCell优于先前方法。

## 4. 资源与算力
- **文中未明确说明**使用的GPU型号、数量、训练时长等计算资源信息。仅提及模型在Human Protein Atlas的全蛋白质组图像上训练，但未提供硬件细节。

## 5. 实验数量与充分性
- **实验数量**：涉及多项单细胞相关任务（但具体数量未列明），包括：
  - 与现有方法对比（多个任务）。
  - 泛化实验（不同数据集，无需微调）。
  - 构建层次化组织图谱（首个从图像学习的全蛋白质组图谱）。
  - 多模态融合实验（与蛋白质序列模型结合）。
- **充分性评估**：
  - 实验设计覆盖了主要任务（定位、形态、功能），并包含跨数据集泛化验证，较为全面。
  - 消融实验？未明确提及。
  - 可能存在的不足：未提供详细的统计显著性分析、具体任务指标数值，以及超参数敏感性分析，客观性和公平性难以从摘要完全判断。

## 6. 主要结论与发现
- SubCell在多种单细胞生物学任务上超越现有最先进方法。
- 可无需微调泛化至其他荧光显微镜数据集，展示强鲁棒性。
- 构建了首个直接从图像数据学习的全蛋白质组层次化组织图谱，定义了从细胞子系统到蛋白质复合物分辨率的多尺度结构。
- 该图谱能揭示相似功能蛋白质，并区分细胞区室内的动态与稳定行为。
- 与蛋白质序列模型结合的多模态方法在基因功能预测上优于单一视觉或序列模型。

## 7. 优点
- **创新性**：提出蛋白质组感知学习目标，使视觉模型捕获亚细胞蛋白质组织信息。
- **泛化能力**：无需微调即可应用于其他数据集，实用性强。
- **多尺度图谱**：首次从图像直接构建全蛋白质组层次化组织图谱，提供新生物学视角。
- **多模态融合**：与序列模型互补，提升功能预测能力。
- **任务覆盖广**：在细胞形态、定位、组织、功能等多个维度验证性能。

## 8. 不足与局限
- **硬件资源未公开**：无法评估训练成本和可复现性。
- **模型细节不透明**：具体架构、损失函数、训练策略等未在摘要中说明。
- **数据集单一性**：主要基于Human Protein Atlas，可能存在批次效应或特定细胞类型偏差（该图谱主要基于人类细胞系）。
- **缺少消融实验**：未明确证明各个设计组件的贡献。
- **泛化范围未定量**：跨数据集泛化效果的具体指标未给出。
- **功能预测验证有限**：仅提及基因功能预测改进，未深入讨论生物学验证（如敲除表型、疾病关联等）。
- **可能存在的风险**：模型可能学习到实验伪影而非真正生物学结构；与序列模型结合时，融合方法未详细解释。

（完）
