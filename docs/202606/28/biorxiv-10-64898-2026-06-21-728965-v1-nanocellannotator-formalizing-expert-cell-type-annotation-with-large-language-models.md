---
title: "NanoCellAnnotator: Formalizing Expert Cell Type Annotation with Large Language Models"
title_zh: NanoCellAnnotator：利用大型语言模型形式化专家细胞类型注释
authors: "Mahmud, M. I., Kochat, V., Anzum, H., Satpati, S., Dwarampudi, J. M. R., Rai, K., Banerjee, T."
date: 2026-06-25
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.21.728965v1.full.pdf"
tags: ["query:spatialprot"]
score: 6.0
evidence: 利用LLM进行空间转录组细胞类型注释
tldr: 空间转录组细胞类型注释面临稀疏基因面板和组织参考图谱有限等挑战，现有LLM方法易产生生物不合理预测和幻象。NanoCellAnnotator通过混合空间正则化NMF发现空间簇，基于GO富集构建功能程序，并利用轻量级本地语言模型在受限标签空间中进行约束标签选择。该框架在胆管癌和乳腺癌数据集上高置信度恢复典型细胞群，同时明确标记异质性区域。其解耦设计和置信度评估提升了注释的可重复性和隐私保护。
source: biorxiv
selection_source: fresh_fetch
motivation: 空间转录组细胞注释因参考图谱稀缺和LLM幻象而不可靠，亟需生物约束和置信度感知的方法。
method: 采用hSNMF识别空间簇，通过GO-slim投影抽象出功能程序，再用轻量级语言模型在PanglaoDB和CellMarker衍生标签空间中选择。
result: 在胆管癌和乳腺癌数据上，准确恢复典型细胞群并识别异质性区域，与手动注释一致性高。
conclusion: 提供生物约束且置信度感知的注释框架，提升了可重复性和隐私友好性。
---

## 摘要
动机：空间转录组学中的细胞类型注释由于基因面板稀疏、空间异质性以及组织匹配参考图谱的有限可用性而具有挑战性。最近的方法探索了利用大型语言模型（LLMs）在注释过程中整合生物学知识，但无约束的推理可能产生生物学上不支持的预测和虚构的细胞类型。此外，许多基于LLM的流程依赖于大型云托管模型，这限制了在隐私敏感环境中的可重复性和部署。结果：我们介绍了NanoCellAnnotator，一个生物约束且置信度感知的框架，用于空间转录组学中自动细胞类型注释。该框架解耦了空间结构发现、确定性生物学证据构建和基于语言模型的语义推理。使用混合空间正则化非负矩阵分解（hSNMF）识别空间聚类，然后通过基因本体富集和GO-slim投影将聚类级别的标记基因抽象为本体衍生的功能程序。一个轻量级本地可执行语言模型在来自PanglaoDB和CellMarker的策展可允许标签空间内执行受限标签选择。注释置信度使用标记支持强度和谱系分离独立估计，使得可以明确标记模糊或异质聚类。我们在肝内胆管癌的Xenium空间转录组数据和一个独立的乳腺癌空间转录组数据集上评估了NanoCellAnnotator。该框架以高置信度恢复典型细胞群体，同时将异质或过渡空间域识别为模糊。使用准确性和调整兰德指数评估与手动注释的一致性。可用性：代码可在https://github.com/ishtyaqmahmud/NanoCellAnnotator获取。

## Abstract
Motivation: Cell-type annotation in spatial transcriptomics is challenging due to sparse gene panels, spatial heterogeneity, and limited availability of tissue-matched reference atlases. Recent approaches have explored large language models (LLMs) for integrating biological knowledge during annotation, but unconstrained inference can produce biologically unsupported predictions and hallucinated cell types. In addition, many LLM-based pipelines rely on large cloud-hosted models that limit reproducibility and deployment in privacy-sensitive environments. Results: We introduce NanoCellAnnotator, a biologically constrained and confidence-aware framework for automated cell-type annotation in spatial transcriptomics. The framework de-couples spatial structure discovery, deterministic biological evidence construction, and language model-based semantic inference. Spatial clusters are identified using hybrid spatially regularized non-negative matrix factorization (hSNMF), after which cluster-level marker genes are abstracted into ontology-derived functional programs using Gene Ontology enrichment and GO-slim projection. A lightweight locally executable language model performs constrained label selection within a curated admissible label space derived from PanglaoDB and CellMarker. Annotation confidence is estimated independently using marker support strength and lineage separation, enabling ambiguous or heterogeneous clusters to be explicitly flagged. We evaluate NanoCellAnnotator on Xenium spatial transcriptomics data from intrahepatic cholangiocarci-noma and an independent breast cancer spatial transcriptomics dataset. The framework recovers canonical cell populations with high confidence while identifying heterogeneous or transitional spatial domains as ambiguous. Agreement with manual annotations was evaluated using accuracy and adjusted Rand index. Availability: Code available at https://github.com/ishtyaqmahmud/NanoCellAnnotator.