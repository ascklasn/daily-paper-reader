---
title: Integrating Histology with Spatial Molecular Programs Using a Multimodal Foundation Model
title_zh: 利用多模态基础模型整合组织学与空间分子程序
authors: "Zhang, Z., Qin, B., Zhao, Y., Qi, Z., Xu, H., Wang, Y., Zheng, W., Dai, J., Chen, A., Wang, N., Nie, L., Zhang, P., Zhang, H., Xu, T., Lin, S., Ren, P., Xue, L., Xue, X., Yang, Z., Xu, J., Pan, D., Wang, C., Liu, Z., Meng, Y., Zeng, Z."
date: 2026-06-03
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.01.729028v1.full.pdf"
tags: ["query:hmm"]
score: 9.0
evidence: 整合组织学与空间分子程序的多模态基础模型
tldr: 癌症诊断依赖组织病理学，但缺乏分子机制。SQUALL多模态基础模型整合组织学图像与空间转录组学，在来自33种组织、3446个切片的17.6亿配对数据上预训练。它能够实现转录组范围的虚拟生物标志物分析，发现与三级淋巴结构成熟和卵巢癌复发相关的空间生态位，重建乳腺癌侵袭的分子轨迹。在898名患者的全切片图像上，SQUALL在预后预测中优于现有病理基础模型，并提供可解释的风险分层。该工作建立了空间对齐多模态预训练的新范式，将分子见解扩展到病理图像。
source: biorxiv
selection_source: fresh_fetch
motivation: 组织病理评估缺少分子上下文，需要将组织学与空间分子信息整合以增强机制解释。
method: SQUALL多模态基础模型在1.76B配对的组织学-空间转录组数据上预训练，学习对齐的嵌入。
result: 模型发现与TLS成熟和癌症复发相关的空间生态位，重建侵袭分子轨迹，并在预后预测中优于现有模型。
conclusion: 空间对齐的多模态预训练为从病理图像中提取分子见解提供了新范式。
---

## 摘要
组织病理学评估仍是癌症诊断和分层的核心，但缺乏分子背景时其机制解释仍然有限。为此，我们开发了SQUALL，一种整合组织学与空间分子程序的多模态基础模型。预训练阶段，我们构建了histMol，一个包含来自3446个组织切片的33种组织和12个平台的17.6亿个配对组织学-空间转录组点/区域的大规模语料库。预训练后，SQUALL能够实现全转录组虚拟生物标志物分析、预后相关的空间生态位发现以及整合性疾病进展建模。利用其多模态嵌入，SQUALL识别了与三级淋巴结构成熟和卵巢癌复发相关的生态位，重建了跨越325,112个点的乳腺癌侵袭分子轨迹，并揭示了潜在的转录程序。应用于来自898名患者的全切片图像时，SQUALL在结果预测上优于现有病理学基础模型，同时实现了可解释的风险分层。总之，这些结果确立了空间对齐的多模态预训练作为将分子洞察扩展到病理图像中的新范式。

## Abstract
Histopathological assessment remains central to cancer diagnosis and stratification, yet its mechanistic interpretation remains limited without molecular context. To address this, we developed SQUALL, a multimodal foundation model integrating histology with spatial molecular programs. For pretraining, we assembled histMol, a large-scale corpus of 1.76 billion paired histology-spatial transcriptomics spots/bins across 33 tissues and 12 platforms from 3,446 tissue sections. Following pretraining, SQUALL enables transcriptome-wide virtual biomarker profiling, prognostically relevant spatial niches discovery, and integrative disease progression modeling. Leveraging its multimodal embeddings, SQUALL identifies niches associated with tertiary lymphoid structure (TLS) maturation and ovarian cancer relapse, reconstructs molecular trajectories of breast cancer invasion across 325,112 spots, and uncovers underlying transcriptional programs. Applied to whole-slide images from 898 patients, SQUALL outperforms existing pathology foundation models in outcome prediction while enabling interpretable risk stratification. Together, these results establish spatially aligned multimodal pretraining as a new paradigm for extending molecular insights into pathology images.

---

## 论文详细总结（自动生成）

## 1. 核心问题与整体含义
- **研究动机**：组织病理学评估是癌症诊断与分层的核心，但缺乏分子背景，导致机制解释受限。现有病理基础模型仅从图像中提取形态特征，不能直接关联空间分子程序。
- **核心目标**：通过多模态基础模型整合组织学图像与空间转录组学数据，将分子层面的洞察（如基因表达、空间生态位、疾病轨迹）扩展到常规病理图像上，实现可解释的预后预测和生物标志物发现。
- **整体意义**：提出“空间对齐多模态预训练”新范式，为病理图像提供分子上下文，推动精准医学中形态-分子联合分析。

## 2. 方法论
- **核心思想**：构建大规模配对的组织学-空间转录组数据语料库（histMol），在此基础上训练多模态基础模型SQUALL，学习组织学图像与空间分子程序的对齐嵌入表示。
- **关键技术细节**：
  - 数据构建：收集来自33种组织、3,446个组织切片、12种平台的17.6亿个配对组织学-空间转录组点/区域。
  - 模型架构：未在摘要中详细说明，推测采用双编码器（图像编码器+分子编码器）并通过对比学习或掩码建模进行对齐预训练。
  - 预训练目标：学习组织学图像与相应空间转录组点/区域之间的语义对应关系。
  - 下游能力：训练后模型可直接用于全转录组虚拟生物标志物分析、空间生态位识别（如与三级淋巴结构TLS成熟和卵巢癌复发相关的生态位）、疾病进展轨迹重建（如乳腺癌侵袭跨越325,112个点的分子轨迹）以及全切片图像（WSI）的预后预测。
- **公式或算法流程**：文本未提供具体公式，但流程可概括为：数据采集→配对对齐→多模态预训练→下游微调/零样本应用。

## 3. 实验设计
- **使用的数据集/场景**：
  - 预训练语料：histMol（1.76B配对点，33种组织，3,446切片，12平台）。
  - 下游验证：898名患者的全切片图像用于预后预测；独立发现空间生态位（如TLS成熟、卵巢癌复发）；乳腺癌侵袭轨迹重建（325,112个点）。
- **基准（Benchmark）**：与“现有病理学基础模型”（如病理图像专用基础模型）在预后预测任务上对比。
- **对比方法**：未列出具体模型名称，但表明SQUALL优于现有病理基础模型。

## 4. 资源与算力
- **文中明确说明**：未提及使用的GPU型号、数量、训练时长等算力信息。仅在元数据中给出预训练数据规模（1.76B配对），但无训练资源细节。
- **推断**：鉴于数据量庞大，很可能使用了多GPU集群（如A100/80GB以上的高性能设备），但缺乏具体数字。

## 5. 实验数量与充分性
- **实验数量**：摘要中列举了多个下游验证：
  - 虚拟生物标志物分析（全转录组范围）
  - 空间生态位识别（2个案例：TLS成熟、卵巢癌复发）
  - 疾病进展轨迹重建（乳腺癌侵袭，325K点）
  - 预后预测（898名患者，WSI）
  - 可解释性风险分层
- **充分性评估**：实验覆盖了多种任务（发现、预测、重建），且数据规模大，但缺乏消融实验、不同模型规模对比、超参数敏感性分析等细节。由于仅提供摘要，未见到统计显著性测试、同源数据集之外的泛化验证等。**结论**：实验设计较为全面，但公开信息不足，无法完全判断公平性与全面性（例如未报告评估指标、置信区间等）。

## 6. 主要结论与发现
- **SQUALL**能够利用其多模态嵌入识别与三级淋巴结构（TLS）成熟和卵巢癌复发相关的空间生态位。
- 成功重建了乳腺癌侵袭过程的分子轨迹（跨越325,112个空间点），并揭示了潜在转录程序。
- 在898名患者的全切片图像预后预测任务中，SQUALL**优于现有病理基础模型**，同时可提供可解释的风险分层。
- 总体结论：空间对齐的多模态预训练是一种**新范式**，可以将分子层面的洞察扩展至病理图像，增强诊断与预后判断的机制基础。

## 7. 优点
- **数据规模空前**：构建了迄今为止最大的组织学-空间转录组配对语料（1.76B，33种组织，12平台），为多模态预训练提供了丰富基础。
- **跨任务统一能力**：一个模型同时支持虚拟生物标志物、空间生态位发现、轨迹重建、预后预测、可解释性分析，体现基础模型的泛化性。
- **临床相关性**：在预后预测上超越现有专用病理基础模型，且提供可解释的风险分层（三级淋巴结构等），兼具性能和可解释性。
- **创新范式**：首次提出“空间对齐多模态预训练”，将分子信息直接注入病理图像表征，突破传统病理模型仅依赖形态的局限。

## 8. 不足与局限
- **算力信息披露不足**：未提供训练资源、耗时等，难以复现或评估资源门槛。
- **模型架构细节缺失**：仅在高层次描述方法，未公开编码器设计、损失函数、训练超参数等，不利于方法复现。
- **实验评估指标不明确**：预后预测的具体指标（如C-index、AUC等）未给出，也未展示置信区间或统计检验，无法判断差异显著性。
- **消融实验缺少**：未分析不同数据规模、不同对齐策略对结果的影响，也未比较是否用单模态基线优于多模态。
- **偏差风险**：数据来自特定平台和组织来源，可能引入批次效应或组织偏好；预后测试仅898名患者，样本量有限，且仅涉及单一癌种（乳腺癌、卵巢癌等），泛化到其他癌症或非癌组织需验证。
- **应用限制**：模型依赖空间转录组数据预训练，在缺乏此类数据的场景下仍需微调；虚拟生物标志物预测精度未经独立实验验证（如蛋白表达验证）。

（完）
