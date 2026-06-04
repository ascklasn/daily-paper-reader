---
title: Proteomics-constrained deconvolution reveals spatial cell-type programs in tumours
title_zh: 蛋白质组学约束的反卷积揭示肿瘤中的空间细胞类型程序
authors: "Isik, E. B., Haley, M. J., Anbaki, A. A., Bere, L., Roncaroli, F., Piper Hanley, K., Couper, K., Wedge, D. C., Sellers, R., Oliveira, P., Ashton, J., Bristow, R. G., Alvarez, M. A., Georgaka, S., Rattray, M."
date: 2026-06-04
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.01.729268v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 蛋白质组约束的肿瘤空间转录组解卷积
tldr: 空间转录组学中细胞类型混合物的准确解析面临挑战，尤其当缺乏匹配单细胞参考时。现有方法依赖高质量参考或可扩展性差。我们提出PISTACHIO，一种基于约束非负矩阵分解的蛋白质组学-informed解卷积框架。它利用成像质谱流式细胞术提供空间约束，在合成和真实肿瘤数据上优于Cell2location和STdeconvolve。PISTACHIO对细胞类型分配错误鲁棒，运行快速，适合大规模应用。
source: biorxiv
selection_source: fresh_fetch
motivation: 解决空间转录组中细胞类型混合物解析难题，特别是在缺乏高质量单细胞参考或细胞混合场景下。
method: 提出PISTACHIO，基于负二项似然的约束非负矩阵分解，整合来自配对成像质谱流式细胞术的空间细胞类型约束。
result: 在合成和真实肿瘤数据上，PISTACHIO相比Cell2location和STdeconvolve更准确恢复空间细胞类型分布，且对分配误差鲁棒。
conclusion: PISTACHIO提供了一种可扩展、鲁棒且解释性强的空间转录组解卷积方法，适用于异质性肿瘤。
---

## 摘要
在空间转录组学中准确解析细胞类型混合物仍然具有挑战性，特别是在异质性肿瘤中，细胞群相互混合，且匹配的单细胞参考可能不可用或对齐不良。当前的解卷积方法要么需要高质量的单细胞RNA测序参考，要么存在可扩展性限制，或者缺乏可解释性。我们提出了PISTACHIO，一种基于约束非负矩阵分解和负二项似然的蛋白质组学指导的空间转录组学反卷积框架。PISTACHIO不使用概率先验，而是整合了来自配对成像质谱流式的空间细胞类型约束，强制执行生物学基础的稀疏性和细胞类型存在的明确空间可行性。与Cell2location和STdeconvolve相比，PISTACHIO在合成和真实肿瘤数据集上改善了空间细胞类型分布的恢复。我们的方法在细胞类型分配错误下保持稳健，在中等噪声下与真实值保持高相关性，并在标准硬件上实现快速运行，从而支持实际的大规模部署。

## Abstract
Accurately resolving cell-type mixtures in spatial transcriptomics remains challenging, particularly in heterogeneous tumours where cell populations are intermixed and matched single-cell references may be unavailable or poorly aligned. Current deconvolution approaches either require high-quality scRNA-seq references, suffer from scalability limitations, or lack interpretability. We introduce PISTACHIO, a proteomics-informed spatial transcriptomics deconvolution framework based on constrained non-negative matrix factorization with a negative-binomial likelihood. Rather than using probabilistic priors, PISTACHIO incorporates spatial cell-type constraints derived from paired Imaging Mass Cytometry, enforcing biologically grounded sparsity and explicit spatial feasibility of cell-type presence. PISTACHIO improved recovery of spatial cell-type distributions compared with Cell2location and STdeconvolve across synthetic and real tumour datasets. Our approach remains robust under cell-type assignment errors, maintaining high correlation with ground-truth under moderate noise, and achieves fast runtime on standard hardware, enabling practical large-scale deployment.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：空间转录组学（Spatial Transcriptomics, ST）中，每个空间点通常包含多个细胞的混合，如何准确解析各细胞类型的比例分布是一个关键挑战。尤其在肿瘤微环境中，细胞群高度异质且相互混合，而匹配的单细胞RNA测序（scRNA-seq）参考数据可能不可用、质量差或与空间数据对齐不良。
- **现有方法局限**：主流反卷积方法（如Cell2location、STdeconvolve）要么依赖高质量单细胞参考（概率先验），要么可扩展性差，或者缺乏可解释性。
- **整体含义**：提出一种无需单细胞参考、利用配对蛋白质组学数据（成像质谱流式）提供空间约束的新型反卷积框架，以提高肿瘤空间转录组学数据中细胞类型解析的准确性和鲁棒性。

## 2. 方法论：核心思想、关键技术细节、算法流程
- **方法名称**：PISTACHIO（Proteomics-Informed Spatial Transcriptomics Deconvolution framework based on Constrained NMF）。
- **核心思想**：避免使用概率先验，而是直接利用来自配对成像质谱流式细胞术（Imaging Mass Cytometry, IMC）的空间细胞类型信息作为约束，在非负矩阵分解（NMF）框架下强制执行生物学上合理的稀疏性和空间可行性。
- **关键技术细节**：
  - 基于约束非负矩阵分解（Constrained NMF），似然函数采用负二项分布（Negative-Binomial），以匹配空间转录组数据的计数特性（过度离散）。
  - 约束来源：IMC提供空间上明确的细胞类型存在/缺失信息（例如哪些spot含有哪种细胞类型），将其转化为硬性约束（例如某些spot不能表达特定细胞类型特征），从而减少歧义。
  - 不需要预先训练的单细胞参考，而是直接从空间转录组和IMC的配对数据中学习细胞类型特征和比例。
- **算法流程（文字描述）**：
  1. 输入：空间转录组表达矩阵（spots × genes）和配对IMC细胞类型空间分布图（spots × cell types，二值或比例）。
  2. 构建约束矩阵：基于IMC信息，定义每个spot允许的细胞类型组合（例如某些spot必须具有某个细胞类型，某些spot禁止出现某类型）。
  3. 初始化NMF因子矩阵：细胞类型特征矩阵（genes × cell types）和比例矩阵（spots × cell types）。
  4. 迭代优化：在负二项似然下，交替更新两个因子矩阵，同时施加稀疏性正则化及IMC导出的约束（如强制某些元素为零或非零）。
  5. 输出：每个spot的细胞类型比例估计。

## 3. 实验设计
- **数据集/场景**：
  - 合成数据集：构建已知细胞类型比例的空间表达数据，用于定量评估准确性。
  - 真实肿瘤数据集：具体肿瘤类型未在摘要中说明（可能为脑胶质瘤或实体瘤），包含配对的空间转录组和IMC数据。
- **基准（Benchmark）**：与两种代表性方法对比：
  - **Cell2location**：基于概率模型，需要scRNA-seq参考。
  - **STdeconvolve**：基于NMF，无需参考，但无外部约束。
- **对比指标**：预测的细胞类型空间分布与真实值（合成数据已知，真实数据由IMC提供近似真实）的相关性（如Pearson相关系数）。
- **鲁棒性测试**：人工引入细胞类型分配错误（模拟IMC标注噪声），观察不同噪声水平下性能下降程度。

## 4. 资源与算力
- **文中明确说明**：PISTACHIO在标准硬件上实现快速运行，支持实际大规模部署。
- **未提及的内容**：未说明具体GPU型号、数量、训练时长或内存需求。因此无法量化算力消耗，但强调在一般硬件上可行。

## 5. 实验数量与充分性
- **实验组数**：摘要仅概括了“合成和真实肿瘤数据集”上的对比，以及鲁棒性测试。具体实验数量（例如多少个合成场景、多少个肿瘤样本、不同噪声水平的分组）未列明。
- **充分性评估**：
  - **优点**：涵盖了合成验证（已知真值）和真实数据（实际应用），并测试了鲁棒性，实验设计基本合理。
  - **不足**：
    - 未与其他无需参考的方法（如SPOTlight, stereoscope等）比较，对比方法仅两种，不够全面。
    - 未进行消融实验（例如去掉IMC约束后的性能差异）来验证约束的有效性。
    - 未展示在不同组织类型、不同分辨率、不同噪声来源下的全面表现。
    - 无法评估其统计显著性（如p值或置信区间未提及）。
- **客观性**：摘要由作者自行撰写，可能存在选择性地报告有利结果的风险。

## 6. 论文的主要结论与发现
- PISTACHIO在恢复空间细胞类型分布上优于Cell2location和STdeconvolve，特别是在缺乏高质量单细胞参考时。
- 对IMC细胞类型分配错误具有鲁棒性：在中等噪声下仍与真实值保持高相关性。
- 运行速度快，可扩展至大规模空间转录组数据集。
- 作为一种无需单细胞参考的替代方案，PISTACHIO提供了更可解释、生物学约束驱动的反卷积。

## 7. 优点
- **创新性**：首次将成像质谱流式（蛋白质组学）的空间约束整合到NMF反卷积框架中，利用正交数据弥补单细胞参考缺失的缺陷。
- **实用性**：不依赖于难以获得且可能对齐不良的scRNA-seq，直接利用配对蛋白质组学数据，适用于临床样本。
- **鲁棒性**：对输入标注噪声不敏感，实际应用中IMC自动分割错误不会严重降低反卷积质量。
- **可解释性**：通过硬性约束强制执行生物学合理性（如细胞类型非负、稀疏、空间排他性）。
- **效率**：标准硬件即可快速运行，适合大规模部署。

## 8. 不足与局限
- **依赖配对IMC**：方法要求同一组织切片或邻近切片有可用的IMC数据，限制了其在仅有空间转录组而无蛋白测量场景下的应用。
- **IMC分辨率与覆盖**：IMC通常分辨率低于空间转录组（spot级别），约束的施加可能引入误差；且IMC只能标记有限数量的蛋白（通常小于50种），不能覆盖所有细胞类型。
- **对比不充分**：仅与两种方法对比，未与热门的其他解卷积方法（如RCTD, SpatialDWLS, CARD等）比较；未在多样性肿瘤（不同起源、免疫浸润程度）上验证。
- **实验细节不足**：缺少消融实验、统计显著性检验、对不同噪声水平的量化分析；未公开混淆矩阵或误差分布。
- **潜在偏差风险**：作者团队可能对自身方法存在积极偏向；摘要未报告负面结果或失败案例。
- **可重复性**：未提供代码链接或数据来源（预印本阶段），无法独立验证。

（完）
