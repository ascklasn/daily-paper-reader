---
title: Multi-Sample and Multi-Group Spatial Colocalization Analysis Using PANORAMIC
title_zh: 使用PANORAMIC进行多样本和多组空间共定位分析
authors: "Chang, J., Perez, A. E., Molina, P., Khurana, R., Zhang, W., Tian, L., Plevritis, S."
date: 2026-06-01
pdf: "https://www.biorxiv.org/content/10.1101/2025.09.18.677135v3.full.pdf"
tags: ["query:spatialprot"]
score: 7.0
evidence: 空间共定位分析方法，适用于空间蛋白组学
tldr: 空间组学研究中，若不考虑样本内空间不确定性，异质性队列推断易产生偏差。PANORAMIC层次框架通过边缘校正邻域富集估计共定位、空间自助法量化不确定性，并利用多级随机效应荟萃分析跨样本传播。模拟实验在多种空间设置和数据降质下证明其恢复不确定性和异质性的能力优于朴素估计器。应用于结直肠癌组织微阵列，PANORAMIC揭示克罗恩样反应肿瘤中B和T细胞共定位更强，且高阶免疫组织更紧密，符合免疫聚集体特征。该工作不仅提升了队列级推断的可靠性，还提供了开源R包以推动应用。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有空间组学方法常忽略样本内空间不确定性，导致异质性队列推断产生偏差，亟需显式量化并传播该不确定性的方法。
method: PANORAMIC采用边缘校正邻域富集估计局部共定位，空间自助法量化不确定性，多级随机效应荟萃分析跨样本、患者和条件传播。
result: 模拟显示PANORAMIC优于朴素估计器；在结直肠癌数据中，发现克罗恩样反应肿瘤中B和T细胞共定位更强及更紧密的高阶免疫组织。
conclusion: 传播样本内空间不确定性可改善空间组学研究的队列级推断，PANORAMIC提供了可行的开源工具。
---

## 摘要
摘要：空间组学研究比较不同样本间的细胞-细胞组织模式，但大多数方法在建模样本间变异时，将样本级别的空间估计视为无误差。忽略样本内不确定性可能会扭曲异质性队列的推断，因此需要能够明确量化并将这种不确定性传播到队列级分析的方法。我们提出了PANORAMIC，一个用于空间共定位分析的分层框架，它使用边缘校正的邻域富集来估计局部细胞类型共定位，使用空间自助法量化样本内不确定性，并使用多水平随机效应荟萃分析将这种不确定性跨样本、患者和条件进行传播。在模拟实验中，与朴素估计器相比，PANORAMIC在多种空间设置和渐进数据退化下，改善了对样本内不确定性和样本间异质性的恢复。应用于通过多重免疫荧光成像分析的大肠癌组织微阵列，PANORAMIC识别出在克罗恩样反应的肿瘤中，B细胞和T细胞的共定位比在弥漫性炎性浸润的肿瘤中更强，同时伴随与免疫聚集体一致的更紧密的高阶免疫组织。这些结果表明，传播样本内空间不确定性可以改善空间组学研究中的队列级推断。可用性和实现：PANORAMIC以开源R包形式发布在https://github.com/plevritis-lab/panoramic。

## Abstract
Motivation: Spatial omics studies compare cell-cell organization across samples, but most methods model between-sample variability while treating sample-level spatial estimates as error-free. Overlooking within-sample uncertainty can distort inference in heterogeneous cohorts, motivating methods that explicitly quantify and propagate this uncertainty into cohort-level analyses. Results: We present PANORAMIC, a hierarchical framework for spatial colocalization analysis that uses edge-corrected neighborhood enrichment to estimate local cell-type colocalization, spatial bootstrapping to quantify within-sample uncertainty, and multilevel random-effects meta-analysis to propagate this uncertainty across samples, patients, and conditions. In simulations, PANORAMIC improved recovery of within-sample uncertainty and between-sample heterogeneity relative to naive estimators across diverse spatial settings and progressive data degradation. Applied to a colorectal cancer tissue microarray profiled by multiplexed immunofluorescence imaging, PANORAMIC identified stronger B- and T-cell colocalization in tumors with Crohn's-like reaction than in tumors with diffuse inflammatory infiltration, together with tighter higher-order immune organization consistent with immune aggregates. These results show that propagating within-sample spatial uncertainty can improve cohort-level inference in spatial omics studies. Availability and Implementation: PANORAMIC is released as an open-source R package at https://github.com/plevritis-lab/panoramic.