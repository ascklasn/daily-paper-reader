---
title: "OmicsNavigator: An auditable scientific partner for scalable hypothesis validation in spatial omics"
title_zh: OmicsNavigator：用于空间组学中可扩展假设验证的可审计科学伙伴
authors: "Li, Y., Vakharia, N., Liang, W., Mayer, A. T., Luo, R., Trevino, A. E., Wu, Z."
date: 2026-06-14
pdf: "https://www.biorxiv.org/content/10.1101/2025.07.21.665821v2.full.pdf"
tags: ["query:spatialprot"]
score: 8.0
evidence: 基于大语言模型的空间组学假设验证系统
tldr: 空间组学数据的高维性和多模态特性导致生物学发现瓶颈。本文提出OmicsNavigator，一种基于大语言模型的自主系统，能直接推理空间组学的视觉和分子特征，实现知识引导的结构注释和零样本语义检索。系统通过预注册、人工审计的蓝图进行客观假设验证，在糖尿病肾病、肾移植排斥和COVID-19肺病理数据上生成循证见解。该方法为空间组学分析提供了可扩展、可解释且模态无关的解决方案。
source: biorxiv
selection_source: fresh_fetch
motivation: 高维空间分子数据难以转化为可检验的生物学发现，亟需可扩展且可解释的分析工具。
method: OmicsNavigator利用大语言模型直接推理空间组学的多模态输入，通过文本化高维数据实现零样本语义检索和假设验证。
result: 系统在糖尿病肾病等病理数据上成功重建疾病谱，并生成人类可读的循证见解，验证了跨数据集的有效性。
conclusion: OmicsNavigator提供了模态无关、可扩展且可审计的空间组学分析框架，有望加速空间生物学发现。
---

## 摘要
将高维、空间分辨的分子数据集转化为可验证的生物学发现仍是主要研究瓶颈。本文提出OmicsNavigator，一个自主的大语言模型驱动系统，用于空间组学数据的端到端数据探索和假设验证。OmicsNavigator直接对空间组学数据的多模态输入（包括视觉和分子特征）进行推理，以执行知识引导的空间结构注释。我们证明，通过将高维数据转化为文本解释，OmicsNavigator能够实现组织生物标志物的零样本语义检索，并从原始组学观察中重建患者级疾病谱。此外，OmicsNavigator具有一个由预注册、人工审计蓝图控制的目标假设验证引擎。通过在包括糖尿病肾病、肾移植排斥和COVID-19肺部病理等多种病理条件的数据集上验证系统，我们证明OmicsNavigator能从空间组学数据生成基于证据、人类可读的见解，具有加速空间生物学发现的潜力。OmicsNavigator为空间组学分析提供了可扩展、可解释且与模态无关的解决方案。

## Abstract
Translating high-dimensional, spatially resolved molecular datasets into testable biological findings remains a major research bottleneck. Here, we present OmicsNavigator, an autonomous large language model-powered system for end-to-end data exploration and hypothesis validation on spatial omics data. OmicsNavigator reasons directly over the multi-modal inputs of spatial omics data, including visual and molecular signatures, to perform knowledge-guided annotation of spatial structures. We show that by transforming high-dimensional data into textual interpretations, OmicsNavigator enables zero-shot semantic retrieval of tissue biomarkers and the reconstruction of patient-level disease profiles from raw omics observations. Furthermore, OmicsNavigator features an objective hypothesis validation engine governed by pre-registered, human-audited blueprints. By validating the system across datasets spanning diverse pathological conditions including diabetic kidney disease, kidney transplant rejection, and COVID-19 pulmonary pathology, we demonstrate that OmicsNavigator generates evidence-based, human-readable insights from spatial omics data, with potential to accelerate spatial biology discoveries.OmicsNavigator offers a scalable, interpretable, and modality-agnostic solution for spatial omics analysis.