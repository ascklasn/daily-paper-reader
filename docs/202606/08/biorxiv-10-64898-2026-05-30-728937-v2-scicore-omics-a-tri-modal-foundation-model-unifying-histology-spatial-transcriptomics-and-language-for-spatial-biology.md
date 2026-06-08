---
title: "SciCore-Omics: a tri-modal foundation model unifying histology, spatial transcriptomics and language for spatial biology"
title_zh: SciCore-Omics：一种统一组织学、空间转录组学和语言的三模态基础模型用于空间生物学
authors: "Xiao, X., Li, Y., Zeng, Z., Yan, Y., Liu, Z., Xiang, Y., Ye, Z., Ying, J., Xie, L., He, F."
date: 2026-06-04
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.30.728937v2.full.pdf"
tags: ["query:hmm"]
score: 9.0
evidence: 连接组织学、空间转录组和语言的三模态基础模型
tldr: "组织形态学与空间转录组学的联合分析面临跨模态对齐难题。现有基础模型仅能处理两两模态，无法联合推断分子状态与空间组织。本文构建了首个三模态基础模型SciCore-Omics，通过配对图像-基因-文本数据集进行三阶段训练。在基因表达预测和空间域识别任务上，相比最强基线提升23.6-80.9%，并实现鲁棒零样本泛化。该模型为计算病理学提供了更通用可解释的基础。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有基础模型仅连接组织学、组学或语言中的两两模态，无法联合推断分子状态和解码空间组织。
method: "构建包含151,182个斑点的配对图像-基因-文本数据集，进行三阶段渐进式训练，学习组织学、空间转录组学与语言的对齐。"
result: "基因表达预测和空间域识别任务相对最强基线提升23.6-80.9%；零样本病理分类平均准确率超GPT-5达6.16个百分点。"
conclusion: 三模态框架有效桥接组织形态学与分子状态，为计算病理学提供更通用、可解释的基础模型。
---

## 摘要
组织形态学和空间转录组学捕捉组织生物学的互补方面，但它们之间的关系在大规模下仍然难以提取、对齐和解释。现有的基础模型通常仅成对连接组织学、组学或语言，这限制了它们联合推断分子状态、解码空间组织结构和生成生物学基础解释的能力。在这里，我们展示了SciCore-Omics，这是首个连接组织学图像、空间转录组学和生物语言的三模态基础模型。我们构建了一个空间配对的图像-基因-文本数据集，包含跨多个组织的151,182个斑点，并在此数据集上对SciCore-Omics进行了三阶段渐进式训练。在基因表达预测和空间域识别方面，与最强的外部基线相比，SciCore-Omics在任务特定指标上实现了23.6%-80.9%的相对提升。它还在组织病理学分类中展示了强大的零样本泛化能力，在四个基准测试中平均准确率超过GPT-5 6.16个百分点。在10例乳腺癌病例中的专家评估证实了其仅依赖H&E染色的病例级分子推理能力。总之，我们的方法表明，三模态框架可以有效地桥接组织形态学和分子状态，为计算病理学和组学分析提供更通用且可解释的基础模型。

## Abstract
Histomorphology and spatial transcriptomics capture complementary aspects of tissue biology, but their relationships remain difficult to extract, align, and interpret at scale. Existing foundation models typically connect histology, omics, or language only pairwise, which limits their capacity to jointly infer molecular states, decode spatial tissue organization, and generate biologically grounded explanations. Here, we show SciCore-Omics, the first tri-modal foundation model linking histology images, spatial transcriptomics, and biological language. We constructed a spatially paired image-gene-text dataset comprising 151,182 spots across multiple tissues and performed a three-stage progressive training of SciCore-Omics on this dataset. Across gene expression prediction and spatial domain recognition, SciCore-Omics achieved 23.6-80.9% relative gains in task-specific metrics over the strongest external baselines. It further showed robust zero-shot generalization in histopathology classification, outperforming GPT-5 by 6.16 percentage points in mean accuracy across four benchmarks. Expert evaluation in 10 breast cancer cases confirmed its H&E-only case-level molecular reasoning capability. Together, our method demonstrates that a tri-modal framework can effectively bridge histomorphology and molecular state, providing a more general and interpretable foundation model for computational pathology and omics analysis.

---

## 论文详细总结（自动生成）

好的，请查收基于提供的论文摘要和元数据生成的详细中文总结。

## 论文详细中文总结

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：组织形态学（组织学图像）和空间转录组学（分子表达谱）是组织生物学的两个互补视角，但大尺度下它们之间的关系难以提取、对齐和解释。现有的基础模型通常只能处理两两模态（如组织学+组学，或组织学+语言），缺乏联合推断分子状态、解码空间组织结构并生成生物学解释的能力。
- **研究动机**：构建一个能够统一组织学图像、空间转录组数据和生物语言的三模态基础模型，以桥接组织形态学与分子状态，实现更通用、可解释的计算病理学分析。
- **整体含义**：该工作是首个尝试将三种模态（图像、基因、语言）联合建模的基础模型，有望在基因表达预测、空间域识别、零样本病理分类等任务上实现显著性能提升，并推动精准医疗和空间生物学研究。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：通过三阶段渐进式训练，学习组织学图像、空间转录组学（基因表达）和生物语言（文本描述）之间的跨模态对齐。
- **关键技术与流程**：
    1.  **数据集构建**：构建了一个空间配对的图像-基因-文本数据集，包含来自多个组织的 **151,182个斑点（spots）**。每个斑点对应一个组织学局部图像patches、一个基因表达向量以及一个相应的文本描述（如细胞类型、功能注释）。
    2.  **模型架构**：基于现有的两两模态对齐框架扩展为三模态，具体架构未在摘要详细说明，但推测采用对比学习或多模态编码器-解码器结构。
    3.  **三阶段渐进式训练**：
        - 阶段一：组织学图像与空间转录组数据的配对对齐。
        - 阶段二：引入生物语言模态，进行图像-基因-语言三方对齐。
        - 阶段三：端到端微调，增强跨模态推理与生成能力。
- **公式或算法流程**：未在元数据中提供具体公式，但流程可概括为：输入→图像编码器+基因编码器+文本编码器→对比学习损失对齐→联合推理。

### 3. 实验设计：数据集、基准与对比方法

- **数据集**：
    - 自建数据集：包含151,182个空间配对的图像-基因-文本斑点，来源多个组织（具体组织类型未说明）。
    - 零样本病理分类使用了四个标准基准测试（具体名称未列出）。
    - 分子推理评估使用了10例乳腺癌病例。
- **基准任务**：
    - **基因表达预测**：预测给定组织学图像对应斑点的基因表达水平。
    - **空间域识别**：识别组织切片中具有不同分子特性的空间区域。
    - **零样本组织病理学分类**：在未见过的数据集上进行分类。
- **对比方法**：
    - 外部基线（最强基线）：在基因表达预测和空间域识别任务中，与现有最强的外部方法比较（名称未列出）。
    - GPT-5：在零样本分类任务中对比GPT-5的性能。
    - 消融实验：通过移除不同模态或训练阶段验证贡献（虽未明说，但通常包含消融）。

### 4. 资源与算力

- **文中说明**：本次提供的文本（摘要及元数据）**未明确提及**所使用的GPU型号、数量、训练时长等算力细节。
- **需要指出**：仅说明训练数据集包含151,182个斑点，并进行了三阶段训练，但具体硬件资源未公开。这可能是由于篇幅限制或预印本阶段省略。

### 5. 实验数量与充分性

- **实验数量**：至少包括三大类实验：
    - 基因表达预测和空间域识别（性能提升23.6%-80.9%）。
    - 零样本病理分类（4个基准测试，平均准确率超GPT-5 6.16个百分点）。
    - 10例乳腺癌病例的专家评估（定性分子推理）。
- **充分性与公平性**：
    - **充分**：覆盖了基因预测、域识别、零样本泛化、临床案例推理等不同难度的任务，从定量到定性均有验证。
    - **公平**：对比了“最强外部基线”和GPT-5，采用相对提升率（百分比）表示，且零样本设置下避免数据泄露。但未披露基线的具体名称与设置，可能影响透明性。总体而言实验设计较为充分。

### 6. 论文的主要结论与发现

- **主要结论**：三模态基础模型SciCore-Omics能够有效桥接组织形态学和分子状态，为计算病理学提供一个更通用、可解释的基础模型。
- **具体发现**：
    - 在基因表达预测和空间域识别任务上，相比最强基线在任务特定指标上实现 **23.6%-80.9%的相对提升**。
    - 在零样本组织病理学分类中，平均准确率超过GPT-5 **6.16个百分点**，展示了强大的泛化能力。
    - 仅依赖H&E染色图像，模型即可在10例乳腺癌病例中进行合理的分子水平推理（经专家评估确认）。

### 7. 优点：方法或实验设计上的亮点

- **创新性**：**第一个**连接组织学、空间转录组学和语言的三模态基础模型，突破了现有两两模态的局限。
- **训练策略**：三阶段渐进式训练，从两两对齐逐步过渡到三模态联合，降低了复杂多模态对齐的难度。
- **数据规模**：构建了包含15万+配对样本的大型高质量多模态数据集，为模型训练提供了坚实基础。
- **性能显著**：在关键任务上提升幅度大（最高80.9%），零样本泛化甚至超越GPT-5，说明方法有效且鲁棒。
- **跨模态推理**：专家评估验证了模型仅从组织学图像推理分子状态的能力，具有临床转化潜力。

### 8. 不足与局限：包括实验覆盖、偏差风险、应用限制等

- **实验覆盖局限**：
    - 仅测试了基因表达预测、空间域识别和病理分类，未涉及基因调控网络推断、疾病预后预测等更复杂的空间生物学任务。
    - 零样本病理分类仅对比了GPT-5，未与其他专门的病理视觉模型（如RETFound、CTransPath）比较。
- **偏差风险**：
    - 数据来源组织类型未具体说明，若仅来源于某几种组织（如肿瘤），则对不同疾病或正常组织的泛化能力未知。
    - 文本描述可能来自公共数据库或人工注释，存在标注误差或风格不一致。
- **应用限制**：
    - 模型需要空间配对的图像-基因-文本数据进行训练，此类数据获取成本高、样本量有限，可能限制了在更多组织上的扩展。
    - 仅依赖H&E染色图像进行分子推理，目前仅在10例病例中测试，临床验证规模较小，鲁棒性有待更大规模前瞻性研究确认。
    - 未提及模型参数量、推理速度，可能难以直接部署到资源受限场景（如边缘设备）。
- **透明性不足**：未公开对比基线的具体名称、数据集划分细节、超参数设置，可能影响结果的可复现性。

（完）
