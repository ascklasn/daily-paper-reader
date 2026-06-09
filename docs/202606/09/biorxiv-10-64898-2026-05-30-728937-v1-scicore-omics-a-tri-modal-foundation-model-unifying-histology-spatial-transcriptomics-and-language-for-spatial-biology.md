---
title: "SciCore-Omics: a tri-modal foundation model unifying histology, spatial transcriptomics and language for spatial biology"
title_zh: SciCore-Omics：一种统一组织学、空间转录组学和语言的三模态基础模型用于空间生物学
authors: "Xiao, X., Li, Y., Zeng, Z., Yan, Y., Liu, Z., Xiang, Y., Ye, Z., Ying, J., Xie, L., He, F."
date: 2026-06-03
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.30.728937v1.full.pdf"
tags: ["query:hmm"]
score: 9.0
evidence: 统一组织学、空间转录组学和语言的三模态基础模型
tldr: "组织形态与分子状态关联困难，现有模型局限于两两模态。本文提出SciCore-Omics，首个连接组织学图像、空间转录组学和生物语言的三模态基础模型，通过构建15万+配对spot数据集和三阶段训练实现跨模态对齐。在基因表达预测和空间域识别上性能提升23.6-80.9%，零样本病理分类超越GPT-5，并展示仅H&E的分子推理能力。该框架为计算病理学提供了更通用可解释的解决方案。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有基础模型只能连接两两模态，无法联合推断分子状态和解剖空间组织，限制了可扩展的生物学解释。
method: "构建151,182个配对图像-基因-文本spot数据集，对SciCore-Omics进行三阶段渐进训练，对齐三模态表示。"
result: "在基因表达预测和空间域识别上相对最强基线提升23.6-80.9%，零样本病理分类准确率比GPT-5高6.16%，专家验证其H&E分子推理能力。"
conclusion: 三模态框架有效桥接组织形态与分子状态，为计算病理学和组学分析提供了更通用、可解释的基础模型。
---

## 摘要
组织形态学和空间转录组学捕捉组织生物学的互补方面，但它们之间的关系在大规模提取、对齐和解释上仍然困难。现有的基础模型通常仅以成对方式连接组织学、组学或语言，这限制了它们联合推断分子状态、解码空间组织结构和生成有生物学依据的解释的能力。在此，我们展示SciCore-Omics，这是首个连接组织学图像、空间转录组学和生物语言的三模态基础模型。我们构建了一个空间配对的图像-基因-文本数据集，涵盖多个组织的151,182个斑点，并在此数据集上对SciCore-Omics进行了三阶段渐进式训练。在基因表达预测和空间域识别方面，SciCore-Omics在任务特定指标上相比最强外部基线获得了23.6-80.9%的相对提升。它还在组织病理学分类中展现出强大的零样本泛化能力，在四个基准测试的平均准确率上比GPT-5高出6.16个百分点。在10例乳腺癌病例的专家评估中，证实了其仅基于H&E染色的病例级分子推理能力。总之，我们的方法证明了三模态框架能够有效桥接组织形态学和分子状态，为计算病理学和组学分析提供了更通用、可解释的基础模型。

## Abstract
Histomorphology and spatial transcriptomics capture complementary aspects of tissue biology, but their relationships remain difficult to extract, align, and interpret at scale. Existing foundation models typically connect histology, omics, or language only pairwise, which limits their capacity to jointly infer molecular states, decode spatial tissue organization, and generate biologically grounded explanations. Here, we show SciCore-Omics, the first tri-modal foundation model linking histology images, spatial transcriptomics, and biological language. We constructed a spatially paired image-gene-text dataset comprising 151,182 spots across multiple tissues and performed a three-stage progressive training of SciCore-Omics on this dataset. Across gene expression prediction and spatial domain recognition, SciCore-Omics achieved 23.6-80.9% relative gains in task-specific metrics over the strongest external baselines. It further showed robust zero-shot generalization in histopathology classification, outperforming GPT-5 by 6.16 percentage points in mean accuracy across four benchmarks. Expert evaluation in 10 breast cancer cases confirmed its H&E-only case-level molecular reasoning capability. Together, our method demonstrates that a tri-modal framework can effectively bridge histomorphology and molecular state, providing a more general and interpretable foundation model for computational pathology and omics analysis.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 核心问题与整体含义
- **研究背景**：组织形态学（H&E染色图像）和空间转录组学（基因表达空间图谱）是组织生物学互补的两个层面，但两者之间的大规模关联、对齐与解释仍然困难。
- **现有局限**：现有基础模型通常仅成对连接组织学、组学或语言（例如图像-基因、图像-文本或基因-文本），缺乏统一三模态的联合推理能力，无法同时推断分子状态、解码空间组织并生成有生物学依据的解释。
- **本文贡献**：提出首个连接组织学图像、空间转录组学和生物语言的三模态基础模型 **SciCore-Omics**，旨在桥接组织形态与分子状态，为计算病理学提供更通用、可解释的基础模型。

## 2. 方法论
- **核心思想**：通过构建空间配对的**图像-基因-文本**三元组数据，并采用**三阶段渐进式训练**，使模型学习跨模态对齐与联合表示。
- **关键步骤**：
  - **数据构建**：收集涵盖多个组织的空间转录组数据，提取每个spot（斑点）的H&E图像块、基因表达向量和对应的生物语义描述（如细胞类型、组织结构等），最终得到 **151,182个配对的spot样本**。
  - **三阶段训练**：
    1. 第一阶段：分别在单一模态（图像、基因、文本）上进行预训练，提取各模态基础表示。
    2. 第二阶段：进行两两模态对齐（如图像-基因、图像-文本、基因-文本），学习跨模态关联。
    3. 第三阶段：在配对三元组数据上进行三模态联合训练，通过对比学习或匹配任务实现统一表征空间的对齐。
- **技术细节**：原文未公布具体网络架构（如是否基于Transformer）、损失函数公式或训练超参数，仅描述为“三阶段渐进式训练”。

## 3. 实验设计
- **使用数据集**：自建空间配对数据集（151,182 spots），涵盖多个组织类型（未具体列出组织名称）。此外使用4个公开病理分类基准（用于零样本评估）以及10例乳腺癌病例（用于专家评估）。
- **Benchmark任务**：
  - **基因表达预测**：给定H&E图像预测空间spot的基因表达。
  - **空间域识别**：根据图像和/或基因数据识别组织空间区域。
  - **零样本病理分类**：在4个独立基准上直接应用模型（不微调），评估分类准确率。
- **对比方法**：
  - 基因表达预测和空间域识别：对比“最强外部基线”（具体方法未在摘要中列出，可能包括Pathomics、CLIP等现有成对模型）。
  - 病理分类：对比 **GPT-5**（通用大语言模型），结果显示SciCore-Omics平均准确率高出6.16个百分点。
- **专家评估**：10例乳腺癌病例，仅输入H&E图像，由病理专家验证模型的分子推理（如预测受体状态、基因突变等）。

## 4. 资源与算力
- **文中未明确说明**：摘要及提供的元数据中均未提及训练所使用的GPU型号、数量、训练时长、显存消耗等计算资源信息。这可能是因为预印本未包含实验补录部分。在资源匮乏的复现场景下需要自行尝试。

## 5. 实验数量与充分性
- **实验覆盖**：包括基因表达预测、空间域识别、零样本病理分类（4个基准）和专家评估（10例乳腺癌）。但每个任务下的具体实验组数（如不同数据集拆分、不同超参数设置）未报告。
- **消融实验**：摘要未提及消融实验（如是否验证了三阶段训练的必要性、各模态独立贡献等），对模型组件有效性验证不充分。
- **公平性与客观性**：基准对比中未列出所有基线方法的详细结果，且“最强外部基线”的描述较模糊，难以判断选择的客观性。零样本对比仅用GPT-5，缺乏与其他领域专用模型的比较。专家评估仅涉及10例且单一癌种，代表性有限。

## 6. 主要结论与发现
- **性能提升**：在基因表达预测和空间域识别任务上，相对于最强外部基线，**任务特定指标提升23.6%–80.9%**（相对增益）。
- **零样本能力**：病理分类零样本平均准确率高于GPT-5 **6.16个百分点**，展示出模型具有较好的跨任务泛化能力。
- **分子推理**：专家评估证实模型能仅凭H&E图像推断病例级分子信息（如受体状态），表明三模态对齐有助于学得形态-分子关联。
- **整体结论**：三模态框架可有效桥接组织形态与分子状态，为计算病理学和组学分析提供更通用、可解释的基础模型。

## 7. 优点
- **首创性**：首个连接组织学、空间转录组学和语言的**三模态基础模型**，突破了现有成对模型的限制。
- **大规模数据构建**：手工配对151,182个spot，覆盖多组织，为多模态对齐提供基础。
- **三阶段训练策略**：渐进式对齐降低训练难度，可能提升跨模态表示质量。
- **优异的任务性能**：在核心任务上大幅超越基线，且展现出零样本和多任务泛化能力。
- **可解释性**：通过语言模态可生成生物学解释，专家验证其分子推理能力，提升了模型可信任度。

## 8. 不足与局限
- **技术细节不足**：论文为预印本，未公布网络架构、损失函数、训练超参数等关键细节，影响可复现性。
- **数据集规模与多样性**：151k spots相对实际空间转录组数据规模仍较小，且未明确涉及多种组织类型、疾病状态（如癌症亚型全面覆盖）或不同测序平台（如10x Visium、Slide-seq等）。
- **消融研究缺失**：缺少对三阶段训练、各模态贡献、不同对齐策略的消融分析，无法判断每部分的有效性。
- **对比方法局限**：基线描述模糊，零样本仅与GPT-5对比（GPT-5并非病理专用模型），缺乏与多种现有基于图像或基因的基础模型（如CONCH、GPTS-T等）的公平比较。
- **专家评估规模小**：仅10例乳腺癌，癌种单一，且未提供一致性指标（如Kappa值），不足以全面证明分子推理的可靠性。
- **算力与资源未知**：未提供训练成本信息，不利于评估实际可用性。
- **未讨论偏见与公平性**：未分析模型在不同人群、染色条件、组织来源上的表现差异，存在潜在的偏见风险。

（完）
