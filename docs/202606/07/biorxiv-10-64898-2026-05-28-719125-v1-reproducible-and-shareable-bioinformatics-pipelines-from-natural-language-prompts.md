---
title: Reproducible and shareable bioinformatics pipelines from natural-language prompts
title_zh: 基于自然语言提示的可重复且可共享的生物信息学流程
authors: "Kim, H.-M., Jeong, H., Mekonnen, A. M., Kim, Y., Oh, Y., Lee, H., Jung, C., Park, J."
date: 2026-06-01
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.28.719125v1.full.pdf"
tags: ["query:agent"]
score: 8.0
evidence: 基于LLM的可复现生物信息学流程平台
tldr: 大型语言模型可生成生物信息学流水线，但结果难以重现且无法远程共享。Autopipe平台通过MCP协议引导LLM生成容器化流水线，自动执行并支持远程HPC部署。用户可发布、共享流水线，并通过Web查看器可视化结果。该工具将对话式分析转化为可重现、可共享的工作流，降低了使用门槛。
source: biorxiv
selection_source: fresh_fetch
motivation: 解决LLM生成生物信息学流水线时结果难以重现和无法在远程HPC上共享的问题。
method: Autopipe包含桌面应用（内嵌MCP服务器）、在线注册表、Web结果查看器和CLI工具，通过MCP引导LLM生成并执行容器化流水线。
result: 用户可从自然语言提示生成可重现的流水线，并在本地或远程HPC上执行，结果通过可视化界面查看。
conclusion: Autopipe将对话式分析转化为可重现和可共享的工作流，提升了生物信息学分析的复用性和可访问性。
---

## 摘要
大型语言模型正越来越多地被用于从自然语言提示生成生物信息学流程并进行分析。然而，由于LLM驱动对话的非确定性和本地执行环境的异质性，生成的分析往往难以在不同会话间重现，无法在远程高性能计算服务器上运行，也难以共享和复用。我们提出了Autopipe，这是一个引导任何兼容模型上下文协议的LLM来生成、执行和发布保留源代码、可重新执行的容器化流程的平台。Autopipe使用户能够在任何本地远程服务器上执行生物信息学流程——附有全面的设置文档，面向没有服务器管理经验的研究人员——并通过可扩展的基于Web的查看器可视化结果。Autopipe平台包含四个组件：一个带有嵌入式MCP服务器的桌面应用程序，用于流程管理和远程执行；一个用于流程和插件发现的在线注册表；一个基于Web的结果查看器；以及一个用于自定义查看器插件的CLI工具。Autopipe将对话式分析转化为可重新执行和可共享的工作流程。Autopipe在https://autopipe.org/上免费提供。

## Abstract
Large language models (LLMs) are increasingly used to generate bioinformatics pipelines and to carry out analyses from natural-language prompts. However, the resulting analyses are often difficult to reproduce across sessions, owing to the non-deterministic nature of LLM-driven conversations and heterogeneity of local execution environments, and cannot run on remote high-performance computing (HPC) servers or be shared and reused. We present Autopipe, a platform that guides any Model Context Protocol (MCP) - compatible LLM to produce, execute, and publish source-preserved, re-executable containerized pipelines. Autopipe enables users to execute bioinformatics pipelines on any on-premises remote servers - supported by comprehensive setup documentation aimed at researchers without prior server-administration experience - and to visualize results through an extensible web-based viewer. The Autopipe platform comprises four components: a desktop application with an embedded MCP server for pipeline management and remote execution, an online registry for pipeline and plugin discovery, a web-based result viewer, and a CLI tool for customizing viewer plugins. Autopipe turns conversational analysis into re-executable and shareable workflows. Autopipe is freely available at https://autopipe.org/.