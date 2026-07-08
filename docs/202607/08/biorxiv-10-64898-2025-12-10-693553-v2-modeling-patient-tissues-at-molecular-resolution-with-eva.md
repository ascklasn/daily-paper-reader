---
title: Modeling patient tissues at molecular resolution with Eva
title_zh: 用Eva在分子分辨率下对患者组织进行建模
authors: "Liu, Y., Sharma, R., Bieniosek, M., Kang, A., Wu, E., Chou, P., Li, I., Rahim, M., Bauer, E., Ji, R., Duan, W., Qian, L., Luo, R., Sharma, P., Dhanasekaran, R., Schürch, C. M., Charville, G., Mayer, A., Zou, J., Trevino, A. E., Wu, Z."
date: 2026-07-08
pdf: "https://www.biorxiv.org/content/10.64898/2025.12.10.693553v2.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 空间蛋白质组学和组织病理学基础模型
tldr: 组织结构与功能密切相关，结构异常常预示疾病。现有空间蛋白质组学数据难以提取洞察。提出Eva基础模型，采用新型视觉Transformer架构，通过对齐的空间蛋白质组学和组织病理学图像进行掩码重建预训练，学习分子、细胞和样本级别的多尺度空间表征。Eva在跨模态推断、质量控制、数据标注、零样本检索、生存建模和患者分层等任务上表现优异，验证了其通用性和泛化能力。有望加速基础研究向临床实践的转化。
source: biorxiv
selection_source: fresh_fetch
motivation: 组织结构与分子、临床信息的关系难以从空间蛋白质组学数据中提取洞察，需新方法建模。
method: Eva采用新型视觉Transformer，在匹配的空间蛋白质组学和组织病理学图像上进行掩码重建预训练，学习多尺度空间表征。
result: Eva在跨模态推断、质量控制、数据标注、零样本检索、生存建模和患者分层等任务上表现优异，验证了通用性。
conclusion: Eva作为基础模型，有望通过桥接基础研究和临床实践，加速转化科学的发展。
---

## 摘要
组织结构对所有器官的功能和稳态至关重要，结构的破坏通常表明疾病。对组织的结构、分子和临床方面之间的关系进行建模，可以推动新的诊断和治疗策略。尽管空间蛋白质组学等分析技术能够捕捉这些关系，但从数据中提取见解仍然具有挑战性。在此，我们提出Eva，一种用于组织成像数据的基础模型，能够在分子、细胞和样本水平上学习组织的多尺度空间表示。Eva采用新颖的视觉变换器架构，并在匹配的空间蛋白质组学和组织病理学图像的掩码重构上进行预训练。我们展示了Eva在多种任务中的出色表现，包括跨模态推理、质量控制、数据注释、零样本检索、生存建模和患者分层。在保留验证数据上的广泛评估证明了所学嵌入的多样性和泛化能力。我们预计Eva将通过桥接基础研究和临床实践来加速转化科学。

## Abstract
Tissue structure is essential to function and homeostasis in all organs, and disruptions to structure usually indicate disease. Modeling relationships between structural, molecular, and clinical aspects of tissues could advance new diagnostics and treatment strategies. Although profiling techniques like spatial proteomics can capture these relationships, the data remain challenging to extract insight from. Here, we present Eva, a foundation model for tissue imaging data that learns multi-scale spatial representations of tissues at the molecular, cellular, and sample level. Eva uses a novel vision transformer architecture and is pre-trained on masked reconstruction of matched spatial proteomics and histopathology images. We show that Eva excels at a variety of tasks, including cross-modal inference, quality control, data annotation, zero-shot retrieval, survival modeling, and patient stratification. Extensive evaluations on held-out validation data demonstrate the versatility and generalizability of the learned embeddings. We anticipate that Eva will accelerate translational science by bridging basic research and clinical practice.

---

## 论文详细总结（自动生成）

# 论文总结：Modeling patient tissues at molecular resolution with Eva

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：组织结构是器官功能与稳态的基础，结构异常常预示疾病。现有的空间蛋白质组学数据虽然能捕获结构、分子和临床信息之间的关系，但从中提取有用洞察极其困难。需要一种能够统一表示组织形态和分子表型、并连接真实世界患者信息的基础模型。
- **整体含义**：Eva（Encoder of visual atlas）是一个针对多重组织成像数据的基础模型，通过自监督学习在大规模匹配的空间蛋白组学和组织病理学图像上预训练，学习分子、细胞和组织水平的多尺度空间表征。旨在桥接基础研究与临床实践，加速转化科学。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：采用两阶段分层Transformer架构（通道编码器 + 令牌级掩码自编码器），在掩码图像重建任务上预训练，灵活处理任意组合的输入通道，并整合生物标志物的先验知识。
- **关键技术细节**：
  - **通道级编码器**：对每个通道独立使用共享卷积核进行嵌入，支持任意输入通道组合；引入基于GenePT（大语言模型）的生物标志物语义嵌入，为非蛋白标志物（如DAPI、H&E通道）随机初始化学习嵌入；通过多头部注意力沿通道轴融合信息，输出聚合令牌。
  - **令牌级掩码自编码器**：将通道聚合令牌与可学习位置编码结合，使用ViT-base编码器捕捉空间关系；解码器重建图像，使用MSE损失仅在掩码位置计算。
  - **掩码策略**：训练采用随机掩码（mask ratio=0.75）；推理时支持令牌掩码、通道掩码、H&E掩码等，评估不同能力。
  - **跨模态微调**：使用MIF掩码目标微调Eva，实现H&E到MIF的预测（仅输入H&E和标志物名称，输出蛋白表达）。
  - **下游嵌入**：图像块级嵌入为所有令牌平均；区域级嵌入通过多头注意力MIL聚合。

## 3. 实验设计：数据集、基准与对比方法

- **训练数据集**：约4,000个人类组织区域（TMA和全切片），涵盖多种器官和约200种蛋白标志物，其中66%有配准H&E。主要来自CODEX/Phenocycler（24%）和PhenoCycler Fusion（64%），少量MIBI（1%）和IMC（11%）。总计约1.1M个224×224图像块（41.6M单通道块）。
- **验证数据集**：超过8,000个区域（71%在训练中完全未见），包括多个公共和私有数据集（如UPMC-HNC、Stanford-GC、MDACC-HCC、EM-PCA、UKT-GEJ等），涵盖多种癌症类型、成像平台和专家标注。
- **基准与对比方法**：
  - **多重成像基础模型**：VirTues（MAE，基于IMC训练）、KRONOS（DINOv2）
  - **H&E到MIF翻译模型**：ROSIE（ConvNext）、GigaTIME（UNet++）
  - **病理基础模型（PFMs）**：UNI、Prov-GigaPath（作为H&E嵌入参考）
- **下游任务**：图像重建（随机/令牌/通道掩码）、跨模态推断（H&E→MIF）、质量控制（NIQE、伪影、标志物质量）、细胞类型分类（12个数据集）、微环境分类、细胞组成预测、图像补丁零样本检索、肿瘤类型/亚型分类、生存分析、患者分层（HPV状态、炎症、预后、治疗反应）、案例级零样本检索、与PFM融合。

## 4. 资源与算力

- **预训练**：8×141 GB NVIDIA H200 GPU，训练20个epoch，batch size 16，使用PyTorch Lightning + Wandb。
- **下游实验**：单张24 GB NVIDIA RTX 4090 GPU。
- **代码与模型权重**：已开源（GitHub和Hugging Face）。

## 5. 实验数量与充分性

- **实验数量**：非常丰富，涵盖超过10个下游任务，涉及12个细胞分类数据集、多个生存/分层数据集、图像重建与跨模态翻译、质量控制（3个子任务）、微环境分类（2个数据集）、细胞组成预测等。包含零样本、少样本、消融实验（不同掩码策略、不同空间上下文等）。
- **充分性**：
  - 对比方法使用公开预训练权重，线性探针统一设置（固定骨干，单层线性分类器，AdamW优化器），保证了公平比较。
  - 训练/验证/测试划分、交叉验证（5折）等设计合理。
  - 但局限性：大多数验证数据来自CODEX/Phenocycler平台，对MIBI/IMC的验证有限；下游标签由专家标注，可能存在偏差。总体而言实验客观、全面。

## 6. 论文的主要结论与发现

- Eva在大多数任务上显著优于现有的多重成像基础模型（VirTues和KRONOS），平均提高11.2%（细胞分类AUC）。
- 在H&E→MIF跨模态预测中，Eva优于ROSIE和GigaTIME，且支持更多标志物。
- 质量控制任务：NIQE预测AUC≈0.999，伪影检测AUC=0.786，标志物质量AUC=0.825。
- 细胞类型分类：12个数据集多类AUC 0.743-0.867（最佳11/12），零样本和少样本标签转移也保持优势。
- 微环境分类：AUC 0.884-0.892；细胞组成预测：PCC提升10-36%，MSE降低39%。
- 图像检索：top-1准确性高，检索结果在生物和视觉上一致。
- 肿瘤类型/亚型分类：F1得分0.706-0.968，对肺癌亚型AUC 0.949。
- 生存分析：C-index最高（UPMC-HNC: 0.685, EM-PCA-CRC: 0.766），KM曲线分离显著。
- 患者分层/检索：多个二分类任务AUC最佳；与PFM（UNI, Prov-GigaPath）融合后性能进一步提升。

## 7. 优点

- **架构创新**：两阶段设计（通道+空间）灵活处理任意通道组合，结合生物标志物语义嵌入，具备可扩展性。
- **计算高效**：通道级编码器共享权重，支持高效编码数百至数千通道。
- **多尺度表征**：从单细胞到组织区域再到患者级别，统一嵌入空间。
- **任务覆盖广泛**：从基本的图像重建到临床级生存分析与患者分层，验证了通用性。
- **可解释性**：注意力图显示模型关注肿瘤、基质等生物学相关区域。
- **开源友好**：代码、模型权重、部分数据公开，利于复现和后续研究。

## 8. 不足与局限

- **数据偏差**：训练和验证主要依赖CODEX/Phenocycler平台（88%+），对MIBI/IMC验证不足，可能影响跨平台泛化。
- **标注偏差**：下游任务标签（细胞类型、微环境、质量等级）由专家人工标注，可能引入主观偏差。
- **机制解释不足**：尽管注意力图在视觉上与已知结构对齐，但如何系统提取驱动患者水平表型的分子/细胞机制仍是开放性挑战。
- **生成能力未内化**：H&E→MIF的跨模态预测是通过微调实现，未在预训练中原生包括生成目标，可能限制了潜力。
- **零样本能力有限**：虽然优于对比模型，但跨数据集零样本性能仍有提升空间。
- **临床验证范围**：生存分析和患者分层仅基于有限数据集（如UPMC-HNC、EM-PCA），缺乏大规模多中心验证。

（完）
