---
title: Proteomics-constrained deconvolution reveals spatial cell-type programs in tumours
title_zh: 蛋白质组约束的反卷积揭示肿瘤中的空间细胞类型程序
authors: "Isik, E. B., Haley, M. J., Anbaki, A. A., Bere, L., Roncaroli, F., Piper Hanley, K., Couper, K., Wedge, D. C., Sellers, R., Baker, A., Oliveira, P., Ashton, J., Bristow, R. G., Alvarez, M. A., Georgaka, S., Rattray, M."
date: 2026-06-22
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.01.729268v2.full.pdf"
tags: ["query:spatialprot"]
score: 8.0
evidence: 将空间转录组与蛋白质组约束整合用于肿瘤解卷积
tldr: 空间转录组学中细胞类型混合物解析在肿瘤异质性场景下存在困难，现有方法依赖高质量单细胞参考或可扩展性差。我们提出PISTACHIO，一种基于负二项似然和约束非负矩阵分解的质谱约束反卷积框架，通过配对成像质谱数据引入空间细胞类型约束。在合成和真实肿瘤数据上，PISTACHIO优于Cell2location和STdeconvolve，对误差鲁棒且运行快速，适用于大规模部署。
source: biorxiv
selection_source: fresh_fetch
motivation: 空间转录组中细胞类型解卷积缺乏高质量参考时准确性不足，且现有方法可扩展性有限。
method: 采用带负二项似然的约束非负矩阵分解，利用配对成像质谱数据提供空间细胞类型约束。
result: PISTACHIO在合成和真实肿瘤数据集上比Cell2location和STdeconvolve更准确地恢复空间细胞类型分布，在中等噪声下保持高相关性。
conclusion: PISTACHIO提出了一种可扩展、鲁棒且无需单细胞参考的空间解卷积方法，适用于肿瘤微环境分析。
---

## 摘要
在空间转录组学中准确解析细胞类型混合仍然具有挑战性，尤其是在异质肿瘤中，细胞群体相互混合，且匹配的单细胞参考可能不可用或对齐不良。当前的反卷积方法要么需要高质量的单细胞RNA测序参考，要么存在可扩展性限制，或者缺乏可解释性。我们提出了PISTACHIO，一种基于约束非负矩阵分解和负二项式似然的蛋白质组学信息空间转录组反卷积框架。PISTACHIO不使用概率先验，而是整合了来自配对成像质谱流式细胞术的空间细胞类型约束，强制实现生物基础的稀疏性和细胞类型存在的明确空间可行性。与Cell2location和STdeconvolve相比，PISTACHIO在合成和真实肿瘤数据集上改善了空间细胞类型分布的恢复。我们的方法在细胞类型分配错误下保持稳健，在中等噪声下与真实值保持高相关性，并在标准硬件上实现快速运行，从而支持实际的大规模部署。

## Abstract
Accurately resolving cell-type mixtures in spatial transcriptomics remains challenging, particularly in heterogeneous tumours where cell populations are intermixed and matched single-cell references may be unavailable or poorly aligned. Current deconvolution approaches either require high-quality scRNA-seq references, suffer from scalability limitations, or lack interpretability. We introduce PISTACHIO, a proteomics-informed spatial transcriptomics deconvolution framework based on constrained non-negative matrix factorization with a negative-binomial likelihood. Rather than using probabilistic priors, PISTACHIO incorporates spatial cell-type constraints derived from paired Imaging Mass Cytometry, enforcing biologically grounded sparsity and explicit spatial feasibility of cell-type presence. PISTACHIO improved recovery of spatial cell-type distributions compared with Cell2location and STdeconvolve across synthetic and real tumour datasets. Our approach remains robust under cell-type assignment errors, maintaining high correlation with ground-truth under moderate noise, and achieves fast runtime on standard hardware, enabling practical large-scale deployment.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：空间转录组学数据中每个捕获点（spot）通常包含多种细胞类型的混合信号，准确解析细胞类型比例（即反卷积）是理解肿瘤微环境异质性的关键。然而，传统反卷积方法依赖高质量的单细胞RNA测序（scRNA-seq）参考，而肿瘤组织中匹配的scRNA-seq参考可能不可用或与空间数据对齐不良；此外，现有方法在可扩展性、可解释性方面也存在不足。
- **研究动机**：为了在不依赖单细胞参考的前提下，利用蛋白质组学数据提供的空间细胞类型约束，开发一种更鲁棒、可扩展且生物可解释的空间反卷积框架。
- **整体含义**：本文提出的PISTACHIO通过整合配对成像质谱（Imaging Mass Cytometry, IMC）的空间约束，实现了无需单细胞参考的、基于负二项似然和约束非负矩阵分解的解卷积，有望在肿瘤微环境分析中大规模部署。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将空间转录组的反卷积建模为约束非负矩阵分解（NMF）问题，利用来自相同组织的配对IMC数据提供空间细胞类型存在的硬约束（生物上合理的稀疏性和空间可行性），并使用负二项式似然拟合计数数据的过度离散特性。
- **关键技术细节**：
  - 模型采用**负二项似然**，适用于空间转录组计数数据的过分散特性。
  - 约束条件来自**IMC数据**：通过IMC获得每个细胞类型的空间分布概率或指示，转化为非负矩阵分解中的可行性掩码（mask），强制只有IMC显示存在某种细胞类型的spot才能分配相应比例（空间稀疏性）。
  - 不使用概率先验（如Cell2location中的变分推断），而是直接施加硬约束，提高了可解释性。
  - 算法流程：输入空间转录组计数矩阵和IMC导出的约束矩阵，通过带约束的非负矩阵分解优化负二项式负对数似然，迭代更新表达谱和比例矩阵。
- **相比现有方法的创新**：避免依赖scRNA-seq参考，同时利用多模态信息（蛋白质组）约束，实现更稳健且快速的反卷积。

### 3. 实验设计

- **使用数据集/场景**：
  - **合成数据集**：模拟生成已知细胞类型比例的合成空间转录组数据（包含不同噪声水平），用于定量评估与真实值（ground truth）的相关性。
  - **真实肿瘤数据集**：包含配对的空间转录组数据与IMC数据（具体肿瘤类型文中未详述，但提及“合成和真实肿瘤数据集”）。
- **基准（Benchmark）**：以模拟生成的真值或IMC推断的细胞类型分布作为ground truth。
- **对比方法**：Cell2location（基于概率的scRNA-seq参考方法）和STdeconvolve（无参考的NMF方法）。
- **评估指标**：与ground truth的相关性（可能是Pearson或Spearman相关系数）以及鲁棒性（在细胞类型分配错误下的表现）。

### 4. 资源与算力

- **文中明确说明**：未提及具体的GPU型号、数量或训练时长。
- **可推断信息**：作者提到“在标准硬件上实现快速运行”，暗示对计算资源要求不高，但具体规格未给出。

### 5. 实验数量与充分性

- **实验组数**：从摘要推断，至少包括：
  - 合成数据实验（可能多个噪声水平或参数设置）。
  - 真实肿瘤数据实验。
  - 鲁棒性测试（引入细胞类型分配错误）。
- **充分性评估**：
  - 优点：覆盖了合成和真实场景，并测试了对噪声和错误分配的鲁棒性，较全面地验证了方法性能。
  - 不足：无法从摘要判断是否进行了消融实验（如移除IMC约束的影响）、不同肿瘤类型的泛化性、更详细的统计显著性检验等。由于缺乏实验细节，整体充分性一般，但符合方法论论文的常见验证范围。

### 6. 论文的主要结论与发现

- PISTACHIO在合成和真实肿瘤数据集上均优于Cell2location和STdeconvolve，更准确地恢复了空间细胞类型分布。
- 在中等噪声水平下，PISTACHIO与真实值的相关性保持较高（提示鲁棒性）。
- PISTACHIO对细胞类型分配错误（来自IMC的误标注）不敏感，具有实际实用性。
- 运行速度快，适合大规模部署。

### 7. 优点

- **新颖的约束策略**：直接利用配对蛋白质组数据（IMC）提供硬约束，无需scRNA-seq参考，降低了方法对单细胞数据的依赖。
- **统计模型恰当**：采用负二项似然，适合计数数据的离散特性，比泊松或高斯模型更合理。
- **鲁棒性**：在多种噪声和错误场景下表现稳定。
- **可解释性**：硬约束使细胞类型分配具有生物学可行性（如相邻spot的细胞类型连续性）。
- **可扩展性**：快速运行时间，可在标准硬件上处理大规模空间数据。

### 8. 不足与局限

- **依赖配对IMC数据**：该方法需要与空间转录组同一组织切片的IMC数据，这在实际临床样本中并非普遍可获得，限制了应用范围。
- **缺乏与更多方法的对比**：仅与Cell2location和STdeconvolve对比，未与SpatialDecon、SPOTlight、CARD等其他流行方法比较，可能影响结论的普适性。
- **实验细节不足**：摘要中未提供具体的数据集规模、细胞类型数量、定量指标的具体值，以及统计显著性检验结果，使客观性评估受限。
- **未讨论IMC约束缺失时的备用方案**：如果IMC与空间转录组配对不良或数据质量差，方法可能失效。
- **偏差风险**：真实肿瘤数据中的ground truth可能来自IMC本身的推测，存在同源偏差风险（用同一模态验证自身）。
- **应用限制**：主要针对肿瘤微环境，对于非肿瘤组织或其他多模态组合（如空间蛋白质组）的适用性未验证。

（完）
