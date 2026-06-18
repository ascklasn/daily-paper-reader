---
title: "OmicOS: A Comprehensive Omics Ecosystem Infrastructure and Agent System for the AI Era"
title_zh: OmicOS：面向AI时代的综合组学生态系统基础设施与智能体系统
authors: "Zeng, Z., Meng, X., Hu, L., Li, C., Liu, P., Shi, Y., Ma, X., Gao, L., Wang, X., Luo, Z., Zheng, Y., Xian, J., Lin, Z., Zhu, H., Jiang, Z., Mao, S., Lu, Y., Tang, W., Peng, Q., Ma, Y., Zhou, L., Xing, C., Zhang, X., Xiong, Y., Du, H."
date: 2026-06-16
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.11.731775v1.full.pdf"
tags: ["query:agent"]
score: 6.0
evidence: 用于AI驱动生物学的组学生态系统基础设施和智能体系统
tldr: "生物学组学方法分散于Python、R/Bioconductor、命令行等工具，AI代理难以可靠选择执行。OmicOS将OmicVerse V2社区的方法注册为状态感知能力契约，使代理能检查数据对象、选择有效方法、执行可控工作流并记录来源。在BiomniBench上达81.2%准确率，添加OmicVerse使qwen-3.6-35b模型任务完成率提升34.2个百分点。该系统将社区方法转化为可靠、可扩展的代理操作基础，代表了AI时代组学基础设施的新范式。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有组学方法分散且面向专家，AI代理难以选择执行验证，需构建专为代理设计的可编程生态系统。
method: 将OmicVerse V2的分析函数注册为状态感知能力契约，代理可检查数据对象、选择方法、执行工作流并记录来源。
result: "BiomniBench排名第一（81.2%）；添加OmicVerse使qwen-3.6-35b任务完成率提升34.2个百分点。"
conclusion: 定义了AI时代组学开放基础，将社区方法转化为可靠、可扩展的代理操作生态系统。
---

## 摘要
生物学积累了庞大的组学方法生态系统，但其中大部分仍是为人类专家而非科学智能体构建的。方法分散在Python包、R/Bioconductor和CRAN工作流、命令行工具、不兼容的数据容器及隐式对象状态中，使得即使是常规分析，AI系统也难以可靠地选择、执行和验证。在此，我们介绍OmicOS——一个综合的组学生态系统基础设施与智能体系统，它将开源组学社区OmicVerse V2转化为可执行的智能体生物学基础。OmicVerse V2提供社区基质：可扩展的AnnDataOOM兼容Rust后端、适用于单细胞、空间、bulk和多组学分析的智能体友好型Python算法、单细胞基础模型接口，以及历史上以R为中心的Bioconductor/CRAN风格工作流的Python原生重构。OmicOS通过将分析函数注册为状态感知的能力契约，使该基质可行，允许智能体检查实时数据对象、选择有效方法、执行受控工作流并记录来源。其结果并非固定管道，而是一个可编程的组学环境，智能体在此从经过验证的社区方法中组合真实分析，而非发明工具。在外部及专门构建的基准测试中，OmicOS在评估系统中排名第一，在BiomniBench上达到81.2%。将OmicVerse添加到最小智能体后，使用qwen-3.6-35b的任务完成度提升了高达34.2个百分点，而受控消融实验表明，性能提升来源于基于注册的执行，而非更大模型、文档检索或不受限制的工具暴露。同一基础设施可扩展至图谱规模数据，在Python中复现以R为中心的工作流，并将外部病理软件转化为智能体可用技能。在一个从全身空间图谱和“阿尔茨海默病”术语开始的发现任务中，OmicOS组合了一个非常规工作流，整合了空间表达、遗传关联、eQTL和共定位证据，提出了以PICALM、CD2AP和CR1为中心的结肠上皮风险轴。总之，OmicVerse和OmicOS定义了AI时代组学的开放基础，展示了生物方法社区如何转化为一个可靠、可扩展且智能体可操作的发现系统。

亮点
- OmicVerse 2.0将涵盖11个组学领域的694种方法整合为智能体可调用的高级API。
- RebuildR在输出等价门控下自动将R/Bioconductor方法重构并演进为Python原生实现。
- OmicOS建立了最先进的组学智能体框架，在跨模型的通用组学基准测试中排名第一，显著提升了本地开源模型的分析能力。
- 生态系统模块的组合使用提出了与阿尔茨海默病风险相关的结肠上皮轴。
- 支持自动迭代演进的外部算法包可集成到OmicOS生态系统中。

## Abstract
Biology has accumulated a vast ecosystem of omics methods, but much of this ecosystem remains built for expert humans rather than scientific agents. Methods are scattered across Python packages, R/Bioconductor and CRAN workflows, command-line tools, incompatible data containers and implicit object states, making even routine analyses difficult for an AI system to choose, execute and verify reliably. Here we introduce OmicOS, a comprehensive omics ecosystem infrastructure and agent system that turns OmicVerse V2, an open-source omics community, into an executable foundation for agentic biology. OmicVerse V2 provides the community substrate: scalable AnnDataOOM-compatible rust backends, agent-friendly Python algorithms for single-cell, spatial, bulk and multi-omics analysis, interfaces to single-cell foundation models, and Python-native reconstructions of historically R-centred Bioconductor/CRAN-style workflows. OmicOS makes this substrate actionable by registering analytical functions as state-aware capability contracts, allowing agents to inspect live data objects, select valid methods, execute controlled workflows and record provenance. The result is not a fixed pipeline, but a programmable omics environment in which agents compose real analyses from verified community methods rather than inventing tools. Across external and purpose-built benchmarks, OmicOS ranked first among the evaluated systems, reaching 81.2% on BiomniBench. Adding OmicVerse to a minimal agent improved task completion by up to 34.2 percentage points with qwen-3.6-35b, and controlled ablations showed that the gains came from registry-grounded execution rather than from larger models, documentation retrieval or unrestricted tool exposure. The same infrastructure scaled to atlas-sized data, reproduced R-centred workflows in Python and converted external pathology software into agent-usable skills. In a discovery task starting from a whole-body spatial map and the term "Alzheimers disease", OmicOS composed a non-canonical workflow that integrated spatial expression, genetic association, eQTL and colocalization evidence to nominate a colon epithelial risk axis centred on PICALM, CD2AP and CR1. Together, OmicVerse and OmicOS define an open foundation for AI-era omics, showing how a community of biological methods can be transformed into a reliable, extensible and agent-operable system for discovery.

HighlightO_LIOmicVerse 2.0 consolidates 694 methods spanning 11 omics domains into agent-callable high-level APIs.
C_LIO_LIRebuildR automatically reconstructs and evolves R/Bioconductor methods as Python-native implementations under output-equivalence gates.
C_LIO_LIOmicOS establishes a state-of-the-art omics agent harness, ranking first on general omics benchmarks across models and substantially improving the analytical capability of local open-source models.
C_LIO_LICompositional use of ecosystem modules nominates a colon epithelial axis associated with Alzheimers disease risk.
C_LIO_LIExternal algorithm packages supporting automatic iterative evolution can be integrated into the OmicOS ecosystem.
C_LI