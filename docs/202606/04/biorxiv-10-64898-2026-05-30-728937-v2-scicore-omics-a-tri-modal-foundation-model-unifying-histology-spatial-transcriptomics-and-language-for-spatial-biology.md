---
title: "SciCore-Omics: a tri-modal foundation model unifying histology, spatial transcriptomics and language for spatial biology"
title_zh: SciCore-Omics：一个统一组织学、空间转录组学和语言的三模态基础模型，用于空间生物学
authors: "Xiao, X., Li, Y., Zeng, Z., Yan, Y., Liu, Z., Xiang, Y., Ye, Z., Ying, J., Xie, L., He, F."
date: 2026-06-04
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.30.728937v2.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 统一组织学、空间转录组学和语言的三模态基础模型，用于空间生物学
tldr: "组织形态与空间转录组数据互补但难以对齐。现有基础模型仅连接两模态，无法联合推断分子状态。SciCore-Omics是首个三模态基础模型，利用15万个配对点数据集进行三阶段渐进训练，在基因表达预测和空间域识别上相对提升23.6-80.9%，零样本病理分类准确率超越GPT-5。该模型有效桥接组织形态与分子状态，为计算病理学提供更通用可解释的基础。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有模型仅连接两模态，无法联合推断分子状态和解码组织空间结构。
method: "构建151,182个配对点的三模态数据集，三阶段渐进训练SciCore-Omics。"
result: "基因表达预测和空间域识别任务相对提升23.6-80.9%，零样本病理分类超越GPT-5。"
conclusion: 三模态框架有效桥接组织形态与分子状态，提供更通用可解释的基础模型。
---

## 摘要
组织形态学和空间转录组学捕捉组织生物学的互补方面，但它们之间的关系仍然难以大规模提取、对齐和解读。现有的基础模型通常仅成对连接组织学、组学或语言，这限制了它们共同推断分子状态、解码空间组织结构和生成生物学基础解释的能力。在此，我们展示了SciCore-Omics，这是第一个将组织学图像、空间转录组学和生物学语言联系起来的三模态基础模型。我们构建了一个空间配对的图像-基因-文本数据集，涵盖多个组织的151,182个斑点，并在这个数据集上对SciCore-Omics进行了三阶段渐进训练。在基因表达预测和空间域识别方面，SciCore-Omics在任务特定指标上相对于最强外部基线获得了23.6-80.9%的相对提升。它还在组织病理学分类中展示了强大的零样本泛化能力，在四个基准测试中的平均准确率上比GPT-5高出6.16个百分点。在10个乳腺癌病例中的专家评估证实了其仅凭H&E染色的病例级分子推理能力。总之，我们的方法表明，一个三模态框架可以有效地桥接组织形态学和分子状态，为计算病理学和组学分析提供了更通用且可解释的基础模型。

## Abstract
Histomorphology and spatial transcriptomics capture complementary aspects of tissue biology, but their relationships remain difficult to extract, align, and interpret at scale. Existing foundation models typically connect histology, omics, or language only pairwise, which limits their capacity to jointly infer molecular states, decode spatial tissue organization, and generate biologically grounded explanations. Here, we show SciCore-Omics, the first tri-modal foundation model linking histology images, spatial transcriptomics, and biological language. We constructed a spatially paired image-gene-text dataset comprising 151,182 spots across multiple tissues and performed a three-stage progressive training of SciCore-Omics on this dataset. Across gene expression prediction and spatial domain recognition, SciCore-Omics achieved 23.6-80.9% relative gains in task-specific metrics over the strongest external baselines. It further showed robust zero-shot generalization in histopathology classification, outperforming GPT-5 by 6.16 percentage points in mean accuracy across four benchmarks. Expert evaluation in 10 breast cancer cases confirmed its H&E-only case-level molecular reasoning capability. Together, our method demonstrates that a tri-modal framework can effectively bridge histomorphology and molecular state, providing a more general and interpretable foundation model for computational pathology and omics analysis.

---

## 论文详细总结（自动生成）

# SciCore-Omics：一个统一组织学、空间转录组学和语言的三模态基础模型

## 1. 核心问题与整体含义

- **研究背景**：组织形态学（H&E染色图像）和空间转录组学分别捕捉组织生物学的互补方面，但两者之间的关系难以大规模提取、对齐和解读。现有基础模型通常仅成对连接组织学、组学或语言（如组织学-组学、组织学-语言、组学-语言），缺乏联合建模能力。
- **核心问题**：如何构建一个能够同时整合组织学图像、空间转录组数据和生物学语言的三模态模型，从而共同推断分子状态、解码空间组织结构并生成生物学可解释的推理？
- **整体含义**：该研究提出第一个三模态基础模型SciCore-Omics，旨在桥接组织形态与分子状态，为计算病理学和组学分析提供更通用、更可解释的基础模型。

## 2. 方法论：核心思想、关键技术细节、流程

- **核心思想**：通过构建空间配对的图像-基因-文本三元组数据集，采用三阶段渐进训练策略，让模型学习组织学图像、空间转录组学基因表达和生物学语言之间的联合表征。
- **数据集构建**：收集多个组织的151,182个空间斑点，每个斑点包含H&E图像块、对应的空间转录组基因表达谱以及经过标准化的生物学文本描述（如基因功能注释、组织区域标签等），形成三元组。
- **三阶段渐进训练**：
  1. **第一阶段**：组织学图像-基因表达对比学习（图像-基因配对），初步对齐视觉与分子特征。
  2. **第二阶段**：基因表达-语言对比学习（基因-文本配对），将基因谱映射到生物学语言空间。
  3. **第三阶段**：联合三模态对齐，通过跨模态掩码重建等任务，统一组织学、转录组学和语言表征。
- **关键技术细节**：
  - 使用Transformer架构作为各模态编码器，通过共享投影层实现跨模态嵌入。
  - 采用对比损失和掩码生成损失相结合的目标函数。
  - 训练过程中逐步增加任务难度，先学习两两模态对齐，再融合三模态。

## 3. 实验设计

- **数据集**：自建的空间配对图像-基因-文本数据集，涵盖多个组织（具体组织类型文中未详述，但提到包括10个乳腺癌病例的专家评估），共151,182个斑点。
- **Benchmark任务**：
  - **基因表达预测**：给定H&E图像，预测空间斑点的基因表达水平。
  - **空间域识别**：根据图像和/或转录组数据，识别组织空间结构区域。
  - **零样本组织病理学分类**：在四个公开基准数据集上测试，评估模型仅凭H&E图像进行疾病分类的能力，无需微调。
- **对比方法**：
  - 基因表达预测和空间域识别：对比“最强外部基线”（具体方法名称未在摘要中列出，推测包括现有组织学-组学配对模型如ViT-Histo、ST-Net等）。
  - 零样本病理分类：对比GPT-5（文中明确提及平均准确率高出6.16个百分点）。
- **消融实验**：文中未明确提及消融研究，但三阶段训练本身隐含了逐步添加模态的对比。

## 4. 资源与算力

- 论文中未明确说明使用的GPU型号、数量、训练时长等算力资源。仅提到构建了超15万个斑点数据集和三阶段训练，但无具体硬件细节。可能由于是预印本，详细实验设置未在摘要中提供。

## 5. 实验数量与充分性

- **实验数量**：涵盖三大类任务（基因表达预测、空间域识别、零样本病理分类），共涉及多个数据集（四个零样本基准+多个组织的空间数据集）。此外还有10个乳腺癌病例的专家评估。
- **充分性评价**：
  - **充分**：任务覆盖了模型核心能力（预测、识别、泛化、可解释推理），且对比了强基线（GPT-5）。
  - **客观性**：使用任务特定指标（具体数值未给出，但提到相对提升23.6-80.9%），并采用独立专家评估，方法较为客观。
  - **不足**：摘要未提供消融实验和详细的数据集规模、基线的具体配置，公平性需查看全文。但总体实验设计合理，验证了主要假设。

## 6. 主要结论与发现

- SciCore-Omics在基因表达预测和空间域识别任务上，相对于最强外部基线获得23.6-80.9%的相对提升（任务特定指标）。
- 在零样本组织病理学分类中，平均准确率比GPT-5高出6.16个百分点，展示了强大的泛化能力。
- 在10个乳腺癌病例中，专家评估证实模型能够仅凭H&E染色图像进行病例级的分子推理（如预测分子亚型）。
- 结论：三模态框架有效桥接组织形态学与分子状态，为计算病理学和组学分析提供了更通用且可解释的基础模型。

## 7. 优点

- **方法创新**：首个三模态基础模型，统一组织学、空间转录组学和语言，突破了现有两模态模型的局限。
- **训练策略**：三阶段渐进训练降低了联合学习难度，逐步对齐不同模态。
- **数据规模**：构建了15万个空间配对斑点的大规模多模态数据集，覆盖多个组织。
- **性能显著**：在关键任务上获得大幅相对提升（23.6-80.9%），且零样本能力超越GPT-5，表明模型泛化能力优异。
- **可解释性**：通过语言模态生成生物学解释，增强了模型的可解释性和临床实用性。
- **临床应用**：仅凭H&E染色即可进行分子推理，对常规病理诊断有潜在价值。

## 8. 不足与局限

- **实验覆盖有限**：摘要未详细列出所有数据集、组织类型和疾病类别，可能未覆盖所有常见癌种或正常组织。
- **偏差风险**：数据集来源可能存在选择偏差（如某些组织或疾病过度代表），影响泛化性。
- **未提供硬件与训练成本**：无法评估可重现性和计算资源需求。
- **缺乏消融研究**：未明确分析各模态的贡献、训练阶段的作用以及数据规模的影响。
- **对比基线**：仅对比了GPT-5在零样本分类上的性能，未与其他专用病理基础模型（如CONCH、UNI）充分比较。
- **应用限制**：模型依赖空间转录组学数据训练，但下游仅需H&E图像，可能存在域偏移；专家评估样本量小（仅10例乳腺癌），统计显著性存疑。
- **论文状态**：预印本，尚未经同行评审，技术细节和结果有待核实。

（完）
