---
title: "PromptBio-Bench: Benchmarking LLM-based Bioinformatics Agents for End-to-End Data Analysis"
title_zh: PromptBio-Bench：基于大语言模型的生物信息学智能体在端到端数据分析中的基准测试
authors: "Guo, W., Zhang, M., Han, B., Ma, Y., Leng, Y., Hebbar, S., Zhou, X., Gu, W., Yang, X., Dhar, S."
date: 2026-06-01
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.05.723092v2.full.pdf"
tags: ["query:agent"]
score: 7.0
evidence: 对基于LLM的生物信息学代理进行端到端数据分析基准测试
tldr: 当前缺乏对基于大语言模型的生物信息学代理在端到端数据分析中的系统性评估。为此提出了PromptBio-Bench基准，包含244个专家策划的任务，覆盖不同难度，并设计了结构化文件比较与评分框架。评估三个现有代理后发现，Biomni和ToolsGenie性能相当，但所有代理的准确率均随任务难度增加而显著下降。该基准为追踪代理型生物信息学进展提供了标准基础设施。
source: biorxiv
selection_source: fresh_fetch
motivation: 缺乏对LLM驱动的生物信息学代理在真实数据分析中的系统评估，阻碍了对其实际应用潜力的判断。
method: 构建244个专家策划任务并设计结构化文件比较与评分框架，以标准化评估代理性能。
result: 三个代理中，Biomni与ToolsGenie性能相当，但所有代理的准确率随任务难度增加显著下降。
conclusion: PromptBio-Bench为评估代理型生物信息学进展提供了标准化的基准基础设施。
---

## 摘要
基于大语言模型（LLM）的智能体在自动化生物信息学工作流程方面具有变革潜力；然而，对其能力的系统性评估仍然有限，阻碍了对它们在实际应用中准备情况的清晰评估。我们推出了PromptBio-Bench，这是一个包含244个专家策划任务的综合评估套件，涵盖不同难度的生物信息学和数据科学任务，并提供了一个针对结构化文件比较和与专家参考答案文件评分的评估框架。对三种最先进的生物信息学智能体的评估显示，Biomni和ToolsGenie的表现相当，所有智能体在任务难度增加时准确率显著下降。随着基础模型和智能体框架的不断发展，PromptBio-Bench为系统追踪智能体生物信息学进展提供了宝贵的基准基础设施。

## Abstract
Large language model (LLM)-based agents hold transformative potential for automating bioinformatics workflows; however, systematic evaluations of their capabilities remain limited, hindering a clear assessment of their readiness for real-world application. We introduce PromptBio-Bench, a comprehensive evaluation suite of 244 expert-curated tasks spanning bioinformatics and data science at varied difficulty levels, and an evaluation framework for structured file comparison and scoring against expert reference answer files. Evaluation of three state-of-the-art bioinformatics agents revealed comparable performance between Biomni and ToolsGenie, with all agents showing a marked decline in accuracy as task difficulty increased. As foundation models and agent frameworks continue to evolve, PromptBio-Bench provides a valuable benchmark infrastructure for systematically tracking progress in agentic bioinformatics.