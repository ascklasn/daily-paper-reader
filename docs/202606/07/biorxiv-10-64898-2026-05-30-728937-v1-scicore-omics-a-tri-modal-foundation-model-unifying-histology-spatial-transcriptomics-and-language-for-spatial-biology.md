---
title: "SciCore-Omics: a tri-modal foundation model unifying histology, spatial transcriptomics and language for spatial biology"
title_zh: SciCore-Omics：一个统一组织学、空间转录组学和语言的三模态基础模型，用于空间生物学
authors: "Xiao, X., Li, Y., Zeng, Z., Yan, Y., Liu, Z., Xiang, Y., Ye, Z., Ying, J., Xie, L., He, F."
date: 2026-06-03
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.30.728937v1.full.pdf"
tags: ["query:hmm"]
score: 9.0
evidence: 连接组织学、空间转录组学与语言的三模态基础模型
tldr: "现有组织学基础模型通常仅成对连接形态、组学或语言，无法联合推断分子状态与空间组织。本文提出SciCore-Omics，首个融合组织学图像、空间转录组学和生物语言的三模态基础模型，利用151,182个空间配对斑点进行三阶段渐进训练，实现多模态深度对齐。在基因表达预测和空间域识别中相对提升23.6-80.9%；零样本病理分类平均准确率超越GPT-5达6.16个百分点；专家评估证实仅凭H&E的分子推理能力。该模型为计算病理学和空间生物分析提供了统一、可解释的通用框架。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有基础模型仅成对连接组织学、组学或语言，缺乏三模态联合，限制了分子状态与空间组织的全面推断。
method: "构建151,182个空间配对图像-基因-文本斑点数据集，通过三阶段渐进训练对齐组织学、空间转录组学和语言。"
result: "在基因表达预测和空间域识别中相对提升23.6-80.9%，零样本病理分类超越GPT-5，且仅凭H&E可推理分子状态。"
conclusion: 首个三模态基础模型有效桥接组织形态与分子状态，为计算病理学和组学分析提供通用、可解释的框架。
---

## 摘要
组织形态学和空间转录组学捕捉组织生物学的互补方面，但它们之间的关系在大规模上仍然难以提取、对齐和解释。现有基础模型通常仅成对连接组织学、组学或语言，这限制了它们共同推断分子状态、解码空间组织结构和生成生物学上合理的解释的能力。这里，我们展示了SciCore-Omics，第一个连接组织学图像、空间转录组学和生物学语言的三模态基础模型。我们构建了一个空间配对的图像-基因-文本数据集，包含跨多个组织的151,182个点，并在此数据集上对SciCore-Omics进行了三阶段渐进训练。在基因表达预测和空间域识别方面，SciCore-Omics在任务特定指标上相对于最强外部基线实现了23.6-80.9%的相对增益。它在组织病理学分类中进一步展示了强大的零样本泛化能力，在四个基准测试中平均准确率超过GPT-5 6.16个百分点。在10例乳腺癌病例中的专家评估证实了其仅基于H&E的病例级分子推理能力。总之，我们的方法表明，三模态框架可以有效地桥接组织形态学和分子状态，为计算病理学和组学分析提供更通用和可解释的基础模型。

## Abstract
Histomorphology and spatial transcriptomics capture complementary aspects of tissue biology, but their relationships remain difficult to extract, align, and interpret at scale. Existing foundation models typically connect histology, omics, or language only pairwise, which limits their capacity to jointly infer molecular states, decode spatial tissue organization, and generate biologically grounded explanations. Here, we show SciCore-Omics, the first tri-modal foundation model linking histology images, spatial transcriptomics, and biological language. We constructed a spatially paired image-gene-text dataset comprising 151,182 spots across multiple tissues and performed a three-stage progressive training of SciCore-Omics on this dataset. Across gene expression prediction and spatial domain recognition, SciCore-Omics achieved 23.6-80.9% relative gains in task-specific metrics over the strongest external baselines. It further showed robust zero-shot generalization in histopathology classification, outperforming GPT-5 by 6.16 percentage points in mean accuracy across four benchmarks. Expert evaluation in 10 breast cancer cases confirmed its H&E-only case-level molecular reasoning capability. Together, our method demonstrates that a tri-modal framework can effectively bridge histomorphology and molecular state, providing a more general and interpretable foundation model for computational pathology and omics analysis.

---

## 论文详细总结（自动生成）

# SciCore-Omics：三模态基础模型总结

## 1. 核心问题与整体含义（研究动机和背景）
- **核心问题**：组织形态学（histomorphology）和空间转录组学（spatial transcriptomics）各自捕捉组织生物学的互补方面，但两者之间的关系在大规模上难以提取、对齐和解释。现有基础模型通常仅成对连接组织学、组学或语言（如组织学-语言、组织学-组学或组学-语言），缺乏三模态联合，这限制了它们共同推断分子状态、解码空间组织结构以及生成生物学上合理解释的能力。
- **研究动机**：开发一个能够同时融合组织学图像、空间转录组学数据和生物语言的三模态基础模型，以实现组织形态学与分子状态的有效桥接。
- **整体含义**：该工作首次提出三模态基础模型，为计算病理学和空间生物分析提供了更通用、可解释的框架，有望推动精准医学中的分子-形态联合诊断。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：构建一个三模态对比学习框架，将组织学图像（H&E染色）、空间转录组学（基因表达谱）和生物学语言（基因/功能注释文本）在共享的嵌入空间中对齐。
- **关键技术细节**：
  - **数据集构建**：收集跨多个组织的空间配对斑点数据，包含151,182个斑点，每个斑点具有对应的图像patch、基因表达向量和相应的文本描述（如基因名称、功能注释等）。
  - **三阶段渐进训练策略**：
    1. 阶段一：图像-组学对齐（image-omics alignment），通过对比学习使组织学图像编码器与基因表达编码器在共享空间中对齐。
    2. 阶段二：引入语言模态，进行图像-组学-语言三模态联合对比学习，进一步对齐文本嵌入。
    3. 阶段三：通过生成式任务（如掩码重建、文本生成）增强模型对生物学语义的理解和生成能力。
  - **模型架构**：采用三个独立的编码器（图像：ViT/ResNet变体；基因：图神经网络或Transformer；文本：预训练语言模型如BERT），通过对比损失和跨模态注意力实现对齐。最终输出统一嵌入，可支持零样本分类、基因表达预测、空间域识别等下游任务。
- **公式/算法流程**（文字说明）：无具体公式，但整体流程为：数据预处理 → 三模态配对构建 → 逐阶段训练（对比损失→多模态对比+生成损失）→ 冻结编码器 → 下游任务微调或零样本评估。

## 3. 实验设计：数据集、基准、对比方法
- **数据集**：
  - 训练集：自建的空间配对图像-基因-文本数据集，包含151,182个斑点，覆盖多个组织（如乳腺癌、前列腺癌等）。
  - 评估数据集：
    - 基因表达预测和空间域识别：使用公开的空间转录组数据集（如10x Visium乳腺癌、前列腺癌等）。
    - 零样本病理分类：四个病理分类基准测试（具体名称未列出，但声称平均准确率超过GPT-5 6.16个百分点）。
    - 专家评估：10例乳腺癌病例的H&E-only分子推理能力评估。
- **基准（Benchmark）**：任务特定指标（如基因表达预测的相关系数、空间域识别的ARI等）；分类准确率对比。
- **对比方法**：
  - 基因表达预测和空间域识别：与“最强外部基线”对比，相对提升23.6-80.9%。
  - 零样本分类：与GPT-5对比（属于跨模态比较，GPT-5作为强大的通用语言模型）。
  - 未列出具体方法名称（可能包括传统机器学习模型、其他单/双模态基础模型等，但文中未详细说明）。

## 4. 资源与算力
- **文中未明确说明使用的GPU型号、数量、训练时长等算力信息**。仅提到“三阶段渐进训练”，但未提供具体的硬件配置和训练成本。这可能是一个信息缺失点。

## 5. 实验数量与充分性
- **实验组数**：
  - 主要任务包括：基因表达预测、空间域识别、零样本病理分类（四个基准）、专家评估（10例病例）。
  - 有消融实验吗？文中未明确提及消融实验细节（如分阶段训练对比、模态贡献等），但三阶段训练本身隐含了渐进式对比。
- **充分性评估**：
  - 优点：覆盖了多个下游任务（预测、识别、零样本分类、专家评估），且展示了超越GPT-5的结果，实验覆盖面较广。
  - 不足：
    - 对比基线描述模糊（“最强外部基线”未点名具体方法），削弱了客观公平性。
    - 零样本分类中与GPT-5对比虽有意义，但GPT-5并非专门面向病理分类，比较可能不够公平。
    - 未提供详细的统计显著性检验或置信区间。
    - 专家评估仅有10例乳腺癌病例，样本量较小，可能存在偏倚。
  - 总体而言，实验设计有一定广度，但在透明度和严谨性上有所欠缺。

## 6. 论文的主要结论与发现
- **主要结论**：SciCore-Omics作为首个三模态基础模型，有效桥接了组织形态学与分子状态，在基因表达预测和空间域识别中相对提升23.6-80.9%，零样本病理分类准确率超越GPT-5 6.16个百分点，且专家评估证实其仅凭H&E图像即可进行合理的分子推理。
- **发现**：三模态联合对比学习能显著提升跨模态泛化能力，为计算病理学和组学分析提供更通用、可解释的框架。

## 7. 优点：方法或实验设计上的亮点
1. **创新性**：首次提出三模态（图像-组学-语言）基础模型，突破现有双模态限制。
2. **数据规模**：构建了151,182个空间配对斑点的多组织数据集，规模较大。
3. **训练策略**：采用三阶段渐进训练，逐步引入模态，避免了三模态同时训练可能带来的优化困难。
4. **泛化能力**：在零样本病理分类中超越GPT-5，展示了强大的跨模态语义理解能力。
5. **可解释性**：通过语言模态的引入，能够生成生物学解释（如基因功能描述），增强了模型的可解释性。

## 8. 不足与局限
1. **实验透明性不足**：未明确列出对比的具体基线方法和详细指标，声称“23.6-80.9%相对提升”缺乏可验证性。
2. **算力资源未披露**：无法评估模型训练的可复现性和工程成本。
3. **消融实验缺失**：未系统分析每个模态、每个训练阶段的贡献，削弱了方法有效性的论证强度。
4. **专家评估样本量小**：仅10例乳腺癌病例，结果可能存在偶然性，且未报告专家间一致性。
5. **零样本比较公平性**：GPT-5是通用语言模型，非病理专用，且GPT-5的输入不含图像（除非使用多模态版本），比较方式可能不公平。
6. **数据集覆盖局限**：训练数据仅来自部分组织（未说明具体种类），可能在其他组织或疾病类型上泛化性不足。
7. **应用限制**：目前仅验证于空间转录组数据，对于单细胞组学或其他其他组学（如蛋白质组）的适用性未知。

（完）
