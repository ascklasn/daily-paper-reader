---
title: scRNA-seq and genomics analyses reveal key mechanisms of inverted papilloma-associated sinonasal squamous cell carcinoma malignant transformation
title_zh: 单细胞RNA测序和基因组学分析揭示内翻性乳头状瘤相关鼻窦鳞状细胞癌恶性转化的关键机制
authors: "Olonisakin, T. F., Zamuner, F. T., Vu, K., Gunti, S., Ding, Y., Hou, Y., Yang, X., Viswanathan, R., Huynh, A., Comoglio, F., Notaro, M., Cherry, C., Patatanian, M., Wong, N., DeKlotz, T. R., Kim, J., Koch, W., Lane, A. P., Ramanathan, M., Rowan, N. R., Lechner, M., Udager, A., Izumchenko, E., Allen, C. T., London, N. R."
date: 2026-06-04
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.01.729345v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 癌症中多重空间蛋白组学与单细胞转录组整合
tldr: "鼻内翻性乳头状瘤有10%恶变为鳞状细胞癌的风险，但分子机制不清。本研究整合单细胞RNA测序、全外显子测序和空间蛋白质组学，发现呼吸上皮基底细胞为起源细胞，恶变伴随CDKN2A缺失和TP53突变。空间免疫图谱显示M2巨噬细胞在肿瘤-间质界面富集，CXCL14通过IDO通路诱导免疫抑制，抑制T细胞功能。该研究揭示了CXCL14-IDO新机制，为IDO靶向免疫治疗提供了理论依据。"
source: biorxiv
selection_source: fresh_fetch
motivation: 阐明鼻内翻性乳头状瘤恶性转化为鳞状细胞癌的分子和免疫驱动因素，寻找治疗新靶点。
method: 对IP和IP-SNSCC队列进行单细胞RNA测序、多重空间蛋白质组学、全外显子测序及功能实验。
result: 鉴定呼吸上皮基底细胞为起源细胞，发现CDKN2A缺失和TP53突变驱动恶变，CXCL14通过IDO通路诱导M2巨噬细胞免疫抑制。
conclusion: CXCL14-IDO轴是关键免疫抑制机制，IDO靶向免疫调节可作为辅助治疗策略。
---

## 摘要
鼻窦内翻性乳头状瘤（IP）有10%的风险恶性转化为IP相关鼻窦鳞状细胞癌（IP-SNSCC），但这一进展的分子和免疫驱动因素仍不清楚。本研究整合了IP和IP-SNSCC队列的单细胞RNA测序、多重空间蛋白质组学、全外显子组测序和功能分析，以定义恶性转化机制。呼吸上皮基底细胞被确定为可能的起源细胞，进展的标志是反复出现的CDKN2A缺失和TP53突变。空间分析揭示了IP-SNSCC中病变界面的免疫重组，其特征是选择性激活的M2巨噬细胞富集。研究表明，CXCL14通过IDO通路依赖机制直接诱导免疫抑制性髓系表型，抑制T细胞IFNγ的产生。这些多模态数据集的整合定义了一种先前未被认识的CXCL14-IDO机制，该机制在肿瘤-基质界面限制了抗肿瘤免疫。这些发现将IDO靶向免疫调节确立为一种合理的辅助策略，并为理解IP-SNSCC发病机制提供了全面的分子框架。

## Abstract
Sinonasal inverted papilloma (IP) carries a 10% risk of malignant transformation to IP-associated sinonasal squamous cell carcinoma (IP-SNSCC), yet the molecular and immune drivers of this progression remain poorly defined. This study integrates single-cell RNA sequencing, multiplexed spatial proteomics, whole-exome sequencing, and functional assays across IP and IP-SNSCC cohorts to define mechanisms of malignant transformation. Respiratory epithelial basal cells are identified as the putative cell of origin, with progression marked by recurrent CDKN2A loss and TP53 mutations. Spatial profiling reveals immune reorganization at the lesional interface in IP-SNSCC, characterized by enrichment of alternatively activated M2 macrophages. CXCL14 is shown to directly induce an immunosuppressive myeloid phenotype that suppresses T-cell IFN{gamma} production through an IDO-pathway-dependent mechanism. Integration of these multimodal datasets defines a previously unrecognized CXCL14-IDO mechanism that constrains anti-tumor immunity at the tumor-stroma interface. These findings establish IDO-targeted immunomodulation as a rational adjuvant strategy and provide a comprehensive molecular framework for understanding IP-SNSCC pathogenesis.

---

## 论文详细总结（自动生成）

## 论文详细中文总结

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：鼻窦内翻性乳头状瘤（IP）有约10%的恶变风险，转化为IP相关的鼻窦鳞状细胞癌（IP-SNSCC），但驱动这一恶性转化的分子和免疫机制尚不明确。IP-SNSCC患者预后长期停滞（5年总生存率约50%），缺乏有效靶向治疗。
- **整体含义**：阐明恶变机制有助于识别早期分子事件和免疫逃逸途径，为发现新的治疗靶点（如免疫检查点）提供依据，改善患者生存。

### 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：通过整合单细胞转录组、空间蛋白质组、全外显子测序和体外功能实验，从上皮细胞起源、基因组突变、免疫微环境重塑三个维度系统解析IP→IP-SNSCC的恶性转化过程。
- **关键技术细节**：
  - **单细胞RNA测序（scRNA-seq）**：使用10x Genomics 5′基因表达试剂盒，对新鲜冷冻标本进行解离、捕获、建库和测序（Illumina NovaSeq 6000）。经Cell Ranger比对，Seurat v4.3.0归一化、降维、Harmony批次校正、Leiden聚类，UMAP可视化。
  - **伪时间轨迹分析**：采用Slingshot推断上皮细胞分化轨迹，结合广义加性模型识别沿伪时间动态变化的基因。
  - **空间蛋白质组学**：使用PhenoCycler-Fusion平台（Akoya Biosciences）对FFPE切片进行25重标记。单细胞分割采用QuPath（v0.6.0）的StarDist扩展，基于DAPI核分割和细胞膜扩展2-3 μm。细胞表型通过层级设门策略分配。空间距离分析：计算免疫细胞到最近参考区室（IP中为上皮，IP-SNSCC中为肿瘤）的欧氏距离，定义浸润比、免疫排斥评分、核心-远处比等指标。
  - **全外显子测序（WES）**：采用Agilent SureSelect V5捕获，NovaSeq 6000 PE150测序（约150×）。经nf-core/sarek流程处理（bwa-mem2比对，GATK Mutect2+Strelka检测体细胞变异，VEP注释），superFreq进行拷贝数分析。
  - **功能实验**：重组人CXCL14处理单核-巨噬细胞，流式检测CD206表达；CD14+单核细胞与抗CD3/CD28刺激的T细胞共培养，ELISA检测IFNγ；加入IDO通路抑制剂Indoximod验证通路依赖。

### 3. 实验设计：数据集、场景、基准与对比方法
- **数据集**：
  - scRNA-seq队列：初始20例患者（15个良性乳头状瘤，5个IP-SNSCC），质控后保留19例（15良性+4恶性）。其中17例同时有WES数据。
  - WES队列：18例患者（14良性+4恶性），共36个DNA样本（肿瘤-正常配对），其中1例IP-SNSCC仅做WES。
  - 空间蛋白质组：6张FFPE切片（3 IP，3 IP-SNSCC）。
- **场景**：比较IP（良性）与IP-SNSCC（恶性）的细胞组成、基因表达、空间定位、突变谱和免疫抑制功能。
- **基准与对比方法**：无显式外部基准，主要为两组间比较（IP vs IP-SNSCC）。对比了公共健康鼻窦黏膜scRNA-seq数据（Deprez et al. 2020）以确定起源细胞。
- **对比方法**：未对比其他已发表恶性转化模型，而是通过多模态数据内部验证。

### 4. 资源与算力
- 论文**未明确说明**所使用的GPU型号、数量、训练时长等信息，仅提及“利用了NIH HPC Biowulf集群”进行计算。
- 单细胞数据处理、WES变异检测等均未报告具体算力开销。这一点不足。

### 5. 实验数量与充分性
- **实验数量**：
  - scRNA-seq：21个样本（19例患者），覆盖良性、恶性和正常对照，聚类分析充分。
  - WES：18个肿瘤-正常配对，足够发现复发突变但样本量偏小。
  - 空间蛋白质组：仅6个标本（3+3），统计推断力有限。
  - 功能实验：使用3个独立健康供体的单核细胞进行T细胞抑制实验，每个供体重复，并设vehicle、CXCL14、CXCL14+Indoximod三组。CD206诱导实验有正对照（IL-4）。TIL/PIL实验使用少数样本。
- **充分性评价**：
  - **优点**：多平台整合，从转录组到基因组再到功能，层层递进，逻辑连贯。空间分析完全分离两组（中位免疫-参考距离无重叠），提示差异显著。
  - **不足**：空间组学样本量小（仅3+3），无法进行多变量校正或泛化统计检验；缺乏独立验证队列（如TCGA或外部SNSCC数据集）；功能实验仅限于体外，缺乏体内动物模型验证；未系统评估肿瘤内异质性及患者预后关联。

### 6. 论文的主要结论与发现
- **细胞起源**：呼吸上皮基底细胞是IP的起源细胞，恶变过程中伴随纤毛基因丢失和基底/干性标记物上调。
- **基因组特征**：IP-SNSCC中反复出现CDKN2A截断突变/拷贝数丢失（3/4样本）和TP53错义突变（2/4样本），良性IP中无。
- **免疫微环境重塑**：IP-SNSCC中免疫细胞向肿瘤-间质界面重新分布（浸润比高、排斥比低），尤其是M2样巨噬细胞（CD68⁺CD206⁺）富集。
- **CXCL14发挥关键免疫抑制功能**：IP-SNSCC肿瘤细胞高表达CXCL14，后者可诱导单核-巨噬细胞向M2样极化，并通过IDO通路依赖机制抑制T细胞IFNγ产生（Indoximod可逆转）。
- **空间免疫调节**：IP-SNSCC中IDO1高表达巨噬细胞聚集在界面附近，形成局部的免疫抑制“生态位”。
- **治疗策略**：提出IDO靶向免疫调节（如Indoximod）可作为IP-SNSCC的辅助治疗选择。

### 7. 优点
- **多模态整合创新**：首次将scRNA-seq、空间蛋白质组学（PhenoCycler）和WES同时应用于IP→IP-SNSCC恶性转化研究，提供了前所未有的分子图谱。
- **发现新的免疫抑制轴**：阐明CXCL14和IDO通路之间的因果关系，揭示了CXCL14此前未知的免疫抑制功能，拓展了肿瘤免疫微环境调控机制。
- **空间分析严谨**：定义多种定量指标（浸润比、排斥比、核心-远处比等），且结果显示两组完全分离，具有强区分度。
- **功能验证充分**：体外实验设计合理，包括多供体重复、正对照、特异性抑制剂，有力地支持了转录组/空间组学推测的机制。
- **临床相关性**：聚焦于10%恶变风险的临床难题，成果直接指导IDO抑制剂作为联合治疗的可能性。

### 8. 不足与局限
- **样本量小**：scRNA-seq仅4个IP-SNSCC、空间组仅3+3、WES仅4个恶性，统计效力有限，且可能引入选择偏倚（如HPV阳性/阴性未分层分析）。
- **缺乏独立验证**：所有发现均来自同一队列，未在外部数据集或更大队列中验证，结果的外推性存疑。
- **空间维度的二维局限性**：分析基于2D组织切片，难以完全反映3D异质性；乳头状IP与实体性SNSCC的形态差异可能影响距离指标，作者虽提及但未充分校正。
- **机制完整性不足**：未明确CXCL14的具体受体（如推测CXCR4、ACKR2、MRGPRX2但未验证），也未在体内模型（如小鼠原位瘤）中证明CXCL14-IDO轴的功能。
- **未考虑肿瘤内异质性和克隆演化**：未对同一患者的多区域样本进行纵向或空间测序，无法追溯从IP到SNSCC的克隆轨迹。
- **缺乏预后与治疗反应数据**：未关联患者生存或免疫治疗反应，结论的临床价值待验证。

（完）
