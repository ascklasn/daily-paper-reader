---
title: Spatial Metabolomics by Desthiobiotin Ligase (DESTNI) in Live Cells
title_zh: 活细胞中利用脱硫生物素连接酶（DESTNI）的空间代谢组学
authors: "Yoo, C.-M., Jo, J.-Y., Choi, C.-R., Park, Y. S., Cha, Y. J., Jung, S., Kang, J., Kim, J., Kang, Y. P., Yoo, T. H., Kim, J.-S., Rhee, H.-W."
date: 2026-07-06
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.05.736296v1.full.pdf"
tags: ["query:spatialprot"]
score: 8.0
evidence: 将邻近标记空间蛋白质组学技术扩展到代谢物的空间分析
tldr: 传统空间蛋白质组学通过邻近标记技术解析活细胞中蛋白质环境，但难以扩展至小分子代谢物。本文基于定向进化改造TurboID，获得高效依赖脱硫生物素的连接酶DESTNI，结合合成标准品、体外筛选与机器学习预测，实现对含胺代谢物的亚细胞区室特异性标记。在线粒体和细胞核中分别富集特征代谢物。该工作搭建了空间蛋白质组学与代谢组学的桥梁，为活细胞亚细胞代谢图谱绘制提供了通用策略。
source: biorxiv
selection_source: carryover_cache
motivation: 现有邻近标记技术局限于蛋白质，缺乏活细胞中空间分辨的小分子代谢物标记方法。
method: 通过酵母展示系统定向进化TurboID获得DESTNI，结合DTB修饰标准品、体外反应与机器学习预测。
result: DESTNI实现线粒体富集甘氨酸等、细胞核富集γ-氨基丁酸等特征代谢物标记。
conclusion: DESTNI作为邻近标记平台，桥接空间蛋白质组学与代谢组学，可解析活细胞亚细胞生化环境。
---

## 摘要
邻近标记通过实现活细胞中蛋白质环境的区室分辨作图，已经改变了空间蛋白质组学，但其扩展到小分子代谢物尚未被证明，可能是由于标记化学和标记代谢物鉴定的局限性。在这里，我们引入了DESTNI，一种通过定向进化从TurboID改造而来的脱硫生物素（DTB）连接酶，并建立了一个用于含胺代谢物空间分辨分析的平台。基于酵母展示系统的定向进化策略产生了具有高效DTB依赖性反应性的DESTNI，能够在不同的亚细胞环境中实现稳健且区室特异性的邻近标记。为了鉴定DTB修饰的氨基代谢组，我们开发了一个集成的分析框架，结合了DTB修饰的氨基代谢物标准品、体外DESTNI分析和计算机MS/MS预测，从而能够系统地注释DTB修饰的氨基代谢物。为了将这种化学扩展到代谢物，我们结合了合成的DTB结合代谢物参考标准品、体外DESTNI反应性代谢物发现以及DTB衍生代谢物和寡肽的机器学习预测。靶向细胞器的DESTNI恢复了可重复的区室富集的氨基代谢物特征，包括线粒体基质富集的甘氨酸、5-氨基乙酰丙酸、鸟氨酸和亚精胺加合物，以及细胞核富集的γ-氨基丁酸和5-氨基戊酸加合物。总之，这项工作确立了DESTNI作为一个邻近标记平台，连接了空间蛋白质组学和代谢组学，并为绘制活细胞中的亚细胞生化环境提供了通用策略。

## Abstract
Proximity labeling has transformed spatial proteomics by enabling compartment-resolved mapping of protein environments in living cells, yet its extension to small-molecule metabolites has not been demonstrated, probably due to limitations in labeling chemistry and identification of labeled metabolites. Here, we introduce DESTNI, an engineered desthiobiotin (DTB) ligase derived from TurboID through directed evolution, and establish a platform for spatially resolved profiling of amine-containing metabolites. A directed evolution strategy based on a yeast display system yielded DESTNI with an efficient DTB-dependent reactivity, enabling robust and compartment-specific proximity labeling across diverse subcellular environments. To identify the DTB-modified amino metabolome, we developed an integrated analytical framework combining DTB-modified amino metabolite standards, in vitro DESTNI profiling, and in silico MS/MS prediction, enabling systematic annotation of DTB-modified amino metabolites. To extend this chemistry to metabolites, we combined synthetic DTB-conjugated metabolite reference standards, in vitro DESTNI-reactive metabolite discovery, and machine-learning prediction of DTB-derivatized metabolites and oligopeptides. Organelle-targeted DESTNI recovered reproducible compartment-enriched amino metabolite signatures, including mitochondrial matrix-enriched glycine, 5-aminolevulinic acid, ornithine and spermidine adducts, as well as nuclear-enriched {gamma}-aminobutyric acid and 5-aminovaleric acid adducts. Together, this work establishes DESTNI as a proximity labeling platform that bridges spatial proteomics and metabolomics and provides a general strategy for mapping subcellular biochemical environments in living cells.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：传统邻近标记技术（如TurboID）已广泛应用于空间蛋白质组学，但无法有效扩展到小分子代谢物。原因包括：① 生物素修饰的代谢物从链霉亲和素中回收效率低；② 外源生物素补充可能导致代谢或发育干扰；③ 内源性生物素化信号与酶标记信号在质谱上无法区分，干扰代谢物鉴定。
- **整体含义**：亟需一种能够在不破坏细胞结构的前提下，在活细胞中对特定亚细胞区域的含胺代谢物进行空间分辨标记的方法。该工作试图将邻近标记从蛋白质拓展到代谢物，建立空间蛋白质组学与代谢组学之间的桥梁。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：使用脱硫生物素（DTB）替代生物素作为底物，通过定向进化改造TurboID获得高效利用DTB的酶（DESTNI），并构建DTB修饰代谢物的混合光谱库（实验+预测），实现活细胞中亚细胞区室特异性含胺代谢物的标记与鉴定。
- **关键技术细节**：
  1. **酶工程**：基于酵母表面展示系统，对TurboID进行两阶段定向进化（第一阶段6轮FACS筛选，第二阶段4轮筛选），获得含11个氨基酸替换的DESTNI（V48L, A129V, R141L, I147T, I153L, M157V, Q180R, E215D, Q227R, I280V, K321E）。这些突变多位于腺苷酰化口袋的第二壳层，协同优化DTB结合与催化活性。
  2. **代谢物标记化学**：DESTNI催化DTB与ATP形成DTB-AMP活性中间体，该中间体与邻近含胺代谢物的伯胺或仲胺反应形成DTB-代谢物加合物。DTB标记具有高效链霉亲和素富集（KD ≈ 10⁻¹³ M）和温和洗脱的优势，并在MS/MS中产生特征诊断离子（m/z 197.128 和 179.117）。
  3. **混合光谱库构建**：
     - 实验参考库：DTB-NHS衍生667种候选代谢物标准品，经LC-MS/MS验证获得152个高置信度DTB修饰谱（对应136种化合物）。
     - 机器学习预测库：基于实验谱训练模型，预测HMDB v5中所有含伯胺/仲胺代谢物（20,251个）及寡肽（9,220个）的DTB修饰谱，总计29,471个预测谱。
  4. **分析流程**：活细胞中DESTNI定点表达→DTB孵育→甲醇提取代谢物→链霉亲和素磁珠富集→酸洗脱→毛细管LC-MS/MS分析（阶梯HCD碰撞能量）→诊断离子过滤→谱库匹配→定量分析。

## 3. 实验设计：使用的数据集/场景、benchmark、对比方法

- **数据集与场景**：
  1. **酶工程验证**：酵母表面展示系统（~10⁷突变体库），FACS筛选；HEK293T细胞中验证（蛋白水平免疫印迹、免疫荧光）。
  2. **空间蛋白质组学验证**：将DESTNI靶向线粒体基质（MTS）、外膜（TOM20）、胞质（NES）、细胞核（NLS）等8种细胞器，在HEK293T细胞中标记15 min，富集DTB修饰肽段进行LC-MS/MS分析（n=3）。
  3. **代谢物检测验证**：体外纯化DESTNI反应（HEK293T代谢提取物），三元重复；活细胞空间代谢组学（稳定表达MTS-DESTNI、DESTNI-NES、DESTNI-NLS的HEK293T-REx细胞），标记3 h（n=6 per group）。
- **Benchmark**：无明确标准benchmark数据集。对照包括：无酶对照、无探针（无DTB）对照、TurboID对比（图1c,d中显示DESTNI活性远高于TurboID及中间突变体）。
- **对比方法**：
  - 与TurboID直接对比DTB利用效率（图1c,d）。
  - 与TurboID (E215D, Q227R) 中间体对比。
  - 与生物素标记代谢物的链霉亲和素回收效率对比（补充图4）。
  - 在机器预测方面，与实验标准谱进行余弦相似度验证（如DTB-三甘肽，cosine=0.986）。

## 4. 资源与算力

- 论文未明确说明使用的GPU型号、数量及训练时长。在机器学习谱预测部分，模型训练基于152个实验谱，但未提供具体计算资源信息。LC-MS/MS分析使用Orbitrap Lumos质谱仪，但未提及集群或硬件规格。

## 5. 实验数量与充分性

- **主要实验组数**：
  - 酵母定向进化：10轮FACS筛选（6+4）。
  - 蛋白标记验证：8种细胞器靶向（图2a,b），每组至少2-3次重复。
  - 空间蛋白质组学：4种靶向（MTS, TOM20, NES, NLS），3次生物学重复。
  - 体外代谢物标记：3次重复（图3h）。
  - 活细胞空间代谢组学：3种靶向（MTS, NES, NLS），6次生物学重复（图4）。
  - 标准品衍生：667化合物，152个高置信度谱。
- **充分性评估**：
  - **充分**：蛋白质组学实验包括多种细胞器对照，统计分析显示分区清晰（PCA、层次聚类、Pearson相关性）。代谢物实验有充分的生物学重复（n=6），对照（无酶、无探针）设计合理。
  - **客观与公平**：比较对象（TurboID）为公认基准，统计方法（Welch t检验、Benjamini-Hochberg校正）适当。但缺少与其他空间代谢组学方法（如MALDI成像、IMS）的直接比较。
  - **不足**：仅使用HEK293T细胞系，未在多种细胞类型或组织中进行验证；仅检测含胺代谢物，覆盖类型有限；注释率仅9.6%（146/1520），大量特征未鉴定。

## 6. 论文的主要结论与发现

1. 成功工程化获得DESTNI，一种高效利用DTB的邻近标记酶，在活细胞中可实现比TurboID更强的DTB依赖性标记。
2. DESTNI标记在蛋白质层面保持亚细胞区室特异性（图2d-f），证实其空间精确性。
3. 构建了首个DTB修饰氨基代谢物的混合光谱库（实验+预测），覆盖超过28,000个独特结构。
4. 活细胞空间代谢组学揭示了区室富集的代谢物特征：
   - 线粒体基质：甘氨酸、5-氨基乙酰丙酸、鸟氨酸、亚精胺（di-DTB-亚精胺）、牛磺酸等，与已知线粒体代谢通路一致。
   - 细胞核：γ-氨基丁酸（GABA）、5-氨基戊酸、N²-甲基赖氨酸、肌肽等，提示这些代谢物在细胞核中的非经典功能。
5. DESTNI可同时检测空间蛋白质与空间代谢物，统一了蛋白质组学和代谢组学的邻近标记平台。

## 7. 优点：方法或实验设计上的亮点

1. **创新性**：首次将邻近标记从蛋白质拓展至小分子代谢物，填补了空间代谢组学在活细胞中的技术空白。
2. **酶工程策略**：采用酵母表面展示定向进化，结合TSA信号放大逐步提高筛选压力，成功将DESTNI的DTB活性提升至远高于亲本TurboID。
3. **DTB标签的多功能设计**：DTB既作为酶底物、又作为富集手柄，同时还是MS/MS特征诊断离子来源，整个工作流无需额外点击化学，操作简便。
4. **混合光谱库构建**：将实验标准品谱与机器学习预测谱相结合，显著扩展了可鉴定的代谢物范围，为后续研究提供了可扩展的资源。
5. **严格的对照设计**：包含无酶、无探针、多种细胞器靶向对照，且蛋白质和代谢物两个层面均验证了空间特异性。
6. **生物学验证**：检测到的区室富集代谢物（如线粒体甘氨酸、5-氨基乙酰丙酸）与已知代谢通路吻合，证明了方法的可靠性；同时也发现意外富集的分子（如线粒体天冬酰胺、细胞核GABA），提出了新的生物学假说。

## 8. 不足与局限：包括实验覆盖、偏差风险、应用限制

1. **化学覆盖有限**：仅针对含伯胺或仲胺的代谢物，无法标记缺乏合适亲核基团的代谢物类别（如脂质、糖类、核酸等）。
2. **注释率低**：仅有9.6%的富集特征（146/1520）获得鉴定，绝大多数特征为“暗代谢组”，限制了全局覆盖。
3. **细胞类型单一**：所有活细胞实验均基于HEK293T-REx细胞株，未在原代细胞、组织或动物模型中验证，可能影响通用性。
4. **DTB浓度和时间**：活细胞中3小时、500 μM DTB孵育可能干扰内源代谢，尽管有对照，但长期效应的评估不足。
5. **空间分辨率限制**：邻近标记基于酶活性半径扩散，无法达到单细胞或亚区室（如核仁）级别分辨率。线粒体基质与外膜靶向的对比虽有用，但内共区域（如嵴）未区分。
6. **缺少直接基准比较**：未与主流空间代谢组学方法（如MALDI-IMS、荧光代谢物成像、同位素标记）进行系统比较，难以评估其相对优势与劣势。
7. **机器学习模型训练数据量小**：仅152个实验谱用于训练，可能限制预测谱的准确性，尤其是对于结构复杂或稀有的代谢物。
8. **计算资源未披露**：缺乏对ML训练时间、推理速度等的信息，影响方法复现性评估。

（完）
