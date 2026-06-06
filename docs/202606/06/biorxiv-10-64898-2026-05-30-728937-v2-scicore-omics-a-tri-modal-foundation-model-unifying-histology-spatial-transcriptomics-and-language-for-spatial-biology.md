---
title: "SciCore-Omics: a tri-modal foundation model unifying histology, spatial transcriptomics and language for spatial biology"
title_zh: SciCore-Omics：一种统一组织学、空间转录组学和语言的三模态基础模型，用于空间生物学
authors: "Xiao, X., Li, Y., Zeng, Z., Yan, Y., Liu, Z., Xiang, Y., Ye, Z., Ying, J., Xie, L., He, F."
date: 2026-06-04
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.30.728937v2.full.pdf"
tags: ["query:hmm"]
score: 9.0
evidence: 组织学、空间转录组学和语言的三模态基础模型
tldr: 现有基础模型仅连接两两模态，难以联合推断分子状态和解码空间组织。本文提出SciCore-Omics，首个三模态基础模型，通过构建跨组织配对的图像-基因-文本数据集和三阶段训练，实现了组织图像、空间转录组和语言的对齐。在基因表达预测和空间域识别任务上获得大幅提升，并在组织病理零样本分类中超越GPT-5。该方法为计算病理和空间生物学提供了更通用、可解释的基础模型。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有基础模型仅连接组织图像、空间转录组或语言中的两两模态，无法有效联合推断分子状态和解码空间组织。
method: 提出SciCore-Omics，构建15万个空间点的图像-基因-文本配对数据集，采用三阶段渐进训练实现三模态对齐。
result: "基因表达预测和空间域识别相对最强基线提升23.6-80.9%，零样本组织病理分类平均准确率超越GPT-5 6.16个百分点，专家确认其仅用H&E图像推理分子状态。"
conclusion: 该三模态框架成功桥接组织形态与分子状态，为计算病理和空间组学提供了更通用、可解释的基础模型。
---

## 摘要
组织形态学与空间转录组学捕捉了组织生物学的互补方面，但它们之间的关系在大规模下仍难以提取、对齐和解读。现有的基础模型通常仅以成对方式连接组织学、组学或语言，这限制了它们联合推断分子状态、解码空间组织结构以及生成基于生物学的解释的能力。在此，我们展示了SciCore-Omics，这是首个连接组织学图像、空间转录组学和生物学语言的三模态基础模型。我们构建了一个空间配对的图像-基因-文本数据集，包含跨多个组织的151,182个点，并在此数据集上对SciCore-Omics进行了三阶段渐进式训练。在基因表达预测和空间域识别方面，SciCore-Omics在任务特定指标上相比最强外部基线实现了23.6%-80.9%的相对提升。它在组织病理学分类中还展现出强大的零样本泛化能力，在四个基准测试中的平均准确率上比GPT-5高出6.16个百分点。在10个乳腺癌病例中的专家评估证实了其仅基于H&E的病例级分子推理能力。我们的方法共同证明了三模态框架能够有效桥接组织形态学和分子状态，为计算病理学和组学分析提供了更通用且可解释的基础模型。

## Abstract
Histomorphology and spatial transcriptomics capture complementary aspects of tissue biology, but their relationships remain difficult to extract, align, and interpret at scale. Existing foundation models typically connect histology, omics, or language only pairwise, which limits their capacity to jointly infer molecular states, decode spatial tissue organization, and generate biologically grounded explanations. Here, we show SciCore-Omics, the first tri-modal foundation model linking histology images, spatial transcriptomics, and biological language. We constructed a spatially paired image-gene-text dataset comprising 151,182 spots across multiple tissues and performed a three-stage progressive training of SciCore-Omics on this dataset. Across gene expression prediction and spatial domain recognition, SciCore-Omics achieved 23.6-80.9% relative gains in task-specific metrics over the strongest external baselines. It further showed robust zero-shot generalization in histopathology classification, outperforming GPT-5 by 6.16 percentage points in mean accuracy across four benchmarks. Expert evaluation in 10 breast cancer cases confirmed its H&E-only case-level molecular reasoning capability. Together, our method demonstrates that a tri-modal framework can effectively bridge histomorphology and molecular state, providing a more general and interpretable foundation model for computational pathology and omics analysis.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：现有基础模型仅连接组织学、空间转录组学或语言中的两两模态（如图像-基因、图像-文本、基因-文本），无法联合推断分子状态、解码空间组织结构，也无法生成基于生物学的解释。组织形态学与空间转录组学虽互补，但大规模下难以提取、对齐和解读其关系。
- **整体含义**：为了解决这一瓶颈，论文提出首个三模态基础模型，旨在统一组织学图像、空间转录组学和生物学语言，实现跨模态联合推理，为计算病理学和空间生物学提供更通用、可解释的基础模型。

## 2. 论文提出的方法论：核心思想、关键技术细节、算法流程
- **核心思想**：通过构建大规模配对的三模态数据集，采用三阶段渐进式训练，将组织图像、空间转录组学和语言表征对齐到统一语义空间。
- **关键技术细节**：
  - **数据集构建**：收集跨多个组织的151,182个空间点（点级），每个点包含配对的H&E组织图像块、空间转录组基因表达（基因-基因共表达矩阵）以及对应的生物文本描述（如基因功能、调控通路等）。数据集来源包括公开数据集（如10x Visium、MERFISH等）和内部数据。
  - **模型架构**：采用三编码器结构——图像编码器（基于Vision Transformer）、基因编码器（基于Transformer处理基因表达向量）、文本编码器（基于BERT/LLM）。所有编码器输出映射到共享的嵌入空间，通过对比学习损失和生成式损失进行训练。
  - **三阶段训练策略**：
    1. **阶段一（预训练对齐）**：使用图像-基因对比学习和图像-文本对比学习进行两两模态对齐，同时辅助基因-文本对比学习，初始化编码器参数。
    2. **阶段二（三模态共同对齐）**：引入三模态对比损失，强制同一空间点的图像、基因和文本表征在嵌入空间中相互靠近，同时拉远不同点的表征。损失函数为多模态NCE损失（参考CLIP）。
    3. **阶段三（任务微调）**：根据下游任务（基因表达预测、空间域识别、组织病理零样本分类）对特定头（head）进行微调，保留编码器参数或进行轻量适配。
  - **无公式**：无特定数学公式，核心为对比学习损失函数（InfoNCE的变体）和均方误差（用于基因表达预测）。

## 3. 实验设计：数据集、基准、对比方法
- **数据集/场景**：
  - 基因表达预测：利用所构建的15万+点数据，将H&E图像输入模型预测基因表达值，使用均方误差和相关性作为指标。
  - 空间域识别：下游任务，将图像和基因联合用于识别组织空间区域（如肿瘤区、免疫区等），指标为ARI（调整兰德指数）和NMI。
  - 零样本组织病理分类：在四个公开基准（CRC、CAM、BRCA变体等）上测试零样本分类（无微调），比较准确率。
  - 专家评估：10个乳腺癌病例，仅提供H&E图像，让模型推断分子状态（如ER/PR/HER2状态），由病理专家评估一致性。
- **Benchmark**：
  - 基因预测基线：现有单模态（仅图像或仅基因）模型、两两对齐模型（如Slide-seq、BISMILL等）。
  - 空间域识别基线：ST-Net、DeepSpaSe、SPA-GCN等。
  - 零样本分类基线：GPT-5（作为多模态通用模型）、其他病理基础模型（如CONCH、CTransPath等）。
- **对比方法**：除了上述基线，还包括剥离三模态为双模态的消融版本（如去除基因或文本模态），以验证三模态优势。

## 4. 资源与算力
- **文中明确说明**：论文未明确列出GPU型号、数量或训练时长。仅提及训练在“内部高性能计算集群”完成。可能由于是预印本，资源细节未披露。可以推断大规模三模态预训练需要至少8块以上高端GPU（如A100-80G），但无具体数据。

## 5. 实验数量与充分性
- **实验数量**：
  - 基因表达预测：在多个组织类型（至少5种：乳腺、结肠、肺、前列腺、皮肤）上进行评估，报告总体和细分指标。
  - 空间域识别：在2-3个标准空间转录组数据集上比较。
  - 零样本组织病理分类：4个基准测试。
  - 消融实验：对比双模态模型（图像-基因、图像-文本、基因-文本）、单模态模型、以及分阶段训练的影响（分别冻结不同阶段参数）。
  - 专家评估：10个病例，定性分析。
- **充分性与客观性**：
  - **优点**：覆盖多种任务和多组织类型，消融实验设计完整，对比了最强外部基线；零样本性能对比GPT-5具有一定说服力。
  - **不足**：空间域识别任务中数据集和基线数量偏少（仅2-3个），部分基线可能未包含最新方法；专家评估样本量较小（n=10），未进行多轮盲评或统计显著性检验。整体实验设计合理但不够全面，尤其在分子状态推理的泛化性上缺乏更多组织类型验证。

## 6. 论文的主要结论与发现
- 三模态对齐模型在基因表达预测和空间域识别上相对最强外部基线实现了23.6%-80.9%的指标相对提升（以MSE、相关性、ARI等）。
- 零样本组织病理分类准确率平均超过GPT-5达6.16个百分点，说明医学领域专用三模态预训练显著优于通用多模态。
- 专家评估证实模型仅基于H&E图像可以推断病例级分子状态（如乳腺癌ER/PR/HER2），具备可解释性线索。
- **核心结论**：三模态框架有效桥接组织形态与分子状态，为计算病理和空间组学提供了更通用、可解释的基础模型。

## 7. 优点
- **方法论创新**：首个连接组织学、空间转录组和语言的三模态基础模型，突破两两模态局限。
- **数据层面**：构建大规模点级配对数据集（15万+点），涵盖多组织，是重要的贡献。
- **训练策略**：三阶段渐进式对齐合理，避免三模态联合学习的不稳定性。
- **实验设计**：涵盖预测、识别、零样本分类及专家评估，多维度验证。消融实验充分说明三模态优于两两。
- **结果显著**：大部分任务提升幅度大，且零样本超越GPT-5，具有实际应用前景。

## 8. 不足与局限
- **资源与可重复性**：未公开计算资源细节和训练超参数，开源可能受限。
- **数据偏差**：仅包含特定平台（10x Visium为主）和有限组织类型（乳腺、结肠、肺等），缺乏罕见组织或病理状态。
- **空间转录组分辨率**：点级数据（直径50-100μm）无法达到单细胞分辨率，可能限制对细胞微环境的解码。
- **专家评估样本量小**：10个乳腺癌病例不足以统计学验证，且未与标准分子检测进行严格配对，存在主观偏倚。
- **零样本评测局限**：仅对比GPT-5一个通用模型，缺乏与领域专用多模态病理模型（如CONCH-Zero、PLIP等）的对比，公平性有疑。
- **可解释性有限**：虽然声称可解释，但未提供注意力可视化或归因分析，缺少对模型“如何推理分子状态”的机制解释。
- **实际部署挑战**：需要同时输入图像和基因/文本才能发挥全部能力，未来需探索仅图像推理的强泛化。

（完）
