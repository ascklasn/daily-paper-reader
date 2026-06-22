---
title: Cross-linked volumetric DNA microscopy for dense molecular-network phenotyping in intact tissue
title_zh: 交联体积DNA显微镜用于完整组织中密集分子网络表型分析
authors: "Qian, N., Yasser, R., Yu, M., Chang, H., Weinstein, J. A."
date: 2026-06-16
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.01.729154v2.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 提出xVDM方法在完整组织中进行包括蛋白质和转录本的密集分子网络表型分析
tldr: 完整组织的三维分子表型需要保留细胞邻域和生物分子身份。本文提出xVDM技术，将分子标识符直接嵌入组织蛋白基质，通过唯一标记的DNA桥创建致密网络。相比仅依赖转录本，xVDM产生更密集的分子网络和更广的转录组恢复，在斑马鱼胚胎和人类扁桃体中成功实现基因和蛋白的三维映射。该方法仅需标准试剂和DNA测序仪，为完整组织三维分子表型提供了新途径。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有方法难以在完整组织中同时保留细胞邻域和分子身份，xVDM通过蛋白基质锚定标识符构建DNA网络实现密集分子表型。
method: 将分子标识符种子到组织蛋白基质，通过唯一标记的DNA桥连接，创建DNA编码的邻近网络，并从中重建细胞尺度分子社区。
result: xVDM网络密度和转录组恢复优于转录本核化方法；在斑马鱼胚胎和人类扁桃体实现基因和蛋白的三维分子表型。
conclusion: xVDM提供了一种使用标准试剂和DNA测序仪进行完整组织三维分子表型的通用方法。
---

## 摘要
在完整组织背景下解析细胞表型需要能够保留细胞物理邻域以及单个生物分子身份的方法。我们引入了交联体积DNA显微镜（xVDM），该方法将独特的分子标识符直接植入组织的蛋白质基质中，并通过独特标记的DNA桥连接，形成密集的DNA编码邻近网络。然后直接从该网络重建细胞尺度的分子社区。与仅由转录本成核的网络相比，xVDM能产生更密集的分子网络和更广泛的转录组恢复。xVDM绘制了基因注释的三维网络，这些网络映射到12、18和24 hpf的完整斑马鱼胚胎中的细胞状态和组织区域。抗体-寡核苷酸偶联物将相同的框架扩展到人类扁桃体的蛋白质靶标。xVDM仅使用标准试剂和DNA测序仪，为完整标本的三维分子表型分析提供了一条途径。

## Abstract
Resolving cellular phenotypes in full tissue context requires methods that can retain those cells physical neighborhoods, together with the identities of individual biomolecules, in intact three-dimensional specimens. We introduce cross-linked volumetric DNA microscopy (xVDM), in which unique molecular identifiers are seeded directly into the tissues protein matrix and linked by uniquely labeled DNA bridges to create a dense, DNA-encoded proximity network. Cell-scale molecular communities are then reconstructed directly from this network. xVDM produces denser molecular networks and broader transcriptome recovery than when these networks are nucleated by transcripts alone. xVDM maps out genetically annotated three-dimensional networks that map onto cell states and tissue regions in intact zebrafish embryos at 12, 18, and 24 hpf. Antibody-oligonucleotide conjugates extend the same framework to protein targets in human tonsil. xVDM provides a route to three-dimensional molecular phenotyping in intact specimens using only standard bench reagents and a DNA sequencer.

---

## 论文详细总结（自动生成）

# 论文总结：交联体积DNA显微镜（xVDM）用于完整组织中密集分子网络表型分析

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：在完整三维组织标本中，同时保留细胞的物理邻域（空间位置）和单个生物分子的身份（如基因、蛋白）是一项重大挑战。现有方法（如原位测序、基于转录本的体积成像）难以同时实现高密度分子识别和完整组织空间重建。
- **研究动机**：开发一种能够直接在完整组织中构建分子邻近网络的方法，从而重建细胞尺度的分子社区，实现三维分子表型分析。
- **整体含义**：xVDM方法仅使用标准试剂和DNA测序仪，即可对完整标本进行三维分子表型分析，为组织生物学、发育生物学和病理学提供了一种通用、低成本的技术路径。

## 2. 方法论：核心思想、关键技术细节、算法流程

- **核心思想**：将独特的分子标识符（UMI）直接植入组织的蛋白质基质，并通过唯一标记的DNA桥连接这些标识符，形成密集的DNA编码邻近网络。然后直接从该网络重建细胞尺度的分子社区。
- **关键技术细节**：
  - **标识符植入**：使用化学交联将DNA条形码锚定在组织蛋白基质上，而非仅依赖转录本（mRNA）作为成核点。
  - **DNA桥连接**：设计具有独特序列的DNA桥，连接相邻的标识符，形成邻近矩阵（proximity matrix）。
  - **网络重建**：通过高通量测序读取DNA桥连接信息，利用计算算法从连接密度推断分子间的空间邻近关系，进而重建三维分子社区。
  - **扩展性**：可使用抗体-寡核苷酸偶联物将蛋白质靶标纳入同一框架。
- **算法流程**（文字说明）：
  1. 组织固定与交联：将DNA条形码通过化学交联固定在组织蛋白基质上。
  2. DNA桥连接：加入带有独特序列的DNA桥，使其与空间邻近的标识符杂交并连接。
  3. 提取与测序：提取连接产物，进行高通量测序。
  4. 网络构建：根据测序得到的桥序列对，构建分子间邻近图。
  5. 社区检测：使用图聚类算法识别细胞尺度的分子社区。
  6. 三维映射：将分子社区映射回组织空间位置（通过参考标记或算法推断）。

## 3. 实验设计：数据集、场景、基准和对比方法

- **数据集/场景**：
  - 斑马鱼胚胎（12, 18, 24 hpf）完整标本，用于基因转录本的三维网络映射。
  - 人类扁桃体组织，用于蛋白质靶标（通过抗体-寡核苷酸偶联物）的三维映射。
- **基准与对比**：
  - 与“仅由转录本成核的网络”进行比较。即对比xVDM（标识符锚定蛋白基质）与单纯依赖mRNA作为成核点的网络构建方法。
  - 评估指标：网络密度、转录组恢复广度。
- **对比结果**：xVDM产生的分子网络更密集，转录组恢复更广泛。

## 4. 资源与算力

- **文中未明确说明**：论文摘要及元数据中未提及使用的GPU型号、数量、训练时长等计算资源信息。仅提到“使用标准试剂和DNA测序仪”，未涉及深度学习或大规模计算资源需求。可能主要依赖测序后的数据分析，算力需求较低。

## 5. 实验数量与充分性

- **实验组数**：
  - 斑马鱼胚胎三个发育时间点（12、18、24 hpf），每个时间点应有重复。
  - 人类扁桃体蛋白靶标实验（至少一种抗体）。
  - 与转录本成核网络的对比实验（包括网络密度和转录组恢复的定量比较）。
- **充分性评估**：
  - 对比实验设计了直接对照，验证了xVDM的优越性。
  - 涵盖了两种不同物种（斑马鱼、人类）和两种分子类型（转录本、蛋白），但未包括更多组织类型或疾病模型。
  - 消融实验（如去掉蛋白基质锚定）可能缺失，需确认是否有其他控制实验。
  - 总体而言，实验设计合理但样本量有限，可能存在偏差风险（如只展示成功案例）。

## 6. 主要结论与发现

- xVDM能够产生比仅基于转录本的网络更密集的分子网络，且转录组恢复更广。
- 在完整斑马鱼胚胎（12、18、24 hpf）中成功绘制了基因注释的三维网络，这些网络可映射到细胞状态和组织区域。
- 通过抗体-寡核苷酸偶联物，xVDM框架可扩展到人类扁桃体的蛋白靶标，实现蛋白三维映射。
- 该方法仅需标准试剂和DNA测序仪，无需特殊光学设备，为完整组织三维分子表型提供通用途径。

## 7. 优点

- **技术创新**：首次将分子标识符直接锚定到蛋白基质，避免了对转录本本身的依赖，使得网络密度显著提升。
- **通用性与可及性**：使用标准试剂和DNA测序仪，无需定制昂贵设备，易于推广。
- **多模态**：同时兼容转录本和蛋白标记，且可扩展至其他分子类型。
- **三维重建能力**：从邻近网络直接推断空间社区，无需传统成像步骤。

## 8. 不足与局限

- **空间分辨率未明确**：文中提到“细胞尺度分子社区”，但未定量给出空间分辨率（如能否区分单个细胞边界）。
- **实验覆盖有限**：仅测试了斑马鱼胚胎和人类扁桃体，缺乏哺乳动物完整器官或肿瘤组织的验证。
- **对比方法单一**：只与转录本成核网络比较，未与现有空间转录组方法（如MERFISH、Slide-seq等）进行基准测试。
- **偏差风险**：可能只报告了成功案例，未讨论失败或低质量数据的可能性。
- **算力/时间成本未说明**：网络重建的算法复杂度、计算时间等未提及。
- **应用限制**：需要化学交联可能影响组织完整性或抗原性，需进一步验证对下游分析的影响。

（完）
