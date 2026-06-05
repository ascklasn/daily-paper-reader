---
title: "Open-Rosalind: Tool-First Biomedical LLM Agents with Process-Aware Benchmarking"
title_zh: "Open-Rosalind: 以工具为先的生物医学大语言模型智能体与过程感知基准测试"
authors: "Wang, L."
date: 2026-05-08
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.06.722404v1.full.pdf"
tags: ["query:agent"]
score: 8.0
evidence: 以工具优先的生物医学LLM智能体及过程感知基准
tldr: "针对通用大语言模型在生物医学研究中缺乏问责性的问题，提出工具优先的Open-Rosalind代理系统，遵循证据输出、轨迹完整、工作流约束及工具中介四项原则，并构建过程感知基准BioBench。内部测试中参考管道达81.4%准确率，去除工具后精度下降19-26个百分点。独立30任务测试初始仅17.8%，经诊断修复后提升至53.3%。强调了外部有效性审计的必要性，而非简单依赖协议约束。"
source: biorxiv
selection_source: fresh_fetch
motivation: 解决通用LLM代理灵活性与生物医学所需问责性之间的冲突，确保可审计性和可靠性。
method: 设计工具优先的四原则代理系统Open-Rosalind，并引入过程感知基准BioBench，同时评估任务准确率和工具正确性等过程指标。
result: "内部基准81.4%准确率，工具贡献最大；外部测试集从17.8%修复至53.3%，消除与无工具基线的负面比较。"
conclusion: Open-Rosalind作为带有外部有效性审计的生物医学代理研究，表明工具优先和约束工作流有效，但需谨慎部署和诊断。
---

## 摘要
大型语言模型越来越多地被用作科学智能体，但有利于通用智能体的灵活性可能与生物医学研究所要求的问责性相冲突。我们研究了是否可以将生物医学智能体组织在可审计的约束而非无约束的自主性周围。我们提出了Open-Rosalind，一个以工具为先的生物智能体系统，围绕四个操作原则设计：基于证据的输出、追踪完整性、工作流约束执行，以及对事实性主张的显式工具中介。为了评估这些原则，我们引入了Open-Rosalind BioBench，一个过程感知的基准测试，不仅衡量任务准确性，还衡量工具正确性、引用存在性、追踪完整性和失败率。

在严格的内部基准测试中，参考流水线实现了81.4%的准确性，并具有完整的执行追踪。在多模型消融和配对复制中，移除工具会使准确性降低19.3至26.4个百分点，表明以工具为先的执行是性能最强且最稳定的贡献因素。约束工作流还减少了在自由形式工具使用上薄弱的模型的下尾失败。

然而，一个作者独立的30任务留置集最初在部署模型上显示出严重的外部有效性崩溃。在诊断出五个路由和归一化失败并应用针对性修复后，留置准确性从17.8%提高到53.3%，并且最令人担忧的与无工具基线的负面对比消失了。这些结果将Open-Rosalind定位为一项具有显式外部有效性审计的生物医学智能体研究，而非声称仅协议约束就能保证卓越性能。

## Abstract
Large language models are increasingly used as scientific agents, yet the flexibility that benefits general-purpose agents can conflict with the accountability required in biomedical research. We study whether biomedical agents can be organized around auditable constraints rather than unconstrained autonomy. We present Open-Rosalind, a tool-first bio-agent system designed around four operational principles: evidence-grounded outputs, trace completeness, workflow-constrained execution, and explicit tool mediation for factual claims. To evaluate these principles, we introduce Open-Rosalind BioBench, a process-aware benchmark that measures not only task accuracy but also tool correctness, citation presence, trace completeness, and failure rate.

On a strict in-house benchmark, the reference pipeline achieves 81.4% accuracy with complete execution traces. In multi-model ablations and paired replications, removing tools reduces accuracy by 19.3 to 26.4 percentage points, indicating that tool-first execution is the strongest and most stable contributor to performance. Constrained workflows also reduce lower-tail failures for models that are weak at free-form tool use.

However, an author-independent 30-task hold-out initially revealed severe external-validity collapse on the deployment model. After diagnosing five routing and normalization failures and applying targeted fixes, hold-out accuracy improved from 17.8% to 53.3%, and the most concerning negative comparison against a no_tool baseline disappeared. These results position Open-Rosalind as a biomedical-agent study with an explicit external-validity audit, rather than as a claim that protocol constraints alone guarantee superior performance.