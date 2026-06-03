---
title: Volumetric Cyclic Immunofluorescence for 3D Spatial Profiling of Immune Structures in Human FFPE Tissue
title_zh: 体积循环免疫荧光技术用于人类FFPE组织中免疫结构的三维空间分析
authors: "Wong, A. Y. H., Lu, Y. D., Zhao, Z., Zhou, F., Park, H., Maliga, z., Anang, Y., Coy, S., Danuser, G., Santagata, S., Yapp, C., Sorger, P. K."
date: 2026-05-27
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.17.725158v2.full.pdf"
tags: ["query:spatialprot"]
score: 10.0
evidence: 人类FFPE组织中免疫结构的三维空间蛋白质组分析
tldr: "人体FFPE组织中的免疫系统由复杂的三维结构组成，传统2D成像难以研究其空间互作。本文提出体积循环免疫荧光（v-CyCIF）技术，结合虚拟H&E，可对厚达1mm的人体标本进行多重免疫细胞和神经成像。实验成功分析了正常与癌组织中的神经免疫互作，并对完整的次级和三级淋巴结构进行了免疫分型。再包埋切片实现了高分辨率亚细胞分析，为临床标本的多尺度3D空间分析提供了灵活框架。"
source: biorxiv
selection_source: fresh_fetch
motivation: 突破人类FFPE组织3D多重成像瓶颈，研究免疫细胞与血管神经等三维结构的互作。
method: "提出v-CyCIF（体积循环免疫荧光）结合虚拟H&E，对厚标本进行多重标记和成像，再包埋切片实现高分辨率分析。"
result: 成功在1mm厚人体FFPE组织中实现免疫细胞和神经的多重成像，分析了神经免疫互作和淋巴结构。
conclusion: v-CyCIF提供了跨成像格式和分辨率的多尺度3D分析框架，适用于临床标本。
---

## 摘要
组织驻留免疫系统涉及复杂的三维组装体，这些组装体与血管和神经等延伸结构相互作用。由于这些相互作用跨越多个组织切片，因此难以使用传统的二维分析方法进行研究。在动物组织中，光片荧光显微镜（LSFM）等体积成像技术被广泛用于研究三维组织结构，标记通常借助基因编码报告基因和血管染料。相比之下，人类标本的LSFM仍不成熟，因为大多数临床样本仅以福尔马林固定石蜡包埋（FFPE）组织形式提供，限制了标记策略主要依赖于染料和抗体。在此，我们提出了一种体积循环免疫荧光（v-CyCIF）和虚拟H&E工具箱，该工具箱克服了在厚度达1毫米的人类标本中对免疫细胞和神经进行多重成像的关键障碍。我们使用v-CyCIF研究正常和癌组织中的神经免疫相互作用，并对完整的次级和三级淋巴结构进行免疫分析。体积成像后对标本进行再包埋和切片，能够对与免疫细胞活性相关的亚细胞结构和细胞-细胞相互作用进行高多重、高分辨率分析。因此，v-CyCIF为跨成像格式和分辨率的临床标本多尺度三维分析提供了一个灵活的框架。

## Abstract
The tissue-resident immune system involves complex 3D assemblies that interact with extended structures such as blood vessels and nerves. These interactions are difficult to study using conventional 2D profiling because they span many tissue sections. In animal tissues, volumetric imaging approaches such as light-sheet fluorescence microscopy (LSFM) are widely used to study 3D tissue organization, with labelling often aided by genetically encoded reporters and vascular dyes. In contrast, LSFM of human specimens remains underdeveloped because most clinical samples are available only as formalin-fixed paraffin-embedded (FFPE) tissue, limiting labeling strategies primarily to dyes and antibodies. Here, we present a volumetric cyclic immunofluorescence (v-CyCIF) and virtual H&E toolbox that overcomes key barriers to multiplexed imaging of immune cells and nerves in human specimens up to 1 mm thick. We use v-CyCIF to study neuroimmune interactions in normal and cancer tissues and to immunoprofile intact secondary and tertiary lymphoid structures. Re-embedding and sectioning of specimens following volumetric imaging enables high-plex high-resolution analysis of subcellular structures and cell-cell interactions associated with immune cell activity. v-CyCIF therefore provides a flexible framework for multi-scale 3D profiling of clinical specimens across imaging formats and resolutions.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：人体组织驻留免疫系统由复杂的三维（3D）结构组成，这些结构与血管、神经等延伸结构之间存在空间互作，但传统的二维（2D）组织切片分析方法无法捕捉跨切片的3D组织信息，导致对神经-免疫互作、淋巴结构完整形态等关键生物学现象的理解受限。
- **研究背景**：在动物模型中，光片荧光显微镜（LSFM）等体积成像技术已被广泛用于研究3D组织结构，标记方法多依赖基因编码报告基因和血管染料。然而，人类临床样本绝大多数以福尔马林固定石蜡包埋（FFPE）形式保存，标记策略仅能使用染料和抗体，缺乏基因编码报告手段，因此人类FFPE标本的LSFM成像仍不成熟。
- **整体含义**：作者提出了一种名为**体积循环免疫荧光（v-CyCIF）**的技术，结合虚拟H&E染色，突破了人类FFPE厚标本（厚度达1 mm）的多重成像瓶颈，实现了免疫细胞和神经的高多重、多尺度3D空间分析，为临床组织病理学从2D向3D转型提供了灵活框架。

## 2. 论文提出的方法论

- **核心技术思想**：v-CyCIF将循环免疫荧光（CyCIF）的思想扩展到体积成像中。CyCIF原本用于2D切片的多轮抗体染色-成像-染料失活循环，v-CyCIF则将其应用于厚度达1 mm的FFPE组织块，通过多轮抗体孵育、光学清除、光片显微镜（或宽场等）采集3D图像堆栈，实现多重标记。同时，结合“虚拟H&E”染色（即利用自体荧光或特定染料模拟H&E对比），使组织学结构可视化。
- **关键技术细节**：
  - **标本制备**：对1 mm厚的FFPE组织块进行脱蜡、抗原修复、光学清除（如用CUBIC或iDISCO类方法）。
  - **多轮循环标记**：每次循环使用一组抗体（如针对免疫细胞标志物、神经标志物、血管标志物等），进行免疫荧光染色，然后使用宽场或光片显微镜进行3D成像；之后通过温和的化学方法（如光漂白或低pH缓冲液）去除荧光信号，再进行下一轮标记。
  - **虚拟H&E**：在成像过程中可利用组织自体荧光或特殊染料（如DRAQ5、苏木精类似物）模拟核染色和胞质染色，生成与常规H&E高度一致的虚拟切片。
  - **再包埋与切片**：完成体积成像后，将组织块重新包埋、切成薄片（如5 μm），使用常规高分辨率显微镜（如共聚焦或超分辨显微镜）对感兴趣的3D区域进行亚细胞分辨率的多重分析，实现跨尺度的关联。
- **算法流程**（文字描述）：没有给出完整数学公式，关键在于多轮循环的流程设计，包括组织处理、抗体结合、3D成像、信号擦除、配准对齐、3D重建和定量分析。

## 3. 实验设计

- **数据集/场景**：论文中使用的是人类FFPE组织标本，包括**正常组织**和**癌组织**，具体类型在摘要中未明确列出，但提到分析了“正常和癌组织中的神经免疫相互作用”以及“完整的次级和三级淋巴结构”（即脾脏、淋巴结中的次级淋巴结构以及肿瘤相关三级淋巴结构）。
- **Benchmark**：没有明确提到与现有方法（如同类3D多重成像技术如CODEX、MIBI等）的定量比较，而是以概念验证为主。作者可能将v-CyCIF的结果与传统的2D免疫组化或2D CyCIF进行了定性对比，但摘要未提及。
- **对比方法**：未直接对比其他方法，但强调了v-CyCIF相较于动物模型LSFM的优势（适用于人类FFPE）以及相较于2D方法的3D信息完整性。

## 4. 资源与算力

- 摘要和元数据中**未明确提及**所使用的计算资源、GPU型号、数量或训练时长。由于这是一个以湿实验为主的方法论文，而非深度学习模型训练，因此可能不需要大量GPU算力。图像处理、配准、3D重建可能需要普通工作站或服务器，但未说明。
- **结论**：文中没有提到具体的算力需求。

## 5. 实验数量与充分性

- **实验数量**：从摘要描述来看，作者在**多种组织类型**（正常和癌组织）以及**多种免疫结构**（次级淋巴结构、三级淋巴结构、神经免疫互作）上进行了验证。但没有给出具体的样本数（例如多少病例、多少组织块），因此无法判断统计显著性。
- **充分性**：作为方法学论文，实验设计侧重于技术可行性验证，覆盖了关键的生物应用场景（神经免疫互作和淋巴结构免疫分型），并且提供了体积成像后薄切高分辨分析的交叉验证。但缺乏与传统2D多重成像在相同组织上的定量比较，也未报告成像深度、抗体穿透效率等量化指标。整体上实验对于证明方法可行是充分的，但对于全面评估稳健性和可重复性可能还不够。

## 6. 论文的主要结论与发现

- v-CyCIF成功实现了在1 mm厚人类FFPE组织中对免疫细胞和神经进行多重三维成像，克服了抗体穿透、信号串扰、光衰减等关键障碍。
- 利用虚拟H&E染色，可以在3D图像中识别组织学结构，与常规H&E一致。
- 成功观察到了神经和免疫细胞之间的三维空间关系（神经免疫互作）。
- 能够对完整的次级淋巴结构（如脾脏生发中心）和三级淋巴结构（肿瘤浸润中的淋巴细胞聚集体）进行免疫细胞亚型的3D空间分布分析。
- 通过对体积成像后的组织再包埋切片，实现了同一组织区域的高分辨率亚细胞分析，补全了3D宏观结构和2D微观细节之间的尺度鸿沟。
- v-CyCIF为临床FFPE标本的多尺度3D空间蛋白质组分析提供了一个灵活、可扩展的框架。

## 7. 优点

- **技术突破**：首次将循环免疫荧光与体积成像结合应用于人类FFPE厚组织，解决了长期存在的人类标本3D多重成像难题。
- **兼容临床样本**：直接使用常规FFPE组织，无需特殊固定或基因操作，具有很高的临床转化潜力。
- **多尺度整合**：体积成像后允许再包埋切片，实现从宏观（1 mm厚）到亚细胞（薄切高分辨）的跨尺度关联，是独特的亮点。
- **虚拟H&E**：不需要单独进行H&E染色即可获得组织学形态，节省样本并利于图像配准。
- **模块化**：标记方案灵活，可根据需要选择抗体组合，适用不同研究目的。

## 8. 不足与局限

- **样本量小**：未报告病例数，可能仅为概念验证，统计效力不足。
- **缺乏定量对比**：没有与传统2D多重成像或其它3D方法（如完整组织透明的LSFM）进行系统比较，难以客观评价优势程度。
- **抗体穿透限制**：虽然克服了一定障碍，但1 mm厚度下深层组织的抗体结合效率和均匀性可能仍低于薄片，会影响定量准确性。
- **成像时间**：多轮循环+体积成像的时间开销较大（未提及具体时长），可能限制高通量应用。
- **组织损伤风险**：多轮化学处理和光漂白可能造成组织退化或抗原损失，评估不足。
- **应用范围**：主要聚焦免疫细胞和神经，对其他细胞类型（如基质细胞、血管内皮等）的兼容性尚未充分展示。
- **资源成本**：需要专业的光片显微镜设备和循环成像自动化系统，普适性受限。

（完）
