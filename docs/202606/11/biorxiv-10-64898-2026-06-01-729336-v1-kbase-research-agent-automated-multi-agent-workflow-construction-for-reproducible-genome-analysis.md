---
title: "KBase Research Agent: Automated Multi-Agent Workflow Construction for Reproducible Genome Analysis"
title_zh: KBase研究代理：面向可重复基因组分析的自动化多智能体工作流构建
authors: "Gupta, P., Riehl, W. J., Cashman, M., Chivian, D., Neely, C. J., Canon, S. R., Cottingham, R., Henry, C., Arkin, A. P., Dehal, P. S."
date: 2026-06-04
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.01.729336v1.full.pdf"
tags: ["query:agent"]
score: 7.0
evidence: 用于生物信息学工作流自动化的多智能体系统
tldr: 多步骤生物信息学工作流构建需要生物学与计算工具双重专业知识，形成可扩展性瓶颈。本文提出KBase Research Agent，一个多智能体系统，利用KBase文档和知识图谱自动构建分析计划，选择、配置、验证并执行KBase应用，生成可重复的KBase Narrative。在参考工作流和100个细菌基因组上的实验表明，系统能自主完成从读段质控到功能注释的全流程，并产生草稿手稿，证实了端到端自动化的可行性。
source: biorxiv
selection_source: fresh_fetch
motivation: 手动构建多步骤基因组分析工作流耗时且依赖专家经验，阻碍大规模可重复研究，急需自动化方案。
method: 基于KBase文档和知识图谱构建多智能体系统，自动规划、选参、验证并执行工作流，输出可重复Narrative。
result: 在参考工作流和100个未分析基因组上，系统成功完成组装、分类和功能注释，生成可重复结果与草稿手稿。
conclusion: 该工作证明了在生物信息学平台中实现领域知识驱动的端到端工作流自动化的可行性与有效性。
---

## 摘要
构建从读段质量控制到基因组组装再到功能注释的多步骤生物信息学工作流，需要掌握生物学和计算工具选择的专业知识，这对可扩展和可重复的分析构成了瓶颈。我们提出了KBase研究代理，这是一个在DOE系统生物学知识库（KBase）中自动化此类工作流的多智能体系统。给定一组测序读段和一个研究目标，代理构建一个基于KBase文档和KBase应用程序目录的知识图的分析计划，然后选择、参数化、验证并执行适当的KBase应用程序来执行工作流。分析结果作为可重复的KBase叙事保存。我们根据同行评审的《微生物资源公告》中衍生的参考工作流构建的地面真值来评估系统的计划和执行质量。我们进一步将代理应用于来自JGI IMG/M数据库的100个先前未分析的细菌分离基因组，它自主执行了读段质量控制、基因组组装、使用GTDB-Tk进行分类学分类以及下游分析，生成注释基因组、可重复叙事和草稿手稿，无需人工干预。在这些实验中，KBase研究代理展示了在生产级生物信息学平台中实现领域基础、端到端科学工作流自动化的可行性。

## Abstract
Constructing multi-step bioinformatics workflows, from read quality control through genome assembly to functional annotation, requires expertise in both biology and computational tool selection, creating a bottleneck for scalable and reproducible analysis. We present the KBase Research Agent, a multi-agent system for automating such workflows within the DOE Systems Biology Knowledgebase (KBase). Given a set of sequencing reads and a research objective, the agent constructs an analysis plan grounded in KBase documentation and a Knowledge Graph (KG) of the KBase application catalog, then selects, parameterizes, validates and executes appropriate KBase applications to carry out the workflow. The resulting analysis is preserved as a reproducible KBase Narrative. We evaluate the systems planning and execution quality against ground truth constructed from reference workflows derived from peer-reviewed Microbiology Resource Announcements. We further apply the agent to 100 previously unanalyzed bacterial isolate genomes from the JGI IMG/M database, where it autonomously performed read quality control, genome assembly, taxonomic classification with GTDB-Tk, and downstream analysis producing annotated genomes, reproducible Narratives, and draft manuscripts without human intervention. Across these experiments, the KBase Research Agent demonstrates the feasibility of domain-grounded, end-to-end scientific workflow automation in a production bioinformatics platform.