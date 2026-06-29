---
title: "Enterprise Health Twins - Conceptual Framework, Design Principles,and Longitudinal Evaluation: Preliminary Results from EpiToMe"
title_zh: 企业健康孪生 - 概念框架、设计原则与纵向评估：来自EpiToMe的初步结果
authors: "ZHANG, G.-Q., Cui, L., Lhatoo, S., Chou, W.-C., Hampson, J., Tao, S."
date: 2026-06-23
pdf: "https://www.biorxiv.org/content/10.64898/2025.12.06.692733v3.full.pdf"
tags: ["query:agent"]
score: 6.0
evidence: 使用数字孪生框架的临床决策支持系统
tldr: "传统电子健康记录架构与专科临床工作流不匹配，导致医生倦怠和二次数据利用困难。本文提出企业健康孪生（EHT）框架，基于数字孪生概念，将静态临床台账转化为动态决策支持系统，通过连续双向反馈连接临床工作流实体与数字接口。在德州大学休斯顿癫痫中心7年产线部署中，手术评估吞吐量提升约400%，无需增加人员，并在点医疗捕获本体锚定的结构化数据，降低认知负荷，推动学习医疗系统护理速度提升。"
source: biorxiv
selection_source: fresh_fetch
motivation: 解决单体式EHR架构与高分辨率专科临床工作流不匹配导致的医生倦怠和数据二次利用挑战。
method: 提出企业健康孪生（EHT）框架，构建物理工作流与数字孪生间的连续双向反馈（前馈摄入与后馈决策支持）。
result: "在癫痫中心7年产线部署中，手术评估吞吐量提升约400%，无需增加人员，并捕获本体锚定结构化数据。"
conclusion: EHT框架能有效提升专科医疗效率和数据质量，推动学习医疗系统的发展。
---

## 摘要
单体式电子健康记录（EHR）架构仍与高分辨率、专科化的临床工作流程从根本上不匹配，导致医生职业倦怠严重以及数据二次利用面临挑战。本研究引入了企业健康孪生（EHT）框架，这是一种基于数字孪生概念的范式，目标是将静态临床记录转变为动态决策支持系统。EHT在临床工作流程的物理实体与反映工作流程不断演变状态的界面数字副本之间建立了连续的双向反馈（前馈摄取和后馈决策支持），针对EHT中每位个体患者。我们在癫痫护理领域对EHT框架进行了概念化、原型设计、并实际运行了七年，在生产环境中、在护理点。部署于德克萨斯大学健康科学中心休斯顿分校癫痫中心，在未增加人员的情况下，专科手术评估吞吐量提高了约400%。EHT在护理点实现了基于本体的结构化数据的新生捕获，减轻了认知负荷，同时增加了用于临床研究的高分辨率、带注释的纵向数据集的规模，并在学习型医疗系统中推动了护理速度的提升。

## Abstract
Monolithic Electronic Health Record (EHR) architectures remain fundamentally misaligned with high-resolution, specialty-specific clinical workflows, contributing to significant physician burnout and challangies in secondary use of data. This study introduces the Enterprise Health Twin (EHT) framework, a paradigm grounded in the Digital Twin concept, with the goal to transform static clinical ledgers into dynamic decision-support systems. The EHT establishes continuous bidirectional feedback (feed-forward ingestion and feed-backward decision support) between the physical entities of clinical workflows and the digital counterparts of interfaces reflecting the evolving states of the workflow, for each individual patient in the EHT. We conceptualized, prototyped, and operationalized the EHT framework for epilepsy care for seven years, in production, at the point of care. Deployed at the Epilepsy Center of the University of Texas Health Science Center at Houston, a [~]400% increase productivity has been achieved in specialized surgical evaluation throughput without additional staffing. The EHT achieved de novo capture of ontology-anchored structured data at the point of care, mitigating cognitive load while growing the volume of high-resolution, annotated longitudinal datasets for clinical research, and driving an increase of care velocity in a learning healthcare system.