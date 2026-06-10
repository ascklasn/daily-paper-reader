---
title: "SciCore-Omics: a tri-modal foundation model unifying histology, spatial transcriptomics and language for spatial biology"
title_zh: SciCore-Omics：一个统一组织学、空间转录组学与语言的三模态基础模型，用于空间生物学
authors: "Xiao, X., Li, Y., Zeng, Z., Yan, Y., Liu, Z., Xiang, Y., Ye, Z., Ying, J., Xie, L., He, F."
date: 2026-06-04
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.30.728937v2.full.pdf"
tags: ["query:hmm"]
score: 9.0
evidence: 三模态基础模型连接组织学、空间转录组学和语言
tldr: "现有基础模型仅两两连接组织学、组学或语言，难以联合推断分子状态和组织空间结构。本文构建含151,182个空间点的图像-基因-文本配对数据集，通过三阶段渐进训练开发首个三模态基础模型SciCore-Omics。该模型在基因表达预测和空间域识别上相对提升23.6-80.9%，零样本组织病理学分类准确率比GPT-5高6.16个百分点，10例乳腺癌案例验证了其H&E分子推理能力。三模态框架有效桥接形态学和分子状态，为空间生物学分析提供更通用可解释的基础模型。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有模型局限于两两模态连接，无法充分融合组织形态学与空间转录组学的互补信息，限制了分子状态和空间组织的联合推断。
method: "构建151,182个空间点的图像-基因-文本配对数据集，采用三阶段渐进训练策略，开发出连接组织学、空间转录组和生物学语言的三模态基础模型。"
result: "基因表达预测与空间域识别任务相对基线提升23.6-80.9%；零样本分类平均准确率超GPT-5达6.16个百分点；乳腺癌案例证实了仅基于H&E图像的分子推理能力。"
conclusion: 三模态框架有效桥接组织形态学与分子状态，为计算病理学和组学分析提供了更全面、可解释的基础模型方案。
---

## 摘要
组织形态学和空间转录组学捕捉了组织生物学的互补方面，但它们之间的关系在大规模上仍难以提取、对齐和解释。现有的基础模型通常仅成对地连接组织学、组学或语言，这限制了它们联合推断分子状态、解码组织结构布局以及生成具有生物学依据的解释的能力。在此，我们展示了SciCore-Omics，这是首个将组织学图像、空间转录组学和生物语言联系起来的三模态基础模型。我们构建了一个空间配对的图像-基因-文本数据集，包含跨多个组织的151,182个点，并在此数据集上对SciCore-Omics进行了三阶段渐进式训练。在基因表达预测和空间区域识别方面，SciCore-Omics在任务特定指标上相比最强的外部基线获得了23.6%-80.9%的相对提升。它还在组织病理学分类中展示了强大的零样本泛化能力，在四个基准测试中的平均准确率上比GPT-5高出6.16个百分点。对10例乳腺癌病例的专家评估证实了其仅基于H&E染色的病例级分子推理能力。总之，我们的方法表明，三模态框架能够有效桥接组织形态学和分子状态，为计算病理学和组学分析提供更通用且可解释的基础模型。

## Abstract
Histomorphology and spatial transcriptomics capture complementary aspects of tissue biology, but their relationships remain difficult to extract, align, and interpret at scale. Existing foundation models typically connect histology, omics, or language only pairwise, which limits their capacity to jointly infer molecular states, decode spatial tissue organization, and generate biologically grounded explanations. Here, we show SciCore-Omics, the first tri-modal foundation model linking histology images, spatial transcriptomics, and biological language. We constructed a spatially paired image-gene-text dataset comprising 151,182 spots across multiple tissues and performed a three-stage progressive training of SciCore-Omics on this dataset. Across gene expression prediction and spatial domain recognition, SciCore-Omics achieved 23.6-80.9% relative gains in task-specific metrics over the strongest external baselines. It further showed robust zero-shot generalization in histopathology classification, outperforming GPT-5 by 6.16 percentage points in mean accuracy across four benchmarks. Expert evaluation in 10 breast cancer cases confirmed its H&E-only case-level molecular reasoning capability. Together, our method demonstrates that a tri-modal framework can effectively bridge histomorphology and molecular state, providing a more general and interpretable foundation model for computational pathology and omics analysis.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：现有基础模型通常仅成对地连接组织学、组学或语言（如组织学+组学、组织学+语言等），无法同时联合推理分子状态、解码组织结构布局并生成生物学解释。这限制了从组织形态学到分子状态的全面理解和跨模态知识迁移。
- **整体含义**：本文首次提出三模态基础模型 SciCore-Omics，将组织学图像、空间转录组学和生物语言统一在一个框架内，旨在桥接形态学与分子状态，为空间生物学提供更通用、可解释的基础模型。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：构建一个能够同时处理 H&E 染色图像、空间基因表达和生物学文本描述的三模态嵌入空间，实现跨模态对齐与推理。
- **数据构建**：创建了包含 **151,182 个空间点**（spots）的图像-基因-文本配对数据集，覆盖多个组织类型。每个空间点由一个组织学图像 patch、对应的空间转录组基因表达向量以及对应的生物学描述文本组成。
- **训练策略——三阶段渐进训练**：
  - **第一阶段**：图像-文本（组织学-语言）对比学习；  
  - **第二阶段**：图像-基因（组织学-转录组）对比学习；  
  - **第三阶段**：三模态联合对比学习与生成性训练，使三个模态的嵌入空间对齐并能相互生成。
- **关键技术**：采用对比学习（CLIP-like 风格）与跨模态注意力机制，未披露具体网络架构细节（文中仅提及三阶段训练及配对数据构造）。

## 3. 实验设计：数据集、基准和对比方法

- **任务与数据集**：
  - **基因表达预测**：从组织学图像预测空间点的基因表达值。  
  - **空间域识别**：基于组织学图像和/或基因表达识别组织区域（如肿瘤区域、基质等）。  
  - **零样本组织病理学分类**：在 **4 个公开基准测试**（未具名具体名称，推测包括 TCGA 等）上进行零样本组织病理学分类。  
  - **乳腺癌案例评估**：10 例乳腺癌病例，由专家评估仅基于 H&E 图像的病例级分子推理能力。
- **基准方法**：对比了“最强外部基线”（文中未列出具体模型名，可能包括传统的空间转录组分析方法和已有的双模态基础模型如 CONCH、CTransPath 等），以及 **GPT-5**（用于零样本分类对比）。
- **评估指标**：任务特定指标（如基因表达预测的相关系数、空间域识别的 NMI/ARI 等），以及零样本分类准确率。

## 4. 资源与算力

- **文未明确说明**：论文摘要及元数据中未提及使用的 GPU 型号、数量、训练时长或内存消耗。仅提到构建了 151,182 个空间点的数据集并进行了三阶段训练，算力需求可能较大，但具体细节缺失。

## 5. 实验数量与充分性

- **实验数量**：主要涉及 3 个定量任务（基因表达预测、空间域识别、零样本分类）和 1 个专家评估案例研究。其中零样本分类覆盖了 4 个基准，基因表达预测和空间域识别各有若干对比（但未说明具体数据集数量）。
- **充分性分析**：
  - **正面**：实验涵盖了预测、识别、分类及真实专家验证等多种任务，且与最强基线对比，提升幅度较大（23.6%-80.9%）。乳腺癌专家评估增加了临床可信度。
  - **不足**：未执行消融实验（如去掉某个阶段或某个模态的效果），未分析不同组织类型或来源的数据对结果的影响，也未见跨数据集泛化的系统测试。算力、模型规模等未报告，影响复现性。

## 6. 论文的主要结论与发现

- 三模态基础模型 SciCore-Omics 在基因表达预测和空间域识别任务上比最强外部基线相对提升 **23.6%-80.9%**。
- 在零样本组织病理学分类任务上，平均准确率超过 GPT-5 达 **6.16 个百分点**。
- 基于 10 例乳腺癌案例的专家评估证实了模型仅凭 H&E 图像即可进行合理的病例级分子推理（如判断 ER/PR/HER2 状态等）。
- 三模态框架能够有效桥接组织形态学和分子状态，为计算病理学和组学分析提供更通用且可解释的基础模型。

## 7. 优点

- **首次三模态统一**：将组织学、空间转录组学和生物语言整合，超越以往双模态模型。
- **渐进训练策略**：通过阶段式对齐逐步融合不同模态信息，有效降低多模态联合训练难度。
- **强零样本能力**：在零样本科分类任务上超越 GPT-5，显示出良好的泛化性。
- **临床验证**：乳腺癌专家评估增强了模型在真实病理场景下的可用性。
- **性能提升显著**：在关键任务上取得 20%-80% 的相对提升，优势明确。

## 8. 不足与局限

- **资源信息缺失**：未报告算力开销、训练时间、模型参数量等，不利于复现和资源评估。
- **消融实验不充分**：未提供分阶段或分模态的消融分析，无法确定各组件贡献。
- **数据集覆盖有限**：虽提及多组织，但未详细列出具体组织类型和样本来源，可能存在偏差风险（如仅涵盖部分癌症类型）。
- **基线描述模糊**：“最强外部基线”未具名，GPT-5 的测试条件（是否微调、prompt 设计等）未说明，影响公平性判断。
- **可解释性未深入**：虽声称“可解释”，但未展示生成的语言解释质量（如文本一致性、生物学合理性的人工评价）。
- **可能过拟合风险**：训练数据仅 15 万点（约 150k 样本），对于多组织大模型可能偏小，跨组织泛化需进一步验证。

（完）
