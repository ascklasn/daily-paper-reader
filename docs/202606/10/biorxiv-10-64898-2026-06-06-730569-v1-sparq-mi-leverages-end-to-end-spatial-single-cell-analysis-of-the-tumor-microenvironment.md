---
title: SPARQ-MI leverages end-to-end spatial single-cell analysis of the tumor microenvironment
title_zh: SPARQ-MI 利用肿瘤微环境的端到端空间单细胞分析
authors: "Kiwitz, L., Turiello, R., Effern, M., Toma, M., Landsberg, J., Hoelzel, M., Thurley, K."
date: 2026-06-10
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.06.730569v1.full.pdf"
tags: ["query:spatialprot"]
score: 8.0
evidence: 肿瘤微环境端到端空间单细胞分析
tldr: 多重荧光成像分析肿瘤微环境时，现有方法受噪声分布不均和人工标注瓶颈限制，难以准确量化单细胞特征。SPARQ-MI提出端到端空间单细胞分析框架，集成自动分割、细胞分型和空间重建，并利用37通道PhenoCycler黑色素瘤数据集验证。应用表明，CD8 T细胞的功能状态和空间位置与免疫治疗反应显著关联，响应者中T细胞更靠近肿瘤区域。该工具在最小用户输入下校正抗体信号空间偏差，实现稳健的细胞组成重建，为临床样本的大规模定量分析奠定基础。
source: biorxiv
selection_source: fresh_fetch
motivation: 解决多重荧光成像中噪声不均匀和手动标注瓶颈，实现高效、自动化的空间单细胞分析。
method: SPARQ-MI：端到端流程，包括自动分割、细胞表型标注、空间架构重建及抗体信号不均匀性校正。
result: 在黑色素瘤数据集上，SPARQ-MI发现CD8 T细胞状态和空间分布与免疫治疗反应显著相关。
conclusion: SPARQ-MI实现自动化定量分析，减少用户输入，支持临床样本的空间生物学发现。
---

## 摘要
通过多重荧光成像对肿瘤微环境（TME）进行详细的空间分析需要定量的图像处理和数据分析方法。尽管现有方法能够进行数据预处理直至单个细胞的分割，但单细胞特征的统计分析受到不均匀噪声分布的损害，尤其是在TME等复杂组织中，同时还受到劳动密集型的手动细胞类型注释和区域分割的影响。在这里，我们提出了SPARQ-MI（来自多重成像的空间表型、结构重建和量化），用于简化的空间单细胞分析，以及一个包含来自免疫治疗下黑色素瘤患者的37个荧光通道的组织微阵列PhenoCycler数据集。我们证明SPARQ-MI能够稳健地重建该组织类型及其他组织类型的细胞和空间组成。我们的分析揭示了CD8 T细胞的细胞状态和空间位置与免疫治疗反应之间的关联。总体而言，SPARQ-MI能够在最少的用户输入下对复杂的荧光组织学样本进行定量分析，并考虑抗体信号的空间不均匀覆盖，为临床样本的定量分析奠定了基础。

## Abstract
Detailed spatial analysis of the tumor micro-environment (TME) through multiplexed fluorescence imaging requires quantitative image-processing and data-analysis methods. While data-preprocessing down to segmentation of individual cells is captured by available methods, statistical analysis of single-cell features is compromised by the uneven noise distribution especially in complex tissues such as the TME, as well as by labor-intensive manual cell-type annotation and region segmentation. Here, we present SPARQ-MI (Spatial Phenotyping, Architecture Reconstruction and Quantification from Multiplexed Imaging) for streamlined spatial single-cell analysis, along with a tissue microarray PhenoCycler data-set with 37 fluorescent channels from melanoma patients under immunotherapy. We demonstrate that SPARQ-MI enables robust reconstruction of the cellular and spatial composition in this and other tissue types. Our analysis reveals associations of the cell-state and spatial location of CD8 T cells with response to immunotherapy. Overall, SPARQ-MI allows for quantitative analysis of complex fluorescence histology samples under minimal user input, and accounting for spatially uneven coverage of antibody signals, setting the stage for quantitative analysis of clinical samples.