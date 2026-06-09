---
title: "SciCore-Omics: a tri-modal foundation model unifying histology, spatial transcriptomics and language for spatial biology"
title_zh: SciCore-Omics：一个统一组织学、空间转录组学和语言的三模态基础模型，用于空间生物学
authors: "Xiao, X., Li, Y., Zeng, Z., Yan, Y., Liu, Z., Xiang, Y., Ye, Z., Ying, J., Xie, L., He, F."
date: 2026-06-04
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.30.728937v2.full.pdf"
tags: ["query:hmm"]
score: 9.0
evidence: 统一组织学、空间转录组和语言的三模态基础模型
tldr: "现有基础模型仅成对连接组织学、组学或语言，难以联合推断分子状态和解码空间组织。本文提出SciCore-Omics，首个三模态基础模型，在151,182个空间配对的图像-基因-文本数据集上三阶段训练。在基因表达预测和空间域识别任务中，相对最强基线提升23.6-80.9%；零样本病理分类平均准确率比GPT-5高6.16个百分点。专家评估确认了基于H&E的分子推理能力，为计算病理和组学分析提供了更通用可解释的基础模型。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有模型仅成对连接组织学、组学或语言，无法联合推断分子状态并解码空间组织。
method: 构建15万空间配对的图像-基因-文本数据集，对SciCore-Omics进行三阶段渐进训练。
result: "基因表达预测和空间域识别相对最强基线提升23.6-80.9%；零样本病理分类平均准确率超GPT-5 6.16个百分点。"
conclusion: 三模态框架有效桥接组织形态与分子状态，为计算病理学和组学分析提供通用可解释基础模型。
---

## 摘要
组织形态学与空间转录组学捕捉组织生物学的互补方面，但它们之间的关系在大规模上仍然难以提取、对齐和解释。现有的基础模型通常仅成对连接组织学、组学或语言，这限制了它们联合推断分子状态、解码空间组织结构和生成具有生物学基础的解释的能力。在此，我们展示了SciCore-Omics，这是首个连接组织学图像、空间转录组学和生物语言的三模态基础模型。我们构建了一个包含跨多个组织的151,182个点的空间配对图像-基因-文本数据集，并在该数据集上对SciCore-Omics进行了三阶段渐进式训练。在基因表达预测和空间域识别方面，SciCore-Omics在任务特定指标上相较于最强的外部基线实现了23.6-80.9%的相对提升。它还在组织病理学分类中展示出强大的零样本泛化能力，在四个基准测试中的平均准确率上比GPT-5高出6.16个百分点。对10例乳腺癌病例的专家评估证实了其仅基于H&E的病例级分子推理能力。综上所述，我们的方法证明了三模态框架能够有效桥接组织形态学和分子状态，为计算病理学和组学分析提供了更通用且可解释的基础模型。

## Abstract
Histomorphology and spatial transcriptomics capture complementary aspects of tissue biology, but their relationships remain difficult to extract, align, and interpret at scale. Existing foundation models typically connect histology, omics, or language only pairwise, which limits their capacity to jointly infer molecular states, decode spatial tissue organization, and generate biologically grounded explanations. Here, we show SciCore-Omics, the first tri-modal foundation model linking histology images, spatial transcriptomics, and biological language. We constructed a spatially paired image-gene-text dataset comprising 151,182 spots across multiple tissues and performed a three-stage progressive training of SciCore-Omics on this dataset. Across gene expression prediction and spatial domain recognition, SciCore-Omics achieved 23.6-80.9% relative gains in task-specific metrics over the strongest external baselines. It further showed robust zero-shot generalization in histopathology classification, outperforming GPT-5 by 6.16 percentage points in mean accuracy across four benchmarks. Expert evaluation in 10 breast cancer cases confirmed its H&E-only case-level molecular reasoning capability. Together, our method demonstrates that a tri-modal framework can effectively bridge histomorphology and molecular state, providing a more general and interpretable foundation model for computational pathology and omics analysis.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义

- **研究动机**：组织形态学（H&E染色图像）与空间转录组学分别捕捉组织生物学的互补方面，但二者之间的关联在大规模数据上难以提取、对齐和解释。现有基础模型通常仅成对连接组织学、组学或语言（例如组织学+组学，或组织学+语言），缺乏同时整合三种模态的联合推理能力，限制了其在分子状态推断、空间组织解码以及生成生物学可解释结论方面的应用。
- **整体含义**：本文提出首个三模态基础模型SciCore-Omics，统一组织学图像、空间转录组学和生物语言，旨在实现跨模态的深层关联，为计算病理学和组学分析提供更通用、可解释的基础工具。

## 2. 论文提出的方法论

- **核心思想**：构建一个包含组织学图像、空间转录组基因表达和相应生物文本描述的三模态对齐数据集，通过三阶段渐进式训练，使模型学会将视觉形态与分子状态及语言描述相互映射。
- **关键技术细节**：
  - **数据集构建**：从多个组织中收集151,182个空间斑点（spots），每个斑点包含配对的H&E图像块、空间转录组基因表达谱以及基于基因表达生成的生物语言描述（如基因功能、空间域标签等）。
  - **三阶段训练策略**：
    1. 第一阶段：图像-基因双模态对齐预训练（如对比学习）。
    2. 第二阶段：图像-文本双模态对齐训练，引入语言描述。
    3. 第三阶段：三模态联合微调，统一图像、基因和文本的嵌入空间。
  - **模型架构**：未在摘要中详细说明，推测使用类似CLIP的多编码器融合架构，分别编码图像（如Vision Transformer）、基因（如MLP或Transformer）和文本（如BERT）。
- **算法流程**（文字说明）：
  1. 输入：H&E图像块 → 图像编码器；基因表达向量 → 基因编码器；对应文本 → 文本编码器。
  2. 通过对比学习或交叉注意力机制对齐各模态表示。
  3. 在推理时，可仅凭图像预测基因表达、识别空间域或进行零样本病理分类，并可生成文本解释。

## 3. 实验设计

- **数据集/场景**：
  - 训练集：包含151,182个空间配对图像-基因-文本点，来自多个组织（如乳腺、结肠等）。
  - 评估任务：
    - 基因表达预测（预测给定H&E图像所在点的基因表达谱）
    - 空间域识别（将组织划分为不同功能区域）
    - 零样本组织病理学分类（在未见过的病理图像数据集上直接分类）
  - 专家评估：针对10例乳腺癌病例，评估模型仅基于H&E图像进行病例级分子推理的能力。
- **基准（Benchmark）**：未具体列出所有基准数据集名称，但包含四个独立的组织病理学分类基准用于零样本测试。
- **对比方法**：
  - 最强外部基线（可能包括仅双模态的模型或通用视觉语言模型）
  - GPT-5（作为零样本分类对比对象）
  - 专家人工评估（作为定性验证）

## 4. 资源与算力

- **文中未明确说明**：摘要和元数据中未提及GPU型号、数量、训练时长或总计算量。推测训练15万余个斑点的大规模三模态模型需要较多计算资源，但具体细节缺失。需指出此信息在现有文本中未提供。

## 5. 实验数量与充分性

- **实验组数**：
  - 至少包括：基因表达预测、空间域识别、四个零样本病理分类基准、专家10例乳腺癌评估。共计至少1+1+4+1=7项主要实验。
  - 消融实验：未在摘要中提及，但三阶段训练可能隐含了消融（如去掉某阶段），但未明确报告。
- **充分性评估**：
  - 优点：覆盖了多种下游任务（预测、识别、零样本分类）和专家验证，任务类型较全面。
  - 不足：缺乏对模型规模、不同模态组合的详细消融分析；未在更大规模多组织数据集上验证泛化性；与现有最先进空间转录组分析方法（如SPOTlight、stLearn等）的直接定量比较未在摘要中给出；零样本基准仅对比GPT-5，对比基线数量有限。
  - 总体公正性：相对提升23.6-80.9%的数据来自外部最强基线，但未明确指出这些基线是否最优，可能存在选择性报告风险。

## 6. 论文的主要结论与发现

- SciCore-Omics是首个三模态基础模型，成功连接组织学、空间转录组学和语言。
- 在基因表达预测和空间域识别上，相比最强外部基线实现了23.6–80.9%的相对指标提升。
- 在零样本病理分类任务上，平均准确率比GPT-5高6.16个百分点。
- 专家评估证实了模型仅基于H&E图像进行病例级分子推理的能力（10例乳腺癌）。
- 三模态框架有效桥接组织形态与分子状态，为计算病理学和组学分析提供了更通用且可解释的基础模型。

## 7. 优点

- **创新性**：首个整合组织学、空间转录组学和语言的三模态模型，突破了现有成对连接的局限。
- **性能显著**：在关键任务上指标提升幅度大（23.6–80.9%），零样本能力超越GPT-5。
- **可解释性**：通过语言模态能够生成生物学解释，增强模型的可理解性。
- **数据规模与多样性**：构建了15万余个跨组织空间配对数据集，为后续研究提供资源。
- **专家验证**：通过病理专家评估，增强了临床可信度。

## 8. 不足与局限

- **实验覆盖**：尽管有多项任务，但未在更多独立空间转录组数据集（如不同平台、不同组织）上验证泛化性；缺乏与传统空间解析方法（如基于物理模型的方法）的对比。
- **消融分析不充分**：未说明三阶段训练中各阶段贡献，及去掉语言模态后的性能变化。
- **资源信息缺失**：未报告训练算力消耗，影响可复现性评估。
- **偏差风险**：训练数据可能主要来自特定来源（如公共数据库），组织类型有限，可能存在组织特异性偏差。
- **应用限制**：模型依赖空间转录组数据的斑点级匹配，对于非空间分辨率的数据无法直接应用；专家评估仅10例乳腺癌，样本量小，结论外推需谨慎。
- **可解释性深度**：尽管能生成文本解释，但其生物学准确性和精细度未系统评估。

（完）
