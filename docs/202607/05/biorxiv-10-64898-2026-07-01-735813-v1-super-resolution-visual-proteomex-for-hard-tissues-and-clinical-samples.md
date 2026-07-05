---
title: Super-Resolution Visual ProteomEx for Hard Tissues and Clinical Samples
title_zh: 硬组织和临床样本的超分辨率视觉蛋白质组Ex
authors: "Zhao, S., Tan, W., Yiu, A., Liu, T., Guo, X., Camara, G. A., Tian, H., Wang, Y., Dong, G., Sun, C., Ding, J., Patra, P., White, A. D., Rodriques, S. G., Mitchener, L., Zhou, H., Guo, T., Liu, Y., Piatkevich, K. D."
date: 2026-07-02
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.01.735813v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 直接提出了一种集成成像与质谱的超分辨率空间蛋白组学平台
tldr: 空间蛋白质组学面临分辨率与覆盖度的权衡，难以同时解析纳米级组织结构和深度蛋白组。microProteomEx整合水凝胶膨胀、荧光成像、激光微切和蛋白质组学，在常规显微镜上实现~47 nm超分辨，并获取29-100 μm分辨率的空间蛋白质组。在硬组织与临床样本中成功分析单肾小球和单斑块（450-1000蛋白），区分黑色素瘤与巨型先天性痣，揭示阿尔茨海默病淀粉样斑块的分子异质性。该平台为关联超微结构与深度空间蛋白质组提供了广泛可及的框架，推动疾病机制与精准医学研究。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有空间蛋白质组学无法同时实现纳米级超分辨成像与深度蛋白鉴定，限制了对组织微环境分子结构的理解。
method: 提出microProteomEx，结合水凝胶组织膨胀、质谱兼容荧光成像、激光捕获显微切割及自下而上蛋白质组学，实现三维超分辨成像与空间蛋白质组解析。
result: 有效侧向分辨率达~47 nm，空间分辨率29-100 μm；在硬组织和临床样本中获取单肾小球/单斑块450-1000蛋白，区分黑色素瘤与结痣，可视化阿尔茨海默病斑块异质性。
conclusion: 建立了一种广泛适用的技术框架，通过关联组织超微结构与深度空间蛋白质组，为疾病生物学、生物标志物发现和精准医学提供支撑。
---

## 摘要
在同一个样本中将纳米级组织 architecture 与无偏分子组成相关联仍然是空间生物学中的一个基本挑战。当前的空间蛋白质组学方法要么缺乏解析纳米级组织架构所需的成像分辨率，要么只能实现有限的蛋白质组覆盖，而能够进行深度蛋白质鉴定的非靶向方法尚未与超分辨率成像整合到单个工作流程中。在这里，我们提出了 microProteomEx，这是一个集成平台，结合了水凝胶辅助组织膨胀、质谱兼容荧光成像、激光捕获显微切割和自下而上蛋白质组学，以实现同时的三维超分辨率成像（在常规衍射极限显微镜上有效侧向分辨率低至约47 nm）和具有可扩展侧向分辨率29-100 μm（0.02-0.28 nL 体积分辨率）的空间分辨蛋白质组学。通过优化固定、蛋白质锚定和二次再包埋策略，我们将该方法扩展到机械坚韧的组织，包括小鼠肾脏和心脏，以及福尔马林固定、石蜡包埋的临床标本。我们展示了单个肾小球和单个斑块的蛋白质组学（每个结构450-1,000种蛋白质），解析了一个罕见儿科病例中恶性黑色素瘤和先天性巨细胞黑色素痣之间的蛋白质组差异，并在阿尔茨海默病小鼠模型的两个疾病阶段中表征了核心与非弥散性β-淀粉样蛋白斑块的形态分辨率分子异质性。microProteomEx 建立了一个广泛可及的框架，用于将组织超微结构与深度空间蛋白质组学相关联，对疾病生物学、生物标志物发现和精准医学具有直接影响。

## Abstract
Correlating nanoscale tissue architecture with unbiased molecular composition within the same specimen remains a fundamental challenge in spatial biology. Current spatial proteomics methods either lack the imaging resolution required to resolve nanoscale tissue architecture or achieve only limited proteome coverage, and untargeted approaches capable of deep protein identification have yet to be integrated with super-resolution imaging within a single workflow. Here, we present microProteomEx, an integrated platform that combines hydrogel-assisted tissue expansion with mass spectrometry-compatible fluorescence imaging, laser capture microdissection, and bottom-up proteomics to achieve simultaneous three-dimensional super-resolution imaging (effective lateral resolution down to ~47 nm on conventional diffraction-limited microscopes) and spatially resolved proteomics at a scalable lateral resolution of 29-100 um (0.02-0.28 nL volumetric resolution). By optimizing fixation, protein anchoring, and a secondary re-embedding strategy, we extend the method to mechanically resilient tissues, including mouse kidney and heart, as well as to formalin-fixed, paraffin-embedded clinical specimens. We demonstrate single-glomerulus and single-plaque proteomics (450-1,000 proteins per structure), resolve proteomic differences between malignant melanoma and giant congenital melanocytic nevus in a rare pediatric case, and characterize the morphology-resolved molecular heterogeneity of cored versus diffuse amyloid-beta plaques in a mouse model of Alzheimer's disease across two disease stages. microProteomEx establishes a broadly accessible framework for correlating tissue ultrastructure with deep spatial proteomics, with direct implications for disease biology, biomarker discovery, and precision medicine.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：空间蛋白质组学面临分辨率与蛋白质覆盖度之间的根本权衡。现有方法要么成像分辨率不足以解析纳米级组织结构（如传统基于抗体的方法），要么只能实现有限的蛋白质组覆盖，而能够进行深度非靶向蛋白质鉴定的方法（如LCM-MS）尚未与超分辨率成像整合在同一工作流中。
- **整体含义**：无法在同一标本内同时获取纳米级组织超微结构信息和全局的分子组成，限制了我们对组织结构与功能关系的理解，特别是在疾病机制、生物标志物发现和精准医学中的转化应用。
- **研究背景**：水凝胶辅助组织膨胀（ExM）已被成功应用于超分辨率成像和原位基因组/转录组学，但此前基于ExM的蛋白质组学方法（如proExM-MS、ProteomEx、FAXP）未能充分实现膨胀样本的超分辨率3D成像能力，且对硬组织（如肾、心）和临床FFPE样本的适用性有限。原始ProteomEx的空间分辨率仅~160 μm，且手动处理小样本困难。

### 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：通过整合水凝胶辅助组织膨胀、质谱兼容荧光染色、激光捕获显微切割（LCM）和自下而上质谱蛋白质组学，在常规衍射极限显微镜上实现超分辨率成像与深度空间蛋白质组的同步分析。
- **关键技术细节**：
  - **二次再包埋策略**：将切取的膨胀凝胶碎片再包埋于非膨胀聚丙烯酰胺凝胶中，稳定尺寸，防止样本丢失，从而使可处理的组织体积降低至0.0235 nL（原始方法的1/25）。
  - **优化固定方法**：对硬组织采用1% PFA + NSA（N-琥珀酰亚胺丙烯酸酯）同时固定与锚定，减少交联，提高均匀膨胀和蛋白质保留，使蛋白鉴定数提高约3倍（相比4% PFA）。
  - **加速工作流**：锚定时间减半（12h→6h），匀浆时间缩短8倍（12h→1.5h），染色/膨胀时间减少3.3倍，总处理时间从65.5h降至33h（不含MS采集）。
  - **超分辨率荧光成像**：使用质谱兼容的SyproRed染料（非共价标记，不干扰质谱）进行全蛋白染色，在常规共聚焦显微镜上实现有效侧向分辨率~47-77 nm（LEF~5.3时）。
  - **图像引导显微切割**：基于荧光图像手动（活检穿孔器）或LCM（激光捕获显微切割）精确获取ROI（兴趣区域），切割后经二次再包埋、胰酶消化、肽段回收，进行LC-MS/MS分析。
  - **算法流程**：DDA或DIA模式采集，FragPipe/DIA-NN分析，R语言进行统计与通路富集，结合AI agent Kosmos进行自动化发现。

### 3. 实验设计：使用的数据集/场景、Benchmark、对比方法
- **数据集/场景**：
  - 小鼠肝脏（标准软组织）、小鼠肾脏和心脏（机械坚韧组织）、临床FFPE皮肤样本（单一儿科病例：GCMN与MM）、5xFAD阿尔茨海默病小鼠模型（5月龄与10月龄的两个疾病阶段）。
  - 在肝脏上进行参数优化（固定条件、匀浆条件、染色条件、组织体积梯度）。
  - 在肾、心上验证硬组织适用性与各向同性膨胀。
  - 在皮肤上比较GCMN与MM区域（11个生物学重复/区域）。
  - 在5xFAD大脑中比较核心斑块（cored）与弥散斑块（diffuse）的蛋白质组（每组3个生物学重复）。
- **Benchmark**：
  - 与前身方法ProteomEx对比（时空分辨率、鉴定深度、处理时间）。
  - 与已发表的DVP（Deep Visual Proteomics）和FAXP（Filter-Aided Expansion Proteomics）进行定性比较（文献讨论）。
  - 自身内部对照组：不同固定液、染料、匀浆条件、组织体积梯度。
- **对比方法**：本工作未进行直接平行实验对比，而是在讨论中与DVP和FAXP进行方法学优劣分析。

### 4. 资源与算力
- 论文**未明确提及**使用的GPU型号、数量、训练时长或具体计算平台。
- 质谱数据采用Bruker timsTOF Pro 2和timsTOF HT采集，数据分析在常规工作站上使用FragPipe、DIA-NN、R和Kosmos（AI agent，可能依赖云端推理）完成。
- Kosmos的迭代分析过程中可能消耗算力，但未量化。

### 5. 实验数量与充分性
- **实验数量**：
  - 优化实验：每组n=3-4个技术重复（来自同一小鼠切片）。
  - 硬组织：肝脏、肾脏、心脏各3个生物学重复（不同切片/小鼠），展示各向同性测量（n=3切片）。
  - 临床皮肤样本：每组11个样本（来自同一病例的两个区域），进行了PCA、GSEA、差异表达分析。
  - AD斑块：每组3个生物学重复（约30个斑块/组，每个重复10个斑块），4个组（YCP, YDP, OCP, ODP）。
  - ChIP-seq验证：每组1个样本（GCMN和MM各一），但论文称有重复（指纹与相关性分析证明可重复性）。
- **充分性与公平性**：
  - 优化实验覆盖了关键步骤，但均为单次实验来源（来自同一小鼠），缺乏跨个体重复，统计推断有限。
  - 临床部分仅一例患者，属于个案研究，不足以推广人群。
  - AD部分每个重复由多个斑块混合，无法评估斑块间异质性。
  - 消融实验（如不同固定、染色）比较了蛋白鉴定数，但未系统比较所有组合。
  - 方法对比未提供定量benchmark，公平性一般。

### 6. 论文的主要结论与发现
1. **方法性能**：microProteomEx实现了有效侧向分辨率~47 nm（常规显微镜），可扩展空间分辨率29-100 μm，0.02-0.28 nL体积分辨率；单结构（肾小球/斑块）鉴定450-1000种蛋白。
2. **硬组织适用性**：通过1% PFA+NSA固定，硬组织（心、肾）可各向同性膨胀（RMS误差~2.4-3.0%），并获取核心蛋白组（肾小球：NPHS2, COL4A3等；心脏：MYH6, TNNT2等）。
3. **临床转化**：在单个FFPE病例中，GCMN与MM区域蛋白质组可清晰分离；MM中ECM蛋白（如ELN, COL8A1）下调，FASN和mTORC1信号上调；ChIP-seq证实H3K27me3介导的ECM基因表观沉默。
4. **AD斑块异质性**：核心斑块富集ApoE、Clu、Gfap、Ptn、Mdk等与淀粉样变性和免疫反应相关蛋白；弥散斑块富集突触蛋白和神经元RNA结合蛋白；两种斑块在早期即呈现分子差异，且随年龄趋于收敛；提出两阶段致病模型。
5. **AI驱动发现**：Kosmos独立验证了主要发现，并提出了新机制假设（如Hras-JNK轴），展示了AI辅助分析的潜力。

### 7. 优点：方法或实验设计上的亮点
- **创新集成**：首次将ExM的超分辨率成像能力（3D）与深度非靶向蛋白质组学无缝整合在同一工作流中，填补了该方向的空白。
- **技术简化**：二次再包埋策略显著降低了样本处理难度，使手动显微切割小区域（~0.28 nL）成为可能，无需昂贵自动化设备。
- **广泛兼容性**：适用于软、硬、FFPE样本，且染色方法（SyproRed、抗体）质谱兼容，不干扰鉴定。
- **速度提升**：总流程时间减半（33h），提高了通量。
- **验证充分**：在多个组织类型和疾病模型中展示，并辅以正交ChIP-seq验证表观调控机制。
- **AI融合**：引入Kosmos进行自动化数据挖掘与假设生成，展示了AI在空间蛋白质组学中的潜力。

### 8. 不足与局限
- **分辨率局限**：当前空间分辨率（25-100 μm）仍高于单细胞尺度（~10 μm），无法精确到单个细胞。
- **蛋白质组深度**：鉴定数目（数百至数千）低于成熟的单细胞蛋白质组学平台（如SCoPE2），受限于微量样本的质谱灵敏度。
- **临床样本量小**：黑色素瘤部分仅一例患者，结论扩展性有限，存在选择偏差。
- **AD部分批次效应风险**：不同年龄小鼠仅各一只（但每组重复来自同一小鼠不同切片），不能代表群体变异。
- **缺乏跨方法定量比较**：未与DVP、FAXP在相同样本上进行平行实验对比，优势论证主要基于文献观点。
- **Kosmos假设未验证**：AI生成的机制假说（如Hras-JNK）缺乏实验证据，仍需后续验证。
- **手工步**骤多：尽管简化，但仍包含多个手动步骤（显微切割、再包埋），可能影响批间重现性。

（完）
