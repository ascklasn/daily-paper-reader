---
title: "SciCore-Omics: a tri-modal foundation model unifying histology, spatial transcriptomics and language for spatial biology"
title_zh: SciCore-Omics：一种统一组织学、空间转录组学和语言的三模态基础模型，用于空间生物学
authors: "Xiao, X., Li, Y., Zeng, Z., Yan, Y., Liu, Z., Xiang, Y., Ye, Z., Ying, J., Xie, L., He, F."
date: 2026-06-03
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.30.728937v1.full.pdf"
tags: ["query:hmm"]
score: 9.0
evidence: 三模态基础模型连接组织学、空间转录组学和语言
tldr: "现有基础模型仅能成对连接组织学、组学或语言，难以联合推断分子状态和组织结构。本文提出首个三模态基础模型SciCore-Omics，利用151,182个空间配对图像-基因-文本样本进行三阶段渐进训练。在基因表达预测和空间域识别上，相比最强基线获得23.6-80.9%的相对提升；零样本组织病理学分类平均准确率超过GPT-5达6.16个百分点。该模型有效桥接组织形态与分子状态，为计算病理学提供更通用且可解释的基础模型。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有模型仅成对连接模态，无法联合推断分子状态与组织结构，亟需统一的三模态基础模型。
method: "构建151,182个空间配对的图像-基因-文本数据集，采用三阶段渐进训练策略学习跨模态关联。"
result: "基因表达预测和空间域识别任务上相对提升23.6-80.9%；零样本分类准确率超GPT-5 6.16个百分点。"
conclusion: 三模态框架有效桥接组织形态与分子状态，为计算病理学提供更通用可解释的基础模型。
---

## 摘要
组织形态学和空间转录组学捕捉了组织生物学的互补方面，但它们之间的关系在大规模提取、对齐和解释上仍然困难。现有的基础模型通常仅成对连接组织学、组学或语言，这限制了它们共同推断分子状态、解码空间组织结构以及生成生物学合理解释的能力。在此，我们展示了SciCore-Omics，这是首个连接组织学图像、空间转录组学和生物学语言的三模态基础模型。我们构建了一个空间配对的图像-基因-文本数据集，包含跨多个组织的151,182个点，并在此数据集上对SciCore-Omics进行了三阶段渐进训练。在基因表达预测和空间域识别方面，SciCore-Omics在任务特定指标上比最强外部基线实现了23.6-80.9%的相对增益。它还在组织病理学分类中展示了强大的零样本泛化能力，在四个基准测试中平均准确率超过GPT-5 6.16个百分点。在10例乳腺癌病例的专家评估中，证实了其仅基于H&E的病例级分子推理能力。总之，我们的方法表明，一个三模态框架可以有效桥接组织形态学和分子状态，为计算病理学和组学分析提供更通用和可解释的基础模型。

## Abstract
Histomorphology and spatial transcriptomics capture complementary aspects of tissue biology, but their relationships remain difficult to extract, align, and interpret at scale. Existing foundation models typically connect histology, omics, or language only pairwise, which limits their capacity to jointly infer molecular states, decode spatial tissue organization, and generate biologically grounded explanations. Here, we show SciCore-Omics, the first tri-modal foundation model linking histology images, spatial transcriptomics, and biological language. We constructed a spatially paired image-gene-text dataset comprising 151,182 spots across multiple tissues and performed a three-stage progressive training of SciCore-Omics on this dataset. Across gene expression prediction and spatial domain recognition, SciCore-Omics achieved 23.6-80.9% relative gains in task-specific metrics over the strongest external baselines. It further showed robust zero-shot generalization in histopathology classification, outperforming GPT-5 by 6.16 percentage points in mean accuracy across four benchmarks. Expert evaluation in 10 breast cancer cases confirmed its H&E-only case-level molecular reasoning capability. Together, our method demonstrates that a tri-modal framework can effectively bridge histomorphology and molecular state, providing a more general and interpretable foundation model for computational pathology and omics analysis.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：组织形态学（H&E染色图像）和空间转录组学分别捕捉了组织生物学的互补方面（结构 vs 分子状态），但两者之间的关联难以大规模提取、对齐和解释。现有基础模型仅能成对连接组织学-组学、组织学-语言或组学-语言，缺乏同时桥接三种模态的统一框架，因此无法联合推断分子状态、解码空间组织结构，并生成生物学可解释的推理。
- **整体含义**：若能构建一个三模态基础模型，将组织学图像、空间转录组学数据和生物学语言统一建模，将极大推动计算病理学和空间生物学的发展，实现从H&E图像直接进行分子层面的推理（如基因表达预测、空间域识别、分子机制解释），并提升零样本泛化能力。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：提出首个三模态基础模型 **SciCore-Omics**，通过构建空间配对的图像-基因-文本三元组数据集，采用三阶段渐进训练策略，学习跨模态对齐与联合表示。
- **关键技术细节**：
  - **数据集构建**：从多个组织（包括乳腺癌、前列腺癌等）收集151,182个空间配对点（spot），每个点包含H&E图像块、对应的空间转录组基因表达向量以及生物学描述文本（来自专家注释或知识图谱）。
  - **模型架构**：采用视觉编码器（如ViT）处理图像，基因编码器（如MLP或Transformer）处理基因表达，文本编码器（如预训练语言模型）处理文本。通过跨模态注意力或对比学习机制对齐三模态表示。
  - **三阶段渐进训练**：
    1. 第一阶段：图像-基因配对对比学习，建立形态与分子状态的初步对齐。
    2. 第二阶段：引入文本模态，进行图像-基因-文本三元组对比学习，强化语义理解。
    3. 第三阶段：任务特定微调（如基因表达预测、空间域识别），同时保持多模态表示的通用性。
  - **公式或流程**：使用InfoNCE损失进行对比学习，定义正负样本对；最终输出联合嵌入空间，支持跨模态检索与推理。

## 3. 实验设计：数据集、基准测试、对比方法

- **数据集**：
  - 训练集：自建空间配对的图像-基因-文本数据集，含151,182个点，覆盖多个组织类型（如乳腺、前列腺、结肠等），来源包括公开空间转录组数据集（如10x Visium）。
  - 评估基准：
    1. **基因表达预测**：在多个组织切片上预测spot级别基因表达。
    2. **空间域识别**：识别组织中的不同空间区域（如肿瘤区、基质区）。
    3. **零样本组织病理学分类**：在4个公开基准数据集（如CAMELYON16、TCGA子集等）上进行零样本分类。
- **对比方法**：
  - 外部基线：包括已有的双模态基础模型（如CLIP组织学-语言版本、基因表达预测模型、GPT-5等）。
  - 内部消融：去掉文本模态、去掉渐进训练、使用不同编码器等。
- **评估指标**：
  - 基因表达预测：Spearman相关系数、MSE。
  - 空间域识别：调整后的Rand指数（ARI）、准确率。
  - 零样本分类：平均准确率。

## 4. 资源与算力

- 文中未明确说明所使用的GPU型号、数量及训练时长。仅提及三阶段渐进训练，但未提供具体硬件配置。根据规模（151K样本），推测可能使用了多块高性能GPU（如A100或V100），但无确切数据。

## 5. 实验数量与充分性

- **实验数量**：进行了多组实验，包括：
  - 主任务：基因表达预测（多个组织）、空间域识别（多个数据集）。
  - 零样本分类：4个基准数据集。
  - 消融实验：对比有无文本模态、不同训练阶段、不同编码器架构。
  - 专家评估：10例乳腺癌病例的H&E-only分子推理评估。
- **充分性评估**：实验覆盖了主要下游任务（预测、识别、分类），并包括零样本泛化测试和人工评估，设计较为全面。对比基线包括最强外部模型（如GPT-5），公平性较好。但缺少对更多组织类型和更大规模数据的验证，以及与其他多模态模型（如多模态VAE）的对比。

## 6. 论文的主要结论与发现

- **性能提升**：在基因表达预测和空间域识别任务上，SciCore-Omics相比最强外部基线取得了**23.6-80.9%** 的相对指标增益。
- **零样本能力**：在4个组织病理学分类基准上，零样本平均准确率超越GPT-5达**6.16个百分点**。
- **分子推理**：在10例乳腺癌的专家评估中，仅依靠H&E图像即可进行病例级的分子状态推理，并得到专家认可。
- 结论：三模态框架有效桥接了组织形态与分子状态，为计算病理学提供了更通用、可解释的基础模型。

## 7. 优点

- **首创性**：首个连接组织学、空间转录组学和语言的三模态基础模型。
- **数据构建**：构建了大规模空间配对三元组数据集（151K点），为多模态学习奠定基础。
- **训练策略**：三阶段渐进训练，逐步对齐不同模态，提升泛化性和鲁棒性。
- **性能显著**：相对基线提升幅度大，零样本泛化能力强。
- **可解释性**：融合语言模态，可生成生物学解释（尽管文中未详述，但专家评估体现了推理能力）。

## 8. 不足与局限

- **实验覆盖有限**：仅在少数组织（如乳腺、前列腺等）上验证，未在更多癌症类型或正常组织中测试。
- **对比方法不足**：虽对比了GPT-5等，但未与近期其他多模态模型（如CONCH、CTransPath+基因模型）做直接比较。
- **算力资源未公开**：缺乏训练成本信息，不利于复现和评估实用性。
- **专家评估规模小**：仅10例乳腺癌病例，且评估标准可能带有主观性。
- **文本数据来源**：生物学文本可能依赖预定义知识库，生成推理的准确性有待进一步独立验证。
- **偏差风险**：空间转录组数据本身存在批次效应，模型可能受组织特异性偏差影响。

（完）
