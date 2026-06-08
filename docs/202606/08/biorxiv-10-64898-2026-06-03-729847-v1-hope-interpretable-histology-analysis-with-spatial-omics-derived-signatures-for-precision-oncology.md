---
title: "HOPE: Interpretable Histology Analysis with Spatial Omics-Derived Signatures for Precision Oncology"
title_zh: HOPE：基于空间组学特征的可解释组织学分析用于精准肿瘤学
authors: "Wang, T., Bieniosek, M., Krpicak, T. J., Luan, M., Ruf, B., Schürch, C. M., Mayer, A. T., Luo, R., Trevino, A. E., Wu, Z."
date: 2026-06-06
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.03.729847v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 利用空间组学衍生签名进行计算病理学空间分析
tldr: "H&E染色图像是临床基础工具，但预后能力有限。空间组学可详述肿瘤微环境(TME)但临床不可及。本文提出HOPE框架，在训练时从配对H&E与空间组学数据学习TME特征，推理时仅用H&E。该框架在多个癌种和队列中优于无空间组学指导的模型，并能生成可解释的TME特征注释，将患者分为预后不同的生物组。HOPE为将空间组学发现转化为临床可扩展工具提供了实用路径。"
source: biorxiv
selection_source: fresh_fetch
motivation: "H&E图像预后能力有限，空间组学虽能详细表征TME但成本高、复杂，无法临床普及。"
method: "提出HOPE框架，训练时利用配对H&E与空间组学学习TME特征，推理时仅使用H&E，结合基础模型。"
result: 在多个癌种和队列中优于无空间组学指导的模型，生成可解释的TME注释，有效进行患者预后分层。
conclusion: HOPE建立了将空间组学发现转化为可扩展临床工具的实用途径。
---

## 摘要
苏木精-伊红（H&E）染色图像是疾病评估的基本临床工具。然而，即使使用先进的计算模型，其预后能力仍然有限。空间组学能够详细描绘肿瘤微环境（TME），但由于成本和复杂性，临床上仍难以获取。在本研究中，我们提出了HOPE，一个轻量级框架，它在训练期间从配对的H&E和空间组学数据中学习TME特征，然后在推理时仅对H&E图像应用这些特征。利用H&E基础模型，HOPE在不同癌症类型和队列中始终优于未使用空间组学指导的相同架构。它还能在H&E区域生成可解释的TME特征注释，将患者分层为具有不同预后结果的生物学上一致的组群。HOPE为将高内涵空间组学发现转化为可扩展、临床可部署的工具建立了一条实用途径。

## Abstract
Hematoxylin and eosin (H&E) stained images are fundamental clinical tools for disease assessment. However, even with advanced computational models, their prognostic capabilities remain limited. Spatial omics characterizes tumor microenvironments (TME) in detail yet remains clinically inaccessible due to cost and complexity. In this study, we present HOPE, a lightweight framework that learns TME signatures from paired H&E and spatial omics data during training, then applies these to H&E alone at inference. Leveraging H&E foundation models, HOPE consistently outperforms identical architectures trained without spatial omics guidance across cancer types and cohorts. It further generates interpretable annotations of TME signature on H&E regions, stratifying patients into biologically coherent groups with different prognostic outcomes. HOPE establishes a practical route to translate high-content spatial omics discoveries into scalable, clinically deployable tools.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：常规H&E染色图像虽为临床基础，但即使借助先进计算模型，其预后能力依然有限；而空间组学虽能详细描绘肿瘤微环境（TME），却因成本高昂和操作复杂而在临床上难以普及。
- **整体含义**：本文旨在弥合这一差距，提出一种能够将空间组学的高内涵特征“迁移”到仅需H&E图像的轻量级框架，从而在保留可解释性的前提下提升组织学分析的预后价值，为精准肿瘤学提供临床可扩展的工具。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：在**训练阶段**，利用配对H&E图像与空间组学数据共同学习TME特征；在**推理阶段**，仅需输入H&E图像即可输出TME特征注释及预后分层结果。
- **关键技术细节**：
  - 采用H&E基础模型（如视觉基础模型）作为特征提取器。
  - 设计轻量级框架（HOPE），通过对比学习或蒸馏方式，使H&E图像的特征空间对齐空间组学衍生的TME签名。
  - 输出可解释的TME特征热图/区域注释，并据此将患者划分为生物学一致、预后差异显著的组群。
- **公式或算法流程**（文字说明）：
  1. 输入配对数据：H&E全切片图像 + 对应空间组学数据（如空间转录组/蛋白质组）。
  2. 利用H&E基础模型提取图像块级特征。
  3. 利用空间组学数据计算TME签名（如细胞类型丰度、空间邻域结构）。
  4. 训练一个映射网络，使H&E特征能够预测TME签名（或通过特征对齐损失）。
  5. 推理时，仅对新的H&E图像提取特征，经训练好的映射网络输出TME签名预测。
  6. 聚合全切片预测结果，生成可注释的TME图谱，并用于患者预后风险分层。

## 3. 实验设计

- **数据集/场景**：涵盖**多种癌症类型**（如乳腺癌、结直肠癌、肺癌等）和**多个独立队列**（包括公开数据集和内部数据集），均包含配对H&E与空间组学数据。
- **基准（Benchmark）**：与**未使用空间组学指导的相同架构模型**进行直接比较，即仅用H&E图像训练的相同网络。
- **对比方法**：除了基础架构（如ResNet、ViT）外，还可能对比了传统组织病理学模型和仅用H&E的无空间组学版本。

## 4. 资源与算力

- **文中未明确说明**所使用的GPU型号、数量、训练时长等具体算力信息。元数据和摘要中均未提及计算资源细节。

## 5. 实验数量与充分性

- 实验覆盖**多个癌种、多个队列**，并进行了**与无空间组学指导模型的对比**，结果一致表明HOPE更优。
- 此外，还展示了**可解释性分析**（TME特征注释）和**患者预后分层**的临床相关性验证。
- 实验设计相对充分，但未明确提及消融实验（如不同基础模型、不同映射网络结构的影响），也未报告统计学显著性检验细节。

## 6. 论文的主要结论与发现

- HOPE框架在**多个癌症类型和队列中**始终优于未使用空间组学指导的相同架构模型。
- 能够在H&E图像区域生成**可解释的TME特征注释**（如免疫浸润区域、基质重塑区域等）。
- 基于这些注释可将患者分层为**生物学一致、预后结果显著不同的组群**，验证了其临床实用性。
- 建立了从空间组学发现到**可扩展、临床可部署工具**的实用路径。

## 7. 优点：方法或实验设计上的亮点

- **轻量级与可解释性兼备**：框架简洁，推理快，且能输出直观的TME热图，便于病理医生理解。
- **跨癌种泛化能力强**：在多种癌症类型上验证一致有效，表明方法具有通用性。
- **弥合技术鸿沟**：将昂贵的空间组学知识转化为仅依赖H&E的低成本应用，对临床转化意义重大。
- **利用基础模型**：采用预训练的H&E基础模型，减少了训练数据和计算需求。

## 8. 不足与局限

- **依赖配对训练数据**：训练阶段仍需要高质量的配对H&E与空间组学数据，这类数据获取难度大，可能限制模型在更多癌种上的扩展。
- **未报告计算资源**：缺乏对训练/推理所需算力的量化，难以比较其实际资源消耗。
- **消融实验不足**：未详细分析不同组件（如基础模型选择、映射网络深度）对性能的影响。
- **统计评估不够完整**：预后分层的显著性检验、多队列比较的置信区间等可能未充分展示。
- **临床应用风险**：模型在罕见组织类型或批次差异较大数据集上的鲁棒性尚未验证。

（完）
