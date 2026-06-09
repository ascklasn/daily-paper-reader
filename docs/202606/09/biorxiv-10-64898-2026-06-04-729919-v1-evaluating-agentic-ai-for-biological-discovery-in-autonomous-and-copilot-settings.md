---
title: Evaluating agentic AI for biological discovery in autonomous and copilot settings
title_zh: 评估自主和协作者模式下用于生物学发现的智能体AI
authors: "Johri, S., Pimenta, E. M., Yates, J., Fu, J., Bao, E. L., Jun, H., Reardon, B., Bacot, S., Shady, M., Fu, D., Mei, W., Camp, S. Y., Park, J., Van Allen, E."
date: 2026-06-09
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.04.729919v1.full.pdf"
tags: ["query:agent"]
score: 8.0
evidence: 评估AI agent在生物发现中自主和协作模式的表现
tldr: 当前AI代理在结构化生物信息分析中表现良好，但面对多组学单细胞数据的开放推理与假说生成能力不足。本文提出M3A框架，在11种癌症类型中系统评估自主和协同模式下的AI代理发现能力。结果显示AI善于广泛数据探索，而人类专家在方法指导与生物学综合中不可或缺。研究为评估支持生物发现的AI系统建立了框架。
source: biorxiv
selection_source: fresh_fetch
motivation: 探索LLM驱动的AI代理在自主与协同模式下支持多组学生物发现的能力边界。
method: 开发M3A框架，基于11种癌症类型多组学单细胞数据，评估自主与协同模式下细胞注释、假说生成等任务。
result: AI代理擅长广泛数据探索与系统分析，而领域专家在方法选择和生物学综合方面仍不可或缺。
conclusion: 划定了当前AI代理在计算生物学中的潜力与局限，提供评估框架以指导未来自主科学发现研究。
---

## 摘要
基于大语言模型（LLMs）的人工智能（AI）智能体在执行结构化分析工作流（包括用于生物学发现的标准生物信息学管线）方面的能力有所提升。然而，计算生物学很少仅由确定性管线执行组成。生物数据集是异质且嘈杂的，有意义的发现通常需要开放式的假设生成和对多模态证据的迭代推理。这些挑战在多组学研究中尤为明显，其中配对的分子模态和异质的临床背景为发现既带来机遇也带来障碍。新兴的智能体AI系统在多大程度上能够支持或自动化这种科学发现模式仍然知之甚少。在这里，我们使用涵盖11种癌症类型的多组学单细胞数据集，系统地评估了智能体AI在生物学发现中的能力和局限性。我们开发了多步骤多模态多组学智能体（M3A）框架，以支持LLM驱动的对持久多模态数据状态的推理，并捕获自主和人机协作者模式下的智能体推理行为。利用该框架，我们评估了AI智能体在互补任务上的表现，包括自主细胞类型注释、从基因程序中生成可证伪的生物学假设，以及测试人类参与和领域专业知识影响的协作者实验。我们发现，当前的AI智能体在广泛、系统性地探索复杂数据方面是有效的，而领域专家在方法学指导和跨分析生物学综合方面仍然至关重要。我们的结果共同描绘了智能体AI在计算生物学中的当前潜力和边界，并建立了一个用于评估旨在支持生物学发现的AI系统的框架。

## Abstract
Advances in large language models (LLMs)-based artificial intelligence (AI) agents have improved their ability to execute structured analytical workflows, including standard bioinformatic pipelines for biological discovery. However, computational biology rarely consists of deterministic pipeline execution alone. Biological datasets are heterogeneous and noisy, and meaningful discovery often requires open-ended hypothesis generation and iterative reasoning over multimodal evidence. These challenges are particularly evident in multi-omic studies, where paired molecular modalities and heterogeneous clinical contexts create both opportunities and obstacles for discovery. The extent to which emerging agentic AI systems can support or automate this mode of scientific discovery remains poorly understood. Here, we systematically evaluated the capabilities and limitations of agentic AI for biological discovery using multi-omic single cell datasets spanning 11 cancer types. We developed the Multistep Multimodal Multiomic Agentic (M3A) Framework to support LLM-driven reasoning over persistent multimodal data states and to capture agentic reasoning behavior in autonomous and human-AI copilot settings. Using this framework, we assessed AI agents across complementary tasks, including autonomous cell-type annotation, generation of falsifiable biological hypotheses from gene programs, and copilot experiments testing the effect of human involvement and domain expertise. We found that current AI agents are effective at broad, systemic exploration of complex data, whereas domain experts remain critical for methodological guidance and biological synthesis across analyses. Together, our results delineate the current potential and boundaries of agentic AI in computational biology, and establish a framework for evaluating AI systems designed to support biological discovery.