---
title: "BRIDGE: A Multi-organ Histo-ST Foundation Model Enables Virtual Spatial Transcriptomics for Enhanced Few-shot Cancer Diagnosis"
title_zh: BRIDGE：一种多器官组织病理学基础模型实现虚拟空间转录组学以增强少样本癌症诊断
authors: "Liang, Z., ZHAO, W., Wang, F., Chen, G., Huang, Y., Yu, L."
date: 2026-05-08
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.05.722971v1.full.pdf"
tags: ["query:pm"]
score: 8.0
evidence: 多器官基础模型对齐组织学与空间转录组用于诊断
tldr: "现有虚拟空间转录组方法依赖单器官模型，在少样本场景下精度不足。本文提出BRIDGE，基于60万对组织学-ST图谱预训练的多器官基础模型，通过跨器官形态与基因组对齐实现泛化。在少样本条件下，BRIDGE预测80个标志基因表达的平均PCC达0.474，较现有最优提升30%；在癌症生存预测中，六项TCGA任务平均C-index为0.724，对未见癌症类型零样本达0.717。BRIDGE为临床少样本诊断和罕见癌研究提供了高效的数据驱动工具。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有虚拟ST方法需大量器官特异性训练数据，难以适用于临床少样本场景。
method: 构建多器官基础模型BRIDGE，在13个器官60万对数据上预训练，对齐形态与基因组特征。
result: "少样本下80基因表达预测PCC 0.474（提升30%）；生存预测C-index 0.724，零样本达0.717。"
conclusion: BRIDGE实现数据高效的虚拟ST，有望替代实验室测序并推动少样本癌症诊断。
---

## 摘要
近年来的研究探索了从组织学图像生成虚拟空间转录组（ST）图谱，为实验室测量的分子图谱提供了一种有前景的替代方案。然而，现有方法主要依赖单器官模型，并需要大量器官特异性训练数据，这在临床实践中具有挑战性的少样本条件下限制了其准确性（例如，针对特定器官或技术可用切片少于10张）。在此，我们提出BRIDGE，一种多器官基础模型，在跨越13个人体器官和三种测序技术的60多万对组织学-ST图谱上进行了预训练。通过在共享的多器官潜在空间中稳健地对齐形态学特征和基因组信息，BRIDGE能够利用不同组织间的共同生物学知识，实现准确且可泛化的泛癌分子图谱分析。无需额外的器官特异性微调，BRIDGE即可准确预测80个生物标志物基因的空间表达，平均皮尔逊相关系数（PCC）达到0.474——在三种临床具有挑战性的少样本场景下，比现有最先进模型提高了30%。利用生成的虚拟ST，BRIDGE在预测癌症生存方面优于当前最先进的病理学基础模型，在六个TCGA队列中平均一致性指数（C-index）达到0.724。值得注意的是，即使在涉及三种训练中未见癌症类型的零样本场景下，BRIDGE仍保持卓越性能，平均C-index为0.717，展示了其超越器官和亚型特异性的强大泛化能力。此外，BRIDGE生成的虚拟空间转录组在预后准确性上可与批量RNA-seq相媲美，凸显其作为实验室测序的空间信息替代方案潜力。总体而言，BRIDGE代表了一种数据高效的虚拟ST工具，有助于临床少样本背景下的生物医学发现，并推进对缺乏足够样本的未被充分研究癌症的诊断。

## Abstract
Recent studies have explored generating virtual spatial transcriptomics (ST) profiles from histological images, offering a promising alternative to laboratory-measured molecular profiling. However, existing approaches predominantly rely on single-organ models and require sub-stantial organ-specific training data, restricting their accuracy under challenging few-shot conditions in clincical practice, where less than 10 slides are available for specific organs or techniques. Here, we present BRIDGE, a multi-organ foundation model pre-trained on over 600,000 paired histology-ST profiles across 13 human organs and three sequencing techniques. By robustly aligning morphological features and genomic information within a shared multi-organ latent space, BRIDGE can leverage common biological knowledge across distinct tissues to enable accurate and generalizable pan-cancer molecular profiling. Without additional organ-specific fine-tuning, BRIDGE accurately predicts the spatial expression of 80 biomarker genes, achieving an average Pearson correlation coefficient (PCC) of 0.474--a 30% improvement over existing state-of-the-art models under three clinically challenging few-shot scenarios. With generated virtual ST, BRIDGE outperforms current state-of-the-art pathology foundation models in predicting cancer survival, achieving an average concordance index (C-index) of 0.724 across six TCGA cohorts. Notably, BRIDGE maintains exceptional performance even in zero-shot scenarios involving three cancer types not seen during its training, achieving an average C-index of 0.717, thereby demonstrating its strong generalization capability that transcends organ- and subtype-specific boundaries. Moreover, BRIDGE-generated virtual spatial transcriptomes match the prognostic accuracy of bulk RNA-seq, highlighting their potential as a spatially informative alternative to laboratory sequencing. In general, BRIDGE represents a data-efficient tool in virtual ST that facilitates biomedical discoveries in clinical few-shot contexts and advances diagnosis of understudied cancers without sufficient samples.