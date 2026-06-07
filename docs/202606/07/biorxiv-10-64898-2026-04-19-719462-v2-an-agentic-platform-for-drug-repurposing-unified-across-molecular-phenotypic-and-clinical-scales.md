---
title: "An Agentic Platform for Drug Repurposing Unified across Molecular, Phenotypic, and Clinical Scales"
title_zh: 一个跨分子、表型和临床尺度统一的药物重定位智能平台
authors: "Wang, C., El Moussaoui, M., Zhang, D., Prabhakaraalva, P., Merzliakov, S., Lu, R. J.-H., Zaman, N., Chakraborty, G., Huang, K.-l."
date: 2026-06-07
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.19.719462v2.full.pdf"
tags: ["query:agent"]
score: 7.0
evidence: 医疗药物重定位代理平台
tldr: 现有药物重定位方法依赖单一证据且跨尺度验证不足。本文提出LinkD平台，统一分子亲和预测（LinkD-Bind）、选择性打分、表型验证和人群临床证据。在BindingDB等基准上排名第一，临床数据揭示β受体阻滞剂降低前列腺癌风险。平台支持自然语言查询，便于用户发现新重定位机会。
source: biorxiv
selection_source: fresh_fetch
motivation: 药物重定位方法多依赖单一线索，缺乏从分子到临床的多尺度统一验证。
method: 提出LinkD框架，整合扩散模型亲和预测、全蛋白质组选择性打分、细胞系表型分析和11.5百万人群队列临床证据。
result: "LinkD-Bind在9个任务中8个排名第一；恢复95.3%已知药物-靶点对；临床证实Propranolol和Carvedilol降低前列腺癌风险5%（HR 0.82/0.92）。"
conclusion: LinkD作为Agentic平台，通过多尺度证据融合和自然语言交互，高效支持药物重定位发现。
---

## 摘要
药物重定位为新疗法提供了一条有效途径，但现有的计算方法依赖单一证据线索，且很少在跨生物学尺度上得到验证。我们提出了LinkD，一个整合了基于扩散的亲和力预测、全蛋白质组选择性评分、表型验证和人群尺度临床证据的综合框架。LinkD-Bind预测了14,981种药物与20,385个人类靶标之间的结合，在9项BindingDB、Davis和KIBA评估中的8项中排名第一，在冷启动条件下提升最大。LinkD-Select通过结合选择性评分和分子对接，恢复了95.3%的已知药物-靶标对。LinkD-Pheno整合了960个癌细胞系的药物敏感性和CRISPR依赖性数据，识别出34个新的药物-基因对，并在前50个候选物中恢复了约85%的已知靶标。在来自西奈山和英国生物库的1150万人中，LinkD优先推荐的β-阻滞剂普萘洛尔（HR 0.82）和卡维地洛尔（HR 0.92）相对于美托洛尔降低了5年前列腺癌发病率，这一点得到了ADRB2对接和LNCaP生长抑制的证实。LinkD-Agent能够有效协调所有证据层，并在公开可用的网络平台上提供服务（https://linkd-agent.onrender.com/），使广大用户能够通过自然语言查询获得新的药物重定位机会。

## Abstract
Drug repurposing offers an effective path to new therapies, yet existing computational approaches rely on a single line of evidence and are rarely validated across biological scales. We present LinkD, an integrated framework that unifies diffusion-based affinity prediction, proteome-wide selectivity scoring, phenotypic validation, and population-scale clinical evidence. LinkD-Bind predicts binding across 14,981 drugs and 20,385 human targets, ranking first in 8 of 9 BindingDB, Davis, and KIBA evaluations, with the largest gains under cold-start conditions. LinkD-Select recovers 95.3% of known drug-target pairs by combining selectivity scoring and molecular docking. LinkD-Pheno integrates drug-sensitivity and CRISPR dependency data across 960 cancer cell lines, identifying 34 novel drug-gene pairs and recovering ~85% of known targets among the top 50 candidates. Across 11.5 million individuals from Mount Sinai and UK Biobank, LinkD-prioritized {beta}-blockers propranolol (HR 0.82) and carvedilol (HR 0.92) reduced 5-year prostate cancer incidence relative to metoprolol, corroborated by ADRB2 docking and LNCaP growth inhibition. LinkD-Agent, which can effectively orchestrate all evidence layers, is served on a publicly available web platform (https://linkd-agent.onrender.com/), enabling a wide range of users to derive new drug repurposing opportunities through natural language queries.