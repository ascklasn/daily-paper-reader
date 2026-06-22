---
title: "OmicOS: A Comprehensive Omics Ecosystem Infrastructure and Agent System for the AI Era"
title_zh: OmicOS：面向人工智能时代的全面组学生态系统基础设施与智能体系统
authors: "Zeng, Z., Meng, X., Hu, L., Li, C., Liu, P., Shi, Y., Ma, X., Gao, L., Wang, X., Luo, Z., Zheng, Y., Xian, J., Lin, Z., Zhu, H., Jiang, Z., Mao, S., Lu, Y., Tang, W., Peng, Q., Ma, Y., Zhou, L., Xing, C., Zhang, X., Xiong, Y., Du, H."
date: 2026-06-16
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.11.731775v1.full.pdf"
tags: ["query:agent"]
score: 9.0
evidence: 面向组学的综合智能体系统基础设施
tldr: "现有组学方法分散于不同语言和工具，难以被AI代理可靠使用。OmicOS基于OmicVerse V2注册694个方法为状态感知函数合约，构建可编程代理环境，支持动态组合与验证。在BiomniBench基准测试中以81.2%准确率排名第一，使小模型任务完成度提升34.2个百分点。该方法重现了R/Bioconductor工作流，并在阿尔茨海默病研究中发现了结肠上皮风险轴，将社区方法转化为可靠的代理驱动系统。"
source: biorxiv
selection_source: fresh_fetch
motivation: 组学分析工具碎片化且面向人类专家，AI代理难以选择、执行和验证，亟需统一可操作的基础设施。
method: 通过OmicVerse V2集成11个领域694种方法，注册为状态感知能力合约，并重构R/Bioconductor算法为Python原生，代理可动态组合验证工作流。
result: "在BiomniBench达81.2%准确率，添加OmicVerse使qwen-3.6-35b任务完成度提升34.2个百分点，并发现阿尔茨海默病结肠上皮风险轴。"
conclusion: OmicOS与OmicVerse将社区方法转化为可靠可扩展的代理系统，定义了AI时代组学的开放基础。
---

## 摘要
生物学领域已积累了庞大的组学方法生态系统，但其中大部分仍是为人类专家而非科学智能体构建的。方法分散于Python包、R/Bioconductor和CRAN工作流、命令行工具、不兼容的数据容器以及隐式对象状态中，这使得即使常规分析也难以被AI系统可靠地选择、执行和验证。为此，我们提出OmicOS，一个全面的组学生态系统基础设施与智能体系统，它将开源组学社区OmicVerse V2转化为面向智能体生物学的可执行基础。OmicVerse V2提供社区底座：可扩展的AnnDataOOM兼容Rust后端、面向智能体的Python算法（涵盖单细胞、空间、批量及多组学分析）、单细胞基础模型接口，以及历史上以R为中心的Bioconductor/CRAN风格工作流的Python原生重构。OmicOS通过将分析函数注册为状态感知能力合约，使智能体能够检查实时数据对象、选择有效方法、执行受控工作流并记录溯源，从而使该底座变得可操作。其结果并非固定流水线，而是一个可编程组学环境，智能体在此环境中基于经过验证的社区方法组合真实分析，而非自行发明工具。在外部及专用基准测试中，OmicOS在评估系统中排名第一，在BiomniBench上达到81.2%。向最小智能体添加OmicVerse后，使用qwen-3.6-35b模型将任务完成率提升高达34.2个百分点，受控消融实验表明，收益来源于注册驱动的执行，而非更大模型、文档检索或不受限制的工具暴露。同一基础设施可扩展至图谱规模数据，在Python中复现以R为中心的工作流，并将外部病理软件转化为智能体可用技能。在一项从全身空间图谱和术语“阿尔茨海默病”出发的发现任务中，OmicOS组合了一个非经典工作流，整合空间表达、遗传关联、eQTL和共定位证据，提名以PICALM、CD2AP和CR1为中心的结肠上皮风险轴。总之，OmicVerse和OmicOS为AI时代的组学定义了开放基础，展示了如何将生物学方法社区转化为可靠、可扩展且可被智能体操作的发现系统。

亮点
O_LIOmicVerse 2.0将涵盖11个组学领域的694种方法整合为可被智能体调用的高级API。
C_LIO_LIRebuildR在输出等价约束下自动将R/Bioconductor方法重构并演化为Python原生实现。
C_LIO_LIOmicOS建立了最先进的组学智能体框架，在跨模型的通用组学基准测试中排名第一，并显著提升了本地开源模型的分析能力。
C_LIO_LI生态系统模块的组合使用提名了一个与阿尔茨海默病风险相关的结肠上皮轴。
C_LIO_LI支持自动迭代演进的外部算法包可集成入OmicOS生态系统。
C_LI

## Abstract
Biology has accumulated a vast ecosystem of omics methods, but much of this ecosystem remains built for expert humans rather than scientific agents. Methods are scattered across Python packages, R/Bioconductor and CRAN workflows, command-line tools, incompatible data containers and implicit object states, making even routine analyses difficult for an AI system to choose, execute and verify reliably. Here we introduce OmicOS, a comprehensive omics ecosystem infrastructure and agent system that turns OmicVerse V2, an open-source omics community, into an executable foundation for agentic biology. OmicVerse V2 provides the community substrate: scalable AnnDataOOM-compatible rust backends, agent-friendly Python algorithms for single-cell, spatial, bulk and multi-omics analysis, interfaces to single-cell foundation models, and Python-native reconstructions of historically R-centred Bioconductor/CRAN-style workflows. OmicOS makes this substrate actionable by registering analytical functions as state-aware capability contracts, allowing agents to inspect live data objects, select valid methods, execute controlled workflows and record provenance. The result is not a fixed pipeline, but a programmable omics environment in which agents compose real analyses from verified community methods rather than inventing tools. Across external and purpose-built benchmarks, OmicOS ranked first among the evaluated systems, reaching 81.2% on BiomniBench. Adding OmicVerse to a minimal agent improved task completion by up to 34.2 percentage points with qwen-3.6-35b, and controlled ablations showed that the gains came from registry-grounded execution rather than from larger models, documentation retrieval or unrestricted tool exposure. The same infrastructure scaled to atlas-sized data, reproduced R-centred workflows in Python and converted external pathology software into agent-usable skills. In a discovery task starting from a whole-body spatial map and the term "Alzheimers disease", OmicOS composed a non-canonical workflow that integrated spatial expression, genetic association, eQTL and colocalization evidence to nominate a colon epithelial risk axis centred on PICALM, CD2AP and CR1. Together, OmicVerse and OmicOS define an open foundation for AI-era omics, showing how a community of biological methods can be transformed into a reliable, extensible and agent-operable system for discovery.

HighlightO_LIOmicVerse 2.0 consolidates 694 methods spanning 11 omics domains into agent-callable high-level APIs.
C_LIO_LIRebuildR automatically reconstructs and evolves R/Bioconductor methods as Python-native implementations under output-equivalence gates.
C_LIO_LIOmicOS establishes a state-of-the-art omics agent harness, ranking first on general omics benchmarks across models and substantially improving the analytical capability of local open-source models.
C_LIO_LICompositional use of ecosystem modules nominates a colon epithelial axis associated with Alzheimers disease risk.
C_LIO_LIExternal algorithm packages supporting automatic iterative evolution can be integrated into the OmicOS ecosystem.
C_LI

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：生物学领域积累了庞大的组学方法生态系统，但这些方法分散于Python包、R/Bioconductor和CRAN工作流、命令行工具、不兼容的数据容器以及隐式对象状态中，主要面向人类专家而非AI系统。这种碎片化导致AI代理难以可靠地选择、执行和验证常规分析。
- **研究动机**：构建一个统一、可操作的基础设施，将社区方法转化为AI代理能够动态组合、执行和验证的系统，从而在AI时代实现组学分析的自动化和可靠发现。
- **整体含义**：提出OmicOS（综合组学生态系统基础设施与智能体系统），将开源社区OmicVerse V2转化为面向智能体生物学的可执行基础，定义AI时代组学的开放基础。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将分析函数注册为**状态感知能力合约（state-aware capability contracts）**，使AI代理能够检查实时数据对象、选择有效方法、执行受控工作流并记录溯源。结果并非固定流水线，而是一个可编程组学环境，代理基于经过验证的社区方法组合分析，而非自行发明工具。

- **关键技术细节**：
  - **OmicVerse V2**：提供社区底座，包括：
    - 可扩展的AnnDataOOM兼容Rust后端
    - 面向智能体的Python算法（涵盖单细胞、空间、批量及多组学分析）
    - 单细胞基础模型接口
    - **RebuildR**：自动将R/Bioconductor和CRAN工作流重构为Python原生实现（在输出等价约束下），历史上以R为中心的方法被转化为Python原生算法。
  - **OmicOS**：通过注册机制使方法可被代理调用。代理可以：
    - 检查数据对象状态
    - 选择有效方法（基于合约的上下文检查）
    - 执行受控工作流
    - 记录全路径溯源
  - **生态系统可扩展性**：支持自动迭代演进的外部算法包集成。

## 3. 实验设计：数据集/场景、基准测试、对比方法

- **基准测试**：
  - **BiomniBench**：通用组学基准测试。OmicOS达到**81.2%准确率**，在评估系统中排名第一。
  - **外部专用基准**：未具体说明名称，但提及在跨模型的通用组学基准中排名第一。
- **实验场景**：
  - **消融实验**：向最小代理添加OmicVerse，使用qwen-3.6-35b模型，任务完成度提升高达34.2个百分点。受控消融实验表明收益来自注册驱动的执行，而非更大模型、文档检索或不受限制的工具暴露。
  - **图谱规模数据**：验证基础设施可扩展到大规模数据。
  - **R工作流复现**：在Python中成功复现以R为中心的工作流。
  - **外部病理软件集成**：将外部病理软件转化为代理可用技能。
  - **发现任务**：从全身空间图谱和术语“阿尔茨海默病”出发，组合非经典工作流（空间表达、遗传关联、eQTL、共定位），提名以**PICALM、CD2AP、CR1**为中心的结肠上皮风险轴。
- **对比方法**：在BiomniBench上与其他系统对比；消融实验对比有/无OmicVerse、不同模型大小、文档检索、不受限制工具暴露等条件。

## 4. 资源与算力

- 文中**未明确说明**使用的具体GPU型号、数量、训练时长等算力信息。
- 仅提及“图谱规模数据”和“外部病理软件”等处理，暗示可能需要一定计算资源，但无精确记录。
- 推测：由于涉及多种方法集成和代理执行，可能使用标准服务器集群或GPU工作站，但论文未披露硬件细节。

## 5. 实验数量与充分性

- **实验数量**：主要包括：
  - BiomniBench基准测试（1组主实验）
  - 消融实验（至少4组：添加OmicVerse vs 无、不同模型大小、文档检索、工具暴露）
  - 图谱规模数据处理实验（1组）
  - R工作流复现实验（1组）
  - 病理软件集成实验（1组）
  - 阿尔茨海默病发现任务（1组组合工作流）
- **充分性与客观性**：
  - **充分**：覆盖了多个维度（基准性能、消融分析、扩展性、复现性、实际发现），消融实验设计合理，控制了关键变量。
  - **公平**：BiomniBench是外部公开基准，对比系统未详细说明，但“排名第一”表明客观比较。消融实验结果量化了OmicVerse的增益，且排除了其他因素的干扰。
  - **局限性**：未提供统计显著性检验（如置信区间），也未在更多独立基准上验证。发现任务属于案例研究，需要进一步验证。

## 6. 论文的主要结论与发现

- OmicVerse 2.0整合了694种方法，覆盖11个组学领域，提供高级API供代理调用。
- RebuildR成功将R/Bioconductor方法自动重构为Python原生实现，维护输出等价性。
- OmicOS建立了最先进的组学代理框架，在BiomniBench上达到81.2%准确率，显著提升本地开源模型（如qwen-3.6-35b）的分析能力（提升34.2个百分点）。
- 收益来源于注册驱动的受控执行，而非模型大小或文档检索。
- 生态系统模块的组合使用提名了阿尔茨海默病相关的结肠上皮风险轴（PICALM, CD2AP, CR1）。
- 外部算法包可集成并通过自动迭代演进融入生态系统。

## 7. 优点：方法或实验设计上的亮点

- **方法亮点**：
  - 将传统社区方法转化为**状态感知能力合约**，实现AI代理的可控、可溯源操作。
  - **RebuildR**创新性自动重构R代码为Python原生，解决了跨语言兼容性。
  - **端到端可编程环境**：代理动态组合已验证方法，而非创造新工具，提高可靠性。
- **实验设计亮点**：
  - **消融实验**设计精细：分离了OmicVerse注册驱动的收益与模型大小、文档检索、工具暴露等混淆因素。
  - **发现任务**展示了系统潜力：从非标准假设（结肠上皮与阿尔茨海默病）中发现新风险轴，验证了组合创新能力。
  - 覆盖多种场景：基准性能、规模扩展、语言迁移、外部工具集成、生物学发现。

## 8. 不足与局限

- **实验覆盖**：
  - 仅在一个公开基准（BiomniBench）上提供性能数据，缺乏在更多独立多组学基准上的评估。
  - 发现任务为单一案例，未提供统计学验证（如独立队列验证、多重假设校正）。
- **偏差风险**：
  - OmicVerse本身是论文作者团队开发的社区，可能对自家方法更友好，存在一定位置偏差。
  - 对比系统未列出具体名称，无法判断对比的全面性。
- **应用限制**：
  - 依赖于OmicVerse生态系统，外部方法集成需要自动迭代演进机制，可能增加复杂性和维护成本。
  - 论文未讨论代理在真实实验室环境中处理隐私数据、版本冲突、软件环境等实际部署问题。
  - 资源消耗（如图谱数据处理的GPU内存）未报告，可能影响可复现性。
- **其他**：未提供代码仓库、详细API文档或用户指南（虽然OmicVerse可能存在），限制了社区采用。

（完）
