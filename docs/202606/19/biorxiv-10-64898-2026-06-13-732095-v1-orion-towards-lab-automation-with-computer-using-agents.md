---
title: "Orion: Towards Lab Automation with Computer-Using Agents"
title_zh: Orion：迈向使用计算机代理的实验室自动化
authors: "Ma, C., Trinh, L., Bucci, M., Regev, A., Wang, H."
date: 2026-06-16
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.13.732095v1.full.pdf"
tags: ["query:agent"]
score: 7.0
evidence: 用于生物医学图像分析和实验室自动化的计算机使用AI智能体
tldr: "实验室计算工作流受限于手动操作专业软件和视觉检查，效率低下且难以扩展。Orion提出计算机使用AI agent，结合大语言模型与终端执行、GUI控制及自适应多步推理，在共享计算环境中实现自动化。在生物医学图像分析中，检索准确率超90%，学会使用CellProfiler和QuPath，100小时自主探索生成52份研究报告，其中22个机制假设通过专家评审。该方法为实验室自动化提供了可扩展、可审计的路线，从实验图像到定量分析、报告和生物学假设。"
source: biorxiv
selection_source: fresh_fetch
motivation: 实验室计算工作流依赖手动操作专业软件和视觉检查，效率低下，亟需自动化方法。
method: 结合大语言模型与终端执行、GUI控制及自适应多步推理的共享计算环境。
result: "生物医学检索准确率>90%，学会使用CellProfiler和QuPath，100小时自主生成52份报告，22个假设被认可。"
conclusion: 计算机使用AI agent可大幅扩展实验室自动化，实现从实验图像到假设的端到端分析。
---

## 摘要
实验室发现越来越依赖于将实验数据与分析、解释和后续假设连接起来的计算工作流程。然而，这些工作流程仍然受到劳动密集型使用的专业软件、通过图形用户界面的视觉检查以及跨多个来源的知识整合的限制。在这里，我们介绍了Orion，一个用于生物医学图像分析和解释的计算机使用AI代理，通过自动化实验室工作的这一计算层来迈向实验室自动化。Orion在共享计算环境中结合了大型语言模型与终端执行、GUI控制和自适应多步推理。它可以检查视觉数据、操作标准科学软件、挖掘网络资源并执行端到端的分析和解释工作流程，无需定制的软件集成。在基准测试中，Orion在生物医学数据库和文献检索任务上达到了超过90%的准确率，学会了分别使用流行工具CellProfiler和QuPath进行细胞和组织图像的定量分析，并促进了实验成像数据中的自主发现。在100小时的大规模扰动成像数据集自主探索中，Orion生成了52份研究报告，其中人类科学家审查优先考虑了22个合理的机制假说。这些结果表明，使用计算机的AI代理可以显著扩大实验室自动化的范围，提供从实验成像数据到定量分析、报告和基于生物学的假说的可扩展且可审计的途径。

## Abstract
Laboratory discovery increasingly depends on computational workflows that connect experimental data to analysis, interpretation and follow-up hypotheses. Yet these workflows remain constrained by labor-intensive use of specialized software, visual inspection through graphical user interfaces, and integration of knowledge across multiple sources. Here, we present Orion, a computer-using AI agent for biomedical image analysis and interpretation that moves towards lab automation by automating this computational layer of laboratory work. Orion combines large language models with terminal execution, GUI control and adaptive multi-step reasoning in a shared computing environment. It can inspect visual data, operate standard scientific software, mine web resources and conduct end-to-end analysis and interpretation workflows without requiring bespoke software integrations. Across benchmarks, Orion achieved over 90% accuracy on biomedical database and literature retrieval tasks, learned to use the popular tools CellProfiler and QuPath for quantitative analysis of cellular and tissue images, respectively, and facilitated autonomous discovery in experimental imaging data. In 100 hours of autonomous exploration of a large-scale perturbation imaging dataset, Orion generated 52 research reports, of which human scientist review prioritized 22 plausible mechanistic hypotheses. These results show that computer-using AI agents can substantially expand the reach of laboratory automation, providing a scalable and auditable route from experimental imaging data to quantitative analysis, reports and biologically grounded hypotheses.