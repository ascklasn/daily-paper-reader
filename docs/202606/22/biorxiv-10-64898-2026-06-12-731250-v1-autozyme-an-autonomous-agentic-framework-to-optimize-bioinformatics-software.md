---
title: "AutoZyme: An Autonomous Agentic Framework to Optimize Bioinformatics Software"
title_zh: AutoZyme：一个用于优化生物信息学软件的自主智能体框架
authors: "Xie, E., Cheng, L., Cai, Y., Shireman, J., Kendziorski, C."
date: 2026-06-16
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.12.731250v1.full.pdf"
tags: ["query:agent"]
score: 6.0
evidence: 自主代理框架用于科学软件优化，可迁移至医学AI代理领域
tldr: "基因组学和生物信息学软件的性能瓶颈因数据集增大而日益严重，传统手动优化难以规模化。AutoZyme是一个自主智能体框架，自动构建基准测试、识别瓶颈并迭代优化代码，仅保留提升速度且保持输出正确的改动。在45个函数上评估，超过95%的情况下运行时间得到改善，内存未显著增加。针对Seurat、Scanpy等38个函数，运行时间中位数降低8.52倍，最大降幅超676倍。优化函数通过AutoZyme-Library作为即插即用替换发布，同时提供可重用框架以优化其他软件，大幅降低了性能优化门槛。"
source: biorxiv
selection_source: fresh_fetch
motivation: 手动优化生物信息学软件性能瓶颈困难且难以扩展，亟需自动化方法。
method: AutoZyme采用智能体框架，自动构建基准测试、剖析瓶颈、迭代修改代码并验证正确性。
result: "在45个函数上超过95%提升运行时间，对38个基因分析函数中位数加速8.52倍，最大超676倍。"
conclusion: AutoZyme通过自动化优化框架和即插即用库，显著提升了生物信息学软件性能，易于集成到现有流程。
---

## 摘要
随着生物数据集规模和数量的持续增长，广泛使用的基因组学和生物信息学软件中的性能瓶颈带来了日益沉重的负担。缓解这些瓶颈主要依赖专家手动优化，因此难以扩展。本文提出AutoZyme，一个用于科学软件优化的智能体框架。给定目标函数，AutoZyme会构建基准测试、识别瓶颈、迭代测试代码变更，仅保留那些在不影响输出的前提下提升运行时的修改。我们在45个函数上评估了AutoZyme，在超过95%的案例中，运行时得到改善且未显著增加内存。对于来自Seurat、Scanpy以及基因组学和生物信息学相关包中的38个函数，AutoZyme将运行时中位数降低了8.52倍，最大降幅超过676倍。优化后的函数通过AutoZyme-Library发布，可作为现有分析管道的即插即用替代品。我们还开放了AutoZyme作为可重用的框架，用于优化用户指定的其他包和函数。

## Abstract
Performance bottlenecks in widely used genomics and bioinformatics software present a substantial and growing burden as biological datasets continue to increase in size and number. Relieving these bottlenecks relies largely on expert manual optimization and therefore remains difficult to scale. Here we present AutoZyme, an agentic framework for scientific software optimization. Given a target function, AutoZyme builds benchmarks, identifies bottlenecks, and iteratively tests code changes, retaining only those that improve runtime while preserving output. We evaluated AutoZyme on 45 functions, improving runtime without substantial memory increases in over 95% of cases considered. Across 38 functions from Seurat, Scanpy and related packages in genomics and bioinformatics, AutoZyme reduced runtime by a median of 8.52-fold, with the largest reductions exceeding 676-fold. The optimized functions are distributed through AutoZyme-Library as drop-in replacements for existing analysis pipelines. We also release AutoZyme as a reusable framework for optimizing additional user-specified packages and functions.