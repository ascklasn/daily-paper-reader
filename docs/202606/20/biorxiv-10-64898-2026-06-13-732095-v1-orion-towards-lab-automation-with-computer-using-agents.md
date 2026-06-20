---
title: "Orion: Towards Lab Automation with Computer-Using Agents"
title_zh: Orion：使用计算机的智能代理走向实验室自动化
authors: "Ma, C., Trinh, L., Bucci, M., Regev, A., Wang, H."
date: 2026-06-16
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.13.732095v1.full.pdf"
tags: ["query:agent"]
score: 8.0
evidence: 用于生物医学图像分析和实验室自动化的计算机操作智能体
tldr: "实验室工作依赖计算流程，但受限于手动操作软件和视觉分析。Orion结合大语言模型与终端执行、GUI控制及多步推理，能自动操作CellProfiler等软件并检索网络资源。在基准测试中检索准确性超90%，100小时自主探索生成52份报告，其中22个假设获专家认可。该方法扩展了实验室自动化范围，实现从成像数据到量化分析与假设的可审计自动化。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有实验室计算流程需人工操作专业软件、视觉检查及知识整合，效率低下且难以规模化，亟需自动化手段。
method: Orion作为计算机使用AI代理，融合大语言模型、终端执行、GUI控制与自适应多步推理，在共享计算环境中操作软件和浏览数据。
result: "在生物数据库检索任务中准确率超90%，学会使用CellProfiler和QuPath；100小时自主探索生成52份报告，22个假设被优先验证。"
conclusion: 计算机使用AI代理可大幅拓展实验室自动化，提供从实验图像到量化分析、报告及假设的可扩展可审计路径。
---

## 摘要
实验室发现越来越依赖于连接实验数据与分析、解释和后续假设的计算工作流。然而，这些工作流仍然受到以下因素的限制：劳动密集型的专业软件使用、通过图形用户界面进行的视觉检查，以及跨多个来源的知识整合。在此，我们提出Orion，一个用于生物医学图像分析和解释的、使用计算机的AI代理，它通过自动化实验室工作的计算层向实验室自动化迈进。Orion在共享计算环境中结合了大型语言模型与终端执行、GUI控制和自适应多步骤推理。它可以检查视觉数据、操作标准科学软件、挖掘网络资源并执行端到端的分析和解释工作流程，无需定制软件集成。在基准测试中，Orion在生物医学数据库和文献检索任务上达到了超过90%的准确率，学会了分别使用流行工具CellProfiler和QuPath进行细胞和组织图像的定量分析，并促进了实验成像数据中的自主发现。在100小时的大规模扰动成像数据集自主探索中，Orion生成了52份研究报告，其中人类科学家审阅后优先考虑了22个合理的机制假设。这些结果表明，使用计算机的AI代理可以显著扩展实验室自动化的范围，提供一条从实验成像数据到定量分析、报告和基于生物学的假设的可扩展且可审计的路径。

图1 Orion概览

Orion在数字实验室环境中运行，像人类科学家一样同时使用图形用户界面和终端。这种双重方法使Orion能够与科学软件无缝交互，同时查看图表和网络数据库以捕捉其细微的视觉信息。

## Abstract
Laboratory discovery increasingly depends on computational workflows that connect experimental data to analysis, interpretation and follow-up hypotheses. Yet these workflows remain constrained by labor-intensive use of specialized software, visual inspection through graphical user interfaces, and integration of knowledge across multiple sources. Here, we present Orion, a computer-using AI agent for biomedical image analysis and interpretation that moves towards lab automation by automating this computational layer of laboratory work. Orion combines large language models with terminal execution, GUI control and adaptive multi-step reasoning in a shared computing environment. It can inspect visual data, operate standard scientific software, mine web resources and conduct end-to-end analysis and interpretation workflows without requiring bespoke software integrations. Across benchmarks, Orion achieved over 90% accuracy on biomedical database and literature retrieval tasks, learned to use the popular tools CellProfiler and QuPath for quantitative analysis of cellular and tissue images, respectively, and facilitated autonomous discovery in experimental imaging data. In 100 hours of autonomous exploration of a large-scale perturbation imaging dataset, Orion generated 52 research reports, of which human scientist review prioritized 22 plausible mechanistic hypotheses. These results show that computer-using AI agents can substantially expand the reach of laboratory automation, providing a scalable and auditable route from experimental imaging data to quantitative analysis, reports and biologically grounded hypotheses.



O_FIG O_LINKSMALLFIG WIDTH=200 HEIGHT=45 SRC="FIGDIR/small/732095v1_ufig1.gif" ALT="Figure 1">
View larger version (20K):
org.highwire.dtl.DTLVardef@3d5486org.highwire.dtl.DTLVardef@7836dforg.highwire.dtl.DTLVardef@5a8355org.highwire.dtl.DTLVardef@645418_HPS_FORMAT_FIGEXP  M_FIG Overview of Orion

Orion operates within a digital lab environment, using both graphical user interfaces and terminals just like a human scientist. This dual approach allows Orion to interact seamlessly with scientific software while also viewing figures and web databases to capture their nuanced visual information.

C_FIG