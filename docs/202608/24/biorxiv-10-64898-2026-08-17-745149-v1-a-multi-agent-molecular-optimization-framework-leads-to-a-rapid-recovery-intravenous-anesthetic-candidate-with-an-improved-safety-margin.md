---
title: A multi-agent molecular optimization framework leads to a rapid-recovery intravenous anesthetic candidate with an improved safety margin
authors: "Xue, Z., Liu, X."
date: 2026-08-20
pdf: "https://www.biorxiv.org/content/10.64898/2026.08.17.745149v1.full.pdf"
tags: ["query:agent"]
score: 6.0
evidence: 面向药物发现的角色专用多智能体分子优化框架
tldr: 药物先导物优化需在巨大化学空间内平衡效能、药代与安全性。MASCOT提出角色专业化的多智能体框架，协同权衡智能体、策略智能体和反思智能体，并在化学约束的图编辑搜索中推进候选分子优化。该方法开发出恢复更快且安全窗改善的静脉麻醉候选药物，展示了多智能体协作在药物发现中的潜力。
source: biorxiv
selection_source: fresh_fetch
motivation: 面向药物发现的角色专用多智能体分子优化框架。
method: 方法与实现细节请参考摘要与正文。
result: 结果与对比结论请参考摘要与正文。
conclusion: 总体而言，该工作在所述任务上展示了有效性，并提供了可复用的思路或工具。
---

## Abstract
Lead optimization, the systematic refinement of therapeutic compounds through iterative structural modification, faces a dual challenge in modern drug discovery: navigating astronomically vast molecular design spaces while balancing conflicting demands on potency, pharmacokinetics, and safety. We present MASCOT (Multi-Agent SearCh for molecular OpTimization), a role-specialized multi-agent framework for molecular optimization. Integrated with a chemically constrained graph-editing search, MASCOT coordinates three specialized agents: a trade-off agent that reprioritizes competing objectives, a strategy agent that adapts how molecular edits are proposed, and a reflection agent that distills lessons from previous decisions. Computational experiments showed that MASCOT achieved the best performance over competing methods on six benchmark settings. On the SARS-CoV-2 main protease task, its mean docking-score improvement was 3.6 times that of the strongest baseline. Applied to the clinically used anesthetic remimazolam (RM), MASCOT prioritized RM-1, which showed a shorter liver microsomal half-life, higher brain exposure, and a larger therapeutic index than RM. Subsequent derivative design yielded RM-7. Extensive animal studies established RM-7 as a rapid-recovery intravenous anesthetic candidate with greater potency, faster functional recovery, a wider safety margin, and preserved flumazenil reversibility. These results demonstrate that multi-agent coordination can link adaptive molecular search to medicinal chemistry and experimental pharmacology.