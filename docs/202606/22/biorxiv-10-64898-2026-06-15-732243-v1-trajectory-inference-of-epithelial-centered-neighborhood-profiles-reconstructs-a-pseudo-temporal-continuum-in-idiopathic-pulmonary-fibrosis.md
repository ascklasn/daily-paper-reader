---
title: Trajectory inference of epithelial-centered neighborhood profiles reconstructs a pseudo-temporal continuum in idiopathic pulmonary fibrosis
title_zh: 上皮中心邻域谱的轨迹推断重构特发性肺纤维化中的伪时间连续体
authors: "Nakamura, S., Tsubouchi, K., Yamamoto, Y., Takano, T., Nakatsuru, K., Takenaka, T., Hashisako, M., Oda, Y., Okamoto, I."
date: 2026-06-18
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.15.732243v1.full.pdf"
tags: ["query:spatialprot"]
score: 8.0
evidence: 使用Xenium平台对肺纤维化组织进行空间转录组分析推断上皮邻域轨迹
tldr: 特发性肺纤维化（IPF）中空间异质性阻碍了疾病进展的整合分析。本研究利用Xenium空间转录组数据，开发以上皮细胞为中心的邻域谱框架，基于局部细胞组成刻画上皮微环境。通过伪时间推断，重构了从肺泡到纤维化/气道样区域的空间连续轴，并沿该轴绘制了上皮状态、微环境、通路活性及细胞间相互作用的协调变化。该框架为IPF中上皮微环境渐进性重塑提供了可检验的空间假设。
source: biorxiv
selection_source: fresh_fetch
motivation: IPF具有复杂空间异质性，现有方法难以整合分析细胞内在与细胞间通讯在疾病进展中的变化。
method: "利用Xenium空间转录组及630,000+细胞，开发基于局部细胞组成的上皮中心邻域谱框架，并进行伪时间推断。"
result: 重构了反映纤维化空间进展的伪时间连续轴，并绘制了上皮状态、微环境及细胞相互作用的协调变化。
conclusion: 提供了一个空间框架，为IPF中渐进性上皮微环境重塑生成可检验的假设。
---

## 摘要
特发性肺纤维化（IPF）的特征在于复杂的肺结构和空间异质性重塑，这阻碍了疾病进展过程中细胞内在活性与细胞间通讯的综合分析。本文利用Xenium 5k panel对六份包含超过63万个细胞的IPF肺标本进行了分析，并开发了一种基于每个上皮细胞局部细胞组成的上皮中心邻域分析框架。该方法无需预定义组织学区域即可捕获与纤维化相关的上皮微环境变异。对这些谱的伪时间连续体推断重构了一个连续轴，反映了从相对完好的肺泡区域到纤维化和气道样重塑区域的空间进展。在这一空间数据集中，我们沿着同一轴描绘了上皮状态、局部微环境、上皮细胞内通路活性以及与邻近细胞类型定向相互作用的协调变化。我们的发现为IPF中渐进性上皮微环境重塑提供了可检验假说的空间框架。

## Abstract
Idiopathic pulmonary fibrosis (IPF) is characterized by complex lung architecture and spatially heterogeneous remodeling, which have hindered integrated analysis of cell-intrinsic activity and intercellular communication during disease progression. Here we profiled six IPF lung specimens comprising more than 630,000 cells using the Xenium 5k panel and developed an epithelial-centered neighborhood profiling framework based on the local cellular composition around each epithelial cell. This approach captured fibrosis-associated variation in epithelial niches without requiring predefined histological regions. Pseudo-temporal continuum inference of these profiles reconstructed a continuous axis that reflected the spatial progression of fibrotic remodeling from relatively preserved alveolar regions to fibrotic and airway-like remodeled regions. Within this spatial dataset, we mapped coordinated changes in epithelial states, local microenvironments, epithelial intracellular pathway activities, and directional interactions with neighboring cell types along the same axis. Our findings provide a spatial framework that generates testable hypotheses for progressive epithelial niche remodeling in IPF.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **背景**：特发性肺纤维化（IPF）是一种慢性、进行性、致命性的间质性肺病，病理上表现为肺组织结构复杂且空间异质性重塑，包括肺泡上皮的进行性丢失、异常上皮细胞的出现以及气道样化生。这种空间复杂性阻碍了从细胞内在活性和细胞间通讯角度整合分析疾病进展。
- **问题**：现有的空间邻域分析通常将组织架构描述为离散的结构状态，或者基于全局细胞类型进行邻域鉴定，缺乏与纤维化进程的连续关联，且难以在同一空间数据集中同时分析上皮细胞内部程序、局部微环境及细胞-细胞相互作用。
- **动机**：需要建立一种框架，将组织架构、上皮重塑、细胞内程序和细胞间信号传导在空间数据中联系起来，从而生成关于IPF中上皮微环境渐进性重塑的可检验假说。

### 2. 论文提出的方法论：核心思想、关键技术细节、算法流程
- **核心思想**：开发“上皮中心邻域分析”框架，基于每个上皮细胞周围局部细胞组成（80μm半径内）构建邻域谱，并通过轨迹推断重建纤维化重塑的伪时间连续体，从而将上皮状态、微环境变化、通路活性和细胞间通讯映射到同一连续轴上。
- **关键技术细节**：
  - **空间转录组学**：使用Xenium 5k平台（10x Genomics）对6个IPF肺组织切片进行原位转录组分析，共获得630,383个细胞和270,458,182个检测转录本（5,001个基因）。
  - **细胞分割优化**：利用ProSeg重新分割细胞，减少背景和溢出的转录本分配。
  - **细胞类型注释**：通过标准单细胞分析流程（Scanpy）进行聚类，并结合两个公共scRNA-seq参考数据集（GSE135893、GSE136831）进行基因表达插补（Tangram和stAI），最终注释出39种细胞亚型。
  - **上皮中心邻域谱构建**：对每个上皮细胞，统计其80μm半径内所有细胞及其亚型数量，得到上皮细胞×亚型的邻域计数矩阵，然后进行聚类得到7类邻域类（近正常肺泡、前纤维化、纤维化、化生、细支气管、肺泡管、上皮丰富）。
  - **伪时间连续体推断**：使用scFates包，以近正常肺泡类为根，仅使用前纤维化、纤维化和化生类（排除细支气管、肺泡管和上皮丰富类）进行非分支轨迹推断，将伪时间值归一化到0-1范围作为“连续体位置”。
  - **通路活性分析**：利用PROGENy和decoupler推断上皮细胞内通路活性；并将连续体位置扩展到30μm半径内的非上皮细胞以评估转录本溢出的影响。
  - **细胞-细胞相互作用分析**：基于CellChat数据库中的配体-受体对（仅含Xenium panel覆盖的基因），构建空间距离加权的相互作用评分（300μm半径内，高斯核权重），计算从邻域到上皮和从上皮到邻域的双向信号，并在连续体不同区间聚合。
  - **信号正/负比较**：对每个上皮细胞，根据相互作用评分是否>0分为信号阳性组和信号阴性组，使用PyDESeq2进行差异表达分析，再通过GSEApy进行Hallmark基因集富集分析。
  - **免疫荧光验证**：使用系列切片对PERIOSTIN-整合素相互作用进行蛋白水平验证（anti-periostin, anti-integrin αVβ3/αVβ5, anti-α-SMA, anti-pan-cytokeratin）。

### 3. 实验设计：使用了哪些数据集/场景，Benchmark和对比方法
- **数据集**：
  - 主数据集：6个IPF肺组织切片（来自4位经临床和影像学诊断为IPF的患者，接受肺癌手术切除的标本，病理确认为寻常型间质性肺炎（UIP）模式）。其中3个为成纤维细胞灶丰富（FR_s1, FR_s3, FR_s4），2个为蜂窝肺占优（HC_s1, HC_s3），1个为相对完好的肺泡与纤维化交界区（AF_s2）。
  - 用于插补的参考数据集：GSE135893（Habermann et al., 2020）和GSE136831（Adams et al., 2020）的scRNA-seq数据，仅使用IPF和对照肺样本。
  - 配体-受体数据库：CellChat（版本未明确，但限定为Secreted Signaling相互作用，且所有基因均在Xenium 5k panel中）。
- **Benchmark**：论文未设置传统的基准数据集或外部验证集；其验证主要通过空间分布与已知组织学特征的一致性、免疫荧光染色确认蛋白表达、以及信号正/负比较中恢复已知生物学关联（如TGFβ信号与EMT富集）来间接论证。
- **对比方法**：没有直接对比其他方法（如NicheNet、CellChat的全局分析等）。作者仅在引言中提到“大多数空间邻域分析描述组织架构为离散结构状态”，而本方法通过连续体解决这一问题，但未在同一数据集上对比其他框架。

### 4. 资源与算力
- **未明确说明**：论文中没有提及使用的GPU型号、数量、训练时长等具体算力资源信息。仅提到使用Python库（Scanpy、scFates、decoupler、PyDESeq2、GSEApy等），推测在常规服务器或工作站上完成分析，但未提供细节。

### 5. 实验数量与充分性
- **实验数量**：
  - 主分析基于6个组织切片，约63万个细胞。细胞类型注释、邻域聚类、轨迹推断、通路活性、细胞-细胞相互作用均在全部细胞上执行。
  - 邻域类别鉴定：聚类得到7类，并进行了空间可视化验证（图2e-g）。
  - 伪时间连续体：针对4个纤维化相关邻域类（排除了3个）进行轨迹推断，并展示了在6个样本上的分布和空间连续性（图3c-e）。
  - 通路活性沿连续体分析：展示了20 bins的PROGENy活性热图（图3h），并针对Androgen和Hypoxia进行了细胞类型解析（图3j-m）。
  - 细胞-细胞相互作用：Sankey图（图4b-c）、代表性PERIOSTIN相互作用（图4d）及免疫荧光验证（图4e-f）；信号正/负比较进行了TGFβ、HGF-MET、PERIOSTIN的GSEA分析（图4g, Extended Data Fig.8）。
  - 动态变化沿连续体：10 bins内展示前50个相互作用（图5a-b），并详细展示了POSTN-ITGAV_ITGB3和C5-C5AR1的圆形图（图5c-d）。
  - 信号正/负比较还包括C5-C5AR1（Extended Data Fig.10e）。
- **充分性与公平性**：
  - **优点**：分析流程较为完整，从细胞注释到空间邻域、轨迹、通路、互作，形成多层次的整合。免疫荧光验证增加了可信度。
  - **不足**：
    - 样本量小（6个切片来自4例患者），统计检验力有限，可能存在个体差异和抽样偏差。
    - 未设置独立的验证队列或外部数据集来泛化结论。
    - 缺乏与其他现有空间分析方法（如MERINGUE、Giotto、Squidpy的全局邻域分析）的直接比较，无法证明本方法的优越性。
    - 信号正/负比较中存在潜在混杂（如局部邻近效应），作者承认转录本溢出可能影响结果。
    - 插补步骤（Tangram和stAI）可能引入参考数据集的偏见，但仅用于注释支持，未用于定量分析。
  - 整体而言，实验设计是探索性的，生成假说而非严格验证。

### 6. 论文的主要结论与发现
- 上皮中心邻域分析能够识别出与纤维化阶段相关的7类空间微环境，反映从正常肺泡到纤维化和气道样化生的连续变化。
- 伪时间连续体与组织学严重程度顺序一致（AF→FR→HC），且在单个切片内呈现空间连续分布。
- 上皮细胞内通路活性沿连续体变化：雄激素和缺氧通路活性在早期肺泡状态中较高，随纤维化进展下降；JAK-STAT、PI3K、VEGF通路在中期达到高峰。
- 细胞-细胞相互作用方面：成纤维细胞灶中，肌成纤维细胞通过PERIOSTIN整合素（αVβ3/αVβ5）信号作用于KRT5-/KRT17+异常上皮细胞和基底细胞，且这些上皮细胞中EMT、TGFβ、TNFα通路富集；免疫荧光证实了蛋白水平的共定位。
- 配体-受体互作沿连续体动态变化：如TGFβ家族不同配体在不同时期活跃，VEGFA-KDR在早期肺泡稳态中显著，PDGF相关信号从KRT5-/KRT17+和基底细胞向促纤维化细胞类型发送。
- 早期AT2细胞通过C5-C5AR1与单核/巨噬细胞通讯，且C5-C5AR1阳性AT2细胞呈现细胞周期、糖酵解和氧化应激相关转录特征。

### 7. 优点：方法或实验设计上的亮点
- **创新性**：提出“上皮中心邻域分析”而非全局邻域分析，更贴合IPF以上皮损伤为核心的病理机制；将伪时间推断思想应用于细胞组成向量而非基因表达，实现了组织微环境连续变化的量化。
- **整合性**：在同一数据集中同时分析上皮状态、微环境组成、细胞内通路活性和细胞间互作，避免了跨数据集整合的偏差。
- **空间粒度**：单细胞分辨率下保留了空间坐标，使得连续体位置可映射到原始组织图像，便于直观验证。
- **验证思路**：通过已知生物学关联（如TGFβ信号与EMT）恢复预期模式，增强了信号正/负比较的可信度；免疫荧光染色提供了蛋白层面的证据。
- **方法透明**：详细描述了参数（80μm半径、300μm半径、高斯核等），且代码即将公开。

### 8. 不足与局限：包括实验覆盖、偏差风险、应用限制
- **样本量小**：仅4例患者的6个切片，可能无法代表IPF的异质性，结论推广需谨慎。
- **技术局限**：Xenium 5k panel仅覆盖5,001个基因，限制了通路推断和配体-受体分析的全面性（许多信号分子未包含）；ProSeg分割仍存在错误和转录本溢出的风险，尤其在信号正/负比较中。
- **伪时间假设**：基于非分支轨迹，可能无法反映潜在的疾病分支（如部分肺泡直接转向化生而不经过纤维化灶？），但论文排除了非纤维化类后尚合理。
- **缺乏外部验证**：所有分析均在同一批次数据内进行，未使用独立队列验证连续体的通用性或关键互作轴的保守性。
- **统计分析局限**：未进行多次比较校正的统计检验（如差异表达分析中只用了PyDESeq2的Wald检验，但未说明多重比较校正策略；GSEA虽报告了FDR，但基于的基因排名可能受小样本影响）。
- **应用限制**：该方法依赖于高分辨率空间转录组数据（如Xenium），成本和技术门槛较高；目前为计算框架，产生假说但未经实验验证（如敲除PERIOSTIN或整合素在体内验证功能）。

（完）
