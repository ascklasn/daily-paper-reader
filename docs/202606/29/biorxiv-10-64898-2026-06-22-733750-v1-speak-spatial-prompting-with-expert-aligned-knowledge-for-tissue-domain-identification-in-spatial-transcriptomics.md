---
title: "SPEAK: Spatial Prompting with Expert Aligned Knowledge for Tissue Domain Identification in Spatial Transcriptomics"
title_zh: SPEAK：基于专家对齐知识的空间提示用于空间转录组学中的组织域识别
authors: "Wei, H., Luo, X., Yu, H., Liang, J., Yang, L., Sauler, M., Kaminski, N., Popa, A., Yan, X."
date: 2026-06-26
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.22.733750v1.full.pdf"
tags: ["query:spatialprot"]
score: 8.0
evidence: 空间转录组组织域识别的大语言模型提示方法
tldr: 空间转录组数据的组织域识别是下游分析的关键。SPEAK通过构建空间上下文提示，结合大语言模型和人类专家知识，实现零样本推理、专家引导微调和原型更新。在STARmap、Visium等数据集上，SPEAK在预测准确率、鲁棒性和生物学可解释性方面均优于现有方法。其贡献在于提供了一种高效、可泛化的空间域识别框架，并支持专家知识的灵活融入。
source: biorxiv
selection_source: fresh_fetch
motivation: 利用LLM和专家知识克服现有空间域识别方法对先验知识依赖强、泛化性差的局限。
method: 为每个细胞/点构建基于邻域细胞类型和标记基因的空间上下文提示，通过两阶段提示实现零样本推理、专家微调和原型更新。
result: 在多种空间转录组数据上，SPEAK在域预测准确率、鲁棒性和生物学可解释性上均优于现有方法。
conclusion: SPEAK是一种高效且可泛化的空间域识别方法，能有效集成专家知识并支持高效微调。
---

## 摘要
空间分辨转录组学（SRT）数据需要通过空间域识别来实现组织微环境特异性的下游分析。本文提出SPEAK（基于专家对齐知识的空间提示）方法，这是一种基于大语言模型（LLM）的方法，利用LLM和人类专家的先验知识从SRT数据中识别空间域。SPEAK根据每个细胞/点的细胞类型及其邻近细胞的标记基因构建空间上下文提示，通过两阶段提示实现零样本推理、专家引导微调和原型更新。应用于STARmap、Visium、MERFISH和Xenium数据集的结果表明，SPEAK在域预测准确性、对有限先验知识的鲁棒性、生物学可解释性以及高效专家引导微调能力（可推广至其他组织切片）方面优于现有空间域识别方法。

## Abstract
Spatially resolved transcriptomic (SRT) data requires spatial domain identification to enable tissue microenvironment-specific downstream analyses. Here we present SPEAK (Spatial Prompting with Expert-Aligned Knowledge), a large language model (LLM)-based method to identify spatial domains from SRT data by taking advantage of the prior knowledge from both LLM and human experts. SPEAK constructs a spatial context prompt for each cell/spot based on cell types and marker genes of its neighboring cells, enabling zero-shot inference, expert-guided fine-tuning, and prototype updating through two-stage prompting. Applications to STARmap, Visium, MERFISH and Xenium datasets showed advantages of SPEAK over existing spatial domain identification methods in domain prediction accuracy, robustness to limited prior knowledge, biological interpretability, and capacity for efficient expert-guided fine-tuning with generalizability to other tissue sections.

---

## 论文详细总结（自动生成）

# SPEAK：基于专家对齐知识的空间提示用于空间转录组学中的组织域识别 —— 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **问题**：空间分辨转录组学（SRT）数据需要识别转录上同质的“空间域”（如组织功能单元）以支持微环境特异性下游分析。现有方法（如基于图神经网络的无监督聚类）存在四大局限：
  - 无法融入先验生物学知识或病理学家指导；
  - 模型需对每个数据集从头训练，难以跨样本迁移；
  - 无监督聚类输出无生物学意义的抽象簇标签，难以解释和跨样本比较；
  - 对预设簇总数敏感，而该数往往未知。
- **目标**：开发一种利用大语言模型（LLM）和人类专家知识的方法，实现高效、可泛化、可解释的空间域识别，并允许用户通过少量标注灵活修正。

## 2. 论文提出的方法论：核心思想、关键技术细节、算法流程

- **核心思想**：为每个细胞/点构建“空间上下文提示”（Spatial Context Prompt），该提示包含任务描述（物种、组织、潜在域列表）和空间概况（邻域细胞类型频率排序 + 邻域标记基因平均表达排序），然后输入预训练LLM进行推理。通过三种模式实现：
  1. **零样本（SPEAK‑Z）**：直接使用预训练LLM预测。
  2. **专家微调（SPEAK‑F）**：由人类专家标注一小部分细胞域标签，结合域原型（该域所有细胞空间概况的平均）生成增强提示，利用LoRA低秩适配对LLM进行微调。
  3. **两阶段提示（SPEAK‑Fs）**：微调后模型先对未标注细胞做第一轮预测，筛选高置信度细胞（超过50%邻居同域）更新域原型，再对所有细胞进行第二轮预测，利用样本特异原型提高跨样本泛化。
- **后处理**：强制空间平滑——若某细胞被多数邻居预测为另一标签，则改为多数标签。
- **关键技术细节**：
  - 邻域半径 δ（STARmap 72 μm, MERFISH 100 μm, Visium 344 μm, Xenium 50 μm）以保证覆盖最小功能单元。
  - 单细胞数据用CCA整合后Leiden聚类挑选标记基因；spot数据用文献既成标记基因。
  - 微调使用OpenAI API（GPT‑4o mini），训练3 epochs，batch size 2，默认学习率。

## 3. 实验设计：数据集、基准、对比方法

- **数据集**（4个）：
  - **STARmap**（小鼠视觉皮层，单细胞，3切片，4个域，3,268细胞）——有ground truth。
  - **Visium**（人背外侧前额叶皮层，spot级，3受试者×4切片，7个域，47,681 spots）——有ground truth，使用SDePER反卷积得到细胞类型组成。
  - **MERFISH**（小鼠下丘脑视前区，单细胞，1受试者×5切片，8个域，28,317细胞）——有ground truth，细胞类型注释较粗。
  - **Xenium**（人COPD肺，单细胞，9,051细胞）——无ground truth，用于人机环演示。
- **基准与方法**：
  - 对比了16种方法，包括：Seurat、BASS、GraphST、STAGATE、SpaGCN、BayesSpace、IRIS、CCST、SEDR、SpaceFlow、conST、stLearn、SCAN‑IT、Leiden、Louvain等，以及形态学增强变体。
  - 实验场景：零样本性能、微调性能（内切片/间切片/跨受试者）、域列表错配鲁棒性、标注比例消融、基因表达缺失鲁棒性、真实病理切片人机协作。
- **评估指标**：
  - 准确性：NMI、HOM、COM（均0~1，越高越好）。
  - 空间连续性：CHAOS（越低越好）、PAS（越低越好）、ASW（越高越好）。

## 4. 资源与算力

- **文中信息**：
  - 开源LLM（Llama‑3.1‑8B/70B, Qwen3‑30B）使用vLLM部署在**2个NVIDIA H200 GPU + 2个CPU核心**上。
  - 速度：Qwen3‑30B约3秒/1024细胞；Llama‑3.1‑70B约18秒/1024细胞。
  - 使用OpenAI API时，STARmap样本（1,088细胞）耗时5–10分钟（取决于网络和服务负载）。
  - **微调的具体显存消耗、训练时长、GPU型号未明确说明**，仅提及使用OpenAI fine‑tuning API，LoRA适配。
- **总结**：算力信息仅部分公开，特别是微调阶段未报告具体训练卡时和资源消耗。

## 5. 实验数量与充分性

- **实验数量**：较为丰富，涵盖：
  - STARmap上零样本与16种方法对比（多种LLM：GPT‑4o mini/4o, Gemini 1.5 Pro, Llama‑3.1‑8B/70B, Qwen3‑30B）。
  - 域列表错配实验（3种场景：遗漏、冗余、替换）。
  - Visium和MERFISH上微调实验（内切片、间切片、跨受试者验证）。
  - 标注比例消融（5%–70%）。
  - 基因表达缺失鲁棒性（丢失率10%–80%）。
  - Xenium数据集的人机环演示与病理学验证。
- **充分性与客观性**：
  - 全部使用公开基准数据集和标准指标，对比方法参数来自先前基准工作（SDMBench），保证了公平性。
  - 每个方法运行3次报告均值，消除随机性。
  - 微调实验随机选择30%作为训练集，内/间/跨受试者设计合理。
- **潜在不足**：Xenium无ground truth，结论依赖病理学家主观判断；仅在4个数据集（2个物种、3个技术平台）上验证，对更多复杂组织（如肿瘤）尚未充分测试。

## 6. 论文的主要结论与发现

1. **零样本性能优越**：SPEAK‑Z在STARmap上NMI最高达0.72（Gemini 1.5 Pro），优于所有非LLM方法；且自动生成有生物学意义的域名称（如“Layer 1”而非“Cluster 0”）。
2. **微调显著提升**：对于细胞类型注释质量低的数据（Visium、MERFISH），30%标注微调后SPEAK‑F性能大幅超越零样本和所有非LLM方法。
3. **两阶段提示改善跨样本泛化**：SPEAK‑Fs在跨受试者场景下表现更稳健，接近用目标受试者自身数据微调的效果。
4. **极小标注即可高效**：仅需5%标注细胞，SPEAK‑F即可超越BASS；30%标注后性能趋于饱和。
5. **鲁棒性**：对域列表遗漏或冗余不敏感（遗漏小面积域影响小，冗余无影响），但错误域名会大幅降低性能（NMI从0.72降至0.19）。
6. **人机环成功**：在COPD肺数据中，SPEAK‑F正确区分了气道和血管平滑肌细胞，差异表达基因符合病理学预期。
7. **计算优势**：并行处理避免内存溢出，支持开放模型保护隐私，可输出推理步骤提升可解释性。

## 7. 优点：方法或实验设计上的亮点

- **融合LLM与专家知识**：既利用LLM预训练的广泛生物学知识，又允许人类通过少量标注引导模型，实现知识对齐。
- **零样本生物意义标签**：直接输出“Layer 1”等可读名称，无需后处理注释，支持跨批次直接比较。
- **域列表鲁棒性**：允许遗漏或冗余域，降低对精确先验知识的需求。
- **高效微调**：LoRA适配仅需少量数据（5%–30%）即可达到高精度，适应稀缺标注场景。
- **两阶段提示**：无需额外手动标注，利用高置信预测更新原型，补偿样本间差异。
- **计算可扩展性**：细胞级并行处理，避免图方法的内存瓶颈；支持本地部署开源LLM保护数据隐私。
- **可解释性**：可输出推理步骤，辅助专家诊断模型是否应用了正确知识。

## 8. 不足与局限

- **对LLM预训练知识的依赖**：对于研究不足的组织或病种（如罕见疾病），LLM知识有限，零样本性能可能差；需依赖微调或更多人工标注。论文未给出置信度评分机制以识别此类案例。
- **需要预设域列表**：用户必须提供可能的域名称列表，虽允许冗余或遗漏，但仍需一定先验知识（可从LLM自动生成，但作者未实现）。
- **邻域半径固定**：当前为手工设定，不同组织/域可能需要不同最优半径，作者未提供自动优化方案。
- **微调资源未明确**：微调所需的GPU显存、训练时间等关键资源信息缺失，不利于可重复性和资源估算。
- **实验覆盖有限**：仅4个数据集（小鼠/人，3种平台），未在肿瘤微环境、多器官同时验证；Xenium演示缺乏定量ground truth，依赖主观病理判断。
- **大模型部署成本**：最优效果依赖Gemini 1.5 Pro等大参数模型，本地部署需高算力（Llama‑3.1‑70B需2×H200）；微调大模型（如GPT‑4o）目前不可用（仅GPT‑4o mini可微调），作者建议未来通过知识蒸馏解决。
- **与现有方法公平性**：对比方法使用预先优化的参数（来自SDMBench基准），但SPEAK‑Z也使用默认参数；微调对比中BASS未使用标注数据进行学习，导致性能无提升，该对比略显偏颇。

（完）
