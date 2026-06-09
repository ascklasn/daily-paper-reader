---
title: Extrachromosomal DNA as a Causal Instrument for Spatial Multi-Omics
title_zh: 染色体外DNA作为空间多组学因果推断的工具
authors: "Craig, D. W., Rodin, A. S."
date: 2026-06-05
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.02.729483v1.full.pdf"
tags: ["query:spatialprot"]
score: 8.0
evidence: 空间多组学因果推断工具
tldr: 空间多组学数据仅能揭示特征间的相关性，无法推断因果关系。本文利用染色体外DNA（ecDNA）随机分配的特性，将其作为工具变量，结合结构因果模型与二阶段最小二乘法，构建了空间多组学的因果推断框架。通过CAUSANTA模拟器验证，该框架能准确恢复癌基因剂量对表型的因果效应。这一方法为肿瘤组织中的因果机制研究提供了新工具。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有空间多组学分析局限于相关性，缺乏因果推断工具，无法区分驱动与被驱动特征。
method: 利用ecDNA无着丝粒导致的随机分配作为工具变量，采用结构因果模型和二阶段最小二乘估计，并进行敏感性与假阳性检验。
result: 在CAUSANTA模拟器中，框架成功恢复已知的癌基因-表型因果效应，并计划应用于真实肿瘤切片的多工具变量设计。
conclusion: 该方法为空间多组学引入因果推断能力，有望揭示肿瘤异质性的因果机制，推动精准医学发展。
---

## 摘要
空间转录组学、多重成像和计算病理学现在能够以细胞分辨率绘制组织图谱，但应用于这些数据的分析仍然停留在相关性层面。聚类和共现统计描述了哪些特征同时出现，但无法说明哪个特征驱动其他特征。我们提出了一种基于染色体外DNA特定特征的空间多组学因果推断框架。ecDNA没有着丝粒，不附着于有丝分裂纺锤体，在细胞分裂时随机分配给子细胞。因此，相同微环境中的两个相邻细胞可能因与局部信号无关的原因继承截然不同的癌基因拷贝数。ecDNA的这些细胞内在随机化特性共同提供了框架，使ecDNA拷贝数可作为工具变量，将癌基因剂量的影响与下游细胞效应分离开来。在本研究中，我们将其形式化为结构因果模型，采用两阶段最小二乘估计，并结合同胞比较和证伪诊断，同时针对残余混杂因素进行敏感性分析。为了将这些方法与真实情况基准测试，我们构建了CAUSANTA，一个基于智能体的模拟器，能够生成具有已知因果图和随机ecDNA遗传的空间组织。该框架从模拟数据中恢复了已知的癌基因到表型效应，并概述了其在真实肿瘤切片中的应用，包括多工具设置，其中携带不同癌基因的独立ecDNA物种使得在单个肿瘤内实现析因设计成为可能。

## Abstract
Spatial transcriptomics, multiplex imaging, and computational pathology now map tissue organization at cellular resolution, but the analyses applied to these data remain correlational. Clustering and co-occurrence statistics describe which features appear together; they cannot say which feature drives the others. We propose a framework for causal inference in spatial multi-omics built on a specific feature of extrachromosomal DNA (ecDNA). ecDNA carries no centromere; it does not attach to the mitotic spindle and partitions randomly to daughter cells at division. Two neighboring cells in the same microenvironment can therefore inherit very different oncogene copy numbers for reasons unrelated to local signaling. Together, these cell-intrinsic randomization properties of ecDNA provide the framework for ecDNA copy number serving as an instrumental variable (IV) separating the effects of oncogene dosage from the downstream cellular effects. In this study, we formalize this within a structural causal model, implement two-stage least squares estimation with sibling-comparison and falsification diagnostics, and provide sensitivity analyses for residual confounding. To benchmark these methods against ground truth, we built CAUSANTA, an agent-based simulator that generates spatial tissue with a known causal graph and stochastic ecDNA inheritance. The framework recovers known oncogene-to-phenotype effects from simulated data, and we outline its application to real tumor sections, including multi-instrument settings where independent ecDNA species carrying different oncogenes enable factorial designs within a single tumor.