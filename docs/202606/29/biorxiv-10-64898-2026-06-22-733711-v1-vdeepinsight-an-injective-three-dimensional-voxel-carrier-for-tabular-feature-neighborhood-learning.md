---
title: "vDeepInsight: an injective three-dimensional voxel carrier for tabular-feature neighborhood learning"
title_zh: "vDeepInsight: 一种用于表格特征邻域学习的单射三维体素载体"
authors: "Jia, S., Lysenko, A., Boroevich, K. A., Sharma, A., Tsunoda, T."
date: 2026-06-26
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.22.733711v1.full.pdf"
tags: ["query:spatialprot"]
score: 6.0
evidence: 将表格特征映射到3D体素空间，适用于空间蛋白质组学数据分析
tldr: 针对DeepInsight方法载体几何构建问题，提出vDeepInsight三维体素载体，通过t-SNE/UMAP嵌入特征并一对一分配到稀疏体素网格，使用子流形稀疏3D卷积网络。在基因表达分析中，3D布局减少邻域扭曲，在依赖基因程序的任务上超越2D载体和表格基线，同时保持可解释性。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有二维载体不能忠实保持特征邻域，当信号依赖于局部特征组时性能受限。
method: 使用t-SNE/UMAP嵌入基因，线性求和分配至稀疏三维体素网格，采用子流形稀疏3D卷积网络处理。
result: 3D载体在表示质量上减少邻域扭曲；在药物响应等程序型任务上超越2D载体和基线，在标记型任务上相当。
conclusion: 增加载体维度提升特征邻域表示保真度，在信号分布广泛的局部基因程序任务上带来最大预测增益。
---

## 摘要
DeepInsight类方法通过将每个特征放置在图像载体上的固定位置，使得表格特征关系可供卷积网络利用。一个开放的设计问题是，当特征邻域本身携带部分信号时，应如何构建载体的几何形状。我们引入了vDeepInsight，一种单射三维（3D）体素载体，它比匹配的二维（2D）载体更忠实地保留特征邻域，同时保持每个特征到单个体素的一一映射。基因通过t-SNE或UMAP嵌入，通过线性分配一一映射到稀疏体素网格，并由子流形稀疏3D卷积网络处理。我们通过四项关联分析评估该载体在基因表达上的表现。首先，表示质量指标表明，在训练任何模型之前，3D布局相对于匹配的2D布局减少了基因邻域失真。其次，受控合成任务表明，稀疏3D卷积可以利用这种保留的局部性，但仅当监督信号依赖于共定位基因且感受野跨越相邻体素时。第三，在真实组学任务上，3D载体的表现达到或超过调整后的表格基线，并持续优于匹配的2D载体；在标记型分类（组织、谱系和癌症类型分类）中，差异较小，因为单个基因已经携带了大部分标签信息；在程序型任务（药物反应回归、TCGA免疫基因组上下文回归和作用机制分类）中，差异较大，因为目标依赖于协调的、通路级别的多基因活动。第四，由于分配是单射的，体素注意力图直接映射回基因，从而实现基因级注意力和通路级功能解释，无需体素到基因的反卷积。总体而言，增加的载体维度改善了特征邻域表示的保真度，并将这种改进转化为预测增益，当信号分布在局部基因程序中而非由单个标记基因主导时，增益最大。

## Abstract
DeepInsight-style methods make tabular feature relationships accessible to convolutional networks by placing each feature at a fixed position on an image carrier. An open design question is how the carrier geometry should be constructed when feature neighborhoods themselves carry part of the signal. We introduce vDeepInsight, an injective three-dimensional (3D) voxel carrier that preserves feature neighborhoods more faithfully than matched two-dimensional (2D) carriers while keeping a one-to-one mapping from each feature to a single voxel. Genes are embedded with t-SNE or UMAP, assigned one-to-one to a sparse voxel grid by linear-sum assignment, and processed by a submanifold sparse 3D convolutional network. We evaluate the carrier on gene expression through four linked analyses. First, representation-quality metrics show that 3D layouts reduce gene-neighborhood distortion relative to matched 2D layouts before any model is trained. Second, controlled synthetic tasks show that a sparse 3D convolution can exploit this preserved locality, but only when the supervised signal is constructed to depend on co-located genes and the receptive field spans adjacent voxels. Third, on real omics tasks the 3D carrier matches or exceeds tuned tabular baselines and consistently exceeds matched 2D carriers; the margin is small on marker-type classification, where individual genes already carry much of the label (tissue, lineage and cancer-type classification), and larger on program-type tasks, where the target depends on coordinated, pathway-level multi-gene activity (drug-response regression, TCGA immunogenomic-context regression and mechanism-of-action classification). Fourth, because the assignment is injective, voxel attribution maps directly back to genes, enabling gene-level attribution and pathway-level functional interpretation without voxel-to-gene deconvolution. Overall, the added carrier dimension improves the fidelity of feature-neighborhood representation and translates this improvement into prediction gains that are largest when the signal is distributed across local gene programs rather than dominated by individual marker genes.