---
title: Client-server interfaces enable efficient agent-driven variant calling
title_zh: 客户端-服务器接口实现高效的智能体驱动变异检测
authors: "Yu, X., Zheng, Z., CHEN, L., QIn, Z., Guo, X., He, M., Luo, R."
date: 2026-06-28
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.25.734665v1.full.pdf"
tags: ["query:agent"]
score: 8.0
evidence: LLM agent驱动的变异检测，通过客户端-服务器接口设计实现可靠的生物信息学分析
tldr: "LLM代理在驱动生物信息学工具时，因工具未针对代理设计而效率低下。本研究将Clair3重构为客户端-服务器系统Clair3-Connect，客户端处理基因组数据并持有标识信息，服务器仅运行神经网络推理，通过schema定义的代理工具接受单次结构化调用。在APOE二倍体分型任务中，所有运行均正确，token消耗比Shell驱动基线减少6.8-14倍，运行时间约四分之一，且更稳定（变异4% vs 35%）。结果表明，为算法设计代理界面应作为生物信息学开发的一等产出。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有生物信息学工具未考虑LLM代理调用，导致多轮交互与高资源消耗。
method: 将Clair3重构为客户端-服务器系统，客户端处理基因数据，服务器仅推理，暴露schema定义的代理工具。
result: "APOE任务中全正确，token消耗降低6.8-14倍，时间缩短约75%，稳定性提升。"
conclusion: 为算法设计代理界面可提升效率与可靠性，应作为工具开发的一等产出。
---

## 摘要
背景：大型语言模型（LLM）智能体越来越多地自动化生物信息学分析，但大多数现有生物信息学工具是为人类专家独立使用而构建的。驱动此类工具的智能体必须从面向人类的文档中推理其安装、配置和执行，每次结果需要多次交互、大量令牌和工具调用。因此，方法如何暴露给智能体可能与方法本身同等重要。通过为这些工具设计智能体接口，智能体可以减少此类开销并提高智能体驱动分析的可靠性。

发现：为测试这一设计，我们将广泛使用的基于深度学习的长读长变异检测工具Clair3重新架构为客户端-服务器系统Clair3-Connect。客户端执行所有基因组学相关处理并持有可识别数据。服务器仅运行神经网络推理，客户端仅将特征张量发送给服务器，而样本标识符和基因组上下文保留在客户端。客户端暴露由模式定义的面向智能体的工具，智能体通过单个结构化调用调用这些工具。在APOE单倍型分型任务中，所有60次智能体运行均正确。智能体工具在3次交互中使用了12K个令牌，比基于shell的基线（81K-163K个令牌）令牌数量减少6.8至14倍，实际运行时间约为四分之一，且稳定性更高（令牌使用变化率为4%对35%）。为保持客户端轻量化，去除了pileup和分阶段处理，在50倍覆盖度下，SNP F1值仅比标准Clair3低0.1-0.3分，而相互TLS和AES-256-GCM加密使端到端运行时间增加了7.2%。

结论：将成熟算法重构为开发者构建的、位于安全客户端-服务器边界之后的智能体工具，使其比第三方封装器更高效、可靠且易于LLM智能体部署，因为第三方封装器无法恢复仅有其开发者知晓的默认设置和约定。智能体接口应成为生物信息学工具开发的一等交付物。

## Abstract
BackgroundLarge language model (LLM) agents increasingly automate bioinformatics analyses, but most existing bioinformatics tools were built for standalone use by human experts. An agent driving such a tool must reason about its installation, configuration, and execution from documentation for human, spending many turns, tokens, and tool calls per result. How a method is exposed to an agent can therefore matter as much as the method itself. By designing agentic interfaces for these tools, agent can reduce such overhead and improve the reliability of agent-driven analyses.

FindingsTo test this design, we re-architected Clair3, a widely used deep-learning-based long-read variant caller, into a client-server system, Clair3-Connect. The client performs all genomics related processing and holds the identifiable data. The server runs only neural-network inference, and the client sends only feature tensors to the server, while sample identifiers and genomic context remain on the client. The client exposes schema-defined agent-facing tools that an agent invokes through single structured calls. On an APOE diplotyping task, all 60 agent runs were correct. The agentic tools used 12K tokens in 3 turns, 6.8 to 14 times fewer tokens than the shell-driven baselines (81K-163K tokens), at about a quarter the wall-clock time and far more stably (4% versus 35% token usage variation). Dropping the pileup and phasing stages to keep the client light left SNP F1 within 0.1-0.3 points of standard Clair3 by 50x coverage, while mutual TLS and AES-256-GCM encryption added 7.2% to end-to-end runtime.

ConclusionsRecasting an established algorithm as developer-built, agentic tools behind a secure client-server boundary makes it more efficient, reliable, and easier to deploy for an LLM agent than a third-party wrapper, which cannot recover the defaults and conventions only its developers know. Agentic interfaces should be a first-class deliverable of bioinformatics tool development.