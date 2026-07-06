---
title: "PIGMENT: A deep learning framework for Porcine Immunohistochemistry seGMENTation"
title_zh: PIGMENT：用于猪免疫组织化学分割的深度学习框架
authors: "Ambastha, P., Dadashkarimi, J., Annavazala, S. K. C., Parker, D., Diaz-Arrastia, R., Song, H., Donahue, R. P., Smith, D. H., Dolle, J.-P., Johnson, V. E., Wolf, J. A., Verma, R."
date: 2026-06-29
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.18.733245v2.full.pdf"
tags: ["query:hmm"]
score: 8.0
evidence: 全切片免疫组化分割的深度学习框架
tldr: 创伤性脑损伤后APP免疫组化标记轴突损伤，但手动量化费时且主观。提出PIGMENT框架，基于SegFormer-B0架构，结合APP特异性数据增强，在少量专家标注上训练。在猪白质切片评估，平均实例级检测率0.86。该框架可生成全切片APP负荷图，为组织病理与影像关联研究提供可扩展方案。
source: biorxiv
selection_source: fresh_fetch
motivation: 解决APP病理手动量化耗时、可重复性差的问题，实现自动化分割。
method: 采用SegFormer-B0架构，结合APP特异性数据增强，在少量标注上训练。
result: 在猪白质切片上平均实例级检测率达0.86。
conclusion: PIGMENT可扩展生成全切片APP负荷图，促进组织病理与影像关联研究。
---

## 摘要
创伤性脑损伤会导致广泛的轴突损伤，可通过淀粉样前体蛋白（APP）免疫组织化学在组织学上评估，该技术能够以细胞分辨率标记受损的轴突轮廓[1,2]。然而，APP病理的量化仍是主要瓶颈：标注是手动的、耗时、空间局限且在不同评估者之间变异大，限制了可扩展性和可重复性。在使用组织学作为神经影像或其他组织水平测量参考的研究中，这一局限性尤为突出，因为细胞APP病理必须以能够与成像异常对齐的空间形式进行量化。

在此，我们介绍PIGMENT——一种用于自动分割和量化猪白质组织学中APP阳性病理的注释高效深度学习框架。PIGMENT采用紧凑的SegFormer-B0架构，使用来自三只猪的四个APP染色切片中的525个专家标注的512×512像素瓦片进行训练。由于APP阳性轮廓稀疏、碎片化、染色变异且形态多样，PIGMENT将有限的专家标签与专门针对APP的增强相结合，以模拟APP阳性强度、大小、连续性、碎片化和局部组织背景的变异。

我们使用实例级检测率评估PIGMENT，该指标衡量是否定位了离散的APP阳性组件。在保留的APP染色数据中，PIGMENT的平均实例级检测率达到0.86。在测试的配置中，包含来自不同动物切片的训练集实现了最高平均检测率，表明在有限标注条件下，标注多样性可能是一个重要因素。

通过将有限的高置信度专家标注扩展为全切片APP负担图，PIGMENT提供了一个可扩展的框架，用于表征创伤性轴突损伤的程度和空间分布。这些图谱可能支持未来将组织学损伤负担与成像衍生测量对齐的研究。

## Abstract
Traumatic brain injury produces widespread axonal damage can be assessed histologically using amyloid precursor protein (APP) immunohistochemistry, which labels injured axonal profiles at cellular resolution [1, 2]. However, quantification of APP pathology remains a major bottleneck: annotation is manual, time-consuming, spatially localized, and variable across raters, limiting scalability and reproducibility. This limitation is particularly important in studies that use histology as a reference for neuroimaging or other tissue-level measurements, where cellular APP pathology must be quantified in a spatial form that can be aligned with imaging abnormalities.

Here, we introduce PIGMENT, an annotation-efficient deep-learning framework for automated segmentation and quantification of APP-positive pathology in porcine white matter histology. PIGMENT uses a compact SegFormer-B0 architecture trained on 525 expert-annotated 512 x 512-pixel tiles from four APP-stained sections across three pigs. Because APP-positive profiles are sparse, fragmented, stain-variable, and morphologically diverse, PIGMENT combines limited expert labels with APP-specific augmentation designed to model variation in APP-positive intensity, size, continuity, fragmentation, and local tissue context.

We evaluated PIGMENT using an instance-level detection rate that measures whether discrete APP-positive components are localized. Across held-out APP-stained data, PIGMENT achieved a mean instance-level detection rate of 0.86. Across the configurations tested, the highest mean detection rate was achieved by a training set that included sections from different animals, suggesting that annotation diversity may be an important factor under limited-label conditions.

By extending limited high-confidence expert annotations into whole-section APP burden maps, PIGMENT provides a scalable framework for characterizing the extent and spatial distribution of traumatic axonal injury. These maps may support future studies that align histological injury burden with imaging-derived measures.