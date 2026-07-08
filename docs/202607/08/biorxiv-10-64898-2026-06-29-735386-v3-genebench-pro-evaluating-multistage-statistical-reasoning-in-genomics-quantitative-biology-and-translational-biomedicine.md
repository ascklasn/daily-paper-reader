---
title: "GeneBench-Pro: Evaluating Multistage Statistical Reasoning in Genomics, Quantitative Biology, and Translational Biomedicine"
title_zh: GeneBench-Pro：评估基因组学、定量生物学和转化生物医学中的多阶段统计推理
authors: "Li, J. H., Ho, A. J."
date: 2026-07-02
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.29.735386v3.full.pdf"
tags: ["query:agent"]
score: 7.0
evidence: 评估AI agent在基因组学和生物医学中的多阶段科学分析能力
tldr: "现有基准难以评估AI在复杂科学问题中的多步推理能力。GeneBench-Pro扩展了此前基准，包含129个需跨10个主要领域和21个子领域进行多阶段决策的真实问题，覆盖基因组学、定量生物学和转化生物医学。最强模型GPT-5.6 Sol Pro通过率仅31.5%，其他模型更低；模型常能识别局部诊断信号但无法将影响传导至后续分析决策。该基准衡量了长期生物学推理的新兴能力，揭示了当前AI在联动决策上的显著不足。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有基准缺乏对多阶段统计推理的评估，GeneBench-Pro填补空白，模拟现实生命科学家面对复杂分析时的决策过程。
method: 构建129个跨10个主要领域和21个子领域的难题，每个问题需模型自主导航多个依赖决策点，识别并执行正确分析工作流。
result: "GPT-5.6 Sol Pro通过率31.5%，GPT-5.0及以下模型均低于16%，模型常完成部分流程但无法正确选择估计量或路径。"
conclusion: GeneBench-Pro揭示了AI在长期生物学推理中仍不可靠，存在“注意到但未行动”的鸿沟，是评估未来模型能力的重要基准。
---

## 摘要
我们推出了GeneBench-Pro，这是GeneBench的扩展和改进版本，包含跨更广泛领域的更难问题。GeneBench-Pro是一个基准，用于评估AI代理在基因组学、定量生物学和转化生物医学中执行现实多阶段科学分析的能力，旨在捕捉计算生命科学家在需要得出下游科学或转化决策所依赖的结论时所面临的实际问题的复杂性。该基准包含129个评估，针对10个主要领域和21个终端子领域中具有直接实际相关性的数量，以基因组学为核心。与GeneBench类似，每个问题为代理提供简要背景、目标估计量以及极少的其他指导；然后代理必须导航多个依赖决策点，即实质性的推断分支，在这些分支中，一个看似合理的错误选择会改变下游分析，从而识别并执行正确的分析工作流，得出正确答案。相对于GeneBench，GeneBench-Pro新增了29个问题，删除了3个，并对剩余100个重叠问题中的54个进行了显著重新设计。129个问题中的82个由外部领域专家审查，他们的发现导致了对那些目标不够明确的问题的提示/数据修改和重新设计。十个经过外部审查的问题公开发布，50个保留问题提供给Artificial Analysis进行独立的第三方模型基准测试，其余问题作为内部保留。在对全部129个问题的评估中，GPT-5.6 Sol在最大推理级别达到28.7%的评估级通过率，而在单独报告的GPT Pro运行中，GPT-5.6 Sol Pro达到31.5%。GPT-5.5达到12.0%，GPT-5.4达到8.9%，最强的非GPT基线Claude Opus 4.8达到16.0%。与GeneBench一样，模型通常能完成工作流的很大一部分，但在注意到局部诊断信号后，未能将其影响传播到相应的分析决策中，表现出注意与行动之间的一致差距。因此，模型常常选择错误的估计量，或者在最初看似合理但错误的分析路径上持续下去。因此，GeneBench-Pro衡量了一种尚不可靠的新兴能力：长时程生物学推理。

## Abstract
We introduce GeneBench-Pro, an expanded and improved version of GeneBench that comprises harder problems across a wider breadth of domains. GeneBench-Pro is a benchmark for AI agents performing realistic multi-stage scientific analyses in genomics, quantitative biology, and translational biomedicine which seeks to capture the complexity of real-world problems that computational life scientists face when tasked with producing a conclusion upon which a downstream scientific or translational decision is contingent. The benchmark comprises 129 evaluations targeting quantities of direct practical relevance across 10 primary domains and 21 terminal subdomains, with a genomics-centered core. Similarly to GeneBench, each problem provides the agent with brief context, a target estimand, and minimal guidance otherwise; the agent must then navigate multiple dependent decision points; i.e., substantive inferential forks where a plausible wrong choice changes the downstream analysis, to identify and execute the correct analysis workflow and arrive at the correct answer. Relative to GeneBench, GeneBench-Pro adds 29 new problems, drops three, and introduces significantly redesigned versions of 54 of the remaining 100 overlapping problems. 82 of the 129 problems were reviewed by external domain experts, whose findings led to prompt/data modifications and redesign of those problems whose targets were not sufficiently identifiable. Ten externally reviewed problems are released publicly, 50 held-out problems were provided to Artificial Analysis for independent third-party model benchmarking, and the remainder are retained as an internal holdout. In evaluations over the full 129-problem suite, GPT-5.6 Sol reaches an eval-level pass rate of 28.7% at the max reasoning level, and GPT-5.6 Sol Pro reaches 31.5% in separately reported GPT Pro runs. GPT-5.5 reaches 12.0%, GPT-5.4 reaches 8.9%, and the strongest non-GPT baseline, Claude Opus 4.8, reaches 16.0%. As with GeneBench, models often complete substantial portions of the workflow but exhibit a consistent gap between noticing and acting by identifying local diagnostic signals but failing to propagate the implications to the corresponding analysis decision. As a result, models often select wrong estimators or persist on initially plausible but incorrect analysis paths. GeneBench-Pro therefore measures an emerging capability of long-horizon biological reasoning that remains unreliable.



O_FIG O_LINKSMALLFIG WIDTH=200 HEIGHT=46 SRC="FIGDIR/small/735386v2_ufig1.gif" ALT="Figure 1">
View larger version (13K):
org.highwire.dtl.DTLVardef@1abbf01org.highwire.dtl.DTLVardef@88edf9org.highwire.dtl.DTLVardef@1bf8e4dorg.highwire.dtl.DTLVardef@1177183_HPS_FORMAT_FIGEXP  M_FIG C_FIG