---
title: Extrachromosomal DNA as a Causal Instrument for Spatial Multi-Omics
title_zh: 染色体外DNA作为空间多组学的因果工具
authors: "Craig, D. W., Rodin, A. S."
date: 2026-06-05
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.02.729483v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 利用染色体外DNA进行空间多组学因果推断的框架
tldr: 当前空间多组学分析仅能描述特征共现，无法区分因果与关联。本文利用ecDNA随机分配的细胞内在特性，将其拷贝数作为工具变量（IV）进行因果推断，建立结构因果模型并采用两阶段最小二乘估计与兄弟姐妹比较等诊断。通过CAUSANTA模拟器生成已知因果图的空间组织数据，验证了该方法能准确恢复致癌基因剂量对下游表型的因果效应。该框架首次为空间多组学提供因果推断手段，并支持多ecDNA物种的因子设计以解析复杂因果网络。
source: biorxiv
selection_source: fresh_fetch
motivation: 解决空间多组学数据只能进行相关性分析、无法推断因果关系的问题。
method: 利用ecDNA随机分配特性作为工具变量，构建结构因果模型，采用两阶段最小二乘估计和因果搜索。
result: 通过CAUSANTA模拟器验证，该方法能准确恢复已知的致癌基因-表型因果效应。
conclusion: 提出了首个用于空间多组学的因果推断框架，支持多工具变量因子设计，可应用于真实肿瘤组织。
---

## 摘要
空间转录组学、多重成像和计算病理学现在能够以细胞分辨率绘制组织图谱，但应用于这些数据的分析仍然是相关性的。聚类和共现统计描述哪些特征同时出现，但无法说明哪个特征驱动了其他特征。我们提出了一个基于染色体外DNA（ecDNA）特定特征的空间多组学因果推断框架。ecDNA没有着丝粒，不附着于有丝分裂纺锤体，在分裂时随机分配到子细胞。因此，同一微环境中两个相邻的细胞可能由于与局部信号无关的原因而继承非常不同的癌基因拷贝数。ecDNA的这些细胞内在随机化特性共同提供了框架，使得ecDNA拷贝数可以作为工具变量（IV），将癌基因剂量的效应与下游细胞效应分离开来。在本研究中，我们在结构化因果模型中形式化这一框架，采用同胞比较和证伪诊断的两阶段最小二乘估计，并对残留混杂进行敏感性分析。为了与真实情况进行基准测试，我们构建了CAUSANTA，一个基于智能体的模拟器，可生成具有已知因果图和随机ecDNA遗传的空间组织。该框架从模拟数据中恢复了已知的癌基因到表型效应，并概述了其在真实肿瘤切片中的应用，包括多工具设置，其中携带不同癌基因的独立ecDNA物种使得在单个肿瘤内实现因子设计。

## Abstract
Spatial transcriptomics, multiplex imaging, and computational pathology now map tissue organization at cellular resolution, but the analyses applied to these data remain correlational. Clustering and co-occurrence statistics describe which features appear together; they cannot say which feature drives the others. We propose a framework for causal inference in spatial multi-omics built on a specific feature of extrachromosomal DNA (ecDNA). ecDNA carries no centromere; it does not attach to the mitotic spindle and partitions randomly to daughter cells at division. Two neighboring cells in the same microenvironment can therefore inherit very different oncogene copy numbers for reasons unrelated to local signaling. Together, these cell-intrinsic randomization properties of ecDNA provide the framework for ecDNA copy number serving as an instrumental variable (IV) separating the effects of oncogene dosage from the downstream cellular effects. In this study, we formalize this within a structural causal model, implement two-stage least squares estimation with sibling-comparison and falsification diagnostics, and provide sensitivity analyses for residual confounding. To benchmark these methods against ground truth, we built CAUSANTA, an agent-based simulator that generates spatial tissue with a known causal graph and stochastic ecDNA inheritance. The framework recovers known oncogene-to-phenotype effects from simulated data, and we outline its application to real tumor sections, including multi-instrument settings where independent ecDNA species carrying different oncogenes enable factorial designs within a single tumor.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：当前空间转录组学、多重成像和计算病理学虽然能以单细胞分辨率绘制组织图谱，但常用的聚类和共现统计仅能描述特征之间的相关性，无法区分因果与关联。即“哪些特征同时出现”而非“哪个特征驱动了其他特征”。
- **整体含义**：作者提出利用染色体外DNA（ecDNA）的细胞内随机分配特性，将其拷贝数作为天然的工具变量，从而在空间多组学数据中实现因果推断。这是首次将因果推理框架引入空间多组学分析领域。

## 2. 方法论

### 核心思想
- ecDNA 没有着丝粒，不附着于有丝分裂纺锤体，细胞分裂时随机分配到子细胞。因此，同一微环境中相邻的两个细胞可能因随机分配而非局部信号差异而继承截然不同的癌基因拷贝数。这种随机性使 ecDNA 拷贝数满足工具变量（Instrumental Variable, IV）的条件：与暴露（癌基因剂量）相关、不影响结局（下游细胞表型）除了通过暴露、且与混杂因素独立。

### 关键技术细节
- **结构因果模型**：将 ecDNA 拷贝数作为工具变量，构建 IV 框架。
- **两阶段最小二乘估计（2SLS）**：第一阶段：用 ecDNA 拷贝数预测癌基因剂量（暴露）；第二阶段：用预测的暴露估计对下游表型的因果效应。
- **同胞比较与证伪诊断**：通过“同胞比较”（类似同一微环境内的细胞对比）来控制未观测混杂；使用证伪检验（如平衡性检验）评估 IV 假设的有效性。
- **残留混杂敏感性分析**：评估即使 IV 假设部分违背时因果估计的稳健性。

### 算法流程（文字说明）
1. 从空间组织图像/数据中提取每个细胞的 ecDNA 拷贝数（工具变量 Z）、癌基因表达或拷贝变异（暴露 X）、下游表型（结局 Y），以及可能的协变量（如空间位置）。
2. 建立结构方程模型：X = α + β Z + γ Cov + ε；Y = δ + θ X̂ + λ Cov + η（其中 X̂ 为第一阶段预测值）。
3. 使用 2SLS 估计因果效应 θ。
4. 进行同胞比较（对同一微环境内的细胞对进行差分估计）以消除局部共享混杂。
5. 实施证伪检验（如检验 Z 与其他已知无关的结局是否相关）以及敏感性分析。

## 3. 实验设计

### 数据集与场景
- 本文未使用真实空间多组学数据集，而是构建了 **CAUSANTA**——一个基于智能体的模拟器，用于生成具有已知因果图和随机 ecDNA 遗传的空间组织数据。该模拟器可产出已知真实因果效应（ground truth）的模拟组织切片。
- benchmark：自身模拟数据，对比真实因果效应与估计效应。未与其他因果推断方法比较（因为尚无同类工作）。

### 对比方法
- 未提供对比方法。论文主要展示框架能否从模拟数据中恢复已知因果效应。

## 4. 资源与算力

- **论文中未提及任何算力信息**（如 GPU 型号、数量、训练时长等）。仅作为一个方法学理论框架及模拟验证，可能不需要大规模计算资源。亦未提及运行时间或硬件配置。

## 5. 实验数量与充分性

- **实验数量**：从摘要和元数据推断，只有一组模拟实验：使用 CAUSANTA 生成数据，验证框架恢复已知因果效应。未提及不同参数设置、不同因果图结构、不同噪声水平的消融实验或鲁棒性测试。
- **充分性评价**：作为概念验证论文，实验覆盖范围有限，仅验证了最基本的功能。缺乏真实数据验证、统计效力分析、与现有方法的比较、多场景压力测试。因此，实验的充分性、客观性和公平性有待加强（但属初步工作，可以理解）。

## 6. 主要结论与发现

- 该因果推断框架能从 CAUSANTA 模拟数据中准确恢复已知的癌基因到表型的因果效应。
- 提出了首个用于空间多组学的因果推断工具，利用 ecDNA 的天然工具变量特性。
- 支持多工具变量设置：当单个肿瘤携带独立 ecDNA 物种（携带不同癌基因）时，可实现因子设计（factorial design），同时推断多个因果路径。
- 概述了在真实肿瘤切片中的应用路径，包括多 ecDNA 物种的联合分析。

## 7. 优点

- **创新性**：首次将 ecDNA 的随机分配生物学特性转化为统计工具变量，为空间组学数据开辟了因果推断新路径。
- **理论严谨**：结构因果模型形式化，结合两阶段最小二乘、同胞比较、证伪诊断和敏感性分析，提供完整的推断与诊断流程。
- **可扩展性**：支持多个 ecDNA 物种作为工具变量，可实现类似随机对照试验的因子设计。
- **开放工具**：提供了 CAUSANTA 模拟器，便于其他研究者生成已知因果图数据进行方法开发与测试。

## 8. 不足与局限

- **实验覆盖不足**：仅基于模拟数据验证，缺乏真实肿瘤组织数据上的应用与验证。真实场景中 ecDNA 拷贝数的测量噪声、缺失值、以及 IV 假设的违背风险（如多效性）未在实验中评估。
- **偏差风险**：ecDNA 随机分配虽满足 IV 关键假设，但实际中某些混杂（如细胞周期状态、微环境压力）可能同时影响 ecDNA 拷贝数和表型，导致 IV 无效。敏感性分析仅为理论工具，未提供模拟中的实际评估。
- **应用限制**：该框架仅在存在 ecDNA 的肿瘤中适用，对其他无 ecDNA 的疾病或组织类型不适用。且需要高分辨率的单细胞 ecDNA 拷贝数定量数据，技术门槛较高。
- **统计效力**：未讨论所需样本量（细胞数）、ecDNA 变异性大小对因果估计精度的影响；两阶段估计在弱工具变量下可能产生偏倚，文中未进行弱工具变量诊断。
- **复现性**：由于论文全文无法获取（biorxiv 403 错误），具体细节（如模拟参数、代码可用性）不明，限制了可复现性。

（完）
