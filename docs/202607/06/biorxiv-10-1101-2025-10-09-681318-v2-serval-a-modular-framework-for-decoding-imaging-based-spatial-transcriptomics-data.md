---
title: "Serval: A modular framework for decoding imaging based spatial transcriptomics data"
title_zh: Serval：一个用于解码基于成像的空间转录组数据的模块化框架
authors: "Tsui, J., Adam, N., Choi, W., Liu, L. Y., Flores, C., Ansari, S., Kong, E., Thapliyal, Y., Lee, H., Haider, S., Von Riedemann, I., O'Flanagan, C., IMAXT Cancer Grand Challenges Consortium,, Aparicio, S., Roth, A."
date: 2026-06-29
pdf: "https://www.biorxiv.org/content/10.1101/2025.10.09.681318v2.full.pdf"
tags: ["query:spatialprot"]
score: 7.0
evidence: 用于解码成像型空间转录组数据的模块化框架
tldr: 成像型空间转录组学的解码准确性依赖于从荧光模式重建条形码。现有解码方法缺乏系统性基准测试。Serval是一个模块化框架，将解码阶段分为独立模块，支持灵活集成算法。基于该框架开发的Cosine解码器优化余弦相似度，在MERFISH和DART-FISH数据上提高了转录本恢复率和与表达参考的相关性，并促进复杂生物结构的注释。总之，Serval提供平台无关的基准测试支持更准确的空间转录组学分析。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有解码方法缺乏系统基准测试，影响下游分析准确性。
method: 提出Serval模块化框架，将解码阶段分离为独立模块；开发Cosine解码器优化余弦相似度。
result: 在MERFISH和DART-FISH数据上，Cosine解码器提高转录本恢复率和与表达参考的相关性，增强聚类稳定性。
conclusion: Serval框架支持平台无关的基准测试，推动更准确的空间转录组分析。
---

## 摘要
基于成像的空间转录组技术为研究完整组织内的细胞组织和基因表达开辟了新途径。然而，下游分析的准确性关键取决于解码步骤，该步骤从荧光模式中重建条形码并将其映射到基因身份。尽管解码方法不断增加，但系统的基准测试仍然有限。在此，我们介绍Serval，一个用于跨不同空间转录组平台开发和基准测试解码方法的模块化框架。Serval将关键解码阶段分离为可独立配置的模块，从而能够灵活集成替代算法。利用该框架，我们开发了余弦解码器，这是一种通过优化与已知条形码的余弦相似性来提高转录本恢复的新方法。我们在合成和真实的MERFISH数据集上评估了余弦解码器和基线方法，表明与现有方法相比，余弦解码器实现了更高的转录本恢复和与表达参考的优越相关性。此外，我们证明了Serval框架可推广到MERFISH之外。通过扩展到DART-FISH平台，我们展示了余弦解码器能够改善转录本恢复、聚类稳定性，并支持对复杂生物结构（如人类初级运动皮层）的更直接注释。这些结果确立了模块化解码框架有助于稳健的、平台无关的基准测试，最终支持跨不同生物样本的更准确空间转录组分析。

## Abstract
Imaging-based spatial transcriptomics technologies have opened new avenues for studying cellular organization and gene expression within intact tissues. However, the accuracy of downstream analyses depends critically on the decoding step that reconstructs barcodes from fluorescence patterns and maps them to gene identities. Despite a growing number of decoding methods, systematic benchmarking has been limited. Here, we introduce Serval, a modular framework for developing and benchmarking decoding methods across diverse spatial transcriptomics platforms. Serval separates key decoding stages into independently configurable modules, enabling flexible integration of alternative algorithms. Using this framework, we develop the Cosine decoder, a novel method that improves transcript recovery by optimizing cosine similarity to known barcodes. We evaluate Cosine and baseline methods on synthetic and real MERFISH datasets, showing that Cosine achieves higher transcript recovery and superior correlation with expression references compared to existing methods. Furthermore, we demonstrate that the Serval framework generalizes beyond MERFISH. By extending to the DART-FISH platform, we show that Cosine improves transcript recovery, clustering stability and supports more direct annotation of complex biological structures such as the human primary motor cortex. These results establish that modular decoding frameworks facilitate robust, platformagnostic benchmarking, ultimately supporting more accurate spatial transcriptomics analysis across diverse biological samples.