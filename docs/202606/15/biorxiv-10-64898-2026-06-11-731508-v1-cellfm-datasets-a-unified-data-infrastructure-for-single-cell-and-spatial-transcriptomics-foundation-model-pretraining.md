---
title: "Cellfm-datasets: A Unified Data Infrastructure for Single-Cell and Spatial Transcriptomics Foundation Model Pretraining"
title_zh: Cellfm-datasets：用于单细胞和空间转录组基础模型预训练的统一数据基础设施
authors: "Zhang, L., Pang, J., Yan, J., Tang, W., Deng, Y., He, Y."
date: 2026-06-14
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.11.731508v1.full.pdf"
tags: ["query:spatialprot"]
score: 7.0
evidence: 为空间转录组基础模型预训练提供统一数据基础设施
tldr: "现有单细胞数据格式H5AD不适用于大规模预训练的高频随机加载。为此提出Cellfm-datasets，将H5AD转换为CSR memmap布局并通过Hugging Face Dataset接口暴露。在基准测试中单核加载速度达60,571样本/秒，多worker可扩展至160,000样本/秒，内存恒定。该方法降低了细胞基础模型预训练的工程负担，促进了可重复性和数据复用。"
source: biorxiv
selection_source: fresh_fetch
motivation: 解决H5AD格式在分布式预训练中频繁随机小批量加载效率低下的问题。
method: 将H5AD转换为CSR memmap布局，并封装为Hugging Face Dataset，支持多种采样策略与分布式分片。
result: "单核随机加载60,571样本/秒，八worker约160,000样本/秒，内存近恒定。"
conclusion: 降低工程负担，促进可重复预训练与多模态数据复用标准化。
---

## 摘要
大规模细胞基础模型日益受到模型架构的限制，但更受限于数据基础设施——需要从内存外数据集中反复采样稀疏转录组图谱。AnnData/H5AD已成为单细胞和空间组学分析的标准交换格式，但其基于HDF5的布局并不适用于多工作节点和分布式预训练下的高频随机小批量加载。我们提出Cellfm-datasets，一个将H5AD数据集转换为自描述的压缩稀疏行（CSR）内存映射布局的数据基础设施制品，并通过Hugging Face Dataset和IterableDataset接口暴露生成的语料库。该制品存储共享基因词汇表、每个样本的元数据、可选的时空坐标、观测元数据、清单和校验和，并在运行时无需密集展开即可重建稀疏细胞或分组记录。统一的采样抽象支持随机细胞组、清单定义的生物区域以及基于坐标的空间块，并跨分布式秩和数据加载器工作节点实现确定性分片。在P14小鼠脑转录组切片上的空间演示展示了真实解剖结构上的区域级和块级采样。在公开异构ModelScope scRNA-seq子集的受控基准测试中，Cellfm-datasets在单核随机加载下达到60,571 ± 1,734样本/秒，使用8个工作节点时扩展到约160,000样本/秒，并在读取多达一百万个细胞时保持近恒定的进程私有内存。通过将稀疏单细胞和空间语料库从模型特定的加载器代码迁移到可重用、经过验证且框架原生的数据集制品，该设计可能减轻可重复细胞基础模型预训练的工程负担，并使重复训练运行、模型比较和混合模态数据重用更易于标准化。

## Abstract
Large-scale cell foundation models are increasingly limited not only by model architecture, but also by the data infrastructure required to repeatedly sample sparse transcriptomic profiles from out-of-core cohorts. AnnData/H5AD has become a standard exchange format for single-cell and spatial omics analysis, yet its HDF5-backed layout is not designed for high-frequency random mini-batch loading under multi-worker and distributed pretraining. We present Cellfm-datasets, a data infrastructure artifact that converts H5AD cohorts into a self-describing compressed sparse row (CSR) memmap layout and exposes the resulting corpus through Hugging Face Dataset and IterableDataset interfaces. The artifact stores a shared gene vocabulary, per-sample metadata, optional spatial coordinates, observation metadata, manifests, and checksums, and reconstructs sparse cell or group records at runtime without dense expansion. A unified sampling abstraction supports random-cell groups, manifest-defined biological regions, and coordinate-based spatial blocks, with deterministic sharding across distributed ranks and data-loader workers. Spatial demonstrations on P14 mouse brain transcriptomics sections illustrate region- and block-level sampling over real anatomical structures. In controlled benchmarks on a public heterogeneous ModelScope scRNA-seq subset, Cellfm-datasets reached 60,571 +/- 1,734 samples/s in single-core random loading, scaled to approximately 160,000 samples/s with eight workers, and maintained near-constant process-private memory while reading up to one million cells. By moving sparse single-cell and spatial corpora from model-specific loader code into reusable, validated, and framework-native dataset artifacts, this design may reduce the engineering burden of reproducible cell foundation model pretraining and make repeated training runs, model comparisons, and mixed-modality data reuse easier to standardize.