---
title: "MORPHE: Bridging Image Generation and Spatial Omics for Tissue Synthesis"
title_zh: MORPHE：连接图像生成与空间组学的组织合成方法
authors: "Feng, Y., Robers, Z., Rasheed, L., Miao, Y., Wen, S., Lee, K., Sohigian, J., Brbic, M., Hickey, J. W."
date: 2026-05-28
pdf: "https://www.biorxiv.org/content/10.64898/2026.03.03.709377v2.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 基于空间组学数据的组织合成AI框架
tldr: 空间组学技术成本高、覆盖不全且存在伪影，需要计算方法扩展组织上下文。MORPHE框架通过图信息概率嵌入将细胞身份和空间关系映射为RGB-like潜在空间，借助预训练扩散模型生成组织架构。该方法在肠道和脑数据集上实现百万细胞级单细胞分辨率生成，支持外推、内插和跨组织插补。MORPHE为空间组学数据合成提供了新范式。
source: biorxiv
selection_source: fresh_fetch
motivation: 克服空间组学成本高、覆盖不全、2D局限和伪影，实现组织架构的计算重建与扩展。
method: 将细胞身份和空间关系编码为RGB-like潜在图嵌入，利用扩散模型生成单细胞分辨率组织图像。
result: 在肠道和脑数据集上成功生成百万细胞级组织，实现外推、内插和2D/3D跨组织连接。
conclusion: 桥接图像生成与空间组学，为单细胞空间数据提供可扩展的组织合成方案。
---

## 摘要
空间分辨组学技术以单细胞分辨率揭示组织结构，但仍受限于实验成本、空间覆盖不完整、仅二维成像以及实验伪影。这些因素促使我们需求能够重建或扩展当前空间测量所提供组织情境的计算方法。我们提出MORPHE（结构化空间高维嵌入建模），一个直接从空间组学数据学习合成生物逼真组织架构的AI框架。MORPHE引入了一种基于图的概率嵌入，将离散的细胞身份及其空间关系映射到与扩散建模兼容的连续RGB相似潜在空间。这种表征桥梁使得空间细胞图谱能够利用大型预训练图像生成模型，同时在解码时保持生物学可解释性。通过将细胞建模为生成的基本单元，并学习其身份和空间关系如何共同形成大规模组织结构，MORPHE能够以单细胞分辨率生成和重建组织架构。我们将该方法应用于来自肠道的单细胞蛋白质组学大规模数据集和来自大脑的单细胞转录组学数据集，展示了在数百万细胞上的计算可扩展性。我们在这些数据集上使用MORPHE进行超出实验限制视野的外推绘制、修复缺失或实验损伤的组织区域，并执行跨组织插补，将分离的组织区域连接成一个连续的样本（二维和三维）。MORPHE代表了一类新的组织生成算法，将有助于解决当前单细胞空间组学数据集的局限性和挑战。

## Abstract
Spatially resolved omics technologies reveal tissue organization at single-cell resolution but remain limited by the cost of the assays, incomplete spatial coverage, 2D-only imaging, and experimental artifacts. These factors motivate the need for in silico methods that can reconstruct or extend tissue context beyond what current spatial measurements provide. We present MORPHE (MOdeling of stRuctured sPatial High-dimensional Embeddings), an AI framework that learns to synthesize biologically faithful tissue architecture directly from spatial-omics data. MORPHE introduces a graph-informed probabilistic embedding that maps discrete cell identities and their spatial relationships into a continuous RGB-like latent space compatible with diffusion modeling. This representational bridge enables spatial cellular maps to leverage large pre-trained image-generative models while preserving biological interpretability upon decoding. By modeling cells as the fundamental units of generation and learning how their identities and spatial relationships collectively give rise to large-scale tissue structure, MORPHE enables generation and reconstruction of tissue architecture at single-cell resolution. We applied the method across large-scale single-cell proteomic datasets from the intestine and single-cell transcriptomic datasets from the brain, showing computational scalability acrosss millions of cells. We used MORPHE on these datasets to outpaint beyond experimentally restricted fields of view, inpaint missing or experimentally damaged tissue regions, and perform cross-tissue imputation, connecting separated tissue regions into a single contiguous sample in both 2D and 3D. MORPHE represents a new class of tissue generation algorithms that will help solve current limitations and challenges with single-cell spatial-omics datasets.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：空间分辨组学技术能揭示组织在单细胞水平的空间结构，但受限于实验成本高、空间覆盖不完整（通常只能成像有限视野）、仅支持二维成像、以及存在实验伪影。这些局限阻碍了对组织完整架构的理解和计算重建。
- **核心问题**：如何利用计算方法从已有空间组学数据中学习并合成生物逼真的组织架构，以扩展或重建超出实验测量范围的组织情境。
- **背景含义**：MORPHE 旨在桥接图像生成与空间组学，为单细胞空间数据提供可扩展的组织合成方案，从而解决当前空间组学数据集面临的覆盖不全、维度限制和伪影问题。

### 2. 论文提出的方法论

- **核心思想**：将离散的细胞身份及其空间关系映射到一个与扩散模型兼容的连续RGB相似潜在空间，利用预训练的扩散图像生成模型合成单细胞分辨率的组织图像。
- **关键技术细节**：
  - **图信息概率嵌入**：基于图的概率嵌入方法，将细胞身份（如细胞类型）和空间邻域关系转换为连续的RGB-like潜在表示。
  - **扩散建模**：该表示与扩散模型兼容，可以借助大型预训练图像生成模型（如扩散模型）进行组织架构生成。
  - **生成单元**：以细胞作为基本生成单元，学习细胞身份和空间关系如何共同决定大规模组织结构。
  - **解码可解释性**：潜在表示解码后能保持生物学可解释性（例如映射回细胞类型）。
- **算法流程（文字说明）**：
  1. 输入空间组学数据（包含细胞坐标、细胞类型或表达信息）。
  2. 构建细胞间空间关系图（如KNN或Delaunay）。
  3. 对每个节点（细胞），通过图神经网络融合其自身特征与邻居特征，得到概率分布的参数。
  4. 采样获得低维连续嵌入（类似RGB三通道），使嵌入服从高斯分布或其他连续分布。
  5. 将嵌入组织为2D图像（每个像素对应一个细胞的嵌入向量，缺失区域用掩码标记）。
  6. 使用预训练的扩散模型对掩码图像进行补全、外推或插补，生成完整潜在图。
  7. 解码潜在图为细胞类型/基因表达，并重建组织图像。

### 3. 实验设计

- **数据集**：
  - 来自肠道的单细胞蛋白质组学大规模数据集（空间蛋白组）。
  - 来自大脑的单细胞转录组学数据集（空间转录组）。
- **应用场景**：
  - 外推（outpaint）：对超出实验视野的组织区域进行预测生成。
  - 内绘（inpaint）：修复缺失或实验损伤的组织区域。
  - 跨组织插补（cross-tissue imputation）：连接分离的组织区域为连续样本，包括2D和3D。
- **Benchmark / 对比方法**：论文未明确说明对比了哪些其他方法或基线。根据描述，可能主要展示MORPHE本身的能力，缺乏与现有组织合成模型的定量比较。
- **评估指标**：未在摘要中提及具体定量指标（如FID、细胞类型分类准确率等），可能在下文有描述但本处未提供。

### 4. 资源与算力

- 文中未明确说明使用的GPU型号、数量或训练时长。从方法复杂度推测，使用大规模扩散模型可能依赖多块GPU（如V100/A100），但用户需要自行查阅全文获取具体算力信息。**此处需指出信息缺失**。

### 5. 实验数量与充分性

- **实验数量**：论文在肠道和大脑两个不同组学模态（蛋白质组、转录组）的数据集上进行了测试，覆盖外推、内绘、跨组织插补（2D和3D）多个任务。但未提及消融实验（例如嵌入维度影响、图构建方式等）。
- **充分性评估**：虽然展示了多场景应用，但缺乏与现有方法的定量对比，也未在更广泛的数据集（如肿瘤、发育组织）上验证。作为新提出的框架，实验覆盖范围较为有限，可能不够充分。评估客观性有待补充标准基准。

### 6. 论文的主要结论与发现

- MORPHE能够直接从空间组学数据学习组织架构生成模型，实现百万细胞级的高质量单细胞分辨率重建。
- 成功在肠道和脑数据集上实现外推（扩大视野）、内绘（修复伪影）和跨组织连接（2D/3D），证明其可扩展性和生物逼真度。
- 通过图信息概率嵌入连接图像生成与空间组学，为单细胞空间数据合成提供了新范式。

### 7. 优点

- **创新性**：首次将扩散模型与空间组学结合，利用图嵌入将离散细胞身份映射到连续RGB空间，实现了图像生成领域的预训练模型在组织合成中的迁移。
- **可扩展性**：能在数百万细胞规模上运行，适用于大规模空间组学数据集。
- **多任务能力**：同一个框架支持外推、内绘、插补等多种任务，且能处理2D和3D。
- **生物学可解释性**：嵌入解码后能恢复细胞类型等生物学信息。

### 8. 不足与局限

- **对比实验缺失**：未与现有组织生成方法（如细胞放置模型、GAN-based合成方法）进行定量比较，难以客观评价性能优劣。
- **评估指标不明确**：未报告生成图像与真实组织的相似度度量（如FID、细胞类型比例一致性、空间分布相关性等）。
- **实验覆盖不足**：仅测试了肠道和脑两个数据集，缺乏多样化的组织类型（如肿瘤、胚胎、免疫组织）验证。未在异质性较高或病理样本上评估。
- **潜在偏差风险**：训练数据可能存在选择性偏差（如仅来自单一技术平台），导致生成的组织不一定泛化到其他平台或物种。
- **算力与复现性**：未提供详细计算资源，可能影响可复现性。未公开代码或权重（根据预印本推测，可能在后续版本提供但未确认）。
- **应用限制**：需要预训练扩散模型，对大规模图构建和嵌入的空间连续性假设可能不适用于高度离散或稀疏的细胞分布。

（完）
