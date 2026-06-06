---
title: Decoding Multicellular Communication Motifs from Spatial Transcriptomics with ALARMIST
title_zh: 使用ALARMIST从空间转录组学解码多细胞通信基序
authors: "Fan, J., Hood, J., Strong, J., Quinn, J. F., Dai, Y., Data Science TeamLab,, Schein, A., Yu, K. K. H., Tansey, W."
date: 2026-06-01
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.21.726986v2.full.pdf"
tags: ["query:spatialprot"]
score: 6.0
evidence: 空间转录组多细胞通信模式推断
tldr: 细胞组织由多种细胞类型间的协调相互作用驱动，现有空间转录组学方法仅考虑单个配体-受体相互作用，忽略高阶交互。为此提出ALARMIST，一种概率框架，从空间数据中推断可解释的多细胞通信模式，将其分解为重复的通信子网（motif）并估计下游表型效应。在肺腺癌和胶质母细胞瘤数据中，ALARMIST识别出免疫活性血管motif和枢纽-辐条motif，揭示了促进肿瘤进展的微环境驱动因素。该方法为理解复杂组织中的细胞通信提供了新工具。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有方法仅分析单个配体-受体相互作用，无法捕获多细胞类型间的高阶通信模式。
method: ALARMIST利用概率框架分解邻域级信号模式为通信modif，每个modif包含多种细胞类型和富集配体-受体对，并估计各细胞motif活性及下游表型效应。
result: 在肺腺癌中鉴定出免疫活性血管modif，提示浆细胞样树突细胞驱动早期炎症；在胶质瘤中发现恶性巨噬细胞亚群为中心的枢纽-辐条modif，GRN-SORT1信号轴下游基因预测低级别胶质瘤生存率。
conclusion: ALARMIST有效揭示空间转录组中多细胞通信的高阶模式，为肿瘤微环境研究提供了新的计算范式。
---

## 摘要
细胞组织是由多种细胞类型之间反复、协调的相互作用驱动的，每种细胞类型都在发送和接收多种信号。现有的空间图谱数据计算方法仅考虑单个配体-受体相互作用，无法捕捉控制组织微环境的高阶相互作用。为弥补这一空白，我们开发了ALARMIST（空间转录组学中配体与受体基序及影响的评估），这是一个从空间数据中推断可解释的多细胞通信模式的概率框架。ALARMIST将邻域级别的信号模式分解为基序：涉及多种细胞类型和一组富集配体-受体相互作用的重复通信子网络。对于每个细胞，ALARMIST识别其活跃基序，并估计每个基序对活跃细胞的下游表型效应。我们将ALARMIST应用于肺腺癌（LUAD）和胶质母细胞瘤（GBM）的空间数据集，以识别肿瘤进展的微环境驱动因素。在配对LUAD和原位腺癌（AIS）样本中，ALARMIST在肿瘤-正常边界识别出一个免疫活跃的血管基序，并提示基序活跃的浆细胞样树突状细胞是早期致癌过程中炎症的驱动因素。在匹配的低级别和高级别胶质瘤样本中，ALARMIST识别出一个以恶性巨噬细胞亚群为中心的枢纽-辐条基序，揭示了GRN-SORT1信号轴及其下游影响基因集，该基因集可预测低级别胶质瘤患者的生存期。ALARMIST代码可在https://github.com/tansey-lab/alarmist获取。

## Abstract
Cellular organization is driven by recurrent, coordinated interactions between multiple cell types, each sending and receiving multiple signals. Existing computational methods for spatial profiling data consider only individual ligand-receptor interactions and fail to capture the higher-order interactions governing the tissue microenvironment. To address this gap, we developed ALARMIST (Assessment of Ligand And Receptor Motifs And Impacts in Spatial Transcriptomics), a probabilistic framework that infers interpretable multicellular communication patterns from spatial data. ALARMIST decomposes neighborhood-level signaling patterns into motifs: recurrent communication subnetworks involving multiple cell types and sets of enriched ligand-receptor interactions. For each cell, ALARMIST identifies its active motifs and estimates the downstream phenotypic effects of each motif on active cells. We applied alarmist to spatial datasets of lung adenocarcinoma (LUAD) and glioblastoma (GBM) to identify microenvironmental drivers of tumor progression. In paired LUAD and adenocarcinoma-in-situ (AIS) samples, ALARMIST identified an immune-active vascular motif at the tumor-normal boundary and implicated motif-active plasmacytoid dendritic cells as drivers of inflammation in early carcinogenesis. In matched low- and high-grade glioma samples, ALARMIST identified a hub-and-spoke motif centered on a malignant macrophage subpopulation, implicating a GRN-SORT1 signaling axis with a downstream impact gene set predictive of survival in low-grade glioma patients. Code for ALARMIST is available at https://github.com/tansey-lab/alarmist.