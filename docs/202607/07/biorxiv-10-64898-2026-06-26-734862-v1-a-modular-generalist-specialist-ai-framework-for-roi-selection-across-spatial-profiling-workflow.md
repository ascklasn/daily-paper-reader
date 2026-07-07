---
title: A modular generalist-specialist AI framework for ROI selection across spatial profiling workflow
title_zh: 一种用于空间分析工作流程中ROI选择的模块化通才-专才AI框架
authors: "Castillo, S. P., Gautam, T., Pinao Gonzales, K. B., Salvatierra, M. E., Serrano, A., Ercan, C., Rodriguez, B. L., Acosta, P., Chen, P., Shokrollahi, Y., Lau, A., Kwong, L. N., Huse, J. T., Pan, X., Patient Mosaic Team,, Solis Soto, L. M., Yuan, Y."
date: 2026-07-01
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.26.734862v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 空间分子分析中AI选择感兴趣区域的框架
tldr: 空间分子谱分析中ROI选择至关重要但存在可重复性差等问题。本研究提出模块化通用-专用AI框架ASTROS，结合蛋白质参考图谱和专用模型。在55种肿瘤类型中，混合通用-专用策略在信号保留、病理一致性、放置一致性和计算效率上取得最佳平衡。该框架支持虚拟染色预览和跨平台模块化部署，提升了空间实验的再现性与通用性。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有ROI选择缺乏可重复性和自适应框架，导致空间谱分析结果易受主观差异影响。
method: 构建多肿瘤蛋白质参考图谱，开发专用模型ASTROS，并与通用模型PLIP/GFM组合成混合策略进行对比测试。
result: 混合通用-专用策略在多项指标上优于仅用专用或通用模型，并能适配NanoString、Visium等多种平台。
conclusion: 该模块化框架为空间分子谱分析提供了可重复、灵活且高效的ROI选择方案。
---

## 摘要
感兴趣区域（ROI）的选择通常是空间分子分析和许多病理学任务中的关键步骤，对研究的可重复性和生物学可解释性具有重要影响。为了提供一个可重复且自适应的AI引导ROI选择框架，我们开发了一种跨越空间分析平台的模块化通才-专才解决方案。在一个包含来自160个组织供体的55种肿瘤类型（使用NanoString数字空间分析和多重免疫荧光分析）的队列中，我们首先建立了一个蛋白质分析参考图谱，捕捉了区室特异性的免疫、检查点、基质和增殖模式。然后，我们开发了一个AI专才任务导向模型（ASTROS），并测试了包括仅专才（ASTROS）、仅通才（PLIP/GFM）和混合通才-专才策略的全面基准测试，表明后者在切片级信号保留、病理学家参考一致性、切片内放置一致性和大切片计算效率之间提供了平衡的权衡。我们进一步展示了虚拟染色用于ROI预览的可行性，以及用于其他空间组学技术（Visium和Visium HD工作流程）的模块化ROI放置。总之，这些结果支持了我们提出的框架，以实现ROI选择，满足减少空间分析实验中评分者间变异性、提高可重复性和通用性的未满足需求。

## Abstract
Selection of regions of interest (ROIs) is often a crucial step in spatial molecular profiling and many pathology tasks, with substantial implications for research reproducibility and biological interpretability. To provide a reproducible and adaptive framework for AI-guided ROI selection, we developed a modular generalist-specialist solution across spatial profiling platforms. In a cohort comprising 55 tumor types from 160 tissue donors profiled using NanoString Digital Spatial Profiling and multiplex immunofluorescence, we first established a protein-profiling reference atlas capturing compartment-specific immune, checkpoint, stromal, and proliferation patterns. We then developed an AI Specialist Task-Oriented Model for ROI Selection (ASTROS) and tested comprehensive benchmarks considering specialist-only (ASTROS), generalist-only (PLIP/GFM), and hybrid generalist-specialist strategies, showing that the latter provides a balanced tradeoff across slide-level signal preservation, pathologist-reference concordance, within-slide placement consistency, and large-slide computational efficiency. We further demonstrated the feasibility of virtual staining for ROI preview and modular ROI placement for other spatial omics technologies, Visium and Visium HD workflows. Together, these results support our proposed framework to enable ROI selection responding to unmet needs for reducing inter-rater variability, reproducibility, and versatility in spatial profiling experiments.

---

## 论文详细总结（自动生成）

# 论文结构化总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：空间分子分析（如NanoString GeoMx DSP、10x Visium）中，感兴趣区域（ROI）的选择高度依赖手动操作，存在**可重复性差、评分者间变异大、扩展性差**等瓶颈，直接影响下游生物学结论的可靠性。
- **背景**：现有自动ROI选择方法多采用单一模型（专用模型或通用基础模型），缺乏灵活性和跨平台适应性。通用基础模型（GFM）擅长上下文理解但缺乏任务特异性，专用任务模型（STM）精度高但泛化能力弱。
- **整体含义**：提出一种**模块化通才‑专才（Generalist‑Specialist）混合框架**，将GFM的特征提取与STM的精确定位协同，实现可重复、跨平台、可定制的ROI选择，对提高空间组学实验的科学严谨性和临床转化具有重要价值。

## 2. 论文提出的方法论
### 核心思想
- 构建一个三阶段“由粗到细”的工作流，将GFM（PLIP/UNI）与自定义专才模型ASTROS（基于YOLOv8）进行**自适应权重融合**，兼顾全局代表性（通才）和局部免疫模式识别（专才）。

### 关键技术细节
- **阶段一：自动免疫评分**  
  在多重免疫荧光（mIF）全切片图像上，基于像素级CD45表达计算每个网格（3000×3000像素）的自动免疫评分（aIS），并与两位病理学家的手动评分进行一致性验证。
- **阶段二：代表性网格选择**  
  - 将全切片网格按免疫类别（低/中/高）分层，保持WSI代表性比例。  
  - 使用GFM（PLIP）提取候选网格和参考网格集的嵌入，计算余弦相似度得分 \( S_{GFM} \)。  
  - 同时应用ASTROS获取专才置信度得分 \( S_{AST} \)。  
  - **自适应评分**：\( S_{adaptive} = \alpha \cdot S_{GFM} + (1-\alpha) \cdot S_{AST} \)，其中 \( \alpha = CV_{GFM} / (CV_{GFM}+CV_{AST}) \)，由当前WSI上两种分数的变异系数动态确定权重。
- **阶段三：ROI精确定位**  
  ASTROS在选中的网格内输出边界框（框中心提取 1649×1961 像素的最终ROI），模型训练基于606个手动标注ROI及额外222个由独立病理学家标注的ROI，使用5折交叉验证。

### 扩展模块
- **虚拟染色预览**：通过H&E重染mIF切片并配准，训练Pix2Pix模型合成虚拟mIF（vmIF），再应用同一Hybrid.v2流程进行ROI预选。
- **跨平台适配**：针对Visium/Visium HD，设计了三种场景（仅GFM、仅STM、人‑机协作），以UNI为GFM、TMESegformer为STM。

## 3. 实验设计
### 数据集
- **DSP队列**：160个组织供体，55种肿瘤类型，1116个手动ROI，配对的mIF全切片和DSP蛋白计数。肿瘤分为癌、黑色素瘤、肉瘤及其他。
- **Visium队列**：70例（4种肿瘤：胶质母细胞瘤GBM、胆管癌CCA、肺腺癌LUNG、上尿路上皮癌UTUC），用于H&E上的ROI选择。
- **虚拟染色测试**：使用DSP队列中重新染色并配准的H&E‑mIF配对（约168例）。

### 基准对比方法（四个AI臂）
- **Hybrid.v2**：自适应GFM+STM融合（全文主方法）。
- **Hybrid.v1**：仅用GFM相似度选网格，然后ASTROM选ROI。
- **GFM-only**：仅用PLIP余弦相似度，无ASTROS。
- **ASTROS-only**：仅用ASTROM置信度，无GFM。
- **参考臂**：手动ROI（金标准）和WSI网格普查（全组织免疫评分均数）。

### 评估指标
- 生物学指标：Pearson r、MAE（与手动ROI/WSI参考对比）、评分者间一致性（Cohen’s κ）、切片内一致性（IoU变异系数）。
- 计算指标：端到端运行时间、每瓦片缩放斜率、大切片效率。

### 实验数量与充分性
- **DSP队列消融实验**：4个AI臂 × 3个免疫类别 × n=1-6 ROI数，统计显著性通过Wilcoxon秩和检验、Kruskal‑Wallis检验、Bootstrap重采样（5000次）验证。
- **虚拟染色实验**：定量评估配准（Dice、MS‑SSIM）和合成质量，比较mIF与vmIF的ROI重叠和免疫得分。
- **Visium场景实验**：对GBM（N=27）、LUNG（N=9）、CCA（N=19+4）分别测试不同GFM/STM组合，并进行了**前瞻性验证**（4例CCA用于Visium HD）。
- **样本量敏感性分析**：从1到6个ROI以及全队列Bootstrap，展示了MAE和不确定性的幂律衰减。
- 整体实验设计覆盖了不同平台、不同肿瘤类型、不同模型组合，统计检验充分，但部分子集（如Visium场景）样本量较小。

## 4. 资源与算力
- 文中**未明确说明**使用的GPU型号、数量、训练机器的内存等具体硬件信息。
- 可推断的信息：
  - ASTROS (YOLOv8) 训练：batch size 64，输入分辨率1280，学习率0.01，momentum 0.937，weight decay 0.0005，最多1000 epoch，early stopping patience 200。
  - Pix2Pix虚拟染色训练：Adam优化器，lr=0.0002，β1=0.5，1000 epoch。
  - 使用PLIP和UNI作为预训练GFM，仅做推理（嵌入提取），未进行微调。
- 没有提供训练/推理总时间、GPU数量等，但提到了运行时分析（例如ASTROS-only vs Hybrid.v2在大型WSI上约1500秒）。

## 5. 实验的主要结论与发现
- **混合通才‑专才策略（Hybrid.v2）在多项指标上取得最佳平衡**：与WSI参考的Pearson r最高（0.857），与病理学家手动ROI的MAE最低，切片内一致性最好（IoU CV=1.424），计算效率领先（大切片每瓦片斜率0.64 s）。
- **自动化评分与病理学家高度一致**：mIF‑aIS与两位病理学家的Cohen’s κ分别达0.708和0.686，接近病理学家间的κ=0.672。
- **虚拟染色可行**：vmIF合成的MS‑SSIM中位0.644，Dice中位0.60；在两个平台上，Hybrid.v2选出的ROI免疫得分与真实mIF无显著差异（p>0.05）。
- **跨平台适应性**：在Visium/Visium HD上，三种场景（GFM、STM、人‑机协作）均能有效选择ROI，其中STM场景下肿瘤/坏死比例与手动ROI显著相关（r=0.98/0.86）。
- **可重复性与代表性**：Hybrid.v2选出的ROI免疫得分分布与WSI整体分布一致，且不受肿瘤类型显著影响。

## 6. 优点
- **模块化设计**：GFM和STM可灵活组合、替换，适应不同目标（免疫、肿瘤形态、坏死排除等）。
- **自适应权重**：根据当前WSI的变异系数动态调整GFM和STM的贡献，避免了固定权重的局限。
- **多平台验证**：覆盖NanoString DSP、10x Visium/Visium HD，并包含虚拟染色扩展。
- **可重复性定量**：系统衡量了与WSI参考的一致性、切片内稳定性，并提供了Bootstrap置信区间。
- **人‑机协作选项**：保留病理学家参与（粗标注），既提高信任度又降低劳动量。
- **高效计算**：混合策略可提前修剪无信息网格，在大切片上效率优于纯GFM或纯STM。

## 7. 不足与局限
- **样本量与分子结论有限**：DSP队列仅160个供体，且肿瘤类型分布不均衡（肉瘤占41.9%），限制了免疫蛋白组差异的泛化能力；部分子集（如Visium场景）样本量更小。
- **手动标注偏差引入**：ASTROS以病理学家标注为金标准训练，虽然采用了多位病理学家，但训练数据仍可能继承主观偏好。
- **复杂形态处理困难**：如高度分化的脂肪肉瘤等，其脂肪样结构会影响虚拟染色和模型转移；H&E‑mIF配准在低结构组织（如肉瘤）中表现较差（Dice中位仅0.474）。
- **虚拟染色精度有限**：约50%的vmIF‑ROI与真实mIF‑ROI重叠，且完全未重叠案例中可能错失真正免疫热点。
- **缺失真实的分子下游验证**：未将AI选择的ROI送入实际DSP/Visium流程并比较分子表达差异，潜在的风险是AI选择可能引入系统性偏差。
- **计算开销仍显著**：在大型WSI上，Hybrid.v2仍需约1535秒，依赖GFM嵌入提取（PLIP/UNI），对规模化应用可能构成瓶颈。
- **无GPU硬件细节**：论文未披露训练/推理的具体算力配置，降低了可复现性。

---

（完）
