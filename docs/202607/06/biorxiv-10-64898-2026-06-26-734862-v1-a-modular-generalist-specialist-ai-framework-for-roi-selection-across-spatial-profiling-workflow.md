---
title: A modular generalist-specialist AI framework for ROI selection across spatial profiling workflow
title_zh: 一种面向空间分析工作流程中ROI选择的模块化通才-专才AI框架
authors: "Castillo, S. P., Gautam, T., Pinao Gonzales, K. B., Salvatierra, M. E., Serrano, A., Ercan, C., Rodriguez, B. L., Acosta, P., Chen, P., Shokrollahi, Y., Lau, A., Kwong, L. N., Huse, J. T., Pan, X., Patient Mosaic Team,, Solis Soto, L. M., Yuan, Y."
date: 2026-07-01
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.26.734862v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 基于蛋白参考图谱的模块化AI框架用于空间谱学ROI选择
tldr: 空间分子分析中ROI选择依赖手动，重复性差。本文提出模块化通用-专业AI框架ASTROS，基于55种肿瘤类型160个样本构建蛋白图谱，测试通用、专业及混合策略，证明混合策略在信号保留、病理一致性、放置一致性和计算效率上最优，并支持虚拟染色与其他空间组学，显著减少评估者间变异，提升通用性。
source: biorxiv
selection_source: fresh_fetch
motivation: 手动ROI选择导致评估者间变异和低可重复性，亟需自适应AI框架以提升空间分子分析的解释性和再现性。
method: 基于NanoString DSP和免疫荧光数据构建蛋白参考图谱，开发ASTROS模型，结合通用基础模型与专业模型的混合策略进行ROI选择。
result: 混合策略在信号保留、病理参考一致性、放置稳定性和计算效率上优于单一策略，且适用于Visium/Visium HD等平台。
conclusion: 该框架通过模块化设计实现了可重复、自适应的ROI选择，降低了人为变异，增强了空间实验的通用性。
---

## 摘要
兴趣区域（ROI）的选择通常是空间分子分析和许多病理学任务中的关键步骤，对研究的可重复性和生物学可解释性具有重要影响。为了提供一个可重复且自适应的AI引导ROI选择框架，我们开发了一种跨空间分析平台的模块化通才-专才解决方案。在一项包含来自160个组织供体的55种肿瘤类型（使用NanoString数字空间分析和多重免疫荧光进行分析）的队列中，我们首先建立了一个蛋白质分析参考图谱，捕捉了区室特异性的免疫、检查点、基质和增殖模式。然后，我们开发了一个用于ROI选择的AI专才任务导向模型（ASTROS），并测试了考虑仅专才（ASTROS）、仅通才（PLIP/GFM）以及混合通才-专才策略的全面基准测试，结果表明后者在切片级信号保留、病理学家参考一致性、切片内放置一致性和大切片计算效率之间提供了平衡的权衡。我们进一步展示了虚拟染色用于ROI预览以及针对其他空间组学技术（Visium和Visium HD工作流程）的模块化ROI放置的可行性。总之，这些结果支持了我们提出的框架，以实现ROI选择，满足减少空间分析实验中评估者间变异、提高可重复性和多功能性的未满足需求。

## Abstract
Selection of regions of interest (ROIs) is often a crucial step in spatial molecular profiling and many pathology tasks, with substantial implications for research reproducibility and biological interpretability. To provide a reproducible and adaptive framework for AI-guided ROI selection, we developed a modular generalist-specialist solution across spatial profiling platforms. In a cohort comprising 55 tumor types from 160 tissue donors profiled using NanoString Digital Spatial Profiling and multiplex immunofluorescence, we first established a protein-profiling reference atlas capturing compartment-specific immune, checkpoint, stromal, and proliferation patterns. We then developed an AI Specialist Task-Oriented Model for ROI Selection (ASTROS) and tested comprehensive benchmarks considering specialist-only (ASTROS), generalist-only (PLIP/GFM), and hybrid generalist-specialist strategies, showing that the latter provides a balanced tradeoff across slide-level signal preservation, pathologist-reference concordance, within-slide placement consistency, and large-slide computational efficiency. We further demonstrated the feasibility of virtual staining for ROI preview and modular ROI placement for other spatial omics technologies, Visium and Visium HD workflows. Together, these results support our proposed framework to enable ROI selection responding to unmet needs for reducing inter-rater variability, reproducibility, and versatility in spatial profiling experiments.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：在空间分子分析（如NanoString GeoMx DSP、10x Visium）中，兴趣区域（ROI）的选择是决定下游分析可重复性和生物学可解释性的关键步骤。然而，传统手动ROI选择严重依赖专家经验，导致评估者间变异大、难以规模化，且无法适应不同平台和项目需求。
- **整体含义**：现有AI方法多为单一任务专用模型（专才）或通用基础模型（通才），缺乏可灵活组合的模块化框架。本文提出一个**模块化的通才-专才混合AI框架**，旨在实现可重复、自适应、跨平台的高质量ROI自动选择，从而减少人为偏差，提升空间分析实验的科学性和效率。

---

### 2. 论文提出的方法论：核心思想、关键技术细节、算法流程
- **核心思想**：将通用基础模型（GFM）的广泛上下文理解能力与专才任务导向模型（STM）的精准定位能力相结合，通过可调权重动态融合二者打分，实现ROI选择的代表性和准确性。
- **关键技术细节**：
  - **GFM**：使用PLIP（一种基于视觉-语言对比学习的病理学基础模型）提取组织图像的嵌入特征，通过余弦相似度衡量候选网格与专家参考集之间的形态相似性。
  - **专才模型ASTROS**：基于YOLOv8目标检测架构，在手动标注的ROI上进行微调，输出每个网格内肿瘤免疫共定位区域的置信度。
  - **自适应评分公式**：  
    \( \alpha = \frac{CV_{GFM}}{CV_{GFM} + CV_{AST}}, \quad S_{adaptive} = \alpha \cdot S_{GFM} + (1-\alpha) \cdot S_{AST} \)  
    其中 \(CV\) 为当前全切片图像中相应得分分布的变异系数，根据得分相对区分度自动分配权重。
  - **虚拟染色模块**：利用Pix2Pix条件生成对抗网络，将H&E图像转换为虚拟mIF图像，从而在仅需H&E的情况下预览ROI。
- **算法流程**（以mIF为例，三阶段粗到细）：
  1. **自动免疫评分**：对mIF全切片图像进行像素级CD45密度计算，按免疫细胞比例将网格分为低、中、高三类。
  2. **GFM引导的网格选择**：基于与专家参考集的余弦相似度，结合ASTROS置信度，按自适应分数排名选择代表性子集。
  3. **ASTROS定位**：在选中的网格内运行ASTROS，提取置信度最高的边界框作为最终ROI，大小与手动ROI一致（1649×1961像素）。

---

### 3. 实验设计：数据集、Benchmark、对比方法
- **数据集**：
  - **DSP队列**：包含160例组织供体、55种肿瘤类型（分为癌、黑色素瘤、肉瘤、其他），共1116个手动ROI，每个ROI有对应的mIF图像和DSP蛋白质组学计数。
  - **Visium队列**：70例H&E切片，包括胶质母细胞瘤、胆管癌、肺腺癌、上尿路上皮癌，对应10x Visium/Visium HD平台。
- **Benchmark**：
  - 对于DSP，将AI方法的结果与手动ROI（金标准）和全切片网格参考进行比较。
  - 对于Visium，与病理学家标注的ROI比较（Dice、IoU）。
- **对比方法（四个AI臂）**：
  - **仅GFM（GFM-only）**：只用PLIP余弦相似度选择网格，并在网格中心截取ROI。
  - **仅ASTROS（ASTROS-only）**：对所有网格运行ASTROS，按最高置信度排序选ROI。
  - **混合v1（Hybrid.v1）**：GFM选择网格后，ASTROS在选中的网格内定位ROI，固定权重。
  - **混合v2（Hybrid.v2）**：自适应融合GFM和ASTROS得分的动态混合策略（主要方法）。
- **其他实验**：
  - Visium平台上的**三个场景**：①仅GFM（训练逻辑回归预测ROI概率）；②仅STM（TMESegformer最大化肿瘤/坏死比）；③人-AI协作（病理学家标注肿瘤床，STM+GMF精调）。
  - **虚拟染色实验**：在DSP队列中，用H&E重染后的切片与mIF对齐，训练Pix2Pix，再对虚拟mIF应用Hybrid.v2。

---

### 4. 资源与算力
- **文中未明确说明使用的GPU型号、数量及训练总时长**。仅提及：
  - ASTROS训练：输入分辨率1280像素，批次大小64，学习率0.01，动量0.937，权重衰减0.0005，最多1000个epoch，早停patience=200。
  - Pix2Pix训练：输入256×256，使用Adam优化器（lr=0.0002，β₁=0.5），训练1000个epoch。
- 由于缺乏硬件配置细节，无法评估算力消耗的具体水平。建议后续补充此类信息以提升可复现性。

---

### 5. 实验数量与充分性
- **实验数量**：丰富且系统。
  - DSP队列上4个AI臂×7种性能指标（Pearson r、MAE、IoU一致性、计算时间等）全面比较。
  - 样本量敏感性分析：within-slide不同ROI数量下的标准差衰减；cohort级bootstrap（5000次迭代，N从5到1036）。
  - 虚拟染色评估：核对齐精度（Dice、MS-SSIM）、合成图像质量、ROI免疫得分相关性。
  - Visium三个场景的回顾性和前瞻性验证。
- **充分性与公平性**：
  - 消融实验完整，分别拆解了GFM、STM、混合各组件的作用。
  - 实验设计采用了分层比较、统计检验（Wilcoxon、Kruskal-Wallis、Dunn校正等），结论具有统计学支持。
  - 但部分肿瘤亚型样本量较少（如“其他”类仅10例），可能影响泛化性。总体而言，实验设计客观、公平，结论可信。

---

### 6. 论文的主要结论与发现
- **混合通才-专才策略（Hybrid.v2）在多个维度达到最佳平衡**：
  - 与手动ROI的免疫评分相关性最高（r=0.624）；全切片代表性MAE最低（6.09%）；切片内放置一致性最高（IoU变异系数=1.424）。
  - 计算效率在大尺寸全切片上最优（每tile缩放斜率仅0.64秒，远低于其他方法）。
- **ASTROS模型表现突出**：平均精确率0.969，召回率0.989，mAP₀.₅₋₀.₉₅=0.907。
- **虚拟染色可行**：从H&E生成的虚拟mIF上进行ROI选择，其免疫评分与真实mIF显著相关（partial Spearman r=0.587），可作为低成本预筛选方案。
- **框架可跨平台适应**：在Visium/Visium HD上通过调整GFM/STM组合及人机协作，成功生成符合病理需求的ROI，并完成前瞻性应用。
- **手动ROI构成的有监督参考图谱有效**：能捕捉不同肿瘤类型间免疫调节异质性，为AI训练提供了可靠标签。

---

### 7. 优点：方法或实验设计上的亮点
- **模块化设计**：GFM、STM、人机协作均可灵活组合，适应不同平台和研究目标，不局限于单一模型。
- **自适应评分机制**：根据切片内得分分布特征自动调整GFM和STM的权重，避免手动调参，增强泛化能力。
- **系统对比**：通过四个AI臂的完整消融，清晰揭示了混合策略相对于单一模型的优势边界。
- **虚拟染色预览**：创新地将生成式AI用于ROI预选，降低实验成本，提升工作流效率。
- **跨平台验证**：同时验证了DSP（蛋白质组学）和Visium（转录组学）两大主流平台，展示了框架的通用性。
- **样本量敏感性分析**：严谨地从切片内和队列层次评估ROI数量对估计精度的影响，为实验设计提供参考。

---

### 8. 不足与局限：包括实验覆盖、偏差风险、应用限制
- **复杂组织形态适应性有限**：如高分化脂肪肉瘤等脂肪丰富肿瘤，其形态与常规肿瘤差异大，可能导致GFM或虚拟染色性能下降。
- **虚拟染色精度依赖配准质量**：H&E与mIF的细胞级对齐困难，且Pix2Pix生成的虚拟mIF在肉瘤等组织上平均Dice仅0.474~0.507，可能引入选择偏差。
- **样本量不均衡**：DSP队列中“其他”类别仅10例（6.2%），肉瘤67例（41.9%），不同类别的统计效力不一致。
- **未能直接评估ROI数量对下游分子生物学结论的影响**：由于实验成本，无法在真实实验中测试不同ROI数量对蛋白质组/转录组结果的影响，仅在仿真中分析了免疫评分估计精度。
- **缺少算力资源详细描述**：未报告GPU型号、数量和总训练时间，影响可复现性和资源需求评估。
- **前瞻性应用规模小**：仅4例胆管癌用于Visium HD，属于概念验证，需更大规模临床验证。
- **依赖高质量手动标注**：ASTROS训练需大量医生标注，虽然引入了多个病理学家以减少偏差，但标注仍然昂贵且耗时。

（完）
