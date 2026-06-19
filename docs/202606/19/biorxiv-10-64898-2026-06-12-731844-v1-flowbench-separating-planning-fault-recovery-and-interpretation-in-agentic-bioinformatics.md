---
title: "FlowBench: separating planning, fault recovery and interpretation in agentic bioinformatics"
title_zh: "FlowBench: 在自主智能生物信息学中分离规划、故障恢复与解释"
authors: "Kurjan, A., Cribbs, A. P."
date: 2026-06-16
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.12.731844v1.full.pdf"
tags: ["query:agent"]
score: 6.0
evidence: 生物信息学代理基准和模块化框架，可迁移到医学AI代理
tldr: 生物信息学中代理LLM系统的评估通常依赖单一指标，混淆了规划、故障恢复和解释等独立能力。FlowBench将性能分解为四个维度，并通过模块化框架FlowAgent对23个模型进行消融分析。结果显示，生成有效工作流规划基本解决，但从生物意图推断工具链极为困难；故障恢复和数据驱动的解释能力严重不足；结构依赖的规划和完整性反思步骤提升性能，而验证重试反而降低质量。安全不随能力自然涌现，规划饱和后，代理架构和拒绝校准比模型规模更具改进潜力。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有代理系统评估混淆了独立能力，需分离规划、故障恢复和解释进行细粒度分析。
method: 提出FlowBench分解性能维度，构建FlowAgent模块化框架，对23个模型进行消融和跨提供者评估。
result: 规划完整度高但工具链推断骤难；故障恢复和解释滞后；结构规划和反思步骤有效，验证重试有害。
conclusion: 一旦规划饱和，改进重点应从模型规模转向代理架构和拒绝校准。
---

## 摘要
AO_SCPLOWBSTRACTC_SCPLOW自主智能大语言模型系统在生物信息学中的应用速度已超过对其的理解，而单一指标的评估会混淆那些独立失效的能力。我们引入了FlowBench，这是一个将自主智能生物信息学性能分解为规划、故障恢复、生物学解释以及端到端输出保真度的基准测试。现有系统实现了较高的规划完整性，但其封闭的、单一提供者的设计使得性能无法归因于脚手架还是底层模型。因此，我们构建了FlowAgent，一个模块化、与提供者无关的框架，其组件可选择性地禁用，其骨干模型可在共享测试平台上跨提供者交换，并利用它评估了来自三个主要提供者的23个模型。发现了三个结果。首先，从命名工具链生成有效的工作流规划基本已解决，而仅从生物学意图推断适当的工具链无论模型层级如何都普遍困难，将所有模型压缩在狭窄的44%-57%通过率区间内。其次，消融实验表明，依赖结构化的规划和完整性反思步骤推动了性能，而添加同上下文验证器驱动的重试反而使结构质量变差。第三，故障恢复和基于数据的解释仍未解决。模型经常提出强制干净退出但底层数据无效的修复方案，而基于数据的解释始终落后于内部知识回忆。安全性并非源于能力，推理层级的模型在识别不可恢复故障方面是最不可靠的之一。一旦规划饱和，富有成效的前沿是自主智能架构和拒绝校准，而非模型规模。

可用性与实现FlowAgent和FlowBench在GPLv3许可下可通过https://github.com/EnteloBio/flowagent获取

联系方式adam@entelo.bio

## Abstract
AO_SCPLOWBSTRACTC_SCPLOWAgentic large language model (LLM) systems are being deployed in bioinformatics faster than they are understood, and single-metric evaluations conflate capabilities that fail independently. We introduce FlowBench, a benchmark that decomposes agentic bioinformatics performance into planning, fault recovery, biological interpretation, and end-to-end output-fidelity. Existing systems achieve high plan completeness, but their closed, single-provider designs prevent attribution of performance to scaffolding versus the underlying model. We therefore built FlowAgent, a modular, provider-agnostic framework whose components can be selectively disabled and whose backbone model can be swapped across providers on a shared harness, and used it to evaluate 23 models from three main providers. Three findings emerge. First, generating a valid workflow plan from a named toolchain is largely solved, whereas inferring an appropriate toolchain from biological intent alone is uniformly difficult regardless of model tier, compressing all models into a narrow 44-57% pass-rate band. Second, ablation shows that the dependency-structured plan and a completeness-reflection step drive performance, while adding a same-context validator-driven retry makes structural quality worse. Third, fault recovery and data-grounded interpretation remain unsolved. Models frequently propose fixes that force a clean exit while leaving the underlying data invalid, and data-grounded interpretation lags internal-knowledge recall by a consistent margin. Safety does not emerge from capability, and reasoning-tier models were among the least reliable at recognising unrecoverable faults. Once planning saturates, agent architecture and refusal calibration, not model scale, are the productive frontier.

Availability and implementationFlowAgent and FlowBench are available under a GPLv3 licence at https://github.com/EnteloBio/flowagent

Contactadam@entelo.bio