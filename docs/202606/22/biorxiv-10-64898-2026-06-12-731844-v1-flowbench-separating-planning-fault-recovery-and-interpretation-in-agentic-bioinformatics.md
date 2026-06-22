---
title: "FlowBench: separating planning, fault recovery and interpretation in agentic bioinformatics"
title_zh: FlowBench：在智能体生物信息学中分离规划、故障恢复与解释
authors: "Kurjan, A., Cribbs, A. P."
date: 2026-06-16
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.12.731844v1.full.pdf"
tags: ["query:agent"]
score: 7.0
evidence: 基于LLM的智能体生物信息学基准和模块化框架
tldr: "生物信息学中的智能体LLM系统评估存在单一指标模糊不同能力的问题。本文提出FlowBench基准，将性能分解为规划、故障恢复和生物解释三个维度，并构建模块化框架FlowAgent。评估23个模型发现：规划完成度虽高，但从意图推导工具链普遍困难（通过率44-57%）；故障恢复和基于数据的解释能力未解决，推理模型在识别不可恢复故障上反而更不可靠。研究揭示了架构设计和拒绝校准的重要性。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有评估混同了规划、故障恢复和解释等独立能力，阻碍了智能体系统在生物信息学中的有效改进。
method: 设计FlowBench分解任务为规划完整性、故障恢复与生物解释，构建FlowAgent框架支持组件消融和多模型对比评估。
result: "规划完成度高但工具链推断困难（44-57%）；依赖结构化规划和反思步骤提升性能，验证器重试反而降低质量；故障恢复与数据解释仍待解决，推理模型安全警觉不足。"
conclusion: 规划饱和后，智能体架构和拒绝校准比模型规模更关键，安全不随能力自然涌现。
---

## 摘要
AO_SCPLOWBSTRACTC_SCPLOW智能体大语言模型（LLM）系统在生物信息学中的部署速度超过了对其理解的速度，而单一指标的评估混淆了独立失效的能力。我们提出了FlowBench，一个将智能体生物信息学性能分解为规划、故障恢复、生物学解释以及端到端输出保真度的基准测试。现有系统实现了较高的计划完整性，但其封闭的、单一供应商的设计使得无法将性能归因于框架还是底层模型。因此，我们构建了FlowAgent，一个模块化的、与供应商无关的框架，其组件可以选择性地禁用，其骨干模型可以在共享平台上的不同供应商之间切换，并用于评估来自三个主要供应商的23个模型。三个发现如下：第一，从已命名的工具链生成有效的工作流计划基本已解决，而仅从生物学意图推断合适的工具链无论模型层级如何都很困难，将所有模型压缩在狭窄的44-57%通过率区间内。第二，消融实验表明，依赖结构的计划和完整性反思步骤驱动了性能，而添加相同上下文验证器驱动的重试会降低结构质量。第三，故障恢复和基于数据的解释仍未解决。模型经常提出强制干净退出但未解决底层数据无效的修复方案，并且基于数据的解释始终落后于内部知识回忆。安全性并非源于能力，推理层级的模型在识别不可恢复故障方面最不可靠。一旦规划饱和，智能体架构和拒绝校准（而非模型规模）成为生产前沿。

可用性与实现FlowAgent和FlowBench在GPLv3许可下可通过https://github.com/EnteloBio/flowagent获取

联系方式adam@entelo.bio

## Abstract
AO_SCPLOWBSTRACTC_SCPLOWAgentic large language model (LLM) systems are being deployed in bioinformatics faster than they are understood, and single-metric evaluations conflate capabilities that fail independently. We introduce FlowBench, a benchmark that decomposes agentic bioinformatics performance into planning, fault recovery, biological interpretation, and end-to-end output-fidelity. Existing systems achieve high plan completeness, but their closed, single-provider designs prevent attribution of performance to scaffolding versus the underlying model. We therefore built FlowAgent, a modular, provider-agnostic framework whose components can be selectively disabled and whose backbone model can be swapped across providers on a shared harness, and used it to evaluate 23 models from three main providers. Three findings emerge. First, generating a valid workflow plan from a named toolchain is largely solved, whereas inferring an appropriate toolchain from biological intent alone is uniformly difficult regardless of model tier, compressing all models into a narrow 44-57% pass-rate band. Second, ablation shows that the dependency-structured plan and a completeness-reflection step drive performance, while adding a same-context validator-driven retry makes structural quality worse. Third, fault recovery and data-grounded interpretation remain unsolved. Models frequently propose fixes that force a clean exit while leaving the underlying data invalid, and data-grounded interpretation lags internal-knowledge recall by a consistent margin. Safety does not emerge from capability, and reasoning-tier models were among the least reliable at recognising unrecoverable faults. Once planning saturates, agent architecture and refusal calibration, not model scale, are the productive frontier.

Availability and implementationFlowAgent and FlowBench are available under a GPLv3 licence at https://github.com/EnteloBio/flowagent

Contactadam@entelo.bio