---
title: Multi-Sample and Multi-Group Spatial Colocalization Analysis Using PANORAMIC
title_zh: 使用PANORAMIC进行多样本和多组空间共定位分析
authors: "Chang, J., Perez, A. E., Molina, P., Khurana, R., Zhang, W., Tian, L., Plevritis, S."
date: 2026-06-01
pdf: "https://www.biorxiv.org/content/10.1101/2025.09.18.677135v3.full.pdf"
tags: ["query:spatialprot"]
score: 8.0
evidence: 空间共定位分析及不确定性量化
tldr: 空间组学研究常忽略样本内空间估计的不确定性，导致异质性队列推断失真。PANORAMIC框架通过边缘校正邻域富集估计局部共定位，空间自举量化不确定性，并利用多水平随机效应荟萃分析传播不确定性。模拟实验证明其优于传统方法；在结直肠癌样本中，识别出克罗恩样反应肿瘤中更强的B/T细胞共定位和更紧密的免疫组织。该工作为传播样本内不确定性以提升队列推断准确性提供了新工具。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有空间组学方法忽略样本内空间估计的不确定性，在异质性队列中导致推断失真，需要量化并传播该不确定性。
method: PANORAMIC：边缘校正邻域富集估计局部共定位，空间自举量化样本内不确定性，多水平随机效应荟萃分析传播至队列水平。
result: 模拟中改善了不确定性恢复；应用于结直肠癌数据，发现克罗恩样反应肿瘤中B/T细胞共定位更强且免疫组织更紧密。
conclusion: 传播样本内空间不确定性可提升空间组学队列推断的准确性。
---

## 摘要
动机：空间组学研究比较样本间的细胞-细胞组织，但大多数方法在将样本水平的空间估计视为无误差的同时，对样本间变异性进行建模。忽略样本内不确定性可能会扭曲异质性队列的推断，因此需要明确量化并将这种不确定性传播到队列级分析中的方法。结果：我们提出了PANORAMIC，一个用于空间共定位分析的层次化框架，该框架使用边缘校正的邻域富集来估计局部细胞类型共定位，使用空间自举来量化样本内不确定性，并使用多水平随机效应荟萃分析将这种不确定性传播到样本、患者和条件中。在模拟中，相对于朴素估计量，PANORAMIC在各种空间设置和渐进数据退化下改善了样本内不确定性和样本间异质性的恢复。应用于通过多重免疫荧光成像分析的结直肠癌组织微阵列，PANORAMIC在具有克罗恩样反应的肿瘤中识别出比具有弥漫性炎症浸润的肿瘤更强的B细胞和T细胞共定位，以及更紧密的高阶免疫组织，与免疫聚集体一致。这些结果表明，传播样本内空间不确定性可以改善空间组学研究中的队列级推断。可用性和实现：PANORAMIC作为开源R包发布，网址为https://github.com/plevritis-lab/panoramic。

## Abstract
Motivation: Spatial omics studies compare cell-cell organization across samples, but most methods model between-sample variability while treating sample-level spatial estimates as error-free. Overlooking within-sample uncertainty can distort inference in heterogeneous cohorts, motivating methods that explicitly quantify and propagate this uncertainty into cohort-level analyses. Results: We present PANORAMIC, a hierarchical framework for spatial colocalization analysis that uses edge-corrected neighborhood enrichment to estimate local cell-type colocalization, spatial bootstrapping to quantify within-sample uncertainty, and multilevel random-effects meta-analysis to propagate this uncertainty across samples, patients, and conditions. In simulations, PANORAMIC improved recovery of within-sample uncertainty and between-sample heterogeneity relative to naive estimators across diverse spatial settings and progressive data degradation. Applied to a colorectal cancer tissue microarray profiled by multiplexed immunofluorescence imaging, PANORAMIC identified stronger B- and T-cell colocalization in tumors with Crohn's-like reaction than in tumors with diffuse inflammatory infiltration, together with tighter higher-order immune organization consistent with immune aggregates. These results show that propagating within-sample spatial uncertainty can improve cohort-level inference in spatial omics studies. Availability and Implementation: PANORAMIC is released as an open-source R package at https://github.com/plevritis-lab/panoramic.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义

- **研究动机**：空间组学研究（如多重免疫荧光成像）通过比较样本间的细胞-细胞组织来揭示生物学机制。然而，现有方法在建模样本间变异性的同时，往往将每个样本内估计出的空间共定位指标视为无误差的确定值。这种忽略样本内不确定性的做法，在异质性队列（如结直癌不同免疫反应亚型）中会导致统计推断失真（例如低估或高估组间差异），进而影响生物学结论的可靠性。
- **整体含义**：需要开发能够明确量化每个样本内空间估计的不确定性，并将该不确定性传播到队列级别（样本、患者、条件）的层次化分析框架，以提升空间组学研究结论的准确性和可重复性。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：通过边缘校正的邻域富集估计局部细胞类型共定位，利用空间自举（spatial bootstrapping）量化样本内不确定性，再通过多水平随机效应荟萃分析将不确定性逐层传播至更高分析级别。
- **关键技术细节**：
  - **局部共定位估计**：使用边缘校正的邻域富集（edge-corrected neighborhood enrichment）计算每个细胞周围特定细胞类型的富集程度，避免边缘效应偏差。
  - **样本内不确定性量化**：采用空间自举（重采样细胞位置或采用保留空间结构的 bootstrap 方法）生成多个重采样数据集，在每个重采样上重新计算共定位估计，从而获得估计的分布和标准误。
  - **多水平随机效应荟萃分析**：构建层次模型，将样本内不确定性（从空间自举获得）作为已知方差，在各水平（细胞 → 样本 → 患者 → 条件）引入随机效应，实现不确定性的传播和组间差异的假设检验。
- **算法流程**（文字说明）：
  1. 输入：多个样本的空间坐标和细胞类型标签。
  2. 对每个样本：计算边缘校正邻域富集得分 → 执行空间自举（B次）→ 得到每个细胞或每个区域共定位估计的样本内方差。
  3. 构建多水平随机效应模型：将每个样本的共定位指标作为响应，其样本内方差作为第一层误差；患者、条件等作为随机效应层。
  4. 使用限制性最大似然（REML）或贝叶斯方法估计模型参数，得到条件间差异的估计及其置信区间。
  5. 输出：条件间共定位差异的显著性检验、不确定性传播后的效应量。

## 3. 实验设计

- **使用的数据集/场景**：
  - **模拟数据**：生成多种空间设置（不同细胞密度、不同共定位强度、不同样本内异质性）并逐步退化数据质量（减少细胞数量、增加噪声等），测试不同条件下方法的鲁棒性。
  - **真实数据**：结直肠癌组织微阵列（TMA），通过多重免疫荧光成像获得，包含两类肿瘤微环境：克罗恩样反应（Crohn's-like reaction, CLR）和弥漫性炎症浸润（diffuse inflammatory infiltration, DII）。
- **Benchmark**：与朴素估计量（即直接使用样本内点估计进行组间比较，忽略样本内不确定性）进行比较。
- **对比方法**：文中没有列出其他外部方法（如SpatialDM、Giotto等）的直接对比，主要与“朴素估计量”作为基线对比，突出自身在不确定性恢复和异质性推断上的改进。

## 4. 资源与算力

- 文中**未明确说明**使用的GPU型号、数量、训练时长等算力信息。PANORAMIC是基于R包实现的，模拟和真实数据分析可能主要在CPU上完成，未提及大规模并行计算或深度学习硬件需求。

## 5. 实验数量与充分性

- **实验数量**：
  - 模拟实验：涵盖了多种空间设置（至少包括不同密度、共定位强度、样本数量等）以及渐进数据退化（如减少细胞数、添加定位噪声等）多个场景。
  - 真实数据应用：一个结直肠癌数据集，包含CLR和DII两组样本，并分析了B细胞和T细胞共定位以及高阶免疫组织结构。
- **充分性与客观性**：
  - 模拟实验设计较为全面，验证了方法在理想条件及退化条件下的表现，支持了方法在不确定性恢复上的优势。
  - 但真实数据仅有一个队列，缺乏独立外部验证集；对比方法仅设为朴素估计量，未与现有其他空间共定位分析工具（如SpatialDM、Giotto、CelliD等）进行系统比较，可能影响了公平性评价。
  - 消融实验方面：文中提到“相对于朴素估计量”，即通过是否纳入样本内不确定性进行对比，可视作消融；但未对自身组件（如不同自举策略、是否使用边缘校正）进行逐一消融。

## 6. 论文的主要结论与发现

1. PANORAMIC在模拟中显著改善了样本内不确定性和样本间异质性的恢复，相较于忽略不确定性的朴素方法，在统计推断上更准确。
2. 在结直肠癌数据中，PANORAMIC识别出克罗恩样反应（CLR）肿瘤中B细胞和T细胞的共定位强度显著高于弥漫性炎症浸润（DII）肿瘤，且高阶免疫组织更紧密（与免疫聚集体一致），这些差异在朴素方法中未能有效捕捉。
3. 传播样本内空间不确定性可以提升空间组学队列级推断的准确性，避免因忽视局部变异而导致的误导性结论。

## 7. 优点

- **方法上的亮点**：
  - 首次系统地将样本内不确定性（通过空间自举量化）引入空间共定位的队列比较中，填补了该领域空白。
  - 采用多水平随机效应荟萃分析，自然地融合了样本、患者、条件多个层级的不确定性，结构简洁且可解释性强。
  - 边缘校正的邻域富集估计减少了边界效应，比常规K函数或L函数更适用于组织切片边缘区域的细胞分析。
- **实验设计上的亮点**：
  - 模拟实验设计了渐进数据退化，检验了方法在不同数据质量下的稳定性，加强了结论的可靠性。

## 8. 不足与局限

- **实验覆盖**：真实数据仅有一个结直肠癌队列（TMA），且只对比了两种免疫反应类型，缺乏其他癌症类型或多种条件（如治疗前后）的验证。
- **对比方法不充分**：仅与朴素估计量比较，未与现有主流空间共定位分析工具（如SpatialDM、Giotto、HMRF、SPARK等）进行基准测试，难以全面评估优越性。
- **偏差风险**：样本内不确定性的量化依赖于空间自举，自举策略（如是否保留细胞间空间依赖性）可能影响结果，文中未详细讨论不同自举方案的敏感性。
- **应用限制**：方法主要针对基于细胞的点模式数据，不直接适用于连续分子成像（如转录本密度图）或空间转录组spot数据；且对大规模数据集（数百万细胞）可能需要高效计算实现（如并行化）以降低耗时。
- **统计假设**：多水平随机效应模型假设样本内方差已知（来自自举），但该方差本身也是估计值，可能引入额外误差；文中未讨论方差估计不稳定时的替代方案。

（完）
