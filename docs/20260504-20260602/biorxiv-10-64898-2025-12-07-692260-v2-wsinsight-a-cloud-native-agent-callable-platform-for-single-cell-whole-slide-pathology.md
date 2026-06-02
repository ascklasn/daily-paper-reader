---
title: "WSInsight: a cloud-native, agent-callable platform for single-cell whole-slide pathology"
title_zh: "WSInsight: 一个云原生、可被智能体调用的单细胞全切片病理学平台"
authors: "Huang, C. H., Awosika, O. E., Fernandez, D."
date: 2026-05-10
pdf: "https://www.biorxiv.org/content/10.64898/2025.12.07.692260v2.full.pdf"
tags: ["query:pm"]
score: 8.0
evidence: 云原生平台用于全切片图像分析，具单细胞分辨率
tldr: 病理全切片图像分析需要对大规模队列进行单细胞分辨率的形态和分子表征，现有工具缺乏可扩展性。WSInsight作为一个开源、云原生的平台，创新性地整合patch级推理与可重训练的单细胞分割和表型分类头部，支持形态学和转录组监督。它从云端存储库读取切片，将结果写入QuPath和OMERO，并通过模型上下文协议（MCP）提供AI代理调用接口。在TCGA多个队列上的实验成功恢复了已知的免疫浸润和分子亚型关联，展示了其在大规模病理分析中的实用价值。
source: biorxiv
selection_source: fresh_fetch
motivation: 当前病理全切片图像分析缺乏面向大规模队列的单细胞分辨率开源平台，且难以与AI代理集成。
method: WSInsight基于patch级推理输出，结合可从公共数据重训练的形态学和转录组级联细胞类型头部，通过云存储读写并标准化输出。
result: 在TCGA多个癌症队列上成功复现了已知的免疫细胞浸润和分子亚型关联模式。
conclusion: 云原生、开源且支持AI代理调用的设计使得单细胞病理分析可扩展、可重现，促进转化研究。
---

## 摘要
WSInsight是一个开源平台，用于队列规模H&E全切片图像分析。它执行贴片级推理以及单细胞分割和表型分类，具有形态学和转录组监督的细胞类型头，可从公共数据重新训练。切片从云存储库读取，每个切片的输出写入QuPath和OMERO。同样的工作流可通过模型上下文协议端点被AI智能体调用。将其应用于TCGA队列恢复了已知的免疫和分子关联。

## Abstract
WSInsight is an open-source platform for cohort-scale H&E whole-slide image analysis. It performs patch-level inference together with single-cell segmentation and phenotype classification, with morphology- and transcriptome-supervised cell-type heads retrainable from public data. Slides are read from cloud repositories and per-slide outputs are written to QuPath and OMERO. The same workflow is AI-agent callable through a Model Context Protocol endpoint. Applying it to TCGA cohorts recovered known immune and molecular associations.