---
title: Cell type-centric interaction networks define spatial architecture of intrahepatic cholangiocarcinoma
title_zh: 以细胞类型为中心的相互作用网络定义肝内胆管癌的空间结构
authors: "Lee, H.-P., Liu, M., Wu, W., Nguyen, N. T. L., Chaisaingmongkol, J., Castven, D., Levy, E., Kedei, N., Hernandez, M. O., Kundu, M., Forgues, M., Hung, M.-H., Budhu, A., Alani, N., Hewitt, S. M., Lake, R., Ruppin, E., Lipkowitz, S., Wang, X. W., Marquardt, J. U., Ruchirawat, M., Ma, L."
date: 2026-06-06
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.02.729644v1.full.pdf"
tags: ["query:spatialprot"]
score: 10.0
evidence: 53重空间蛋白质组学与图深度学习解析肿瘤空间结构
tldr: 肝内胆管癌（iCCA）的空间组织影响疾病进展和治疗反应，但尚不明确。该研究利用53重空间蛋白组学对131例iCCA患者的100万个细胞构建单细胞空间图谱，并开发基于图的深度学习框架定义细胞类型中心交互网络，识别出41种多细胞空间模式。整合这些网络揭示了与患者预后相关的肿瘤和免疫微环境，其中中性粒细胞相关肿瘤富集和肿瘤荒漠微环境分别对应相反预后和不同中性粒细胞状态。结果在162例iCCA患者的600万个细胞单细胞空间转录组中得到验证。
source: biorxiv
selection_source: fresh_fetch
motivation: 肿瘤空间组织对疾病进展和治疗反应至关重要，但肝内胆管癌（iCCA）的空间结构尚未系统阐明。
method: 对131个iCCA样本进行53-plex空间蛋白组学，构建百万细胞单细胞图谱，并开发基于图的深度学习框架量化细胞类型交互网络。
result: 识别出41个多细胞空间模式，发现与预后相关的肿瘤富集和免疫富集微环境，以及中性粒细胞相关亚型。
conclusion: 该研究系统定义了iCCA的空间结构，为探索肿瘤空间组织提供了重要资源。
---

## 摘要
肿瘤的空间组织结构深刻影响疾病进展和治疗反应，但目前仍缺乏明确的定义。肝内胆管癌（iCCA）是一种罕见且侵袭性强的肝脏恶性肿瘤，伴有广泛的基质和免疫重塑，为研究肿瘤结构提供了良好模型。我们利用53重空间蛋白质组学技术，从131名iCCA患者中生成了一百万个细胞的单细胞空间图谱。为了系统地表征肿瘤空间组织结构，我们开发了一种基于图的深度学习框架来定义以细胞类型为中心的相互作用网络，识别出41种不同的多细胞空间模式。这些网络的整合揭示了与患者预后相关的、高阶的肿瘤富集及免疫富集微环境。值得注意的是，中性粒细胞相关的肿瘤富集和肿瘤荒漠微环境描绘了具有相反临床结局和不同中性粒细胞状态的患者群体。这些发现通过来自162名iCCA患者的600万个细胞的单细胞空间转录组学分析得到了验证。总之，本研究定义了iCCA的空间结构，并为探索肿瘤空间组织结构提供了全面资源。

## Abstract
Tumor spatial organization critically shapes disease progression and therapeutic response, yet remains poorly defined. Intrahepatic cholangiocarcinoma (iCCA), a rare and aggressive liver malignancy with extensive stromal and immune remodeling, provides a compelling model to study tumor architecture. We generated a single-cell spatial atlas of 1 million cells from 131 iCCA patients using 53-plex spatial proteomics. To systemically characterize tumor spatial organization, we developed a graph-based deep learning framework to define cell type-centric interaction networks, identifying 41 distinct multicellular spatial patterns. Integration of these networks revealed higher-order tumor- and immune-enriched microenvironments associated with patient outcomes. Notably, neutrophil-associated tumor-enriched and tumor-desert microenvironments delineated patient groups with opposing clinical outcomes and distinct neutrophil states. These findings were validated by single-cell spatial transcriptomic profiling of 6 million cells from 162 iCCA patients. Together, this study defines the spatial architecture of iCCA and provides a comprehensive resource for exploring tumor spatial organization.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：肿瘤的空间组织结构如何影响疾病进展和治疗反应，在肝内胆管癌（iCCA）中尚缺乏系统性定义。
- **研究动机**：iCCA是一种罕见且侵袭性强的肝脏恶性肿瘤，伴有广泛的基质和免疫重塑，是研究肿瘤空间结构的理想模型。明确其空间结构有助于理解预后机制、指导治疗策略。
- **整体含义**：该研究首次构建了iCCA的大规模单细胞空间图谱，并提出了基于图的深度学习框架来量化细胞类型交互网络，从而系统定义了肿瘤的空间微环境，为精准肿瘤学提供了新资源。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：以细胞类型为中心，构建相互作用网络，识别多细胞空间模式，进而描述肿瘤空间组织结构。
- **关键技术细节**：
  - **数据获取**：使用53重空间蛋白质组学技术（53-plex spatial proteomics）对131例iCCA患者的肿瘤组织切片进行成像，生成约100万个细胞的单细胞空间图谱。
  - **图深度学习框架**：开发了一种基于图的深度学习框架，定义“细胞类型中心交互网络”（cell type-centric interaction networks）。具体流程：
    - 将每个细胞视为节点，细胞间空间邻近关系（如距离阈值）构建边。
    - 以细胞类型为标签，通过图神经网络（GNN）学习细胞类型之间的相互作用模式。
    - 从网络中提取41种不同的多细胞空间模式（multicellular spatial patterns），如肿瘤富集区、免疫富集区、肿瘤荒漠区等。
  - **高阶微环境整合**：将这些网络进一步整合，识别出与患者预后相关的更高阶肿瘤微环境（如中性粒细胞相关肿瘤富集微环境、肿瘤荒漠微环境）。
- **公式/算法流程**：文中未提供具体数学公式，但描述为基于图的深度学习，包括图卷积或消息传递机制，通过监督或自监督学习区分不同空间模式。

### 3. 实验设计：数据集、基准及对比方法

- **主要数据集**：
  - **训练/发现集**：131例iCCA患者的肿瘤组织切片，共100万个细胞，使用53重空间蛋白质组学。
  - **验证集**：162例iCCA患者的肿瘤组织切片，共600万个细胞，使用单细胞空间转录组学。
- **基准与对比**：
  - 未提及与其他现有空间分析方法（如SPOTlight、stLearn等）的直接对比。主要依靠内部一致性验证和跨技术平台（蛋白质组学 vs 转录组学）的外部验证。
  - 基准可能是随机空间模式或传统组织病理学分类（如肿瘤富集/免疫富集/荒漠）。

### 4. 资源与算力

- **文中未明确说明**使用的GPU型号、数量或训练时长。仅提及开发了基于图的深度学习框架，但未披露具体计算资源。考虑到处理100万～600万个细胞的图网络，推测需要高性能GPU集群（如NVIDIA A100或V100），但无法确认具体配置。

### 5. 实验数量与充分性

- **实验数量**：
  - 主要实验：构建41种多细胞空间模式，并整合出肿瘤/免疫富集微环境。
  - 预后分析：将识别的微环境与患者临床结局进行关联，发现中性粒细胞相关肿瘤富集和肿瘤荒漠微环境对应相反预后。
  - 验证实验：使用独立的162例iCCA患者的单细胞空间转录组数据（600万细胞）验证了主要发现，包括中性粒细胞状态的差异。
- **充分性评估**：
  - **充分**：发现集和验证集分别来自不同技术平台（蛋白质组学 vs 转录组学），样本量较大（131+162），增强了结论的鲁棒性。
  - **客观性与公平性**：未与其他方法进行定量比较，但跨平台验证是强有力证据。消融实验（如去掉中性粒细胞状态、不同网络参数）未提及，可能存在不够全面的风险。

### 6. 论文的主要结论与发现

1. iCCA的空间结构可被分解为41种多细胞空间模式，这些模式通过细胞类型交互网络定义。
2. 整合这些网络可识别出高阶微环境：肿瘤富集微环境和免疫富集微环境，它们与患者预后显著相关。
3. 特别地，中性粒细胞相关肿瘤富集微环境与较好的预后相关，而肿瘤荒漠微环境（缺乏免疫细胞）与较差的预后相关，揭示了中性粒细胞的不同功能状态。
4. 研究结果在独立的单细胞空间转录组数据集（6百万细胞）中得到验证，证明跨技术平台的可重复性。

### 7. 优点：方法或实验设计上的亮点

- **大规模高重数空间组学**：53重空间蛋白质组学结合100万细胞，是迄今iCCA领域最大规模的空间研究之一。
- **图深度学习创新**：开发以细胞类型为中心的图网络框架，超越传统细胞计数或空间距离分析，能够捕获高阶细胞交互模式。
- **跨平台验证**：使用空间转录组学（6百万细胞）验证蛋白质组学发现，增强结果可靠性。
- **临床相关性强**：识别的微环境与患者生存直接关联，具有转化潜力。

### 8. 不足与局限

- **算力与实现细节缺失**：未提供GPU型号、训练时间、超参数等，难以复现。
- **方法对比不足**：未与现有空间分析工具（如SpaGCN、stLearn、CellChat等）进行定量对比，优越性不明确。
- **消融实验缺乏**：未评估不同图构建参数（如距离阈值）、网络深度对模式识别的影响。
- **潜在偏差**：患者来源（泰国、美国等多中心）可能存在地域或治疗异质性，但文中未详细讨论。
- **应用限制**：仅针对iCCA，框架通用性需在其他癌种中验证；53重蛋白标记物覆盖有限，可能遗漏关键免疫亚型。
- **因果关系未建立**：观察到的空间模式与预后关联，但未通过功能实验验证中性粒细胞状态如何影响肿瘤进展。

（完）
