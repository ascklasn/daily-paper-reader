---
title: "SciCore-Omics: a tri-modal foundation model unifying histology, spatial transcriptomics and language for spatial biology"
title_zh: SciCore-Omics：一种统一组织学、空间转录组学和语言的三模态基础模型用于空间生物学
authors: "Xiao, X., Li, Y., Zeng, Z., Yan, Y., Liu, Z., Xiang, Y., Ye, Z., Ying, J., Xie, L., He, F."
date: 2026-06-03
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.30.728937v1.full.pdf"
tags: ["query:hmm"]
score: 9.0
evidence: 统一组织学、空间转录组和语言的三模态基础模型
tldr: "组织形态学与空间转录组学的关联难以大规模提取和对齐。现有基础模型仅实现两两模态连接。本文提出首个三模态基础模型SciCore-Omics，统一组织学图像、空间转录组学和生物语言。通过构建15万点空间配对数据集并设计三阶段渐进训练，模型在基因表达预测和空间域识别任务上相对最强基线提升23.6-80.9%，零样本组织病理学分类准确率超越GPT-5达6.16个百分点。该工作为计算病理学提供了更通用、可解释的三模态基础框架。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有模型仅支持两模态（组织学-组学或组织学-语言），缺乏统一三模态理解的能力，限制了分子状态推断和组织解析。
method: 构建15万点空间配对图像-基因-文本数据集，设计三阶段渐进训练（对齐-融合-生成），学习组织学、空间转录组学与语言的联合表征。
result: "基因表达预测和空间域识别指标相对提升23.6-80.9%；零样本组织病理学分类准确率超GPT-5达6.16个百分点；10例乳腺癌专家验证仅H&E分子推理能力。"
conclusion: 三模态框架有效桥接组织形态学与分子状态，为计算病理学和组学分析提供更通用、可解释的基础模型。
---

## 摘要
组织形态学与空间转录组学捕捉了组织生物学的互补方面，但它们之间的关系在大规模提取、对齐和解释方面仍然困难。现有的基础模型通常仅以成对方式连接组织学、组学或语言，这限制了它们联合推断分子状态、解码空间组织结构和生成具有生物学基础的解释的能力。在此，我们展示了SciCore-Omics，这是首个连接组织学图像、空间转录组学和生物学语言的三模态基础模型。我们构建了一个空间配对的图像-基因-文本数据集，包含跨多个组织的151,182个点，并在此数据集上对SciCore-Omics进行了三阶段渐进训练。在基因表达预测和空间域识别方面，SciCore-Omics在任务特定指标上相对于最强外部基线实现了23.6-80.9%的相对提升。它在组织病理学分类中进一步展示了强大的零样本泛化能力，在四个基准测试中平均准确率超过GPT-5 6.16个百分点。对10例乳腺癌病例的专家评估证实了其仅基于H&E染色的病例级分子推理能力。总之，我们的方法证明了三模态框架能够有效桥接组织形态学和分子状态，为计算病理学和组学分析提供了一个更通用且可解释的基础模型。

## Abstract
Histomorphology and spatial transcriptomics capture complementary aspects of tissue biology, but their relationships remain difficult to extract, align, and interpret at scale. Existing foundation models typically connect histology, omics, or language only pairwise, which limits their capacity to jointly infer molecular states, decode spatial tissue organization, and generate biologically grounded explanations. Here, we show SciCore-Omics, the first tri-modal foundation model linking histology images, spatial transcriptomics, and biological language. We constructed a spatially paired image-gene-text dataset comprising 151,182 spots across multiple tissues and performed a three-stage progressive training of SciCore-Omics on this dataset. Across gene expression prediction and spatial domain recognition, SciCore-Omics achieved 23.6-80.9% relative gains in task-specific metrics over the strongest external baselines. It further showed robust zero-shot generalization in histopathology classification, outperforming GPT-5 by 6.16 percentage points in mean accuracy across four benchmarks. Expert evaluation in 10 breast cancer cases confirmed its H&E-only case-level molecular reasoning capability. Together, our method demonstrates that a tri-modal framework can effectively bridge histomorphology and molecular state, providing a more general and interpretable foundation model for computational pathology and omics analysis.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：组织形态学（H&E染色图像）与空间转录组学分别捕捉组织生物学的互补方面，但两者之间的大规模关联提取、对齐和解释仍然困难。现有的基础模型仅能实现两两模态连接（如组织学-组学、组织学-语言或组学-语言），缺乏统一的三模态理解能力，从而限制了联合推断分子状态、解码空间组织结构以及生成有生物学基础的解释的能力。
- **整体含义**：本文提出首个三模态基础模型 SciCore-Omics，旨在桥接组织形态学、空间转录组学和生物学语言，为计算病理学和组学分析提供更通用、可解释的统一框架，推动从形态到分子的跨层次生物学理解。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：构建大规模空间配对的图像-基因-文本三元组数据集，通过三阶段渐进训练学习三模态联合表征，使模型能够同时理解组织图像、基因表达和生物学语言。
- **关键技术细节**：
  - **数据集构建**：收集跨多个组织的空间转录组数据，将每个点（spot）对应的H&E图像块、基因表达谱（可能经降维或归一化）以及自动生成或人工标注的生物学文本描述（如细胞类型、功能注释）配对，形成151,182个三元组。
  - **三阶段渐进训练**：
    1. **对齐阶段（Alignment）**：使用对比学习（如CLIP风格）在图像-文本、基因-文本、图像-基因成对之间建立初始对齐，学习共享嵌入空间。
    2. **融合阶段（Fusion）**：引入跨模态注意力或Transformer融合模块，联合编码三模态信息，增强模态间的交互。
    3. **生成阶段（Generation）**：以自回归或掩码生成方式预训练，使模型能够根据部分模态输入生成其他模态（如从图像生成基因表达描述），提升泛化与可解释性。
  - **模型架构**：未明确具体编码器类型，推测使用视觉Transformer（ViT）处理图像，基因编码器（可能为MLP或Transformer）处理基因表达向量，文本编码器（如BERT）处理语言。融合部分可能采用交叉注意力或Perceiver结构。

## 3. 实验设计

- **数据集**：
  - 空间配对图像-基因-文本数据集：包含151,182个点，跨多个组织（如乳腺癌、脑组织、肠道等）。具体组织来源未详述。
  - 零样本评估使用4个公开的组织病理学分类基准（未指名，可能包含PatchCamelyon、BRCA等）。
  - 专家评估：10例乳腺癌病例的H&E切片进行仅基于图像的分子亚型推理（如Luminal A/B、HER2+、三阴性等）。
- **任务场景与Benchmark**：
  - **基因表达预测**：从H&E图像预测特定基因的空间表达水平。
  - **空间域识别**：根据H&E图像识别组织空间区域（如肿瘤、基质、免疫等）。
  - **零样本组织病理学分类**：无需微调，直接使用预训练模型对组织图像进行疾病/亚型分类。
- **对比方法**：
  - 外部基线：最强的现有双模态基础模型（如CONCH、UNI、PathCLIP等，具体未列出，但声称在任务指标上相对提升23.6-80.9%）。
  - GPT-5：在零样本分类上直接对比，其平均准确率被SciCore-Omics超越6.16个百分点。
  - 消融：三阶段训练效果可能通过移除某阶段验证（文中未明确说明消融实验数目，但三阶段设计隐含对比）。

## 4. 资源与算力

- **未明确说明**：论文摘要及元数据中未提及GPU型号、数量、训练时长、内存消耗等具体算力信息。仅指出在151,182个点数据集上进行三阶段训练。推测需要大规模GPU集群（如8×A100或更高），但具体细节缺失。

## 5. 实验数量与充分性

- **实验数量**：至少包括以下类别：
  - 基因表达预测任务（1组主实验）
  - 空间域识别任务（1组主实验）
  - 零样本组织病理学分类（4个基准测试，共4组实验）
  - 专家评估10例乳腺癌（1组定性实验）
  - 可能包含消融实验（文中未明确列出，但三阶段训练的不同组合可视为消融，需检查全文）。
- **充分性与客观性**：
  - **优点**：覆盖多个任务类型（回归、分类、域识别、零样本），评估维度丰富；与最强基线及GPT-5对比，结果显著；专家评估提供了临床相关性验证。
  - **不足**：未展示三模态消融（如仅双模态 vs 三模态）的定量比较；未在更多数据集上验证空间域识别；零样本评估仅限分类任务，未涵盖分割、检测等其他病理任务；对比的基线数量有限，未列出所有基线名称。

## 6. 论文的主要结论与发现

- 三模态基础模型 SciCore-Omics 能够统一组织学、空间转录组学和生物学语言，有效桥接形态与分子。
- 在基因表达预测和空间域识别任务上，SciCore-Omics 相对于最强外部基线在任务指标上取得23.6-80.9%的相对提升。
- 零样本组织病理学分类在4个基准上平均准确率超过GPT-5达6.16个百分点，展示了强大的泛化能力。
- 在10例乳腺癌专家评估中，仅基于H&E图像即可进行病例级分子推理，验证了模型的生物学可解释性和临床潜力。

## 7. 优点

- **首次提出三模态统一框架**：突破了现有双模态模型的局限，为跨模态生物学发现提供了更完整的视角。
- **大规模配对数据集**：构建15万点空间三元组，为训练和评估提供了基础资源。
- **三阶段渐进训练设计**：对齐-融合-生成逐步提升模态对齐与生成能力，符合多模态学习规律。
- **多任务通用性强**：在同一框架下支持基因表达预测、空间域识别、零样本分类、分子推理等多种任务。
- **零样本能力突出**：超越GPT-5，表明模型学到了生物语义而非简单记忆。
- **临床验证**：专家评估增加了结果可信度与转化潜力。

## 8. 不足与局限

- **数据集规模与多样性**：15万点对于大规模预训练仍显不足；跨组织覆盖种类未详细说明，可能缺乏罕见癌种或正常组织。
- **计算资源未公开**：缺乏训练成本信息，难以评估可复现性和资源门槛。
- **消融实验不清晰**：未明确展示各训练阶段贡献度以及三模态相对双模态的定量增益。
- **对比基线不够详尽**：未列出所有基线名称及超参数设置，公平性验证不足；GPT-5的版本和评估条件未明确。
- **专家评估规模小**：仅10例乳腺癌，统计显著性弱；未进行多中心、多读者验证。
- **应用限制**：依赖空间转录组数据构建，对于仅有组织切片的场景需借助零样本推理，但零样本任务仅限分类；模型可解释性虽声称生成生物学解释，但未提供具体生成结果示例。
- **领域偏差风险**：可能存在训练数据来源的批次效应或技术偏差，泛化到其他平台或染色方案需验证。

（完）
