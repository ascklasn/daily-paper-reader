---
title: "PIGMENT: A deep learning framework for Porcine Immunohistochemistry seGMENTation"
title_zh: PIGMENT：一个用于猪免疫组织化学分割的深度学习框架
authors: "Ambastha, P., Dadashkarimi, J., Annavazala, S. K. C., Parker, D., Diaz-Arrastia, R., Song, H., Smith, D. H., Dolle, J.-P., Johnson, V. E., Wolf, J. A., Verma, R."
date: 2026-06-23
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.18.733245v1.full.pdf"
tags: ["query:spatialprot"]
score: 8.0
evidence: 用于免疫组织化学分割的深度学习框架，属于空间病理学
tldr: 创伤性脑损伤后APP免疫组化标记轴突损伤，但量化依赖人工标注，耗时且可重复性差。本文提出PIGMENT框架，基于SegFormer-B0架构，利用525张专家标注瓦片和APP特定增强，实现自动化分割。在猪白质数据上平均实例检测率达0.86，且跨动物训练提升了性能。该方法可生成全切片APP负荷图，为组织学与影像对齐研究提供可扩展工具。
source: biorxiv
selection_source: fresh_fetch
motivation: APP阳性轴突病理量化是手动、耗时且可重复性低的瓶颈，亟需自动化方法。
method: 采用紧凑SegFormer-B0，结合有限标注与APP特定增强（强度、碎片、形态等）训练。
result: 在猪APP染色切片上平均实例检测率0.86，跨动物训练集效果最佳。
conclusion: PIGMENT生成全切片APP负荷图，支持组织学与神经影像对齐，扩展了轴突损伤研究规模。
---

## 摘要
创伤性脑损伤会产生广泛的轴突损伤，可通过淀粉样前体蛋白（APP）免疫组织化学进行组织学评估，该方法能在细胞分辨率下标记受损的轴突轮廓[1, 2]。然而，APP病理学的量化仍是主要瓶颈：标注是手动的、耗时的、空间局限的，且不同评估者之间存在差异，限制了可扩展性和可重复性。这一限制在将组织学作为神经影像学或其他组织层面测量参考的研究中尤为重要，因为细胞APP病理学必须以空间形式进行量化，以便与影像异常对齐。

在此，我们介绍PIGMENT，一个标注高效的深度学习框架，用于自动分割和量化猪白质组织学中的APP阳性病理。PIGMENT采用紧凑的SegFormer-B0架构，在来自三头猪的四个APP染色切片中，由专家标注的525个512×512像素图块上进行训练。由于APP阳性轮廓稀疏、碎片化、染色变异且形态多样，PIGMENT将有限的专家标签与APP特异性增强相结合，该增强旨在模拟APP阳性强度、大小、连续性、碎片化和局部组织背景的变化。

我们使用实例级检测率来评估PIGMENT，该指标衡量离散的APP阳性成分是否被定位。在保留的APP染色数据上，PIGMENT的平均实例级检测率达到0.86。在测试的配置中，包含来自不同动物切片的训练集取得了最高的平均检测率，这表明在有限标签条件下，标注多样性可能是一个重要因素。

通过将有限的、高置信度的专家标注扩展到全切片APP负担图，PIGMENT提供了一个可扩展的框架，用于表征创伤性轴突损伤的程度和空间分布。这些图谱可能支持未来将组织学损伤负担与影像衍生测量对齐的研究。

## Abstract
Traumatic brain injury produces widespread axonal damage can be assessed histologically using amyloid precursor protein (APP) immunohistochemistry, which labels injured axonal profiles at cellular resolution [1, 2]. However, quantification of APP pathology remains a major bottleneck: annotation is manual, time-consuming, spatially localized, and variable across raters, limiting scalability and reproducibility. This limitation is particularly important in studies that use histology as a reference for neuroimaging or other tissue-level measurements, where cellular APP pathology must be quantified in a spatial form that can be aligned with imaging abnormalities.

Here, we introduce PIGMENT, an annotation-efficient deep-learning framework for automated segmentation and quantification of APP-positive pathology in porcine white matter histology. PIGMENT uses a compact SegFormer-B0 architecture trained on 525 expert-annotated 512 x 512-pixel tiles from four APP-stained sections across three pigs. Because APP-positive profiles are sparse, fragmented, stain-variable, and morphologically diverse, PIGMENT combines limited expert labels with APP-specific augmentation designed to model variation in APP-positive intensity, size, continuity, fragmentation, and local tissue context.

We evaluated PIGMENT using an instance-level detection rate that measures whether discrete APP-positive components are localized. Across held-out APP-stained data, PIGMENT achieved a mean instance-level detection rate of 0.86. Across the configurations tested, the highest mean detection rate was achieved by a training set that included sections from different animals, suggesting that annotation diversity may be an important factor under limited-label conditions.

By extending limited high-confidence expert annotations into whole-section APP burden maps, PIGMENT provides a scalable framework for characterizing the extent and spatial distribution of traumatic axonal injury. These maps may support future studies that align histological injury burden with imaging-derived measures.

---

## 论文详细总结（自动生成）

好的，以下是根据您提供的论文内容生成的详细中文总结。

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：创伤性脑损伤（TBI）后的轴突损伤可通过免疫组化（APP）染色在细胞水平进行评估。然而，对APP阳性病理的量化分析严重依赖于人工标注，这是一个耗时、劳动密集且主观性强的过程，成为限制大规模研究和影像-组织学对照研究的“主要瓶颈”。特别是在将组织学作为神经影像学验证的“金标准”时，需要可扩展且可重复的细胞级病理量化方法。
- **研究动机**：开发一个自动化、可扩展、且鲁棒的深度学习框架，用于猪白质组织切片中APP阳性轴突病理的自动分割和量化。目标是生成全切片范围的APP损伤负荷图，以支持下游的解剖学和影像学分析，尤其是将组织学损伤与弥散MRI等影像学指标进行空间对齐。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：采用 **“标注高效”的深度学习方法**，在有限的专家标注数据上训练一个紧凑的模型。该方法不试图替代专家判断，而是利用专家在高置信度区域（小图块）的标注，来学习通用的特征，从而将其扩展到更大的组织区域。
- **关键技术细节**：
    - **模型架构**：采用 **SegFormer-B0**，一个轻量级的层级Transformer分割模型，参数约370万。使用ImageNet-1k预训练权重初始化。模型输入512x512像素的RGB图块，输出对应大小的二值概率图。
    - **训练策略**：
        - **损失函数**：像素级的 **Dice损失**，训练过程中排除图块边界（避免不完整结构带来的影响）和标签噪声区域的像素（利用EMA教师模型检测教师预测与手动标注的强不一致区域）。
        - **优化器**：AdamW，学习率1e-5，权重衰减0.01。
    - **数据增强（核心创新）**：设计了 **APP特异性增强管线**，分为五类，共同目标是在不破坏图像-掩码对应关系的前提下，模拟APP染色的真实变异：
        - **空间变换**：翻转、旋转、仿射变换、弹性变形。
        - **光度变换**：亮度、对比度、颜色抖动、高斯模糊、运动模糊、JPEG压缩等。
        - **复制-粘贴**：从同一图像中随机采样APP阳性组件，经过变换后粘贴到图中其他位置，增加阳性样本的多样性与密度。
        - **形态学连接**：附近端点间进行桥接，或沿局部方向延伸细长结构，模拟真实病理轮廓的连续性。
        - **组织级别变换**：模拟背景染色变异（如白质组织丢失），以及利用高斯混合模型（GMM）将颜色接近APP阳性区域的像素提升为假阳性前景，以增强模型辨伪能力。

### 3. 实验设计：数据集、Benchmark、对比方法

- **数据集**：
    - **开发与测试集**：来自3头猪的4张APP染色的白质切片（D1-D4）。猪P1贡献D1，P2贡献D2和D3，P3贡献D4。每张切片由专家在选定的矩形区域内标注APP阳性轮廓，然后从中提取512x512像素的图块（共525张）。
    - **数据划分**：每张切片的数据按大约80%训练、20%测试划分。
    - **独立验证样本**：一个来自不同损伤模型（控制性皮层撞击，CCI）的猪脑切片，仅用于定性评估（无专家全面标注）。

- **Benchmark（评估指标）**：
    - **主要指标**：**实例级检测率（Detection Rate, DR）**。对于一个标注的APP阳性连通域，只要预测的二值掩码有任何像素与之重叠，即视为被检测到。该指标更侧重于判断病灶“是否定位”，比像素重叠指标更具生物学意义。
    - **次要指标**：**Dice系数** 和 **交并比（IoU）**，为标准的像素级重叠指标。

- **对比方法**：
    - **UniverSeg**：一个通用医学图像分割的少样本方法，在测试时提供支持图像-掩码对。
    - **MicroSAM**：基于Segment Anything Model（SAM）的显微图像分割框架，零样本应用。
    - **消融实验**：对比 **全增强管线** 与 **仅直方图匹配（无空间增强）** 对性能的影响。

### 4. 资源与算力

- **明确提及**：单个模型在 **24GB GPU** 上训练 **不到2小时**。这表明方法计算需求不高。
- **未明确说明**：文中未提及使用的GPU型号（如V100, A4000等）以及具体数量。也未提及训练一批模型（多个配置）所需的总算力。

### 5. 实验数量与充分性

- **实验数量**：
    - **训练配置实验（4组）**：比较不同训练集组合对泛化能力的影响（见下表），这是论文的核心实验。
      | 配置 | 切片组成 | 训练图块数 | 源猪数量 |
      | :--- | :--- | :--- | :--- |
      | D1 | 仅P1: D1 | 180 | 1 |
      | D1+D2+D3 | P1: D1; P2: D2, D3 | 312 | 2 |
      | D1+D2+D3+D4 | 全部 | 420 | 3 |
      | **D1+D4 (最优)** | **P1: D1; P3: D4** | **288** | **2** |
    - **基线对比实验**：PIGMENT vs. UniverSeg vs. MicroSAM。
    - **消融实验**：全增强 vs. 仅强度归一化（无空间增强）。
    - **定性评估**：在一个独立的CCI样本上进行应用。

- **充分性评估**：
    - **优点**：实验设计有层次，核心实验（训练配置对比）能清晰揭示“数据多样性优于数据量”的意外发现。设置了独立的定性测试集（CCI样本），考察了模型对不同损伤模型的泛化潜力。
    - **局限性**：**训练和测试数据规模非常小**（525张图块，3头猪，4张切片）。最优配置（D1+D4）的发现存在过拟合风险，如作者所言仅是“假说生成性”的。外部验证（CCI样本）因缺乏标注，仅停留在定性层面，**不足以支撑强有力的结论**。

### 6. 论文的主要结论与发现

- **PIGMENT框架有效**：在有限的标注数据下，PIGMENT在APP病理分割任务上取得了**平均实例检测率0.85**，显著优于UniverSeg（约0.51）和MicroSAM（近0）。
- **实例级DR优于像素级指标**：DR作为主要指标，揭示了模型在精确边界之外仍能有效定位病灶的能力，而Dice/IoU会低估这种有效检测。
- **标注多样性比数据量更重要**：在有限标注约束下，**跨动物、跨切片的多样性**（配置D1+D4, 2个动物, 288张图）比单纯增加来自同一动物的切片数量（D1+D2+D3, 2个动物, 312张图）或单纯增加所有数据（D1+D2+D3+D4, 3个动物, 420张图）更能提升模型泛化性能。
- **APP特定增强有益但温和**：空间增强相比仅颜色归一化，在大部分（3/4）测试切片上提供了性能增益，但整体提升幅度不大。

### 7. 优点

- **方法的实用性**：针对APP染色量化这一具体、棘手的现实问题，提出了一个**标注经济、计算高效**（训练<2小时）的实用解决方案。
- **指标设计对生物学意义的重视**：提出以**实例级检测率**为主要评估指标，直指“是否找到病灶”这一生物学核心问题，而非过度关注像素级边界对齐，这是非常务实和有洞察力的。
- **数据增强的创新性**：设计的**APP特异性增强管线**（GMM引导假阳性、形态学连接等）直接针对APP病理独有的挑战（低对比度、碎片化、形态多样），是方法的主要亮点。
- **训练配置实验的设计**：通过精心设计的训练配置对比（D1 vs D1+D2+D3 vs D1+D4），有力地揭示和强调了“数据多样性优于数据量”这一重要发现。

### 8. 不足与局限

- **数据集过小**：**核心局限性**。3头猪、4张切片、525个图块的规模限制了实验的可推广性和统计显著性。作者也承认无法区分D2、D3是有害的变异还是无益的噪音，结论需在更大规模数据上验证。
- **外部验证不足**：对CCI损伤模型的评估是**定性的**，缺乏严格的定量外部验证。无法确认模型在正式训练数据外，以及在不同染色批次、不同损伤模型、不同物种上的泛化能力。
- **难以处理的病例**：模型对**微弱、碎片化、或低对比度**的APP阳性轮廓做出错误预测和漏检，这是目前的主要失败模式。此外，在非预期的皮质区域产生假阳性也显示了模型的局限性。
- **核心发现的不确定性**：“跨动物多样性优于数据量”这一核心发现，由于仅基于3头猪的实验，**统计效力极弱**，可能是数据偏差而非普遍规律。

（完）
