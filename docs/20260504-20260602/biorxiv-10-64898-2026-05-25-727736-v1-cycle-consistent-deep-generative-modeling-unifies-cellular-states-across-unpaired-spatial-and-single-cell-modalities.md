---
title: Cycle-consistent deep generative modeling unifies cellular states across unpaired spatial and single-cell modalities
title_zh: 循环一致深度生成模型统一非配对空间和单细胞模态的细胞状态
authors: "Zhang, H., Quinn, J. F., Data Science TeamLab,, Tansey, W."
date: 2026-05-26
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.25.727736v1.full.pdf"
tags: ["query:spatialprot"]
score: 8.0
evidence: 整合空间转录组和蛋白质组，使用深度生成模型
tldr: 当前空间和单细胞技术捕获细胞状态的互补但不完全视图，整合面临未配对测量、特征空间不匹配和模态特定偏差等挑战。MultiTME通过空间正则化的循环一致深度生成模型，学习共享潜在表示，实现无需配对观测或共享特征的跨模态翻译。在基准测试中，MultiTME优于现有方法，实现准确跨模态细胞分类，改善空间转录组面板补全，并转移全转录组信息生成细胞分辨率空间图谱。应用于结直肠癌数据集，MultiTME揭示单模态不可直接观察的空间连贯增殖-侵袭肿瘤轴；在五个多模态空间数据集中，MultiTME能校正Xenium与CosMx之间的平台特异性偏差，促进跨数据集协调和泛癌空间研究。
source: biorxiv
selection_source: fresh_fetch
motivation: 整合未配对、特征空间不匹配的多模态空间与单细胞数据，克服模态特定偏差。
method: 采用空间正则化的循环一致深度生成模型（CycleGAN），学习共享潜在空间实现双向映射。
result: 在多种基准上性能最优，实现跨模态细胞分类、面板补全和全转录组空间映射。
conclusion: MultiTME可揭示单模态不可见的生物轴，校正平台偏差，促进跨数据集和泛癌研究。
---

## 摘要
当前的空间和单细胞技术捕获了细胞状态的互补但不完整的视图，转录组、蛋白质组和空间信息分布在不同的平台上。非配对的测量、不匹配的特征空间以及模态特定偏差给整合带来了挑战。我们提出了MultiTME，一个多模态框架，它使用空间正则化、循环一致的深度生成模型来整合异质的空间和单细胞数据。通过强制双向映射的一致性，MultiTME学习了一个共享的潜在表示，使得无需配对观测或共享特征即可在模态之间进行转换。在基准测试中，MultiTME优于现有方法，产生准确的跨模态细胞分型，提高了空间转录组面板的完整性，并转移全转录组信息以生成细胞分辨率的空间解析图谱。应用于多模态结直肠癌数据集，我们证明MultiTME整合揭示了一个在单一模态中无法直接观察到的空间一致的增殖-侵袭性肿瘤轴。在五个多模态空间数据集中，我们展示MultiTME可以纠正Xenium和CosMx之间的平台特定偏差，从而促进跨数据集协调并实现泛癌空间研究。MultiTME的代码可在https://github.com/tansey-lab/multitme获取。

## Abstract
Current spatial and single-cell technologies capture complementary but incomplete views of cellular state, with transcriptomic, proteomic, and spatial information distributed across distinct platforms. Integration is challenged by unpaired measurements, mismatched feature spaces, and modality-specific biases. We present MultiTME, a multimodal framework that integrates heterogeneous spatial and single-cell data using a spatially-regularized, cycle-consistent deep generative model. By enforcing consistency of bidirectional mappings, MultiTME learns a shared latent representation that enables translation between modalities without requiring paired observations or shared features. Across benchmarks, MultiTME outperforms existing methods, produces accurate cross-modal cell typing, improves spatial transcriptomic panel completion, and transfers whole-transcriptome information to generate spatially resolved maps at cellular resolution. Applied to a multimodal colorectal cancer dataset, we demonstrate that MultiTME integration reveals a spatially coherent proliferative-invasive tumor axis not directly observable within single modalities. Across five multimodal spatial datasets, we show MultiTME can correct for platform-specific biases between Xenium and CosMx, thereby facilitating cross-dataset harmonization and enabling pan-cancer spatial studies. Code for MultiTME is available at https://github.com/tansey-lab/multitme.