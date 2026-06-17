---
title: "Cellfm-datasets: A Unified Data Infrastructure for Single-Cell and Spatial Transcriptomics Foundation Model Pretraining"
title_zh: Cellfm-datasets：用于单细胞和空间转录组基础模型预训练的统一数据基础设施
authors: "Zhang, L., Pang, J., Yan, J., Tang, W., Deng, Y., He, Y."
date: 2026-06-14
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.11.731508v1.full.pdf"
tags: ["query:spatialprot"]
score: 6.0
evidence: 单细胞和空间转录组学统一数据基础设施，与空间蛋白组学综合主题相关
tldr: 单细胞和空间转录组基础模型预训练受限于数据加载效率，现有H5AD格式不适合多worker分布式训练。Cellfm-datasets将H5AD转换为CSR memmap布局，通过Hugging Face Dataset接口提供可扩展的数据加载。支持随机细胞、区域和空间块采样，在公开数据集上单核达6万样本/秒，多核约16万样本/秒，内存近恒定。该设计降低了基础模型预训练的工程负担，促进可重复训练与模型比较。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有H5AD格式在分布式预训练中随机小批量加载效率低，需统一高效的数据基础设施。
method: 将H5AD转换为CSR memmap布局，通过Hugging Face Dataset接口封装，支持多级采样与确定性分片。
result: "单核随机加载达60,571样本/秒，八核约160,000样本/秒，内存占用近恒定，支持百万级细胞读取。"
conclusion: Cellfm-datasets减少基础模型预训练的工程负担，增强可重复性与多模态数据复用标准化。
---

## 摘要
大规模细胞基础模型日益受到的限制不仅来自模型架构，还来自数据基础设施——需要从外存队列中反复采样稀疏的转录组图谱。AnnData/H5AD已成为单细胞和空间组学分析的标准交换格式，但其基于HDF5的布局并不适合多工作节点和分布式预训练下的高频随机小批量加载。我们提出了Cellfm-datasets，一种数据基础设施构件，它将H5AD队列转换为自描述的压缩稀疏行（CSR）内存映射布局，并通过Hugging Face Dataset和IterableDataset接口暴露生成的语料库。该构件存储共享的基因词汇表、每个样本的元数据、可选的空间坐标、观测元数据、清单和校验和，并在运行时无需密集展开即可重建稀疏的细胞或组记录。统一的采样抽象支持随机细胞组、清单定义的生物区域和基于坐标的空间块，并实现了跨分布式等级和数据加载器工作节点的确定性分片。在P14小鼠脑转录组切片上的空间演示展示了在真实解剖结构上的区域级和区块级采样。在公开的异构ModelScope scRNA-seq子集的受控基准测试中，Cellfm-datasets在单核随机加载下达到60,571 +/- 1,734样本/秒，使用8个工作节点后扩展至约160,000样本/秒，并且在读取多达一百万个细胞时保持近乎恒定的进程私有内存。通过将稀疏单细胞和空间语料库从模型特定的加载器代码转移到可重用、经过验证且框架原生的数据集构件中，这种设计可能减少可重复细胞基础模型预训练的工程负担，并使重复训练运行、模型比较和混合模态数据重用更容易标准化。

代码可用性：https://github.com/PangJiangShuan/cellfm-datasets

## Abstract
Large-scale cell foundation models are increasingly limited not only by model architecture, but also by the data infrastructure required to repeatedly sample sparse transcriptomic profiles from out-of-core cohorts. AnnData/H5AD has become a standard exchange format for single-cell and spatial omics analysis, yet its HDF5-backed layout is not designed for high-frequency random mini-batch loading under multi-worker and distributed pretraining. We present Cellfm-datasets, a data infrastructure artifact that converts H5AD cohorts into a self-describing compressed sparse row (CSR) memmap layout and exposes the resulting corpus through Hugging Face Dataset and IterableDataset interfaces. The artifact stores a shared gene vocabulary, per-sample metadata, optional spatial coordinates, observation metadata, manifests, and checksums, and reconstructs sparse cell or group records at runtime without dense expansion. A unified sampling abstraction supports random-cell groups, manifest-defined biological regions, and coordinate-based spatial blocks, with deterministic sharding across distributed ranks and data-loader workers. Spatial demonstrations on P14 mouse brain transcriptomics sections illustrate region- and block-level sampling over real anatomical structures. In controlled benchmarks on a public heterogeneous ModelScope scRNA-seq subset, Cellfm-datasets reached 60,571 {+/-} 1,734 samples/s in single-core random loading, scaled to approximately 160,000 samples/s with eight workers, and maintained near-constant process-private memory while reading up to one million cells. By moving sparse single-cell and spatial corpora from model-specific loader code into reusable, validated, and framework-native dataset artifacts, this design may reduce the engineering burden of reproducible cell foundation model pretraining and make repeated training runs, model comparisons, and mixed-modality data reuse easier to standardize.

Code availabilityhttps://github.com/PangJiangShuan/cellfm-datasets