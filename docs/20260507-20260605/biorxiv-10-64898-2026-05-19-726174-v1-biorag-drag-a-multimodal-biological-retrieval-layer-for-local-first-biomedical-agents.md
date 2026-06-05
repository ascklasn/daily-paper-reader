---
title: "BioRAG-DRAG: A Multimodal Biological Retrieval Layer for Local-First Biomedical Agents"
title_zh: BioRAG-DRAG：面向本地优先生物医学代理的多模态生物检索层
authors: "Wang, L."
date: 2026-05-21
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.19.726174v1.full.pdf"
tags: ["query:agent"]
score: 8.0
evidence: 多模态检索层增强生物医学代理
tldr: 生物医学智能体需访问文本、序列和关系等多种证据，但传统工具如BLAST难以作为LLM的统一接口。本文提出BioRAG-DRAG，结合可插拔神经序列-文本检索、BLAST验证和DRAG证据图，实现本地优先的多模态检索。在包含257886条记录的BioRAG-Standard v0上测试，BLAST几乎饱和生物匹配，向量检索匹配率较低，公共蛋白编码器优于专用模型，DNA检索薄弱。结果表明有界架构有效：向量检索提供统一候选，BLAST和DRAG确保生物验证与归因。
source: biorxiv
selection_source: fresh_fetch
motivation: 经典序列工具与LLM缺乏统一接口，现有检索无法同时处理多模态生物证据。
method: 构建可插拔的神经检索层，融合ESM-2等专用编码器、BLAST验证及DRAG图包装。
result: BLAST实现近饱和生物匹配；公共蛋白编码器优于OmniGene；DNA密集检索弱；图结构显示部分序列相似性驱动。
conclusion: 向量检索提供统一候选上下文，BLAST和DRAG互补实现生物学验证与归因。
---

## 摘要
生物医学代理需要可靠地访问异质证据：文献文本、基因和通路记录、蛋白质序列、DNA/cDNA序列以及结构化的生物学关系。经典的序列工具（如BLAST）仍然是对齐验证的正确选择，但它们并不是大型语言模型代理的统一上下文接口。我们提出了BioRAG-DRAG，一种本地优先的多模态检索层，它结合了可插拔的神经序列-文本检索、BLAST验证和基于图的证据打包。专用编码器（如ESM-2）可以服务于蛋白质分区，而OmniGene CPT则为混合序列/文本和面向代理的使用提供了统一的生物学语言骨干；BLAST对序列候选进行重排序或验证；DRAG图为下游代理暴露了带类型、可追溯的路径。

我们引入了BioRAG-Standard v0，一个包含257,886条可检索记录的分区语料库/库，以及基于Open-Rosalind标准生物医学记录和序列窗口扩展构建的初始标注层，用于工程评估。在索引内序列窗口压力测试中，BLAST几乎饱和了生物学匹配，而向量检索恢复了大量但较低的生物学匹配率。在留出的父片段控制上，公共蛋白质编码器优于当前的OmniGene蛋白质窗口嵌入，而DNA/cDNA密集检索即使使用现成的Nucleotide Transformer池化仍然较弱；这支持了模型无关的BioRAG设计，而不是声称一个统一的生成器骨干是最好的序列搜索编码器。在标准文本和10万序列窗口集合上的索引Chroma查找在查询嵌入后仅增加了少量查找开销；这并未衡量端到端的即时延迟。最后，探索性序列DRAG踪迹展示了可检查的生物学邻域，包括免疫球蛋白家族和基因符号模块，初始图控制表明结构非随机且部分由序列相似性驱动。这些结果支持一种受限的架构：向量检索提供统一的候选上下文，而BLAST和DRAG提供生物学验证和证据归因。

## Abstract
Biomedical agents need reliable access to heterogeneous evidence: literature text, gene and pathway records, protein sequences, DNA/cDNA sequences, and structured biological relations. Classical sequence tools such as BLAST remain the right choice for alignment-grounded verification, but they are not a unified context interface for large language model agents. We present BioRAG-DRAG, a local-first multimodal retrieval layer that combines pluggable neural sequence-text retrieval, BLAST verification, and graph-based evidence packaging. Specialized encoders such as ESM-2 can serve protein partitions, while OmniGene CPT provides a unified biological-language backbone for mixed sequence/text and agent-facing use; BLAST reranks or verifies sequence candidates; and DRAG graphs expose typed, traceable paths for downstream agents.

We introduce BioRAG-Standard v0, a partitioned corpus/library with 257,886 retrievable records and an initial annotation layer for engineering evaluation built from Open-Rosalind Standard biomedical records and sequence-window extensions. On an in-index sequence-window stress test, BLAST nearly saturates biological matching, while vector retrieval recovers substantial but lower biological match rates. On held-out parent-fragment controls, public protein encoders outperform the current OmniGene protein-window embedding, while DNA/cDNA dense retrieval remains weak even with off-the-shelf Nucleotide Transformer pooling; this supports a model-agnostic BioRAG design rather than a claim that one unified generator backbone is the best sequence-search encoder. Indexed Chroma lookup over Standard text and 100k sequence-window collections adds only small lookup overhead after query embedding; this does not measure end-to-end instant latency. Finally, exploratory sequence DRAG traces show inspectable biological neighborhoods, including immunoglobulin-family and gene-symbol modules, with initial graph controls indicating non-random but partly sequence-similarity-driven structure. These results support a bounded architecture: vector retrieval supplies unified candidate context, while BLAST and DRAG provide biological verification and evidence attribution.