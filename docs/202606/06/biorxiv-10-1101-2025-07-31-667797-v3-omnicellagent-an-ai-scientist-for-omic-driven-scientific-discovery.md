---
title: "OmniCellAgent: An AI Scientist for Omic-Driven Scientific Discovery"
title_zh: "OmniCellAgent: 用于组学驱动科学发现的AI科学家"
authors: "Huang, D., Li, H., Li, W., Zhang, H., Xu, T., Lu, Y., Fang, K., Xu, Z., Chen, J., Dickson, P., Sardiello, M., Buchser, W., Cooper, J. D., Cruchaga, C., Eghtesady, P., Li, G., Goedegebuure, P., DeNardo, D., Ding, L., Fields, R. C., Zhan, M., Miller, J. P., Province, M., Chen, Y., Payne, P., Li, F."
date: 2026-06-02
pdf: "https://www.biorxiv.org/content/10.1101/2025.07.31.667797v3.full.pdf"
tags: ["query:agent"]
score: 7.0
evidence: 用于组学驱动科学发现的AI智能体，包括病理学
tldr: 现有AI代理需用户预定义疾病数据集，过程耗时且挑战大。OmniCellAgent基于大规模单细胞RNA测序数据，通过多智能体框架自动检索和分析疾病相关数据集，整合生物先验知识、文献和领域专家代理，系统注释组学靶点。在多种疾病评估中成功生成结构化分析报告和科学假设。该框架降低了组学驱动研究的技术门槛，加速生物医学发现。
source: biorxiv
selection_source: fresh_fetch
motivation: 针对现有AI代理需用户预定义疾病数据集的耗时问题，提出自动检索与分析的解决方案。
method: 构建多智能体框架，集成数据检索、先验知识库、文献综述与领域专家代理，自动处理scRNA-seq数据并注释靶点。
result: 在多种疾病场景中成功识别相关数据集，生成结构化分析报告和科学假设。
conclusion: 多智能体AI系统降低技术门槛，加速组学驱动的科学发现与假设生成。
---

## 摘要
现实世界的生物医学科学发现是一个迭代的生命周期，整合了四个核心支柱：针对特定问题的组学数据集的靶向识别和分析；利用丰富的生物医学先验知识数据库对分子数据进行情境感知解释；全面的文献综述；以及人类科学家的主观创造力和专家直觉。这些支柱共同驱动了稳健的证据合成和新假设的产生。最近报道的AI智能体支持自动化的组学分析和文献综述，但通常需要用户预定义和策划特定疾病的数据库，这一过程仍然具有挑战性且耗时。在本研究中，我们提出了OmniCellAgent，一个基于大规模单细胞RNA测序（scRNA-seq）数据集的新型多智能体AI框架，能够自主检索和分析与疾病和对照组相关的、跨组织和细胞类型的scRNA-seq数据集。此外，它整合了生物医学先验知识和文献综述智能体，以及疾病领域特定的专家智能体，以系统性地注释组学数据衍生的靶点。通过聚合来自多个智能体的证据，该框架生成结构化的分析报告和潜在的科学假设。我们在多种疾病背景下评估了OmniCellAgent，展示了其识别相关数据集、生成组学数据分析结果以及产生结构化报告和科学假设的能力。我们的结果表明，多智能体AI系统降低了组学驱动研究的技术门槛，从而加速了生物医学研究和精准医学中的科学发现和假设生成。源代码公开在：https://github.com/FuhaiLiAiLab/OmniCellAgent。

## Abstract
Real-world biomedical scientific discovery operates as an iterative lifecycle integrating four core pillars: the targeted identification and analysis of question-specific omics datasets; the context-aware interpretation of molecular data using rich biomedical prior knowledge database; comprehensive literature reviews; and the subjective creativity and expert intuition of human scientists. Together, these pillars drive robust evidence synthesis and novel hypothesis generation. The recently reported AI agents support automated omics analysis and literature review, which typically require users to predefine and curate disease-specific datasets, which is a process that remains challenging and time-consuming. In this study, we present OmniCellAgent, a novel multi-agent AI framework built on large-scale single-cell RNA sequencing (scRNA-seq) datasets, and can autonomously retrieve and analyze disease and control-related scRNAseq datasets of diverse cell types across tissues and conditions. Moreover, it incorporates a biomedical prior knowledge and literature review agents, and disease domain-specific expert agents to systematically annotate omic data-derived targets. By aggregating evidence across agents, the framework generates structured analytical reports and potential scientific hypotheses. We evaluated OmniCellAgent across multiple disease settings, demonstrating its ability to identify relevant datasets, generate omic data analysis results, and produce structured reports and scientific hypotheses. Our findings demonstrate that multi-agent AI systems lower the technical barriers to omics-driven research, thereby accelerating scientific discovery and hypothesis generation in biomedical research and precision medicine. The source code is publicly available at: https://github.com/FuhaiLiAiLab/OmniCellAgent.