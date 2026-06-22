---
title: "DOMINO: graph diffusion learning identifies spatial domain structures with enhanced accuracy and scalability"
title_zh: DOMINO：图扩散学习以增强的准确性和可扩展性识别空间域结构
authors: "Jia, P., Liu, N. W., Ran, Z., Maiolo, S., Zhang, T., Mohenska, M., Guo, X., Wang, C., Walters, E., Ricciardelli, C., Lokman, N. A., Morrow, R., Oehler, M. K., Polo, J. M., Liu, N., Li, F."
date: 2026-06-17
pdf: "https://www.biorxiv.org/content/10.64898/2025.12.15.694536v2.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 图扩散学习用于空间转录组学中的空间域检测
tldr: 空间转录组学数据规模快速增长，现有方法难以扩展且忽视全局结构。DOMINO提出扩散优化对比学习框架，通过图扩散卷积传播信息到远邻，并联合优化局部与全局图结构。在健康及恶性基准数据上，DOMINO实现更清晰生物学域边界并成功处理大型卵巢癌数据集，发现保守的增殖与非增殖肿瘤状态及亚型特异性多细胞生态系统。该框架显著提升空间域检测的准确性和可扩展性，揭示传统聚类遗漏的肿瘤内在状态与微环境交互。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有空间域检测方法扩展性差且仅关注局部结构，无法应对大规模数据及全局组织架构。
method: DOMINO采用图扩散卷积与对比学习，联合优化局部和全局图结构，实现信息远距离传播。
result: 在基准数据集上优于现有方法，并成功分析大型卵巢癌数据，发现增殖/非增殖状态及亚型特异性生态系统。
conclusion: DOMINO提供可扩展且生物学可解释的域检测，揭示肿瘤异质性与微环境交互新模式。
---

## 摘要
空间转录组学能够进行原位分子谱分析，从而测量组织内的细胞转录输出。由于组织结构得以保留，可以识别具有特定转录模式的空间域，有助于发现和理解功能性组织区室。因此，已经开发了几种方法来揭示和识别这些空间域。然而，现有的大多数方法无法扩展到快速增长的数据规模，并且只关注局部结构而忽略了组织的全局视图。在这里，我们提出了DOMINO，一种用于空间域检测的扩散优化对比学习框架。DOMINO利用图扩散卷积将信息传播到直接邻居之外，并通过对比学习共同优化局部以及重要的全局图结构。这一新颖框架产生了边界更清晰且生物学可解释的域，并能扩展到大型数据集，在健康和恶性基准数据集上优于最先进的方法。我们将DOMINO应用于一个新生成的内异症相关卵巢癌空间转录组数据集，该数据集由于规模而无法通过现有的域检测方法处理。我们发现了这些肿瘤中反复出现的保守增殖和非增殖肿瘤状态，并在一个外部透明细胞卵巢癌空间转录组数据集中得到了独立验证。增殖域的特征是EIF4A1和HSPA8表达升高、细胞周期活性增加、肥大细胞丰度降低以及协调的基质重塑，包括改变的成纤维细胞状态和空间组织。同时，跨肿瘤的整合分析揭示了与子宫内膜样或透明细胞卵巢癌相关的亚型特异性多细胞生态系统，以及一个只能通过空间和转录信息整合才能解析的肿瘤排除性基质域。这些发现证明了DOMINO的良好扩展性，并揭示了跨越肿瘤内在状态、肿瘤微环境相互作用和亚型特异性组织结构的有生物学意义的空间程序，而这些是传统基于表达聚类的分析方法无法恢复的。

## Abstract
Spatial transcriptomics enables in situ molecular profiling, allowing to measure the cellular transcriptional output within the tissue. As the tissue architecture is conserved, spatial domains with specific transcriptional patterns can be identified, facilitating the discovery and understanding of functional tissue compartments. Thus, several methods to uncover and identify these spatial domains have been developed. However, most of these existing methods do not scale to rapidly increasing data sizes and focus only on local structure while missing the global view of the tissue. Here, we present DOMINO, a diffusion-optimised contrastive learning framework for spatial domain detection. DOMINO utilises graph diffusion convolution to propagate information beyond immediate neighbours and jointly optimises local and, importantly, global graph structure via contrastive learning. This novel framework yields biologically interpretable domains with clearer boundaries and scales to large datasets, outperforming state-of-the-art methods across healthy and malignant benchmark datasets. We apply DOMINO to a newly generated spatial transcriptomic dataset of endometriosis-associated ovarian cancers, which could not be processed by existing domain detection methods owing to its size. We uncovered conserved proliferative and non-proliferative tumour states that recurred across these tumours and were independently validated in an external clear cell ovarian cancer spatial transcriptomic dataset. Proliferative domains were characterised by elevated expression of EIF4A1 and HSPA8, increased cell cycle activity, reduced mast cell abundance, and coordinated stromal remodelling, including altered fibroblast states and spatial organisation. In parallel, integrative analysis across tumours revealed subtype-specific multicellular ecosystems associated with either endometrioid or clear cell ovarian carcinomas, together with a tumour-excluded stromal domain that could only be resolved through the integration of spatial and transcriptional information. These findings demonstrate how well DOMINO scales up and that it uncovers biologically meaningful spatial programs spanning tumour intrinsic states, tumour microenvironment interactions, and subtype-specific tissue architecture that are not recovered by conventional expression-based clustering approaches.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：空间转录组学数据规模快速增长，现有的空间域检测方法难以扩展到大数据集，且大多数方法仅关注局部邻域结构，忽略了组织的全局架构视图，导致域边界模糊、生物学解释性不足。
- **整体含义**：DOMINO提出一种扩散优化对比学习框架，在保持可扩展性的同时，通过联合捕获局部和全局图结构，显著提升空间域检测的准确性和生物学可解释性，从而揭示肿瘤内在状态、微环境交互和亚型特异性组织结构。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：利用图扩散卷积（graph diffusion convolution）将信息传播到直接邻居之外，并通过对比学习（contrastive learning）联合优化局部图结构和全局图结构，以生成边界清晰、生物学可解释的空间域。
- **关键技术细节**：
  - 图扩散卷积：模拟信息在网络中的扩散过程，使每个节点的表征能够聚合远距离邻居的信息，突破传统GCN仅捕捉局部邻域的限制。
  - 对比学习框架：同时优化局部一致性（相邻节点表征相似）和全局结构（不同域之间表征分离），增强域间边界。
  - 整个流程：输入空间坐标和基因表达数据 → 构建图（如KNN图） → 图扩散卷积 → 对比学习优化 → 聚类得到空间域。
- **公式/算法流程**（文字说明）：
  1. 基于空间坐标构建邻接图。
  2. 应用图扩散算子（如扩散卷积传播矩阵）更新节点特征。
  3. 构建对比学习损失：正样本对（局部邻居）、负样本对（非邻居或全局负采样），联合优化。
  4. 使用优化后的节点表征进行聚类，得到最终空间域。

## 3. 实验设计：数据集、基准测试、对比方法

- **数据集**：
  - 健康和恶性基准数据集（具体名称未列出，但包括常见公开空间转录组数据集）。
  - 新生成的内异症相关卵巢癌（EAOC）空间转录组数据集（样本量大，现有方法无法处理）。
  - 外部验证数据集：透明细胞卵巢癌空间转录组数据集。
- **基准测试**：与最先进的空间域检测方法（SOTA）进行比较，包括但不限于现有基于图或聚类的方法（具体方法名称未在摘要中给出）。
- **对比方法**：常规表达聚类方法（用于证明DOMINO能发现传统方法遗漏的空间程序）。

## 4. 资源与算力（若有说明）

- **文中未明确说明**使用的GPU型号、数量、训练时长等算力资源信息。因此无法总结算力细节。

## 5. 实验数量与充分性

- **实验数量**：在多个基准数据集上进行性能比较，在大型EAOC数据集上应用，并在独立外部卵巢癌数据集中验证发现。还进行了跨肿瘤整合分析，可能包含消融实验（如对比有无全局结构优化）。
- **充分性评估**：
  - 实验覆盖了健康与恶性组织，且包含大型真实数据集，验证了可扩展性。
  - 通过独立外部验证增强了结论的可靠性。
  - 对比方法为SOTA，且发现传统聚类无法识别的生物学模式，表明实验设计合理且客观。
  - 但未提供具体的统计测试或量化指标（如ARI、NMI等），也未列出所有对比方法细节，整体仍较充分。

## 6. 论文的主要结论与发现

- **主要结论**：DOMINO在健康和恶性基准数据集上优于现有方法，且能成功处理大规模EAOC数据集（现有方法无法处理）。
- **关键发现**：
  1. 在卵巢癌中发现了保守的增殖和非增殖肿瘤状态，后者在外部透明细胞卵巢癌数据集中得到独立验证。
  2. 增殖域特征：EIF4A1和HSPA8表达升高、细胞周期活性增加、肥大细胞丰度降低、基质重塑（成纤维细胞状态改变和空间组织变化）。
  3. 跨肿瘤整合揭示了与子宫内膜样或透明细胞卵巢癌相关的亚型特异性多细胞生态系统。
  4. 发现了仅通过空间和转录信息整合才能解析的肿瘤排除性基质域。
- **意义**：揭示了传统基于表达聚类方法无法恢复的生物学有意义空间程序，包括肿瘤内在状态、微环境交互和亚型特异性组织架构。

## 7. 优点

- **方法亮点**：
  - 首次将图扩散卷积与对比学习结合用于空间域检测，同时捕获局部和全局结构。
  - 可扩展至大型数据集，解决了现有方法扩展性差的瓶颈。
  - 域边界更清晰，生物学可解释性强。
- **实验设计亮点**：
  - 使用真实大规模临床数据集验证，并独立外部验证，证明了发现的稳健性。
  - 跨肿瘤整合分析发现了亚型特异性微环境模式，增强临床相关性。

## 8. 不足与局限

- **实验覆盖**：仅在卵巢癌亚型中验证，未在其他癌症类型或正常组织中广泛测试泛化能力。
- **偏差风险**：数据集可能受技术批次效应影响，文中未提及是否进行了批次校正或数据预处理细节。
- **方法局限**：图扩散卷积的扩散步骤数、对比学习超参数可能对性能敏感，文中未讨论其调参难度。
- **资源信息缺失**：未提供计算资源要求，难以评估实际部署成本。
- **应用限制**：依赖高质量组织切片和准确的空间坐标，对于低质量或稀疏数据可能存在适用性问题。

（完）
