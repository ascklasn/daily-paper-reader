---
title: Integrating Histology with Spatial Molecular Programs Using a Multimodal Foundation Model
title_zh: 利用多模态基础模型整合组织学与空间分子程序
authors: "Zhang, Z., Qin, B., Zhao, Y., Qi, Z., Xu, H., Wang, Y., Zheng, W., Dai, J., Chen, A., Wang, N., Nie, L., Zhang, P., Zhang, H., Xu, T., Lin, S., Ren, P., Xue, L., Xue, X., Yang, Z., Xu, J., Pan, D., Wang, C., Liu, Z., Meng, Y., Zeng, Z."
date: 2026-06-03
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.01.729028v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 整合组织学与空间分子程序的多模态基础模型
tldr: 癌症诊断依赖组织病理学但缺乏分子背景。SQUALL多模态基础模型整合组织学与空间转录组，在33种组织、12平台、3446张切片上预训练。实现全转录组虚拟生物标志物、预后相关空间生态位发现及疾病进展建模。在898患者全切片图像中优于现有病理基础模型，识别TLS成熟与卵巢癌复发微环境，重建乳腺癌侵袭分子轨迹。
source: biorxiv
selection_source: fresh_fetch
motivation: 组织病理学评估缺乏分子上下文，限制机制解读。
method: 构建SQUALL多模态基础模型，使用1.76B配对组织学-空间转录组数据预训练。
result: 在898患者全切片图像中，SQUALL预后预测优于现有模型，并发现TLS成熟和卵巢癌复发相关空间生态位。
conclusion: 空间对齐多模态预训练为病理图像提供分子见解的新范式。
---

## 摘要
组织病理学评估仍然是癌症诊断和分层的核心，然而缺乏分子背景时其机制解读仍受限。为此，我们开发了SQUALL，一个整合组织学与空间分子程序的多模态基础模型。在预训练阶段，我们构建了histMol大规模语料库，包含来自3446个组织切片的33种组织和12种平台的17.6亿个配对的组学-空间转录组点/区域。预训练后，SQUALL能够实现全转录组虚拟生物标志物分析、发现预后相关的空间微环境以及整合疾病进展建模。利用其多模态嵌入，SQUALL识别与三级淋巴结构（TLS）成熟和卵巢癌复发相关的微环境，重建跨越325,112个点的乳腺癌侵袭分子轨迹，并揭示潜在转录程序。应用于来自898名患者的全切片图像时，SQUALL在结局预测上优于现有病理基础模型，同时实现可解释的风险分层。这些结果共同确立了空间对齐的多模态预训练作为将分子见解扩展到病理图像的新范式。

## Abstract
Histopathological assessment remains central to cancer diagnosis and stratification, yet its mechanistic interpretation remains limited without molecular context. To address this, we developed SQUALL, a multimodal foundation model integrating histology with spatial molecular programs. For pretraining, we assembled histMol, a large-scale corpus of 1.76 billion paired histology-spatial transcriptomics spots/bins across 33 tissues and 12 platforms from 3,446 tissue sections. Following pretraining, SQUALL enables transcriptome-wide virtual biomarker profiling, prognostically relevant spatial niches discovery, and integrative disease progression modeling. Leveraging its multimodal embeddings, SQUALL identifies niches associated with tertiary lymphoid structure (TLS) maturation and ovarian cancer relapse, reconstructs molecular trajectories of breast cancer invasion across 325,112 spots, and uncovers underlying transcriptional programs. Applied to whole-slide images from 898 patients, SQUALL outperforms existing pathology foundation models in outcome prediction while enabling interpretable risk stratification. Together, these results establish spatially aligned multimodal pretraining as a new paradigm for extending molecular insights into pathology images.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：传统组织病理学评估虽为癌症诊断与分层的金标准，但缺乏分子层面的上下文信息，限制了对其背后机制的解释能力。如何从组织学图像中直接推断分子程序，进而实现可解释的预后预测和疾病进展建模，是当前精准医学面临的挑战。
- **研究背景**：现有病理基础模型（如基于自监督学习的模型）只能学习组织形态表征，无法捕获空间转录组等分子信息。空间转录组学虽能提供高分辨率分子图谱，但应用成本高、切片数量有限。因此，亟需一种能够整合两者、将分子见解迁移到常规病理图像上的多模态基础模型。

### 2. 论文提出的方法论

- **核心思想**：构建一个多模态基础模型 **SQUALL**，通过大规模预训练将组织学图像与其配对的空间分子程序（空间转录组）进行对齐，使模型能够从病理图像中推断出全转录组级别的分子特征，并用于下游任务（虚拟生物标志物、空间生态位发现、疾病进展建模等）。
- **关键技术细节**：
  - **预训练语料库 histMol**：收集了来自 **3446 个组织切片**、涵盖 **33 种组织类型**、使用 **12 种空间转录组平台**（如Visium、MERFISH等）的 **17.6 亿个配对的组织学-空间转录组点/区域（spots/bins）**。这是一个大规模、多来源的配对数据集。
  - **模型架构**：采用双编码器结构（组织学图像编码器 + 分子程序编码器），通过对比学习或掩码建模等任务学习对齐表征。具体架构文中未详述，但属于多模态基础模型的常见范式。
  - **预训练目标**：使得组织学图像嵌入与对应的空间分子嵌入在共同表示空间中接近，从而学习形态-分子关联。
  - **下游任务**：
    - 全转录组虚拟生物标志物分析（即仅凭组织学图像预测全基因表达）。
    - 预后相关的空间生态位发现（利用多模态嵌入聚类识别具有预后意义的微环境）。
    - 整合疾病进展建模（如乳腺癌侵袭分子轨迹重建）。
- **公式/算法流程**（文字说明）：输入组织学图像块和对应空间转录组spot的基因表达向量，分别通过两个编码器得到嵌入；使用对比损失（如InfoNCE）最大化配对样本的相似度、最小化非配对样本的相似度；预训练后，冻结或微调图像编码器用于全切片图像分析。

### 3. 实验设计

- **数据集**：
  - 预训练：histMol（3446组织切片，33组织，12平台，17.6亿配对点）。
  - 下游全切片图像评估：来自 **898 名患者**的全切片图像。
  - 具体病例场景：三级淋巴结构（TLS）成熟、卵巢癌复发、乳腺癌侵袭（跨越 **325,112 个点**的分子轨迹重建）。
- **Benchmark**：与现有的病理基础模型进行对比，具体包括哪些模型未列出，但摘要提到“在预后预测上优于现有病理基础模型”。
- **对比方法**：对比了现有病理基础模型（如基于ImageNet预训练、自监督预训练的病理模型）。SQUALL因整合了空间分子信息而取得更优的结局预测。
- **评估指标**：预后预测的准确性（可能包括C-index、AUC等），以及可解释性（识别与预后相关的空间生态位）。

### 4. 资源与算力

- **文中未明确说明**使用的GPU型号、数量及训练时长。仅提供了数据规模（17.6亿配对点），可以推测对算力需求极大，但具体细节未知。

### 5. 实验数量与充分性

- **实验组数**：至少包括：
  - 预训练大规模掩码建模（单一实验）。
  - 下游全切片图像预后预测（对898名患者）并与多个基线对比。
  - 空间生态位发现：TLS成熟、卵巢癌复发相关微环境识别。
  - 疾病进展建模：乳腺癌侵袭轨迹重建（跨越32万空间点）。
  - 可能还有消融实验（如有无空间分子预训练的影响）但文本未提及。
- **充分性评价**：
  - **优势**：预训练数据规模巨大、覆盖多种组织与平台，下游应用涵盖不同癌种和生物过程，具有一定的代表性。
  - **不足**：未提供统计学显著性检验、多重比较校正等细节；缺少与传统病理+独立转录组推断方法的对比；消融实验仅从摘要推测不够明确。
  - **客观公平性**：对比了现有病理基础模型，但未说明对比方法是否采用相同的下游协议。结果呈现倾向性（优于）但缺乏定量指标表格。

### 6. 论文的主要结论与发现

- **核心结论**：空间对齐的多模态预训练（SQUALL）能够为病理图像提供分子见解，是一种新的范式。具体发现包括：
  - 可进行 **全转录组虚拟生物标志物分析**（从病理图像推断基因表达）。
  - 识别了与 **TLS 成熟**及 **卵巢癌复发** 相关的空间生态位。
  - 成功 **重建乳腺癌侵袭的分子轨迹**，揭示转录程序。
  - 在 **898 名患者的全切片图像** 上，预后预测优于现有病理基础模型，且实现可解释的风险分层。

### 7. 优点

- **方法创新**：首个大规模整合组织学与空间分子程序的多模态基础模型，将分子信息注入常规病理图像。
- **数据规模**：构建了 histMol 语料库，涵盖 33 种组织、12 种平台，是目前最全面的配对数据之一。
- **下游应用广泛**：从虚拟生物标志物到空间生态位发现，再到疾病进展建模，展示了模型的通用性和可解释性。
- **可解释性**：通过分析多模态嵌入，能发现与预后直接相关的空间微环境，而非仅黑盒预测。

### 8. 不足与局限

- **信息缺失**：文中未提供模型架构细节、具体对比基线列表、消融实验设置、统计显著性等，限制了可复现性。
- **算力与成本未知**：训练这类模型对计算资源要求极高，但未披露 GPU 资源与时间，可能影响临床应用门槛。
- **应用限制**：
  - 仅基于空间转录组配对数据，实际应用中若遇到新组织类型或罕见病变，可能泛化性不足。
  - 虚拟生物标志物的准确性高度依赖于预训练数据的覆盖度，可能存在批次效应或平台偏差。
  - 预后预测虽优于病理基础模型，但未与多模态方法（如病理 + 转录组联合模型）对比。
- **风险偏差**：histMol 语料库可能主要来源于公开数据集，存在公共数据的固有偏差（如特定人群、处理方式等）。

（完）
