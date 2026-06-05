---
title: "ClaroAI-Bench: Evaluating Agentic Scientific Reproducibility on Real Biomedical Papers"
title_zh: ClaroAI-Bench：在真实生物医学论文上评估智能型科学可重复性
authors: "O'Connell, K. A."
date: 2026-05-12
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.08.723611v1.full.pdf"
tags: ["query:agent"]
score: 8.0
evidence: 评估AI代理在生物医学可重复性上的表现
tldr: "当前AI agent在代码生成方面表现优异，但缺乏对科研可复现性的端到端评估。ClaroAI-Bench基于35篇真实生物医学论文，从数据可发现性、可访问性、代码可用性、环境可重建性和结果可复现性五维度评估agent。实验表明，完整agent (Claude Code)成功复现了60.6%的计算论文，而基准方法均无法复现。该基准填补了代码生成与科学AI评估之间的空白，揭示了环境重建是评价分歧最大的维度。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有AI评估缺乏对科研可复现性的真实世界测试，无法衡量agent完成完整复现流水线的能力。
method: 构建包含35篇NIH论文的基准，设计五维评分标准，在三种条件下评估Agent的复现能力。
result: "完整agent复现了20/33篇(60.6%)，D1-D4得分与D5强相关(r=0.68)，环境重建是评价分歧最大维度。"
conclusion: ClaroAI-Bench提供了评估AI可复现性的标准化框架，有助于推动自动化科学研究。
---

## 摘要
我们介绍了ClaroAI-Bench，这是一个用于衡量人工智能代理重现已发表生物医学研究中的计算发现能力的评估套件。该基准包含35篇由NIH资助的真实论文，涵盖五种模态（基因组学、影像学、临床/EHR、流行病学、湿实验），并按照五个维度进行评分：数据可发现性（D1）、数据可访问性（D2）、代码可用性（D3）、环境可重建性（D4）和结果可重复性（D5）。每个任务要求代理定位数据、获取代码、重建计算环境、执行分析，并根据已发表的声明验证结果——这一过程反映了完整的科学重现流程。在三条件消融实验中，仅审计的基线（D1-D4元数据评分）和仅使用bash工具的代理（API+bash工具）均实现了0%的D5重现率，而全功能代理（Claude Code，所有工具）成功重现了33篇计算论文中的20篇（60.6%；95%置信区间[42.4, 75.8]）。D1-D4元数据评分强烈预测D5结果（Spearman r=0.68，p<0.0001），可访问数据和代码的论文的D5得分比受限论文高2.9倍（p=0.0013）。使用三个前沿模型（Claude Opus 4.6、GPT-5.4、Gemini 2.5 Pro）进行多模型评分，在D3上模型间一致性为r=0.85-0.97，但在D4上仅为r=0.51-0.81，这表明环境重建是评估者分歧最大的维度。ClaroAI-Bench通过测试具有脆弱环境、缺失元数据和访问限制的长期、真实世界的重现任务，填补了代码生成基准（SWE-bench）与端到端科学AI评估之间的空白。该基准、评分标准、代理日志以及可通过pip安装的审计器已存档于https://doi.org/10.5281/zenodo.20071236和HuggingFace数据集https://huggingface.co/datasets/kyleaoconnell22/claroai-bench。

## Abstract
We introduce ClaroAI-Bench, an evaluation suite for measuring AI agents ability to reproduce computational findings from published biomedical research. The benchmark comprises 35 real NIH-funded papers spanning five modalities (genomics, imaging, clinical/EHR, epidemiology, wet-lab) scored on a five-dimension rubric: data findability (D1), data accessibility (D2), code availability (D3), environment reconstructability (D4), and results reproducibility (D5). Each task requires an agent to locate data, obtain code, reconstruct the compute environment, execute the analysis, and verify results against published claims--mirroring the full scientific reproduction pipeline. In a three-condition ablation, an audit-only baseline (D1-D4 metadata scoring) and a bash-only agent (API + bash tool) both achieve 0% D5 reproduction, while a full-capability agent (Claude Code, all tools) reproduces 20 of 33 computational papers (60.6%; 95% CI [42.4, 75.8]). D1-D4 metadata scores strongly predict D5 outcomes (Spearman r=0.68, p<0.0001), and papers with accessible data and code achieve 2.9x higher D5 scores than restricted papers (p=0.0013). Multi-model scoring with three frontier models (Claude Opus 4.6, GPT-5.4, Gemini 2.5 Pro) yields inter-model agreement of r=0.85-0.97 on D3 but only r=0.51-0.81 on D4, identifying environment reconstruction as the dimension with highest evaluator disagreement. ClaroAI-Bench fills a gap between code-generation benchmarks (SWE-bench) and end-to-end scientific AI evaluations by testing long-horizon, real-world reproduction tasks with brittle environments, missing meta-data, and access constraints. The benchmark, scoring rubric, agent logs, and pip-installable auditor are archived at https://doi.org/10.5281/zenodo.20071236 and on HuggingFace Datasets at https://huggingface.co/datasets/kyleaoconnell22/claroai-bench.