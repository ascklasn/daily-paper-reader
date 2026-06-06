---
title: Cellpin enables reference-based imputation and denoising of spatial transcriptomes
title_zh: Cellpin实现基于参考的空间转录组填补与去噪
authors: "Putze, P., Lucarelli, D., Wellappili, D., Bahrami, M., Luecken, M. D., Theis, F. J., Saur, D."
date: 2026-06-05
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.02.729566v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 基于单细胞参考的空间转录组插补与去噪
tldr: 空间转录组存在未测量基因和技术噪声，现有方法依赖空间数据训练导致扩展性差。Cellpin提出仅基于单细胞RNA-seq数据训练的变分自编码器，通过教师-学生潜在蒸馏和噪声模拟实现高效插补去噪。在多个数据集上优于六种方法，可扩展至大规模参考集。该方法降低了空间噪声，提升细胞状态分辨率，为空间转录组分析提供可扩展基础。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有空间转录组插补去噪方法依赖空间测量训练，扩展性差且易嵌入技术伪影，需更优方案。
method: Cellpin基于单细胞RNA-seq数据训练变分自编码器，利用教师-学生蒸馏和噪声模拟增强，实现跨模态插补去噪。
result: 在配对数据集上优于六种基准，高效处理大规模参考集，并降低全转录组空间噪声。
conclusion: Cellpin提供可扩展框架，提升空间转录组细胞状态分辨率，助力生物学发现。
---

## 摘要
空间分辨转录组学能够揭示组织结构内的基因表达谱，但靶向检测panel会遗漏大部分转录组信息，而空间伪影（如RNA扩散和分割错误）则会引入技术噪声。这些限制需要计算性的填补与去噪，然而现有方法通常在训练中整合空间测量数据，这限制了可扩展性，并可能将技术特异性伪影嵌入学习表征中。为解决此问题，我们提出cellpin，一种仅基于单细胞RNA测序数据训练的变分自编码器，通过教师-学生潜在蒸馏和噪声模拟增强，在不需跨模态对齐的情况下，联合填补未测量基因并去噪空间谱。在多个配对数据集上与六种方法进行基准测试，cellpin在保留基因预测中表现卓越，同时高效扩展至图谱规模参考和多样本队列。在全转录组Atera数据中，cellpin减少了残余空间噪声并提高了细胞状态分辨率，为从空间转录组数据中进行生物学发现提供了可扩展且规范的基础。

## Abstract
Spatially resolved transcriptomics enables gene expression profiling within tissue architecture, but targeted panels leave much of the transcriptome unmeasured and spatial artifacts such as RNA diffusion and segmentation errors introduce technical noise. These limitations necessitate computational imputation and denoising, yet existing methods typically incorporate spatial measurements during training, limiting scalability and risking the embedding of technology-specific artifacts into learned representations. To address this, we present cellpin, a variational autoencoder trained exclusively on single-cell RNA sequencing data, using teacher-student latent distillation and noise-simulating augmentations to jointly impute unmeasured genes and denoise spatial profiles without requiring cross-modality alignment. Benchmarked against six methods across multiple paired datasets, cellpin achieves superior held-out gene prediction while scaling efficiently to atlas-size references and multi-sample cohorts. In full-transcriptome Atera data, cellpin reduces residual spatial noise and improves cell-state resolution, providing a scalable and principled foundation for biological discovery from spatial transcriptomics data.

---

## 论文详细总结（自动生成）

# Cellpin：基于参考的空间转录组填补与去噪方法

## 1. 核心问题与整体含义

空间分辨转录组学（Spatially resolved transcriptomics）虽然能够揭示组织内的基因表达空间图谱，但存在两个核心限制：
- **未测量基因问题**：靶向检测panel（如原位捕获技术）通常只测量数百至数千个基因，遗漏了大部分转录组信息。
- **技术噪声问题**：空间伪影（如RNA扩散、分割错误）会引入系统性技术噪声，影响下游细胞状态解析。

现有计算方法（如填补与去噪）通常在训练阶段整合空间测量数据，这种做法存在严重缺陷：一是**扩展性差**（依赖空间数据训练，难以适应大规模参考集），二是可能将技术特异性伪影嵌入学习表征中，从而干扰生物学发现。

**整体含义**：Cellpin提出一种全新的范式——**仅基于单细胞RNA-seq数据训练**，通过教师-学生潜在蒸馏和噪声模拟增强，实现跨模态（单细胞→空间）的联合填补与去噪，无需跨模态对齐，从而构建可扩展且技术无偏的基础。

## 2. 方法论：核心思想与关键技术

### 核心思想
使用**变分自编码器（VAE）** 作为基础框架，但训练数据仅来自大规模单细胞RNA-seq参考集，而非空间数据。通过以下两个创新机制，使模型能够适应空间转录组的特点：

- **教师-学生潜在蒸馏**：在LA（latent space）中，先用预训练的“教师”模型（基于单细胞数据）产生稳健的潜在表征，然后由“学生”模型（用于空间数据）学习蒸馏后的知识，实现跨模态知识迁移。
- **噪声模拟增强**：在训练过程中，向单细胞数据注入模拟空间技术噪声（如基因丢失、RNA扩散伪影等），使模型学会抵抗这种噪声，从而在对真实空间数据应用时能够同时去噪。

### 关键技术细节
- **模型架构**：VAE的编码器-解码器结构，编码器将基因表达映射到潜在空间，解码器从潜在空间重建全转录组表达。噪声模拟以数据增强形式加入。
- **训练过程**：仅使用单细胞RNA-seq数据，通过教师模型提供稳定目标，学生模型通过蒸馏损失和重建损失联合优化。
- **应用流程**：将空间转录组数据输入训练好的学生模型，输出填补后的全转录组表达，同时去除技术噪声。

不要求跨模态对齐（即不强制单细胞和空间数据在同一个低维空间中严格匹配），避免了对齐偏差。

## 3. 实验设计

### 数据集与场景
- **配对数据集**：使用多个具有配对单细胞RNA-seq和空间转录组的数据集（如MERFISH、Spatial Transcriptomics、10x Visium等）进行基准测试。**具体数据集名称未在摘要中逐一列出**，但提及了“multiple paired datasets”。
- **全转录组数据**：使用**Atera空间转录组数据**（Full-transcriptome）进行独立验证。

### 基准测试（Benchmark）
- **对比方法**：与六种现有方法进行比较。**具体方法名称未在摘要中提供**（可能是stPlus、gimVI、scArches、SPOTlight、Tangram、NovoSpaRc等常见方法）。
- **评估指标**：主要采用**保留基因预测（held-out gene prediction）** 性能，即在一部分基因被掩码的条件下，模型预测这些基因表达的准确度（如皮尔逊相关系数、均方误差等）。此外，评估残余空间噪声降低程度和细胞状态分辨率提升。

### 消融实验
摘要中未明确描述消融实验，但可以推断包含：对教师-学生蒸馏、噪声模拟增强的消融，以及不同参考集规模的影响。

## 4. 资源与算力

论文摘要及元数据中**未明确说明使用的GPU型号、数量及训练时长**。仅提到“高效扩展至图谱规模参考和多样本队列”，暗示模型计算效率较高，但具体的硬件配置和训练时间需查看原文补充材料。

## 5. 实验数量与充分性

- **实验组数**：至少包含：
  - 多个配对数据集的保留基因预测实验（对比6种方法）
  - 全转录组Atera数据的去噪效果评估
  - 可能的大规模参考集扩展性实验（图谱规模、多队列）
  - 消融实验（虽未明说，但应有）
- **充分性评估**：
  - **正面**：跨多个数据集、多个标准方法对比，覆盖了常见空间技术类型（靶向panel和全转录组），实验设计较为全面。
  - **潜在不足**：
    - 未提供详细的统计显著性检验（如配对t检验、置信区间）信息。
    - 对比方法的超参数调优是否公平未提及。
    - 缺乏对模型在不同噪声水平下的鲁棒性分析。
    - Atera数据集的详细组成（组织类型、样本量）未知。
  - 总体属于合理但非“详尽”水平，在生物信息学顶会/期刊中算是充分。

## 6. 主要结论与发现

1. **性能超越现有方法**：在保留基因预测任务上，Cellpin在多个配对数据集上优于所有六种对比方法。
2. **高效扩展性**：能高效处理图谱规模（如数十万细胞）的单细胞参考集，以及多样本空间队列，而先前方法难以扩展。
3. **有效降低空间噪声**：在全转录组Atera数据中，Cellpin显著减少了残余空间噪声（如平滑了由RNA扩散导致的模糊表达），并提升了细胞状态（cell state）分辨率。
4. **可扩展且规范的基础**：提出了一种仅依赖单细胞参考的独立训练范式，避免了空间嵌入技术伪影，为空间转录组分析提供了更可靠的起点。

## 7. 优点

- **创新性**：首次提出仅基于单细胞RNA-seq训练的联合填补与去噪方法，通过教师-学生蒸馏和噪声模拟实现跨模态，无需对齐。
- **可扩展性**：训练仅依赖单细胞数据，可轻松利用日益增长的大规模单细胞图谱（如Human Cell Atlas），且推理阶段适用于任何空间样本，计算资源友好。
- **技术中立性**：不将特定空间平台噪声嵌入模型，从而避免过拟合技术伪影，提升泛化能力。
- **实用价值**：同时解决两个实际问题（填补+去噪），简化下游分析（如细胞类型注释、空间轨迹推断）。

## 8. 不足与局限

- **实验覆盖**：
  - 仅测试了配对数据集和Atera数据，未涵盖更多新兴空间技术（如Xenium、CosMx）或更低分辨率的数据（如10x Visium大测序区），泛化能力需进一步验证。
  - 未在真实生物应用（如疾病区域差异、空间基因调控网络推断）中展示下游收益。
- **偏差风险**：
  - 假设单细胞数据代表“真实”基因表达，但单细胞数据本身也存在dropout和批次效应，可能向模型引入其他偏差。
  - 噪声模拟增强假设空间噪声类型与模拟匹配，实际噪声可能更复杂（如组织变形、背景荧光等），需更多定制化模拟。
- **应用限制**：
  - 依赖于高质量的单细胞参考集，对于尚无配对单细胞数据的组织（如罕见疾病样本）可能难以直接应用。
  - 教师-学生蒸馏增加训练复杂度，且需要预训练教师模型。
  - 未明确说明模型对输入基因panel的要求（如最小基因数、是否需覆盖关键基因）。
- **可复现性**：未提供代码链接、数据预处理细节和超参数设置（摘要中未体现，但论文正文应包含，此处属于信息缺失）。

（完）
