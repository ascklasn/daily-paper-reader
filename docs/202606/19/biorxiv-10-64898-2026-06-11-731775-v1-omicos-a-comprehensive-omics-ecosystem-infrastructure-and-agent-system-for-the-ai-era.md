---
title: "OmicOS: A Comprehensive Omics Ecosystem Infrastructure and Agent System for the AI Era"
title_zh: OmicOS：面向AI时代的综合性组学生态系统基础设施与智能体系统
authors: "Zeng, Z., Meng, X., Hu, L., Li, C., Liu, P., Shi, Y., Ma, X., Gao, L., Wang, X., Luo, Z., Zheng, Y., Xian, J., Lin, Z., Zhu, H., Jiang, Z., Mao, S., Lu, Y., Tang, W., Peng, Q., Ma, Y., Zhou, L., Xing, C., Zhang, X., Xiong, Y., Du, H."
date: 2026-06-16
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.11.731775v1.full.pdf"
tags: ["query:agent"]
score: 8.0
evidence: 组学生态系统代理系统支持自主生物学
tldr: "组学分析方法分散在Python、R/Bioconductor和命令行工具中，数据容器和对象状态不兼容，AI系统难以可靠选择和执行。OmicOS将OmicVerse V2的694种方法注册为状态感知能力合约，使代理能检查数据、选择方法、执行工作流并记录溯源。在BiomniBench上达81.2%准确率，为小型模型带来最高34.2个百分点的任务完成度提升。该基础设施可扩展至大规模数据，并整合外部病理软件，成功从空间图谱出发发现阿尔茨海默病相关的结肠上皮风险轴。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有组学方法碎片化且面向人类专家，AI代理无法系统调用和验证，亟需统一可执行的基础设施。
method: 构建OmicVerse V2，提供AnnDataOOM后端和Python原生方法；OmicOS注册为状态感知合约，支持代理可控工作流和溯源。
result: "BiomniBench排名第一（81.2%），小型模型任务完成度提升34.2个百分点，重现R工作流，发现阿尔茨海默病结肠上皮风险轴。"
conclusion: OmicOS将社区组学方法转化为可靠、可扩展的代理系统，为AI时代组学分析提供开放基础。
---

## 摘要
生物学已经积累了大量的组学方法生态系统，但其中大部分生态系统仍是针对人类专家而非科学智能体构建的。方法分散在Python包、R/Bioconductor和CRAN工作流、命令行工具、不兼容的数据容器以及隐式对象状态中，这使得即使是常规分析，AI系统也难以可靠地选择、执行和验证。在这里，我们介绍OmicOS，一个全面的组学生态系统基础设施和智能体系统，它将开源组学社区OmicVerse V2转变为可执行的智能体生物学基础。OmicVerse V2提供了社区基础：可扩展的兼容AnnDataOOM的Rust后端、用于单细胞、空间、批量和多组学分析的智能体友好型Python算法、与单细胞基础模型的接口，以及以R为中心的Bioconductor/CRAN风格工作流的Python原生重建。OmicOS通过将分析函数注册为状态感知能力契约，使这些基础可操作，允许智能体检查实时数据对象、选择有效方法、执行受控工作流并记录溯源。结果并非固定流程，而是一个可编程的组学环境，智能体在其中使用经过验证的社区方法组合真实分析，而不是发明工具。在外部和专门构建的基准测试中，OmicOS在评估系统中排名第一，在BiomniBench上达到81.2%。将OmicVerse添加到最小智能体中，使用qwen-3.6-35b可将任务完成度提高多达34.2个百分点，受控消融实验表明，收益来自注册驱动的执行，而非更大的模型、文档检索或不受限制的工具暴露。相同的基础设施扩展到图谱规模的数据，在Python中重现了以R为中心的工作流，并将外部病理软件转化为智能体可用的技能。在一个从全身空间图谱和术语“阿尔茨海默病”开始的发现任务中，OmicOS组合了一个非标准工作流，整合了空间表达、遗传关联、eQTL和共定位证据，以提名一个以PICALM、CD2AP和CR1为中心的结肠上皮风险轴。总之，OmicVerse和OmicOS为AI时代的组学定义了一个开放基础，展示了如何将生物学方法的社区转变为可靠、可扩展且智能体可操作的发现系统。

亮点
O_LIOmicVerse 2.0将跨越11个组学领域的694种方法整合为智能体可调用的高级API。
C_LIO_LIRebuildR自动在输出等价门控下将R/Bioconductor方法重建并演进为Python原生实现。
C_LIO_LIOmicOS建立了一个最先进的组学智能体框架，在跨模型的通用组学基准测试中排名第一，并显著提升了本地开源模型的分析能力。
C_LIO_LI生态系统模块的组合使用提名了一个与阿尔茨海默病风险相关的结肠上皮轴。
C_LIO_LI支持自动迭代演进的外部算法包可以集成到OmicOS生态系统中。
C_LI

## Abstract
Biology has accumulated a vast ecosystem of omics methods, but much of this ecosystem remains built for expert humans rather than scientific agents. Methods are scattered across Python packages, R/Bioconductor and CRAN workflows, command-line tools, incompatible data containers and implicit object states, making even routine analyses difficult for an AI system to choose, execute and verify reliably. Here we introduce OmicOS, a comprehensive omics ecosystem infrastructure and agent system that turns OmicVerse V2, an open-source omics community, into an executable foundation for agentic biology. OmicVerse V2 provides the community substrate: scalable AnnDataOOM-compatible rust backends, agent-friendly Python algorithms for single-cell, spatial, bulk and multi-omics analysis, interfaces to single-cell foundation models, and Python-native reconstructions of historically R-centred Bioconductor/CRAN-style workflows. OmicOS makes this substrate actionable by registering analytical functions as state-aware capability contracts, allowing agents to inspect live data objects, select valid methods, execute controlled workflows and record provenance. The result is not a fixed pipeline, but a programmable omics environment in which agents compose real analyses from verified community methods rather than inventing tools. Across external and purpose-built benchmarks, OmicOS ranked first among the evaluated systems, reaching 81.2% on BiomniBench. Adding OmicVerse to a minimal agent improved task completion by up to 34.2 percentage points with qwen-3.6-35b, and controlled ablations showed that the gains came from registry-grounded execution rather than from larger models, documentation retrieval or unrestricted tool exposure. The same infrastructure scaled to atlas-sized data, reproduced R-centred workflows in Python and converted external pathology software into agent-usable skills. In a discovery task starting from a whole-body spatial map and the term "Alzheimers disease", OmicOS composed a non-canonical workflow that integrated spatial expression, genetic association, eQTL and colocalization evidence to nominate a colon epithelial risk axis centred on PICALM, CD2AP and CR1. Together, OmicVerse and OmicOS define an open foundation for AI-era omics, showing how a community of biological methods can be transformed into a reliable, extensible and agent-operable system for discovery.

HighlightO_LIOmicVerse 2.0 consolidates 694 methods spanning 11 omics domains into agent-callable high-level APIs.
C_LIO_LIRebuildR automatically reconstructs and evolves R/Bioconductor methods as Python-native implementations under output-equivalence gates.
C_LIO_LIOmicOS establishes a state-of-the-art omics agent harness, ranking first on general omics benchmarks across models and substantially improving the analytical capability of local open-source models.
C_LIO_LICompositional use of ecosystem modules nominates a colon epithelial axis associated with Alzheimers disease risk.
C_LIO_LIExternal algorithm packages supporting automatic iterative evolution can be integrated into the OmicOS ecosystem.
C_LI