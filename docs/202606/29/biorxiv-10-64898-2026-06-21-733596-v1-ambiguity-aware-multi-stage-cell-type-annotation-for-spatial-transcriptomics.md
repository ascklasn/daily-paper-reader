---
title: Ambiguity-Aware Multi-Stage Cell-Type Annotation for Spatial Transcriptomics
title_zh: 空间转录组学的模糊感知多阶段细胞类型注释
authors: "Mahmud, M. I., Kochat, V., Anzum, H., Satpati, S., Dwarampudi, J. M. R., Rai, K., Banerjee, T."
date: 2026-06-25
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.21.733596v1.full.pdf"
tags: ["query:spatialprot"]
score: 8.0
evidence: 空间转录组细胞类型注释方法
tldr: "空间转录组学中细胞类型标注因表达异质性和过渡状态而面临模糊性挑战。现有方法强制单标签分配导致过度自信。本文提出模糊感知多阶段框架，结合混合空间特征聚类与约束语言模型推理，通过标记覆盖率、候选分离和熵分配置信度，低置信度簇局部重建，未解析簇保留为混合。在胆管癌Xenium数据上，簇级模糊性从16.1%降至2.27%，细胞级从18.4%降至0.86%，置信度校准改善。空间消融验证拓扑整合优于仅特征基线，轻量语言模型保证可扩展与生物学一致的注释。该方法显式处理模糊性，为异质性肿瘤可靠空间标注提供关键方案。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有细胞类型标注方法强制每个簇一个标签，忽视生物学模糊性，导致过度自信和错误注释。
method: 提出多阶段框架：混合空间特征聚类结合约束语言模型推理，基于标记覆盖率、候选分离和熵赋置信度，低置信度区局部重聚类，未解析簇保留为混合。
result: "在胆管癌Xenium数据上，簇级模糊性从16.1%降至2.27%，细胞级从18.4%降至0.86%，置信度校准显著改善。"
conclusion: 显式模糊处理结合拓扑信息和轻量语言模型，实现了可靠、可扩展且生物学一致的空间细胞类型标注。
---

## 摘要
空间转录组学能够表征完整组织中的细胞组织，但由于异质性表达谱、混合细胞群和过渡状态的存在，稳健的细胞类型注释仍然具有挑战性。现有方法通常对每个聚类强制分配单一标签，掩盖了具有生物学意义的模糊性，并产生过度自信的分配。

我们提出了一种用于空间细胞类型注释的模糊感知多阶段框架。该方法将混合空间特征聚类与基于精选标签集的约束语言模型推理相结合，并基于标记覆盖度、候选分离度和熵分配置信度分数。低置信度聚类通过模糊区域的局部重聚类进行选择性细化，而未解决的聚类则保留为混合状态，而非强行标注。

应用于来自胆管癌的10x Genomics Xenium空间转录组数据，所提出的细化方法将聚类级别的模糊性从16.1%降低到2.27%，细胞级别的模糊性从18.4%降低到0.86%，同时改善了置信度校准。空间消融实验证实，与仅基于特征的基线相比，拓扑整合解决了结构模糊性，而通过轻量级语言模型进行的约束推理确保了可扩展且生物学一致的注释。这些结果强调了在异质性肿瘤中进行可靠空间注释时显式处理模糊性的重要性。

## Abstract
Spatial transcriptomics enables characterization of cellular organization in intact tissue, but robust cell-type annotation remains challenging due to heterogeneous expression profiles, mixed populations, and transitional states. Existing methods often enforce a single label per cluster, obscuring biologically meaningful ambiguity and producing overconfident assignments.

We propose an ambiguity-aware, multi-stage framework for spatial cell-type annotation. The method combines hybrid spatial-feature clustering with constrained language-model inference over curated label sets, and assigns confidence scores based on marker coverage, candidate separation, and entropy. Low-confidence clusters are selectively refined via local reclustering of ambiguous regions, while unresolved clusters are preserved as mixed rather than forcibly labeled.

Applied to 10x Genomics Xenium spatial transcriptomics data from cholangiocarcinoma, the proposed refinement reduces cluster-level ambiguity from 16.1% to 2.27% and cell-level ambiguity from 18.4% to 0.86%, while improving confidence calibration. Spatial ablation confirms that topological integration resolves structural ambiguity over feature-only baselines, while constrained inference via a lightweight language model ensures scalable and biologically coherent annotations. These results highlight the importance of explicit ambiguity handling for reliable spatial annotation in heterogeneous tumors.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **问题**：空间转录组学技术虽能表征完整组织中的细胞组织，但细胞类型注释面临巨大挑战。主要根源包括：  
  - 异质性表达谱（如肿瘤内异质性）；  
  - 混合细胞群（多个细胞类型在同一空间位置共存）；  
  - 过渡状态（细胞分化或状态转变导致的连续性表达变化）。  
- **现有方法缺陷**：多数现成方法强制每个聚类分配唯一标签，忽略了生物学上的模糊性，导致过度自信且可能错误的注释，阻碍了对组织真实状态的准确理解。  
- **研究意义**：提出一种显式处理模糊性的注释框架，旨在在不掩盖生物学复杂性的前提下，提升空间转录组细胞类型分配的可靠性、校准性和生物学一致性。

### 2. 论文提出的方法论：核心思想、关键技术细节、算法流程

- **核心思想**：构建多阶段、模糊感知的注释流水线，避免强制单标签分配；通过置信度评估与选择性细化，保留合理的混合注释。  
- **关键技术细节**：  
  1. **混合空间特征聚类**：同时利用基因表达特征与空间邻域拓扑信息进行聚类，生成初始簇。  
  2. **约束语言模型推理**：基于精选的已知标记基因集（curated label sets），使用轻量级语言模型（轻量LLM）进行推理，将候选标注与簇匹配；推理过程受预定义标记集约束，保证生物学一致性。  
  3. **置信度分数**：每个候选簇赋予三个指标：  
     - **标记覆盖度（Marker Coverage）**：簇内表达已知标记基因的比例；  
     - **候选分离度（Candidate Separation）**：不同候选标签在特征空间的分离程度；  
     - **熵（Entropy）**：聚类后细胞分配到不同候选标签的概率分布的混乱程度。  
  4. **选择性细化**：低置信度簇不直接强制标注，而是通过**局部重聚类**（仅针对模糊区域）进行细化；  
  5. **未解析簇保留**：若重聚类后仍无法明确，则保留为“混合（mixed）”状态，而非强行赋予单一标签。  
- **算法流程（文字描述）**：  
  1. 输入：空间转录组数据（基因表达矩阵 + 空间坐标）；  
  2. 第一步：混合空间特征聚类 → 获得初始簇；  
  3. 第二步：对每个簇，使用约束语言模型在精选标记集上推断候选标签并计算置信度分数；  
  4. 第三步：低置信度簇触发局部重聚类（仅涉及该簇及邻近模糊区域），重新执行步骤2；  
  5. 第四步：仍无法解析的簇标记为“混合”类型，其余簇赋予最终细胞类型标签及对应置信度。

### 3. 实验设计：数据集、基准、对比方法

- **使用数据集**：10x Genomics Xenium 平台获取的**胆管癌（cholangiocarcinoma）** 空间转录组数据（具体样本量、切片数量文中未细述）。  
- **基准与对比**：未提及与其他已有方法（如Seurat、CellTypist、SPOTlight等）的直接定量对比；主要进行了**空间消融实验**，对比：  
  - 完整框架（含空间拓扑特征） vs. **仅特征基线（仅基因表达特征，不含空间信息）**。  
- **默认评价方法**：  
  - 簇级模糊性比例（cluster-level ambiguity）  
  - 细胞级模糊性比例（cell-level ambiguity）  
  - 置信度校准（confidence calibration）

### 4. 资源与算力

- **文中未明确说明**使用的GPU型号、数量、训练时长等算力信息。论文属于方法学框架，可能主要依赖推理轻量级语言模型，算力需求相对较低，但具体硬件细节缺失。

### 5. 实验数量与充分性

- **实验数量**：  
  - 仅在**一个胆管癌Xenium数据集**上进行了测试；  
  - 包含**空间消融实验**（完整方法 vs. 仅特征基线）；  
  - 无跨数据集（如其他癌症、正常组织）验证。  
- **充分性评价**：  
  - **不充分**：缺乏与主流细胞类型注释方法的定量基准比较（如F1分数、正确率等）和统计显著性检验；单一数据集的验证可能限制了泛化性的评估；消融实验仅支持了空间信息的作用，未对比不同聚类算法或语言模型的影响。  
  - **客观性与公平性**：作者自行提出消融实验，但未与外部独立方法比较，难以判断相对优劣。不过，结果中簇级模糊性从16.1%降至2.27%、细胞级从18.4%降至0.86%的改善是明确的内部提升指标。

### 6. 论文的主要结论与发现

- 提出的多阶段模糊感知框架能够有效识别并解决空间转录组细胞类型注释中的模糊性，显著降低簇级和细胞级模糊性比例，同时改善置信度校准。  
- 空间拓扑信息的整合比仅基于特征的聚类更能解决结构模糊性。  
- 通过轻量级语言模型进行约束推理，实现了可扩展且生物学一致的注释，避免了过度自信。  
- 显式处理模糊性（而非强制单标签）是异质性肿瘤空间注释中可靠且必要的策略。

### 7. 优点

- **创新方法论**：首次将“模糊感知”与“多阶段细化”结合到空间注释流程中，显式保留混合状态，避免强制分配。  
- **灵活可扩展**：使用轻量级语言模型进行约束推理，可适应不同标记集，且计算成本较低。  
- **置信度指标设计合理**：结合标记覆盖、候选分离和熵三个互补指标，综合评估分派可靠性。  
- **空间消融实验有力**：验证了空间拓扑信息对解决模糊性的关键作用，与仅特征基线形成对照。  
- **结果清晰**：以具体数值（16.1%→2.27%等）展示提升，直观且令人信服。

### 8. 不足与局限

- **实验验证不足**：仅使用单一个数据集（胆管癌Xenium）进行评估，缺乏在其他组织类型、不同平台（如Visium、Slide-seq）上的泛化性测试。  
- **缺乏与现有方法定量对比**：未在公共基准上比较（例如与CellTypist、SPOTlight、Seurat等方法的准确率、模糊度处理能力）。  
- **未讨论语言模型选择的影响**：未比较不同规模或结构的语言模型对推理性能的影响，也未说明具体使用的模型名称。  
- **未分析计算效率**：未提供运行时间、内存消耗等实际部署必要指标。  
- **缺少对混合状态的验证**：保留为“混合”的簇是否真实对应生物学上的混合区域，缺乏原位验证或外部专家验证。  
- **消融实验仅对比空间特征有无**：未进一步对比不同聚类算法、不同置信度阈值的影响等更细致的超参数分析。

（完）
