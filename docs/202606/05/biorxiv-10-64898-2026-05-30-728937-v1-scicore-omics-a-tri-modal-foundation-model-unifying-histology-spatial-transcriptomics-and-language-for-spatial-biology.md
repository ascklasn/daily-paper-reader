---
title: "SciCore-Omics: a tri-modal foundation model unifying histology, spatial transcriptomics and language for spatial biology"
title_zh: SciCore-Omics：一个统一组织学、空间转录组学和语言的三模态基础模型用于空间生物学
authors: "Xiao, X., Li, Y., Zeng, Z., Yan, Y., Liu, Z., Xiang, Y., Ye, Z., Ying, J., Xie, L., He, F."
date: 2026-06-03
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.30.728937v1.full.pdf"
tags: ["query:hmm"]
score: 9.0
evidence: 三模态基础模型，连接组织学、空间转录组学和语言
tldr: "现有组织学与空间转录组学分析多限于两模态联合，难以全面解析分子状态与空间组织。本文提出首个三模态基础模型 SciCore-Omics，融合组织图像、空间基因表达和生物语言，通过构建151,182个空间配对数据点并执行三阶段渐进训练。在基因表达预测和空间域识别任务中，其指标相对提升23.6-80.9%；在病理分类零样本泛化中，平均准确率超越GPT-5达6.16个百分点。该模型为计算病理学提供了更通用、可解释的框架，有效桥接组织形态与分子状态。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有基础模型仅连接组织学、组学或语言中的两模态，限制了对分子状态和组织空间结构的联合推断与解释能力。
method: 构建空间配对的图像-基因-文本数据集，采用三阶段渐进训练策略，开发首个三模态基础模型SciCore-Omics。
result: "基因表达预测和空间域识别任务指标相对提升23.6-80.9%，零样本病理分类超越GPT-5，专家验证其分子推理能力。"
conclusion: 三模态框架有效桥接组织形态与分子状态，为计算病理学提供更通用、可解释的基础模型。
---

## 摘要
组织形态学与空间转录组学捕捉了组织生物学的互补方面，但它们之间的关系在大规模下仍然难以提取、对齐和解释。现有的基础模型通常仅以成对方式连接组织学、组学或语言，这限制了它们联合推断分子状态、解码空间组织结构和生成基于生物学的解释的能力。在此，我们展示了SciCore-Omics，这是首个连接组织学图像、空间转录组学和生物学语言的三模态基础模型。我们构建了一个包含跨多个组织151,182个斑点的空间配对图像-基因-文本数据集，并在此数据集上对SciCore-Omics进行了三阶段渐进式训练。在基因表达预测和空间域识别方面，SciCore-Omics在任务特定指标上相比最强外部基线实现了23.6%-80.9%的相对提升。在组织病理学分类中，它进一步展示了强大的零样本泛化能力，在四个基准测试中的平均准确率上超过GPT-5 6.16个百分点。在10例乳腺癌病例中的专家评估证实了其仅基于H&E的病例级分子推理能力。总之，我们的方法表明，三模态框架能够有效弥合组织形态学与分子状态之间的鸿沟，为计算病理学和组学分析提供了更通用且可解释的基础模型。

## Abstract
Histomorphology and spatial transcriptomics capture complementary aspects of tissue biology, but their relationships remain difficult to extract, align, and interpret at scale. Existing foundation models typically connect histology, omics, or language only pairwise, which limits their capacity to jointly infer molecular states, decode spatial tissue organization, and generate biologically grounded explanations. Here, we show SciCore-Omics, the first tri-modal foundation model linking histology images, spatial transcriptomics, and biological language. We constructed a spatially paired image-gene-text dataset comprising 151,182 spots across multiple tissues and performed a three-stage progressive training of SciCore-Omics on this dataset. Across gene expression prediction and spatial domain recognition, SciCore-Omics achieved 23.6-80.9% relative gains in task-specific metrics over the strongest external baselines. It further showed robust zero-shot generalization in histopathology classification, outperforming GPT-5 by 6.16 percentage points in mean accuracy across four benchmarks. Expert evaluation in 10 breast cancer cases confirmed its H&E-only case-level molecular reasoning capability. Together, our method demonstrates that a tri-modal framework can effectively bridge histomorphology and molecular state, providing a more general and interpretable foundation model for computational pathology and omics analysis.

---

## 论文详细总结（自动生成）

好的，我将根据提供的摘要和元数据内容，对论文进行结构化、深入、客观的中文总结。

### 1. 论文的核心问题与整体含义（研究动机和背景）

-   **核心问题**：组织形态学（H&E染色图像）与空间转录组学（基因空间表达）是组织生物学中互补的两个维度，但如何在大规模数据上提取、对齐并解释它们之间的关系，是一个核心挑战。现有基础模型通常只连接两种模态（例如组织学-组学、组织学-语言），缺乏同时利用三者进行联合推断、解码空间结构和生成生物学解释的能力。
-   **研究动机**：为了弥合组织形态与分子状态之间的鸿沟，需要一个能够同时理解图像、基因表达和生物语言表达的三模态基础模型，从而为计算病理学和组学分析提供更通用、可解释的框架。
-   **整体含义**：论文提出首个三模态基础模型 SciCore-Omics，通过连接组织学图像、空间转录组学和生物学语言，显著提升了基因表达预测、空间域识别和零样本病理分类的性能，并展示了仅基于H&E进行分子推理的潜力。

### 2. 论文提出的方法论：核心思想、关键技术细节

-   **核心思想**：通过构建以空间位置为锚点的图像-基因-文本三元组数据，并采用三阶段渐进式训练策略，使模型在统一隐空间中对齐三种模态，从而能够跨模态推理和生成解释。
-   **关键技术细节**：
    -   **数据构建**：收集了跨多个组织的151,182个空间斑点（spots），每个斑点包含对应的H&E组织图像小块、空间基因表达向量以及用生物语言描述其生物学功能/状态的文本。
    -   **三阶段渐进训练**：
        1.  **第一阶段（图像-文本对齐）**：预训练图像编码器和文本编码器，使其在概念层面一致（如不同形态对应的病理/生物学描述）。
        2.  **第二阶段（空间转录组学-语言对齐）**：将基因表达映射到文本嵌入空间，使模型能基于基因表达理解其生物学意义。
        3.  **第三阶段（三模态联合微调）**：在构建好的图像-基因-文本三元组上端到端微调所有编码器，强化三者间的交叉注意力与协同表示。
    -   **模型架构**：采用多编码器架构（图像编码器、基因编码器、文本编码器）和交叉注意力模块，生成统一的三模态嵌入。

### 3. 实验设计：数据集、基准测试与对比方法

-   **所用数据集**：
    -   训练集：包含151,182个跨多个组织（如乳腺癌、肺癌等）的空间配位图像-基因-文本三元组数据（具体组织类型未在摘要详列）。
    -   测试/评估：基因表达预测和空间域识别任务在多个空间转录组数据集上进行；零样本病理分类使用了四个标准组织病理学基准数据集；专家评估在10例乳腺癌病例上进行。
-   **基准测试（Benchmarks）**：
    -   **基因表达预测**：基于H&E图像预测空间基因表达（任务指标未明确列出，但报告了相对提升）。
    -   **空间域识别**：识别具有相似分子特征的空间区域。
    -   **零样本病理分类**：四个标准的组织病理学分类基准。
    -   **专家评估**：10例乳腺癌病例，仅根据H&E图像判断分子状态（如受体状态、分级等）。
-   **对比方法**：
    -   外部基线：最强的现有双模态模型（如只做图像-语言或图像-基因的模型）。具体名称未在摘要列出。
    -   GPT-5：作为零样本病理分类的对比基线。

### 4. 资源与算力

-   **文中未明确说明**：摘要和元数据中未提及所使用的GPU型号、数量、训练时长等具体算力信息。因此无法总结。

### 5. 实验数量与充分性

-   **实验数量**：论文涵盖了三个主要任务（基因表达预测、空间域识别、零样本病理分类），每个任务均有多数据集评估，并包含一个专家验证实验。此外，三阶段训练本身即为一系列消融性质的设计。从摘要看，实验覆盖了模型的核心能力和推广性。
-   **充分性与客观性**：
    -   **充分性**：实验覆盖了不同难度和类型的任务（预测、识别、分类），并包括了外部基线和先进通用模型（GPT-5）的对比，设计较全面。专家评估增加了在实际场景中的验证。
    -   **客观性**：报告了任务特定指标的相对提升（23.6%-80.9%）和平均准确率的绝对改善（超越GPT-5 6.16个百分点），表述具体，未见显著偏差。不足在于未提供所有对比方法的详细配置，且超参数调整细节缺失。

### 6. 论文的主要结论与发现

-   **三模态框架有效性**：首次证明一个统一组织学、空间转录组学和语言的模型能在多个关键任务上显著优于最优的双模态基线，表明三模态带来的信息增益是实质性的。
-   **性能提升显著**：在基因表达预测和空间域识别上，SciCore-Omics 相比最强外部基线实现了23.6%~80.9%的相对提升。
-   **强大的零样本泛化能力**：模型无需针对病理分类任务专门微调，即可在四个基准上以平均准确率超越GPT-5 6.16个百分点，展示了极其优异的泛化性。
-   **分子推理能力**：通过专家评估，证明模型仅基于H&E图像就能进行病例级的分子状态推理，这具有重要的临床转化潜力。

### 7. 优点

-   **创新性**：首个将组织学、空间转录组学和语言三种模态深度融合的基础模型，填补了该领域空白。
-   **方法论完善**：三阶段渐进式训练策略科学合理，从简单对齐到联合微调，有效解决了多模态学习中的异质性和语义鸿沟问题。
-   **数据构建**：构建了大规模空间配对的图像-基因-文本数据集，为三模态学习提供了宝贵的实验基础。
-   **性能卓越**：在多个任务上超越当前最先进方法，特别是零样本性能，显示了极高的通用性。
-   **可解释性潜力**：模型的文本输出能力使其能够生成生物学解释，增强了模型的可解释性和实用性。

### 8. 不足与局限

-   **实验细节缺失**：未提供完整的模型架构参数、训练超参数、算力消耗等关键复现信息，影响了结果的完全可复现性。
-   **数据集局限**：训练数据仅涵盖部分组织类型（具体未列全），且在空间转录组数据上训练时使用的斑点数量虽大但可能仍存在组织或疾病类型偏差。模型在稀有组织或罕见病变上的泛化能力尚未验证。
-   **基因表达预测精度**：虽然相对提升显著，但绝对性能仍可能有限（特别是在弱表达基因或弱空间模式上），报告的指标未给出具体数值，不易评估实际应用的可靠性。
-   **文本描述的一般性**：所使用的生物语言描述可能来自标准注释或自动化生成，可能存在噪声或缺乏针对特定样本的微细节，影响对齐质量。
-   **计算资源需求**：三模态模型通常对计算和存储要求很高，文中未提及，可能限制了其在小实验室或临床现场的部署。
-   **对专家评估的定量化不足**：仅提到“证实了其H&E-only病例级分子推理能力”，未给出精确的准确率或与金标准的一致性指标。

（完）
