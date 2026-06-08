---
title: "PromptBio-Bench: Benchmarking LLM-based Bioinformatics Agents for End-to-End Data Analysis"
title_zh: PromptBio-Bench：用于端到端数据分析的基于LLM的生物信息学智能体基准测试
authors: "Guo, W., Zhang, M., Han, B., Ma, Y., Leng, Y., Hebbar, S., Zhou, X., Gu, W., Yang, X., Dhar, S."
date: 2026-06-01
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.05.723092v2.full.pdf"
tags: ["query:agent"]
score: 6.0
evidence: 基准测试基于LLM的生物信息学代理，对医学代理评估有启发
tldr: 大语言模型（LLM）在生物信息学自动化中展现潜力，但缺乏系统评估。我们提出PromptBio-Bench，包含244个专家构建的多难度任务和结构化文件比较框架。评估三个先进生物信息学agent发现准确率随难度增加显著下降。该基准为追踪agent生物信息学进展提供了基础设施。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有LLM agent在生物信息学工作流自动化能力缺乏系统评估，需要全面基准测试。
method: 构建244个专家策划任务和文件比较评分框架的评估套件。
result: 三个先进agent性能相当，但准确率随任务难度增加显著下降。
conclusion: PromptBio-Bench为系统追踪agent生物信息学进展提供了宝贵基准基础设施。
---

## 摘要
基于大型语言模型（LLM）的智能体在自动化生物信息学工作流程方面具有变革潜力；然而，对其能力的系统评估仍然有限，阻碍了对其实际应用准备情况的清晰评估。我们引入了PromptBio-Bench，这是一个包含244个专家精心策划的任务的综合评估套件，涵盖不同难度级别的生物信息学和数据科学，以及一个用于结构化文件比较和根据专家参考答案文件进行评分的评估框架。对三个最先进的生物信息学智能体的评估显示，Biomni和ToolsGenie性能相当，所有智能体在任务难度增加时准确率显著下降。随着基础模型和智能体框架的不断发展，PromptBio-Bench为系统跟踪智能体生物信息学的进展提供了宝贵的基准基础设施。

## Abstract
Large language model (LLM)-based agents hold transformative potential for automating bioinformatics workflows; however, systematic evaluations of their capabilities remain limited, hindering a clear assessment of their readiness for real-world application. We introduce PromptBio-Bench, a comprehensive evaluation suite of 244 expert-curated tasks spanning bioinformatics and data science at varied difficulty levels, and an evaluation framework for structured file comparison and scoring against expert reference answer files. Evaluation of three state-of-the-art bioinformatics agents revealed comparable performance between Biomni and ToolsGenie, with all agents showing a marked decline in accuracy as task difficulty increased. As foundation models and agent frameworks continue to evolve, PromptBio-Bench provides a valuable benchmark infrastructure for systematically tracking progress in agentic bioinformatics.