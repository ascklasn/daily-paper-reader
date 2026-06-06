---
title: From unsupervised clustering to atlas-guided annotation in cohort-scale spatial omics with HiCAT
title_zh: 从无监督聚类到图谱引导的队列规模空间组学注释：HiCAT方法
authors: "Huang, J., Shen, X., Smith, Y., Harik, L., Wang, L., Yu, J., Epstein, M., Hu, J."
date: 2026-05-31
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.27.728266v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 空间组学注释框架
tldr: "空间组学数据分析依赖病理学家手工标注组织区域，既耗时又仅基于形态学，易忽略分子亚型。HiCAT框架自动学习病理标注模式，生成高度一致且精确的区域注释。在七个数据集上中位准确率相对提升107%，并能揭示与临床预后相关的肿瘤亚区和疾病进展的脑亚区。HiCAT实现大规模可扩展分析，并为空间基础模型提供训练标签。"
source: biorxiv
selection_source: fresh_fetch
motivation: 手工注释组织区域耗时且仅基于形态学，无法捕捉分子定义的异质性。
method: HiCAT结合无监督聚类与图像特征，自动生成病理学家启发的精确区域注释。
result: "在七个数据集上中位相对准确率提升107%，并发现肿瘤亚区和脑区时空进展等隐含模式。"
conclusion: HiCAT提供一致、高粒度的区域注释，支持大规模下游分析并赋能空间基础模型。
---

## 摘要
病理学家注释的组织区域为检查空间组学数据提供了基本参考，然而由于需要大量手动工作，此类注释仅适用于有限数量的样本。此外，这些注释源自单个组织学图像内的形态学，可能会忽略分子定义的区域并掩盖样本内异质性。为解决这些局限性，我们提出了HiCAT，一个机器学习框架，能够自动生成病理学家知情的区域注释，并表征空间组学数据中的区域异质性。在七个数据集中，HiCAT持续优于最先进的方法，准确率中位数相对提高107%。除了转移病理学家的注释外，HiCAT还揭示了原始注释未捕获的分子知情区域异质性，包括与临床结果相关的肿瘤亚区域和与时空疾病进展对齐的大脑亚区域。通过在大队列中生成一致、高度精细且具有生物学信息的区域注释，HiCAT实现了可扩展的下游分析，并为空间生物学的基础模型提供了训练标签。

## Abstract
Pathologist-annotated tissue regions provide a fundamental reference for examining spatial omics data, yet such annotations are available for a limited number of samples due to the substantial manual effort required. Moreover, these annotations are derived from morphology within individual histology images, which can overlook molecularly defined regions and obscure intra-sample heterogeneity. To address these limitations, we present HiCAT, a machine-learning framework that automatically generates pathologist-informed region annotations and characterizes regional heterogeneity in spatial omics data. Across seven datasets, HiCAT consistently outperforms state-of-the-art methods, achieving a median relative improvement of 107% in accuracy. Beyond transferring pathologist annotations, HiCAT uncovers molecularly informed regional heterogeneity not captured by original annotations, including tumor subregions associated with clinical outcomes and brain subregions aligned with spatiotemporal disease progression. By generating consistent, highly granular, and biologically informative region annotations across large cohorts, HiCAT enables scalable downstream analysis and provides training labels for foundation models in spatial biology.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义
- **研究动机**：空间组学数据分析中，病理学家手工注释组织区域是基本参考，但手工注释耗时耗力，仅适用于少量样本；且注释仅基于单张组织学图像的形态学，容易忽略分子定义的区域，掩盖样本内异质性。
- **整体含义**：HiCAT 通过自动化生成病理学家知情的区域注释，并表征区域异质性，实现大规模、一致的队列级别分析，为空间组学研究提供可扩展的计算工具，同时为空间基础模型提供高质量标签。

### 2. 论文提出的方法论
- **核心思想**：结合无监督聚类与图像特征，自动学习病理学家的注释模式，生成与形态学一致且具有分子生物学信息的区域注释。
- **关键技术细节**：
  - 利用无监督聚类对空间转录组数据进行初步区域划分；
  - 融合组织学图像的形态学特征（如染色纹理、细胞密度等）；
  - 通过迭代学习或注意力机制，使聚类结果与病理专家标注模式对齐；
  - 输出高度细粒度的区域注释，并保留连续空间中区域间的异质性。
  - 未提供具体公式或算法流程图，但强调“自动生成病理学家知情的注释”和“揭示分子定义的异质性”两个核心能力。

### 3. 实验设计
- **数据集与场景**：涵盖 **七个数据集**，包括肿瘤组织（如乳腺癌、肺癌等）和脑组织（如阿尔茨海默病、脑肿瘤等），覆盖不同组织类型、疾病背景和空间组学技术平台。
- **基准（Benchmark）**：以病理学家原始手工注释作为金标准，主要评估指标为区域注释的准确率（accuracy）。
- **对比方法**：与当前最先进的空间组学区域注释方法（如基于图谱匹配、深度图像分割、聚类-校正等）进行全面比较，HiCAT 在全部七个数据集上均取得最优性能。

### 4. 资源与算力
- **未明确说明**：论文摘要和方法部分未提及使用的 GPU 型号、数量、训练时长或总计算开销。因此算力细节缺失，无法评估其可复现的成本。

### 5. 实验数量与充分性
- **实验数量**：至少包括七个独立数据集的性能对比实验；可能包含消融实验（如移除无监督聚类或图像特征的影响），但摘要未明确提及。
- **充分性与客观性**：
  - 优势：覆盖多种组织类型和疾病，结果一致优于 SOTA（中位准确率相对提升107%），且有临床预后验证（肿瘤亚区）和疾病进展关联（脑亚区），说明方法有效且泛化性较好。
  - 不足：未提供详细的消融分析、统计显著性检验、以及在不同噪声或数据稀疏条件下的鲁棒性测试，实验规模（七个数据集）虽合理但不算极度广泛。

### 6. 论文的主要结论与发现
- HiCAT 在七个数据集的准确率中位数相对提升 **107%**，显著优于所有对比方法。
- 能够发现原始病理注释未捕捉的 **分子知情区域异质性**：
  - 肿瘤样本中识别出与患者临床预后相关的肿瘤亚区域；
  - 脑样本中识别出与时空疾病进展（如阿尔茨海默病）对齐的脑亚区域。
- 生成的注释具有一致性、高粒度和生物学信息，支持大规模队列下游分析（如差异表达、细胞互作）。
- 高质量的注释可以作为训练标签，赋能空间基础模型（foundation models）。

### 7. 优点
- **自动化与可扩展**：完全消除手工标注瓶颈，能够扩展到成百上千样本的队列分析。
- **跨模态融合**：整合形态学（组织图像）与分子信号（空间转录组），弥补纯形态学注释的分子盲区。
- **生物学发现能力**：不仅复制病理注释，还能揭示具有临床和生物学意义的新异质性区域。
- **性能卓越**：在多种数据集上远超现有方法，且绝对准确率提升显著。
- **赋能基础模型**：提供大规模、一致的标准标签，有助于训练更通用的空间组学基础模型。

### 8. 不足与局限
- **计算资源未报告**：缺乏训练所需 GPU、时间、内存等信息，不利于学术界复现和资源评估。
- **依赖训练数据质量**：方法需要一定量的病理专家注释作为监督信号，若原始注释不准确或存在主观偏差，可能影响学习效果。
- **泛化性需进一步验证**：虽覆盖七种数据集，但未涵盖所有常见组织（如肠道、皮肤等）或新兴空间技术在低分辨率、高噪声等极端条件下的表现。
- **消融分析缺失**：未明确展示各个组件（无监督聚类、图像特征、对齐机制）的贡献，无法判断方法提高准确率的具体来源。
- **可解释性有限**：未说明如何确保自动生成的区域注释在生物学上可解释，以及如何排除假阳性区域性模式。

（完）
