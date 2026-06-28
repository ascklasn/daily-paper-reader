---
title: "Enterprise Health Twins - Conceptual Framework, Design Principles,and Longitudinal Evaluation: Preliminary Results from EpiToMe"
title_zh: 企业健康孪生——概念框架、设计原则与纵向评估：来自EpiToMe的初步结果
authors: "ZHANG, G.-Q., Cui, L., Lhatoo, S., Chou, W.-C., Hampson, J., Tao, S."
date: 2026-06-23
pdf: "https://www.biorxiv.org/content/10.64898/2025.12.06.692733v3.full.pdf"
tags: ["query:agent"]
score: 6.0
evidence: 企业健康孪生框架作为动态决策支持系统
tldr: "传统EHR架构与临床工作流脱节导致医生倦怠和数据利用困难。本研究提出企业健康孪生（EHT）框架，基于数字孪生构建临床物理实体与数字接口的双向反馈。在癫痫中心部署七年，手术评估吞吐量提升约400%，并实时捕获本体锚定的结构化数据。该框架减轻认知负荷、加速护理速度，推动学习型医疗系统发展。"
source: biorxiv
selection_source: fresh_fetch
motivation: 传统EHR架构与高分辨率专科工作流不匹配，造成医生倦怠和二次利用困难，亟需动态决策支持系统。
method: 基于数字孪生，构建EHT框架实现临床工作流物理实体与数字接口的连续双向反馈（前馈摄入和后馈决策支持）。
result: "在德州大学癫痫中心部署七年，手术评估吞吐量提升约400%，并捕获本体锚定的结构化数据。"
conclusion: EHT框架有效提升效率、减轻认知负荷，推动学习型医疗系统的数据增长和护理加速。
---

## 摘要
单体电子健康记录架构本质上与高分辨率、专科特定的临床工作流程不匹配，导致医生严重倦怠和数据的二次使用困难。本研究引入企业健康孪生框架——一种基于数字孪生概念的范式，旨在将静态临床记录转变为动态决策支持系统。企业健康孪生建立了临床工作流程物理实体与反映工作流程演变状态的数字孪生界面之间的连续双向反馈（前馈输入和反馈决策支持），针对企业健康孪生中的每位患者。我们围绕癫痫护理，在临床一线生产环境中历时七年完成了企业健康孪生框架的概念化、原型构建和实际运行。部署在休斯顿得克萨斯大学健康科学中心癫痫中心后，在未增加额外人员的情况下，专科手术评估效率提升了约400%。企业健康孪生实现了在临床一线原生采集基于本体的结构化数据，减轻认知负荷的同时增加了高分辨率、带注释的纵向临床研究数据集规模，并在学习型医疗系统中推动了护理速度的提升。

## Abstract
Monolithic Electronic Health Record (EHR) architectures remain fundamentally misaligned with high-resolution, specialty-specific clinical workflows, contributing to significant physician burnout and challangies in secondary use of data. This study introduces the Enterprise Health Twin (EHT) framework, a paradigm grounded in the Digital Twin concept, with the goal to transform static clinical ledgers into dynamic decision-support systems. The EHT establishes continuous bidirectional feedback (feed-forward ingestion and feed-backward decision support) between the physical entities of clinical workflows and the digital counterparts of interfaces reflecting the evolving states of the workflow, for each individual patient in the EHT. We conceptualized, prototyped, and operationalized the EHT framework for epilepsy care for seven years, in production, at the point of care. Deployed at the Epilepsy Center of the University of Texas Health Science Center at Houston, a [~]400% increase productivity has been achieved in specialized surgical evaluation throughput without additional staffing. The EHT achieved de novo capture of ontology-anchored structured data at the point of care, mitigating cognitive load while growing the volume of high-resolution, annotated longitudinal datasets for clinical research, and driving an increase of care velocity in a learning healthcare system.