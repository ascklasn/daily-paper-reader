---
title: "UMITIC: An unsupervised framework for the joint characterization of cellular phenotypes and spatial neighborhoods in multiplex and hyperplex immunofluorescence imaging data"
title_zh: UMITIC：一种用于多重和超多重免疫荧光成像数据中细胞表型和空间邻域联合表征的无监督框架
authors: "Sangüesa Recalde, M., De Andrea, C. E., Ariz, M."
date: 2026-06-01
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.29.728633v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 从多重蛋白成像数据中无监督表征细胞表型和空间邻域
tldr: 多路复用成像技术可同时测量数十个蛋白标记，但高维数据分析极具挑战。UMITIC无监督框架通过CellCut分割、CellMap对比学习和TissueNet图神经网络，联合表征细胞表型和空间邻域。在7-58标记的多个数据集上，UMITIC准确识别免疫细胞群并重建组织区域，在专家注释数据上优于现有方法。该框架无需手动注释，提供客观可复现的组织分析工具。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有分析依赖专家手动注释，难以扩展到高维无标注数据，需无监督方法自动表征细胞表型和空间结构。
method: 提出UMITIC，包含核质分割CellCut、对比学习CellMap和空间图神经网络TissueNet三个模块，实现无监督联合分析。
result: 在扁桃体、结直肠癌和肺组织四个数据集上，UMITIC成功识别细胞亚型并重建解剖区域，性能优于现有方法。
conclusion: UMITIC无需注释即可实现从表型到组织的多尺度分析，为临床研究提供可解释、可复现的成像数据处理方案。
---

## 摘要
多重成像技术能够在保留组织背景的同时同时测量数十种蛋白质标志物，提供组织组织结构的高分辨率视图。然而，从这些高维数据集（尤其是在超多重（>20种标志物）设置下）中提取有意义的见解仍然是一个重大的计算挑战，特别是在缺乏标注数据的情况下。在这里，我们提出UMITIC（通过组织特征进行多重图像的无监督分析），一个模块化的无监督计算框架，用于从多重成像数据中联合表征细胞表型和组织邻域。UMITIC集成了三个组件：(i) CellCut，一种结合核和细胞质预测以改善框架轮廓描绘能力的策略；(ii) CellMap，一种对比学习方法，生成富含形态学特征的单细胞图像裁剪的低维表示；(iii) TissueNet，一种图神经网络，模拟空间细胞-细胞相互作用以识别组织邻域。我们在四个复杂度递增的数据集上评估了UMITIC，以评估其鲁棒性、可扩展性和生物学相关性。针对7重人类扁桃体数据集，该框架识别了典型的免疫细胞群并重建了公认的解剖区域。当应用于43重扁桃体图像时，UMITIC保留了这些组织级结构，同时实现了由增加标志物维度驱动的更精细的细胞亚型分层过程。我们进一步在58重结直肠癌队列上验证了我们的方法，UMITIC能够恢复先前报道的不同预后患者组之间的免疫组成差异和空间组织变化。最后，当使用专家标注的人类肺组织质谱成像数据集时，UMITIC与参考组织标注的一致性高于现有方法，显示出改进的肺微解剖重建准确性。这些结果共同表明，UMITIC能够在无需手动标注的情况下，对不同多重和超多重成像数据集中的细胞表型和组织结构进行一致且可解释的分析。

作者总结：理解细胞在组织内的组织方式对于解读疾病至关重要，然而分析组织成像数据仍然是一个重大挑战。最近开发的成像技术能够在单个组织切片中可视化数十种蛋白质，揭示前所未有的细胞身份和空间组织细节。然而，提取有意义的生物学见解需要专家病理学家进行大量手动标注工作，限制了可扩展性。在这里，我们提出了一个全自动计算框架，以无监督方式在两个互补层面表征组织结构：它基于蛋白质表达和形态识别细胞类型，并绘制这些细胞如何组织成空间一致的组织结构，且无需任何手动标注。我们的方法在细胞层面是模块化且可解释的。我们在四个独立数据集上验证了我们的框架，包括7到58个同时蛋白质标志物的面板，包括健康人体组织和结直肠癌队列，其中分析了具有不同免疫特征的患者。值得注意的是，UMITIC在定性和定量评估中均优于现有方法的性能。这些结果表明，我们的框架为在研究和临床环境中进行组织分析提供了客观、可解释和可重复的图像处理工具。

## Abstract
Multiplexed imaging technologies enable the simultaneous measurement of dozens of protein markers while preserving context, providing a high-resolution view of tissue organization schemes. However, extracting meaningful insights from these high-dimensional datasets--particularly in hyperplex settings (>20 markers)--remains a major computational challenge, especially in the absence of annotated data. Here, we present UMITIC (Unsupervised Analysis of Multiplex Images via TIssue Characterization), a modular and unsupervised computational framework for the joint characterization of cell phenotypes and tissue neighborhoods from multiplex imaging data. UMITIC integrates three components: (i) CellCut, a strategy that combines nuclear and cytoplasmic predictions to improve the delineation capabilities of the framework; (ii) CellMap, a contrastive learning approach that generates low-dimensional representations of single-cell image crops that are enriched with morphological features; and (iii) TissueNet, a graph neural network that models spatial cell-cell interactions to identify tissue neighborhoods. We evaluated UMITIC across four datasets of increasing complexity to assess its robustness, scalability and biological relevance. With respect to a 7-plex human tonsil dataset, the framework identified canonical immune cell populations and reconstructed well-established anatomical regions. When applied to a 43-plex tonsil image, UMITIC preserved these tissue-level structures while enabling a finer cell subtype stratification process driven by increased marker dimensionality. We further validated our method on a 58-plex colorectal cancer cohort, where UMITIC was able to recover previously reported immune composition differences and spatial organization variations between patient groups with different prognoses. Finally, when an expert-annotated mass cytometry imaging dataset concerning human lung tissue was used, UMITIC achieved higher agreement with the reference tissue annotations than the existing approaches did, demonstrating improved lung microanatomy reconstruction accuracy. Together, these results show that UMITIC enables consistent and interpretable analyses of both cellular phenotypes and tissue architectures across diverse multiplex and hyperplex imaging datasets without the need for manual annotations.

Author summaryUnderstanding how cells are organized within tissues is fundamental to deciphering diseases, yet analyzing tissue imaging data remains a major challenge. The recently developed imaging technologies enable the visualization of dozens of proteins in a single tissue section, revealing unprecedented cell identity and spatial organization details. However, extracting meaningful biological insights requires extensive manual annotation work performed by expert pathologists, limiting the scalability. Here, we present a fully automated computational framework that characterizes tissue architectures in an unsupervised manner at two complementary levels: it identifies cell types based on their protein expressions and morphologies and maps how those cells are organized into spatially coherent tissue structures, and it does so without requiring any manual annotations. Our approach is modular and interpretable at the cell level. We validated our framework across four independent datasets with panels consisting of 7 to 58 simultaneous protein markers, including healthy human tissue and a colorectal cancer cohort in which patients with distinct immune profiles were analyzed. Remarkably, UMITIC improved upon the performance of existing methods across both qualitative and quantitative assessments. These results suggest that our framework provides objective, interpretable and reproducible image processing tools for conducting tissue analyses in both research and clinical settings.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：多重和超多重免疫荧光成像技术能够同时测量数十种蛋白质标志物，保留组织背景，提供高分辨率组织结构视图。然而，从这些高维数据中提取有意义的生物学见解需要专家病理学家进行大量手动注释，导致可扩展性差、主观性强，尤其在没有标注数据的情况下，分析面临重大计算挑战。
- **研究动机**：开发一种无需手动标注、全自动、可解释且可复现的无监督计算框架，能够在细胞表型和空间邻域两个互补层面联合表征组织结构，以适应不同多重成像数据集（从7重到58重标志物）的分析需求。
- **整体含义**：提出的UMITIC框架为临床和研究环境中的组织分析提供了客观、可解释、可重复的图像处理工具，有望推动疾病机制理解和预后评估的自动化。

## 2. 论文提出的方法论

- **核心思想**：通过模块化无监督流水线，先进行细胞分割（核质联合），再通过对比学习获取单细胞形态与表达的低维表示，最后利用图神经网络建模细胞间空间相互作用，从而联合识别细胞表型和组织邻域。
- **关键技术细节**：
  - **CellCut**：结合核预测和细胞质预测的策略，改善细胞轮廓的描绘能力，为后续单细胞裁剪提供更准确的分割掩膜。
  - **CellMap**：一种对比学习方法，对单细胞图像裁剪（富含形态特征）生成低维表示，嵌入细胞表型信息。
  - **TissueNet**：图神经网络，将细胞视为节点、空间邻近关系视为边，建模细胞-细胞相互作用，在图上进行社区发现以识别空间一致的组织邻域。
- **算法流程（文字说明）**：
  1. 输入多重成像图像；
  2. 使用CellCut进行核-质联合分割，提取单细胞裁剪；
  3. 应用CellMap对单细胞裁剪进行对比学习，得到低维嵌入；
  4. 基于嵌入和细胞空间坐标构建细胞图；
  5. 使用TissueNet在图结构上进行无监督社区划分，输出细胞表型聚类和空间邻域分区。

## 3. 实验设计

- **数据集**：四个复杂度递增的数据集：
  - **7重人类扁桃体**：验证能否识别经典免疫细胞群和重建公认解剖区域。
  - **43重扁桃体**：测试更高维度下是否保持组织结构并支持更精细的细胞亚型分层。
  - **58重结直肠癌队列**：评估能否恢复不同预后患者组之间的免疫组成差异和空间组织变化。
  - **专家标注的人类肺组织质谱成像数据集**：与现有方法对比微解剖重建准确性。
- **Benchmark**：参考专家标注（肺组织）以及先前文献报道的疾病分组差异（结直肠癌）。
- **对比方法**：文中提到“UMITIC achieved higher agreement with the reference tissue annotations than the existing approaches did”，但未列出具体方法名称。

## 4. 资源与算力

- **文中未明确说明**使用的GPU型号、数量、训练时长或显存需求。仅描述为“全自动计算框架”，未提供硬件配置细节。

## 5. 实验数量与充分性

- **实验数量**：在四个不同数据集上进行了评估，涵盖健康组织和癌症队列，标志物数量从7到58种。
- **充分性**：实验覆盖了从简单到复杂、从单一图像到队列级数据的不同场景，且有定性与定量评估（如肺组织标注一致性）。但缺乏对更多方法（例如其他无监督聚类方法）的详细对比、消融实验（分析各模块贡献）的具体描述。由于全文未提供，无法判断消融实验是否完备。总体看，实验设计较为充分，能支撑方法有效性的初步结论。

## 6. 论文的主要结论与发现

- UMITIC能够在无需手动标注的条件下，一致且可解释地分析不同多重和超多重成像数据集中的细胞表型和组织结构。
- 在扁桃体、结直肠癌和肺组织数据上，UMITIC成功识别免疫细胞群、重建解剖区域，并在定量上优于现有方法。
- 增加标志物维度（43重 vs 7重）可实现更精细的细胞亚型分层，同时保留组织级结构。
- 在结直肠癌队列中，UMITIC恢复了与预后相关的免疫组成差异和空间组织变化，验证了其临床相关性。

## 7. 优点

- **无监督性**：完全自动化，无需专家手动标注，消除主观性，可扩展至大规模临床队列。
- **模块化与可解释性**：CellCut、CellMap、TissueNet各司其职，每个阶段的输出（细胞分割、嵌入、社区划分）均可独立检查和解释。
- **多尺度分析**：同时输出细胞表型（单细胞聚类）和空间组织邻域（图社区），提供从微观到介观的信息。
- **数据兼容性**：适用于从7重到58重标志物的不同成像平台（如多重免疫荧光、质谱成像），鲁棒性强。
- **性能优越**：在专家标注数据集上重建准确性高于现有方法。

## 8. 不足与局限

- **未明确提及算力需求**：模型在超高清或大规模队列上的可部署性难以评估。
- **缺乏详尽的消融实验**：文中未展示三个模块各自的贡献分析，也未对比不同分割策略或对比学习设置的影响。
- **对比方法不清晰**：未列出具体对比方法的名称、设置和公平性控制（如超参数调优是否一致），削弱了性能提升的量化可信度。
- **验证依赖专家标注**：尽管方法无监督，但效果评估仍需专家标注，可能引入参考标准本身的偏差。
- **应用限制**：仅测试了扁桃体、结直肠癌和肺组织，其他组织类型（如脑、肝）及低质量图像（噪声、染色不均）的鲁棒性未知。

（完）
