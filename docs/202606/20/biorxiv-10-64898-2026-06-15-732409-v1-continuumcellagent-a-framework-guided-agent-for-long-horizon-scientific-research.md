---
title: "ContinuumCellAgent: A Framework-Guided Agent for Long-Horizon Scientific Research"
title_zh: ContinuumCellAgent：一个面向长周期科学研究的框架引导型智能体
authors: "Li, H., Lu, Y., Fang, K., Xu, Z., Li, F."
date: 2026-06-19
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.15.732409v1.full.pdf"
tags: ["query:agent"]
score: 8.0
evidence: 自主智能体框架用于科学研究，符合医学AI智能体和工作流自动化需求
tldr: 现有AI科学家系统缺乏模块化、提示系统化及长程行为可观测性。本文提出ContinuumCellAgent，采用模块化超节点架构实现阶段级后端替换，基于研究方法检查表协议驱动提示设计并定义审稿标准，配备诊断层记录文件、消息和状态。在开放域QA和生物医学案例上，系统可生成可核查的研究成果，同时为AI联合科学家研究提供流水线动态分析能力。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有AI科学家系统难以诊断，缺乏模块化、系统化提示基础和长程行为可观测性，限制了自动化科学研究的可靠性和可复现性。
method: 提出模块化超节点架构支持阶段级后端替换，使用研究方法检查表协议统一提示和审稿标准，并构建诊断层记录文件、消息和状态转换。
result: 在开放域QA基准和生物医学/长寿案例上验证，系统能生成可核查的研究成果，并暴露流水线动态，支持诊断和迭代。
conclusion: ContinuumCellAgent通过模块化框架和诊断层提升了AI科学家系统的可观测性和可诊断性，为长期自主科学研究提供了可行方案。
---

## 摘要
人工智能科学家系统正开始自动化科学研究的某些部分。我们提出了ContinuumCellAgent，一个自主智能体，能够作为单次无人值守运行执行文献综述、假设形成、计算实验、手稿起草和对抗性同行评审。现有的人工智能科学家系统由于缺乏模块化、系统的提示基础以及对长时间运行行为的可观测性，仍然难以诊断。ContinuumCellAgent通过模块化超节点架构（支持分阶段后端替换）、基于精选研究方法清单（同时也定义评审者评分标准）的协议，以及记录基于文件的人工产物、消息轨迹和状态转换的诊断层，解决了这些不足。我们在开放领域问答基准测试以及生物医学/长寿案例研究中评估了该系统，表明它能够产生可检验的研究人工产物，同时暴露流水线动态，以支持严谨的人工智能协同科学家研究。

## Abstract
AI-scientist systems are beginning to automate parts of scientific research. We present ContinuumCellAgent, an autonomous agent that executes literature review, hypothesis formation, computational experimentation, manuscript drafting, and adversarial peer review as a single unattended run. Existing AI scientist systems remain difficult to diagnose because they lack modularity, systematic prompt grounding, and observability into long-running behavior. ContinuumCellAgent addresses these gaps with a modular supernode architecture for stage-wise backend swapping, protocols grounded in curated research-method checklists that also define reviewer rubrics, and a diagnostics layer that records file-based artifacts, message traces, and state transitions. We evaluate the system on open-domain QA benchmarks and biomedical/longevity case studies, showing that it can produce checkable research artifacts while exposing pipeline dynamics for rigorous AI co-scientist research.