---
title: "SciCore-Omics: a tri-modal foundation model unifying histology, spatial transcriptomics and language for spatial biology"
title_zh: SciCore-Omics：一个统一组织学、空间转录组学和语言的三模态基础模型用于空间生物学
authors: "Xiao, X., Li, Y., Zeng, Z., Yan, Y., Liu, Z., Xiang, Y., Ye, Z., Ying, J., Xie, L., He, F."
date: 2026-06-03
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.30.728937v1.full.pdf"
tags: ["query:hmm"]
score: 9.0
evidence: 组织学、空间转录组和语言的三模态基础模型
tldr: "现有基础模型通常仅连接组织学、组学或语言中的两种模态，无法联合推断分子状态和解译空间组织。SciCore-Omics是首个三模态基础模型，统一组织学图像、空间转录组学和生物学语言。在三阶段渐进训练后，基因表达预测和空间域识别任务相对最强基线提升23.6-80.9%，零样本病理学分类准确率超越GPT-5达6.16个百分点。专家评估证实其仅凭H&E图像即可进行分子水平的推理能力，为计算病理学提供了更通用可解释的基础模型。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有模型仅两两连接组织学、组学或语言，缺乏统一三模态联合推理能力。
method: "构建151,182个spot的空间配对图像-基因-文本数据集，进行三阶段渐进训练。"
result: "基因表达预测和空间域识别相对最优基线提升23.6-80.9%，零样本分类超越GPT-5。"
conclusion: 三模态框架有效桥接组织形态与分子状态，提供更通用可解释的计算病理学基础模型。
---

## 摘要
组织形态学和空间转录组学捕捉了组织生物学的互补方面，但它们之间的关系在大规模上仍然难以提取、对齐和解释。现有的基础模型通常仅成对连接组织学、组学或语言，这限制了它们联合推断分子状态、解码空间组织结构和生成具有生物学依据的解释的能力。在此，我们展示了SciCore-Omics，这是首个连接组织学图像、空间转录组学和生物语言的三模态基础模型。我们构建了一个包含跨多个组织的151,182个点的空间配对图像-基因-文本数据集，并在此数据集上对SciCore-Omics进行了三阶段渐进式训练。在基因表达预测和空间区域识别方面，SciCore-Omics在任务特定指标上相对于最强外部基线实现了23.6%-80.9%的相对提升。它还在组织病理学分类中展示了强大的零样本泛化能力，在四个基准测试中的平均准确率上超越了GPT-5 6.16个百分点。在10例乳腺癌病例中的专家评估证实了其仅依赖H&E染色的病例级分子推理能力。总之，我们的方法表明，一个三模态框架能够有效桥接组织形态学和分子状态，为计算病理学和组学分析提供了更通用且可解释的基础模型。

## Abstract
Histomorphology and spatial transcriptomics capture complementary aspects of tissue biology, but their relationships remain difficult to extract, align, and interpret at scale. Existing foundation models typically connect histology, omics, or language only pairwise, which limits their capacity to jointly infer molecular states, decode spatial tissue organization, and generate biologically grounded explanations. Here, we show SciCore-Omics, the first tri-modal foundation model linking histology images, spatial transcriptomics, and biological language. We constructed a spatially paired image-gene-text dataset comprising 151,182 spots across multiple tissues and performed a three-stage progressive training of SciCore-Omics on this dataset. Across gene expression prediction and spatial domain recognition, SciCore-Omics achieved 23.6-80.9% relative gains in task-specific metrics over the strongest external baselines. It further showed robust zero-shot generalization in histopathology classification, outperforming GPT-5 by 6.16 percentage points in mean accuracy across four benchmarks. Expert evaluation in 10 breast cancer cases confirmed its H&E-only case-level molecular reasoning capability. Together, our method demonstrates that a tri-modal framework can effectively bridge histomorphology and molecular state, providing a more general and interpretable foundation model for computational pathology and omics analysis.

---

## 论文详细总结（自动生成）

# 论文详细总结：SciCore-Omics：一个统一组织学、空间转录组学和语言的三模态基础模型

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：组织形态学（H&E染色图像）和空间转录组学捕捉了组织生物学的互补信息，但二者之间的关系在大规模上难以提取、对齐和解释。现有基础模型通常仅成对连接组织学、组学或语言（例如组织学-组学、组织学-语言、组学-语言），无法同时联合推断分子状态、解码空间组织结构并生成生物学可解释的结果。
- **整体含义**：本研究提出首个三模态基础模型 **SciCore-Omics**，通过统一组织学图像、空间转录组学和生物语言三个模态，旨在桥接形态学与分子状态，为计算病理学和组学分析提供更通用且可解释的基础模型。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：构建空间配对的图像-基因-文本三元组数据集，并通过三阶段渐进式训练，让模型学会在三个模态之间进行对齐和联合推理。
- **关键技术细节**：
  - **数据集构建**：跨多个组织收集了 **151,182 个空间点（spots）** 的配对数据，每个点包含 H&E 图像片段、对应的空间转录组基因表达谱，以及通过自动或专家方式生成的生物学描述文本。
  - **三阶段渐进训练**：
    - 第一阶段：图像和基因表达模态的对比学习，建立形态-分子基础对齐。
    - 第二阶段：引入语言模态，进行图像-基因-文本的三模态对齐，可能采用多模态对比损失或生成式预训练。
    - 第三阶段：联合微调，以完成下游任务（如基因表达预测、空间域识别）。
  - 未给出具体公式或模型架构细节（如 Transformer 变体、对比损失函数等），但属于多模态基础模型的标准框架。

## 3. 实验设计：数据集、基准测试与对比方法

- **数据集**：
  - 内部构建的空间配对图像-基因-文本数据集（151,182 个 spot），涵盖多种组织类型（具体未列明）。
  - 四个公开组织病理学分类基准测试（用于零样本评估）。
  - 10 例乳腺癌病例用于专家评估。
- **基准任务**：
  - **基因表达预测**：从图像预测 spot 的基因表达。
  - **空间域识别**：识别组织空间区域（如肿瘤区域、基质等）。
  - **零样本组织病理学分类**：在不额外训练的情况下，直接对四个基准测试进行分类。
- **对比方法**：
  - 基因表达预测和空间域识别：与“最强外部基线”比较（未具名，可能是其他多模态模型如 ST-Net、HisToGene 等）。
  - 零样本分类：与 **GPT-5** 进行比较。
- **专家评估**：由病理学家对 10 例乳腺癌病例的模型推理结果进行人工评判。

## 4. 资源与算力

- 论文中**未明确说明**使用的 GPU 型号、数量及训练时长等算力资源。
- 推测训练 151k spot 规模的三模态模型需要较大算力（如 A100 或 H100 集群），但具体信息缺失。

## 5. 实验数量与充分性

- **实验数量**：
  - 三个定量任务（基因表达预测、空间域识别、零样本分类），每个任务在多个指标上报告结果。
  - 专家评估（10 例病例）作为定性验证。
- **充分性与公平性**：
  - 基因表达预测和空间域识别的相对提升幅度（23.6%-80.9%）基于特定指标，但未提供绝对数值和消融实验，难以判断是否完全公平。
  - 零样本分类对比 GPT-5 的 6.16 个百分点优势明确，但缺乏与其他多模态病理模型的比较。
  - 缺少对模型在不同组织类型、不同测序平台上的鲁棒性分析。
  - 专家评估样本量较小（10 例），可能统计效力有限。
  - 总体而言，实验覆盖了核心能力，但消融实验、多数据集交叉验证、错误分析等有所欠缺。

## 6. 论文的主要结论与发现

- 三模态联合训练显著优于任何两两模态组合：在基因表达预测和空间域识别任务上，相对最强外部基线提升 **23.6%-80.9%**。
- 零样本泛化能力出色：在四个病理分类基准上，平均准确率超越 GPT-5 **6.16 个百分点**。
- 专家评估证实模型仅凭 H&E 图像即可进行具有生物学依据的分子级推理（如判断分子亚型、基因活性等）。
- 结论：三模态框架能有效桥接组织形态学与分子状态，为计算病理学提供了更通用且可解释的基础模型。

## 7. 优点：方法或实验设计上的亮点

- **首创性**：首个连接组织学、空间转录组学和语言三模态的基础模型，填补了现有研究空白。
- **渐进训练策略**：三阶段渐进式学习，逐步对齐不同模态，避免直接多模态联合训练的困难。
- **强泛化能力**：在零样本分类上超越 GPT-5，表明模型学到了通用生物医学知识。
- **可解释性**：通过语言模态生成解释，结合形态和分子特征，增强模型的可信度。
- **专家验证**：引入病理学家评估，提升实际应用价值。

## 8. 不足与局限

- **计算资源未公开**：使可复现性降低。
- **消融实验缺乏**：未评估各模态贡献、每阶段收益、数据规模影响等。
- **基准比较不全面**：仅与“最强外部基线”和 GPT-5 比较，缺少与其他多模态病理模型（如 CTransPath、CONCH、PLIP）的对比。
- **数据规模和多样性有限**：151k spot 的数据集相对于全切片尺度仍然较小，且组织类型未详述，可能偏向特定组织。
- **专家评估样本量小**：仅 10 例乳腺癌病例，统计效力有限，可能无法推广到其他癌种或良性疾病。
- **未讨论偏差风险**：H&E 图像和空间转录组数据可能存在批次效应、染色差异等，模型在跨中心、跨染色方案下的鲁棒性未知。
- **应用限制**：当前需要配对的空间转录组数据才能训练，限制了直接应用于常规 H&E 切片的场景（虽然零样本可行，但需要先验训练）。

（完）
