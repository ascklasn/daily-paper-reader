---
title: "DOMINO: graph diffusion learning identifies spatial domain structures with enhanced accuracy and scalability"
title_zh: DOMINO：图扩散学习以更高的准确性和可扩展性识别空间域结构
authors: "Jia, P., Liu, N. W., Ran, Z., Maiolo, S., Zhang, T., Mohenska, M., Guo, X., Wang, C., Walters, E., Ricciardelli, C., Lokman, N. A., Morrow, R., Oehler, M. K., Polo, J. M., Liu, N., Li, F."
date: 2026-06-17
pdf: "https://www.biorxiv.org/content/10.64898/2025.12.15.694536v2.full.pdf"
tags: ["query:spatialprot"]
score: 8.0
evidence: 基于图扩散学习的空间域检测
tldr: 空间转录组数据分析常受限于扩展性和全局结构忽略问题。本文提出DOMINO框架，利用图扩散卷积和对比学习联合优化局部与全局结构，实现可扩展的空间域检测。在健康和恶性数据集上超越现有方法，并成功应用于大规模内异症相关卵巢癌数据集，揭示增殖与非增殖肿瘤状态及亚型特异性微环境。该方法产生边界清晰的生物学域，可扩展至大数据，发现传统聚类无法恢复的空间程序。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有空间域检测方法难以扩展到大规模数据，且仅关注局部结构，忽略组织全局视图。
method: 提出DOMINO，采用图扩散卷积扩展邻域信息，并通过对比学习联合优化局部与全局图结构。
result: 在基准数据上优于现有方法，并在大肠卵巢癌数据中发现保守增殖状态（EIF4A1/ HSPA8高表达）及亚型特异性微环境。
conclusion: DOMINO可扩展且能揭示有生物学意义的空间程序，包括肿瘤内在状态和微环境互作，超越传统聚类。
---

## 摘要
空间转录组学能够进行原位分子分析，从而测量组织内的细胞转录输出。由于组织结构是保守的，可以识别具有特定转录模式的空间域，有助于发现和理解功能性组织区室。因此，已经开发了几种方法来揭示和识别这些空间域。然而，大多数现有方法无法扩展以应对快速增长的数据规模，并且仅关注局部结构而忽略了组织的全局视图。在这里，我们提出了DOMINO，一种用于空间域检测的扩散优化对比学习框架。DOMINO利用图扩散卷积将信息传播到直接邻居之外，并通过对比学习联合优化局部以及重要的全局图结构。这一新颖框架产生了边界更清晰且生物学可解释的域，并且能够扩展到大型数据集，在健康和恶性基准数据集上优于最先进的方法。我们将DOMINO应用于新生成的内膜异位症相关卵巢癌空间转录组数据集，该数据集因规模较大而无法通过现有域检测方法处理。我们发现了这些肿瘤中重复出现的保守增殖和非增殖肿瘤状态，并在一个外部透明细胞卵巢癌空间转录组数据集中独立验证。增殖域的特征是EIF4A1和HSPA8表达升高、细胞周期活性增加、肥大细胞丰度降低以及协调的基质重塑，包括改变的成纤维细胞状态和空间组织。同时，跨肿瘤的整合分析揭示了与子宫内膜样或透明细胞卵巢癌相关的亚型特异性多细胞生态系统，以及一个仅通过整合空间和转录信息才能解析的肿瘤排除基质域。这些发现证明了DOMINO的良好扩展性，并且能够揭示涵盖肿瘤内在状态、肿瘤微环境相互作用和亚型特异性组织结构的生物学意义空间程序，而这些程序无法通过传统的基于表达的分聚类方法恢复。

## Abstract
Spatial transcriptomics enables in situ molecular profiling, allowing to measure the cellular transcriptional output within the tissue. As the tissue architecture is conserved, spatial domains with specific transcriptional patterns can be identified, facilitating the discovery and understanding of functional tissue compartments. Thus, several methods to uncover and identify these spatial domains have been developed. However, most of these existing methods do not scale to rapidly increasing data sizes and focus only on local structure while missing the global view of the tissue. Here, we present DOMINO, a diffusion-optimised contrastive learning framework for spatial domain detection. DOMINO utilises graph diffusion convolution to propagate information beyond immediate neighbours and jointly optimises local and, importantly, global graph structure via contrastive learning. This novel framework yields biologically interpretable domains with clearer boundaries and scales to large datasets, outperforming state-of-the-art methods across healthy and malignant benchmark datasets. We apply DOMINO to a newly generated spatial transcriptomic dataset of endometriosis-associated ovarian cancers, which could not be processed by existing domain detection methods owing to its size. We uncovered conserved proliferative and non-proliferative tumour states that recurred across these tumours and were independently validated in an external clear cell ovarian cancer spatial transcriptomic dataset. Proliferative domains were characterised by elevated expression of EIF4A1 and HSPA8, increased cell cycle activity, reduced mast cell abundance, and coordinated stromal remodelling, including altered fibroblast states and spatial organisation. In parallel, integrative analysis across tumours revealed subtype-specific multicellular ecosystems associated with either endometrioid or clear cell ovarian carcinomas, together with a tumour-excluded stromal domain that could only be resolved through the integration of spatial and transcriptional information. These findings demonstrate how well DOMINO scales up and that it uncovers biologically meaningful spatial programs spanning tumour intrinsic states, tumour microenvironment interactions, and subtype-specific tissue architecture that are not recovered by conventional expression-based clustering approaches.