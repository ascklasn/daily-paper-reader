---
title: scRNA-seq and genomics analyses reveal key mechanisms of inverted papilloma-associated sinonasal squamous cell carcinoma malignant transformation
title_zh: 单细胞RNA测序和基因组学分析揭示内翻性乳头状瘤相关鼻窦鳞状细胞癌恶性转化的关键机制
authors: "Olonisakin, T. F., Zamuner, F. T., Vu, K., Gunti, S., Ding, Y., Hou, Y., Yang, X., Viswanathan, R., Huynh, A., Comoglio, F., Notaro, M., Cherry, C., Patatanian, M., Wong, N., DeKlotz, T. R., Kim, J., Koch, W., Lane, A. P., Ramanathan, M., Rowan, N. R., Lechner, M., Udager, A., Izumchenko, E., Allen, C. T., London, N. R."
date: 2026-06-04
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.01.729345v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 整合空间蛋白组学、单细胞RNA测序和基因组学于癌症研究
tldr: 鼻腔鼻窦内翻性乳头状瘤（IP）恶变为鳞状细胞癌（IP-SNSCC）的分子机制不明。本研究整合单细胞RNA测序、空间蛋白质组、全外显子测序及功能实验，发现呼吸道上皮基底细胞为起源细胞，恶变伴随CDKN2A缺失和TP53突变。空间分析揭示IP-SNSCC中肿瘤-基质界面免疫重组，M2巨噬细胞富集，CXCL14通过IDO通路诱导免疫抑制髓系表型抑制T细胞IFNγ。该研究定义了CXCL14-IDO免疫逃逸机制，为IDO靶向免疫调节作为辅助治疗策略提供了依据。
source: biorxiv
selection_source: fresh_fetch
motivation: 明确IP恶变为IP-SNSCC的分子和免疫驱动机制，以指导治疗策略。
method: 整合scRNA-seq、空间蛋白质组、全外显子测序及功能实验，分析IP和IP-SNSCC队列。
result: 发现呼吸道上皮基底细胞为起源，恶变伴CDKN2A/TP53突变，CXCL14通过IDO通路诱导M2巨噬细胞抑制T细胞IFNγ。
conclusion: 揭示CXCL14-IDO免疫逃逸机制，提出IDO靶向免疫调节作为IP-SNSCC辅助治疗策略。
---

## 摘要
鼻窦内翻性乳头状瘤（IP）有10%的恶性转化风险，可发展为IP相关鼻窦鳞状细胞癌（IP-SNSCC），但这一进展的分子和免疫驱动因素仍不清楚。本研究整合了单细胞RNA测序、多重空间蛋白质组学、全外显子组测序和功能实验，覆盖IP和IP-SNSCC队列，以定义恶性转化的机制。呼吸道上皮基底细胞被确定为可能的起源细胞，进展过程中伴有复发性CDKN2A缺失和TP53突变。空间分析揭示了IP-SNSCC中病变界面的免疫重组，其特征是替代激活的M2型巨噬细胞富集。CXCL14被证明可直接诱导免疫抑制性髓系表型，通过IDO通路依赖机制抑制T细胞IFNγ的产生。这些多模态数据集的整合定义了一个先前未被识别的CXCL14-IDO机制，该机制在肿瘤-基质界面限制抗肿瘤免疫。这些发现确立了靶向IDO的免疫调节作为一种合理的辅助策略，并为理解IP-SNSCC发病机制提供了全面的分子框架。

## Abstract
Sinonasal inverted papilloma (IP) carries a 10% risk of malignant transformation to IP-associated sinonasal squamous cell carcinoma (IP-SNSCC), yet the molecular and immune drivers of this progression remain poorly defined. This study integrates single-cell RNA sequencing, multiplexed spatial proteomics, whole-exome sequencing, and functional assays across IP and IP-SNSCC cohorts to define mechanisms of malignant transformation. Respiratory epithelial basal cells are identified as the putative cell of origin, with progression marked by recurrent CDKN2A loss and TP53 mutations. Spatial profiling reveals immune reorganization at the lesional interface in IP-SNSCC, characterized by enrichment of alternatively activated M2 macrophages. CXCL14 is shown to directly induce an immunosuppressive myeloid phenotype that suppresses T-cell IFN{gamma} production through an IDO-pathway-dependent mechanism. Integration of these multimodal datasets defines a previously unrecognized CXCL14-IDO mechanism that constrains anti-tumor immunity at the tumor-stroma interface. These findings establish IDO-targeted immunomodulation as a rational adjuvant strategy and provide a comprehensive molecular framework for understanding IP-SNSCC pathogenesis.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：鼻腔鼻窦内翻性乳头状瘤（IP）有约10%的概率恶性转化为IP相关的鼻窦鳞状细胞癌（IP-SNSCC），但其分子和免疫驱动机制尚不明确。
- **研究动机**：阐明IP恶变过程中的关键分子事件和免疫微环境变化，从而为IP-SNSCC的早期诊断、预防和靶向治疗提供理论基础。
- **整体含义**：本研究通过多模态整合分析，首次系统揭示了IP-SNSCC恶性转化的细胞起源、基因组驱动因素及免疫逃逸新机制（CXCL14-IDO通路），为开发IDO靶向免疫调节辅助治疗提供了依据。

### 2. 论文提出的方法论
- **核心思想**：整合单细胞转录组学、空间蛋白质组学、基因组学和体外功能实验，从多维度解析IP→IP-SNSCC恶性转化的分子和免疫全景。
- **关键技术细节**：
  - **单细胞RNA测序（scRNA-seq）**：对IP和IP-SNSCC组织进行单细胞转录组分析，定义细胞亚群和分化轨迹。
  - **多重空间蛋白质组学**：利用高参数空间成像技术（如CODEX或类似平台），在组织原位分析肿瘤-基质界面中多种蛋白（包括免疫标志物）的空间分布。
  - **全外显子组测序（WES）**：对配对样本进行突变和拷贝数变异分析，鉴定复发性基因组改变。
  - **功能实验**：通过体外共培养体系（如巨噬细胞与T细胞），验证CXCL14对髓系细胞表型（IDO表达）及T细胞IFNγ产生的直接影响。
- **公式或算法流程**：文中未提及具体数学公式，但整体分析流程可概括为：  
  `【临床样本收集】→【scRNA-seq + WES】→【细胞类型注释及起源鉴定】→【空间蛋白质组学定位免疫格局】→【候选因子（CXCL14）筛选】→【功能验证（体外共培养+IDO抑制剂干预）】→【机制模型构建】`

### 3. 实验设计
- **数据集/场景**：
  - **队列**：IP患者和IP-SNSCC患者的手术标本（队列规模未在摘要中明确，但推测为较小样本量的多中心队列）。
  - **场景**：包括原位肿瘤组织、肿瘤-基质交界区、以及体外细胞共培养模型。
- **基准（benchmark）**：未设外部基准，主要通过与正常呼吸道上皮、单独IP组织及已发表的scRNA-seq参考数据对比。
- **对比方法**：未提及与其他方法的系统性对比；研究以内部分析为主，通过不同模态数据相互验证。

### 4. 资源与算力
- **未明确说明**：论文摘要和元数据中未提及所使用的GPU型号、数量、训练时长等算力信息。仅提到进行了计算分析，但具体硬件配置和计算资源需求未披露。

### 5. 实验数量与充分性
- **实验组数**：主要包含四类分析：
  1. 单细胞转录组分析（可能包含多个患者样本的数十万个细胞）。
  2. 空间蛋白质组学成像（可能包含多张组织切片）。
  3. 全外显子组测序（配对肿瘤-正常或IP-SNSCC-IP样本）。
  4. 功能验证实验（体外共培养+IDO抑制剂处理）。
- **充分性与客观性**：
  - **优点**：多模态数据相互印证，从基因组驱动到免疫微环境重塑再到功能验证，逻辑链完整。
  - **不足**：队列样本量可能较小（常见于罕见肿瘤研究），缺乏独立外部验证队列；且未进行体内动物模型验证。因此结论的普适性和因果性需进一步确认。

### 6. 论文的主要结论与发现
- **细胞起源**：呼吸道上皮基底细胞是IP恶变为IP-SNSCC的起源细胞。
- **基因组驱动**：恶性转化过程中常见CDKN2A缺失和TP53突变。
- **免疫微环境重塑**：IP-SNSCC中肿瘤-基质界面发生免疫重组，替代激活的M2型巨噬细胞显著富集。
- **关键机制**：CXCL14通过IDO通路依赖方式诱导免疫抑制性髓系表型，进而抑制T细胞产生IFNγ，形成肿瘤免疫逃逸。
- **治疗启示**：靶向IDO的免疫调节可作为IP-SNSCC的合理辅助治疗策略。

### 7. 优点
- **多模态整合**：首次将scRNA-seq、空间蛋白质组学、全外显子测序和功能实验有机结合，提供了从宏观基因组到微环境空间格局的完整视图。
- **空间解析度**：通过空间蛋白质组学精确定位免疫变化的“界面”，发现界面处的M2巨噬细胞富集及CXCL14作用。
- **机制新颖性**：揭示CXCL14-IDO这一此前未知的免疫逃逸通路，为罕见肿瘤的免疫治疗提供了新靶点。
- **临床转化潜力**：直接提出IDO抑制剂联合标准治疗的辅助策略，具有较强的应用导向。

### 8. 不足与局限
- **样本量有限**：作为罕见肿瘤研究，队列规模可能较小，统计效力及亚组分析受限。
- **缺乏独立验证**：结论主要基于内部分析，未在独立外部队列或动物模型中进行验证。
- **功能验证的简化**：体外共培养体系无法完全模拟体内复杂的肿瘤微环境，尤其是基质细胞和细胞外基质的影响。
- **CXCL14来源不明**：文中未明确CXCL14的主要细胞来源（肿瘤细胞？基质细胞？），空间定位尚需更精细的分析。
- **IDO靶向的临床风险**：IDO抑制剂在其他肿瘤中临床疗效有限，需进一步通过体内模型评估在IP-SNSCC中的有效性及耐药机制。

（完）
