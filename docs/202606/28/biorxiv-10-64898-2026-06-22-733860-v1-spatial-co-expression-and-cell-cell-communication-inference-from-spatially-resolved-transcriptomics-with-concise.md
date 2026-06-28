---
title: Spatial co-expression and cell-cell communication inference from spatially resolved transcriptomics with CONCISE
title_zh: 利用CONCISE从空间分辨转录组学推断空间共表达和细胞间通讯
authors: "Zhao, J., Shan, X., Wang, G., Chu, T., Lin, C., Chang, R., Zhao, H."
date: 2026-06-28
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.22.733860v1.full.pdf"
tags: ["query:spatialprot"]
score: 8.0
evidence: 空间转录组共表达与细胞通讯推断
tldr: 空间转录组学为研究细胞通讯提供了新机遇，但数据中的空间自相关、分子计数变异和测量误差易导致假阳性推断。CONCISE通过联合建模这些混杂因素，结合矩估计和解析假设检验，实现快速且统计严谨的推断。模拟和真实数据表明，现有方法假阳性率高，而CONCISE校准良好、假阳性控制稳健且检出力更强。应用于肠道炎症和肺癌数据，揭示了炎症相关成纤维细胞特异性互作及肿瘤微环境中的复杂信号网络。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有空间通讯推断方法未充分校正空间自相关、分子计数变异和测量误差，导致假阳性偏高，推理不可靠。
method: CONCISE联合建模空间自相关、总分子计数变异和测量误差，采用矩估计和解析假设检验，无严格分布假设。
result: 模拟和真实数据中，CONCISE校准可靠，假阳性控制优于现有方法，检出力提升；MERFISH和CosMx数据验证了生物学实用性。
conclusion: CONCISE为空间转录组提供了稳健的细胞通讯推断，揭示了疾病微环境中的关键互作网络。
---

## 摘要
细胞间通讯是组织维持稳态、疾病发生发展的基础。空间转录组学的最新进展为直接在完整组织中系统表征配体-受体相互作用提供了前所未有的机会。然而，由于空间转录组数据的内在特征，包括空间自相关、总分子计数的变异和测量误差，可能导致虚假的空间共表达并引发膨胀的假阳性结果，因此稳健地推断空间配体-受体相互作用仍然具有挑战性。大多数现有方法未能充分考虑这些混杂因素，限制了推断细胞通讯的可靠性。在此，我们提出CONCISE，一种用于空间约束共表达和配体-受体相互作用的统计方法，该方法联合建模空间自相关、总分子计数变异、测量误差和空间邻近约束。CONCISE将高效的基于矩的参数估计与分析假设检验相结合，无需严格的分布假设即可实现快速且统计严谨的推断。通过在不同空间转录组平台上的广泛模拟、真实数据置换实验和生物动机阴性对照分析，我们发现大多数现有方法呈现膨胀的假阳性率，而CONCISE实现了良好校准的推断、稳健的假阳性控制和提升的检测能力。将CONCISE应用于肠道炎症和非小细胞肺癌的高分辨率MERFISH和CosMx数据集，进一步凸显了其在疾病背景中的生物学实用性。CONCISE揭示了肠道炎症期间与炎症相关的成纤维细胞特异性相互作用，并描绘了肿瘤微环境中复杂的肿瘤-免疫和肿瘤-基质信号网络。

## Abstract
Cell-cell communication is fundamental to tissue organization, homeostasis, and disease progression. Recent advances in spatial transcriptomics provide unprecedented opportunities to systematically characterize ligand-receptor interactions directly within intact tissues. However, robust inference of spatial ligand-receptor interactions remains challenging because intrinsic features of spatial transcriptomics data, including spatial autocorrelation, variation in total molecular counts, and measurement errors, can induce spurious spatial co-expression and lead to inflated false-positive results. Most existing methods do not adequately account for these confounding factors, limiting the reliability of inferred cellular communication. Here, we present CONCISE, a statistical method for spatially constrained co-expression and ligand-receptor interaction inference that jointly models spatial autocorrelation, variation in total molecular counts, measurement errors, and spatial proximity constraints. CONCISE combines efficient moment-based parameter estimation with analytical hypothesis testing, enabling fast and statistically rigorous inference without restrictive distributional assumptions. Through extensive simulations, real-data permutation experiments, and biologically motivated negative-control analyses across different spatial transcriptomics platforms, we show that most existing methods presented inflated false-positive rates, whereas CONCISE achieved well-calibrated inference, robust false-positive control, and improved detection power. Application of CONCISE to high-resolution MERFISH and CosMx datasets from intestinal inflammation and non-small cell lung cancer further highlights its biological utility in disease contexts. CONCISE uncovered inflammation-associated fibroblast-specific interactions during intestinal inflammation and delineated complex tumor-immune and tumor-stromal signaling networks within the tumor microenvironment.