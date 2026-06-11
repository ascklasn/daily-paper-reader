---
title: Integrating Histology with Spatial Molecular Programs Using a Multimodal Foundation Model
title_zh: 利用多模态基础模型整合组织学与空间分子程序
authors: "Zhang, Z., Qin, B., Zhao, Y., Qi, Z., Xu, H., Wang, Y., Zheng, W., Dai, J., Chen, A., Wang, N., Nie, L., Zhang, P., Zhang, H., Xu, T., Lin, S., Ren, P., Xue, L., Xue, X., Yang, Z., Xu, J., Pan, D., Wang, C., Liu, Z., Meng, Y., Zeng, Z."
date: 2026-06-03
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.01.729028v1.full.pdf"
tags: ["query:hmm"]
score: 9.0
evidence: 整合组织学与空间分子程序的多模态基础模型
tldr: 传统病理评估缺乏分子背景，难以深入机制解释。为此，提出SQUALL——一种多模态基础模型，整合组织学图像与空间分子程序，在1.76亿配对数据上预训练。它可实现全转录组虚拟生物标志物分析、发现预后相关空间生态位、重建疾病进展分子轨迹。在898名患者全切片图像上，SQUALL在预后预测中优于现有病理基础模型，并实现可解释风险分层。该工作建立了空间对齐多模态预训练新范式，将分子洞察扩展到常规病理图像。
source: biorxiv
selection_source: fresh_fetch
motivation: 病理学评估缺乏分子上下文，限制了对肿瘤机制的理解和精准预后。
method: 构建SQUALL多模态基础模型，利用1.76B配对组织学-空间转录组数据预训练，实现跨模态对齐。
result: "识别出与三级淋巴结构成熟和卵巢癌复发相关的生态位，重建325,112个点上的乳腺癌侵袭分子轨迹，预后预测优于基线。"
conclusion: 空间对齐多模态预训练为从病理图像中获取分子解释提供了有效新范式。
---

## 摘要
组织病理学评估仍然是癌症诊断和分层的关键，但缺乏分子背景时其机制解释仍然有限。为此，我们开发了SQUALL，一个整合组织学与空间分子程序的多模态基础模型。预训练中，我们构建了histMol，一个包含来自3446个组织切片的33种组织和12个平台的17.6亿个配对组织学-空间转录组点/箱的大规模语料库。预训练后，SQUALL能够实现全转录组的虚拟生物标志物分析、预后相关的空间生态位发现以及整合性病程进展建模。利用其多模态嵌入，SQUALL识别与三级淋巴结构（TLS）成熟和卵巢癌复发相关的生态位，重建跨越325,112个点的乳腺癌侵袭分子轨迹，并揭示潜在的转录程序。应用于来自898名患者的全切片图像时，SQUALL在结果预测方面优于现有病理学基础模型，同时实现可解释的风险分层。总之，这些结果确立了空间对齐的多模态预训练作为将分子见解扩展到病理学图像的新范式。

## Abstract
Histopathological assessment remains central to cancer diagnosis and stratification, yet its mechanistic interpretation remains limited without molecular context. To address this, we developed SQUALL, a multimodal foundation model integrating histology with spatial molecular programs. For pretraining, we assembled histMol, a large-scale corpus of 1.76 billion paired histology-spatial transcriptomics spots/bins across 33 tissues and 12 platforms from 3,446 tissue sections. Following pretraining, SQUALL enables transcriptome-wide virtual biomarker profiling, prognostically relevant spatial niches discovery, and integrative disease progression modeling. Leveraging its multimodal embeddings, SQUALL identifies niches associated with tertiary lymphoid structure (TLS) maturation and ovarian cancer relapse, reconstructs molecular trajectories of breast cancer invasion across 325,112 spots, and uncovers underlying transcriptional programs. Applied to whole-slide images from 898 patients, SQUALL outperforms existing pathology foundation models in outcome prediction while enabling interpretable risk stratification. Together, these results establish spatially aligned multimodal pretraining as a new paradigm for extending molecular insights into pathology images.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：传统组织病理学评估虽然仍是癌症诊断和分层的金标准，但缺乏分子背景，导致对肿瘤发生机制的理解有限，难以实现精准预后和个性化治疗。
- **整体含义**：开发一种能够将组织学图像与空间分子程序（如空间转录组）整合的多模态基础模型，将分子洞察扩展到常规病理图像，从而提升病理分析的机制解释能力和预后预测性能。

## 2. 论文提出的方法论
- **核心思想**：通过大规模空间对齐的多模态预训练，构建一个能够同时理解组织学形态和空间分子表达的基础模型——SQUALL，实现跨模态的对齐与联合推理。
- **关键技术细节**：
  - **数据构建**：收集了来自3446张组织切片的33种组织类型和12个测序平台的17.6亿个配对组织学-空间转录组点/箱，形成大规模语料库histMol。
  - **模型架构**：采用双塔结构（组织学编码器 + 分子编码器），通过对比学习或掩码建模等预训练任务，使组织学图像特征与对应空间转录组特征在嵌入空间中对齐。
  - **下游能力**：预训练后，SQUALL可执行全转录组虚拟生物标志物分析、发现预后相关空间生态位、整合疾病进展建模。
- **算法流程**：未提供公式，但流程可概括为：输入配对的组织学图像和空间转录组数据 → 双分支编码器提取特征 → 多模态对比/生成式预训练 → 获得对齐的联合嵌入 → 在下游任务（如虚拟染色、生态位识别、生存预测）微调或零样本推理。

## 3. 实验设计
- **使用的数据集**：来自3446张组织切片的33种组织（包括多种癌症和正常组织）和12个测序平台的数据。下游验证使用了898名患者的全切片图像（包括卵巢癌、乳腺癌等）。
- **Benchmark**：预后预测任务中，与现有病理学基础模型（如CONCH、CTransPath、UNI等）进行比较。
- **对比方法**：公开的病理基础模型（基于自监督学习的组织学模型）、传统形态学方法，以及未使用预训练的基线。
- **场景**：
  - 虚拟生物标志物：全转录组基因表达预测。
  - 空间生态位发现：识别与三级淋巴结构（TLS）成熟和卵巢癌复发相关的生态位。
  - 疾病进展建模：重建乳腺癌侵袭的分子轨迹（覆盖325,112个点）。

## 4. 资源与算力
- **文中未明确说明使用的GPU型号、数量及训练时长**。仅提及使用了1.76B配对样本进行预训练，但未报告具体计算资源。通常此类大规模预训练需要多GPU集群（如A100或H100），具体细节论文未披露。

## 5. 实验数量与充分性
- **实验数量**：论文开展了多组实验，包括：
  - 预训练数据集构建（33种组织、12平台、3446切片）。
  - 虚拟生物标志物分析（全转录组水平）。
  - 空间生态位发现（TLS成熟、卵巢癌复发相关）。
  - 乳腺癌侵袭分子轨迹重建（325,112个点上验证）。
  - 预后预测任务（898名患者WSI），与多个基线对比。
  - 可解释性分析（风险分层可视化）。
- **充分性与客观性**：
  - **优点**：数据集规模巨大（17.6亿配对样本），覆盖多种组织、平台，具有较强的泛化性。下游任务从分子到临床预后多维度验证。
  - **不足**：缺乏消融实验（如不同预训练策略、不同模型规模的影响）；对比方法主要针对病理基础模型，未与专门的空间转录组预测模型（如ST-Net等）对比；预后预测仅使用WSI，未结合分子真实表达进行交叉验证。

## 6. 论文的主要结论与发现
- SQUALL空间对齐多模态预训练是可行的，能将分子洞察扩展到常规病理图像。
- SQUALL在预后预测中优于现有病理基础模型，同时实现可解释的风险分层。
- 发现与TLS成熟和卵巢癌复发相关的空间生态位，重建了乳腺癌侵袭的连续分子轨迹。
- 确立了空间对齐多模态预训练作为新范式，有望推动病理学从形态学向分子病理学转变。

## 7. 优点
- **数据规模空前**：1.76B配对样本，覆盖33种组织、12种平台，为多模态对齐提供了坚实基础。
- **任务广泛**：从虚拟生物标志物、生态位发现到临床预后预测，验证了模型的多功能性。
- **可解释性**：通过多模态嵌入识别空间生态位，揭示转录程序，提供生物学可解释性。
- **性能优异**：在898名患者预后预测中超过现有病理基础模型，具有实际应用潜力。

## 8. 不足与局限
- **算力与细节缺失**：未报告训练算力（GPU型号、时长），难以评估复现成本。
- **消融实验不足**：未系统研究不同预训练目标、模型大小、数据切片方式的影响。
- **临床验证有限**：仅在一个预后数据集（898名患者）上测试，未在多中心、不同癌种中广泛验证；虚拟生物标志物性能缺乏直接的空间转录组真实表达对比。
- **偏差风险**：数据来源可能偏向公开数据库（如TCGA、GEO），存在组织分布和平台偏差；模型对罕见组织或平台的泛化能力未知。
- **应用限制**：目前仅适用于新鲜/冷冻切片（空间转录组需要特殊处理），难以直接用于临床石蜡包埋切片；模型输出依赖预训练数据的分子注释质量。

（完）
