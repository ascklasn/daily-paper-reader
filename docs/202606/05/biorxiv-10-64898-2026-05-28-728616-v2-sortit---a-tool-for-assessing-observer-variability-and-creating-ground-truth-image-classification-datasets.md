---
title: SortIT - A Tool For Assessing Observer Variability And Creating Ground Truth Image Classification Datasets
title_zh: SortIT——评估观察者变异性和创建基准真值图像分类数据集的工具
authors: "Uegami, W., Bisson, T., Okoshi, E. N., Costa da Silva, F. G., Munkhdelger, J., Lami, K., Zerbe, N., Bychkov, A., Fukuoka, J."
date: 2026-06-02
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.28.728616v2.full.pdf"
tags: ["query:hmm"]
score: 6.0
evidence: 用于创建全切片图像分析金标准数据集的工具
tldr: 病理诊断中观察者间变异严重影响诊断可靠性。AI技术虽有望标准化，但需高质量共识数据集。SortIT是一个开源Web应用，支持多位标注者独立标注病理图块，通过统计分析可视化和量化变异，并利用共识标注构建地面真值。在三个用例中成功应用，包括有丝分裂分割、前列腺癌分级和肉芽肿分类。该工具易于部署，为开发稳健的AI诊断工具提供了关键基础设施。
source: biorxiv
selection_source: fresh_fetch
motivation: 病理诊断中观察者变异挑战诊断可靠性，需系统方法创建共识地面真值以减少AI模型训练偏差。
method: SortIT开源Web应用，支持多标注者独立标注病理图块，灵活权限控制，导出数据用于变异分析与共识构建。
result: 通过有丝分裂分割、前列腺癌分级和肉芽肿分类三个用例验证，有效量化观察者变异并生成可靠地面真值数据集。
conclusion: SortIT易部署开源，助力高质量地面真值创建，推动病理AI诊断工具标准化与泛化性提升。
---

## 摘要
病理评估中的观察者间变异性是一个公认的挑战，影响诊断可靠性和疾病理解。由于评估的主观性，这种变异性存在于许多亚专业领域。应用于全切片图像的人工智能有潜力标准化流程并减少病理学中的变异性，但过渡到这些技术并不能保证改进。建立带有共识注释的可靠基准真值数据集对于开发稳健的人工智能解决方案至关重要。我们推出SortIT，这是一个开源网络应用程序，便于系统性地创建和评估基准真值图像块注释。SortIT允许多个注释者独立标记图像块，并具有灵活的用户权限控制。注释数据可以导出，用于观察者变异的统计分析以及从共识图像块创建基准真值数据集。我们概述了使用SortIT的几个用例协议：(1) 肿瘤区域中的有丝分裂分割，(2) 通过与专家共识比较来评估前列腺癌分级的人工智能解决方案，以及(3) 通过注释判别性图像块级别特征进行肉芽肿分类。SortIT的主要优势在于其易于部署，使其对广泛用户群体可访问且易用。总体而言，SortIT为建立高质量的基准真值数据集和全面评估观察者变异性提供了有价值的工具。使用系统化注释方法对基准真值质量进行批判性评估，对于开发准确且可推广的诊断人工智能工具至关重要。其开源特性促进了社区的采用和进一步开发。

## Abstract
Interobserver variability in pathological assessments is a well-recognized challenge that impacts diagnostic reliability and disease understanding. This variability exists across many subspecialties due to the subjective nature of evaluations. Artificial intelligence (AI) applied to whole slide images has potential to standardize procedures and reduce variability in pathology, but transitioning to these technologies does not guarantee improvement. Establishing reliable ground truth datasets with consensus annotations is crucial for developing robust AI solutions. We introduce SortIT, an open-source web application that facilitates systematic creation and evaluation of ground truth image tile annotations. SortIT enables multiple annotators to independently label tiles, with flexible user permission controls. Annotated data can be exported for statistical analysis of observer variation and for creating ground truth datasets from consensus tiles. We outline protocols using SortIT for several use cases: (1) mitosis segmentation in tumor regions, (2) evaluating AI solutions for prostate cancer grading by comparing to expert consensus, and (3) granuloma classification by annotating discriminative tile-level features. Key strengths of SortIT lies in its ease of deployment, making it accessible and usable for a wide range of users. Overall, SortIT provides a valuable tool to establish high-quality ground truth datasets and comprehensively assess observer variability. Critical evaluation of ground truth quality using systematic annotation methodologies is crucial for developing accurate and generalizable diagnostic AI tools. Its open-source nature facilitates community adoption and further development.