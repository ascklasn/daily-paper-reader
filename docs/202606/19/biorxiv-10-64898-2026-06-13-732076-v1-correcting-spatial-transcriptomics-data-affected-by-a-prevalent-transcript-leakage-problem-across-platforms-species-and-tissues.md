---
title: "Correcting spatial transcriptomics data affected by a prevalent transcript leakage problem across platforms, species, and tissues"
title_zh: 纠正跨平台、跨物种和跨组织中普遍存在的转录本泄漏问题影响的空间转录组学数据
authors: "Shi, C. H., Zhai, Y., Chow, S. H.-C., Li, L., Carver, C. M., Teneche, M. G., Flores, J., Kern, C., Adams, P. D., Ren, B., Schafer, M. J., Zhu, Q., Wei, Y., Yip, K. Y."
date: 2026-06-17
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.13.732076v1.full.pdf"
tags: ["query:spatialprot"]
score: 6.0
evidence: 空间转录组数据校正，与空间组学整合相关
tldr: 空间转录组数据中普遍存在转录本渗漏问题，导致转录本扩散到邻近细胞并被重复检测，影响定量和下游分析。我们提出基于无参考贝叶斯模型的DeLeakage方法，通过概率建模有效清除渗漏信号。在多种平台、物种和组织数据上，DeLeakage比现有降噪方法显著提升数据洁净度，同时改善细胞类型注释并避免假阳性空间依赖基因表达检测。
source: biorxiv
selection_source: fresh_fetch
motivation: 空间转录组数据普遍因转录本渗漏导致邻近细胞信号污染，亟需有效校正方法。
method: 提出无参考贝叶斯模型DeLeakage，通过概率建模移除转录本渗漏信号。
result: DeLeakage在多种平台、物种和组织数据上优于现有降噪方法，显著提高数据洁净度。
conclusion: DeLeakage有效校正转录本渗漏，提升细胞注释和空间表达分析的可靠性。
---

## 摘要
空间转录组学已被广泛应用于研究组织样本中细胞类型、细胞状态和特定基因表达的空间分布。然而，我们发现空间转录组学数据中存在一个普遍存在的转录本泄漏问题，即某个细胞表达的转录本扩散到其邻近区域，并在附近的细胞中被反复检测到。通过分析已发表的数据集，我们表明这个问题普遍存在于使用不同基于成像和基于测序的空间转录组学平台从不同组织和不同物种产生的数据中。它既影响上游任务如表达定量，也影响下游任务如细胞类型注释和空间依赖性基因表达的检测。为了解决转录本泄漏问题，我们提出了一种无参考的基于贝叶斯模型的方法DeLeakage，它比现有的去噪方法更有效地清理数据。DeLeakage还改善了细胞类型注释，并避免了空间依赖性表达的假阳性检测。

## Abstract
Spatial transcriptomics has been widely applied to study the spatial distribution of cell types, cell states, and specific gene expression in tissue samples. However, we show that there is a prevalent transcript leakage problem in spatial transcriptomics data, where transcripts expressed by a cell diffuse to its neighborhood and are recurrently detected in the nearby cells. By analyzing published data sets, we show that this problem is general across data produced from different tissues and different species using different imaging-based and sequencing-based spatial transcriptomics platforms. It affects both upstream tasks such as expression quantification as well as downstream tasks such as cell-type annotation and detection of spatially-dependent gene expression. To tackle the transcript leakage problem, we propose a reference-free Bayesian model-based method, DeLeakage, which cleans up the data much more effectively than existing denoising methods. DeLeakage also improves cell-type annotation and avoids false detection of spatially dependent expression.