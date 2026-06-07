---
title: FlashDeconv reveals resolution horizons in atlas-scale spatial transcriptomics
title_zh: FlashDeconv揭示图谱尺度空间转录组学中的分辨率极限
authors: "Yang, C., Chen, J., Zhang, X."
date: 2026-05-31
pdf: "https://www.biorxiv.org/content/10.64898/2025.12.22.696108v4.full.pdf"
tags: ["query:spatialprot"]
score: 8.0
evidence: 空间解卷积方法，适用于高分辨率空间蛋白质组学
tldr: 图谱级空间转录组学中，分辨率粗化会导致细胞类型共定位符号反转。现有方法需粗化数据才能处理百万bin尺度，但粗化会扭曲信号。本文提出FlashDeconv，结合杠杆得分重要性采样与稀疏空间正则化，在153秒内处理160万bin，精度优于现有方法。通过多分辨率分析揭示8-16μm组织特异性分辨率视界，并首次基于测序定量Tuft细胞化学感应生态位（15.3倍干细胞富集）。在人类结直肠癌中识别出中性粒细胞-免疫调节树突状细胞共定位微域，弥补了离散标签分析的局限性。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有空间解卷积方法在处理百万bin尺度时需粗化数据，导致细胞共定位信号失真，无法准确解析精细空间结构。
method: 提出FlashDeconv，利用杠杆得分重要性采样选择性处理关键bin，结合稀疏空间正则化约束，实现高效高精度解卷积。
result: 在160万bin数据上153秒完成，精度超越现有方法，发现Visium HD分辨率视界（8-16μm）及肿瘤微环境炎症微域。
conclusion: 首次基于测序定量Tuft细胞化学感应生态位，并揭示离散标签遗漏的肿瘤-基质界面空间结构，推动了图谱级空间转录组学分析。
---

## 摘要
将Visium HD分辨率从8微米粗化到64微米可将细胞类型共定位从负相关变为正相关（r = -0.12 → +0.80），然而许多广泛使用的组成性反卷积工作流程需要在百万级bin尺度上进行粗化或子采样。这里我们介绍FlashDeconv，它结合杠杆得分重要性采样与稀疏空间正则化，在普通硬件上处理160万个bin仅需153秒，同时达到具有竞争力的基准精度。对Visium HD小鼠肠道的系统性多分辨率分析揭示了组织特异性的分辨率极限（8-16微米）——即发生这种符号反转的尺度，并由Xenium地面实况验证。在此极限以下，FlashDeconv提供了据我们所知的第一个基于测序的Tuft细胞化学感应微环境定量（干细胞富集度15.3倍）。在一个包含160万个bin的人类结直肠癌队列中，FlashDeconv在肿瘤-基质界面揭示了与免疫调节性树突细胞（mRegDC）共定位的中性粒细胞炎症微结构域——这些空间微环境在很大程度上被离散标签摘要所遗漏，而RCTD双峰模式标记仅将2.3%的热点bin标记为中性粒细胞单峰。

## Abstract
Coarsening Visium HD resolution from 8 to 64 {micro}m can flip cell-type co-localization from negative to positive (r = -0.12 [-&gt;] +0.80), yet many widely used compositional deconvolution workflows require coarsening or subsampling at million-bin scale. Here we introduce FlashDeconv, which combines leverage-score importance sampling with sparse spatial regularization to achieve competitive benchmark accuracy while processing 1.6 million bins in 153 seconds on commodity hardware. Systematic multi-resolution analysis of Visium HD mouse intestine reveals a tissue-specific resolution horizon (8-16 {micro}m)--the scale at which this sign inversion occurs--validated by Xenium ground truth. Below this horizon, FlashDeconv provides, to our knowledge, the first sequencing-based quantification of Tuft cell chemosensory niches (15.3-fold stem cell enrichment). In a 1.6-million-bin human colorectal cancer cohort, FlashDeconv uncovers neutrophil inflammatory microdomains co-localized with immunoregulatory dendritic cells (mRegDC) at the tumor-stroma interface--spatial niches largely missed by discrete-label summaries, with RCTD doublet mode labeling only 2.3% of hotspot bins as neutrophil singlets.