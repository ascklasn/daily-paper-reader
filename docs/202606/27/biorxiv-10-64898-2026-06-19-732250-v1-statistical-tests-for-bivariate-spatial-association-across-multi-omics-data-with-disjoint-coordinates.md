---
title: Statistical tests for bivariate spatial association across multi-omics data with disjoint coordinates
title_zh: 多组学数据中不相交坐标上的双变量空间关联统计检验
authors: "Hawinkel, S., Hu, W., Velten, B., Maere, S."
date: 2026-06-24
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.19.732250v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 多组学空间关联统计检验
tldr: "多模态空间组学数据中，不同技术测量的特征空间坐标不重叠，传统相关性检验失效；现有方法忽略空间自相关导致假阳性。本研究修改 Moran's I、高斯过程和广义加性模型为双变量检验，直接处理非重叠坐标集，并纳入空间自相关方差估计。在模拟和真实数据（小鼠/人类空间转录组和代谢组）中验证了新方法的有效性和准确性。成果提供 R 包 sbivar，为多模态空间组学中生物学意义解读提供可靠工具。"
source: biorxiv
selection_source: fresh_fetch
motivation: 克服多模态空间组学中坐标不匹配及忽略空间自相关导致的假阳性问题。
method: "修改空间变量基因检测方法（Moran's I、Gaussian processes、GAM）为双变量检验，并纳入空间自相关方差估计。"
result: 在模拟和真实数据中验证了新方法有效性，发现了新的基因-代谢物共定位对。
conclusion: 提供了在非重叠坐标下考虑空间自相关的双变量空间关联检验套件，开源为 R 包 sbivar。
---

## 摘要
空间生物学已进入多模态分析的新时代，在连续组织切片上测量多种高维空间组学类型，或在同一切片上共同检测。因此，对不同模态特征之间的空间关联进行统计检验引起了关注，以深入了解生物过程。一个主要挑战是双变量组合数量众多，导致计算需求高。另一个困难是技术间空间分辨率不同，意味着即使对齐后，两种模态的测量点之间也缺乏一一对应关系。因此，常见的统计度量如联合分布和相关性无法定义，检验必须仅依赖空间邻近性。此外，我们认为许多现有的双变量关联检验针对不适当的零假设，或做出不适当的假设，两者都意味着任何特征中都不存在空间自相关，从而导致误导性结论。作为补救，我们修改了用于检测空间可变基因的检验（Moran's I、高斯过程和广义加性模型（样条）），以推导出跨模态且坐标集不重叠的双变量检验，并提供考虑空间自相关的方差估计量。我们为单个切片以及具有多个切片的重复实验开发了推断方法，并在非参数和参数模拟中比较了它们的性能。最后，我们将新开发的方法应用于小鼠和人类的两个共同检测的空间转录组学和代谢组学数据集。全套检验可从github.com/sthawinke/sbivar以R包sbivar的形式获得。

作者总结：空间生物学研究活体组织中分子和细胞的空间背景。为此，最近的技术允许在相同或相邻的组织切片上检测不同类别的生物分子。在这项工作中，我们专注于检测分子对共定位的方法，这可能为它们的生物学功能提供线索，例如参与相同的通路。许多现有的用于识别此类共定位对的统计检验强制切片之间进行点对点匹配，从而未能充分利用数据的全部空间分辨率。此外，现有方法忽略了空间组学数据中自然存在的空间模式或自相关，导致许多假阳性发现。作为补救，我们提出了一套可扩展的方法，这些方法直接在不重叠的坐标集上工作，并考虑空间自相关，在模拟研究中验证了其有效性。接下来，我们将新方法应用于小鼠和人类数据集的代谢物和基因表达测量，揭示了有趣的新共定位基因-代谢物对。所提出的方法可在sbivar R包中获得，来自github.com/sthawinke/sbivar。

## Abstract
Spatial biology has entered a new era of multimodal profiling, with multiple, high-dimensional spatial omics types being measured on consecutive tissue slices, or co-assayed on the same slice. Interest then lies in statistical testing for spatial association between the features of the different modalities, to gain insight in biological processes. One major challenge is the multitude of bivariate combinations, leading to high computational demands. Another difficulty is the difference in spatial resolution between technologies, implying no one-to-one matching between the measurement spots of the two modalities, even after alignment. As a result, common statistical measures such as joint distributions and correlations are not defined, and tests need to rely on spatial vicinity only. Moreover, we argue that many existing bivariate association tests address an inappropriate null hypothesis, or make inappropriate assumptions, both implying absence of spatial autocorrelation in any of the features and leading to misleading conclusions. As a remedy, we modify tests for the detection of spatially variable genes (Morans I, Gaussian processes and generalized additive models (splines)) to derive bivariate tests across modalities with non-overlapping coordinate sets and provide variance estimators that do account for spatial autocorrelation. We develop inference methods for single sections as well as for replicated experiments with multiple sections, and compare their performance in nonparametric and parametric simulations. Finally, we apply the newly developed methods to two co-assayed spatial transcriptomics and metabolomics datasets from mouse and human. The full suite of tests is available from github.com/sthawinke/sbivar as the R-package sbivar.

Author summarySpatial biology investigates molecules and cells in their spatial context in living tissues. For this purpose, recent technologies allow to detect different classes of biomolecules on the same or adjacent tissue sections. In this work, we focus on methods to detect colocalization of molecule pairs, which may provide clues on their biological function, e.g. involvement in the same pathways. Many existing statistical tests for identifying such colocalized pairs enforce spot-to-spot matching between tissue sections, thus failing to exploit the full spatial resolution of the data. Moreover, existing methods ignore spatial patterning or autocorrelation naturally present in spatial omics data, leading to many false findings. As a remedy, we present a suite of scalable methods that work directly on disjoint coordinate sets and do account for spatial autocorrelation, confirming their validity in simulation studies. Next we apply the new methods to metabolite and gene expression measurements of mouse and human datasets, uncovering interesting new colocalized gene-metabolite pairs. The methods presented are available in the sbivar R-package from github.com/sthawinke/sbivar.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：随着空间生物学进入多模态分析时代，不同空间组学技术（如转录组学、代谢组学）在同一组织切片或连续切片上测量多种生物分子。研究者需要统计检验不同模态特征之间的空间关联（即双变量空间关联），以揭示生物学过程（如共定位、通路激活）。然而，现有方法面临三大挑战：
  - **坐标不匹配**：不同技术空间分辨率不同，即使对齐后，两种模态的测量点之间缺乏一一对应关系，导致无法定义联合分布和相关性。
  - **计算负担**：双变量组合数量庞大（如基因×代谢物），需高效算法。
  - **零假设不当**：许多现有检验（如双变量Moran's I、Pearson相关性）隐含“无空间自相关”的零假设，导致假阳性——即空间自相关本身就能使检验显著，而非真正的双变量关联。
- **核心贡献**：作者提出一套新的统计检验方法，专门针对**不相交坐标集**，并**校正空间自相关**，实现仅检验双变量空间关联（零假设为条件独立：给定自身空间自相关后，两个变量无关）。方法集成于R包`sbivar`。

## 2. 论文提出的方法论

### 2.1 核心思想
- 现有方法（如双变量Moran's I、Gaussian过程、GAM）原本用于检测单变量空间变异基因（SVG），作者将其改造为**双变量关联检验**，并设计能处理不相交坐标集的权重/协方差结构，同时估计空间自相关以校正方差。
- 零假设：双变量独立（即给定各自的空间结构后无额外关联），而非传统“随机化”假设（要求无空间自相关）。

### 2.2 三种方法

#### (1) 双变量Moran's I（独立性零假设）
- 定义：\(I_{xy} = \mathbf{x}^T W \mathbf{y}\)，其中\(W\)为基于距离衰减的权重矩阵（跨越两模态坐标集）。
- 均值：零假设下\(E(I_{xy})=0\)。
- 方差：通过估计协方差矩阵\(\hat{\Sigma}_x\)和\(\hat{\Sigma}_y\)（利用Matheron变差函数和拟合变异函数模型），计算\(\text{Var}(I_{xy}) = \text{tr}(W^T \hat{\Sigma}_x W \hat{\Sigma}_y)\)。若忽略空间自相关，方差被低估为\(\text{tr}(W^T W)\)，导致假阳性。
- 显著性：采用渐近正态性，并使用多个权重矩阵（不同尺度）结合Cauchy组合检验。

#### (2) 双变量高斯过程（bivariate GP）
- 模型：将两模态的观测值拼接为向量\(\mathbf{z}\)，服从多元正态分布：\(\mathbf{z} \sim MVN(\mu, \Sigma)\)。
- 协方差分解：\(\Sigma = \sigma I + \Sigma_{SAC} + \Sigma_{biv}\)，其中\(\Sigma_{SAC}\)为块对角（各自空间自相关），\(\Sigma_{biv}\)为跨模态空间协方差（感兴趣参数）。
- 检验：对\(\Sigma_{biv}=0\)使用**得分检验**（score test），避免在边界参数空间上的Wald检验问题。分别测试正、负关联，取两倍最小p值作为双尾p值。需测试多个长度尺度后组合p值。

#### (3) 广义加性模型（GAM）
- 模型：分别对两模态特征拟合2D平滑样条（thin plate spline）加上低秩GP平滑器去除残差自相关：\(x_i = \beta_0 + s_x(c_i) + g_x(c_i) + \epsilon_i\)，\(y_j\)类似。
- 评价：在公共网格点\(C_B\)上评估样条曲面，得到\(\iota_B = s_x(C_B), \zeta_B = s_y(C_B)\)，计算协方差\(\hat{q}_{xy}\)和相关性\(\hat{\rho}_{xy}\)。
- 方差：通过Delta方法传播样条系数的不确定性，得到\(\text{Var}(\hat{q}_{xy})\)，然后进行z检验。
- 优点：可视化贡献区域（如\(( \iota_b - \bar{\iota})(\zeta_b - \bar{\zeta})\)热图），易于解释，且可扩展到非正态分布（如负二项、Gamma）。

#### (4) 多切片重复分析
- 对于多个组织的切片（如生物学重复），作者提出先计算每张切片的关联度量（如bivariate Moran's I或GAM相关性），然后在线性模型中分析这些度量，并考虑设计结构（如随机效应）。为了提高效率，可用估计方差的倒数作为权重，但实验显示不加权反而控制更好地类型I错误，而按最大值缩放Moran's I可保持效果。

## 3. 实验设计

### 3.1 数据集
- **非参数模拟**：基于两个真实数据集：
  - **Godfrey数据**：人肺癌/乳腺癌的空间转录组和代谢组（同一切片，已经过点匹配，但作者反匹配生成不相交坐标）。
  - **Vicari数据**：小鼠脑（帕金森模型）的空间转录组和代谢组（真实不相交坐标，作者用MAGPIE对齐）。
- **参数模拟**：在均匀网格上生成数据（联合/不相交坐标），模拟五种场景：
  - 无空间模式（独立同分布）
  - 独立高斯过程（各自空间自相关但独立）
  - 依赖高斯过程（有双变量空间协方差）
  - 条带（streak）模式
  - 区域（zones）模式
- **多切片复制模拟**：生成9个复制切片，变化点数。
- **对齐误差模拟**：在Vicari坐标上添加位置噪声。

### 3.2 对比方法
- 现有方法：双变量Moran's I（多种变体：随机化、置换、SpatialDM、随机移位）、Lee's L、Geary's C、SpaGene、Pearson相关性、修正t检验、Kendall相关性（随机移位）。
- 作者提出的新方法：sbivar包中的Moran's I（独立性零假设）、双变量GP、GAM。

### 3.3 评估指标
- 类型I错误率（p值分布是否均匀，在0.05检验水平下假阳性比例）。
- 统计功效（在备择场景下检出显著的比例）。
- 计算时间。

## 4. 资源与算力

论文**未明确说明**使用的GPU型号、数量或训练时长。作者提到：
- 双变量GP计算最慢，且即使使用GPU加速也难以大幅提速，因为主要耗时在计算测试统计量和方差。
- GAM和bivariate Moran's I（sbivar实现）较快，计算时间随点数增长缓慢。
- 模拟在R环境中运行，未提供具体硬件细节。

## 5. 实验数量与充分性

- **非参数模拟**：基于两个真实数据集，各样本（约7个切片）重复排列多个特征对（前30个特征），进行了大量测试。
- **参数模拟**：5种场景 × 2种坐标（联合/不相交） × 50次蒙特卡洛模拟 × 10个特征/模态，覆盖了从无关联到有强空间自相关和双变量关联的场景。
- **对齐误差模拟**：4个噪声水平 × 20次重复 × 多个特征对。
- **多切片复制模拟**：9个复制，不同组合方法对比。
- **真实数据分析**：两个数据集（多个切片/样本）的完整分析，并展示了新发现与生物学注释。
- **充分性判断**：实验设计较为全面，覆盖了不同零假设、不同空间模式、不同坐标类型、对齐误差和多切片情况。对比方法包括各类主流方法，公平性较好（参数一致）。但缺乏对大规模高维特征对（如数千×数千）的可扩展性严苛测试，以及缺乏与更多最新方法的比较（如SpatialDE2、SPARK-X双变量变体等）。

## 6. 论文的主要结论与发现

- **类型I错误控制**：许多现有方法（如Pearson相关性、SpatialDM、Lee's L、Geary's C、SpaGene）在仅有一个模态存在空间自相关时假阳性严重；而作者的三种方法（bivariate Moran's I独立性零假设、GAM、双变量GP）在模拟中均控制类型I错误。
- **统计功效**：新方法在多个备择场景下具有良好功效，双变量GP在“依赖GP”场景中最好，GAM在“条带/区域”模式中表现稳定。随机移位法功效较低。
- **计算效率**：bivariate Moran's I（sbivar）最快，GAM次之，双变量GP最慢且扩展性差。
- **真实数据发现**：
  - Godfrey数据：发现Kallikrein基因（KLK10-13）与磷脂酰肌醇PI 34:1在肺癌样本中强共定位，与PI3K/AKT通路关联一致。
  - Vicari数据：发现星形胶质细胞标记基因CSRP1与palmitoyl-L-carnitine在纹状体正关联；Ier5与去甲肾上腺素在黑质负关联（与6-OHDA损伤应激反应相关）。
- **多切片分析**：尽管样本量小，但线性模型方法在类型I错误控制上有效，但功效有限；缩放Moran's I可提升功效。

## 7. 优点

- **方法创新**：首次系统解决多模态空间组学中不相交坐标和空间自相关双重问题，将单变量SVG检测方法推广为双变量，且方差校正严谨。
- **数学严谨**：推导了bivariate Moran's I在独立性零假设下的解析方差公式，利用了变差函数估计空间自相关，兼顾计算效率。
- **实用性强**：提供R包`sbivar`，包含多种适用场景的方法（非参数Moran's I、模型化GP、可解释GAM），用户可根据数据类型和计算资源选择。
- **可视化能力**：GAM方法允许绘制空间关联贡献图，有助于生物学解释。
- **仿真全面**：包括非参数（基于真实数据置换）和参数模拟，覆盖多种空间模式及对齐误差，验证了方法的鲁棒性。
- **实际应用价值**：在真实数据中发现有生物学意义的基因-代谢物对，并通过文献支持其关联机制。

## 8. 不足与局限

- **计算复杂度**：双变量GP和bivariate Moran's I（联合计算多次权重）仍面临大点数下的平方级复杂度，尤其是GP。论文未对超大特征数（如万级）进行测试。
- **方差估计假设**：bivariate Moran's I的方差依赖于变差函数拟合，对于高异质性数据（如稀疏计数数据）拟合可能不稳健。作者指出GAM可通过适当分布（如负二项）缓解，但Moran's I非参数版本在处理异方差时已知问题。
- **多切片分析局限性**：线性模型方法假设每张切片关联度量独立，但切片间可能有结构相关（如空间位置对齐差异）。作者未探索更高级的联合模型（如分层贝叶斯），因计算成本太高。
- **缺乏与最新方法的比较**：未与SpaceBF（贝叶斯框架）、或专门针对多模态的Deep learning方法比较。
- **类型I错误与功效平衡**：在“独立GP”场景（仅空间自相关但无关联）下，所有方法控制类型I错误，但个别场景（如高空间自相关）下功效略有下降（如GAM在“依赖GP”场景中略逊于GP方法）。
- **对齐误差稳健性**：对齐误差虽然不影响类型I错误，但会降低某些模式（如条带）的检测功效，提示实际应用中需要精确对齐。

（完）
