---
title: "WSInsight: a cloud-native, agent-callable platform for single-cell whole-slide pathology"
title_zh: WSInsight：一个云原生、可被智能体调用的单细胞全切片病理学平台
authors: "Huang, C. H., Awosika, O. E., Fernandez, D."
date: 2026-05-10
pdf: "https://www.biorxiv.org/content/10.64898/2025.12.07.692260v2.full.pdf"
tags: ["query:agent"]
score: 9.0
evidence: 可被AI智能体调用的全切片病理分析平台
tldr: 全切片病理分析面临高分辨率单细胞级分析需求。WSInsight作为云原生平台，实现补丁级推理、单细胞分割与表型分类，细胞类型头可基于公共数据重训练，并通过MCP端点支持AI代理调用。在TCGA队列中应用，成功恢复已知免疫细胞浸润与分子亚型关联。该开源平台整合云存储与标准输出，为大规模病理分析提供可扩展、可调用的新范式。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有病理分析平台缺乏云原生和AI代理调用能力，难以高效进行大规模单细胞级全切片分析。
method: 采用补丁级推理结合单细胞分割与表型分类，使用形态与转录组监督的可重训练细胞类型头；从云存储读取切片，输出至QuPath和OMERO，通过MCP端点支持AI代理调用。
result: 在TCGA多个癌种队列中应用，成功复现已知的免疫细胞浸润模式和分子亚型关联。
conclusion: WSInsight作为开源云原生平台，通过可调用接口实现单细胞全切片分析，为大规模病理学与AI集成提供新方案。
---

## 摘要
WSInsight是一个用于队列规模H&E全切片图像分析的开源平台。它执行补丁级推理，同时进行单细胞分割和表型分类，并具有可从公共数据重新训练的形态学和转录组监督的细胞类型头。切片从云存储库读取，每个切片的输出写入QuPath和OMERO。同一工作流可通过模型上下文协议端点被AI智能体调用。将其应用于TCGA队列恢复了已知的免疫和分子关联。

## Abstract
WSInsight is an open-source platform for cohort-scale H&E whole-slide image analysis. It performs patch-level inference together with single-cell segmentation and phenotype classification, with morphology- and transcriptome-supervised cell-type heads retrainable from public data. Slides are read from cloud repositories and per-slide outputs are written to QuPath and OMERO. The same workflow is AI-agent callable through a Model Context Protocol endpoint. Applying it to TCGA cohorts recovered known immune and molecular associations.