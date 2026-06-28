---
title: "BioBrain: A Multi-Agent Framework for Natural Language Driven Quantitative Microscopy Data Analysis"
title_zh: BioBrain：一种自然语言驱动的定量显微镜数据分析多智能体框架
authors: "Tsolakidis, K., Breuer, A., Bender, S. W. B., Margaritaki, S., Dreisler, M. W., Oikonomou, A., Hatzakis, N. S."
date: 2026-06-21
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.17.732700v1.full.pdf"
tags: ["query:agent"]
score: 8.0
evidence: 用于显微镜数据分析的多智能体框架
tldr: 荧光显微镜数据日益复杂，现有分析依赖专业软件和技能，难以普及。BioBrain多智能体框架将自然语言分析目标转化为可执行、可复现的显微镜分析管道，集成现有脚本并透明报告方法和参数。在TIRF和晶格光片基准上，指定参数时精确复现专家结果；未指定时性能可预测下降，而前沿语言模型产生大误差。该框架让实验科学家以生物学语言而非软件语言进行定量分析，缩小了数据获取与生物学发现之间的鸿沟。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有显微镜数据分析方法依赖专业软件和技能，限制了生物学家对复杂定量数据的解读。
method: BioBrain多智能体框架通过自然语言理解，动态组装验证过的分析方法并透明报告每一步，支持集成实验室脚本。
result: 在TIRF和晶格光片基准测试中，指定参数时精确复现专家结果，未指定时性能可预测且可追溯下降，优于前沿语言模型。
conclusion: BioBrain为生物学家提供了一种以自然语言驱动数据分析的实用途径，弥合了数据采集与生物学解释之间的鸿沟。
---

## 摘要
荧光显微镜的进步极大地扩展了可解决的生物学问题范围，以前所未有的时空分辨率实现了对分子相互作用和细胞动力学的定量观测。然而，成像数据的日益复杂性已超出了我们的分析能力。尽管存在众多计算方法，但它们往往依赖于专门的软件环境、异构的数据格式以及专业技术知识，这限制了其应用，并加剧了数据采集与定量生物学解释之间的鸿沟。在此，我们介绍BioBrain，一种将自然语言分析目标转化为可执行且可重现的显微镜分析流程的多智能体框架。BioBrain并非生成分析代码，而是组装经过验证的分析方法，并可通过将现有实验室脚本整合到统一的对话框架中来扩展其分析能力。每个选择的方法和推断的参数都会被透明地报告，确保分析的可追溯性和可重现性。在双通道全内反射荧光和三维晶格光片基准测试中，当参数被指定时，BioBrain精确重现了专家得出的结果；当参数未被指定时，其性能以可预测且可追溯的方式下降，而前沿语言模型即使在无警告完成的情况下也产生了较大的、模型依赖的定量误差。BioBrain为弥合数据采集与生物学发现之间日益扩大的鸿沟提供了一条实用途径，使实验科学家能够以生物学的语言而非软件的语言与计算分析进行交流。

## Abstract
Advances in fluorescence microscopy have dramatically expanded the range of biological questions that can be addressed, enabling quantitative observations of molecular interactions and cellular dynamics with unprecedented spatial and temporal resolution. However, the growing complexity of imaging data has outpaced our ability to analyze them. Despite numerous computational methods exist, they often rely on specialized software environments, heterogeneous data formats, and technical expertise, limiting adoption and widening the gap between data acquisition and quantitative biological interpretation. Here we introduce BioBrain, a multi-agent framework that translates natural-language analytical goals into executable and reproducible microscopy analysis pipelines. Instead of generating analysis code, BioBrain assembles validated analytical methods and can expands its analytical capabilities by integrating existing laboratory scripts into a unified conversational framework. Every selected method and inferred parameter is transparently reported, ensuring traceable and reproducible analyses. On two-channel total internal reflection fluorescence and three-dimensional lattice light-sheet benchmarks, BioBrain exactly reproduces expert-derived results when parameters are specified and degrades predictably and traceably when they are not, while frontier language models generated large, model-dependent quantitative errors despite completing without warning. BioBrain offers a practical path for closing the widening gap between data acquisition and biological discovery, enabling experimental scientists to communicate with computational analysis in the language of biology rather than the language of software.