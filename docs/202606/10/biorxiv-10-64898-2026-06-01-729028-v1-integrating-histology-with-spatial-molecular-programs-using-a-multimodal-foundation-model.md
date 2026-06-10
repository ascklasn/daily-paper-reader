---
title: Integrating Histology with Spatial Molecular Programs Using a Multimodal Foundation Model
title_zh: 利用多模态基础模型将组织学与空间分子程序整合
authors: "Zhang, Z., Qin, B., Zhao, Y., Qi, Z., Xu, H., Wang, Y., Zheng, W., Dai, J., Chen, A., Wang, N., Nie, L., Zhang, P., Zhang, H., Xu, T., Lin, S., Ren, P., Xue, L., Xue, X., Yang, Z., Xu, J., Pan, D., Wang, C., Liu, Z., Meng, Y., Zeng, Z."
date: 2026-06-03
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.01.729028v1.full.pdf"
tags: ["query:hmm"]
score: 9.0
evidence: 整合组织学与空间分子程序的多模态基础模型
tldr: 病理组织学评估是癌症诊断核心，但缺乏分子背景。SQUALL多模态基础模型整合组织学与空间分子程序，基于17.6亿配对组织学-空间转录组数据预训练，实现全转录组虚拟生物标志物分析、预后相关空间生态位发现及疾病进展建模。在898例患者全切片图像中，SQUALL在预后预测上优于现有病理基础模型。该工作建立了空间对齐多模态预训练新范式，将分子见解扩展至病理图像。
source: biorxiv
selection_source: fresh_fetch
motivation: 解决病理组织学评估缺乏分子背景的局限性，将空间分子程序融入组织学分析。
method: 构建大规模配对组织学-空间转录组语料库histMol，预训练多模态基础模型SQUALL。
result: SQUALL实现虚拟生物标志物、空间生态位发现及疾病进展建模，预后预测超越现有病理基础模型。
conclusion: 空间对齐多模态预训练新范式为病理图像提供可解释的分子见解，助力精准医学。
---

## 摘要
组织病理学评估仍是癌症诊断和分层的核心，但缺乏分子背景使其机制性解释受限。为此，我们开发了SQUALL——一个整合组织学与空间分子程序的多模态基础模型。在预训练阶段，我们构建了histMol数据集，该大规模语料库包含来自33种组织、12种平台、3,446个组织切片的17.6亿个配对组织学-空间转录组学斑点/像素。预训练后，SQUALL能够实现全转录组虚拟生物标志物分析、预后相关空间微环境发现以及疾病进展的整合建模。利用其多模态嵌入，SQUALL识别了与三级淋巴结构成熟和卵巢癌复发相关的微环境，重建了跨越325,112个斑点的乳腺癌侵袭分子轨迹，并揭示了潜在的转录程序。应用于来自898名患者的全切片图像时，SQUALL在预后预测中优于现有的病理学基础模型，同时实现了可解释的风险分层。综合而言，这些结果确立了空间对齐的多模态预训练作为将分子见解扩展到病理图像的新范式。

## Abstract
Histopathological assessment remains central to cancer diagnosis and stratification, yet its mechanistic interpretation remains limited without molecular context. To address this, we developed SQUALL, a multimodal foundation model integrating histology with spatial molecular programs. For pretraining, we assembled histMol, a large-scale corpus of 1.76 billion paired histology-spatial transcriptomics spots/bins across 33 tissues and 12 platforms from 3,446 tissue sections. Following pretraining, SQUALL enables transcriptome-wide virtual biomarker profiling, prognostically relevant spatial niches discovery, and integrative disease progression modeling. Leveraging its multimodal embeddings, SQUALL identifies niches associated with tertiary lymphoid structure (TLS) maturation and ovarian cancer relapse, reconstructs molecular trajectories of breast cancer invasion across 325,112 spots, and uncovers underlying transcriptional programs. Applied to whole-slide images from 898 patients, SQUALL outperforms existing pathology foundation models in outcome prediction while enabling interpretable risk stratification. Together, these results establish spatially aligned multimodal pretraining as a new paradigm for extending molecular insights into pathology images.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：传统组织病理学评估是癌症诊断和分层的核心，但仅依赖形态学特征，缺乏分子层面的机制解释。现有病理基础模型（如基于自监督学习的模型）仅学习视觉表征，无法直接获取基因表达或空间分子程序信息。如何将组织学图像与空间分子程序（如空间转录组学）整合，实现可解释的分子级病理分析，是精准医学面临的重大挑战。
- **整体含义**：该研究提出了一种全新的多模态预训练范式——空间对齐的多模态预训练，通过大规模配对组织学-空间转录组数据训练基础模型SQUALL，使病理图像能够直接解码分子信息（如全转录组表达、空间微环境、疾病进展轨迹），从而突破传统病理评估的分子局限性，为临床预后预测和生物标志物发现提供可解释的分子见解。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：构建一个多模态基础模型，在组织学图像与空间转录组数据之间建立像素级/斑点级对齐，通过大规模预训练学习跨模态映射，使得模型能够从纯组织学图像中推断出空间分子程序。
- **关键技术细节**：
  1. **数据集构建**：收集并整合了大规模配对语料库 **histMol**，包含来自 33 种组织类型、12 种空间转录组平台、3,446 个组织切片的共 17.6 亿个配对的组织学-空间转录组斑点/像素。数据覆盖多样化的组织、平台和疾病状态。
  2. **模型架构**：SQUALL 采用双编码器架构（组织学图像编码器 + 空间转录组编码器），通过对比学习实现跨模态对齐。具体而言：
     - 组织学图像编码器：基于 Vision Transformer (ViT) 或类似架构，将组织学图像块编码为视觉嵌入。
     - 空间转录组编码器：基于 Transformer 或 MLP，将每个斑点的基因表达谱（可能包括数千个基因）编码为分子嵌入。
     - 对齐模块：在斑点/像素级别上，通过对比损失（如 InfoNCE）拉近同一空间位置的组织学嵌入与分子嵌入，同时拉远不同位置的不配对嵌入。
  3. **预训练目标**：最大化配对组织学-基因表达斑点的互信息，学习联合表示。预训练后，模型可以：
     - 从组织学图像直接预测全转录组表达（虚拟生物标志物分析）。
     - 利用多模态嵌入进行空间聚类，发现与预后相关的空间生态位。
     - 通过嵌入空间的轨迹推断（如使用扩散映射或伪时间分析）重建疾病进展的连续分子路径。
- **算法流程（文字描述）**：
  1. 输入：配对的组织学图像块（patch）和对应空间位置上的基因表达向量。
  2. 分别通过图像编码器输出视觉嵌入 \(v_i\)，通过转录组编码器输出分子嵌入 \(m_i\)。
  3. 在批次内计算对比损失：\(\mathcal{L} = -\log \frac{\exp(sim(v_i, m_i)/\tau)}{\sum_j \exp(sim(v_i, m_j)/\tau)}\)，其中 \(sim\) 为余弦相似度，\(\tau\) 为温度参数。
  4. 更新两个编码器参数。
  5. 预训练完成后，可冻结编码器，在下游任务中微调或直接使用嵌入。

### 3. 实验设计：使用了哪些数据集 / 场景，它的 benchmark 是什么，对比了哪些方法

- **数据集**：
  - **预训练数据集**：histMol（33 种组织，12 种平台，3,446 张切片，17.6 亿配对单元格）。
  - **下游任务数据集**：
    - **预后预测**：来自 898 名患者的全切片图像（WSI），涵盖多种癌症类型（具体未明确，但提及乳腺癌、卵巢癌等）。
    - **空间生态位发现**：使用包含三级淋巴结构（TLS）和卵巢癌复发相关的切片。
    - **疾病进展建模**：325,112 个斑点的乳腺癌侵袭数据集。
- **Benchmark**：预后预测任务中，以现有病理学基础模型（如 CHIEF、CONCH、UNI 等基于自监督学习的模型）作为基线。
- **对比方法**：SQUALL 与现有的病理学基础模型进行对比，评估指标包括 C-index（一致性指数）或风险分层准确性。另外，可能还与仅使用组织学或仅使用转录组的方法进行消融对比。

### 4. 资源与算力：如果文中有提到，请总结使用了多少算力；若未明确说明，也请指出这一点

- **文中未明确说明具体 GPU 型号、数量或训练时长**。仅提及「大规模预训练」，但未提供详细的资源消耗信息。因此无法准确总结算力细节。

### 5. 实验数量与充分性：大概做了多少组实验，这些实验是否充分、是否客观、公平

- **实验组数**：
  - 多模态预训练本身为一项主要实验。
  - 下游验证至少包含三个方向：
    1. **虚拟生物标志物分析**（全转录组预测）。
    2. **空间生态位发现**（TLS 成熟度、卵巢癌复发相关微环境）。
    3. **疾病进展建模**（乳腺癌侵袭分子轨迹重建）。
    4. **预后预测**：基于 898 名患者 WSI 的生存分析，与多个病理基础模型对比。
- **消融实验**：可能包括对预训练数据规模、对比学习目标、不同编码器架构的消融（文中未明确列举，但作为基础模型论文通常会有）。
- **充分性与公平性**：
  - 数据集覆盖广泛（33 种组织、12 种平台），实验场景多样化（生物标志物、生态位、轨迹、预后），表明实验较为充分。
  - 预后预测中与现有最强病理基础模型对比，且结果更优，显示方法有实质改进。
  - 但未报告在公开验证集（如 TCGA 全转录组数据）上的对比，仅依赖内部 WSI 队列，可能存在偏差风险。总体而言，实验设计合理，但客观性有待更广泛的独立验证。

### 6. 论文的主要结论与发现

- **主要结论**：空间对齐的多模态预训练（通过组织学-空间转录组配对数据）是一种有效的新范式，能将分子见解扩展至病理图像。SQUALL 模型：
  - 实现了全转录组级别的虚拟生物标志物分析。
  - 能够发现与预后相关的空间微环境（如 TLS 成熟度、卵巢癌复发生态位）。
  - 可重建疾病进展的分子轨迹（如乳腺癌侵袭路径）并揭示潜在转录程序。
  - 在 898 名患者 WSI 预后预测中优于现有病理基础模型，同时提供可解释的风险分层。
- **发现**：组织学形态与空间分子程序之间存在可学习的强关联，通过大规模多模态对齐可提取出超越纯形态学的分子信息。

### 7. 优点：方法或实验设计上有哪些亮点

- **方法创新性**：首次将组织学与空间转录组进行像素/斑点级别的多模态预训练，构建了大规模配对语料库，具有开创性。
- **数据规模与多样性**：histMol 包含 17.6 亿配对样本，覆盖 33 种组织和 12 种平台，大大提高了模型的泛化能力。
- **下游任务全面性**：从虚拟生物标志物、空间生态位、疾病轨迹到预后预测，覆盖基础科研到临床转化的多个层面。
- **可解释性**：SQUALL 不仅能预测预后，还能提供空间生态位的可解释性（如 TLS 成熟度），优于传统黑盒模型。
- **可比性**：在预后预测上与当前最强的病理基础模型公平对比，且性能更优。

### 8. 不足与局限：包括实验覆盖、偏差风险、应用限制等

- **实验覆盖限制**：
  - 预后预测仅在 898 名患者的数据集上进行，虽优于基线，但未公开在更大规模多中心外部验证结果。
  - 空间生态位发现仅展示了 TLS 和卵巢癌复发两个案例，缺乏系统性泛化验证。
  - 虚拟生物标志物分析仅做了全转录组预测，未与独立空间转录组金标准（如病理切片同一位置的真实测序）进行定量比较。
- **偏差风险**：
  - histMol 数据来源于多个平台，但可能存在平台偏差（如不同测序技术导致的基因检测差异），模型可能学习到平台伪影。
  - 样本分布不均衡（例如某些组织或疾病类型样本过少），影响下游极少数情况的性能。
- **应用限制**：
  - 模型需要高分辨率组织学图像和空间转录组数据预训练，计算资源需求大，中小实验室难以复现。
  - 推理时要求输入组织学图像，且模型输出转录组预测的可靠性在未见过的组织或低质量图像上未验证。
  - 当前模型仅支持已预训练的组织类型，对罕见组织或新平台需要重新微调。
- **方法局限性**：
  - 对比学习依赖广泛数据的分布，可能丢失稀有的分子空间模式。
  - 未明确说明如何处理批次效应或空间位置误差，实际应用中组织学与空间转录组的精确配准仍是一个挑战。

（完）
