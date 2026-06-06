---
title: "PromptBio-Bench: Benchmarking LLM-based Bioinformatics Agents for End-to-End Data Analysis"
title_zh: PromptBio-Bench：基于LLM的生物信息学智能体进行端到端数据分析的基准测试
authors: "Guo, W., Zhang, M., Han, B., Ma, Y., Leng, Y., Hebbar, S., Zhou, X., Gu, W., Yang, X., Dhar, S."
date: 2026-06-01
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.05.723092v2.full.pdf"
tags: ["query:agent"]
score: 8.0
evidence: 基于LLM的生物信息学Agent基准测试
tldr: 大型语言模型代理在自动化生物信息学分析中具有潜力，但缺乏系统评估。为此构建了PromptBio-Bench，包含244个专家策划的任务和标准化评估框架，覆盖不同难度。对三个先进代理的评估显示，Biomni与ToolsGenie性能相当，且所有代理的准确率随任务难度增加而显著下降。该基准为跟踪代理在生物信息学中的进展提供了基础设施。
source: biorxiv
selection_source: fresh_fetch
motivation: 缺乏对基于大语言模型的生物信息学代理在端到端数据分析中的系统评估，阻碍了对其实际应用能力的判断。
method: 创建包含244个专家任务和结构化文件比较评分框架的PromptBio-Bench评估套件，涵盖不同难度级别的生物信息学与数据科学任务。
result: Biomni和ToolsGenie表现相当，所有代理的准确率随任务难度增加而显著下降。
conclusion: PromptBio-Bench为系统性追踪代理生物信息学能力的进展提供了有价值的基准基础设施。
---

## 摘要
基于大型语言模型（LLM）的智能体在自动化生物信息学工作流程方面具有变革潜力；然而，对其能力的系统评估仍然有限，阻碍了对其实用性的清晰评估。我们推出了PromptBio-Bench，一个包含244个由专家精心策划的任务的综合评估套件，涵盖不同难度级别的生物信息学和数据科学领域，以及一个针对结构化文件比较和与专家参考答案文件评分的评估框架。对三个最先进的生物信息学智能体的评估显示，Biomni和ToolsGenie的表现相当，所有智能体的准确性随着任务难度增加而显著下降。随着基础模型和智能体框架的不断发展，PromptBio-Bench为系统追踪智能体生物信息学的进展提供了宝贵的基准基础设施。

## Abstract
Large language model (LLM)-based agents hold transformative potential for automating bioinformatics workflows; however, systematic evaluations of their capabilities remain limited, hindering a clear assessment of their readiness for real-world application. We introduce PromptBio-Bench, a comprehensive evaluation suite of 244 expert-curated tasks spanning bioinformatics and data science at varied difficulty levels, and an evaluation framework for structured file comparison and scoring against expert reference answer files. Evaluation of three state-of-the-art bioinformatics agents revealed comparable performance between Biomni and ToolsGenie, with all agents showing a marked decline in accuracy as task difficulty increased. As foundation models and agent frameworks continue to evolve, PromptBio-Bench provides a valuable benchmark infrastructure for systematically tracking progress in agentic bioinformatics.