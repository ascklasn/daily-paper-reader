---
title: "DOMINO: graph diffusion learning identifies spatial domain structures with enhanced accuracy and scalability"
title_zh: DOMINO：图扩散学习以增强的准确性和可扩展性识别空间域结构
authors: "Jia, P., Liu, N. W., Ran, Z., Maiolo, S., Zhang, T., Mohenska, M., Guo, X., Wang, C., Walters, E., Ricciardelli, C., Lokman, N. A., Morrow, R., Oehler, M. K., Polo, J. M., Liu, N., Li, F."
date: 2026-06-17
pdf: "https://www.biorxiv.org/content/10.64898/2025.12.15.694536v2.full.pdf"
tags: ["query:spatialprot"]
score: 7.0
evidence: 图扩散学习用于空间转录组学领域检测，方法可迁移至空间蛋白质组学
tldr: 空间转录组数据分析面临数据规模大、现有方法多只关注局部结构而忽略全局视图的问题。本文提出DOMINO，一种扩散优化对比学习框架，通过图扩散卷积传播信息并结合对比学习联合优化局部与全局图结构。该方法比现有方法在边界清晰度和可扩展性上更优，成功应用于大规模子宫内膜异位相关卵巢癌数据集，发现了增殖与非增殖肿瘤状态等生物学有意义的结构。DOMINO能够揭示肿瘤内在状态、微环境互作及亚型特异性组织架构，超越了常规表达聚类方法。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有空间域检测方法无法扩展到大规模数据，且只关注局部结构，缺乏全局视角。
method: 提出DOMINO框架，利用图扩散卷积和对比学习联合优化局部与全局图结构。
result: 在健康与恶性基准数据集上优于现有方法，成功处理大规模卵巢癌数据集，发现保守的增殖与非增殖肿瘤状态等。
conclusion: DOMINO可扩展且能揭示常规方法无法恢复的生物学意义空间程序。
---

## 摘要
空间转录组学能够实现原位分子分析，从而测量组织内的细胞转录输出。由于组织结构得以保留，可以识别具有特定转录模式的空间域，有助于发现和理解功能性组织隔室。因此，已有多种方法被开发用于揭示和识别这些空间域。然而，现有方法大多无法扩展到快速增长的數據量，且仅关注局部结构而忽略了组织的全局视图。本文提出DOMINO，一种用于空间域检测的扩散优化对比学习框架。DOMINO利用图扩散卷积将信息传播到直接邻居之外，并通过对比学习联合优化局部和重要的全局图结构。这一新颖框架能够生成边界更清晰、具有生物学可解释性的域，并可扩展至大型数据集，在健康和恶性基准数据集上均优于现有最先进方法。我们将DOMINO应用于新生成的内异症相关卵巢癌空间转录组数据集，该数据集因规模过大而无法被现有域检测方法处理。我们发现了在这些肿瘤中反复出现且保守的增殖性和非增殖性肿瘤状态，并在外部透明细胞卵巢癌空间转录组数据集中得到独立验证。增殖性域的特征是EIF4A1和HSPA8表达升高、细胞周期活性增加、肥大细胞丰度降低以及协调的基质重塑，包括成纤维细胞状态和空间组织的改变。同时，跨肿瘤整合分析揭示了与子宫内膜样或透明细胞卵巢癌相关的亚型特异性多细胞生态系统，以及一个仅通过整合空间和转录信息才能解析的肿瘤排斥基质域。这些发现展示了DOMINO良好的扩展性，并揭示了超越传统基于表达聚类方法所能恢复的、涵盖肿瘤内在状态、肿瘤微环境相互作用和亚型特异性组织结构的具有生物学意义的空间程序。

## Abstract
Spatial transcriptomics enables in situ molecular profiling, allowing to measure the cellular transcriptional output within the tissue. As the tissue architecture is conserved, spatial domains with specific transcriptional patterns can be identified, facilitating the discovery and understanding of functional tissue compartments. Thus, several methods to uncover and identify these spatial domains have been developed. However, most of these existing methods do not scale to rapidly increasing data sizes and focus only on local structure while missing the global view of the tissue. Here, we present DOMINO, a diffusion-optimised contrastive learning framework for spatial domain detection. DOMINO utilises graph diffusion convolution to propagate information beyond immediate neighbours and jointly optimises local and, importantly, global graph structure via contrastive learning. This novel framework yields biologically interpretable domains with clearer boundaries and scales to large datasets, outperforming state-of-the-art methods across healthy and malignant benchmark datasets. We apply DOMINO to a newly generated spatial transcriptomic dataset of endometriosis-associated ovarian cancers, which could not be processed by existing domain detection methods owing to its size. We uncovered conserved proliferative and non-proliferative tumour states that recurred across these tumours and were independently validated in an external clear cell ovarian cancer spatial transcriptomic dataset. Proliferative domains were characterised by elevated expression of EIF4A1 and HSPA8, increased cell cycle activity, reduced mast cell abundance, and coordinated stromal remodelling, including altered fibroblast states and spatial organisation. In parallel, integrative analysis across tumours revealed subtype-specific multicellular ecosystems associated with either endometrioid or clear cell ovarian carcinomas, together with a tumour-excluded stromal domain that could only be resolved through the integration of spatial and transcriptional information. These findings demonstrate how well DOMINO scales up and that it uncovers biologically meaningful spatial programs spanning tumour intrinsic states, tumour microenvironment interactions, and subtype-specific tissue architecture that are not recovered by conventional expression-based clustering approaches.