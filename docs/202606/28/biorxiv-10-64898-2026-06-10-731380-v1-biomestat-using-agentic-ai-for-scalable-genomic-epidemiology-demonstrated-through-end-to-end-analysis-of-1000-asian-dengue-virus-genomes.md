---
title: "biomeStat: Using Agentic AI for Scalable Genomic Epidemiology Demonstrated Through End-to-End Analysis of 1,000 Asian Dengue Virus Genomes"
title_zh: "biomeStat: 利用代理AI实现可扩展基因组流行病学——通过对1,000个亚洲登革病毒基因组的端到端分析进行演示"
authors: "Ariyaratne, D., Somaratna, N., Malavige, G. N."
date: 2026-06-23
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.10.731380v1.full.pdf"
tags: ["query:agent"]
score: 8.0
evidence: 用于可扩展基因组流行病学的自主AI代理
tldr: 基因组流行病学分析通常依赖专家人工操作多种专门工具并手动调参，计算环境异构且难以复现。biomeStat作为自主AI代理，自动编写代码调用确定性生物信息学工具，动态分配CPU/GPU资源，保证分析的严格可重复性。对1000个亚洲登革热病毒基因组的全自动分析在24小时内完成，揭示了地方性稳定（Re≈1.0），鉴定1869个免疫逃逸位点，并确认176个高度保守的药物靶点残基。该方法将自然语言意图转化为确定性执行，大幅缩短从数周至单次会话，兼顾易用性与方法论透明度。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有基因组流行病学工作流需专家操作多工具和调参，计算基础设施要求高，且生成式AI易在复杂生物领域产生幻觉，缺乏可重复性。
method: biomeStat作为自主AI代理，通过自动编写代码执行IQ-TREE、BEAST2等确定性工具，动态协调CPU/GPU资源，在沙箱环境中保证可重复性。
result: 对1000个DENV基因组全自动分析，24小时内完成系统发育、贝叶斯系统动力学、选择压力及结构映射，鉴定1869个免疫逃逸位点和176个高度保守药物靶点。
conclusion: biomeStat桥接自然语言意图与确定性计算执行，将数周专家工作压缩为单次会话分析，兼具易用性与完全方法透明度。
---

## 摘要
基因组流行病学工作流程通常需要专家对多种专用工具进行精心管理、广泛的手动参数调整以及访问异构计算基础设施。虽然标准生成式AI模型在复杂的生物领域常常产生幻觉，但我们引入了biomeStat：一个自主AI代理，它作为一个严格的确定性协调器。通过自动编写代码在沙盒环境中执行已建立的生物信息学工具，biomeStat动态配置计算资源（CPU和GPU），并保证可重复性，使其对无需命令行专业知识的科学家立即可用。

为了演示该平台，我们对2000年至2025年间从16个亚洲国家采样的1,000个登革病毒（DENV）基因组进行了完全自主的基因组流行病学和结构分析。该代理无缝协调了系统发育重建（IQ-TREE、TreeTime）、贝叶斯系统动力学（通过NVIDIA H200 GPU的BEAST2）、选择压力分析（HyPhy）和结构映射（PyMOL）。分析在不到24小时的挂钟时间内完成，揭示了地方性稳定（R_e ≈ 1.0），并识别出1,869个与B细胞和T细胞表位结构共定位的候选免疫逃逸位点。此外，该代理验证了病毒复制复合体中176个高度保守的药物靶点残基，确认了新兴抗病毒药物JNJ-1802和NITD-688的耐药相关位点在所有四种血清型中保持完全保守。通过弥合自然语言意图与确定性计算执行之间的差距，biomeStat将数周的专家工作缩减为一次完整的单次分析，并具有完全方法透明度。

## Abstract
Genomic epidemiology workflows typically require expert curation of multiple specialized tools, extensive manual parameter tuning, and access to heterogeneous compute infrastructure. While standard generative AI models often hallucinate in complex biological domains, we introduce biomeStat: an autonomous AI agent that functions as a strict deterministic orchestrator. By automatically writing code to execute established bioinformatics tools in sandboxed environments, biomeStat dynamically provisions compute resources (CPU and GPU) and guarantees reproducibility, making it immediately useful for scientists without requiring command-line expertise.

To demonstrate the platform, we performed a fully autonomous genomic epidemiology and structural analysis of 1,000 Dengue virus (DENV) genomes sampled from 16 Asian countries between 2000 and 2025. The agent seamlessly orchestrated phylogenetic reconstruction (IQ-TREE, TreeTime), Bayesian phylodynamics (BEAST2 via NVIDIA H200 GPU), selection pressure analysis (HyPhy), and structural mapping (PyMOL). The analysis was completed in under 24 hours of wall-clock time, revealing endemic stability (R_e [~]1.0) and identifying 1,869 candidate immune escape sites structurally colocalized with B-cell and T-cell epitopes. Furthermore, the agent validated 176 highly conserved drug target residues across the viral replication complex, confirming that resistance-associated positions for emerging antivirals JNJ-1802 and NITD-688 remain absolutely conserved across all four serotypes. By bridging the gap between natural language intent and deterministic computational execution, biomeStat reduces weeks of expert effort into a single-session analysis with full methodological transparency.