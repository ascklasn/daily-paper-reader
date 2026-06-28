---
title: "SPEAK: Spatial Prompting with Expert Aligned Knowledge for Tissue Domain Identification in Spatial Transcriptomics"
title_zh: "SPEAK: 基于专家对齐知识的空间提示用于空间转录组学中的组织域识别"
authors: "Wei, H., Luo, X., Yu, H., Liang, J., Yang, L., Sauler, M., Kaminski, N., Popa, A., Yan, X."
date: 2026-06-26
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.22.733750v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 利用大语言模型提示进行空间转录组领域识别
tldr: 空间转录组学数据需识别空间域以分析组织微环境，但现有方法依赖先验知识且适应性差。SPEAK方法利用大语言模型和专家知识，构建空间上下文提示实现零样本推理，并通过两阶段提示进行专家引导微调和原型更新。在STARmap、Visium等数据集上，SPEAK在域预测准确度、鲁棒性、生物可解释性及对有限先验知识的容错性上优于现有方法。其高效微调能力可便捷泛化至其他组织切片。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有空间域识别方法对先验知识依赖强且泛化性弱，需结合LLM与专家知识实现准确鲁棒的识别。
method: 构建空间上下文提示，包含细胞类型和标记基因，通过零样本推理、专家引导微调及原型更新两阶段提示识别空间域。
result: 在STARmap、Visium、MERFISH、Xenium数据集上，SPEAK在域预测精度、鲁棒性、可解释性和泛化性超越现有方法。
conclusion: SPEAK高效融合LLM与专家知识，为空间转录组微环境分析提供精确且可迁移的域识别方案。
---

## 摘要
空间分辨转录组学（SRT）数据需要空间域识别，以支持组织微环境特异性的下游分析。本文提出SPEAK（基于专家对齐知识的空间提示），一种基于大语言模型（LLM）的方法，通过利用LLM和人类专家的先验知识从SRT数据中识别空间域。SPEAK根据每个细胞/点的细胞类型及其邻近细胞的标记基因构建空间上下文提示，通过两阶段提示实现零样本推理、专家指导的微调和原型更新。在STARmap、Visium、MERFISH和Xenium数据集上的应用表明，SPEAK在域预测准确性、对有限先验知识的鲁棒性、生物学可解释性以及高效专家指导微调且对其他组织切片具有泛化能力方面优于现有空间域识别方法。

## Abstract
Spatially resolved transcriptomic (SRT) data requires spatial domain identification to enable tissue microenvironment-specific downstream analyses. Here we present SPEAK (Spatial Prompting with Expert-Aligned Knowledge), a large language model (LLM) -based method to identify spatial domains from SRT data by taking advantage of the prior knowledge from both LLM and human experts. SPEAK constructs a spatial context prompt for each cell/spot based on cell types and marker genes of its neighboring cells, enabling zero-shot inference, expert-guided fine-tuning, and prototype updating through two-stage prompting. Applications to STARmap, Visium, MERFISH and Xenium datasets showed advantages of SPEAK over existing spatial domain identification methods in domain prediction accuracy, robustness to limited prior knowledge, biological interpretability, and capacity for efficient expert-guided fine-tuning with generalizability to other tissue sections.

---

## 论文详细总结（自动生成）

# SPEAK 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：空间转录组学（SRT）数据需要识别组织内部的“空间域”（spatial domain），即具有相似细胞组成和分子程序的功能单元，以支持组织微环境特异性的下游分析。
- **现有方法局限**：
  - 大多数现有方法（如图神经网络+聚类）无法融入先验生物学知识或人类专家指导。
  - 针对每个数据集从头训练，模型难以迁移到新样本。
  - 聚类结果产生无生物意义的抽象标签（如cluster 0, cluster 1），解释和跨样本比较困难。
  - 对预定义聚类数量（K）敏感，而K常未知。
- **整体含义**：迫切需要一种能集成大语言模型（LLM）已有知识与人类专家领域知识、无需重新训练即可泛化、输出可解释域名称的方法。

## 2. 论文提出的方法论

- **核心思想**：利用预训练LLM的语义理解能力，将每个细胞/点的空间邻域信息（细胞类型组成和标记基因表达）构建为“空间上下文提示”（spatial context prompt），通过提示工程实现零样本域识别；进一步通过专家标注少量细胞进行LoRA微调，并使用两阶段提示策略更新域原型以提升跨样本泛化性。
- **关键技术细节**：
  - **空间上下文提示构建**：
    - 为每个细胞定义邻域（半径为δ的圆，不同数据集δ不同）。
    - 从邻域中提取两个有序列表：
      1. 邻域细胞类型列表（按细胞类型频率降序）
      2. 邻域标记基因列表（按平均表达水平降序）
    - 任务描述中提供物种、组织类型、潜在域名称列表及响应格式。
  - **三种模式**：
    - **SPEAK-Z（零样本）**：直接输入预训练LLM（GPT-4o、Gemini等），无需任何标注。
    - **SPEAK-F（微调）**：人类专家提供少量细胞（如30%）的正确域标签，结合域原型（该域所有细胞平均邻域特征）构建增强提示，使用LoRA（Low-Rank Adaptation）对LLM进行微调（3个epoch，batch size=2，默认学习率）。
    - **SPEAK-Fs（两阶段提示）**：应用微调模型时，先进行第一轮预测，筛选高置信度细胞（邻域中>50%预测一致），用其更新域原型；第二阶段用更新后的原型重新预测剩余细胞。
  - **后处理**：类似SpaGCN的邻域平滑（若邻域多数标签不同则重新标记）。
- **公式/算法流程**（文字说明）：输入SRT数据（坐标、细胞类型、标记基因表达） → 每细胞构建邻域 → 生成两个有序列表 → 组装提示（任务描述+列表） → 零样本或微调+两阶段预测 → 后处理平滑 → 输出带生物学意义的域名称。

## 3. 实验设计

- **数据集**：
  - **STARmap**（小鼠视觉皮层，单细胞分辨率，4个域，3张切片，共3268细胞）
  - **Visium**（人背外侧前额叶皮层，spot级，7个域，3个受试者各4张切片，共47681 spots）
  - **MERFISH**（小鼠下丘脑视前区，单细胞，8个域，1受试者5张切片，共28317细胞）
  - **Xenium**（人COPD肺，单细胞，无标签，作为验证案例，9051细胞）
- **基准（benchmark）**：前三个数据集有手工标注的真实域标签作为金标准。
- **对比方法**：16种已有方法，包括基于图的（CCST, GraphST, STAGATE, SpaGCN, SEDR）、集成方法（Seurat, IRIS, BASS, conST, SpaceFlow, SCAN-IT, stLearn, BayesSpace）、非空间聚类（Leiden, Louvain）等。有些需要组织学图像（如SpaGCN(HE)）仅在部分数据集上评估。
- **评估指标**：
  - 准确性：NMI（归一化互信息）、HOM（同质性）、COM（完整性）
  - 空间连续性：CHAOS（越低越好）、PAS（越低越好）、ASW（越高越好）
- **消融实验**：
  - 不同LLM对比（GPT-4o mini, GPT-4o, Gemini 1.5 Pro, Llama-3.1-8B/70B, Qwen3-30B）
  - 域列表不完整、冗余、错指时的鲁棒性测试
  - 微调数据比例影响（5%~70%）
  - 基因表达缺失（dropout）鲁棒性
  - 跨受试者泛化测试（同一受试者内切片间 vs 不同受试者间）
  - 人类在环（human-in-the-loop）：专家选择少量正确预测细胞进行微调

## 4. 资源与算力

- 文中明确提到：
  - 使用**2块NVIDIA H200 GPU**和**2个CPU核心**部署开源LLM（通过vLLM）。
  - 速度：Qwen3-30B-A3B-Instruct-2507 约3秒/1024细胞；Llama-3.1-70B-Instruct 约18秒/1024细胞。
  - 商业API（GPT-4o, Gemini）时间取决于网络和负载，STARmap（1088细胞）约5-10分钟。
  - 微调使用OpenAI的Fine-tuning API（LoRA），未给出具体训练时长（推测较短，因为仅3轮小批量）。
- 未提及：预训练LLM本身的训练资源（非本文贡献）。

## 5. 实验数量与充分性

- **实验数量丰富**：
  - 在3个基准数据集上进行了充分比较（每种方法3次运行取均值）。
  - 覆盖4种不同平台（STARmap, Visium, MERFISH, Xenium），不同物种（小鼠、人），不同分辨率（单细胞、spot）。
  - 对比了16种基线方法，包括非空间和空间方法。
  - 进行了多个消融实验：不同LLM规模、域列表偏差、微调比例、噪声鲁棒性、跨受试者泛化、人机协作。
- **充分性评价**：
  - **客观公平**：所有方法使用相同输入（细胞类型+位置），并在相同金标准下评估参数（对基线方法使用已有最优参数或直接引用基准结果）。
  - **全面**：从零样本到微调再到两阶段，层层递进证明了每个组件的贡献。
  - **不足**：仅对一个疾病案例（COPD）展示，缺少更多病理/复杂组织验证；未与其他LLM-based方法对比（可能无同类方法）。

## 6. 论文的主要结论与发现

- SPEAK-Z在STARmap上显著优于所有非LLM方法，尤其Gemini 1.5 Pro取得最高准确性和空间连续性。
- LLM规模越大，零样本性能越好（GPT-4o > GPT-4o mini；Llama-70B > 8B）。
- SPEAK对域列表错误（遗漏、冗余）具有鲁棒性，远超传统方法对聚类数K的敏感性。
- 微调（SPEAK-F）在Visium和MERFISH上大幅提升性能，即使仅用30%标注细胞。
- 两阶段提示（SPEAK-Fs）有效减小跨受试者差异，无需额外标注即可适应新切片。
- 少量标注（5%~30%）即可达到高准确度，且性能随标注增加持续提升。
- 在COPD案例中，SPEAK准确区分气道平滑肌和血管平滑肌，并识别疾病相关的分子差异，展现病理洞察力。
- SPEAK输出可读的推理步骤，提高可解释性。

## 7. 优点

- **精准与鲁棒**：零样本即达顶尖性能，对先验知识不完整容忍度高。
- **可解释性**：输出带生物学意义的域名称和推理过程，避免后处理标注。
- **高效微调**：少量标注即可泛化至新切片，人机协作闭环。
- **计算效率**：并行处理避免图方法的内存瓶颈，支持大规模数据。
- **先进架构**：性能随LLM发展自然提升。
- **平台通用性**：适用于多种SRT技术（单细胞/spot，不同基因面板）。

## 8. 不足与局限

- **对LLM先验知识的依赖**：对于研究不足的组织或疾病，零样本性能可能受限（需要微调或更多人工指导）。
- **需要潜在域列表**：用户需事先提供可能存在的域名称，虽然对冗余鲁棒，但仍需初始知识。
- **邻域半径固定**：不同组织或域可能适用不同最优半径，当前未自适应。
- **微调成本**：大型LLM（如Llama-70B）微调计算资源要求高，且文中仅对GPT-4o-mini进行了微调（其他模型因API限制未参与微调比较）。
- **局限性验证**：疾病案例仅一个（COPD），缺少多病人、多组织、跨疾病泛化验证。

（完）
