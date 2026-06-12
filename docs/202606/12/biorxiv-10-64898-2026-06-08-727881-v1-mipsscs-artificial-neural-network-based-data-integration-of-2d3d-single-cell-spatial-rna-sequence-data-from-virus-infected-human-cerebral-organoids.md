---
title: "MipSScs: Artificial neural network-based data integration of 2D/3D single-cell spatial RNA sequence data from virus-infected human cerebral organoids"
title_zh: MipSScs：基于人工神经网络的病毒感染人类脑类器官2D/3D单细胞空间RNA序列数据整合
authors: "Doddi, A. D., Dawes, P., Chan, Y., Lim, E. T."
date: 2026-06-11
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.08.727881v1.full.pdf"
tags: ["query:spatialprot"]
score: 6.0
evidence: 使用神经网络整合2D/3D单细胞空间RNA序列数据
tldr: 本研究利用HSV-1感染2D解离细胞和3D脑类器官模型，生成单细胞非空间和空间转录组数据。通过多层感知机(MLP)跨平台整合2D/3D数据，成功将类器官细胞类型高验证率映射至成人脑细胞。发现感染3D类器官中内皮细胞和星形胶质细胞最近邻距离显著聚集，且非整体密度差异所致。该工作证明人工神经网络在跨维度单细胞数据整合中的关键作用，有助于理解阿尔茨海默病等神经退行性疾病的病毒诱因。
source: biorxiv
selection_source: fresh_fetch
motivation: 利用HSV-1感染脑类器官模型研究AD相关分子转录组变化，需跨2D/3D平台的数据整合方法。
method: 对HSV-1感染2D dcOrgs和3D cOrgs进行单细胞非空间和空间RNA测序，使用MLP进行细胞类型注释，并用交叉验证评估。
result: MLP实现从2D/3D类器官到成人脑细胞的高验证率映射；感染3D cOrgs中内皮细胞和星形胶质细胞最近邻距离更聚集。
conclusion: 人工神经网络如MLP能有效整合2D和3D单细胞转录组数据，为神经疾病研究提供新见解。
---

## 摘要
近年来，单细胞空间转录组学技术被用于深入了解疾病机制。我们此前利用单纯疱疹病毒1型（HSV-1）诱导的人脑类器官2D解离细胞（dcOrgs）神经炎症模型，模拟与阿尔茨海默病（AD）相关的分子和转录组特征。在本研究中，我们通过单细胞非空间RNA测序和单细胞空间RNA测序技术，对HSV-1感染的2D dcOrgs和HSV-1感染的3D脑类器官（cOrgs）生成了两个数据集。利用人类胎儿脑和成人死后脑的单细胞非空间RNA序列数据，对2D dcOrgs和3D cOrgs中的细胞进行细胞类型注释，以推断通过病毒感染（与AD相关）引起的AD相关体外扰动的转录组效应。我们评估了计算和机器学习方法，包括使用多层感知机（MLPs），并以跨2D/3D平台比较作为基准来评估人工神经网络模型。在此过程中，我们发现使用MLPs可以从2D和3D人脑类器官中高验证率地将细胞类型身份分配至成人死后脑样本中发现的细胞类型。此外，这些技术和系统的应用使得识别与病毒转录生命周期相关的伪时间轨迹和细胞簇成为可能。我们鉴定了几种细胞类型，包括内皮细胞和星形胶质细胞，在感染的3D cOrgs中，这些细胞的细胞-细胞最近邻距离比模拟感染的3D cOrgs显著更聚集。置换检验表明，这些最近邻距离的差异不太可能由单个感染3D cOrgs与模拟3D cOrgs之间的整体结构差异（如细胞密度差异）驱动。鉴于与人类死后脑样本的单细胞空间（3D）RNA序列数据集相比，已有更多大规模单细胞非空间（2D）RNA序列数据集来自人类死后脑样本，因此利用人工神经网络（如MLPs）对来自人类死后脑样本及人类体外系统（如脑类器官）的2D和3D单细胞转录组数据集进行数据整合，可能对获得AD等神经退行性疾病的新见解至关重要。

## Abstract
There is interest in the use of recent single-cell spatial transcriptomic technologies to gain biological insights into disease mechanisms. Previously, we characterized the use of herpes simplex virus 1 (HSV-1) induced neuroinflammation in 2D dissociated cells from human cerebral organoids (dcOrgs) to model molecular and transcriptomic readouts associated with Alzheimers disease (AD). In this work, we generated two datasets by using single-cell non-spatial RNA sequencing and single-cell spatial RNA sequencing technologies on HSV-1-infected 2D dcOrgs and HSV-1-infected 3D cerebral organoids (cOrgs). We conducted cell type assignment for the cells in the 2D dcOrgs and 3D cOrgs, by using single-cell non-spatial RNA sequence data from human fetal brains and adult post-mortem brains, to infer the transcriptomic effects of AD-associated in-vitro perturbations through viral infections linked to AD. We evaluated computational and machine learning methods, including the use of multi-layer perceptrons (MLPs), and we used cross-2D/3D platform comparisons as a benchmark to evaluate the artificial neural network models. In the process, we found that the use of MLPs can lead to high validation rates for assigning cell type identities from 2D and 3D human cerebral organoids to cell types found in human adult post-mortem brain samples. Furthermore, the use of these technologies and systems enabled the identification of pseudotime trajectories and cell clusters associated with the viral transcriptional life cycle. We identified several cell types, including endothelial cells and astrocytes, with significantly more clustered cell-cell nearest neighbor distances in infected 3D cOrgs compared to mock 3D cOrgs. Permutation tests revealed that these differences in nearest neighbor distances are unlikely to be driven by overall structural differences between individual infected 3D cOrgs and mock 3D cOrgs, such as differences in the density of cells. Given that there are more large-scale single-cell non-spatial (2D) RNA sequence datasets that had been generated from human post-mortem brain samples, compared to single-cell spatial (3D) RNA sequence datasets from human post-mortem brain samples, the development of data integration approaches by using artificial neural networks such as MLPs, across 2D and 3D single-cell transcriptomics datasets generated from human post-mortem brain samples and human in-vitro systems such as brain organoids is likely to be critical to gain novel insights into neurodegenerative diseases such as AD.