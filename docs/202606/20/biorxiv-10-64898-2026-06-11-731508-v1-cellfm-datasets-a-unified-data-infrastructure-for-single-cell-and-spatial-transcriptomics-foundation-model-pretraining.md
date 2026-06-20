---
title: "Cellfm-datasets: A Unified Data Infrastructure for Single-Cell and Spatial Transcriptomics Foundation Model Pretraining"
title_zh: Cellfm-datasets：单细胞和空间转录组基础模型预训练的统一数据基础设施
authors: "Zhang, L., Pang, J., Yan, J., Tang, W., Deng, Y., He, Y."
date: 2026-06-14
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.11.731508v1.full.pdf"
tags: ["query:spatialprot"]
score: 6.0
evidence: 用于单细胞和空间转录组基础模型预训练的数据基础设施
tldr: "单细胞与空间转录组学基础模型预训练受限于数据基础设施。现有H5AD格式不适用于分布式多worker下的高频随机小批量加载。本文提出Cellfm-datasets，将H5AD转换为自描述CSR memmap布局，并集成Hugging Face Dataset接口，支持随机细胞组、区域和空间块采样。基准测试中单核随机加载速率达60,571样本/秒，8 worker时约160,000样本/秒，内存保持近恒定。该设计降低了基础模型预训练的工程负载，提升了可重复性和标准化程度。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有AnnData/H5AD格式不适合分布式预训练中的高频随机小批量加载，亟需高效统一的数据基础设施。
method: 将H5AD转换为CSR memmap布局，提供Hugging Face Dataset接口，支持随机细胞组、区域和空间块采样及确定性分片。
result: "单核随机加载速率60,571±1,734样本/秒，8 worker达~160,000样本/秒，内存近恒定，可读取百万细胞。"
conclusion: 通过可复用数据集工件替代模型专用加载代码，降低工程负担，促进可重复预训练与混合模态数据重用。
---

## 摘要
大规模细胞基础模型日益受到限制，不仅在于模型架构，还在于数据基础设施——需要从外存样本队列中重复采样稀疏转录组谱。AnnData/H5AD已成为单细胞和空间组学分析的标准交换格式，但其基于HDF5的布局并不适用于多工作节点和分布式预训练下的高频随机小批量加载。我们提出了Cellfm-datasets，一种将H5AD样本队列转换为自描述压缩稀疏行（CSR）内存映射布局的数据基础设施工件，并通过Hugging Face Dataset和IterableDataset接口暴露生成的语料库。该工件存储共享的基因词汇表、每个样本的元数据、可选的坐标、观察元数据、清单和校验和，并在运行时重建稀疏细胞或组记录，无需密集展开。统一的采样抽象支持随机细胞组、通过清单定义的生物区域以及基于坐标的空间块，并在分布式秩和数据加载器工作节点之间实现确定性分片。在P14小鼠脑转录组切片上的空间展示说明了真实解剖结构上的区域块级采样。在公开的异构ModelScope scRNA-seq子集上的受控基准测试中，Cellfm-datasets在单核随机加载下达到60,571±1,734个样本/秒，使用八个工作节点时扩展到约160,000个样本/秒，并在读取多达一百万个细胞时保持近乎恒定的进程私有内存。通过将稀疏单细胞和空间语料库从模型特定的加载器代码迁移到可复用、经过验证且框架原生的数据集工件中，本设计可能会减少可重复细胞基础模型预训练的工程负担，并使重复训练运行、模型比较和混合模态数据重用更容易标准化。

代码可用性：https://github.com/PangJiangShuan/cellfm-datasets

## Abstract
Large-scale cell foundation models are increasingly limited not only by model architecture, but also by the data infrastructure required to repeatedly sample sparse transcriptomic profiles from out-of-core cohorts. AnnData/H5AD has become a standard exchange format for single-cell and spatial omics analysis, yet its HDF5-backed layout is not designed for high-frequency random mini-batch loading under multi-worker and distributed pretraining. We present Cellfm-datasets, a data infrastructure artifact that converts H5AD cohorts into a self-describing compressed sparse row (CSR) memmap layout and exposes the resulting corpus through Hugging Face Dataset and IterableDataset interfaces. The artifact stores a shared gene vocabulary, per-sample metadata, optional spatial coordinates, observation metadata, manifests, and checksums, and reconstructs sparse cell or group records at runtime without dense expansion. A unified sampling abstraction supports random-cell groups, manifest-defined biological regions, and coordinate-based spatial blocks, with deterministic sharding across distributed ranks and data-loader workers. Spatial demonstrations on P14 mouse brain transcriptomics sections illustrate region- and block-level sampling over real anatomical structures. In controlled benchmarks on a public heterogeneous ModelScope scRNA-seq subset, Cellfm-datasets reached 60,571 {+/-} 1,734 samples/s in single-core random loading, scaled to approximately 160,000 samples/s with eight workers, and maintained near-constant process-private memory while reading up to one million cells. By moving sparse single-cell and spatial corpora from model-specific loader code into reusable, validated, and framework-native dataset artifacts, this design may reduce the engineering burden of reproducible cell foundation model pretraining and make repeated training runs, model comparisons, and mixed-modality data reuse easier to standardize.

Code availabilityhttps://github.com/PangJiangShuan/cellfm-datasets