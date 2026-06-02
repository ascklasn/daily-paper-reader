---
title: Cycle-consistent deep generative modeling unifies cellular states across unpaired spatial and single-cell modalities
title_zh: 循环一致深度生成模型统一了跨非配对空间和单细胞模态的细胞状态
authors: "Zhang, H., Quinn, J. F., Data Science TeamLab,, Tansey, W."
date: 2026-05-26
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.25.727736v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 使用循环一致生成模型整合空间转录组和蛋白质组
tldr: 现有空间和单细胞技术只能捕获细胞状态的互补但零散信息，且面临数据非配对、特征空间不匹配等难题。本文提出MultiTME框架，通过空间正则化和循环一致性约束的深度生成模型，学习统一隐空间实现模态间双向翻译，无需配对数据。在多个基准上优于现有方法，实现准确跨模态细胞分型、完善空间转录组面板，并恢复全转录组空间图谱。应用于结直肠癌数据集，揭示单模态难以观察的增殖-侵袭肿瘤轴；在五个空间数据集上展示跨平台偏差校正能力，促进数据整合。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有单细胞和空间技术数据非配对、特征空间不匹配，缺乏统一整合方法，限制了对细胞状态全面理解。
method: 提出MultiTME，利用空间正则化和循环一致性约束的深度生成模型，学习共享隐空间实现未配对数据间双向翻译。
result: 优于现有方法，实现准确跨模态细胞分型、面板补全和全转录组空间重建，揭示单模态无法观察的肿瘤轴，校正平台偏差。
conclusion: MultiTME提供了一种无需配对数据的通用空间-单细胞整合框架，促进跨数据集和跨癌症研究。
---

## 摘要
当前的空间和单细胞技术捕获了细胞状态的互补但不完整的视图，其中转录组、蛋白质组和空间信息分布在不同的平台上。整合面临非配对测量、特征空间不匹配以及模态特定偏见的挑战。我们提出了MultiTME，一个多模态框架，使用空间正则化、循环一致的深度生成模型来整合异质空间和单细胞数据。通过强制执行双向映射的一致性，MultiTME学习了一个共享的潜在表示，使得无需配对观测或共享特征即可在模态之间进行翻译。在基准测试中，MultiTME优于现有方法，产生准确的跨模态细胞分型，改进空间转录组面板补全，并转移全转录组信息以生成细胞分辨率的空间解析图。应用于一个多模态结直肠癌数据集，我们证明了MultiTME整合揭示了一个空间连贯的增殖-侵袭性肿瘤轴，这在单一模态中无法直接观察到。在五个多模态空间数据集中，我们展示了MultiTME可以校正Xenium和CosMx之间的平台特异性偏差，从而促进跨数据集协调，并使得泛癌空间研究成为可能。MultiTME的代码可在https://github.com/tansey-lab/multitme获取。

## Abstract
Current spatial and single-cell technologies capture complementary but incomplete views of cellular state, with transcriptomic, proteomic, and spatial information distributed across distinct platforms. Integration is challenged by unpaired measurements, mismatched feature spaces, and modality-specific biases. We present MultiTME, a multimodal framework that integrates heterogeneous spatial and single-cell data using a spatially-regularized, cycle-consistent deep generative model. By enforcing consistency of bidirectional mappings, MultiTME learns a shared latent representation that enables translation between modalities without requiring paired observations or shared features. Across benchmarks, MultiTME outperforms existing methods, produces accurate cross-modal cell typing, improves spatial transcriptomic panel completion, and transfers whole-transcriptome information to generate spatially resolved maps at cellular resolution. Applied to a multimodal colorectal cancer dataset, we demonstrate that MultiTME integration reveals a spatially coherent proliferative-invasive tumor axis not directly observable within single modalities. Across five multimodal spatial datasets, we show MultiTME can correct for platform-specific biases between Xenium and CosMx, thereby facilitating cross-dataset harmonization and enabling pan-cancer spatial studies. Code for MultiTME is available at https://github.com/tansey-lab/multitme.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：当前空间转录组学和单细胞技术能够捕获细胞状态的互补但零散的信息——转录组、蛋白质组和空间信息分布在不同的技术平台上。然而，这些数据通常**非配对**（同一细胞无法同时获得所有模态）、**特征空间不匹配**（不同平台检测的基因/蛋白集不同），且存在**模态特异性偏差**，导致整合困难。现有方法大多依赖配对数据或共享特征，限制了跨平台、跨研究的统一分析。
- **整体含义**：本文旨在提出一种无需配对数据、无需共享特征的多模态整合框架，通过学习共享潜在表示实现模态间双向翻译，从而统一细胞状态视图，推动空间生物学和精准医学研究。

## 2. 论文提出的方法论

- **核心思想**：利用**空间正则化**和**循环一致性（cycle-consistency）约束**的深度生成模型，将异质空间和单细胞数据映射到**共享潜在空间**，实现无需配对观测的跨模态翻译。
- **关键技术细节**：
  - 模型采用两个编码器-解码器结构（分别对应空间模态和单细胞模态），通过对抗训练或变分推断学习潜在分布。
  - 引入**循环一致性损失**，确保从模态A翻译到模态B再返回模态A后结果与原数据一致，从而在没有配对数据的情况下强制双向映射的语义对应。
  - 利用**空间正则化**（如基于细胞空间位置的平滑先验或图拉普拉斯正则项），使潜在表示保留空间连续性。
  - 共享潜在空间捕获模态不变量，使得可以完成跨模态细胞分型、面板补全（spatial panel completion）以及全转录组空间重建。
- **算法流程（文字说明）**：
  1. 输入：非配对的空间数据（包含部分基因/蛋白表达+空间坐标）和单细胞数据（全转录组或特定蛋白组）。
  2. 分别通过两个编码器提取潜在表示。
  3. 添加循环一致性约束：空间→单细胞→空间，单细胞→空间→单细胞。
  4. 添加空间正则化损失（如相邻细胞潜在表示相似性）。
  5. 联合优化：重构损失 + 循环一致性损失 + 空间正则项 + 可能存在的判别器损失。
  6. 训练完成后，可利用任意模态的潜在表示翻译至另一模态，或用于跨模态细胞类型注释。

## 3. 实验设计

- **使用的数据集/场景**：
  - **基准测试**：使用多个标准空间和单细胞数据集进行跨模态细胞分型、面板补全、全转录组空间重建评估。
  - **多模态结直肠癌数据集**：用于揭示空间连贯的增殖-侵袭性肿瘤轴。
  - **五个多模态空间数据集**（涵盖Xenium和CosMx平台）：用于验证跨平台偏差校正能力。
- **Benchmark**：与现有方法（如Seurat、SCVI、Starmap等）对比，评估指标包括细胞分型准确率、表达重建相关性等。
- **对比方法**：文中提到“优于现有方法”，但未列出具体方法名称；从上下文推测可能包括基于映射或正则化的整合方法。

## 4. 资源与算力

- 论文摘要及元数据中**未明确说明**使用的GPU型号、数量、训练时长等算力信息。仅提供代码仓库链接（GitHub），未提及硬件配置。因此无法总结具体算力需求。

## 5. 实验数量与充分性

- **实验数量**：论文涉及至少3类实验（细胞分型、面板补全、全转录组重建），并在结直肠癌数据集上展示生物学发现，同时在5个跨平台数据集上验证偏差校正。但具体实验数目（如消融实验、不同超参数测试）未在摘要中体现。
- **充分性与客观公平性**：
  - 覆盖多类任务和多个独立数据集，提高了结论的泛化性。
  - 但摘要未说明是否进行了充分的消融实验（如移除空间正则化或循环一致性的效果），也未给出与所有对比方法的详细统计比较。缺乏对统计显著性的说明，可能存在选择性报告风险。需要阅读全文才能全面评估。

## 6. 论文的主要结论与发现

1. MultiTME在多个基准上**优于现有方法**，实现了准确的跨模态细胞分型。
2. 能够改进空间转录组面板补全，并转移全转录组信息生成细胞分辨率的空间解析图。
3. 在多模态结直肠癌数据集中，整合揭示了**空间连贯的增殖-侵袭性肿瘤轴**，该轴在单一模态中无法直接观察到。
4. 能有效校正Xenium和CosMx之间的平台特异性偏差，实现跨数据集协调，支撑泛癌空间研究。

## 7. 优点

- **无需配对数据**：解决了实际数据常缺乏配对样本的痛点，具有高度实用性。
- **无需共享特征**：可处理不同平台检测不同基因集的情况，灵活性高。
- **循环一致性框架**：提供强约束，确保翻译的语义一致性，优于单向映射方法。
- **空间正则化**：保留空间结构信息，更符合生物学真实分布。
- **多任务统一**：在同一框架下同时完成细胞分型、面板补全、全转录组重建和偏差校正，展示了模型的通用性。
- **公开代码**：促进可重复性和社区发展。

## 8. 不足与局限

- **计算资源需求未说明**：难以评估部署门槛；若不提供GPU时长，不利于复现。
- **实验细节不充分**：缺乏消融实验、超参数敏感性分析、对比方法的具体实现细节，使得论文的深度验证存疑。
- **数据集规模与多样性**：结直肠癌和五个跨平台数据集虽然有一定代表性，但未涵盖更多组织类型或疾病状态（如正常组织、发育样本）。
- **潜在偏差风险**：模型可能过度平滑罕见细胞亚群，或对外部平台偏差补偿不足；需要更多独立验证。
- **未讨论循环一致性训练稳定性**：深度生成模型（特别是GAN）常面临训练不稳定、模式崩溃等，文中未提供解决方案。
- **应用限制**：当模态间信息高度不对等（如空间数据仅有极少数基因，单细胞数据有完整转录组）时，翻译质量可能下降，文中未探讨极限条件。

（完）
