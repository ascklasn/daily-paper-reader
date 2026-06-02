---
title: "WSInsight: a cloud-native, agent-callable platform for single-cell whole-slide pathology"
title_zh: WSInsight：一个云原生、可被AI代理调用的单细胞全切片病理学平台
authors: "Huang, C. H., Awosika, O. E., Fernandez, D."
date: 2026-05-17
pdf: "https://www.biorxiv.org/content/10.64898/2025.12.07.692260v3.full.pdf"
tags: ["query:pm"]
score: 9.0
evidence: 全切片图像分析平台，包含深度学习推理和单细胞分割
tldr: "构建云原生、可被AI智能体调用的病理全切片分析平台WSInsight，支持H&E切片的patch级推理、单细胞分割与表型分类，细胞类型头部可基于公开数据重训练。从云存储读取切片，输出到QuPath和OMERO。在TCGA队列中验证，成功复现已知免疫和分子关联，展示了可扩展的病理数据自动化分析能力。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有全切片分析平台缺乏云原生、可扩展及AI智能体调用能力，难以满足大规模队列分析需求。
method: 基于patch级推理与单细胞分割，设计可重训练的细胞类型分类头部，通过MCP协议支持AI智能体调用，集成云存储与开源工具。
result: 在TCGA队列上应用，成功复现已知的免疫浸润和分子分型关联，验证了平台的有效性和可扩展性。
conclusion: WSInsight为大规模病理图像分析提供了云原生、可调用的开源方案，助力探索组织形态与分子表型关系。
---

## 摘要
WSInsight是一个开源平台，用于大规模队列的H&E全切片图像分析。它执行斑块级推理，同时进行单细胞分割和表型分类，其形态学和转录组监督的细胞类型头可从公开数据重新训练。切片从云存储库读取，每个切片的输出写入QuPath和OMERO。相同的工作流可通过模型上下文协议端点被AI代理调用。将其应用于TCGA队列，恢复了已知的免疫和分子关联。

## Abstract
WSInsight is an open-source platform for cohort-scale H&E whole-slide image analysis. It performs patch-level inference together with single-cell segmentation and phenotype classification, with morphology- and transcriptome-supervised cell-type heads retrainable from public data. Slides are read from cloud repositories and per-slide outputs are written to QuPath and OMERO. The same workflow is AI-agent callable through a Model Context Protocol endpoint. Applying it to TCGA cohorts recovered known immune and molecular associations.