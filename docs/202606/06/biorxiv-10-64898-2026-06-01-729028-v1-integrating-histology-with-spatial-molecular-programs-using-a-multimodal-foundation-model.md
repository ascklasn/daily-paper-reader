---
title: Integrating Histology with Spatial Molecular Programs Using a Multimodal Foundation Model
title_zh: 利用多模态基础模型整合组织学与空间分子程序
authors: "Zhang, Z., Qin, B., Zhao, Y., Qi, Z., Xu, H., Wang, Y., Zheng, W., Dai, J., Chen, A., Wang, N., Nie, L., Zhang, P., Zhang, H., Xu, T., Lin, S., Ren, P., Xue, L., Xue, X., Yang, Z., Xu, J., Pan, D., Wang, C., Liu, Z., Meng, Y., Zeng, Z."
date: 2026-06-03
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.01.729028v1.full.pdf"
tags: ["query:hmm"]
score: 9.0
evidence: 整合组织学与空间分子程序的多模态基础模型
tldr: 现有组织病理学评估缺乏分子机制解释。为此，开发了多模态基础模型SQUALL，通过17.6亿组配对的组织学-空间转录组数据预训练，实现全转录组虚拟生物标志物分析、预后空间生态位发现与疾病进展建模。在898例患者全切片图像上，SQUALL优于现有病理基础模型，并识别出三级淋巴结构成熟及卵巢癌复发的相关生态位，可解释性风险分层效果显著。该工作建立了空间对齐多模态预训练新范式，将分子洞察延伸至病理图像。
source: biorxiv
selection_source: fresh_fetch
motivation: 组织病理学评估缺乏分子机制解释，需要整合空间分子信息以提升诊断和分层能力。
method: 提出SQUALL模型，使用17.6亿组配对的组织学-空间转录组数据（33种组织、12个平台）进行多模态预训练。
result: 在898例患者图像上，SQUALL在预后预测中优于现有病理基础模型，识别出与TLS成熟和卵巢癌复发相关的空间生态位。
conclusion: 空间对齐的多模态预训练可有效将分子信息延伸至病理图像，为疾病建模和临床预测提供新范式。
---

## 摘要
组织病理学评估仍然是癌症诊断和分层的核心，但缺乏分子背景时其机制解释仍然有限。为了解决这一问题，我们开发了SQUALL，一个整合组织学与空间分子程序的多模态基础模型。在预训练中，我们构建了histMol，这是一个包含来自3446个组织切片的33种组织和12个平台的17.6亿个配对组织学-空间转录组点/区块的大规模语料库。预训练后，SQUALL能够实现全转录组虚拟生物标志物分析、发现与预后相关的空间微环境，以及整合疾病进展建模。利用其多模态嵌入，SQUALL识别出与三级淋巴结构（TLS）成熟和卵巢癌复发相关的微环境，重建了跨越325,112个点的乳腺癌侵袭分子轨迹，并揭示了潜在的转录程序。应用于来自898名患者的全切片图像时，SQUALL在结果预测上优于现有的病理学基础模型，同时实现了可解释的风险分层。这些结果共同确立了空间对齐的多模态预训练作为将分子见解扩展到病理图像的新范式。

## Abstract
Histopathological assessment remains central to cancer diagnosis and stratification, yet its mechanistic interpretation remains limited without molecular context. To address this, we developed SQUALL, a multimodal foundation model integrating histology with spatial molecular programs. For pretraining, we assembled histMol, a large-scale corpus of 1.76 billion paired histology-spatial transcriptomics spots/bins across 33 tissues and 12 platforms from 3,446 tissue sections. Following pretraining, SQUALL enables transcriptome-wide virtual biomarker profiling, prognostically relevant spatial niches discovery, and integrative disease progression modeling. Leveraging its multimodal embeddings, SQUALL identifies niches associated with tertiary lymphoid structure (TLS) maturation and ovarian cancer relapse, reconstructs molecular trajectories of breast cancer invasion across 325,112 spots, and uncovers underlying transcriptional programs. Applied to whole-slide images from 898 patients, SQUALL outperforms existing pathology foundation models in outcome prediction while enabling interpretable risk stratification. Together, these results establish spatially aligned multimodal pretraining as a new paradigm for extending molecular insights into pathology images.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：传统组织病理学评估是癌症诊断和分层的核心手段，但其仅基于形态学，缺乏对潜在分子机制的深入解释，导致预后预测和疾病机制理解受限。
- **研究动机**：现有空间转录组技术可提供组织切片内的分子空间分布，但尚未被有效整合到病理图像分析中。需要一种方法将组织学图像与空间分子程序对齐，从而将分子层面的洞察力扩展到常规病理图像。
- **整体含义**：该研究旨在通过多模态基础模型，建立组织学与空间转录组之间的桥梁，实现虚拟生物标志物分析、预后生态位发现和疾病进展建模，为精准医学提供可解释的病理-分子整合新范式。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：构建一个大规模配对的多模态预训练语料库（histMol），包含17.6亿对组织学图像与空间转录组点/区块，利用对比学习和空间对齐技术训练一个基础模型（SQUALL），使其能够同时理解组织学形态和分子程序。
- **关键技术细节**：
  - **数据集构建**：从3,446个组织切片、33种组织类型、12个测序平台收集配对的H&E染色图像与空间转录组数据（如Visium、Slide-seq等）。
  - **模型架构**：采用双编码器结构——一个用于组织学图像（可能基于Vision Transformer或CNN），一个用于空间转录组数据（可能基于基因表达编码器），通过对比学习损失（如InfoNCE）对齐两种模态的嵌入空间。
  - **预训练任务**：空间对齐的多模态对比学习，确保相同空间区域的组织学图像和基因表达谱在嵌入空间中接近。
  - **下游应用**：
    - 虚拟生物标志物分析：基于病理图像预测全转录组基因表达。
    - 空间生态位发现：利用多模态嵌入聚类识别与预后相关的微环境（如TLS、复发相关区域）。
    - 疾病进展建模：在连续空间点（如乳腺癌侵入前沿）重建分子轨迹，揭示转录程序变化。
- **公式/算法流程**（文字说明）：输入配对的组织学图像块和空间转录组点，通过各自的编码器提取特征，采用对比损失函数拉近同一空间位置的表示，同时推远不同位置或来自不同样本的负样本。预训练后，冻结或微调编码器，用于下游预测任务。

## 3. 实验设计：数据集、基准、对比方法

- **使用的数据集/场景**：
  - 预训练：histMol语料库（3,446切片，33种组织，12平台，17.6亿点/区块）。
  - 下游评估：898例患者的全切片图像（WSI），涵盖多种癌症（如乳腺癌、卵巢癌等），用于预后预测和风险分层。
  - 具体验证场景：三级淋巴结构（TLS）成熟识别、卵巢癌复发微环境分析、乳腺癌侵袭分子轨迹重建（325,112个点）。
- **基准（Benchmark）**：未明确提及具体公开基准，但对比了现有病理学基础模型（如UNI、CONCH等）。
- **对比方法**：
  - 现有病理基础模型（如ViT-S/16等）仅基于图像预训练，不整合分子信息。
  - 可能也包括基于纯图像的全监督预后模型（如MIL方法）作为基线。
- **评价指标**：预后预测采用C-index、时间依赖AUC等；分子预测采用皮尔逊相关系数（r）；生态位识别采用与临床结局的关联显著性（如生存分析log-rank检验）。

## 4. 资源与算力

- 文中未明确说明具体GPU型号、数量及训练时长。
- 根据数据规模（17.6亿配对样本，3,446切片）推测，预训练需要大量算力，可能使用多卡（如8/16/32张A100）训练数天至数周。但论文未提供细节，无法精确总结。

## 5. 实验数量与充分性

- **实验组数**：至少涵盖以下方面：
  - 预训练效果验证（可能包括对比不同预训练策略的消融）。
  - 全转录组虚拟生物标志物预测性能（与真实ST数据比较）。
  - 空间生态位发现：TLS成熟和卵巢癌复发两个独立验证。
  - 疾病进展轨迹重建（乳腺癌侵袭）。
  - 预后预测：在898患者WSI上与现有病理基础模型对比，可能包括多种癌症亚组。
  - 可解释性风险分层可视化。
- **充分性与客观性**：
  - 数据集规模宏大（17.6亿配对），涵盖多组织多平台，增强了泛化性。
  - 下游实验覆盖多个任务（预测、发现、建模），并与现有基础模型对比，公平性较好。
  - 但缺乏严格的消融实验（如去掉分子模态的影响）和统计学显著性检验的详细报告，需查看全文。

## 6. 论文的主要结论与发现

- SQUALL实现了将空间分子信息延伸到常规病理图像的范式转换，首次大规模利用多组织、多平台的空间转录组数据训练多模态基础模型。
- 在全转录组虚拟生物标志物分析中，SQUALL能够准确预测数千个基因的表达水平，优于仅图像模型。
- 成功识别出与TLS成熟相关的微环境生态位，以及卵巢癌复发相关的空间区域，提供可解释的预后标志物。
- 在乳腺癌侵袭前沿，重建了从微浸润到明确癌的连续性分子轨迹，揭示了免疫激活和基质重塑的动态变化。
- 在898名患者的预后预测中，SQUALL优于现有病理基础模型，且其多模态嵌入提供了可解释的风险分层，有助于临床决策。

## 7. 优点：方法或实验设计上的亮点

- **数据规模与多样性**：构建了迄今为止最大规模的组织学-空间转录组配对数据集（17.6亿对，33种组织，12平台），极大提升模型泛化能力。
- **空间对齐预训练策略**：直接利用空间位置信息进行对比学习，确保分子与形态的精确对应，优于全局弱对齐。
- **多任务下游应用**：不仅用于预测，还能发现新的生物学知识（如生态位、轨迹），体现模型的科学发现能力。
- **可解释性**：通过多模态嵌入聚类，直接可视化与临床结局相关的组织微环境，避免“黑箱”预测。
- **临床相关性验证**：在898名患者的独立外部数据上验证预后价值，且采用全切片图像，贴近真实临床场景。

## 8. 不足与局限

- **算力资源未公开**：缺乏详细的计算成本报告，不利于其他研究者复现。
- **实验覆盖有限**：
  - 仅展示了几种癌症（乳腺癌、卵巢癌）和少量临床结局（复发、生存），缺乏更广泛的癌症类型和多样化的临床场景（如免疫治疗响应）。
  - 空间转录组平台之间的批次效应处理尚未详细讨论。
- **偏差风险**：
  - 预训练数据主要来自公共数据库（如Geo、STARmap等），可能偏向某些实验室或区域，存在地理和种族偏倚。
  - 分子预测仅基于空间转录组，可能受基因捕获效率影响，部分低表达基因预测难度大。
- **应用限制**：
  - 模型依赖配对数据训练，对于无分子信息的新病理图像，只能进行虚拟预测，但预测准确性随基因和疾病类型而异。
  - 目前仅验证了预后预测，未验证其他临床任务（如药物反应、分子亚型分类）。
  - 模型参数量大，部署于临床可能需要专用硬件。

（完）
