---
title: "SpatialClaw: A Memory-Augmented Autonomous Ecosystem for Spatial Omics Analysis"
title_zh: SpatialClaw：一种用于空间组学分析的内存增强自主生态系统
authors: "Du, G., Lan, O., Wei, X., Wu, Y., Meng, G., Wu, J., Li, Z., Li, X., Shang, X."
date: 2026-05-25
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.21.723451v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 统一的空间组学分析AI平台
tldr: 空间组学分析面临工具碎片化、工作流不可重复的问题。SpatialClaw通过集成30项专业技能并引入图结构持久记忆架构（会话、情节、语义三层），利用记忆增强推理算子实现自然语言驱动的一站式分析。在三个记忆敏感场景中优于标准大模型，并在15切片三阴性乳腺癌队列中零脚本完成全流程分析。该工作将空间组学从零散计算转变为可追溯、可重复、自我优化的生态系统。
source: biorxiv
selection_source: fresh_fetch
motivation: 空间组学分析方法碎片化，导致端到端分析复杂且不可重复，缺乏领域特定的自然语言交互工具。
method: 构建包含30项技能的自主生态系统，引入图结构持久记忆（三层次）和记忆增强推理算子，实现自然语言驱动的统一分析。
result: 在三个记忆敏感场景中超越标准LLM和仅记忆配置；三项对话内完成15切片乳腺癌微环境全流程分析。
conclusion: 协同综合工具与结构化记忆，实现可追溯、可重复、自我提升的空间组学发现生态系统。
---

## 摘要
尽管空间组学的扩展彻底改变了我们解析组织结构的能力，但不相容的计算方法的积累严重割裂了端到端分析，使得复杂工作流难以复现。通用对话代理缺乏导航复杂生物学管道所需的领域特异性精度。为克服这一问题，我们提出了SpatialClaw，一种内存增强自主生态系统，将空间组学分析统一在单一自然语言交互之下。SpatialClaw整合了30项专门技能，涵盖原始数据预处理、空间域识别、解卷积、空间可变基因检测、细胞间通讯分析、多样本及跨模态整合。与现有代理不同，SpatialClaw引入了一种基于图的持久内存架构，将数据集元数据、分析谱系、生物学见解以及用户偏好作为版本化节点和边缘存储于三个层次层级（会话层、情景层和语义层）中，并由确定性提升策略管理。内存增强推理（MAR）操作器连接内存存储与主代理，将检索到的经验综合为针对每个查询的任务特定指导。在涵盖10项空间组学技能的三个内存敏感场景的严格基准测试中，SpatialClaw的表现优于标准大型语言模型和仅内存配置。此外，通过解析15切片人类三阴性乳腺癌队列的复杂肿瘤微环境，我们展示了其强大的生物学实用性。仅需三个对话轮次且无需直接脚本编写，SpatialClaw即可执行全面的端到端工作流，生成标准化输出包。最终，通过将综合分析工具与结构化持久内存协同，SpatialClaw将空间组学从脱节的计算拼凑提升为完全可追踪、可重复且自改进的发现生态系统。SpatialClaw已准备就绪，可通过https://github.com/ShangBioLab/SpatialClaw获取。

## Abstract
While the expansion of spatial omics has revolutionized our ability to dissect tissue architecture, the accumulation of incompatible computational methods has heavily fragmented end-to-end analysis, rendering complex workflows irreproducible. Generic conversational agents lack the domain-specific precision necessary to navigate the intricate biological pipelines. To overcome this, we present SpatialClaw, a memory-augmented autonomous ecosystem to unify spatial omics analysis under a single natural-language interaction. SpatialClaw integrates 30 specialized skills, spanning raw data preprocessing, spatial domain identification, deconvolution, spatially variable gene detection, cell-cell communication analysis, multi-sample and cross-modality integration. Distinct from existing agents, SpatialClaw introduces a graph-based persistent memory architecture that stores dataset metadata, analysis lineage, biological insights, and user preferences as versioned nodes and edges across three hierarchical layers (Session, Episodic, and Semantic), governed by a deterministic promotion policy. A Memory-Augmented Reasoning (MAR) Operator bridges the memory store and the main agent, synthesizing retrieved experiences into task-specific guidance for each query. In rigorous benchmarking spanning three memory-sensitive scenarios across 10 spatialomics skills, SpatialClaw outperforms both a standard large language model and the memory-only configuration. Furthermore, we demonstrate its robust biological utility by dissecting the complex tumor microenvironment of a 15-section human triple-negative breast cancer cohort. In merely three conversational turns and with zero direct scripting, SpatialClaw executes a comprehensive end-to-end workflow, yielding standardized output bundles. Ultimately, by synergizing comprehensive analytical tools with structured persistent memory, SpatialClaw elevates spatial omics from disjointed computational stitching to a fully traceable, reproducible, and self-improving discovery ecosystem. SpatialClaw is ready to use at https://github.com/ShangBioLab/SpatialClaw.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：空间组学分析面临工具碎片化、工作流不可重复的严重困境。大量不相容的计算方法累积，导致端到端分析被割裂，复杂流程难以复现；通用对话代理（如标准LLM）缺乏领域特异性精度，无法导航复杂的生物学管道。
- **研究动机**：亟需一个统一的、自然语言驱动的自主生态系统，能够集成空间组学全流程的专门技能，并引入结构化持久记忆以支持跨会话的知识复用、分析追踪和自我改进。
- **整体含义**：将空间组学从脱节的计算拼凑提升为完全可追踪、可重复且自优化的发现生态系统，显著降低分析门槛和复现成本。

## 2. 论文提出的方法论

- **核心思想**：构建一个内存增强的自主智能体（SpatialClaw），通过集成30项专门技能，并引入图结构持久记忆架构，实现自然语言驱动的一站式空间组学分析。
- **关键技术细节**：
  - **技能集成**：覆盖原始数据预处理、空间域识别、解卷积、空间可变基因检测、细胞间通讯分析、多样本及跨模态整合等30项专业技能。
  - **图结构持久记忆架构**：分三个层次层级存储：
    - **会话层**：记录当前对话上下文与临时交互。
    - **情景层**：存储过去会话中的完整分析谱系（操作序列、参数、中间结果）。
    - **语义层**：提炼升华后的生物学见解、用户偏好和跨会话知识。
    - 所有数据以版本化节点和边形式存储于图结构中，由确定性提升策略管理（决定何时将短期记忆提升至长期记忆）。
  - **内存增强推理（MAR）算子**：连接记忆存储与主智能体，针对每个用户查询，从记忆中检索相关经验（如先前成功的工作流、领域常识），综合为任务特定的指导，辅助主智能体决策。
- **算法流程**（文字描述）：
  1. 用户以自然语言提出空间组学分析需求。
  2. MAR算子查询图记忆存储，检索历史中类似场景的会话/情景/语义知识。
  3. 主智能体（基于LLM）接收查询与检索到的指导，调用对应的专业化技能（工具模块）执行分析。
  4. 每一步执行结果和中间决策被记录为版本化节点，更新到会话层；关键重复模式或用户确认的见解经提升策略转入情景层或语义层。
  5. 最终反馈与产出包以标准格式输出，同时记忆被持久化，供后续会话复用。

## 3. 实验设计

- **数据集/场景**：
  - **三个记忆敏感场景**：覆盖10项空间组学技能，专门测试智能体在需要跨会话记忆复用、分析谱系追踪和个性化偏好适应方面的能力（例如：同一数据集的增量分析、跨队列的相似分析模式复用、用户偏好记录后的自动化调整）。
  - **真实生物学用例**：15切片人类三阴性乳腺癌（TNBC）队列，解析复杂肿瘤微环境。
- **Benchmark**：在所选的三个记忆敏感场景上，对比以下方法：
  1. **标准大型语言模型（标准LLM）**：无专门技能集成，无记忆。
  2. **仅内存配置（Memory-only）**：具备持久记忆存储但未使用MAR算子（即直接检索而不合成任务指导）。
  3. **SpatialClaw（完整方法）**：同时具备30项专门技能、图持久记忆和MAR算子。
- **评估指标**：未明确列出具体数值指标，但从描述看侧重于任务完成成功率、跨会话记忆回溯正确率、用户交互轮次效率等。
- **零脚本全流程演示**：在乳腺癌队列中，仅通过三个对话轮次（无需用户直接编写代码），SpatialClaw执行了从数据预处理到通讯分析及结果打包的完整端到端工作流。

## 4. 资源与算力

- **文中未明确说明**使用的GPU型号、数量、训练时长或推理资源。推测可能基于LLM API（如GPT-4）或开源模型微调，但论文摘要和元数据仅提供了代码仓库地址，未披露具体算力细节。

## 5. 实验数量与充分性

- **实验组数**：
  - 基准测试：三个记忆敏感场景 × 3种方法对比 = 9组基本比较（可能每个场景含多次重复）。
  - 乳腺癌队列：一个端到端案例（3轮对话），展示完整流程。
  - 未提及明确的消融实验（如逐步移除记忆层级或MAR算子的逐级消融），仅有“仅内存配置”作为部分消融对照。
- **充分性评价**：
  - **优点**：三个记忆敏感场景直接针对核心创新点（记忆增强），对比标准LLM和仅记忆配置，能体现MAR算子与综合工具的联合效益。乳腺癌案例展示了真实生物学场景的可行性。
  - **不足**：实验中未系统评估不同记忆层级单独、不同提升策略、技能粒度等消融效果。基准测试规模有限（10项技能，三个场景），未能覆盖所有30项技能的组合复杂性。缺少与传统工作流（如手动R/Python脚本）在时间、准确率、复现性上的量化对比。

## 6. 论文的主要结论与发现

- 在三个记忆敏感场景中，SpatialClaw全面优于标准LLM和仅内存配置，证实了结构化持久记忆与内存增强推理算子的关键作用。
- 仅需三个对话轮次且零脚本，SpatialClaw即可对15切片三阴性乳腺癌队列完成全套空间组学分析，生成标准化输出包，展示了强大的生物学实用性。
- 通过协同综合分析工具与结构化持久记忆，空间组学分析从碎片化、不可复现的计算缝合转变为可追踪、可重复、自改进的生态系统。

## 7. 优点

- **方法创新**：首次将图结构多层级持久记忆引入空间组学AI智能体，并设计专用MAR算子连接记忆与推理，解决领域特定分析中的跨会话知识复用问题。
- **实用性**：集成30项专业技能覆盖全流程，自然语言交互降低用户使用门槛；三个对话轮次即可完成真实复杂分析，提升效率与复现性。
- **设计严谨**：记忆采用版本化图存储，支持分析谱系追踪；确定性提升策略保证记忆质量；基准测试设置记忆敏感场景，直接验证核心贡献。
- **开源**：提供GitHub代码仓库，便于社区复现与扩展。

## 8. 不足与局限

- **实验规模有限**：仅三个记忆敏感场景和1个生物学案例，未能在大规模多样本多平台数据集上系统评估通用性；缺少与经典工具链（如STUtility、Seurat等）的直接运行时间和准确率对比。
- **消融实验不充分**：仅对比了完整方法与“仅内存配置”，未单独分析会话层/情景层/语义层各自贡献，也未评估不同提升策略的影响。
- **资源成本未提及**：未说明推理所需的算力与耗时，可能面临LLM API调用成本或大模型本地部署开销。
- **潜在偏差风险**：记忆增强依赖初始会话经验积累，若首次分析不准确或用户偏好异常，可能误导后续任务；此外，确定性提升策略虽提高可解释性，但可能缺乏灵活性，无法适应动态变化的需求。
- **应用限制**：仅针对空间组学领域，记忆架构与技能库与领域紧密耦合，迁移至其他组学或通用任务需重新设计与集成；当前版本可能不支持实时数据流或大规模队列的并行分析。

（完）
