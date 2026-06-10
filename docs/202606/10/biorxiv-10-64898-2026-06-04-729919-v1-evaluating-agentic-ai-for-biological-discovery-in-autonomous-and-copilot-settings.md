---
title: Evaluating agentic AI for biological discovery in autonomous and copilot settings
title_zh: 在自主和副驾驶员模式下评估用于生物发现的智能体AI
authors: "Johri, S., Pimenta, E. M., Yates, J., Fu, J., Bao, E. L., Jun, H., Reardon, B., Bacot, S., Shady, M., Fu, D., Mei, W., Camp, S. Y., Park, J., Van Allen, E."
date: 2026-06-09
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.04.729919v1.full.pdf"
tags: ["query:agent"]
score: 8.0
evidence: 基于LLM的AI agent用于生物发现和多组学研究
tldr: LLM驱动的AI代理在生物发现中应用潜力巨大，但面临数据异构与开放推理等挑战。本文构建M3A框架，在多癌种单细胞多组学数据上评估自主与协同模式。发现当前代理擅长广泛系统探索，而领域专家在方法论指导和生物学综合中仍不可或缺。该工作划定了代理AI的当前边界，并提供了评估标准。
source: biorxiv
selection_source: fresh_fetch
motivation: 评估当前LLM代理在生物发现中自主与协同模式的能力与局限。
method: 基于11种癌症多组学单细胞数据，开发M3A框架测试细胞注释、假设生成等任务。
result: 代理擅长系统探索，但领域专家在方法引导和生物综合上仍关键。
conclusion: 本研究揭示了代理AI在计算生物学中的潜力与边界，并建立了评估框架。
---

## 摘要
基于大型语言模型的人工智能代理的进步提高了它们执行结构化分析工作流程的能力，包括用于生物发现的标准生物信息学流程。然而，计算生物学很少仅由确定性流程执行组成。生物数据集是异质且嘈杂的，有意义的发现通常需要开放式的假设生成和对多模态证据的迭代推理。这些挑战在多组学研究中尤为明显，其中配对的分子模式和异质性临床背景为发现提供了机遇和障碍。新兴的智能体AI系统能在多大程度上支持或自动化这种科学发现模式仍不清楚。在这里，我们使用涵盖11种癌症类型的多组学单细胞数据集，系统评估了智能体AI在生物发现中的能力与局限性。我们开发了多步骤多模态多组学智能体框架，以支持LLM驱动的对持久多模态数据状态的推理，并捕获自主和人机副驾驶模式下的智能体推理行为。利用该框架，我们评估了AI代理在互补任务上的表现，包括自主细胞类型注释、从基因程序生成可证伪的生物假设，以及测试人类参与和领域专业知识影响的副驾驶实验。我们发现，当前AI代理在对复杂数据进行广泛系统性探索方面是有效的，而领域专家在方法指导和跨分析的生物综合方面仍然至关重要。总之，我们的结果描绘了智能体AI在计算生物学中的当前潜力和边界，并建立了一个评估旨在支持生物发现的AI系统的框架。

## Abstract
Advances in large language models (LLMs)-based artificial intelligence (AI) agents have improved their ability to execute structured analytical workflows, including standard bioinformatic pipelines for biological discovery. However, computational biology rarely consists of deterministic pipeline execution alone. Biological datasets are heterogeneous and noisy, and meaningful discovery often requires open-ended hypothesis generation and iterative reasoning over multimodal evidence. These challenges are particularly evident in multi-omic studies, where paired molecular modalities and heterogeneous clinical contexts create both opportunities and obstacles for discovery. The extent to which emerging agentic AI systems can support or automate this mode of scientific discovery remains poorly understood. Here, we systematically evaluated the capabilities and limitations of agentic AI for biological discovery using multi-omic single cell datasets spanning 11 cancer types. We developed the Multistep Multimodal Multiomic Agentic (M3A) Framework to support LLM-driven reasoning over persistent multimodal data states and to capture agentic reasoning behavior in autonomous and human-AI copilot settings. Using this framework, we assessed AI agents across complementary tasks, including autonomous cell-type annotation, generation of falsifiable biological hypotheses from gene programs, and copilot experiments testing the effect of human involvement and domain expertise. We found that current AI agents are effective at broad, systemic exploration of complex data, whereas domain experts remain critical for methodological guidance and biological synthesis across analyses. Together, our results delineate the current potential and boundaries of agentic AI in computational biology, and establish a framework for evaluating AI systems designed to support biological discovery.