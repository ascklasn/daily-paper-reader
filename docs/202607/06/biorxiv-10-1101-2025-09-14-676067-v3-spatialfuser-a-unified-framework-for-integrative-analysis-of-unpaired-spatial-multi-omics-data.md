---
title: "SpatialFuser: a unified framework for integrative analysis of unpaired spatial multi-omics data"
title_zh: SpatialFuser：一个用于非配对空间多组学数据整合分析的统一框架
authors: "Cai, W., Li, W."
date: 2026-07-02
pdf: "https://www.biorxiv.org/content/10.1101/2025.09.14.676067v3.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 深度学习方法整合空间多组学数据，包括蛋白组
tldr: 空间多组学数据整合面临异质性挑战，SpatialFuser框架通过三个模块实现无配对数据的联合分析：MCGATE自编码器学习多尺度空间表征，几何预匹配提供粗初始化，迭代匹配融合结合最优传输与对比学习进行跨切片对齐。在空间域识别、对齐和多组学整合上超越现有方法，揭示互补信号和隐藏变异，适用于多场景扩展。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有空间多组学整合方法难以处理无配对、异质性数据，缺乏通用框架。
method: 提出SpatialFuser，包含MCGATE、几何预匹配和迭代匹配融合模块，结合图注意力、最优传输与对比学习。
result: 在基准测试中空间域识别、对齐和整合性能优于SOTA，成功解析发育动态并恢复互补信号。
conclusion: SpatialFuser通用且可扩展，为空间多组学分析提供统一解决方案。
---

## 摘要
空间多组学技术的最新进展为解读组织微环境中的分子特征提供了前所未有的机会，但跨异质数据集的整合分析仍然具有挑战性。在此，我们提出SpatialFuser，一个用于跨表观基因组学、转录组学、蛋白质组学和代谢组学的非配对空间多组学数据整合分析的深度学习框架。SpatialFuser由三个协调模块组成：MCGATE，一种多头协作图注意自编码器，学习多尺度空间表示以解析预定义空间邻域之外的细粒度空间异质性；一个可选的几何预匹配模块，在组织几何不匹配下提供粗略初始化；以及一个迭代匹配-融合模块，将几何约束的最优传输匹配与对比学习引导的模态融合相结合，用于跨切片对齐和整合。系统基准测试表明，与现有最先进方法相比，在空间域识别、跨切片对齐和多组学整合方面具有优越的性能和可靠性。应用于真实数据集的结果表明，SpatialFuser能够解析精确的空间分子模式，揭示发育动态，并恢复跨模态的互补信号。通过我们的方法对弱相关模态进行跨分辨率整合，进一步揭示了先前被掩盖的生物学变异。我们框架的泛化性和多功能性使得定制的分析场景成为可能，并可扩展到新兴组学。

亮点
O_LI一个用于空间多组学整合数据分析的统一深度学习框架
C_LI
O_LI在空间识别、对齐和多组学整合方面优于最先进的方法
C_LI
O_LI前所未有的跨模态分析场景，提供空间多组学的整体视图
C_LI
O_LI全面的框架设计，具有泛化性和多功能性，适用于定制场景和潜在扩展
C_LI

## Abstract
Recent advances in spatial multi-omics technologies provide unprecedented opportunities to interpret molecular features in tissue microenvironments, but integrative analysis across heterogeneous datasets remains challenging. Here we present SpatialFuser, a deep learning framework for integrative analysis of unpaired spatial multi-omics data across epigenomics, transcriptomics, proteomics, and metabolomics. SpatialFuser consists of three coordinated modules: MCGATE, a Multi-head Collaborative Graph Attention auToEncoder that learns multi-scale spatial representations to decipher fine-grained spatial heterogeneity beyond predefined spatial neighbourhoods; an optional geometric pre-matching module that provides coarse initialization under tissue geometry mismatch; and an iterative matching-fusion module that couples geometry-constrained optimal transport matching with contrastive-learning-guided modality fusion for cross-slice alignment and integration. Systematic benchmarks demonstrate superior performance and reliability compared with existing state-of-the-art methods in spatial domain identification, cross-slice alignment, and multi-omics integration. Applications to real datasets illustrate that SpatialFuser resolves precise spatial molecular patterns, reveals developmental dynamics, and recovers complementary signals across modalities. Cross-resolution integration of weakly correlated modalities by our method further uncovers previously obscured biological variation. The generalizability and versatility of our framework enable customized analytical scenarios and potential extension for emerging omics.

HighlightsO_LIA unified deep learning framework for spatial multi-omics integrative data analysis
C_LIO_LISuperior performance against state-of-the-art methods in spatial identification, alignment, and multi-omics integration
C_LIO_LIUnprecedented cross-modality analysis scenarios to offer a holistic view of spatial multi-omics
C_LIO_LIComprehensive framework design with generalizability and versatility for customized scenarios and potential extension
C_LI

---

## 论文详细总结（自动生成）

# SpatialFuser 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：空间多组学技术快速发展，但来自不同平台、不同模态（表观基因组、转录组、蛋白质组、代谢组）的数据往往在组织几何形状、空间分辨率、细胞组成上存在显著差异，且通常是非配对的（即不共享相同空间坐标）。现有整合方法大多针对配对数据或同一切片，或假设特征结构一致，难以处理弱相关模态、跨分辨率、几何不匹配等复杂场景。
- **研究动机**：需要一个统一、通用、可扩展的深度学习框架，能够同时实现**单切片精细空间域识别**、**跨切片对齐**和**跨模态整合**，并支持**非配对**、**不同分辨率**、**弱相关特征**的数据。
- **整体含义**：提出的 SpatialFuser 填补了这一空白，通过创新的模块化设计（MCGATE 多尺度表征 + 几何预匹配 + 迭代匹配‑融合），为空间多组学分析提供了一个灵活且鲁棒的解决方案。

## 2. 论文提出的方法论

### 2.1 核心思想
将空间多组学数据视为图结构数据，通过**多头协作图注意力自编码器（MCGATE）** 学习每个切片的低维嵌入；对于几何错位严重的切片，先用**可选的几何预匹配**（ICP 或 NDT 算法）进行粗对齐；然后通过**迭代匹配‑融合模块**，将**几何约束的最优传输匹配**与**对比学习引导的模态融合**联合优化，实现跨切片对齐与整合。

### 2.2 关键技术细节

#### (1) MCGATE（Multi-head Collaborative Graph Attention auToEncoder）
- **编码器**：每个切片构建空间 KNN 图；每层利用局部注意力聚合邻域信息（公式 1‑4）。
- **自适应邻域扩展层**：除了局部邻域，还根据嵌入空间的余弦相似度，动态选择**空间远端但分子相似**的 spot 作为长程邻居，形成协作注意力（公式 5‑8），从而捕获多尺度空间模式。
- **解码器**：对称结构，参数共享，重构输入特征。
- **多头注意力**：将特征投影到多个子空间并行计算，增强表达力（公式 11‑12）。
- **损失**：MSE 重构损失（公式 10）。

#### (2) 几何预匹配（可选）
- 将 spot 坐标视为 2D 点云，使用 **ICP（迭代最近点）** 或 **NDT（正态分布变换）** 算法估计刚性变换（旋转矩阵 R 和平移向量 t），缩小几何差异（公式 20‑22）。

#### (3) 迭代匹配‑融合模块
- **匹配层**：基于**最优传输**（Sinkhorn 算法），在几何约束的候选窗口内计算跨切片软匹配矩阵（公式 13‑14）；引入**尘箱通道**（dustbin）处理不可匹配的 spot，避免强制对齐（公式 15‑16）。
- **融合层**：共享 MLP 将两个切片的 MCGATE 嵌入投影到公共潜在空间；以匹配层产生的高置信度对应作为**锚点‑正样本对**，从同一切片非邻域区域采样**负样本对**，使用改进的三元组损失进行对比学习（公式 17）；同时加入**嵌入方向约束损失**（公式 18）和重构损失。
- **迭代机制**：融合层更新后的嵌入反馈给匹配层，重新计算匹配，如此交替优化，逐步细化对齐和整合（总损失公式 19）。

#### (4) 整切片对齐质量控制
基于余弦相似度和随机背景分布（95% 分位数阈值）筛选最终对齐结果。

## 3. 实验设计

### 3.1 数据集与场景
| 数据集 | 描述 | 任务 |
|--------|------|------|
| 10X Visium DLPFC（12 切片） | 人背外侧前额叶皮质，33,438 基因 | 空间域识别（单切片） |
| osmFISH 小鼠体感皮层 | 图像式空间转录组，33 基因 | 跨平台域识别 |
| CODEX 人膀胱癌 | 空间蛋白质组，35 蛋白标记 | 跨模态域识别（细胞类型分布） |
| BaristaSeq 小鼠视觉皮层（2 相邻切片） | 1525+2042 spots | 跨切片对齐+整合 |
| Stereo-seq 蝾螈再生成年端脑（发育期 54 vs 57） | 多发育阶段，非相邻切片 | 跨时间、跨发育阶段对齐 |
| 空间 ATAC‑RNA‑seq E13 小鼠胚胎 | 2187 spots，共测表观+转录 | 跨模态整合（表观基因组+转录组） |
| 多组学小鼠小脑（MAGIC-seq, PLATO, MALDI-MSI） | 不同分辨率、弱相关模态、几何错位 | 跨分辨率、弱相关模态对齐+整合 |

### 3.2 Benchmark 与对比方法
- **空间域识别**：对比 SpaGCN、STAGATE、SEDR、STAligner（Mclust 聚类）；额外用 Leiden、Louvain；消融实验（有无长程注意、头数、超参数鲁棒性）。
- **跨切片对齐**：对比 SPACEL、SLAT、STAligner（Sankey 图、对齐精度、UMAP、ARI 前后对比）。
- **跨模态整合**：对比 MISO、MultiGATE、SpatialGlue、SIMO（聚类图、纯度‑覆盖度分析、标记基因增强、训练时间）。
- **弱相关跨分辨率整合**：无现成可比方法，以 ROC 曲线评价标记基因判别力。

### 3.3 评估指标
- ARI、AMI、同质性、完整性、V‑Measure（域识别）。
- 对齐精度（正确对应比例）、纯度‑覆盖度曲线（CP 标记富集）。
- 训练时间（效率对比）。

## 4. 资源与算力
- **明确说明**：MCGATE 单切片训练（DLPFC）在 **NVIDIA GeForce RTX 4090（24 GB）** 上约 **30 秒**。
- **效率对比**：在 E13 小鼠胚胎数据上，SpatialFuser 训练时间最短（图 4f）；MultiGATE 因框架老旧需在 CPU 上训练 1.5‑2 小时。
- **GPU 数量**：未明确说明使用多少张 GPU，但推测实验在单张 RTX 4090 上完成。
- **计算资源**：论文指出多头注意力在高维稀疏矩阵下存在 GPU 内存瓶颈，但提供了稀疏优化的单头模式用于大切片。

## 5. 实验数量与充分性
- **数量**：覆盖 6 大类数据集，涉及 10+ 种对比方法，包括域识别、对齐、整合、消融、鲁棒性等实验。例如 DLPFC 12 切片全部测试；BaristaSeq 用相邻切片；Stereo-seq 用不同发育阶段；E13 多模态整合；小脑三模态跨分辨率整合。
- **充分性**：
  - **消融实验**：验证长程注意力、多头数、网络深度/宽度、随机种子。
  - **鲁棒性**：超参数网格搜索，展示模型对参数不敏感。
  - **客观性**：对对比方法均采用官方推荐参数并进行了网格调优（特别提及 STAligner、STAGATE、SLAT 等，见图 S6‑S8）；对齐精度采用公认的 ground truth 标签。
  - **公平性**：对于跨模态整合（E13），对比的方法各自有不同设计目标，论文指出了各自的适用场景，并确保比较合理（如 SIMO 适用单细胞映射而非 spot 级整合）。
- **局限性**：部分实验（如 osmFISH、CODEX）仅展示单一切片，未做全批量定量对比，但论文已说明这些作为跨平台/跨模态的适用性测试而非 exhaustive benchmark。

## 6. 论文的主要结论与发现

1. **空间域识别**：SpatialFuser 在 DLPFC 上达到平均 ARI 0.625（最高 0.809），显著优于 SpaGCN（0.422）、STAGATE（0.556）等方法。
2. **跨切片对齐**：在 BaristaSeq 相邻切片中，对齐精度 0.972，略低于监督方法 SPACEL（0.987），但优于 STAligner（0.949）和 SLAT（0.857）。整合后的嵌入 UMAP 显示出更清晰的层次结构和更少的边界模糊。
3. **跨发育阶段整合**：在 Stereo-seq 数据中成功捕捉了从 stage 54 到 stage 57 的细胞动态变化，并在 dEGCs 区域发现此前未注释的子结构（富集 FGF17、STRA6、SLIT2）。
4. **跨模态整合**：在 E13 小鼠胚胎上，SpatialFuser 能区分皮质板与脑室区，而单独模态无法分辨；并且增强了低表达但表观遗传易感基因（如 Vax2, Pax6）的检测，揭示谱系相关调控信号。
5. **跨分辨率弱相关整合**：在小脑三模态数据中，SpatialFuser 有效整合了转录组、蛋白质组、代谢组，将 MALDI‑MSI 的高分辨率信息用于增强转录组中的纤维束区分，ROC AUC 显著提升。
6. **效率**：SpatialFuser 训练时间最低，在所有比较方法中计算效率最高。

## 7. 优点

- **统一框架**：覆盖单切片、双切片、多切片、跨模态、跨分辨率场景，无需针对不同任务切换模型。
- **MCGATE 的创新**：协作注意力同时捕获局部邻域和长程分子相似性，打破“空间邻近即相似”的假设，更贴近真实组织异质性。
- **迭代匹配‑融合**：将对齐和整合从松耦合变为紧耦合，允许初始匹配在优化中逐步改善，降低错误传播。
- **非配对支持**：无需配对坐标或强制特征维度匹配，使用尘箱机制和几何约束处理不可匹配 spot，适应细胞类型/分辨率不一致。
- **跨弱相关模态**：首次实现在蛋白质组-代谢组-转录组弱相关情况下的有效整合，并验证了生物意义。
- **可扩展性**：提供单头稀疏模式处理大切片，代码开源并附带教程，便于社区采用。

## 8. 不足与局限

- **计算资源消耗**：多头注意力机制在 PyTorch 等框架下缺乏高效稀疏张量并行操作，导致 GPU 内存占用大；虽然提供单头模式，但长期仍需更优的稀疏计算策略。
- **缺失组织学图像**：当前不包含组织学图像模块，而图像信息在一些平台上（如 H&E）能提升识别性能。论文解释是为了保持平台通用性和轻量化。
- **重构损失局限性**：MSE 损失不区分技术性 dropout 与真实生物学缺失，对零膨胀数据建模能力有限，可能影响下游稀疏特征的解析。
- **实验覆盖**：跨分辨率整合部分缺乏与现有方法的直接比较（因无现成方法可对比），仅用 ROC 内部验证；且未在有配对 ground truth 的大数据集上系统验证弱相关模态整合的定量优势。
- **生物学推断有限**：论文强调能增强低表达基因检测，但未明确区分“真实转录准备”与“技术噪声”，需进一步实验验证。
- **超参数敏感性**：尽管宣称鲁棒，但具体参数（如 KNN 的 K、长期注意 α、温度系数 τ）仍需用户根据数据调整，可能影响易用性。

（完）
