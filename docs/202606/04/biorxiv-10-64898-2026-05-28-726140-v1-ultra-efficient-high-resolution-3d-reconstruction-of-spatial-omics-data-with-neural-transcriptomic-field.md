---
title: Ultra-efficient High Resolution 3D Reconstruction of Spatial Omics Data with Neural Transcriptomic Field
title_zh: 基于神经转录组场的高效高分辨率空间组学数据三维重建
authors: "Gong, Y., Yuan, X., Gao, R., Chen, J., Yu, Z."
date: 2026-06-01
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.28.726140v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 空间组学数据三维重建
tldr: 现有空间组学技术主要分析二维切片，难以高效重建三维组织。本文提出神经转录组场(NTF)，利用多分辨率哈希网格编码和隐式神经表示学习全局连续三维表征。NTF在15分钟内重建包含1亿细胞的完整小鼠胚胎图谱，速度提升1000倍，且能从稀疏切片进行超分辨率重建。该方法适用于多种组学数据，为构建下一代三维组织图谱提供高效解决方案。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有三维重建方法依赖切片间插值，难以平衡保真度、噪声去除和效率。
method: 提出NTF框架，采用多分辨率哈希网格编码与隐式神经表示学习全局连续三维分子分布。
result: "实现1000倍加速，15分钟重建1亿细胞级小鼠胚胎图谱，仅用10%切片即可超分辨率重建。"
conclusion: NTF提供了快速、可扩展、鲁棒的计算引擎，推动下一代三维组织图谱构建。
---

## 摘要
生物组织本质上是三维（3D）生态系统，其中空间结构决定细胞功能。虽然空间组学技术彻底改变了分子图谱分析，但它们主要局限于孤立的二维（2D）组织切片。现有的试图从稀疏切片重建3D体积的计算方法严重依赖于局部切片间插值，难以平衡高保真重建、降噪和图谱级效率。在此，我们提出神经转录组场（NTF），一种采用多分辨率哈希网格编码和隐式神经表示的深度学习框架。与仅仅连接相邻观测的基于插值的方法不同，NTF学习组织的全局连续3D表示。通过建模潜在的潜在生物模式，NTF固有地将真实分子信号与技术伪影解耦，自然实现稳健的降噪和高保真重建。这种全局场范式打破了传统的可扩展性限制：NTF比现有方法实现高达1000倍的加速，尤其能在15分钟内重建包含1亿细胞规模的3D全小鼠胚胎图谱。此外，NTF能从稀疏输入（例如仅使用10%的切片）生成超分辨率体积，并稳健地外推到未观察的组织区域。我们展示了NTF在多种转录组和蛋白质组数据集上的多功能性，捕获果蝇和小鼠胚胎发生中的复杂时空动态，并绘制人类乳腺癌中的瘤内功能梯度。最终，NTF为构建下一代综合3D组织图谱提供了前所未有的快速、可扩展且稳健的计算引擎。

## Abstract
Biological tissues are inherently three-dimensional (3D) ecosystems where spatial architecture dictates cellular function. While spatial omics technologies have revolutionized molecular profiling, they are largely restricted to isolated two-dimensional (2D) tissue sections. Existing computational methods attempting to reconstruct 3D volumes from sparse slices rely heavily on local slice-to-slice interpolation, struggling to balance high-fidelity reconstruction, noise reduction, and atlas-scale efficiency. Here, we present Neural Transcriptomic Field (NTF), a deep learning framework employing multi-resolution hash-grid encoding and implicit neural representations. Unlike interpolation-based approaches that merely bridge adjacent observations, NTF learns a global, continuous 3D representation of the tissue. By modeling the underlying latent biological patterns, NTF intrinsically decouples true molecular signals from technical artifacts, naturally enabling robust denoising and high-fidelity reconstructions. This global field paradigm shatters traditional scalability limits: NTF achieves up to a 1,000x speedup over existing methods, notably reconstructing a 100-million-cell scale 3D whole-mouse embryo atlas in under 15 minutes. Furthermore, NTF can generate super-resolved volumes from sparse input (e.g., utilizing only 10% of slices) and robustly extrapolating into unseen tissue regions. We demonstrate NTFs versatility across diverse transcriptomic and proteomic datasets, capturing complex spatiotemporal dynamics in Drosophila and mouse embryogenesis, and mapping intra-tumoral functional gradients in human breast cancer. Ultimately, NTF provides an unprecedentedly fast, scalable, and robust computational engine for constructing the next generation of comprehensive 3D tissue atlases.

---

## 论文详细总结（自动生成）

## 论文详细中文总结

### 1. 核心问题与整体含义
- **研究动机**：生物组织是三维生态系统，但当前空间组学技术主要测量孤立2D切片，丢失了关键的3D空间信息。
- **问题**：现有计算3D重建方法（如SpatialZ、FEAST）依赖局部切片间插值，面临**高保真重建、噪声去除、图谱级效率三者不可兼得**的困境，且难以处理稀疏输入和外推。
- **整体含义**：NTF旨在提供一种**全局、连续、隐式神经场**方法，突破插值局限，实现**超高效、高保真、可降噪、可超分辨率、可外推**的3D空间组学重建。

### 2. 方法论
- **核心思想**：将组织视为一个连续的3D分子场，学习坐标→分子特征映射（类似NeRF），而非离散切片插值。
- **关键技术细节**：
  - **多分辨率哈希网格编码**（InstantNGP）：高效编码空间坐标，捕捉多尺度特征。
  - **轻量MLP解码器**：预测潜在基因表达、方差和dropout概率。
  - **Point Spread Function (PSF) 建模**：模拟有限采集模糊，用蒙特卡洛采样聚合局部邻域信号。
  - **专门模块处理技术伪影**：
    - **零膨胀模块**：独立的dropout网络预测零计数概率，用加权BCE损失训练。
    - **批效应校正**：可学习的切片嵌入预测偏置项。
    - **异方差噪声建模**：方差网络基于潜在特征和切片嵌入输出对数方差。
  - **损失函数**（式3-6）：
    - 不确定性感知重建损失（非零观测的高斯负对数似然）
    - Dropout BCE损失
    - 空间平滑正则化（局部MSE）
    - 偏置L2正则化
  - **训练**：Adam优化器，混合精度，20,000迭代，batch size 8,192，学习率1e-4。

### 3. 实验设计
| 数据集/场景 | 描述 | 基准方法 | 评估指标 |
|------------|------|----------|----------|
| **模拟数据**（多规模） | 从1M到10M细胞，含域特异性表达、噪声、零膨胀 | SpatialZ, FEAST | RMSE, Spearman, 3D SSIM |
| **稀疏与超分辨率模拟** | 100切片模拟鼠脑，分别减至10%切片或降采样（bin factor 1-8） | FEAST（稀疏）、NTF仅自比较（超分辨率） | 同上 |
| **真实3D小鼠视觉皮层**（STARmap） | 7切片，三种预测任务：中间切片缺口、大块连续缺口、边界外推 | SpatialZ, FEAST | Spearman, 可视化Rorb |
| **果蝇胚胎/幼虫**（Stereo-seq pseudo-3D） | 多阶段胚胎/幼虫，对比BDGP ISH | SpatialZ（可视化对比） | 定性：与ISH模式一致性 |
| **人类乳腺癌**（IMC空间蛋白质组） | 多切片IMC数据，重建panCK、Ki-67、E/P-Cadherin | naive pseudo-3D | 定性：3D形态功能梯度 |
| **全胚胎小鼠E16.5**（MOSTA） | 13切片，1000+基因，1亿体素规模 | 伪3D堆叠 | 定性：连续梯度、器官边界 |
| **小鼠脑虚拟切片** | 训练后任意角度切面，与Allen Atlas对比 | — | 定性 |

### 4. 资源与算力
- **GPU**：单块 **NVIDIA A100 40GB**。
- **峰值内存**：<10GB（最大规模实验）。
- **训练时长**：
  - 10M细胞模拟数据：<7分钟。
  - 1亿细胞、1000+基因全胚胎图谱：<15分钟。
- **总训练迭代**：默认20,000次，早期停止。

### 5. 实验数量与充分性
- **实验数量**：涵盖**6大类场景**（模拟、真实皮层、果蝇、乳腺癌、全胚胎、虚拟切片），每个场景含多个子实验（如不同基因、不同缺口大小、不同分辨率）。
- **充分性**：
  - **对比基线**：与SpatialZ、FEAST对比，但FEAST在部分设置下性能不佳（可能参数未优化？）。
  - **消融实验**：文中**未明确执行消融**（如去除PSF、dropout、正则化等模块）。但通过实验对比间接体现了各模块作用。
  - **公平性**：在模拟数据中直接比较数值指标；真实数据中由于方法特性（FEAST/SpatialZ无法外推），部分实验仅展示NTF结果，但中间切片/大块缺口任务做了公平对比。
- **总体评价**：实验覆盖面广，但**缺乏系统消融**是一点不足；对比方法在超分辨率、外推任务上天然不适用，故无法在同条件下完全公平。

### 6. 主要结论与发现
- **计算效率**：NTF相比SpatialZ/FEAST实现**最高1000倍加速**，15分钟重建亿级细胞图谱。
- **重建保真度**：在模拟和真实数据上**RMSE/Spearman/3D SSIM全面优于基线**。
- **降噪能力**：因学习全局连续场+平滑正则化，NTF输出更接近干净真实信号，而SpatialZ保留噪声。
- **稀疏鲁棒性**：仅用**10%切片**即可达到与全切片相当的重建质量。
- **超分辨率能力**：即使输入bin factor=8（极低分辨率），NTF仍恢复精细结构。
- **外推能力**：独特支持**边界外推**（预测未观察的切片），而插值方法无法实现。
- **生物学意义**：
  - 果蝇：还原grh从表皮到脑叶的发育转移。
  - 乳腺癌：揭示连续3D肿瘤形态及功能梯度（增殖、侵袭）。
  - 全胚胎：刻画Otx2、Cdkn1c、Slc1a3的器官特异表达梯度和异步器官发生。
- **虚拟切片**：轻量，可任意角度/分辨率查询，无需预存全集。

### 7. 优点
- **极致效率**：哈希编码+轻量MLP实现线性时间开销，远超现有方法。
- **统一框架**：同时处理零膨胀、批效应、异方差噪声、PSF模糊，无需多个预处理步骤。
- **连续隐式表示**：支持任意分辨率、任意方向切片，极大提升下游分析灵活性。
- **强外推能力**：突破局部插值约束，可预测未扫描组织区域（如临床活检重建）。
- **跨模态通用性**：验证于转录组（STARmap、Stereo-seq、MOSTA）和蛋白质组（IMC）。
- **资源友好**：单GPU、<10GB内存、分钟级训练。

### 8. 不足与局限
- **缺乏系统消融**：未量化各模块（PSF、dropout、偏置、方差网络）单独贡献，模块必要性论据不足。
- **外推范围有限**：文中仅外推邻近切片（距离≤2切片），未测试更远外推；作者自身承认受信息密度约束。
- **对比方法覆盖不全**：未与PASTE2、STAlign等对齐方法在3D重建任务上比较；FEAST可能因实现问题表现偏弱。
- **无交叉验证/统计测试**：主要展示点估计和定性结果，缺乏显著性检验。
- **应用限制**：仅验证小鼠、果蝇、人类乳腺癌；外推仍需形态学先验或基础模型辅助才能用于极端未知区域。
- **未探索多模态融合**：仅处理单模态，未与H&E、MRI等整合。
- **代码和数据的可复现性**：虽提供开源代码和Zenodo数据，但bioRxiv预印本阶段尚未经同行评议，需谨慎解读。

（完）
