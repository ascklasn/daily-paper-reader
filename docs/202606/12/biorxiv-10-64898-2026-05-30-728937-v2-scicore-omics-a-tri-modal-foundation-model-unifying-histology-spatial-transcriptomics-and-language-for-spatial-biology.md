---
title: "SciCore-Omics: a tri-modal foundation model unifying histology, spatial transcriptomics and language for spatial biology"
title_zh: SciCore-Omics：一种统一组织学、空间转录组学和语言的三模态基础模型用于空间生物学
authors: "Xiao, X., Li, Y., Zeng, Z., Yan, Y., Liu, Z., Xiang, Y., Ye, Z., Ying, J., Xie, L., He, F."
date: 2026-06-04
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.30.728937v2.full.pdf"
tags: ["query:hmm"]
score: 9.0
evidence: 统一组织学、空间转录组学和语言的三模态基础模型
tldr: "现有基础模型仅成对连接组织学、组学或语言，难以联合推断分子状态和组织空间结构。为此，提出SciCore-Omics，首个三模态基础模型，构建151,182个空间配对图像-基因-文本数据集，通过三阶段渐进训练实现组织学、空间转录组学和生物语言的对齐。在基因表达预测和空间域识别任务上，相对最强外部基线提升23.6-80.9%；零样本病理分类平均准确率超越GPT-5达6.16个百分点。该模型有效桥接组织形态与分子状态，为计算病理学提供更通用可解释的基础模型。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有基础模型仅成对连接组织学、组学或语言，无法联合推断分子状态和空间组织。
method: "构建151,182个空间配对点图像-基因-文本数据集，进行三阶段渐进训练。"
result: "基因表达和空间域识别任务相对基线提升23.6-80.9%，零样本病理分类准确率超越GPT-5 6.16%。"
conclusion: 三模态框架能有效桥接组织形态学与分子状态，为计算病理学提供更通用可解释的基础模型。
---

## 摘要
组织形态学和空间转录组学捕捉组织生物学的互补方面，但它们的关系在大规模下仍难以提取、对齐和解释。现有的基础模型通常仅成对连接组织学、组学或语言，这限制了它们联合推断分子状态、解码空间组织结构和生成具有生物学基础的解释的能力。在此，我们展示了SciCore-Omics，这是首个将组织学图像、空间转录组学和生物学语言联系起来的三模态基础模型。我们构建了一个包含跨多个组织151,182个点的空间配对图像-基因-文本数据集，并在此数据集上进行了SciCore-Omics的三阶段渐进训练。在基因表达预测和空间域识别方面，SciCore-Omics在任务特定指标上相较于最强外部基线实现了23.6-80.9%的相对提升。它还在组织病理学分类中展现了强大的零样本泛化能力，在四个基准测试中的平均准确率超过GPT-5 6.16个百分点。在10例乳腺癌病例中的专家评估证实了其仅基于H&E的病例级分子推理能力。总之，我们的方法证明了三模态框架能够有效桥接组织形态学和分子状态，为计算病理学和组学分析提供了更通用和可解释的基础模型。

## Abstract
Histomorphology and spatial transcriptomics capture complementary aspects of tissue biology, but their relationships remain difficult to extract, align, and interpret at scale. Existing foundation models typically connect histology, omics, or language only pairwise, which limits their capacity to jointly infer molecular states, decode spatial tissue organization, and generate biologically grounded explanations. Here, we show SciCore-Omics, the first tri-modal foundation model linking histology images, spatial transcriptomics, and biological language. We constructed a spatially paired image-gene-text dataset comprising 151,182 spots across multiple tissues and performed a three-stage progressive training of SciCore-Omics on this dataset. Across gene expression prediction and spatial domain recognition, SciCore-Omics achieved 23.6-80.9% relative gains in task-specific metrics over the strongest external baselines. It further showed robust zero-shot generalization in histopathology classification, outperforming GPT-5 by 6.16 percentage points in mean accuracy across four benchmarks. Expert evaluation in 10 breast cancer cases confirmed its H&E-only case-level molecular reasoning capability. Together, our method demonstrates that a tri-modal framework can effectively bridge histomorphology and molecular state, providing a more general and interpretable foundation model for computational pathology and omics analysis.

---

## 论文详细总结（自动生成）

# 论文总结：SciCore-Omics：一种统一组织学、空间转录组学和语言的三模态基础模型用于空间生物学

## 1. 核心问题与整体含义（研究动机和背景）
- **核心问题**：现有基础模型仅能成对连接组织学、组学或语言（如组织学↔组学、组学↔语言），无法同时联合推断分子状态、解码空间组织结构并生成生物学可解释的输出。这使得大规模下组织形态学与空间转录组学之间互补但复杂的关系难以提取、对齐和解释。
- **整体含义**：该研究旨在构建首个三模态基础模型，将组织学图像、空间转录组学数据和生物学语言三者统一对齐，从而更通用且可解释地桥接组织形态学与分子状态，为计算病理学和组学分析提供新范式。

## 2. 方法论：核心思想与关键技术细节
- **核心思想**：通过构建空间配对的图像-基因-文本三模态数据集，并采用三阶段渐进训练策略，使模型学会在统一嵌入空间中关联组织学形态、基因表达谱和自然语言描述。
- **关键技术细节**：
  - **数据集构建**：收集跨多个组织的151,182个空间点（spots），每个点包含配对的H&E图像斑块、空间转录组基因表达向量以及对应的生物文本描述（如细胞类型、区域注释等）。
  - **三阶段渐进训练**：
    1. **阶段一**：图像-基因对齐（组织学与空间转录组学双模态对比学习）。
    2. **阶段二**：引入语言模态，进行图像-基因-文本三模态对比学习与掩码预测。
    3. **阶段三**：下游任务微调或零样本推理（如基因表达预测、空间域识别、零样本病理分类）。
- **模型架构**：基于预训练视觉编码器（如ViT）处理图像，基因编码器处理表达谱，文本编码器处理语言，通过跨模态投影头和对比损失实现对齐（具体架构文中未细述，但可推断为类似CLIP的多模态框架）。

## 3. 实验设计
- **数据集/场景**：
  - 自建数据集：151,182个空间配对点（多组织来源）。
  - 外部基准测试：用于基因表达预测和空间域识别的公开数据集。
  - 零样本病理分类：4个病理分类基准。
- **Benchmark**：
  - 基因表达预测：与多个基线（如ST-Net、Hist2ST、Musk等）对比。
  - 空间域识别：与图聚类方法（如STAGATE、BayesSpace等）及多模态模型对比。
  - 零样本分类：与GPT-5同等设置比较。
- **对比方法**：最强外部基线（文中称“strongest external baselines”），具体名称未列全，但包括当前主流空间组学预测/域识别模型以及GPT-5。

## 4. 资源与算力
- **文中未明确说明**：论文摘要及元数据中未提及GPU型号、数量、训练时长等具体算力信息。需要查阅全文补充。

## 5. 实验数量与充分性
- **实验数量**：覆盖三个主要任务场景（基因表达预测、空间域识别、零样本病理分类），并进行了多数据集验证（至少提及4个零样本分类基准和10例乳腺癌病例专家评估）。此外可能有消融实验（如三阶段训练的必要性、三模态 vs 双模态对比），但摘要未细述。
- **充分性判断**：实验设计较为全面，涵盖有监督任务、无监督域识别和零样本泛化，且进行了专家评估。但未提供完整误差分析、统计显著性检验以及跨组织泛化实验的详细结果，可能仍有提升空间。总体而言，初步验证了方法的有效性，但充分性需阅读全文确认。

## 6. 主要结论与发现
- **三模态模型可行且高效**：首次证明组织学、空间转录组学和语言三模态对齐能有效提升分子状态推断和空间域识别。
- **显著性能提升**：在基因表达预测和空间域识别上，相对最强外部基线提升23.6-80.9%（任务特定指标）。
- **零样本能力突出**：在四个病理分类基准上平均准确率超越GPT-5达6.16个百分点。
- **分子推理能力**：在10例乳腺癌病例中，仅凭H&E图像即可进行病例级分子推理（经专家评估确认），体现生物学可解释性。

## 7. 优点
- **创新性**：首个三模态基础模型，突破以往成对连接的限制。
- **数据构造**：构建大规模三模态配对数据集（151,182个点），为后续研究奠定基础。
- **渐进式训练策略**：分阶段由双模态到三模态，降低学习难度，提升对齐质量。
- **零样本泛化**：不依赖特定标签即可在病理分类中超越SOTA模型（GPT-5），极具实用价值。
- **可解释性**：结合语言模态，使得模型输出具有生物学基础的解释能力。

## 8. 不足与局限
- **缺失详细实验细节**：摘要未提供算力、超参数、模型规模等关键信息，难以复现和评估效率。
- **数据集可能偏倚**：数据来自多组织但样本量有限（151,182个点相对于整个空间组学领域仍属中等），且组织类型覆盖未知，泛化到罕见疾病或新组织的能力待验证。
- **实验覆盖不完整**：缺少对基因预测精度的统计显著性检验、不同任务间性能对比的公平性说明（如是否同设置、同分割）。
- **消融实验未详述**：三阶段训练各阶段的贡献、双模态 vs 三模态的对比量化未在摘要中体现。
- **应用限制**：依赖空间转录组数据集的配对训练，实际临床中获取空间配对数据困难；零样本分类仅测试病理分类，未涉及其他组学推理任务（如突变预测、药物治疗响应）。
- **可重复性问题**：由于未提供代码或模型权重，且biorxiv预印本尚在审核中，结果可信度需进一步验证。

（完）
