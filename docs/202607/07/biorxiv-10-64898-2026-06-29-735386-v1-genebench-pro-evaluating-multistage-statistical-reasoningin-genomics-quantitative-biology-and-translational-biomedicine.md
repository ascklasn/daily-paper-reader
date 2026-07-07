---
title: "GeneBench-Pro: Evaluating Multistage Statistical Reasoning\\\\in Genomics, Quantitative Biology, and Translational Biomedicine"
title_zh: "GeneBench-Pro: 在基因组学、定量生物学和转化生物医学中评估多阶段统计推理"
authors: "Li, J. H., Ho, A. J."
date: 2026-06-30
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.29.735386v1.full.pdf"
tags: ["query:agent"]
score: 6.0
evidence: 基因组学与转化生物医学中AI智能体的多阶段推理评估基准
tldr: "GeneBench-Pro是一个评估AI智能体在基因组学、定量生物学和转化生物医学中进行多阶段统计推理的基准。包含129个问题，覆盖10个主要领域，相比GeneBench新增29个问题并大幅修改54个。评估显示GPT-5.6 Sol通过率28.7%，Claude Opus 4.8为16.0%。模型常能完成大部分工作流但在关键决策点失误，表现出识别与行动之间的差距。该基准用于衡量长时间跨度生物推理的新兴能力。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有基准无法捕捉真实世界中多步骤科学分析的复杂性，需构建更难、更广的评估以测试AI在关键推理环节的可靠性。
method: 构建129个问题，覆盖10个领域21个子域，每个问题提供简短背景和目标量，要求模型自主导航多个依赖决策点完成正确分析工作流。
result: "GPT-5.6 Sol达到28.7%通过率，最强非GPT模型Claude Opus 4.8为16.0%，模型常识别局部信号但未能将影响传导至分析决策。"
conclusion: GeneBench-Pro揭示了当前AI在长时间生物推理中的不可靠性，为衡量和推动该新兴能力的发展提供了标准基准。
---

## 摘要
我们推出了GeneBench-Pro，这是GeneBench的扩展和改进版本，涵盖了更广泛领域中更困难的问题。GeneBench-Pro是一个针对人工智能代理在基因组学、定量生物学和转化生物医学中进行现实多阶段科学分析的基准测试，旨在捕捉计算生命科学家在需要得出下游科学或转化决策所依赖的结论时所面临的现实问题的复杂性。该基准测试包含129个评估，针对10个主要领域和21个终端子领域中直接实际相关的量，以基因组学为核心。与GeneBench类似，每个问题为代理提供简要背景、目标估计量以及最少的其他指导；代理随后必须导航多个依赖决策点，即实质性的推断岔路口，在这些岔路口，一个看似合理的错误选择会改变下游分析，从而识别并执行正确的分析工作流程，得出正确答案。与GeneBench相比，GeneBench-Pro增加了29个新问题，删除了三个问题，并对剩余的100个重叠问题中的54个进行了显著重新设计。129个问题中有82个经过外部领域专家评审，其发现导致了提示/数据修改以及那些目标不够明确的问题的重新设计。十个经过外部评审的问题已公开发布，50个保留问题提供给Artificial Analysis进行独立的第三方模型基准测试，其余问题作为内部保留集。在对全部129个问题套件的评估中，GPT-5.6 Sol在最大推理级别上的评估级通过率达到28.7%，而在单独报告的GPT Pro运行中，GPT-5.6 Sol Pro达到31.5%。GPT-5.5达到12.0%，GPT-5.4达到8.9%，最强的非GPT基线Claude Opus 4.8达到16.0%。与GeneBench一样，模型通常完成工作流程的很大一部分，但通过识别局部诊断信号却未能将影响传播到相应的分析决策，从而在注意到和行动之间存在持续的差距。因此，模型常常选择错误的估计量，或者坚持最初看似合理但错误的分析路径。因此，GeneBench-Pro衡量的一种长期生物推理的新兴能力仍然不可靠。

## Abstract
We introduce GeneBench-Pro, an expanded and improved version of GeneBench that comprises harder problems across a wider breadth of domains. GeneBench-Pro is a benchmark for AI agents performing realistic multi-stage scientific analyses in genomics, quantitative biology, and translational biomedicine which seeks to capture the complexity of real-world problems that computational life scientists face when tasked with producing a conclusion upon which a downstream scientific or translational decision is contingent. The benchmark comprises 129 evaluations targeting quantities of direct practical relevance across 10 primary domains and 21 terminal subdomains, with a genomics-centered core. Similarly to GeneBench, each problem provides the agent with brief context, a target estimand, and minimal guidance otherwise; the agent must then navigate multiple dependent decision points; i.e., substantive inferential forks where a plausible wrong choice changes the downstream analysis, to identify and execute the correct analysis workflow and arrive at the correct answer. Relative to GeneBench, GeneBench-Pro adds 29 new problems, drops three, and introduces significantly redesigned versions of 54 of the remaining 100 overlapping problems. 82 of the 129 problems were reviewed by external domain experts, whose findings led to prompt/data modifications and redesign of those problems whose targets were not sufficiently identifiable. Ten externally reviewed problems are released publicly, 50 held-out problems were provided to Artificial Analysis for independent third-party model benchmarking, and the remainder are retained as an internal holdout. In evaluations over the full 129-problem suite, GPT-5.6 Sol reaches an eval-level pass rate of 28.7% at the max reasoning level, and GPT-5.6 Sol Pro reaches 31.5% in separately reported GPT Pro runs. GPT-5.5 reaches 12.0%, GPT-5.4 reaches 8.9%, and the strongest non-GPT baseline, Claude Opus 4.8, reaches 16.0%. As with GeneBench, models often complete substantial portions of the workflow but exhibit a consistent gap between noticing and acting by identifying local diagnostic signals but failing to propagate the implications to the corresponding analysis decision. As a result, models often select wrong estimators or persist on initially plausible but incorrect analysis paths. GeneBench-Pro therefore measures an emerging capability of long-horizon biological reasoning that remains unreliable.



O_FIG O_LINKSMALLFIG WIDTH=200 HEIGHT=46 SRC="FIGDIR/small/735386v2_ufig1.gif" ALT="Figure 1">
View larger version (13K):
org.highwire.dtl.DTLVardef@113198borg.highwire.dtl.DTLVardef@f2225corg.highwire.dtl.DTLVardef@ae01fforg.highwire.dtl.DTLVardef@52f92_HPS_FORMAT_FIGEXP  M_FIG C_FIG