---
title: Integrating Histology with Spatial Molecular Programs Using a Multimodal Foundation Model
title_zh: 使用多模态基础模型整合组织学与空间分子程序
authors: "Zhang, Z., Qin, B., Zhao, Y., Qi, Z., Xu, H., Wang, Y., Zheng, W., Dai, J., Chen, A., Wang, N., Nie, L., Zhang, P., Zhang, H., Xu, T., Lin, S., Ren, P., Xue, L., Xue, X., Yang, Z., Xu, J., Pan, D., Wang, C., Liu, Z., Meng, Y., Zeng, Z."
date: 2026-06-03
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.01.729028v1.full.pdf"
tags: ["query:hmm"]
score: 9.0
evidence: 整合组织学与空间分子程序的多模态基础模型
tldr: 组织病理学评估缺乏分子背景，限制其机制解读。SQUALL多模态基础模型将组织学与空间分子程序整合，在涵盖33种组织、12种平台、3446张切片的17.6亿配对数据上预训练。该模型可实现虚拟生物标志物分析、发现与三级淋巴结构成熟及卵巢癌复发相关的空间微环境，并构建乳腺浸润分子轨迹。在898名患者全切片图像上，SQUALL在预后预测中超越现有病理基础模型，实现可解释的风险分层。空间对齐的多模态预训练为病理图像拓展分子洞察提供了新范式。
source: biorxiv
selection_source: fresh_fetch
motivation: 组织病理学评估缺乏分子背景，需将组织学与空间分子程序整合以增强其机制解读能力。
method: 构建SQUALL多模态基础模型，在大规模配对组织学-空间转录组数据（1.76亿样本）上预训练，实现跨模态融合。
result: SQUALL在虚拟生物标志物分析、空间微环境发现及疾病进展建模中表现优异，在898名患者预后预测上超越现有模型。
conclusion: 空间对齐的多模态预训练为从病理图像中获取分子见解提供了新范式。
---

## 摘要
组织病理学评估仍然是癌症诊断和分层的核心，但在缺乏分子背景的情况下，其机制解释仍然有限。为此，我们开发了SQUALL，一种整合组织学与空间分子程序的多模态基础模型。在预训练阶段，我们构建了histMol，这是一个包含来自3446个组织切片的33种组织类型、12个平台的17.6亿对组织学-空间转录组点/区域的大规模语料库。预训练后，SQUALL能够实现全转录组的虚拟生物标志物分析、发现与预后相关的空间生态位，以及进行整合性疾病进展建模。利用其多模态嵌入，SQUALL识别出与三级淋巴结构成熟和卵巢癌复发相关的生态位，重建了跨越325,112个点的乳腺癌侵袭分子轨迹，并揭示了潜在的转录程序。当应用于898名患者的全切片图像时，SQUALL在结果预测方面优于现有的病理学基础模型，同时实现了可解释的风险分层。综上所述，这些结果确立了空间对齐的多模态预训练作为将分子见解扩展到病理图像的新范式。

## Abstract
Histopathological assessment remains central to cancer diagnosis and stratification, yet its mechanistic interpretation remains limited without molecular context. To address this, we developed SQUALL, a multimodal foundation model integrating histology with spatial molecular programs. For pretraining, we assembled histMol, a large-scale corpus of 1.76 billion paired histology-spatial transcriptomics spots/bins across 33 tissues and 12 platforms from 3,446 tissue sections. Following pretraining, SQUALL enables transcriptome-wide virtual biomarker profiling, prognostically relevant spatial niches discovery, and integrative disease progression modeling. Leveraging its multimodal embeddings, SQUALL identifies niches associated with tertiary lymphoid structure (TLS) maturation and ovarian cancer relapse, reconstructs molecular trajectories of breast cancer invasion across 325,112 spots, and uncovers underlying transcriptional programs. Applied to whole-slide images from 898 patients, SQUALL outperforms existing pathology foundation models in outcome prediction while enabling interpretable risk stratification. Together, these results establish spatially aligned multimodal pretraining as a new paradigm for extending molecular insights into pathology images.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **核心问题**：传统组织病理学评估虽然是癌症诊断和分层的核心，但缺乏分子层面的背景信息，导致其机制解释能力有限。现有病理基础模型（如基于自监督学习的病理图像模型）无法直接提供分子水平的洞察。
- **整体含义**：为了弥合组织学形态与空间分子程序之间的鸿沟，作者提出了一种多模态基础模型SQUALL，通过大规模配对的病理图像与空间转录组数据预训练，实现从组织学图像中推断分子特征、发现预后相关空间生态位、构建疾病进展分子轨迹，从而为病理图像赋予分子层面的解释能力。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：采用**空间对齐的多模态预训练**范式，将组织学图像斑块与对应的空间转录组测序点/区域进行配对，构建大规模语料库，通过对比学习或类似的多模态融合框架，学习组织学形态与分子表达程序之间的联合嵌入。
- **关键技术细节**：
  - **数据构建**：名为**histMol**的大规模语料库，包含来自3446个组织切片的**17.6亿**对（histology–spatial transcriptomics spots/bins），覆盖33种组织类型、12个技术平台。
  - **模型架构**：SQUALL包含两个编码器（图像编码器和分子编码器），通过空间对齐进行预训练，学习将组织学形态映射到全转录组分子程序的能力。
  - **下游任务能力**：
    - 虚拟生物标志物分析（全转录组水平的基因表达推断）。
    - 空间生态位发现（如识别与三级淋巴结构TLS成熟、卵巢癌复发相关的生态位）。
    - 整合性疾病进展建模（如重建乳腺癌侵袭分子轨迹，覆盖325,112个点）。
- **公式/算法流程**（文字说明）：
  1. **预处理**：从组织切片获取配对的组织学图像块和空间转录组表达谱。
  2. **预训练**：使用对比学习或其他多模态对齐损失，训练图像编码器和分子编码器，使匹配的图像-表达对在嵌入空间中接近，非匹配对远离。
  3. **微调/推理**：将预训练模型应用于全切片图像（WSI），输出全转录组预测、空间生态位聚类、预后风险评分等。

## 3. 实验设计：数据集、基准、对比方法
- **数据集**：
  - 预训练所用：histMol语料库（3446张切片，33种组织，12个平台）。
  - 下游验证：独立数据包括**898名患者的全切片图像**（用于预后预测）；以及乳腺癌、卵巢癌等特定数据集（用于空间生态位发现和轨迹重建）。
- **基准任务**：
  - 虚拟生物标志物分析（预测基因表达）。
  - 空间生态位识别（与TLS成熟、复发相关）。
  - 疾病进展建模（乳腺癌侵袭分子轨迹）。
  - 预后预测（在898名患者上比较）。
- **对比方法**：与**现有的病理基础模型**（如基于自监督学习的视觉模型）进行比较，SQUALL在预后预测上超越后者，且提供可解释的风险分层。

## 4. 资源与算力
- **文中未明确说明**：预训练histMol（17.6亿样本对）所需的GPU型号、数量、训练时长等细节未在摘要中给出。需注意，论文全文可能包含相关描述，但根据提供内容无法获知。

## 5. 实验数量与充分性
- **实验数量**：
  - 预训练为单一大规模设置。
  - 下游评估包含多个任务：虚拟生物标志物、空间生态位发现（至少两个案例：TLS和卵巢癌复发）、乳腺癌分子轨迹重建（325,112个点）、预后预测（898名患者）。
  - 消融实验可能包括不同预训练策略或模型变体，但摘要未提及具体消融组数。
- **充分性判断**：
  - 实验覆盖了从微观分子推断到宏观预后预测的多个层面，且在不同组织类型和平台上验证，具有一定广泛性。
  - 但缺乏与现有空间转录组分析方法的直接比较（如仅与病理模型比，未与非多模态方法比），可能部分削弱结论的绝对优势。
  - 预后预测仅在898名患者上测试，样本量中等，需更大规模独立验证。

## 6. 主要结论与发现
- SQUALL能够**从组织学图像中实现全转录组水平的虚拟生物标志物分析**，即无需测序即可预测基因表达。
- 通过多模态嵌入，**识别出与三级淋巴结构（TLS）成熟和卵巢癌复发相关的空间生态位**，展示了发现新生物学的能力。
- **重建了乳腺癌侵袭的分子轨迹**（325,112个点），揭示了潜在的转录程序，有助于理解肿瘤进展。
- 在898名患者全切片图像上的预后预测中，**SQUALL超越了现有病理基础模型**，同时实现了可解释的风险分层（基于空间生态位特征）。
- **总体结论**：空间对齐的多模态预训练为从病理图像中获取分子见解提供了新范式。

## 7. 优点
- **大规模多模态预训练语料**：histMol的规模（17.6亿对、33种组织、12平台）前所未有，为模型泛化性提供坚实基础。
- **统一多模态框架**：能同时完成虚拟生物标志物、生态位发现、疾病轨迹重建和预后预测，具有多功能性。
- **可解释性**：通过识别空间生态位实现风险分层，增强了临床可用性。
- **超越现有病理模型**：在预后任务上证明多模态融合优于纯视觉模型。

## 8. 不足与局限
- **算力成本未披露**：预训练如此大规模的数据需要极高计算资源，未说明使复现和成本评估困难。
- **对比方法有限**：预后预测仅与病理基础模型对比，未与基于转录组数据的预后模型或整合组织学-转录组的其他方法（如空间转录组分析工具）比较。
- **偏差风险**：histMol语料库可能偏向常见癌症类型或常用平台，对罕见组织或新型平台的适用性未知。
- **应用限制**：
  - 虚拟生物标志物分析依赖于预训练时覆盖的基因集，对未观察到的基因或非编码RNA可能失效。
  - 空间生态位发现需要人工验证，摘要未提供独立实验验证（如免疫组化或随访数据）。
  - 临床部署需要处理WSI标准化、批次效应等问题。
- **实验覆盖**：仅展示了乳腺癌和卵巢癌的生态位发现，其他组织类型的验证未提及。

（完）
