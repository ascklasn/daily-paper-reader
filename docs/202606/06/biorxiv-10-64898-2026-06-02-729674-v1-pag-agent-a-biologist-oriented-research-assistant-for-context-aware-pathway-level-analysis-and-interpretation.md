---
title: "PAG-Agent: a biologist-oriented research assistant for context-aware pathway-level analysis and interpretation"
title_zh: PAG-Agent：面向生物学家的情境感知通路级分析与解读研究助手
authors: "Nguyen, Q.-H., Zhang, Z., Le, D.-H., Chen, J. Y., Ku, W.-S., Chen, H., Yue, Z."
date: 2026-06-06
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.02.729674v1.full.pdf"
tags: ["query:agent"]
score: 6.0
evidence: 面向生物学家的研究助手，利用大语言模型进行通路分析与解释
tldr: 现有路径分析工具常孤立分析基因集，难以结合实验上下文。PAG-Agent 提出面向生物学家的上下文感知路径分析助手，集成统计、文献推理与写作支持，通过点击和对话交互简化流程。在阿尔茨海默病案例中一致识别神经退行相关路径，引用检索基准优于六个LLM。该工具降低了路径分析技术壁垒，助力从数据到生物学解释。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有路径分析工具难以结合实验条件优先化生物学相关路径，导致结果难以解释。
method: 集成路径级统计分析、上下文感知解释、文献推理和写作支持，支持点击与对话交互。
result: 在阿尔茨海默病案例中一致识别神经退行路径；引用检索基准 outperform 六个LLM。
conclusion: PAG-Agent 降低路径分析技术壁垒，助力研究者从组学数据到生物学解释与假设生成。
---

## 摘要
通路分析是将基因层面的组学结果转化为生物学机制的关键步骤，然而现有工作流往往给研究者留下难以解读、验证和联系实验背景的统计显著通路长列表。我们开发了PAG-Agent，这是一个面向生物学家的虚拟研究助手，它将通路级统计分析、情境感知生物学解读、文献支撑推理和科学写作支持整合在一个统一工作流中。PAG-Agent支持批量及单细胞转录组数据，用户可通过点击式与聊天式交互执行数据预处理、差异表达分析、通路分析、通路级共识分析和通路级元分析。与大多孤立分析基因集的传统通路分析工具不同，PAG-Agent引入实验条件和研究目标，优先排序生物学相关通路并生成可解释的假设。该系统还提供基因与通路注释、引文检索、可视化和写作精修功能。在使用三个转录组数据集进行的阿尔茨海默病例研究中，PAG-Agent在多种分析方法和数据集上一致识别出神经退行相关通路。在引文检索基准测试中，PAG-Agent在五个常见文献支撑场景中优于六种竞争性LLM，展现出更强的情境相关有效参考文献提供能力。总体而言，PAG-Agent降低了通路级分析的技术门槛，帮助研究者从转录组数据走向生物学根基性解读、假设生成与科学交流。

## Abstract
Pathway analysis is a critical step for translating gene-level omics results into biological mechanisms, yet existing workflows often leave researchers with long lists of statistically significant pathways that are difficult to interpret, validate, and connect to experimental context. We developed PAG-Agent, a biologist-oriented virtual research assistant that integrates pathway-level statistical analysis, context-aware biological interpretation, literature-supported reasoning, and scientific writing support within a unified workflow. PAG-Agent supports bulk and single-cell transcriptomic data and enables users to perform data preprocessing, differential expression analysis, pathway analysis, pathway-level consensus analysis, and pathway-level meta-analysis through click-based and chat-based interactions. Unlike conventional pathway-analysis tools that analyze gene sets largely in isolation, PAG-Agent incorporates experimental conditions and research objectives to prioritize biologically relevant pathways and generate interpretable hypotheses. The system also provides gene and pathway annotation, citation retrieval, visualization, and writing refinement functions. In Alzheimer's disease case studies using three transcriptomic datasets, PAG-Agent consistently identified neurodegeneration-related pathways across multiple analysis methods and datasets. In citation-retrieval benchmarking, PAG-Agent outperformed six competing LLMs across five common literature-support scenarios, demonstrating improved ability to provide contextually relevant and valid references. Overall, PAG-Agent lowers technical barriers for pathway-level analysis and helps researchers move from transcriptomic data to biologically grounded interpretation, hypothesis generation, and scientific communication.