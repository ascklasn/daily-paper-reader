---
title: SpaGRD deciphers signaling architectures in spatial transcriptomics using graph reaction-diffusion systems
title_zh: SpaGRD利用图反应-扩散系统解码空间转录组学中的信号架构
authors: "Liu, J., Sun, S., Chen, Z., Lv, Z., Jiang, S., Li, G., Liu, B."
date: 2026-07-02
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.28.735031v1.full.pdf"
tags: ["query:spatialprot"]
score: 7.0
evidence: 利用反应扩散系统推断空间转录组学细胞间通讯
tldr: 空间转录组学为研究细胞间通讯提供新机会，但现有方法多基于静态启发模型，忽略时空动态和机制复杂性。SpaGRD基于Fick扩散定律和质量作用定律的偏微分方程，利用图信号处理在空间图上求解，实现更准确鲁棒的通讯推断。模拟和多种组织数据集验证显示其优越性能，揭示动态通讯模式和空间解析信号异质性。该框架为定量研究时空细胞通讯提供了准确、可解释且机制化的途径。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有细胞间通讯推理方法缺乏时空动态性和机制基础，准确性及生物学可解释性受限。
method: 基于Fick扩散定律和质量作用定律的偏微分方程，结合图信号处理在空间图上求解反应-扩散系统。
result: 模拟数据上准确性及鲁棒性优于现有方法；真实数据集揭示动态通讯模式与空间异质性。
conclusion: SpaGRD提供了准确、可解释且机制化的框架，促进时空细胞通讯的定量研究。
---

## 摘要
空间转录组学的快速兴起为通过捕获基因表达及其空间背景来研究细胞间通信提供了前所未有的机遇。然而，现有的细胞间通信推断方法通常依赖于静态的启发式模型，忽略了细胞间信号传导固有的时空动态性和机制复杂性，限制了准确性和生物学可解释性。在此，我们提出SpaGRD，一种基于第一性原理的方法，通过从菲克扩散定律和质量作用定律推导出的偏微分方程显式建模配体-受体相互作用。利用图信号处理技术，SpaGRD在空间图上求解这些方程，为细胞间通信推断提供了一种原理性且可推广的方法。通过大量模拟，SpaGRD相较于现有方法展现出更高的准确性和鲁棒性。在跨不同组织和平台的多个数据集上的应用揭示了具有空间分辨信号异质性的动态细胞间通信模式，为细胞协调和发育过程提供了具有生物学意义的见解。通过将物理模型与空间转录组学相结合，SpaGRD为推进时空细胞间通信的定量研究提供了一个准确、可解释且基于机制的框架。

## Abstract
The rapid emergence of spatial transcriptomics offers unprecedented opportunities to study cell-cell communication (CCC) by capturing gene expression alongside spatial context. However, existing CCC inference methods often rely on static, heuristic models that overlook the inherently spatiotemporal dynamics and mechanistic complexity of intercellular signaling, limiting both accuracy and biological interpretability. Here, we present SpaGRD, a first-principles-based method that explicitly models ligand-receptor interactions through partial differential equations derived from Ficks law of diffusion and the mass action law. Leveraging graph signal processing techniques, SpaGRD solves these equations on spatial graphs, providing a principled and generalizable approach to CCC inference. Through extensive simulations, SpaGRD demonstrates superior accuracy and robustness compared to existing methods. Applications to multiple datasets across diverse tissues and platforms reveal dynamic CCC patterns with spatially resolved signaling heterogeneity, providing biologically meaningful insights into cellular coordination and developmental processes. By bridging physical modeling with spatial transcriptomics, SpaGRD provides an accurate, interpretable, and mechanistically grounded framework for advancing quantitative studies of spatiotemporal cell-cell communication.