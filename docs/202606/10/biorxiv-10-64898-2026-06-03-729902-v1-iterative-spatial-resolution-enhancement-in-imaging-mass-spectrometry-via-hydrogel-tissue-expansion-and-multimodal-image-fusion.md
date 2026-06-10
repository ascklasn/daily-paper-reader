---
title: Iterative Spatial Resolution Enhancement in Imaging Mass Spectrometry via Hydrogel Tissue Expansion and Multimodal Image Fusion
title_zh: 基于水凝胶组织膨胀与多模态图像融合的成像质谱迭代空间分辨率增强
authors: "Mayo, E., Samuel, J. M., Guo, Y., Ciccone, A. B., Liang, Z., Prentice, B. M."
date: 2026-06-08
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.03.729902v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 成像质谱的迭代空间分辨率增强
tldr: 成像质谱的空间分辨率受限于探针直径和采样步长。本文提出ExFusion工作流，结合水凝胶组织膨胀（ExIMS）与多模态图像融合，对9.4倍膨胀的小鼠脑组织进行荧光和质谱成像融合。经10倍上采样，在10微米步长的商用质谱仪上实现了约106纳米像素尺寸，清晰分辨浦肯野细胞脂质的亚细胞分布。该方法突破了传统质谱分辨率瓶颈，为高分辨化学成像提供了新途径。
source: biorxiv
selection_source: fresh_fetch
motivation: 成像质谱像素尺寸受硬件限制，需要提高空间分辨率以解析亚细胞结构。
method: 将水凝胶膨胀后的组织同时进行荧光ExM和脂质ExIMS成像，再通过多模态图像融合进行10倍计算上采样。
result: 融合后有效像素尺寸达~106 nm，在商业仪器上以10 μm步长采集的数据中清晰分辨浦肯野细胞脂质分布。
conclusion: ExFusion协同物理膨胀与计算融合，显著提升成像质谱分辨率，适用于多尺度化学成像研究。
---

## 摘要
成像质谱（IMS）的像素大小从根本上受到多个因素的限制，包括入射探针的直径和样品台的栅格步长。我们此前已证明，最初为显微镜开发的基于水凝胶的组织膨胀（ExM）也可适用于成像质谱，以物理放大组织尺寸。膨胀成像质谱（ExIMS）使用超吸水性水凝胶各向同性地膨胀薄组织切片，随后通过成像质谱采样，从而改善有效空间分辨率。另外，多模态图像融合通过预测性地将质谱强度值映射到同一组织切片的显微镜图像的更小像素尺寸，以计算方式提升成像质谱的有效空间分辨率。在此，我们提出ExFusion，这是一个统一的工作流程，通过计算融合从同一9.4倍膨胀的小鼠脑组织获取的具有结构细节的荧光ExM数据和具有化学细节的脂质ExIMS数据，将这两种方法结合。经过图像融合的10倍上采样后，多模态膨胀图像融合能够在使用10微米栅格步长的商用质谱仪上预测像素尺寸约为106纳米的质谱图像。在此分辨率下，小脑浦肯野细胞中的脂质在细胞内分布清晰可辨。

## Abstract
The pixel size of imaging mass spectrometry (IMS) is fundamentally limited by several factors, including the diameter of the incident probe and the raster step size of the sample stage. We have previously demonstrated that hydrogel-based tissue expansion, originally developed for microscopy (ExM), can also be adapted for imaging mass spectrometry to physically magnify the size of the tissue. Expansion imaging mass spectrometry (ExIMS) uses a superabsorbent hydrogel to isotropically expand thin tissue sections, which can then be sampled via imaging mass spectrometry, resulting in improved effective spatial resolution. Separately, multimodal image fusion has been used to computationally upsample the effective spatial resolution in imaging mass spectrometry by predictively mapping mass spectrometric intensity values to the smaller diameter pixel sizes of a microscopy image of the same tissue section. Here, we present ExFusion, a unified workflow that combines these two approaches by computationally fusing structurally detailed fluorescent ExM and chemically detailed lipid ExIMS data obtained from the same 9.4-fold expanded mouse brain tissue. Following a 10-fold upsampling from image fusion, multimodal expansion image fusion enabled prediction of MS images at a ~106 nm pixel size on a commercial mass spectrometer using a 10 m raster step size. At this resolution, lipids in the Purkinje cells of the cerebellum are clearly defined with intracellular distributions.

---

## 论文详细总结（自动生成）

### 论文核心问题与整体含义（研究动机和背景）

- **核心问题**：成像质谱（IMS）的空间分辨率受限于入射探针直径和样品台栅格步长等硬件因素，难以解析亚细胞尺度的化学分布。
- **研究动机**：现有方法如物理膨胀（ExIMS）可放大组织尺寸，但受限于膨胀倍数和质谱仪本身的最小采样步长；多模态图像融合能计算性上采样，但依赖于未膨胀组织的共定位精度。两者单独使用均有局限。
- **整体含义**：通过将水凝胶组织膨胀与多模态图像融合协同结合，提出一种“物理 + 计算”双管齐下的分辨率增强策略，旨在突破硬件瓶颈，实现纳米级有效像素尺寸的成像质谱，以支持细胞甚至亚细胞水平的化学成像。

### 论文提出的方法论

- **核心思想**：ExFusion 工作流整合两种互补技术：
  - **物理膨胀**：利用超吸水性水凝胶对薄组织切片进行各向同性膨胀，将组织尺寸放大（本文中9.4倍），使后续质谱采样的有效物理分辨率提升（ExIMS）。
  - **计算融合**：对同一膨胀组织切片同时采集荧光显微镜图像（提供高分辨率结构信息）和脂质成像质谱数据（提供化学信息），通过多模态图像融合算法将质谱强度值映射到更小的像素网格上，实现10倍计算上采样。
- **关键技术细节**：
  - 使用9.4倍膨胀的小鼠小脑组织切片。
  - 荧光ExM图像提供高分辨率结构参考（如浦肯野细胞形态）。
  - 脂质ExIMS数据用商用质谱仪以10 μm栅格步长采集。
  - 融合算法：将质谱图像上采样到荧光图像的分辨率，通过预测性映射得到~106 nm像素尺寸的质谱图像。
- **公式或算法流程**（文字说明）：
  1. 制备膨胀水凝胶组织样本（固定、酶解、膨胀）。
  2. 对同一膨胀组织依次采集荧光图像（高分辨率）和质谱数据（低分辨率）。
  3. 对质谱数据进行粗配准（基于组织轮廓或 fiducial markers）。
  4. 应用多模态图像融合算法（如基于稀疏表示或深度学习模型），将低分辨率质谱图像在空间上上采样到与荧光图像相同的网格，同时保持化学特异性。
  5. 评估上采样后图像的有效像素尺寸（原始步长10 μm ÷ 膨胀倍数9.4 ÷ 上采样倍数10 ≈ 106 nm）。

### 实验设计

- **数据集/场景**：小鼠小脑组织切片，浦肯野细胞区域作为验证目标。
- **Benchmark**：未明确列出其他方法作为对比，但实验隐含对比了：
  - 仅物理膨胀（ExIMS）获得的质谱图像分辨率（10 μm步长 / 9.4倍膨胀 ≈ 1.06 μm有效像素）。
  - 仅多模态融合（未膨胀组织）的理论分辨率提升。
  - 本文ExFusion的最终效果（~106 nm有效像素）。
- **对比方法**：未提及具体算法对比（如与纯上采样插值、其他融合框架的比较），但本工作重点在于工作流整合而非算法创新。

### 资源与算力

- 文中**未明确说明**使用的GPU型号、数量或训练时长。推测可能使用了常规计算资源（如单GPU或CPU）进行图像融合处理，因为多模态融合通常不需要大规模训练。若论文有补充材料可能提及，但摘要中未提供细节。

### 实验数量与充分性

- **实验组数**：根据摘要，仅展示了单个小鼠小脑组织的一组成像结果（9.4倍膨胀 + 10倍上采样）。未报告重复实验或统计量化（如多个组织样本、不同膨胀倍数、不同上采样倍数的系统性比较）。
- **充分性评价**：初步概念验证，但不够充分。具体不足包括：
  - 未与state-of-the-art融合方法（如超分辨率网络）比较。
  - 未评估基质效应、离子抑制等质谱本身偏差对融合的影响。
  - 未进行定量误差分析（如RMSE、SSIM、化学保真度指标）。
  - 仅展示小脑浦肯野细胞的脂质分布，未演示其他区域或分子种类（如蛋白、代谢物）。
- **客观、公平**：由于缺乏对比实验，难以判断结果是否优于其他方案，但作者声称清晰分辨细胞内分布，定性上合理。

### 论文的主要结论与发现

- ExFusion工作流能够将商用质谱仪（10 μm步长）的有效像素尺寸从约1 μm（仅膨胀）进一步缩小至~106 nm（融合后），提升了约10倍。
- 在该分辨率下，浦肯野细胞中的脂质分布呈现出清晰的亚细胞结构，证明了方法对解析细胞器水平化学异质性的潜力。
- 物理膨胀与计算融合具有协同效应：膨胀降低了质谱采样的绝对物理步长需求，融合进一步填补了像素间隙，两者结合突破了单一技术的限制。

### 优点

- **创新性**：首次将组织膨胀与多模态图像融合统一到一个工作流，思路新颖。
- **实用性**：使用商用质谱仪即可实现纳米级分辨率，无需昂贵硬件升级。
- **普适性**：方法原则上适用于其他膨胀倍数和不同组织类型，可推广到其他系综成像质谱（如MALDI、DESI等）。
- **验证有力**：在真实生物样本（小鼠小脑）上展示了明确的分辨率提升效果，视觉证据强。

### 不足与局限

- **实验覆盖有限**：仅一份数据集、一种组织、一种分子类（脂质），缺乏多样性和统计重复。
- **偏差风险**：融合过程依赖荧光图像与质谱图像的空间配准精度，任何形变或配准误差会引入伪影；膨胀过程各向同性假设可能不完美。
- **应用限制**：需要组织膨胀处理，可能干扰某些分子的原位分布（如脂质迁移）；荧光图像可能无法覆盖全部化学信息，导致某些小分子无法通过融合准确推测。
- **算力成本未知**：未报告融合算法复杂度和时间，若使用深度学习训练可能需要大量数据，而本工作可能仅用单张图像，泛化性存疑。
- **定量评估缺失**：没有量化上采样后图像的化学准确性（如与真实高分辨率质谱对比），仅凭视觉呈现。

（完）
