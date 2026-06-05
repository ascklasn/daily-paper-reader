---
title: "SciCore-Omics: a tri-modal foundation model unifying histology, spatial transcriptomics and language for spatial biology"
title_zh: SciCore-Omics：一种统一组织学、空间转录组学和语言的三模态基础模型，用于空间生物学
authors: "Xiao, X., Li, Y., Zeng, Z., Yan, Y., Liu, Z., Xiang, Y., Ye, Z., Ying, J., Xie, L., He, F."
date: 2026-06-04
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.30.728937v2.full.pdf"
tags: ["query:hmm"]
score: 9.0
evidence: 三模态基础模型统一组织学、空间转录组和语言
tldr: "现有基础模型仅支持两模态配对，难以联合推断分子状态和解释空间组织。本文提出首个三模态基础模型SciCore-Omics，构建151,182个空间配对的图像-基因-文本数据集，通过三阶段渐进训练统一组织学、空间转录组学和语言。在基因表达预测和空间域识别任务上，相对最强外部基线提升23.6-80.9%；零样本病理分类平均准确率超越GPT-5达6.16个百分点。该框架有效桥接形态与分子状态，为计算病理和组学分析提供更通用可解释的基础模型。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有模型仅支持两模态配对，无法联合推断分子状态和解释空间组织。
method: 构建空间配对的图像-基因-文本数据集，三阶段渐进训练三模态基础模型。
result: "基因表达和空间域识别任务提升23.6-80.9%，零样本病理分类超越GPT-5 6.16个百分点。"
conclusion: 三模态框架有效桥接组织形态和分子状态，提供更通用可解释的基础模型。
---

## 摘要
组织形态学和空间转录组学捕捉了组织生物学的互补方面，但它们之间的关系在大规模上仍然难以提取、对齐和解释。现有的基础模型通常仅以成对方式连接组织学、组学或语言，这限制了它们联合推断分子状态、解码空间组织结构和生成具有生物学基础的解释的能力。在此，我们展示了SciCore-Omics，这是首个连接组织学图像、空间转录组学和生物语言的三模态基础模型。我们构建了一个空间配对的图像-基因-文本数据集，包含跨多个组织的151,182个点，并在该数据集上对SciCore-Omics进行了三阶段渐进式训练。在基因表达预测和空间域识别方面，SciCore-Omics在任务特定指标上相对于最强的外部基线实现了23.6-80.9%的相对提升。它还在组织病理学分类中展示了强大的零样本泛化能力，在四个基准测试中的平均准确率上比GPT-5高出6.16个百分点。在10例乳腺癌病例中的专家评估确认了其仅基于H&E切片的病例级分子推理能力。总之，我们的方法表明，三模态框架可以有效地桥接组织形态学和分子状态，为计算病理学和组学分析提供了更通用和可解释的基础模型。

## Abstract
Histomorphology and spatial transcriptomics capture complementary aspects of tissue biology, but their relationships remain difficult to extract, align, and interpret at scale. Existing foundation models typically connect histology, omics, or language only pairwise, which limits their capacity to jointly infer molecular states, decode spatial tissue organization, and generate biologically grounded explanations. Here, we show SciCore-Omics, the first tri-modal foundation model linking histology images, spatial transcriptomics, and biological language. We constructed a spatially paired image-gene-text dataset comprising 151,182 spots across multiple tissues and performed a three-stage progressive training of SciCore-Omics on this dataset. Across gene expression prediction and spatial domain recognition, SciCore-Omics achieved 23.6-80.9% relative gains in task-specific metrics over the strongest external baselines. It further showed robust zero-shot generalization in histopathology classification, outperforming GPT-5 by 6.16 percentage points in mean accuracy across four benchmarks. Expert evaluation in 10 breast cancer cases confirmed its H&E-only case-level molecular reasoning capability. Together, our method demonstrates that a tri-modal framework can effectively bridge histomorphology and molecular state, providing a more general and interpretable foundation model for computational pathology and omics analysis.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义
- **研究动机**：组织形态学（H&E染色图像）和空间转录组学分别捕捉组织生物学的互补方面，但现有基础模型仅支持两模态配对（如图像-文本、图像-基因或基因-文本），无法联合推断分子状态、解码空间组织结构并生成生物学解释。
- **整体含义**：本文提出首个三模态基础模型 **SciCore-Omics**，统一组织学图像、空间转录组学和生物语言，为计算病理学和组学分析提供更通用、可解释的框架。

### 2. 方法论
- **核心思想**：通过构建空间配对的图像-基因-文本数据集，采用三阶段渐进式训练，对齐三个模态的表示，从而实现对组织形态与分子状态的联合推理。
- **关键技术细节**：
  - **数据集构建**：收集涵盖多个组织的 **151,182 个点**（spots），每个点包含对应的H&E图像块、空间转录组表达向量以及生物学文本描述（如基因功能注释或空间域标签）。
  - **三阶段渐进训练**：
    1. **第一阶段**：对图像编码器和基因编码器进行对比学习，对齐图像-基因配对。
    2. **第二阶段**：引入文本编码器，通过跨模态对比损失（image-text, gene-text）进一步对齐语言与视觉/组学模态。
    3. **第三阶段**：联合训练所有编码器，使用统一的对比学习目标，使三模态嵌入空间一致。
- **算法流程**（文字说明）：输入一个H&E图像块 → 图像编码器提取视觉特征；输入对应点的基因表达向量 → 基因编码器提取组学特征；输入文本描述（如“肿瘤区域高表达ERBB2”）→ 文本编码器提取语义特征。三阶段训练中，依次或联合优化各模态之间的对比损失，最终使同一点的三模态表示在嵌入空间中接近。

### 3. 实验设计
- **数据集与场景**：
  - 训练集：自建的空间配对图像-基因-文本数据集（151,182 个点，跨多个组织）。
  - 下游任务：
    1. **基因表达预测**：基于H&E图像预测空间点的基因表达。
    2. **空间域识别**：根据图像和表达特征划分组织功能区域。
    3. **零样本组织病理学分类**：在四个公开基准数据集上测试（如乳腺癌、肺癌等）。
    4. **病例级分子推理**：10例乳腺癌病例，仅基于H&E切片进行专家评估。
- **基准与方法对比**：
  - 对比方法：最强外部基线（包括两模态模型）、GPT-5（用于零样本分类）。
  - 评价指标：任务特定指标（如基因表达预测的相关系数、空间域识别的ARI/NMI）、分类准确率。
- **结果**：
  - 基因表达预测和空间域识别：相对最强外部基线提升 **23.6–80.9%**。
  - 零样本病理分类：平均准确率超越GPT-5 **6.16 个百分点**。
  - 专家评估：10例乳腺癌病例中确认了H&E-only的分子推理能力。

### 4. 资源与算力
- **文中未明确说明**所使用的GPU型号、数量及训练时长。仅提及使用自建数据集和三阶段渐进训练，但具体硬件配置和计算开销未公开。

### 5. 实验数量与充分性
- **实验数量**：覆盖了四个主要任务（基因表达预测、空间域识别、零样本分类、病例级验证），但未提及详细的消融实验（如不同阶段训练对性能的贡献、不同模态组合的对比）。
- **充分性与公平性**：
  - 在多个任务上与多个基线对比（包括GPT-5），结果显著提升，表明方法有效。
  - 专家评估提供了定性验证，增强了可信度。
  - **不足**：缺乏对数据集规模、组织多样性、模型泛化边界的系统分析；未报告消融实验，难以判断三阶段设计是否最优；未对计算资源/效率进行对比。

### 6. 主要结论与发现
- 三模态框架（图像-基因-文本）能有效桥接组织形态学与分子状态，在预测任务上大幅优于两模态模型。
- 零样本泛化能力强，在病理分类上超越GPT-5（当时最强的语言模型）。
- 仅用H&E图像即可进行有意义的分子层面推理，为临床诊断提供潜在工具。

### 7. 优点
- **创新性**：首个三模态基础模型，统一了组织学、空间转录组学和语言，突破了现有两模态配对的限制。
- **数据建设**：构建了15万+空间配对的图像-基因-文本数据集，为后续研究提供资源。
- **训练策略**：三阶段渐进式对齐，逐步融合模态，可能避免过早过拟合。
- **零样本能力**：在病理分类上超越GPT-5，显示对语言的强大理解与迁移能力。
- **应用验证**：专家评估确认了分子推理的临床相关性，增强方法实用性。

### 8. 不足与局限
- **数据规模与覆盖**：仅15万点，可能不足以覆盖组织类型和疾病的多样性；空间转录组数据来源可能局限于特定平台（如10x Visium）。
- **实验设计**：缺少消融实验（如两模态 vs 三模态、训练阶段顺序的影响）和模型效率对比；未报告在无空间配对的真实病例上的泛化性能。
- **偏差风险**：训练数据中可能隐含批次效应或病理标签偏差，未讨论公平性和伦理问题。
- **应用限制**：当前仅基于H&E图像推理分子状态，实际临床中需结合多模态数据；模型的可解释性（如何解释推理过程）未深入分析。
- **资源信息缺失**：算力开销未知，难以评估复现成本。

（完）
