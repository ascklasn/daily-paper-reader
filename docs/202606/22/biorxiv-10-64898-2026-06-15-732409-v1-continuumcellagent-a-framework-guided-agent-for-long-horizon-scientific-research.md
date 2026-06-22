---
title: "ContinuumCellAgent: A Framework-Guided Agent for Long-Horizon Scientific Research"
title_zh: ContinuumCellAgent：一个框架引导的面向长周期科学研究的智能体
authors: "Li, H., Lu, Y., Fang, K., Xu, Z., Li, F."
date: 2026-06-19
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.15.732409v1.full.pdf"
tags: ["query:agent"]
score: 7.0
evidence: 用于科学研究的自主智能体；框架引导的智能体架构
tldr: 现有AI科学家系统因缺乏模块化、提示系统化和长期行为可观察性而难以诊断。ContinuumCellAgent采用模块化超节点架构，支持阶段级后端替换；基于研究清单的协议同时定义审阅标准，确保提示接地；诊断层记录文件、消息和状态转换。在开放域QA和生物医学案例中，系统能生成可检查的研究工件并暴露管道动态，为可诊断的AI协同科学家研究提供框架。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有AI科学家系统缺乏模块化和可观察性，难以诊断和复现长期运行行为。
method: 提出模块化超节点架构，支持阶段级后端替换；协议基于研究清单同时定义审阅标准；诊断层记录工件、消息和状态转换。
result: 在开放域QA和生物医学/长寿案例中，系统生成可检查的研究工件并揭示管道动态。
conclusion: ContinuumCellAgent实现了可诊断、可检查的AI科学家框架，支持严格评估和后端替换。
---

## 摘要
AI科学家系统正开始自动化科学研究的某些部分。我们提出了CO_SCPLOWONTINUUMC_SCPLOWCO_SCPLOWELLC_SCPLOWAO_SCPLOWGENTC_SCPLOW，一个自主智能体，能够以单次无人值守运行的方式执行文献综述、假设形成、计算实验、手稿起草和对抗性同行评审。现有的AI科学家系统由于缺乏模块化、系统化的提示基础以及对长期行为的可观测性，仍然难以诊断。CO_SCPLOWONTINUUMC_SCPLOWCO_SCPLOWELLC_SCPLOWAO_SCPLOWGENTC_SCPLOW通过一种模块化的超级节点架构（用于分阶段后端替换）、基于精选研究方法清单（同时也定义了评审者评分标准）的协议，以及记录基于文件的人工制品、消息轨迹和状态转换的诊断层，弥补了这些不足。我们在开放域QA基准测试以及生物医学/长寿案例研究上评估了该系统，表明它能够生成可检查的研究人工制品，同时暴露流程动态，以支持严格的AI联合科学家研究。

## Abstract
AI-scientist systems are beginning to automate parts of scientific research. We present CO_SCPLOWONTINUUMC_SCPLOWCO_SCPLOWELLC_SCPLOWAO_SCPLOWGENTC_SCPLOW, an autonomous agent that executes literature review, hypothesis formation, computational experimentation, manuscript drafting, and adversarial peer review as a single unattended run. Existing AI scientist systems remain difficult to diagnose because they lack modularity, systematic prompt grounding, and observability into long-running behavior. CO_SCPLOWONTINUUMC_SCPLOWCO_SCPLOWELLC_SCPLOWAO_SCPLOWGENTC_SCPLOW addresses these gaps with a modular supernode architecture for stage-wise backend swapping, protocols grounded in curated research-method checklists that also define reviewer rubrics, and a diagnostics layer that records file-based artifacts, message traces, and state transitions. We evaluate the system on open-domain QA benchmarks and biomedical/longevity case studies, showing that it can produce checkable research artifacts while exposing pipeline dynamics for rigorous AI co-scientist research.