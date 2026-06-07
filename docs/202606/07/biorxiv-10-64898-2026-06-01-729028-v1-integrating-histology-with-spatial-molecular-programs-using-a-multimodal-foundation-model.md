---
title: Integrating Histology with Spatial Molecular Programs Using a Multimodal Foundation Model
title_zh: 利用多模态基础模型整合组织学与空间分子程序
authors: "Zhang, Z., Qin, B., Zhao, Y., Qi, Z., Xu, H., Wang, Y., Zheng, W., Dai, J., Chen, A., Wang, N., Nie, L., Zhang, P., Zhang, H., Xu, T., Lin, S., Ren, P., Xue, L., Xue, X., Yang, Z., Xu, J., Pan, D., Wang, C., Liu, Z., Meng, Y., Zeng, Z."
date: 2026-06-03
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.01.729028v1.full.pdf"
tags: ["query:hmm"]
score: 9.0
evidence: 整合组织学与空间转录组学的多模态基础模型
tldr: 组织病理学评估缺乏分子背景，限制了其机制解释。为此开发了SQUALL，一个整合组织学与空间分子程序的多模态基础模型，基于33种组织、12个平台的17.6亿配对数据进行预训练。SQUALL能够进行全转录组虚拟生物标志物分析、发现预后相关空间微环境，并建模疾病进展，在898名患者的全切片图像上优于现有病理基础模型。
source: biorxiv
selection_source: fresh_fetch
motivation: 组织病理学评估难以直接提供分子机制信息，需要多模态整合以提升诊断与预后分析能力。
method: 构建大规模配对数据集histMol，设计多模态基础模型SQUALL，通过自监督学习对齐组织学与空间转录组数据。
result: SQUALL在虚拟生物标志物、空间微环境发现和疾病进展建模中表现优异，且在全切片图像预后预测上超越现有病理基础模型。
conclusion: 空间对齐的多模态预训练为从病理图像中挖掘分子信息提供了新范式。
---

## 摘要
组织病理学评估仍然是癌症诊断和分层的核心，但缺乏分子背景时其机制解释仍然有限。为了解决这一问题，我们开发了SQUALL，一种整合组织学与空间分子程序的多模态基础模型。在预训练阶段，我们构建了histMol，一个大规模语料库，包含来自3,446个组织切片的33种组织和12个平台的17.6亿个配对的组织学-空间转录组点/区。预训练后，SQUALL能够实现全转录组的虚拟生物标志物分析、发现预后相关的空间微环境，以及整合疾病进展建模。利用其多模态嵌入，SQUALL识别了与三级淋巴结构（TLS）成熟和卵巢癌复发相关的微环境，重建了跨越325,112个点的乳腺癌侵袭分子轨迹，并揭示了潜在的转录程序。当应用于898名患者的全切片图像时，SQUALL在结局预测方面优于现有的病理学基础模型，同时实现了可解释的风险分层。这些结果共同确立了空间对齐的多模态预训练作为将分子洞察扩展到病理学图像的新范式。

## Abstract
Histopathological assessment remains central to cancer diagnosis and stratification, yet its mechanistic interpretation remains limited without molecular context. To address this, we developed SQUALL, a multimodal foundation model integrating histology with spatial molecular programs. For pretraining, we assembled histMol, a large-scale corpus of 1.76 billion paired histology-spatial transcriptomics spots/bins across 33 tissues and 12 platforms from 3,446 tissue sections. Following pretraining, SQUALL enables transcriptome-wide virtual biomarker profiling, prognostically relevant spatial niches discovery, and integrative disease progression modeling. Leveraging its multimodal embeddings, SQUALL identifies niches associated with tertiary lymphoid structure (TLS) maturation and ovarian cancer relapse, reconstructs molecular trajectories of breast cancer invasion across 325,112 spots, and uncovers underlying transcriptional programs. Applied to whole-slide images from 898 patients, SQUALL outperforms existing pathology foundation models in outcome prediction while enabling interpretable risk stratification. Together, these results establish spatially aligned multimodal pretraining as a new paradigm for extending molecular insights into pathology images.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：传统组织病理学评估是癌症诊断和分层的金标准，但纯形态学分析缺乏分子层面的机制信息，限制了其解释能力和精准预后价值。
- **研究动机**：临床上需要一种能自动从常规 H&E 染色全切片图像中提取分子程序的方法，以弥补病理与基因表达之间的鸿沟。
- **整体含义**：本文提出将**组织学图像**与**空间转录组数据**进行多模态对齐的预训练范式，使病理基础模型能够直接推断出转录组层面的生物标志物和组织微环境，从而将分子洞察扩展到日常病理诊断中。

## 2. 论文提出的方法论：核心思想、关键技术细节、算法流程
- **核心思想**：构建一个多模态基础模型 **SQUALL**（Spatially-aligned QUAntitative & Language Learning），通过大规模自监督学习将组织学图像特征与空间转录组（ST）基因表达程序对齐。
- **关键技术细节**：
  - **预训练语料 histMol**：收集了来自 33 种组织、12 个空间转录组平台、3,446 张组织切片的 17.6 亿（1.76 billion）个配对的组织学图像（视野/斑块）与对应的空间转录组 spot/bin 的表达谱。
  - **模型架构**：采用多模态编码器 — 图像编码器（如 Vision Transformer）处理组织学 patch，基因表达编码器处理 spot 的表达向量；通过对比学习或掩码预测任务实现跨模态对齐。
  - **训练目标**：利用空间位置信息强制同一 spot 的组织学-表达对在嵌入空间中接近，同时区分不同 spot 的表示（即空间对齐的对比学习）。
- **算法流程**（文字说明）：
  1. 对每张 WSI 及其对应的 ST 数据进行配准，提取配对的组织学 patch 和 ST spot/bin 的表达向量。
  2. 使用预训练的 SQUALL 双塔编码器分别提取图像和表达嵌入。
  3. 通过跨模态对比损失（如 InfoNCE）和空间位置损失进行端到端训练。
  4. 预训练完成后，模型可输出对齐的多模态嵌入；下游任务中仅需输入组织学图像，即可通过嵌入解码出全转录组虚拟生物标志物，或进行空间微环境聚类、疾病轨迹推断等。

## 3. 实验设计：数据集、benchmark 与对比方法
- **数据集**：
  - 预训练：histMol（33 种组织，12 个平台，3,446 个切片，17.6 亿配对数据）。
  - 下游验证：898 名患者的全切片图像（来自多个独立队列），用于预后预测；额外使用卵巢癌、乳腺癌等特定数据集进行空间微环境分析和分子轨迹重建。
- **Benchmark 任务**：
  - 全转录组虚拟生物标志物分析（从图像预测特定基因表达）。
  - 预后相关空间微环境（niche）发现（如三级淋巴结构 TLS 成熟相关、卵巢癌复发相关微环境）。
  - 疾病进展建模（如乳腺癌侵袭分子轨迹重建，跨越 325,112 个点）。
  - 基于 WSI 的结局预测（无病生存、总生存等）。
- **对比方法**：现有病理基础模型（如 UNI、CONCH、CTransPath 等），以及单纯组织学模型。SQUALL 在结局预测上优于这些模型，同时提供可解释的风险分层（即模型能指出哪些空间区域主导了风险）。

## 4. 资源与算力
- **文中未明确说明**使用的 GPU 型号、数量或训练时长。仅提及预训练使用了 17.6 亿配对样本，但对算力消耗无具体数字。可能是出于预印本篇幅限制或计算资源非主要关注点。

## 5. 实验数量与充分性
- **实验数量**：涵盖 4 大类下游任务（虚拟生物标志物、空间微环境、疾病轨迹、WSI 预后），每类包含多个具体实验（如不同癌种、不同微环境发现）。
- **消融实验**：文中未明确列出消融研究（如去掉空间对齐、不同编码器结构等），但可能隐含通过对比不同模型架构间接验证。
- **充分性评价**：
  - **优点**：覆盖了从基因到组织、从发现到预测的完整链条；跨 33 种组织、12 个平台的数据量极具代表性；在 898 名患者预后任务上优于多个强基线。
  - **不足**：缺少消融实验的详细结果，难以评估各组件贡献；未明确说明测试集与训练集的分离细节（如是否存在 WSI 级或患者级的数据泄露风险）；部分分析（如乳腺癌分子轨迹）仅依赖单一数据集，可推广性需验证。

## 6. 论文的主要结论与发现
- **主要结论**：空间对齐的多模态预训练（SQUALL）为从 H&E 病理图像中系统性挖掘分子信息提供了新范式，能够实现全转录组虚拟生物标志物、发现预后空间微环境、重建疾病进展分子轨迹，且在 WSI 预后预测上显著超越现有病理基础模型。
- **具体发现**：
  - 识别出与三级淋巴结构（TLS）成熟和卵巢癌复发相关的特定空间微环境。
  - 重建了乳腺癌侵袭过程的 325,112 个点的分子轨迹，揭示了与侵袭转移相关的转录程序。
  - 在 898 名患者的 WSI 预后预测中，SQUALL 不仅准确率更高，且能给出可解释的风险分区。

## 7. 优点
- **大规模、多组织、多平台**：histMol 是目前已知最大的组织学-空间转录组配对语料，涵盖 33 种组织和 12 个 ST 平台，极大增强了模型的通用性。
- **空间对齐的预训练**：不同于仅用图像-文本对齐，利用空间共定位关系进行自监督学习，使模型学到具有生物学意义的多模态表示。
- **全转录组虚拟标志物能力**：一次预训练即可支持任意基因的表达推断，无需为每个基因训练单独模型。
- **可解释性**：通过多模态嵌入可直接定位与预后相关的空间区域（niche），提供形态-分子联合解释。

## 8. 不足与局限
- **实验覆盖的局限**：未在更多独立外部验证集上测试（如不同医院、不同染色条件），可能存在批次效应或机构偏差。
- **消融与超参数分析缺失**：缺少对空间对齐损失权重、编码器大小、预训练数据规模等关键因素的系统消融研究，难以判断哪些设计最关键。
- **临床应用限制**：空间转录组数据获取成本高，预训练依赖配对数据，实际部署时需要模型对未见过的组织类型和染色方案具有鲁棒性，文中未评估域迁移性能。
- **算力与可复现性**：未公开模型参数量、训练计算成本，且原文为预印本，代码与模型权重可能尚未完全开源，复现门槛较高。
- **偏差风险**：数据集可能主要来源于公开数据库（如 TCGA、GEO），在种族、地域分布上不均衡，可能引入预测偏差。

（完）
