---
title: "Quantifying the Localization of Histological Staining Markers within the GI Epithelial Unit Axis: A Gastrointestinal Spatial Pathology Plugin for ImageJ"
title_zh: 量化组织学染色标记在胃肠道上皮单位轴内的定位：一个用于ImageJ的胃肠道空间病理学插件
authors: "Dey, A., Weis, J. A., Weis, V. G."
date: 2026-06-01
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.28.728613v1.full.pdf"
tags: ["query:spatialprot"]
score: 7.0
evidence: 空间病理学插件用于组织学分析
tldr: 胃肠组织学分析常依赖人工评分，缺乏空间定量评估。为此开发了一个开源ImageJ插件，通过手动标注上皮单元基底和顶端地标及阳性细胞坐标，计算其归一化轴向距离。该插件可生成直方图，量化细胞定位模式，支持EdU检测、迁移距离等分析。它提供了一个用户友好、可批量处理的解决方案，有助于深入理解胃肠上皮结构的空间生物学。
source: biorxiv
selection_source: fresh_fetch
motivation: 传统组织学半定量分析缺乏对胃肠上皮单元轴内空间定位的精确评估。
method: 基于ImageJ开发插件，手动标注上皮单元基底和顶端地标及兴趣点坐标，计算绝对与归一化距离。
result: 输出兴趣点坐标、绝对和归一化距离，生成直方图，实现细胞定位的量化统计。
conclusion: 该开源插件提供半自动化、可大规模应用的空间分析工具，助力胃肠病理学研究。
---

## 摘要
组织学分析对于理解胃肠道稳态和疾病病理生理学至关重要。在研究中，各种组织学染色常用于评估发育、疾病发病机制和治疗效果。特别是在有序结构的胃肠道上皮中，当前的半定量组织学染色分析主要依赖于手动评分标准，且往往缺乏稳健的空间评估。为弥补这一不足，我们开发了一个开源的ImageJ插件，基于其闭源前身，旨在分析用户定义的兴趣点（例如阳性染色细胞）沿胃肠道上皮单位的空间定位模式。该插件使用ImageJ 1.53.0和Eclipse中的Java编程语言开发，与ImageJ交互，并利用Java库进行数据处理。工作流程包括上传目标胃肠道组织的显微镜图像，通过手动识别确定胃肠道上皮单位的基部和顶部方向标记，并使用ImageJ注释兴趣点坐标。输出包括每个兴趣点的质心坐标、兴趣点到基部和顶部标记的绝对距离，以及兴趣点相对于胃肠道单位总高度的归一化距离。插件生成直方图以显示沿胃肠道单位轴的平均兴趣点距离。这些信息有助于量化总兴趣点计数、分析胃肠道单位内的高度定位，以及确定平均胃肠道单位高度。该插件是稳健评估胃肠道内各种生物学机制的关键工具，包括EdU定位、迁移距离、细胞类型定位变化以及沿胃肠道单位轴识别新表达模式。总体而言，这个开源的ImageJ插件提供了一个半自动化、用户友好的解决方案，用于从胃肠道结构架构中组织学染色表达模式的空间定位中获得重要见解，并具有简化的后处理流程，用于稳健的大规模分析。

## Abstract
Histological analysis is crucial for understanding gastrointestinal (GI) tract homeostasis and disease pathophysiology. Various histological stains are commonly used in research settings for assessing development, disease pathogenesis, and therapeutic impacts. Specifically in the ordered architecture of the GI epithelium, current semi-quantitative analysis of histological staining relies heavily on manual scoring rubrics and often lacks robust spatial assessment. To address this gap, we developed an open-source ImageJ plugin, building on a closed-source predecessor, aimed at analyzing the spatial localization pattern of user-defined points-of-interest, such as positively stained cells, along the GI epithelial units. The plugin, developed using ImageJ 1.53.0 and Java programming language in Eclipse, interfaces with ImageJ and leverages Java libraries for data processing. The workflow involves uploading a microscopy image of the GI tissue of interest, determining base and top orientation landmarks of the GI epithelial units through manual identification, and annotating point-of-interest coordinates using ImageJ. The output includes centroid coordinates for each point-of-interest, the absolute distances of the points from the base and top landmarks, and the normalized distances of the points relative to the total height of the GI unit. The plugin generates histograms for displaying average point-of-interest distances along the GI unit axis. This information facilitates quantification of total points-of interest counts, analysis of height localization within the GI unit, and determination of average GI unit heights. The plugin serves as a crucial tool for robustly assessing various biological mechanisms within the GI tract, including EdU localization, migration distances, changes in cell type localization, and identification of new expression patterns along the GI unit axis. Overall, this open-source ImageJ plugin provides a semi-automated, user-friendly solution for leveraging important insights into spatial localization of tissue histology expression patterns within the GI structured architecture, with streamlined post-processing pipelines for robust large-scale analysis.