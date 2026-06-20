---
title: "Vessel Spatial Analysis (VeSpA): a tool for whole slide image segmentation, morphometry, and QuPath extension."
title_zh: 血管空间分析（VeSpA）：一种用于全切片图像分割、形态测量和QuPath扩展的工具
authors: "Grion, G., Hussain, R., Colella, F. E., Roufail, K., Uccella, S., Frapolli, R., Matteo, C., Mintemur, O., Pennati, F., Renne, S. L."
date: 2026-06-20
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.15.732366v1.full.pdf"
tags: ["query:spatialprot"]
score: 8.0
evidence: VeSpA工具用于WSI中血管自动分割和空间分析
tldr: 血管空间分析在组织学和肿瘤微环境研究中至关重要，但现有工具操作繁琐或缺乏平台集成。VeSpA是一种开源的QuPath扩展，通过CMYK黄色通道提取和可选DAB反卷积实现CD31染色全切片图像的自动血管分割与形态测量。经独立病理学家验证，其在重叠度量上优于SAM和YOLOv8-seg，为计算病理学提供了可重复的血管定量流程。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有血管分析工具多依赖手动操作或编程技能，且缺少与数字病理平台的直接集成，亟需自动化、易用的解决方案。
method: VeSpA采用CMYK黄色通道提取（默认）或H-DAB图像的反卷积进行信号提取，结合阈值分割、形态学细化、轮廓滤波与管腔填充生成血管掩模。
result: 在测试数据集上，VeSpA的分割性能接近独立病理学家间的一致性，并在基于重叠的指标上优于黄色通道提示的SAM和零样本YOLOv8-seg。
conclusion: VeSpA将血管分割、形态测量与QuPath可视化整合为单一可重复工作流，适用于计算病理学和组织空间分析。
---

## 摘要
量化组织病理学全切片图像中的血管结构对于研究组织组织、肿瘤微环境生物学以及疾病相关的血管重塑至关重要。然而，常规免疫组织化学中的血管分析仍面临挑战。现有工作流程通常依赖手动操作、需要编程专业知识，或缺乏与数字病理学平台的直接集成。我们开发了VeSpA（血管空间分析），这是一个开源流水线和QuPath扩展，用于在CD31染色的全切片图像中进行自动化血管分割和形态测量量化。VeSpA结合了可配置的信号提取（默认使用CMYK黄色通道提取，对于H-DAB图像可选DAB染色去卷积）、基于自动或百分位数的阈值化、形态学细化、轮廓过滤和管腔填充，从标准DAB染色切片生成血管掩膜。QuPath扩展包括一个图形界面，用于选择标注、TMA核心或全图像，配置分割参数，运行Python后端，并将血管对象直接导入QuPath层次结构。对于每个检测到的血管，VeSpA提取面积、长轴长度、短轴长度、偏心率、质心和取向，同时将汇总测量结果附加到父标注和TMA核心。与独立病理学家标注的验证表明，VeSpA实现了接近评分者间一致性的分割性能，并且在测试数据集的基于重叠的指标上优于基于黄色通道提示的SAM和零样本YOLOv8-seg。VeSpA将血管分割、形态测量特征提取和基于QuPath的可视化整合到一个可重复的工作流程中，用于计算病理学中的血管量化以及组织结构的空间分析。

## Abstract
Quantifying vascular architecture in histological whole slide images is needed to study tissue organisation, tumour microenvironment biology, and disease-associated vascular remodelling. However, vessel analysis in routine immunohistochemistry remains challenging. Available workflows are often manual, require programming expertise, or lack direct integration with digital pathology platforms. We developed VeSpA (Vessel Spatial Analysis), an open-source pipeline and QuPath extension for automated vessel segmentation and morphometric quantification in CD31-stained whole slide images. VeSpA combines configurable signal extraction, using CMYK Yellow channel extraction by default and optional DAB stain deconvolution for H-DAB images, with automatic or percentile-based thresholding, morphological refinement, contour filtering, and lumen filling to generate vessel masks from standard DAB-stained sections. The QuPath extension includes a graphical interface for selecting annotations, TMA cores, or whole images, configuring segmentation parameters, running the Python backend, and importing vessel objects directly into the QuPath hierarchy. For each detected vessel, VeSpA extracts area, major axis length, minor axis length, eccentricity, centroid, and orientation, while also appending summary measurements to parent annotations and TMA cores. Validation against independent pathologist annotations showed that VeSpA achieved segmentation performance close to inter-rater agreement and outperformed yellow channel prompt-based SAM and zero-shot YOLOv8-seg on overlap-based metrics in the tested dataset. VeSpA integrates vessel segmentation, morphometric feature extraction, and QuPath-based visualisation into a single reproducible workflow for vascular quantification in computational pathology and spatial analysis of histological tissue architecture.