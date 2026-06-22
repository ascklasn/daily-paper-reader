---
title: "BioBrain: A Multi-Agent Framework for Natural Language Driven Quantitative Microscopy Data Analysis"
title_zh: BioBrain：一种自然语言驱动的定量显微镜数据分析的多智能体框架
authors: "Tsolakidis, K., Breuer, A., Bender, S. W. B., Margaritaki, S., Dreisler, M. W., Oikonomou, A., Hatzakis, N. S."
date: 2026-06-21
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.17.732700v1.full.pdf"
tags: ["query:agent"]
score: 6.0
evidence: 自然语言驱动的显微镜数据分析多智能体框架
tldr: 荧光显微镜数据日益复杂，传统分析依赖专业软件和编程技能，限制了生物学家直接进行定量分析。BioBrain提出多智能体框架，将自然语言分析目标转化为可执行且可重复的分析流程，通过组装验证方法而非生成代码，并透明报告参数选择。在双通道全内反射荧光和三维晶格光片显微镜基准上，BioBrain在参数指定时精确复现专家结果，参数缺失时可预测且可追溯地退化，而前沿语言模型产生严重定量错误。该工作为实验科学家提供了用生物学语言指导数据分析的实用工具，有效缩小了数据获取与生物学发现之间的差距。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有显微镜数据分析依赖专业软件和编程技能，阻碍了生物学家直接进行定量分析。
method: BioBrain采用多智能体架构，将自然语言指令解析为可重复的分析流程，并集成已验证的分析方法和实验室脚本。
result: 在双通道TIRF和三维晶格光片显微镜数据上，BioBrain在指定参数时精确复现专家结果，参数缺失时退化可预测，优于基线语言模型。
conclusion: BioBrain使实验科学家能通过自然语言交互完成复杂图像分析，降低了计算门槛，推动了数据驱动的生物学发现。
---

## 摘要
荧光显微镜的进步极大地拓展了可解决的生物学问题范围，使得能够以前所未有的时空分辨率定量观测分子相互作用和细胞动力学。然而，成像数据日益增长的复杂性已超出了我们的分析能力。尽管存在众多计算方法，但它们通常依赖专门的软件环境、异构数据格式和技术专长，限制了采用，并加深了数据采集与定量生物学解释之间的鸿沟。在此，我们介绍BioBrain，一个多智能体框架，将自然语言的分析目标转化为可执行且可复现的显微镜分析流程。BioBrain并非生成分析代码，而是组装经过验证的分析方法，并通过将现有实验室脚本集成到统一对话框架中来扩展其分析能力。每个选定的方法和推断的参数都会被透明报告，确保可追溯和可复现的分析。在双通道全内反射荧光和三维晶格光片基准测试中，当指定参数时，BioBrain精确重现了专家得出的结果；当参数未指定时，其性能以可预测和可追溯的方式下降，而前沿语言模型虽无警告完成，却产生了大量、模型依赖的定量误差。BioBrain为缩小数据采集与生物学发现之间日益扩大的差距提供了一条实用路径，使实验科学家能够用生物学的语言而非软件的语言与计算分析进行沟通。

## Abstract
Advances in fluorescence microscopy have dramatically expanded the range of biological questions that can be addressed, enabling quantitative observations of molecular interactions and cellular dynamics with unprecedented spatial and temporal resolution. However, the growing complexity of imaging data has outpaced our ability to analyze them. Despite numerous computational methods exist, they often rely on specialized software environments, heterogeneous data formats, and technical expertise, limiting adoption and widening the gap between data acquisition and quantitative biological interpretation. Here we introduce BioBrain, a multi-agent framework that translates natural-language analytical goals into executable and reproducible microscopy analysis pipelines. Instead of generating analysis code, BioBrain assembles validated analytical methods and can expands its analytical capabilities by integrating existing laboratory scripts into a unified conversational framework. Every selected method and inferred parameter is transparently reported, ensuring traceable and reproducible analyses. On two-channel total internal reflection fluorescence and three-dimensional lattice light-sheet benchmarks, BioBrain exactly reproduces expert-derived results when parameters are specified and degrades predictably and traceably when they are not, while frontier language models generated large, model-dependent quantitative errors despite completing without warning. BioBrain offers a practical path for closing the widening gap between data acquisition and biological discovery, enabling experimental scientists to communicate with computational analysis in the language of biology rather than the language of software.