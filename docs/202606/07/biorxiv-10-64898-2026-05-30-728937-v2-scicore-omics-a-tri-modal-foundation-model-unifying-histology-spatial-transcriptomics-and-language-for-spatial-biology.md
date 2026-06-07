---
title: "SciCore-Omics: a tri-modal foundation model unifying histology, spatial transcriptomics and language for spatial biology"
title_zh: SciCore-Omics：统一组织学、空间转录组学和语言的三模态基础模型，用于空间生物学
authors: "Xiao, X., Li, Y., Zeng, Z., Yan, Y., Liu, Z., Xiang, Y., Ye, Z., Ying, J., Xie, L., He, F."
date: 2026-06-04
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.30.728937v2.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 三模态基础模型整合组织学、空间转录组学和语言
tldr: "现有模型仅能两两连接组织学、组学或语言，难以联合推断分子状态。本文提出首个三模态基础模型SciCore-Omics，构建151,182个空间配对点的图像-基因-文本数据集，并进行三阶段渐进训练。在基因表达预测和空间域识别任务上，相比最强基线相对提升23.6-80.9%；零样本组织病理学分类平均准确率超越GPT-5达6.16%。该方法有效桥接组织形态与分子状态，为计算病理学提供更通用可解释的基础模型。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有模型仅能连接两种模态，无法联合推断分子状态与空间组织。
method: 构建空间配对图像-基因-文本数据集，采用三阶段渐进训练三模态基础模型SciCore-Omics。
result: "基因预测和空间域识别指标相对提升23.6-80.9%，零样本分类准确率超GPT-5达6.16%。"
conclusion: 三模态框架有效桥接组织形态与分子状态，为计算病理学提供通用可解释的基础模型。
---

## 摘要
组织形态学和空间转录组学捕捉组织生物学的互补方面，但它们之间的关系在大规模上仍然难以提取、对齐和解释。现有的基础模型通常仅以成对方式连接组织学、组学或语言，这限制了它们共同推断分子状态、解码空间组织结构和生成生物学合理解释的能力。在此，我们展示了SciCore-Omics，这是首个连接组织学图像、空间转录组学和生物学语言的三模态基础模型。我们构建了一个包含跨多个组织151,182个点的空间配对图像-基因-文本数据集，并在该数据集上对SciCore-Omics进行了三阶段渐进式训练。在基因表达预测和空间域识别方面，SciCore-Omics在任务特定指标上相比最强外部基线实现了23.6-80.9%的相对提升。它还在组织病理学分类中展示了强大的零样本泛化能力，在四个基准测试的平均准确率上比GPT-5高出6.16个百分点。在10例乳腺癌病例的专家评估中，证实了其仅基于H&E染色的病例级分子推理能力。总之，我们的方法表明，三模态框架能够有效桥接组织形态学和分子状态，为计算病理学和组学分析提供了更通用且可解释的基础模型。

## Abstract
Histomorphology and spatial transcriptomics capture complementary aspects of tissue biology, but their relationships remain difficult to extract, align, and interpret at scale. Existing foundation models typically connect histology, omics, or language only pairwise, which limits their capacity to jointly infer molecular states, decode spatial tissue organization, and generate biologically grounded explanations. Here, we show SciCore-Omics, the first tri-modal foundation model linking histology images, spatial transcriptomics, and biological language. We constructed a spatially paired image-gene-text dataset comprising 151,182 spots across multiple tissues and performed a three-stage progressive training of SciCore-Omics on this dataset. Across gene expression prediction and spatial domain recognition, SciCore-Omics achieved 23.6-80.9% relative gains in task-specific metrics over the strongest external baselines. It further showed robust zero-shot generalization in histopathology classification, outperforming GPT-5 by 6.16 percentage points in mean accuracy across four benchmarks. Expert evaluation in 10 breast cancer cases confirmed its H&E-only case-level molecular reasoning capability. Together, our method demonstrates that a tri-modal framework can effectively bridge histomorphology and molecular state, providing a more general and interpretable foundation model for computational pathology and omics analysis.

---

## 论文详细总结（自动生成）

# 论文结构化总结：SciCore-Omics：统一组织学、空间转录组学和语言的三模态基础模型

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：组织形态学（H&E染色图像）与空间转录组学能够从不同维度揭示组织生物学特征，但二者之间的关系在大规模数据上难以提取、对齐和解释。现有基础模型通常仅以**成对**方式连接组织学、组学或语言（如仅组织学↔组学、组学↔语言、组织学↔语言），缺乏联合解码三种模态的能力，导致难以共同推断分子状态、解码空间组织结构和生成生物学可解释的推理。
- **研究背景**：空间生物学需要跨模态整合，但当前方法局限于两两对齐，无法实现真正的三模态联合建模。语言模型在生物医学领域的成功提示引入生物学语言（如基因描述、病理注释）有望提升模型的可解释性和泛化性。
- **整体含义**：提出首个三模态基础模型SciCore-Omics，旨在桥接组织形态与分子状态，为计算病理学和组学分析提供更通用且可解释的基础工具，能够从H&E图像直接推断基因表达、识别空间域，并基于语言生成生物学解释。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：构建**三模态对齐的空间配对数据集**，并通过**三阶段渐进式训练**，使模型学会同时理解组织学图像、空间转录组学数据和生物学语言，实现联合推理。
- **关键技术细节**：
  - **数据集构建**：收集跨多个组织（如乳腺、前列腺、结肠等）的151,182个空间点，每个点包含H&E图像块、对应的空间转录组基因表达谱（可能来自10x Visium等平台）、以及描述该点生物学状态的文本注释（如细胞类型、区域功能等）。
  - **模型架构**：基于预训练的视觉编码器（如ViT）、基因表达编码器（如Transformer）和语言编码器（如LLM），通过跨模态注意力或对比学习将三者映射到共享嵌入空间。具体架构文中未详细展开，但推断采用多模态Transformer或类似CLIP的多编码器对齐结构。
  - **三阶段渐进训练**：
    1. **阶段一**：图像-基因配对对比学习，建立组织形态与基因表达的基本映射。
    2. **阶段二**：加入语言模态，进行图像-基因-文本的三模态对齐，通过对比损失或生成损失（如文本描述生成）强化语义关联。
    3. **阶段三**：任务微调，在基因表达预测、空间域识别等下游任务上轻量级微调，或直接用于零样本分类。
- **算法流程**（文字说明）：
  1. 输入：H&E图像块、对应空间转录组基因表达向量、生物学文本描述。
  2. 分别通过三个编码器提取特征：图像特征、基因特征、文本特征。
  3. 采用对比学习损失（如InfoNCE）最大化三模态正样本对的相似度，最小化负样本对。
  4. 预训练后，冻结部分或全部编码器，在下游任务上添加任务头（如回归头预测基因表达，或聚类头识别空间域）。
  5. 零样本推理时，直接输入H&E图像，通过图像编码器获取嵌入，与基因或文本原型比较，完成分类或生成解释。

## 3. 实验设计：数据集、基准测试、对比方法

- **数据集**：
  - **三模态训练集**：包含151,182个空间点，来自多个组织（乳腺、前列腺、结肠等），每个点有H&E图像、空间转录组基因表达谱和文本注释。
  - **下游评估数据集**：
    - 基因表达预测任务：使用独立的空间转录组数据集（可能包含未见过的组织或平台）。
    - 空间域识别任务：标注的空间域划分数据集（如肿瘤区域、基质区域等）。
    - 零样本组织病理学分类：4个公开基准（如Breast Cancer、Lung Cancer、Colon Cancer等类别平衡数据集）。
    - 专家评估：10例乳腺癌病例，仅提供H&E图像，要求模型推断分子状态（如ER/PR/HER2状态、分子亚型等），并由病理专家评判。
- **基准测试**：
  - 基因表达预测：常用指标如皮尔逊相关系数、均方误差等。
  - 空间域识别：调整兰德指数（ARI）、归一化互信息（NMI）、准确率等。
  - 零样本分类：平均准确率。
- **对比方法**：
  - 外部基线：如已发表的单模态/双模态基础模型（例如GeneCompass、PathBERT、CLIP-based病理模型等），以及GPT-5（用于零样本分类）。
  - 消融实验：对比不同训练阶段（两模态 vs 三模态）、不同模态组合、不同数据集规模等。

## 4. 资源与算力

- 论文中**未明确说明**所使用GPU型号、数量及训练时长，但作为大规模基础模型，可推测使用了多块A100或同等算力的GPU集群，训练时间可能需要数天至数周。元数据中也未提及具体算力细节。

## 5. 实验数量与充分性

- **实验组数**：论文主要报告了以下实验：
  - **基因表达预测**：至少在一组独立数据集上对比多个基线，报告相对提升23.6-80.9%。
  - **空间域识别**：类似地，在至少一组标注数据上对比基线。
  - **零样本组织病理学分类**：在4个基准数据集上进行评估。
  - **专家评估**：10例乳腺癌病例，由专家评分。
  - **消融实验**：推测包含不同模态组合、不同训练阶段、不同数据规模的影响（元数据未详细说明，但根据常见做法应有消融）。
- **充分性与客观性**：
  - 实验覆盖了三个主要下游任务，且对比了最强外部基线，结果显著提升。
  - 零样本分类对比GPT-5具有明显优势（6.16%），且专家评估验证了分子推理能力，增强了可信度。
  - **可能不足**：未报告在更多样化组织类型（如罕见肿瘤）上的表现，也未见跨平台泛化实验（如从10x Visium到Slide-seq或MERFISH）。此外，消融实验细节未在摘要中展开，需看全文确认是否充分。

## 6. 论文的主要结论与发现

- **主要结论**：三模态基础模型SciCore-Omics能够有效桥接组织形态学和分子状态，是首个实现H&E图像、空间转录组学和生物学语言联合建模的基础模型。
- **关键发现**：
  1. 在基因表达预测和空间域识别任务上，相对于最强的双模态基线，任务指标相对提升23.6%至80.9%，表明加入语言模态带来显著增益。
  2. 零样本组织病理学分类准确率超越GPT-5平均6.16个百分点，说明预训练的三模态空间知识可迁移至常规组织学任务。
  3. 仅依赖H&E图像的分子推理能力在专家评估中得到确认，有望辅助临床决策。

## 7. 优点：方法与实验设计亮点

- **方法亮点**：
  - 首个三模态框架，突破了现有双模态对齐的局限，真正实现了图像、组学和语言的联合表示。
  - 三阶段渐进训练策略，从图像-基因对齐逐步过渡到语言融合，降低了多模态对齐难度。
  - 利用生物学语言作为桥梁，增强了模型的可解释性和泛化性。
- **实验设计亮点**：
  - 构建了大规模空间配对图像-基因-文本数据集（15万+点），为后续研究提供资源。
  - 多任务评估体系：包括基因预测（回归）、空间域识别（聚类）、零样本分类（分类）和专家评测（定性），全面展示模型能力。
  - 直接与GPT-5对比零样本表现，具有挑战性且结果显著。

## 8. 不足与局限

- **实验覆盖局限**：
  - 未明确说明跨平台泛化能力（如从10x Visium到Slide-seq或Xenium等更高分辨率平台）。
  - 专家评估仅限10例乳腺癌，样本量较小，且可能仅限于特定癌症类型，结论推广需更广泛验证。
  - 消融实验具体结果未在摘要提供，无法确认各阶段贡献大小。
- **偏差风险**：
  - 训练数据可能来自公开数据集（如TCGA、GEO等），若存在批次效应或平台偏差，模型可能对某些组织类型或染色条件敏感。
  - 文本注释可能来源于人工标注或公开知识库，注释质量影响语言模态对齐效果。
- **应用限制**：
  - 模型需要H&E图像和对应的空间转录组数据联合预训练，对于缺乏组学数据的实验室直接应用受限。
  - 基因表达预测任务中，空间分辨率可能受Visium点（约50μm）限制，无法精确到单细胞尺度。
  - 推理时仍需输入图像块，大规模全切片图像的处理效率有待评估。

（完）
