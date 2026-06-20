---
title: "Morpho-FM: spatial molecular reconstruction from routine H&E histology using transcriptomic foundation-model priors"
title_zh: "Morpho-FM：利用转录组基础模型先验从常规H&E组织学进行空间分子重建"
authors: "Huang, J.-J., Feng, X., Qu, L.-H., Zheng, L.-L."
date: 2026-06-19
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.15.732498v1.full.pdf"
tags: ["query:hmm"]
score: 9.0
evidence: "利用转录组基础模型从H&E图像预测空间基因表达，多模态组织病理学方法"
tldr: "常规H&E染色捕获组织形态但缺乏转录组信息，空间转录组学成本高且采样稀疏。Morpho-FM利用预训练的单细胞转录组基础模型作为先验，通过轻量级适配器将H&E全切片图像特征映射到转录组解码器，实现从稀疏测量到密集组织图谱的基因表达预测。在前列腺癌、肾癌和乳腺癌等多个数据集上取得领先性能，并成功恢复肿瘤区域、分子梯度和组织结构。该方法验证了转录组先验在形态驱动分子解码中的有效性，可将空间转录组洞察扩展到常规病理切片。"
source: biorxiv
selection_source: fresh_fetch
motivation: "H&E染色缺乏直接分子信息，而空间转录组学成本高、工作流程复杂，亟需从常规H&E图像高效预测基因表达的方法。"
method: "利用预训练单细胞转录组基础模型作为先验，通过轻量级形态-转录组适配器将H&E全切片特征映射到转录组解码器，实现稀疏到密集的预测。"
result: 在前列腺癌基准中平均Pearson相关系数达0.286-0.298，在肾癌和乳腺癌数据集中表现优异，并能恢复ERBB2富集区域和分子梯度。
conclusion: 转录组基础模型先验有效约束形态条件分子解码，Morpho-FM可将空间转录组洞察扩展到常规病理切片。
---

## 摘要
常规苏木精和伊红(H&E)组织学以临床规模捕获组织架构，但缺乏对组织肿瘤上皮、基质、脉管和免疫区室转录程序的直接分子读数。空间转录组学提供了这一背景，但成本、工作流程复杂性和稀疏采样限制了常规应用。大多数现有的组织学-表达模型是在小型配对队列上新训练的，因此在从稀疏测量外推到密集的组织范围分子图谱时约束较弱。这里我们介绍Morpho-FM，一个弱监督框架，通过将预训练的单细胞转录组基础模型先验条件化于局部组织学邻域，从常规H&E全切片图像预测空间基因表达。一个轻量级的形态学-转录组适配器将缓存的整张切片组织学特征映射到转录组解码器，从而实现在测量位置的预测、密集全切片重建以及重新聚合到原始测量支持。在统一的前列腺癌基准测试中，Morpho-FM在五种代表性方法中取得了最强的整体性能，在旋转单切片评估中平均每基因皮尔逊相关系数达到0.286，在多切片留出验证中达到0.298。该框架在肾癌切片中复制了这一优势，在56个定向单切片评估中实现了平均相关系数0.210，并在外部迁移至透明细胞肾细胞癌切片后保留了可测量的预测信号。受控消融分析确定，预训练转录组初始化是可重复的性能增益来源，其增益超过归因于组织学特征骨干变化的部分。除了预测准确性基准测试外，Morpho-FM在Xenium和HER2ST乳腺癌数据集中恢复了富含ERBB2的肿瘤区室、边界相关的分子梯度和注释对齐的组织域。这些结果共同支持转录组基础模型先验作为形态条件化分子解码的有效约束，并展示了Morpho-FM将空间转录组学洞察扩展到常规病理切片的潜力。

## Abstract
Routine haematoxylin and eosin (H&E) histology captures tissue architecture at clinical scale, but lacks a direct molecular readout of the transcriptional programmes that organise tumour epithelium, stroma, vasculature and immune compartments. Spatial transcriptomics provides this context, yet cost, workflow complexity and sparse sampling limit routine use. Most existing histology-to-expression models are trained de novo on small paired cohorts and therefore remain weakly constrained when extrapolating from sparse measurements to dense, tissue-wide molecular maps. Here we introduce Morpho-FM, a weakly supervised framework that predicts spatial gene expression from routine H&E whole-slide images by conditioning a pretrained single-cell transcriptomic foundation-model prior on local histological neighbourhoods. A lightweight morphology-to-transcriptome adapter maps cached whole-slide histology features into a transcriptomic decoder, enabling prediction at measured locations, dense full-section reconstruction, and re-aggregation to the original measurement support. Across harmonized prostate cancer benchmarks, Morpho-FM achieved the strongest overall performance among five representative methods, reaching mean per-gene Pearson correlations of 0.286 in rotating single-slide evaluation and 0.298 in multi-slide held-out validation. The framework reproduced this advantage across kidney cancer sections, achieved a mean correlation of 0.210 across 56 directed single-slide evaluations and retained measurable predictive signal after external transfer to clear-cell renal cell carcinoma sections. Controlled ablation analyses identified pretrained transcriptomic initialization as a reproducible source of performance gain exceeding that attributable to changes in the histology feature backbone. Beyond predictive accuracy benchmarks, Morpho-FM recovered ERBB2-enriched tumour compartments, boundary-associated molecular gradients, and annotation-aligned tissue domains across Xenium and HER2ST breast cancer datasets. Together, these results support transcriptomic foundation-model priors as an effective constraint for morphology-conditioned molecular decoding and demonstrate the potential of Morpho-FM to extend spatial transcriptomic insight across routine pathology sections.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义

- **研究动机**：常规H&E染色组织切片虽然能捕获组织形态结构，但缺乏直接的空间分子信息；空间转录组技术能提供分子背景，但成本高、工作流程复杂、采样稀疏，限制了常规应用。
- **核心问题**：如何从廉价的常规H&E全切片图像映射出高分辨率的空间基因表达图谱，从而将空间转录组洞察扩展到大规模临床病理切片？
- **整体含义**：Morpho-FM利用预训练的单细胞转录组基础模型作为先验，约束形态条件化的分子解码，实现了从稀疏测量到密集组织图谱的外推，有望降低空间转录组学的应用门槛。

## 2. 论文提出的方法论

- **核心思想**：弱监督框架，将预训练单细胞转录组基础模型（先验）条件化于局部组织学邻域，通过轻量级适配器将H&E全切片图像特征映射到转录组解码器，从而在测量位置预测基因表达，并实现全切片重建。
- **关键技术细节**：
  - 使用预先训练的组织学特征骨干（如ResNet、ViT等）缓存全切片图像特征。
  - 设计一个轻量级“形态-转录组适配器”（morphology-to-transcriptome adapter），将缓存的特征映射到转录组解码器。
  - 转录组解码器初始化自预训练的单细胞转录组基础模型（如scGPT等），在训练时微调或保持冻结。
  - 训练方式：弱监督，只在有空间转录组测量点的位置上进行监督，模型可预测任意位置，实现全切片重建，并可重新聚合到原始测量支持。
- **无具体公式或算法流程的详细伪代码，但文字描述了端到端流程**。

## 3. 实验设计

- **数据集/场景**：
  - 前列腺癌（统一基准，包含多个切片）。
  - 肾癌（包括透明细胞肾细胞癌ccRCC切片，以及跨外部数据集迁移）。
  - HER2ST乳腺癌数据集（用于恢复ERBB2富集肿瘤区室、分子梯度）。
  - Xenium乳腺癌数据集（用于揭示组织域）。
- **Benchmark**：统一的前列腺癌基准，包含旋转单切片评估和多切片留出验证。
- **对比方法**：五种代表性方法（具体名称未在摘要中列出，但文中提到“五种代表性方法”），覆盖组织学-表达预测的现有主流方法。
- **评估指标**：主要使用每基因的皮尔逊相关系数（Pearson correlation）；此外，还有组织域恢复、分子梯度检测等定性/定量分析。

## 4. 资源与算力

- **文中未明确说明**使用了多少GPU型号、数量、训练时长等具体算力信息。仅在摘要中提及“轻量级适配器”和“缓存整张切片特征”，暗示计算效率较高，但无量化数据。

## 5. 实验数量与充分性

- **实验数量**：涉及前列腺癌、肾癌、乳腺癌多个数据集，包含旋转单切片评估（每切片留一）、多切片留出验证、跨数据集迁移、消融分析、组织域恢复等。
- **充分性与公平性**：
  - 在前列腺癌基准上对比了五种代表性方法，结果客观。
  - 消融分析专门验证了预训练转录组初始化带来的增益，且增益超过改变组织学特征骨干带来的收益，设计合理。
  - 在肾癌上复制优势，并在外部迁移场景中仍有可测量信号，增加了泛化证据。
  - 不足之处：缺乏在更大规模、更多癌种（如肺癌、结直肠癌等）上的验证；对比方法的选取是否完全覆盖最新方法也未可知（但至少在基准测试中领先）。

## 6. 论文的主要结论与发现

- Morpho-FM在多个数据集上取得领先性能：前列腺癌平均Pearson r=0.286（旋转单切片）和0.298（多切片留出验证），肾癌平均r=0.210。
- 预训练转录组基础模型先验是可重复的性能增益来源，且增益超过单纯改进组织学特征骨干。
- 在乳腺癌数据集中，Morpho-FM成功恢复了ERBB2富集肿瘤区室、边界相关分子梯度、以及注释对齐的组织域。
- 结论：转录组基础模型先验可作为形态条件化分子解码的有效约束，Morpho-FM有潜力将空间转录组洞察扩展到常规临床病理切片。

## 7. 优点

- **方法创新**：首次将预训练单细胞转录组基础模型作为先验引入H&E到基因表达的预测，利用了大量单细胞数据的知识，克服小样本配对的限制。
- **框架灵活**：弱监督设计，可处理任意稀疏测量，实现全切片密集重建。
- **实验全面**：多个癌种、多种评估协议、消融研究、跨数据集迁移、组织学特征骨干对比等。
- **性能显著**：在统一基准上超越五种代表性方法，且泛化性良好。

## 8. 不足与局限

- **实验覆盖**：集中在泌尿系统（前列腺癌、肾癌）和乳腺癌，缺乏其他常见癌症（如肺癌、结直肠癌、黑素瘤等）的验证。
- **偏差风险**：使用预训练单细胞基础模型时，不同模型的选择可能会影响结果，但未进行多个转录组先验的对比（仅与无先验的消融对比）。
- **应用限制**：目前仅基于H&E图像，未整合其他多模态数据（如病理报告、基因组突变等）；需要配对的H&E和空间转录组数据用于训练，对于无配对数据的部署场景仍需外推验证。
- **资源信息缺失**：未提供计算资源细节，不易复现或评估计算成本。
- **评估指标单一**：主要使用Pearson相关系数，可能无法完全反映生物意义（如差异基因表达、通路激活的恢复效果），虽补充了组织域恢复，但定量指标可以更丰富。

（完）
