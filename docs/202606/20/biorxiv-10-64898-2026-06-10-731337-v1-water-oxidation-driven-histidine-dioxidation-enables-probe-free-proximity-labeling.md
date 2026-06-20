---
title: Water oxidation-driven histidine dioxidation enables probe-free proximity labeling
title_zh: 水氧化驱动的组氨酸双氧化实现无探针邻近标记
authors: "Lee, C., Lee, J. K., Yoo, C.-M., Kim, B. G., Yoon, G., Kang, J., Na, S., Rhee, H.-W., Kwon, T.-H."
date: 2026-06-12
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.10.731337v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 无探针邻近标记用于空间蛋白组学
tldr: 现有光催化邻近标记依赖单线态氧和探针捕获，存在因探针分布不均导致的空间偏差。本文开发IDM光催化剂，通过水氧化产生羟基和超氧自由基，协同双自由基机制将组氨酸二氧化为稳定内酯互变异构体，实现无探针活细胞邻近标记。在细胞内囊泡运输中，该方法不仅检出外泌体标志物，还揭示了被探针依赖方法低估的囊泡运输亚蛋白质组。该策略为空间蛋白质组映射提供了一种最小偏差的工具。
source: biorxiv
selection_source: fresh_fetch
motivation: 克服传统光催化邻近标记中因探针非均匀分布导致的蛋白质组覆盖偏差。
method: 设计IDM光催化剂，利用水氧化产生·OH和O2·-，协同氧化组氨酸为稳定二氧代内酯，实现无探针活细胞邻近标记。
result: 在囊泡运输中，PF-Map不仅检出外泌体标志物，还捕获了探针依赖方法低估的囊泡运输亚蛋白质组。
conclusion: PF-Map为空间蛋白质组提供了一种最小偏差的光催化策略，适用于探针可达性不均的细胞区室。
---

## 摘要
光催化邻近标记(photo-PL)已成为亚细胞区室空间蛋白质组学的有力工具。然而，许多photo-PL工具依赖于单线态氧(1O2)生成高度不稳定的内过氧化物中间体，这些中间体必须立即被高浓度的外源探针捕获。这一限制可能会偏差空间蛋白质组覆盖范围，特别是在诸如内体和外泌体等动态且异质的区室中，其中探针的可及性本质上是不均匀的。在此，我们开发了IDM，一种通过水氧化而非1O2生成羟自由基(*OH)和超氧自由基(O*-)的有机光催化剂，从而实现协同双自由基机制，用于活细胞中的无探针邻近蛋白映射(PF-Map)。所产生的自由基将邻近的组氨酸残基双氧化为持久性二氧化的状态(His-2O)，该状态以内酰胺互变异构体形式热力学稳定，在细胞裂解后仍保持亲电性并可化学寻址。通过将组氨酸氧化与活细胞探针捕获解耦，PF-Map可以最小化由探针非均匀分布引起的空间偏差。将PF-Map应用于细胞内囊泡运输，我们发现PF-Map和依赖探针的工作流程(PD-Map)均能稳健地识别外泌体标志物，而PF-Map还额外揭示了PD-Map低估的隐藏囊泡运输相关亚蛋白质组。总之，我们建立了一种用于复杂生物系统中空间蛋白质映射的、偏差最小的光催化策略。

## Abstract
Photocatalytic proximity labeling (photo-PL) has emerged as a powerful tool for spatial proteomics in subcellular compartments. However, many photo-PL toolboxes rely on singlet oxygen (1O2) to generate highly unstable endoperoxide intermediates that must be trapped immediately by high concentrations of exogenous probes. This constraint can bias spatial proteome coverage, particularly in dynamic and heterogeneous compartments such as endosomes and exosomes, where probe accessibility is intrinsically nonuniform. Here, we develop IDM, an organic photocatalyst that generates hydroxyl (*OH) and superoxide (O *-) radicals via water oxidation instead of 1O , enabling a synergistic dual-radical mechanism for probe-free proximal protein mapping in live cells (PF-Map). The resulting radicals dioxidize proximal histidine residues into a persistent dioxidized state (His-2O) that is thermodynamically stabilized as lactam tautomers, which remain electrophilic and chemically addressable after cell lysis. By decoupling histidine oxidation from live{square}cell probe capture, PF{square}Map can minimize spatial bias arising from heterogeneous probe distribution. Applying PF{square}Map to intracellular vesicle trafficking, we find that both PF{square}Map and a probe{square}dependent workflow (PD{square}Map) robustly identify exosome markers, whereas PF{square}Map additionally reveals a hidden vesicle trafficking-related subproteome that PD-Map underestimated. Together, we establish a minimally biased photocatalytic strategy for spatial protein mapping in complex biological systems.

Graphical abstract

O_FIG O_LINKSMALLFIG WIDTH=200 HEIGHT=111 SRC="FIGDIR/small/731337v1_ufig1.gif" ALT="Figure 1">
View larger version (35K):
org.highwire.dtl.DTLVardef@13da43dorg.highwire.dtl.DTLVardef@1e9cb7corg.highwire.dtl.DTLVardef@2e7557org.highwire.dtl.DTLVardef@19e16c_HPS_FORMAT_FIGEXP  M_FIG C_FIG

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义

- **研究动机**：现有光催化邻近标记方法（如基于单线态氧的photo-PL）依赖外源探针捕获不稳定的内过氧化物中间体，这导致在探针可及性不均匀的区室（如内体、外泌体）中产生空间蛋白质组覆盖偏差。
- **核心目标**：开发一种不依赖外源探针、通过水氧化产生自由基直接修饰蛋白质的方法，实现无探针、最小偏差的空间蛋白质组映射。
- **整体含义**：提出了一种全新的光催化机制（双自由基协同氧化组氨酸为稳定二氧代内酯），突破了传统探针依赖型方法的局限，为复杂细胞区室的空间蛋白质组学提供了更公正的工具。

## 2. 论文提出的方法论

- **核心思想**：设计有机光催化剂IDM，通过水氧化（而非单线态氧途径）产生羟自由基(·OH)和超氧自由基(O₂·⁻)，两种自由基协同作用将邻近组氨酸残基双氧化为持久性的二氧代状态（His-2O），该状态以内酰胺互变异构体形式热力学稳定，在细胞裂解后仍保持亲电性和化学可寻址性。
- **关键技术细节**：
  - 光催化剂IDM在水存在下光照产生·OH和O₂·⁻，实现无外源探针的邻近标记。
  - 组氨酸双氧化产物稳定，可在细胞裂解后通过化学方法捕获（如生物正交连接），从而将活细胞氧化与捕获步骤解耦。
  - 方法命名为PF-Map（probe-free proximity mapping），区别于传统探针依赖的PD-Map。
- **公式/算法流程（文字说明）**：
  1. 活细胞中表达或添加IDM光催化剂。
  2. 光照激发IDM，通过水氧化生成·OH和O₂·⁻。
  3. 双自由基与邻近蛋白质的组氨酸残基反应，生成稳定的二氧代组氨酸（His-2O）。
  4. 细胞裂解后，利用化学选择反应（如基于炔基或肼的探针）对His-2O进行标记和富集。
  5. 质谱鉴定富集的蛋白质，获得空间蛋白质组。

## 3. 实验设计

- **应用场景**：细胞内囊泡运输系统（包括内体、外泌体等动态异质区室）。
- **数据集/基准**：未明确提及特定公开数据集；以传统探针依赖方法（PD-Map）作为对比基准。
- **对比方法**：PD-Map（prob-dependent workflow），即依赖单线态氧和外源探针的邻近标记方法。
- **实验验证**：在囊泡运输背景下比较PF-Map和PD-Map检测到的蛋白质组，发现两者均能识别已知外泌体标志物，但PF-Map额外捕获了PD-Map低估的囊泡运输相关亚蛋白质组。

## 4. 资源与算力

- 论文摘要及元数据中**未明确说明**所使用的GPU型号、数量、训练时长等算力资源。仅提及使用质谱进行蛋白质鉴定，未涉及大规模深度学习模型训练。因此无法提供具体算力信息。

## 5. 实验数量与充分性

- 从摘要看，论文主要是在囊泡运输场景下进行了一组对比实验（PF-Map vs PD-Map），并展示了外泌体标志物识别和亚蛋白质组发现。但未提及消融实验、不同细胞类型或扰动的重复实验数量。由于缺乏完整全文，无法评估实验充分性。不过，方法本身具有新颖机制，初步验证了概念可行性。
- **客观性**：对比了传统探针依赖方法，显示PF-Map能发现被低估的蛋白质组，结论相对客观，但需要更多独立实验验证。

## 6. 论文的主要结论与发现

- PF-Map（无探针光催化邻近标记）能有效在活细胞中进行空间蛋白质组映射，克服了传统方法因探针分布不均导致的空间偏差。
- 在细胞内囊泡运输中，PF-Map不仅稳健识别外泌体标志物，还揭示了被PD-Map低估的囊泡运输相关亚蛋白质组，表明该方法能捕获更完整的空间蛋白组信息。
- 水氧化驱动的双自由基机制将组氨酸氧化为稳定二氧代内酯，实现活细胞氧化与后续捕获解耦，是方法的核心创新。

## 7. 优点

- **机制创新**：首次利用水氧化而非单线态氧产生双自由基，实现无外源探针的邻近标记，从根本上避免探针非均匀分布导致的偏差。
- **化学稳定性**：组氨酸二氧代产物（His-2O）以内酰胺形式稳定，便于裂解后化学操作，标记事件与检测解耦，简化实验流程。
- **适用性**：特别适合探针可及性不均匀的动态亚细胞区室（如内体、外泌体、囊泡），有望推广到其他空间蛋白质组学研究。
- **方法简洁**：无需复杂探针合成，仅需光催化剂IDM和光照即可实现原位标记。

## 8. 不足与局限

- **实验覆盖不足**：仅在一个生物学场景（囊泡运输）中验证，缺乏多种细胞类型、不同亚细胞区室的系统性评估。
- **缺乏消融研究**：未显示对光照时间、催化剂浓度、pH等条件的优化和消融实验，可能影响结论的鲁棒性。
- **可能与原有方法重叠**：尽管PF-Map捕获了额外亚蛋白质组，但与传统方法的重叠程度、背景非特异性结合等未明确讨论。
- **扩展性**：组氨酸氧化修饰是否会干扰蛋白质功能？体内长期光照对细胞毒性如何？文中未提及。
- **资源限制**：基于摘要无法获取更多技术细节，如催化剂效率、标记半径、时间分辨率等参数未提供。

（完）
