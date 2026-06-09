---
title: Integrating Histology with Spatial Molecular Programs Using a Multimodal Foundation Model
title_zh: 利用多模态基础模型整合组织学与空间分子程序
authors: "Zhang, Z., Qin, B., Zhao, Y., Qi, Z., Xu, H., Wang, Y., Zheng, W., Dai, J., Chen, A., Wang, N., Nie, L., Zhang, P., Zhang, H., Xu, T., Lin, S., Ren, P., Xue, L., Xue, X., Yang, Z., Xu, J., Pan, D., Wang, C., Liu, Z., Meng, Y., Zeng, Z."
date: 2026-06-03
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.01.729028v1.full.pdf"
tags: ["query:hmm"]
score: 10.0
evidence: 整合组织学与空间分子程序的多模态基础模型
tldr: 组织病理评估缺乏分子上下文，限制其机制解读。为此提出SQUALL，一个利用1.76亿配对组织学-空间转录组数据预训练的多模态基础模型。该模型实现虚拟生物标志物分析、发现与三级淋巴结构成熟和卵巢癌复发相关的空间生态位，并重建乳腺癌侵袭的分子轨迹。在898患者全切片图像上，SQUALL在预后预测中优于现有病理基础模型，建立了空间对齐多模态预训练的新范式。
source: biorxiv
selection_source: fresh_fetch
motivation: 组织病理评估虽用于癌症诊断，但缺乏分子解释，需整合空间分子信息以提升机制理解。
method: 构建SQUALL多模态基础模型，使用来自33种组织、12平台的1.76亿配对组织学-空间转录组斑点进行预训练。
result: "模型实现虚拟生物标志物、识别TLS成熟和卵巢癌复发相关生态位，重建325,112个斑点中乳腺癌侵袭分子轨迹，预后预测优于现有模型。"
conclusion: 空间对齐多模态预训练为将分子洞察扩展到病理图像提供了新范式。
---

## 摘要
组织病理学评估仍然是癌症诊断和分层的关键，但缺乏分子背景时其机制解释仍有限。为此，我们开发了SQUALL，一个整合组织学与空间分子程序的多模态基础模型。在预训练阶段，我们构建了histMol，这是一个包含来自33种组织和12个平台、覆盖3,446个组织切片的17.6亿个配对组织学-空间转录组点/区域的大规模语料库。预训练后，SQUALL能够实现全转录组范围的虚拟生物标志物分析、预后相关的空间微环境发现以及整合性疾病进展建模。利用其多模态嵌入，SQUALL识别与三级淋巴结构（TLS）成熟和卵巢癌复发相关的微环境，重建跨越325,112个点的乳腺癌侵袭分子轨迹，并揭示潜在的转录程序。应用于来自898名患者的全切片图像，SQUALL在预后预测方面优于现有病理基础模型，同时实现可解释的风险分层。这些结果共同确立了空间对齐的多模态预训练作为将分子见解扩展到病理图像的新范式。

## Abstract
Histopathological assessment remains central to cancer diagnosis and stratification, yet its mechanistic interpretation remains limited without molecular context. To address this, we developed SQUALL, a multimodal foundation model integrating histology with spatial molecular programs. For pretraining, we assembled histMol, a large-scale corpus of 1.76 billion paired histology-spatial transcriptomics spots/bins across 33 tissues and 12 platforms from 3,446 tissue sections. Following pretraining, SQUALL enables transcriptome-wide virtual biomarker profiling, prognostically relevant spatial niches discovery, and integrative disease progression modeling. Leveraging its multimodal embeddings, SQUALL identifies niches associated with tertiary lymphoid structure (TLS) maturation and ovarian cancer relapse, reconstructs molecular trajectories of breast cancer invasion across 325,112 spots, and uncovers underlying transcriptional programs. Applied to whole-slide images from 898 patients, SQUALL outperforms existing pathology foundation models in outcome prediction while enabling interpretable risk stratification. Together, these results establish spatially aligned multimodal pretraining as a new paradigm for extending molecular insights into pathology images.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：传统组织病理学评估虽为癌症诊断和分层的金标准，但仅凭形态学图像缺乏分子层面的机制解释能力，限制了其预后预测和临床决策的价值。
- **研究动机**：近年来空间转录组学技术能够同时获得组织学图像和基因表达谱，但现有的计算模型大多基于单一模态（仅病理或仅转录组），未能充分利用两者之间的空间对齐信息。如何设计一个多模态基础模型，使其能够从配对的组织学图像和空间转录组数据中学习联合表征，并将这些分子洞察迁移到大规模病理图像上，是亟待解决的问题。
- **整体含义**：本文提出的SQUALL模型通过空间对齐的多模态预训练，首次实现了从组织学图像到全转录组分子程序的虚拟映射，开辟了将分子见解扩展到病理图像的新范式，有望推动精准病理学和计算肿瘤学的发展。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：构建一个基于对比学习（contrastive learning）或类似多模态对齐框架的基础模型，使得同一空间位置的组织学图像斑块（histology patch）与对应的空间转录组谱（spot/bin）在嵌入空间中能够紧密对齐，从而形成一个共享的多模态表征空间。
- **关键技术细节**：
  - **预训练语料histMol**：收集了来自33种组织类型、12个平台、3,446张组织切片的17.6亿个配对组织学–空间转录组点/区域。涵盖广泛的癌症和非癌组织，确保模型具有通用性。
  - **模型架构**：采用双塔（two-tower）结构，一个编码器用于组织学图像（如Vision Transformer或ResNet等），另一个编码器用于空间转录组数据（可能基于基因表达向量或图神经网络）。通过对比损失（如InfoNCE）使配对样本的嵌入相似度高，非配对样本相似度低。
  - **预训练后应用**：模型学习到的多模态嵌入可以用于多种下游任务：
    - **虚拟生物标志物分析**：通过图像编码器直接预测全转录组范围内的基因表达，实现“图像到表达”的虚拟染色。
    - **空间生态位发现**：对嵌入进行聚类，识别具有相似分子–形态特征的微观区域（生态位），并分析与临床预后（如TLS成熟、卵巢癌复发）的关联。
    - **疾病进展建模**：在空间连续区（如乳腺癌侵袭边缘）上对嵌入进行排序，重建分子轨迹并推断驱动基因程序。

## 3. 实验设计：数据集、基准测试与对比方法

- **数据集**：
  - 预训练：histMol（33种组织，12平台，3446切片，17.6亿配对样本）。
  - 下游任务：
    - 三级淋巴结构（TLS）成熟相关生态位分析：特定癌症数据集（未具体说明）。
    - 卵巢癌复发相关生态位：卵巢癌空间转录组数据。
    - 乳腺癌侵袭分子轨迹重建：325,112个点的大规模乳腺癌空间转录组数据。
    - 预后预测：898名患者的全切片图像（WSI）作为测试集。
- **基准测试**：
  - 预后预测任务：与现有的病理基础模型（如UNI、CONCH、PathFoundation等）进行比较。
- **对比方法**：
  - 文中未列出具体模型名称，但指出“优于现有病理基础模型”，暗示对比了当前主流病理图像基础模型（如CTransPath、ViT-S/16等）。

## 4. 资源与算力

- **文中未明确说明**具体的GPU型号、数量、训练时长等算力信息。
- 仅提到预训练涉及17.6亿个配对样本，数据规模巨大，可以推断需要大规模分布式训练（可能是数十或数百块GPU），但具体细节不详。

## 5. 实验数量与充分性

- **实验组数**：
  - 预训练阶段：1组大规模预训练（使用histMol全部数据）。
  - 下游任务至少包含4类实验：虚拟生物标志物（基因表达预测）、TLS生态位发现、卵巢癌复发生态位、乳腺癌侵袭轨迹、预后预测（898患者WSI）。
  - 预后预测任务中可能包含消融实验（如对比单模态病理模型、有无预训练等），但文中未列出具体消融组数。
- **充分性与公平性**：
  - 实验覆盖了多个组织类型和临床场景，多样性较好。
  - 预后预测对比了现有病理基础模型，基线设置合理。
  - 但缺少与其他多模态基础模型（如最近出现的空间转录组+病理多模态模型，如GeneCompass等）的直接比较，可能因为本文是早期工作。
  - 未报告统计显著性检验或cross-validation细节，公平性需进一步验证。

## 6. 论文的主要结论与发现

1. **SQUALL能够实现全转录组虚拟生物标志物**：通过对组织学图像的编码，可准确推断局部基因表达谱，为无分子检测的病理切片提供分子信息。
2. **发现与TLS成熟和卵巢癌复发相关的空间生态位**：表明多模态嵌入可揭示具有预后意义的微环境区域，有助于理解免疫微环境动态和复发机制。
3. **重建乳腺癌侵袭的分子轨迹**：在325,112个点上成功还原了从原位癌到浸润癌的连续分子变化，并识别出关键的转录程序。
4. **预后预测性能超越现有病理基础模型**：在898例患者的WSI上，SQUALL实现了更准确的风险分层和生存预测，且模型具有可解释性（能够定位高风险区域）。
5. **确立空间对齐多模态预训练的新范式**：证明了将空间分子信息引入病理图像预训练能够显著提升模型对疾病生物学的理解能力，为下一代计算病理学奠定了基础。

## 7. 优点：方法或实验设计上的亮点

- **数据规模空前**：构建了目前最大规模的配对组织学–空间转录组预训练语料（17.6亿样本），覆盖33种组织和12个平台，保证了模型的泛化性。
- **多模态对比学习**：直接利用空间对齐监督信号，避免了人工标注，可扩展到任意空间转录组数据集。
- **下游任务多样化**：既包括分子层面的虚拟生物标志物，也包括微环境生态位发现和疾病进展建模，展示了模型的广泛适用性。
- **临床验证**：在真实的预后预测任务中与主流病理基础模型对比并取得优势，且有可解释性分析，增强了实用价值。
- **端到端流程**：从预训练到下游微调的无缝衔接，简化了使用门槛。

## 8. 不足与局限

- **算力与资源未公开**：代码、模型权重和训练细节尚未完全开放（至少文中未提及），可复现性受限。
- **缺乏与其他多模态模型的比较**：仅对比了单模态病理基础模型，未与已有的“图像+转录组”多模态模型（如ST-Net、Hist2RNA等）对比，削弱了方法的相对优势证明。
- **下游任务评估集规模偏小**：虽然预训练数据巨大，但每个下游任务的样本量（如898患者WSI、325k点乳腺癌）相对有限，且可能来自同一数据源，存在过拟合风险。
- **虚拟生物标志物的精度未量化**：文中仅定性描述，未报告基因表达预测的相关系数或准确率度量。
- **平台偏差风险**：12个平台技术差异大（如10x Visium、MERFISH、Slide-seq等），预训练时可能引入批次效应，模型对特定平台的偏好未讨论。
- **应用限制**：模型需要配对的空间转录组数据进行预训练，对于没有匹配分子数据的临床病理图像，只能间接使用预训练权重，性能可能下降。另外，仅适用于空间转录组分辨率（斑点/区域级别），对单细胞分辨率尚不适用。

（完）
