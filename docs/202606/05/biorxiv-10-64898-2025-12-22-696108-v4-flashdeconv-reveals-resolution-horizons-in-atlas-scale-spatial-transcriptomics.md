---
title: FlashDeconv reveals resolution horizons in atlas-scale spatial transcriptomics
title_zh: FlashDeconv揭示图谱级空间转录组学的分辨率视界
authors: "Yang, C., Chen, J., Zhang, X."
date: 2026-05-31
pdf: "https://www.biorxiv.org/content/10.64898/2025.12.22.696108v4.full.pdf"
tags: ["query:spatialprot"]
score: 6.0
evidence: 空间转录组去卷积方法
tldr: "针对Visium HD空间转录组学在百万bin尺度下需降采样或粗化的瓶颈，提出FlashDeconv方法。该方法结合杠杆评分重要性采样与稀疏空间正则化，在基准测试中保持竞争精度的同时，仅用153秒即可处理160万个bin。通过小鼠肠道多分辨率分析，揭示8–16微米为组织特异性分辨率视界——细胞共定位符号在此尺度翻转。验证了Tuft细胞化学感应生态位（干细胞富集15.3倍），并在人类结直肠癌中识别出肿瘤-基质界面中性粒细胞炎症微域，而RCTD等离散标签方法仅标记2.3%热点bin。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有空间解卷积流程在百万bin尺度下需降采样或粗化，导致分辨率损失和细胞共定位误判。
method: FlashDeconv结合杠杆评分重要性采样与稀疏空间正则化，实现高效且准确的空间解卷积。
result: 处理160万bin仅需153秒，在小鼠肠道中精确识别8–16微米分辨率视界，并量化Tuft细胞生态位和中粒细胞炎症微域。
conclusion: FlashDeconv为大规模空间转录组学提供高效高分辨率分析工具，揭示被传统方法忽略的细微空间生态位。
---

## 摘要
将Visium HD分辨率从8微米粗化至64微米，可使细胞类型共定位从负相关翻转为正相关（r = -0.12 → +0.80），然而许多广泛使用的组成反卷积工作流需要在百万bin尺度下进行粗化或子采样。本文提出FlashDeconv，它结合杠杆得分重要性采样与稀疏空间正则化，在商用硬件上仅需153秒即可处理160万个bin，同时达到具有竞争力的基准精度。对Visium HD小鼠肠道的系统性多分辨率分析揭示了组织特异性分辨率视界（8-16微米）——即发生上述符号反转的尺度——并由Xenium金标准验证。在此视界以下，FlashDeconv提供了据我们所知首个基于测序的Tuft细胞化学感应微环境量化（干细胞富集15.3倍）。在一个包含160万bin的人类结直肠癌队列中，FlashDeconv在肿瘤-间质界面揭示了与免疫调节性树突状细胞（mRegDC）共定位的中性粒细胞炎症微区域——这些空间微小生境在很大程度上被离散标签总结所遗漏，而RCTD双峰模式仅将2.3%的热点bin标记为中性粒细胞单峰。

## Abstract
Coarsening Visium HD resolution from 8 to 64 {micro}m can flip cell-type co-localization from negative to positive (r = -0.12 [-&gt;] +0.80), yet many widely used compositional deconvolution workflows require coarsening or subsampling at million-bin scale. Here we introduce FlashDeconv, which combines leverage-score importance sampling with sparse spatial regularization to achieve competitive benchmark accuracy while processing 1.6 million bins in 153 seconds on commodity hardware. Systematic multi-resolution analysis of Visium HD mouse intestine reveals a tissue-specific resolution horizon (8-16 {micro}m)--the scale at which this sign inversion occurs--validated by Xenium ground truth. Below this horizon, FlashDeconv provides, to our knowledge, the first sequencing-based quantification of Tuft cell chemosensory niches (15.3-fold stem cell enrichment). In a 1.6-million-bin human colorectal cancer cohort, FlashDeconv uncovers neutrophil inflammatory microdomains co-localized with immunoregulatory dendritic cells (mRegDC) at the tumor-stroma interface--spatial niches largely missed by discrete-label summaries, with RCTD doublet mode labeling only 2.3% of hotspot bins as neutrophil singlets.