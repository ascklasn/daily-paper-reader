---
title: "Morpho-FM: spatial molecular reconstruction from routine H&E histology using transcriptomic foundation-model priors"
title_zh: "Morpho-FM：利用转录组基础模型先验从常规H&E组织学进行空间分子重建"
authors: "Huang, J.-J., Feng, X., Qu, L.-H., Zheng, L.-L."
date: 2026-06-19
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.15.732498v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: "利用转录组基础模型从H&E图像重建空间分子图谱"
tldr: "常规H&E染色缺乏转录组信息，空间转录组虽能提供但成本高。Morpho-FM利用预训练单细胞转录组基础模型先验，通过轻量级适配器从H&E全切片图像预测空间基因表达，实现密集重建。在前列腺癌基准上平均每基因Pearson相关性达0.286-0.298，优于五种对比方法，并恢复了乳腺癌中的分子梯度与组织区域。结果表明转录组先验能有效约束形态学分子解码。"
source: biorxiv
selection_source: fresh_fetch
motivation: "常规H&E组织学缺乏转录组信息，而空间转录组成本高、采样稀疏，需从H&E图像低成本预测基因表达。"
method: "采用弱监督框架，以预训练单细胞转录组基础模型为先验，通过形态-转录组适配器从H&E全切片特征解码空间基因表达，支持密集重建。"
result: 在前列腺癌基准上平均每基因Pearson相关性0.286-0.298，在肾癌和乳腺癌数据集上表现良好，消融证明转录组初始化是关键增益。
conclusion: 转录组基础模型先验能有效约束形态学分子解码，Morpho-FM将空间转录组洞察扩展到常规病理切片。
---

## 摘要
常规苏木精-伊红（H&E）组织学在临床尺度上捕捉组织架构，但缺乏对组织肿瘤上皮、间质、血管和免疫区室的转录程序的直接分子读取。空间转录组学提供了这一背景，但成本、工作流程复杂性和稀疏采样限制了常规使用。大多数现有的组织学-表达模型是在小型配对队列上从头训练的，因此在从稀疏测量外推至密集的全组织分子图谱时约束力较弱。此处我们介绍Morpho-FM，一个弱监督框架，通过将预训练的单细胞转录组基础模型先验条件置于局部组织学邻域上，从常规H&E全切片图像预测空间基因表达。一个轻量级的形态学-转录组适配器将缓存的整张切片组织学特征映射到转录组解码器，从而能够在测量位置进行预测、密集的全切片重建，并重新聚合到原始测量支持。在统一的 prostate cancer 基准测试中，Morpho-FM 在五种代表性方法中取得了最强的整体性能，在旋转单切片评估中达到平均每基因 Pearson 相关性0.286，在多切片保留验证中达到0.298。该框架在 kidney cancer 切片中重现了这一优势，在56次定向单切片评估中达到平均相关性0.210，并在外部迁移至 clear-cell renal cell carcinoma 切片后保留了可测量的预测信号。受控消融分析确定预训练转录组初始化是性能提升的可重复来源，超过归因于组织学特征骨干变化的提升。除预测准确性基准外，Morpho-FM 在 Xenium 和 HER2ST breast cancer 数据集中恢复了富集 ERBB2 的肿瘤区室、边界相关的分子梯度以及与注释对齐的组织域。总之，这些结果支持转录组基础模型先验作为形态条件分子解码的有效约束，并展示了 Morpho-FM 在常规病理切片中扩展空间转录组学视野的潜力。

## Abstract
Routine haematoxylin and eosin (H&E) histology captures tissue architecture at clinical scale, but lacks a direct molecular readout of the transcriptional programmes that organise tumour epithelium, stroma, vasculature and immune compartments. Spatial transcriptomics provides this context, yet cost, workflow complexity and sparse sampling limit routine use. Most existing histology-to-expression models are trained de novo on small paired cohorts and therefore remain weakly constrained when extrapolating from sparse measurements to dense, tissue-wide molecular maps. Here we introduce Morpho-FM, a weakly supervised framework that predicts spatial gene expression from routine H&E whole-slide images by conditioning a pretrained single-cell transcriptomic foundation-model prior on local histological neighbourhoods. A lightweight morphology-to-transcriptome adapter maps cached whole-slide histology features into a transcriptomic decoder, enabling prediction at measured locations, dense full-section reconstruction, and re-aggregation to the original measurement support. Across harmonized prostate cancer benchmarks, Morpho-FM achieved the strongest overall performance among five representative methods, reaching mean per-gene Pearson correlations of 0.286 in rotating single-slide evaluation and 0.298 in multi-slide held-out validation. The framework reproduced this advantage across kidney cancer sections, achieved a mean correlation of 0.210 across 56 directed single-slide evaluations and retained measurable predictive signal after external transfer to clear-cell renal cell carcinoma sections. Controlled ablation analyses identified pretrained transcriptomic initialization as a reproducible source of performance gain exceeding that attributable to changes in the histology feature backbone. Beyond predictive accuracy benchmarks, Morpho-FM recovered ERBB2-enriched tumour compartments, boundary-associated molecular gradients, and annotation-aligned tissue domains across Xenium and HER2ST breast cancer datasets. Together, these results support transcriptomic foundation-model priors as an effective constraint for morphology-conditioned molecular decoding and demonstrate the potential of Morpho-FM to extend spatial transcriptomic insight across routine pathology sections.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **问题**：常规H&E染色是临床广泛使用的组织学技术，能呈现组织架构，但缺乏直接的转录组信息。空间转录组学（ST）可提供分子背景，但成本高、工作流程复杂、采样稀疏，限制了常规使用。现有从H&E预测基因表达模型大多在小型配对数据集上从头训练，输出空间约束弱，难以从稀疏测量外推到全组织密集分子图谱。
- **背景**：计算病理学中的基础模型（如HIPT）能表示组织形态；单细胞转录组基础模型（如CellFM）学习了基因共表达、细胞状态等结构。但此前这两类模型在空间基因表达预测任务中尚未有效连接。
- **研究目标**：验证将病理学形态特征通过转录组基础模型先验解码，能否在有限配对数据下更准确地进行空间分子重建。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：弱监督框架，利用预训练的单细胞转录组基础模型（CellFM）作为解码器的先验，将局部H&E组织学邻域作为条件，预测空间基因表达。分离为两个耦合约束：病理特征捕捉组织架构变化，转录组解码器约束表达状态空间。
- **关键技术细节**：
  - **H&E特征缓存**：使用HIPT（Hierarchical Image Pyramid Transformer）编码整张H&E切片，得到特征网格（分辨率1/16原图），每个位置为579维向量。
  - **局部盘状多实例学习（MIL）bag**：每个ST测量位置，在特征网格上取半径为对应测量半径的圆形区域内的特征作为bag实例。
  - **形态-转录组适配器**：轻量级两层全连接网络（含层归一化、非线性激活、dropout），将579维特征映射到CellFM的1536维潜空间。
  - **转录组解码器**：使用预训练CellFM，对于每个实例，解码得到每个基因的非负归一化表达率。bag内实例率取平均得到bag级预测。
  - **训练目标**：负二项计数损失（negative-binomial count objective），考虑ST测量的过度离散。损失函数包含基因特异性色散参数。
  - **训练参数**：大部分CellFM参数冻结，仅训练适配器、基因嵌入矩阵、解码器投影和色散参数。AdamW优化，混合精度，早停。
  - **预测模式**：支持测量位置预测和全切片密集重建，密集预测可重新聚合到原始测量支持进行一致性检验。

## 3. 实验设计：数据集、基准测试、对比方法

- **数据集**：
  - 前列腺癌：HEST-1k中的4张切片（INT25-INT28），每张包含H&E和ST配对。
  - 肾癌：HEST-1k中的8张切片（INT13-INT19, INT21, INT24）。
  - 外部迁移：两个外部透明细胞肾细胞癌（ccRCC）Visium切片。
  - 乳腺癌Xenium：10x Genomics Xenium FFPE乳腺癌两个连续切片（S1、S2），经基因面板匹配后保留306个基因。
  - HER2ST：患者H的三个连续切片（H1-H3），保留13080个基因。
- **基准测试（Benchmark）**：
  - **单切片旋转评估**：每个前列腺/肾癌切片单独训练，其他切片测试，得到定向比较（前列腺12个方向，肾癌56个方向）。
  - **多切片保留验证**：前列腺4个fold，每个fold用两个切片训练、一个验证、一个测试。
  - **外部迁移**：肾癌多切片训练后直接应用于ccRCC切片。
  - **Xenium**：四个设置（S1→S1, S1→S2, S2→S2, S2→S1），评估测量位置预测和密集重建后重新聚合。
  - **HER2ST**：留一切片交叉验证（H1 from H2+H3, 等）。
- **对比方法**：HisToGene, iStar, mclSTExp, sCellST, HiST。所有方法使用相同预处理、空间坐标、基因面板和评估指标。

## 4. 资源与算力

- 论文中**未明确说明**使用的GPU型号、数量、训练时长等算力细节。仅提及使用AdamW优化器、自动混合精度训练、早停等常规设置。未提供硬件配置、训练时间或能耗信息。

## 5. 实验数量与充分性

- **实验数量**：包含前列腺癌（12+4个方向）、肾癌（56个方向）、ccRCC外部迁移（2个切片）、Xenium（4个设置）、HER2ST（3个留一实验），以及消融实验（初始化对比、特征骨干对比）。总体实验规模较大，覆盖多种癌种、平台和训练场景。
- **充分性**：实验设计较为充分，评估了单切片、多切片、外部迁移、跨平台迁移、密集重建与重新聚合验证。消融实验直接比较了转录组初始化（预训练vs随机）和特征骨干（HIPT vs ResNet-50），控制变量良好。评估指标统一（每基因Pearson相关性、HVG召回等），过程客观。
- **公平性**：所有对比方法在同一预处理管线、相同基因面板、相同评估指标下运行，未修改基线核心架构。因此对比公平。

## 6. 论文的主要结论与发现

1. **Morpho-FM在多个基准测试中显著优于五种对比方法**：前列腺单切片平均每基因Pearson 0.286（vs iStar 0.155）；多切片0.298（vs iStar 0.114）；肾癌0.210（vs iStar 0.049）。
2. **转录组基础模型先验是性能提升的主要来源**：消融表明预训练CellFM初始化带来的增益（单切片+0.081，多切片+0.061）远大于替换特征骨干（HIPT vs ResNet-50无稳定差异）。
3. **能够进行测量约束的密集全切片分子重建**：在Xenium乳腺癌中，密集重建后重新聚合与测量数据的相关性保持结构（如ERBB2 r=0.565-0.692），边界梯度和区域富集分析与测量一致。
4. **潜在表示支持组织域发现**：Morpho-FM的潜变量聚类与人工注释的一致性（NMI 0.376-0.396）远高于原始形态特征聚类（NMI 0.105-0.121），并恢复了KRT14/KRT5富集的肌上皮层。
5. **跨平台推广性**：在HER2ST乳腺癌数据上留一验证，每基因平均Pearson约0.14（顶部HVG约0.40），且聚类域与组织标签有可测量一致性。

## 7. 优点：方法或实验设计上的亮点

- **创新性**：首次将病理学基础模型和单细胞转录组基础模型耦合，用转录组先验约束形态学分子解码。
- **设计巧妙**：通过缓存特征网格将稀疏测量与密集重建统一在共享坐标系；使用MIL bag匹配ST测量的区域性质；轻量适配器避免从头训练大量参数。
- **评估全面**：涵盖多种癌种（前列腺、肾、乳腺）、多平台（Visium、Xenium、HER2ST）、多训练范式（单/多切片、外部迁移）、密集重建一致性检验。
- **消融实验严谨**：直接分离了转录组初始化和特征骨干的影响，控制变量充分。
- **生物学可解释性**：潜变量聚类恢复已知组织域（如肌上皮层），分子梯度符合病理边界。

## 8. 不足与局限

- **算力信息缺失**：未报告GPU型号、数量、训练时长，影响可重复性和资源需求评估。
- **外部迁移性能波动**：在第二个ccRCC切片上表现下降（平均Pearson 0.138），表明跨数据集迁移仍敏感于组织异质性和平台差异。
- **依赖配对数据**：仍需要H&E与ST配对用于训练，不能完全摆脱空间转录组。
- **密集预测无法直接验证**：未测量位置无真值，仅通过重新聚合进行一致性检查，不能替代直接测量。
- **缺乏不确定性估计**：预测无校准的置信度，用户难以区分高置信与低置信区域。
- **跨平台基因面板匹配限制**：Xenium仅保留了306个基因，HER2ST为13080，可能遗漏重要基因。
- **组织域识别为假设性**：HER2ST无标签切片上的域聚类仅为候选，需进一步验证。
- **单细胞分辨率未深入**：Xenium分析使用细胞级测量，但MIL bag基于宏观特征网格，可能丢失精细空间结构。
- **方法对比范围**：尽管对比了五种方法，但可能遗漏其他最新工作（如基于Transformer的预测模型）。

（完）
