---
title: FlashDeconv reveals resolution horizons in atlas-scale spatial transcriptomics
title_zh: FlashDeconv揭示图谱级空间转录组学中的分辨率界限
authors: "Yang, C., Chen, J., Zhang, X."
date: 2026-05-31
pdf: "https://www.biorxiv.org/content/10.64898/2025.12.22.696108v4.full.pdf"
tags: ["query:spatialprot"]
score: 6.0
evidence: 空间转录组去卷积与分辨率分析，对空间蛋白质组集成有参考价值
tldr: 空间转录组分辨率粗化会导致细胞共定位信号反转，但现有解卷积方法需牺牲分辨率或子采样。FlashDeconv通过杠杆分数重要性采样与稀疏正则化，在153秒内处理160万bin。多分辨率分析揭示8-16微米分辨率视界，该视界以下首次量化Tuft细胞趋化生态位，并在结肠癌中发现中性粒细胞-免疫调节树突细胞微域，这些生态位被离散标签方法遗漏。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有解卷积方法因分辨率粗化丢失空间共定位信息，且大规模数据处理缓慢。
method: FlashDeconv结合杠杆分数重要性采样与稀疏空间正则化，实现快速高精度解卷积。
result: 在160万bin上153秒完成解卷积，发现8-16微米分辨率视界，揭示Tuft细胞生态位和中性粒细胞-树突细胞微域。
conclusion: FlashDeconv为大规模空间转录组提供高效解卷积，揭示被传统方法忽略的空间生态位，提升分辨率分析能力。
---

## 摘要
将Visium HD分辨率从8 µm粗化至64 µm，可使细胞类型共定位从负变为正（r = -0.12 -> +0.80），然而许多广泛使用的组成性反卷积工作流需要在百万bin尺度上进行粗化或子采样。在此，我们介绍FlashDeconv，它结合了杠杆得分重要性采样与稀疏空间正则化，在普通硬件上处理160万个bin仅需153秒，同时达到具有竞争力的基准精度。对Visium HD小鼠肠道的系统性多分辨率分析揭示了一个组织特异性分辨率界限（8-16 µm）——即发生这种符号反转的尺度——并通过Xenium真实数据验证。在此界限以下，据我们所知，FlashDeconv提供了首个基于测序的Tuft细胞化学感觉生态位定量分析（干细胞富集15.3倍）。在一个160万bin的人类结直肠癌队列中，FlashDeconv揭示了肿瘤-基质界面处与免疫调节树突状细胞（mRegDC）共定位的中性粒细胞炎症微域——这些空间生态位很大程度上被离散标签汇总所遗漏，RCTD双峰模式仅将2.3%的热点bin标记为中性粒细胞单峰。

## Abstract
Coarsening Visium HD resolution from 8 to 64 {micro}m can flip cell-type co-localization from negative to positive (r = -0.12 [-&gt;] +0.80), yet many widely used compositional deconvolution workflows require coarsening or subsampling at million-bin scale. Here we introduce FlashDeconv, which combines leverage-score importance sampling with sparse spatial regularization to achieve competitive benchmark accuracy while processing 1.6 million bins in 153 seconds on commodity hardware. Systematic multi-resolution analysis of Visium HD mouse intestine reveals a tissue-specific resolution horizon (8-16 {micro}m)--the scale at which this sign inversion occurs--validated by Xenium ground truth. Below this horizon, FlashDeconv provides, to our knowledge, the first sequencing-based quantification of Tuft cell chemosensory niches (15.3-fold stem cell enrichment). In a 1.6-million-bin human colorectal cancer cohort, FlashDeconv uncovers neutrophil inflammatory microdomains co-localized with immunoregulatory dendritic cells (mRegDC) at the tumor-stroma interface--spatial niches largely missed by discrete-label summaries, with RCTD doublet mode labeling only 2.3% of hotspot bins as neutrophil singlets.