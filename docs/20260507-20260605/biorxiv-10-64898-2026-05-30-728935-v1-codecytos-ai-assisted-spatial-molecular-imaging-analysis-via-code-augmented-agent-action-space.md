---
title: "CodeCytos: AI-assisted spatial molecular imaging analysis via code-augmented agent action space"
title_zh: CodeCytos：通过代码增强的智能体动作空间实现人工智能辅助空间分子成像分析
authors: "Vo, H. Q., Ly, S. T., Wan, Z., Nguyen, A.-V., Zhao, H., Sheng, J., Wong, S. T. C., Nguyen, H. V."
date: 2026-06-03
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.30.728935v1.full.pdf"
tags: ["query:spatialprot"]
score: 8.0
evidence: 基于编码的智能体框架用于空间分子成像分析
tldr: 传统组织图像分析软件缺乏代码驱动自动化，灵活性有限。我们提出CodeCytos，一个基于编码推理的智能体框架，实现动态、可编程的空间分子成像数据分析，支持自定义特征探索。在四个不同组织数据集上的评估表明，结合领域无关的少样本编码推理示例，CodeCytos显著优于基线方法。该框架展示了代码驱动代理在加速生物标志物发现中的潜力。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有组织分析工具依赖人工干预且仅支持固定特征，无法高效满足复杂空间研究中对自定义细胞特征的灵活探索需求。
method: 提出CodeCytos框架，通过编码增强的智能体动作空间，利用大语言模型实现用户问题的动态编程式交互与特征计算。
result: 在脑组织、肺癌、胰腺和扁桃体四类数据集上，CodeCytos在最小提示设置下超越基线，且领域无关的少样本示例显著提升性能。
conclusion: 代码驱动的推理智能体能有效支持空间分子成像中的自定义特征探索，为生物标志物发现提供可扩展方案。
---

## 摘要
传统的组织图像分析软件为细胞分析提供了基础功能，包括分割、形态特征提取和空间组织分析；然而，这些工具通常需要人工干预，缺乏与代码驱动自动化的无缝集成，限制了复杂空间组织研究的效率和可扩展性，同时由于仅支持一组固定的预定义空间细胞特征，对自定义分析的灵活性有限。为了解决这些限制，我们提出了CodeCytos，一个基于编码的推理智能体框架，能够实现与空间分子成像数据的动态、可编程交互，并简化了跨不同研究需求的自定义空间细胞特征的探索。我们通过对四个专家策划的数据集（涵盖不同的组织类型，包括额叶皮质、非小细胞肺癌、胰腺和扁桃体）进行案例研究来展示其实用性，并在一个现实的最小提示设置下进行评估，在该设置中，生物科学家提出简单问题，没有任务特定指令或先验上下文知识，并对多个具有强大编码能力的大型语言模型骨干进行基准测试。我们进一步表明，纳入领域无关的少量样本上下文编码推理示例（从空间分析领域之外随机采样）可以显著提高性能，而无需昂贵的专家制作的领域内演示；总体而言，CodeCytos优于基线方法，突出了代码驱动推理智能体在空间分子成像中支持自定义特征探索并加速生物标志物发现的潜力。

## Abstract
Conventional tissue image analysis software provides foundational capabilities for cellular analysis, including segmentation, morphological feature extraction, and spatial organization analysis; however, these tools often require manual intervention and lack seamless integration with code-driven automation, limiting efficiency and scalability for complex spatial tissue studies, while also offering limited flexibility for custom analyses by supporting only a fixed set of predefined spatial cellular features. To address these limitations, we propose CodeCytos, a coding-based reasoning agent framework that enables dynamic, programmable interaction with spatial molecular imaging data and streamlines the exploration of custom spatial cellular features across diverse research needs. We demonstrate its utility through case studies on four expert-curated datasets spanning distinct tissue types, including frontal cortex, non-small-cell lung cancer, pancreas, and tonsil, and evaluate it under a realistic minimal prompt setting in which bioscientists pose simple questions without task-specific instructions or prior contextual knowledge, benchmarking multiple large language model backbones with strong coding capabilities. We further show that incorporating domain-agnostic few-shot in-context coding-reasoning examples, randomly sampled from outside the spatial analysis domain, substantially improves performance without requiring costly expert-crafted in-domain demonstrations; overall, CodeCytos outperforms baseline approaches, highlighting the potential of code-driven reasoning agents to support custom feature exploration in spatial molecular imaging and accelerate biomarker discovery.