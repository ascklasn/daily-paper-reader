---
title: "An open multimodal spatial resource integrating same-tissue transcriptomics, proteomics, and histology"
title_zh: 整合同一组织转录组学、蛋白质组学和组织学的开放多模态空间资源
authors: "Duchini, E., Tsao, C., Madore, J., Ashhurst, T. M., De Almeida Silva, J., Shin, J.-S., Gupta, R., McCaughan, G., Palendira, U., Liu, K., Ferguson, A., Marsh-Wakefield, F."
date: 2026-08-21
pdf: "https://www.biorxiv.org/content/10.64898/2026.08.17.742355v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: "同一组织切片的空间转录组、蛋白质组与H&E组织学多模态资源"
tldr: "空间转录组与蛋白组在同一组织切片上的整合面临技术挑战，且公共多模态数据稀缺。本文提出一个顺序工作流，在同一FFPE组织切片上依次进行Xenium空间转录组、COMET循环免疫荧光和H&E染色，实现转录组、蛋白与组织形态的联合分析。该方法在扁桃体、肝细胞腺瘤及配对肝细胞癌组织中成功应用，并公开了四个对齐的组织核心数据，含转录坐标、蛋白图像、细胞分割及集成单细胞数据。此外还开发了UnumLocalia可视化工具，支持交互探索和数据导出，为多模态空间生物学研究提供了可复用资源。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有空间技术难以在同一切片上整合转录组和蛋白组，且缺乏适合计算方法开发的多模态公共数据集。
method: "开发了在同一FFPE切片上顺序进行Xenium、COMET和H&E染色的工作流，经图像配准后应用Xenium细胞分割生成集成单细胞数据。"
result: 在多种人类组织中成功应用，公开了四个对齐组织核心及集成数据，并发布UnumLocalia交互式可视化工具。
conclusion: 该工作流、软件与开放数据集为多模态空间生物学、计算方法验证及数据整合提供了可复用的基础资源。
---

## 摘要
空间转录组学和蛋白质组学技术为组织结构、细胞表型和功能提供了互补的见解，但将这些模态整合到同一组织切片上仍然具有技术挑战性。顺序工作流程必须在保持准确空间配准的同时，保留RNA完整性、抗原性和组织形态。目前，适合计算方法开发的公开多模态数据集仍然有限。在这里，我们提出了一种工作流程，用于在同一福尔马林固定石蜡包埋组织切片上进行顺序的10x Genomics Xenium空间转录组学、COMET循环免疫荧光以及苏木精和伊红（H&E）组织学染色。我们展示了该方法在多种生物学上不同的人体组织中的适用性，包括扁桃体、肝细胞腺瘤以及匹配的肿瘤和非肿瘤肝细胞癌，说明了该工作流程超越单一组织类型的广泛适用性。在图像配准之后，将Xenium衍生的细胞分割应用于蛋白质图像，以生成用于下游分析的整合单细胞转录组和蛋白质组测量数据。为了促进社区复用，我们公开发布了四个代表性的对齐组织核心，连同转录坐标、多重蛋白质图像、H&E图像、细胞分割和整合的单细胞数据集。我们还介绍了UnumLocalia，一个开源的可视化和数据提取工具，它能够交互式探索对齐的多模态图像，支持用户自定义的细胞分割，并允许导出整合的单细胞数据用于下游分析。总之，该技术方案、工作流程、软件和公开可用的数据集为多模态空间生物学提供了可复用的资源，支持生物发现、计算方法开发、多模态数据整合以及跨互补空间技术的新兴分析方法的验证方面的进展。

## Abstract
Spatial transcriptomic and proteomic technologies provide complementary insights into tissue organisation, cellular phenotype and function, yet integrating these modalities on the same tissue section remains technically challenging. Sequential workflows must preserve RNA integrity, antigenicity and tissue morphology while maintaining accurate spatial registration. At present, publicly available multimodal datasets suitable for computational method development remain limited. Here, we present a workflow for sequential 10x Genomics Xenium spatial transcriptomics, COMET cyclic immunofluorescence, and haematoxylin and eosin (H&E) histological staining on the same formalin-fixed paraffin-embedded tissue section. We demonstrate this approach across multiple biologically distinct human tissues, including tonsil, hepatocellular adenoma, and matched tumour and non-tumour hepatocellular carcinoma, illustrating the widespread applicability of the workflow beyond a single tissue type. Following image registration, Xenium-derived cell segmentations were applied to protein images to generate integrated single-cell transcriptomic and proteomic measurements for downstream analyses. To facilitate community reuse, we publicly release four representative aligned tissue cores together with transcript coordinates, multiplex protein images, H&E images, cell segmentations, and integrated single-cell datasets. We additionally introduce UnumLocalia, an open-source visualisation and data extraction tool that enables interactive exploration of aligned multimodal images, supports user-defined cell segmentation, and allows export of integrated single-cell data for downstream analyses. Together, this technical protocol, workflow, software, and openly available dataset provide a reusable resource for multimodal spatial biology, supporting advances in biological discovery, computational method development, multimodal data integration, and validation of emerging analytical approaches across complementary spatial technologies.

---

## 论文详细总结（自动生成）

## 论文详细中文总结

### 1. 核心问题与整体含义（研究动机与背景）

- **背景与动机**：空间转录组学（如 Xenium）和空间蛋白质组学（如 COMET 循环免疫荧光）分别提供了组织在转录层面和蛋白层面的互补信息。然而，将这两种模态整合到**同一组织切片**上仍面临重大技术挑战。
- **核心瓶颈**：顺序工作流必须同时满足三个要求——保持 RNA 完整性、保留抗原性、维持组织形态，并确保不同模态图像之间的**精确空间配准**。此外，目前适合计算方法开发与验证的**公开多模态空间数据集极为稀缺**。
- **研究意义**：这项工作的核心价值在于提供一个**可复用的技术协议**和**开放的公共数据资源**，使空间生物学领域能够跨越单一模态的限制，为多模态数据整合、计算方法开发和生物发现奠定基础。

### 2. 方法论：核心思想与关键技术细节

- **总体思路**：在同一张福尔马林固定石蜡包埋（FFPE）组织切片上，依次执行三种互补的空间检测技术，最后通过图像配准和细胞分割实现多模态数据的单细胞级整合。
- **顺序工作流（核心流程）**：
  1. **Xenium 空间转录组学**：首先在组织切片上运行 10x Genomics Xenium 平台，获取高多重空间转录本坐标。
  2. **COMET 循环免疫荧光**：随后在同一组织切片上进行 COMET 循环免疫荧光染色，获取多重蛋白图像。
  3. **H&E 组织学染色**：最后执行苏木精-伊红染色，保留传统组织形态学信息。
- **数据整合流程**：完成三种模态的图像采集后，首先进行**图像配准**，将不同模态的图像对齐到同一空间坐标系；然后将 Xenium 生成的**细胞分割结果**直接应用到蛋白图像上，从而生成集成的单细胞转录组-蛋白质组测量数据。
- **可视化工具**：开发了开源工具 **UnumLocalia**，支持交互式探索对齐后的多模态图像、用户自定义细胞分割，并可导出整合后的单细胞数据用于下游分析。

### 3. 实验设计：数据集、场景与基准

- **组织类型覆盖**：该工作流在多种生物学上不同的人类组织中进行了验证，包括：
  - 扁桃体（淋巴组织）
  - 肝细胞腺瘤（良性肿瘤）
  - 肝细胞癌（HCC）的配对肿瘤组织和非肿瘤组织
- **公开数据规模**：公开发布了**四个代表性的对齐组织核心（tissue cores）**，包含：
  - 转录本坐标
  - 多重蛋白图像
  - H&E 图像
  - 细胞分割结果
  - 整合后的单细胞数据集
- **Benchmark 与对比**：**论文没有进行与其他方法或工作流的定量对比**（如配准精度比较、数据质量对比等）。本文属于新型技术工作流验证，而非算法性能竞赛型研究。主要验证方式是展示工作流在多种组织中的实际可行性，而非与既有方法做性能基准测试。

### 4. 资源与算力

- **论文未明确说明**：原文中**没有提供**任何关于算力资源的信息，包括 GPU 型号、GPU 数量、训练时长、计算集群配置等。
- 这可能是因为该研究的核心在于湿实验流程（组织切片处理、染色和成像），计算部分主要涉及图像配准、细胞分割和可视化工具的实现，这些步骤通常不需要大规模训练算力。但若需复现全流程，用户需自行评估计算资源需求。

### 5. 实验数量与充分性

- **实验规模**：实验覆盖了**四类生物学上不同的组织场景**（扁桃体、腺瘤、配对 HCC 肿瘤/非肿瘤），并公开了四个代表性组织核心。这属于**多场景适用性验证**，而非大规模统计性实验。
- **实验充分性与客观性分析**：
  - **优点**：跨多种组织类型展示工作流的普适性，规避了单一组织可能带来的偶然性；四种组织在细胞组成、结构复杂性和抗原表达谱上差异显著，验证力度较好。
  - **不足**：
    - 公开的核心数量有限（仅 4 个），样本量较小；
    - **缺乏消融实验**（如单独评估各步骤对 RNA 完整性/抗原性的损伤程度）；
    - **没有定量评估**配准精度或蛋白-转录组模态间的一致性指标（如相关系数）；
    - 未与\"独立切片分别测各模态\"的标准流程做系统对比，无法定量评估同一组织切片顺序处理带来的数据质量折损。

### 6. 主要结论与发现

- **技术可行性得到验证**：在同一个 FFPE 组织切片上顺序执行 Xenium → COMET → H&E 的流程是**可行的**，且能在多种人类组织中稳定工作。
- **多模态整合路径成立**：通过将 Xenium 的细胞分割应用于配准后的蛋白图像，合理地生成了单细胞水平的整合转录组-蛋白组数据，为下游分析提供了基础。
- **公开资源贡献**：该论文提供了完整的技术协议、开放的多模态数据集和可视化工具 UnumLocalia，构成一套可复用的多模态空间生物学资源。
- **填补空白**：这项工作直接回应了当前多模态空间数据稀缺的现状，为计算方法开发、多模态数据整合研究和新兴分析方法的交叉验证提供了参考数据资源和实物基准。

### 7. 优点

- **技术路径新颖且具有可操作性**：将三模态（转录组-蛋白组-组织学）顺序整合到同一切片上的方案，并不依赖昂贵的定制设备，均使用商业化的成熟平台，具有较好的推广基础。
- **跨组织普适性验证**：选择扁桃体（免疫器官）、腺瘤（良性）和 HCC 配对肿瘤/非肿瘤（恶性）组织，展示了工作流对异质性组织的广泛兼容性，设计思路合理。
- **开放科学姿态**：不仅发布数据，还同步发布可视化工具和完整协议，符合可重复性和社区复用的需求。
- **单细胞级整合策略简单有效**：利用 Xenium 的高质量细胞分割直接映射到蛋白图像，避免了复杂的跨模态配准后重新分割的困难，降低了计算复杂度。
- **工具实用性强**：UnumLocalia 支持自定义分割和数据导出，增强了资源对下游用户的灵活适配性。

### 8. 不足与局限

- **样本量偏小**：公开数据集仅包含 4 个组织核心，对于建立大规模基准或深度学习训练集来说仍然不够充分。
- **缺少定量质量评估**：论文没有定量验证多轮顺序染色对 RNA 质量、抗原信号强度和形态结构完整性的累积损伤程度；也没有量化蛋白图像与转录组数据之间的空间一致性（如配准误差、模态相关性）。
- **未与传统方法系统性对比**：没有与\"同一组织相邻切片分别进行单模态染色\"的常规方案做比较，因此无法衡量顺序方案相对于平行方案的收益与代价。
- **缺乏跨平台泛化性论证**：工作流依赖于 Xenium 和 COMET 两个特定平台，结论能否泛化到其他空间转录组平台（如 Visium、Slide-seq）或其他蛋白检测平台尚不明确。
- **配准误差风险**：多轮成像之间的组织形变、荧光信号衰减和 H&E 染色的覆盖效应可能引入配准偏差，但文中未对此风险进行定量分析和误差传播讨论。
- **样本选择偏差**：全部组织均来自同一研究中心的临床标本，人口学背景和病理类型的代表性有限，可能存在选择偏倚。

---

（完）
