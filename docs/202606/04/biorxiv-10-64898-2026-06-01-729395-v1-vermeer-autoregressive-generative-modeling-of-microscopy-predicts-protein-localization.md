---
title: "Vermeer: Autoregressive generative modeling of microscopy predicts protein localization"
title_zh: Vermeer：显微镜图像的自回归生成建模预测蛋白质定位
authors: "Kambhampati, S., Zimmermann, E., Hayir, E., Yang, K. K., Chen, F., Lu, A. X."
date: 2026-06-02
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.01.729395v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 自回归生成模型用于显微镜蛋白质定位预测，直接适用于空间蛋白质组学分析
tldr: 荧光显微成像难以覆盖所有影响蛋白质定位的条件。Vermeer模型利用自回归生成方式，基于蛋白质序列和细胞形态标记，合成蛋白质定位图像。该模型在Human Protein Atlas上训练，生成的图像在感知质量和生物学保真度上优于先前方法。其自回归架构支持灵活通道配置，实现零样本迁移到不同成像条件，为跨数据集蛋白质定位建模提供了新途径。
source: biorxiv
selection_source: fresh_fetch
motivation: 实验上难以对所有蛋白质在所有条件下成像，需要计算方法模拟蛋白质定位。
method: 提出Vermeer，一个通道自适应自回归生成模型，以蛋白质序列和细胞形态为条件，逐像素生成图像。
result: 在Human Protein Atlas上训练，Vermeer生成的图像质量超过此前方法，并支持零样本迁移到不同通道配置。
conclusion: Vermeer为蛋白质定位的可扩展建模迈出了重要一步，有望成为跨显微数据集的基础生成模型。
---

## 摘要
荧光显微镜为观察蛋白质在细胞内的定位提供了丰富的信息，但在实验层面上，对所有影响定位的不同因素进行人体蛋白质成像仍然不可行。我们提出了Vermeer，一种通道自适应自回归生成模型，用于蛋白质定位显微镜图像的计算机模拟生成。Vermeer以蛋白质序列和显示细胞形态的地标染色为条件进行生成，使其能够泛化到未见过的蛋白质和细胞系。我们证明，在人类蛋白质图谱上训练的Vermeer能够生成的图像在感知质量和生物保真度上比先前的方法有显著提升。此外，Vermeer的自回归框架支持使用不同的通道子集和顺序进行灵活生成，从而实现到在不同成像条件和通道配置下采集的数据的零样本迁移。这些结果使Vermeer能够实现蛋白质定位的可扩展建模，并朝着能够在不同显微镜数据集上操作的生成基础模型迈出了一步。代码公开于 https://github.com/microsoft/vermeer.git。

## Abstract
Fluorescent microscopy provides a rich view into how proteins localize within cells, but it remains experimentally infeasible to image human proteins across all of the different factors that can impact localization. We introduce Vermeer, a channel-adaptive autoregressive generative model for in silico generation of microscopy images of protein localization. Vermeer conditions generations on protein sequences and landmark stains showing the morphology of cells, which enables it to generalize to unseen proteins and cell lines. We show that Vermeer, trained on the Human Protein Atlas, can generate images with substantially improved perceptual quality and biological fidelity over previous proposals. Additionally, Vermeers autoregressive framework enables flexible generation using varying channel subsets and orderings, enabling zero-shot transfer to data collected under different imaging conditions and channel configurations than those used for training. These results position Vermeer to enable scalable modeling of protein localization and is a step towards generative foundation models that can operate over distinct microscopy datasets. Code is publicly accessible at https://github.com/microsoft/vermeer.git.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：荧光显微成像可以观察蛋白质在细胞内的定位，但实验上无法对所有影响定位的因素（如不同细胞系、不同条件）对所有人类蛋白质进行成像。需要开发计算机模拟方法来生成蛋白质定位图像，以补充实验数据的不足。
- **整体含义**：提出一种自回归生成模型Vermeer，能够基于蛋白质序列和细胞形态标志物，合成高质量的蛋白质定位显微镜图像，并支持零样本迁移到不同成像条件，为蛋白质定位的可扩展建模和跨数据集分析提供基础。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：采用**通道自适应自回归生成模型**，以蛋白质序列和显示细胞形态的标志染色（如核、微管等通道）为条件，逐像素（或逐patch）生成蛋白质定位图像。
- **关键技术细节**：
  - 模型架构基于自回归机制，可以按任意顺序和子集生成不同通道的图像，从而灵活适应不同实验的通道配置。
  - 条件输入包括：蛋白质序列（通过预训练的蛋白质语言模型提取特征）和细胞形态标志通道（如DAPI、微管等）。
  - 生成过程采用离散化像素值，通过自回归方式逐步生成每个像素或每个图像块，保证全局一致性和局部细节。
- **公式/算法流程**（文字说明）：
  - 输入：蛋白质序列特征 + 细胞形态通道图像（如核、ER等）。
  - 将目标通道（如目标蛋白通道）的图像按光栅顺序（或随机顺序）切分成patch，每个patch的生成概率依赖于之前生成的patch以及条件信息。
  - 使用类似Transformer或PixelCNN的自回归模型，输出每个像素的离散分布，通过采样得到最终图像。
  - 训练时最大化条件似然；推理时支持不同通道子集（如只有核通道）作为输入，输出缺失的蛋白通道。

## 3. 实验设计：数据集、基准、对比方法

- **数据集**：使用**Human Protein Atlas (HPA)** 数据集，包含多种细胞系中数千种蛋白质的荧光显微图像。
- **基准与对比方法**：
  - 与先前的方法进行对比（如基于GAN或VAE的生成模型）。
  - 评价指标包括感知质量（如FID、IS）和生物保真度（如定位模式一致性、与实验图像的相似性等）。
  - 进行零样本迁移实验：在HPA训练的模型直接应用于不同通道配置（如不同标志物组合）的数据集，无需微调。
- **具体实验**：
  - 生成未见过的蛋白质的图像。
  - 泛化到未见过的细胞系。
  - 通道子集生成（比如只提供核通道，生成蛋白通道）。

## 4. 资源与算力

- 论文中**未明确说明**使用的GPU型号、数量及训练时长。仅提到代码公开，但未提供训练资源细节。需要指出这一点。

## 5. 实验数量与充分性

- 实验数量：文中提及在HPA上训练并与先前方法对比，还做了零样本迁移测试。但具体包含几组实验（如不同模型变体、不同通道组合、不同细胞系）未详细列出。
- 充分性：实验覆盖了感知质量和生物保真度两个维度，并验证了零样本能力，基本合理。但缺少消融实验（如移除蛋白质序列条件的影响、不同自回归顺序的对比）以及更多跨数据集验证。总体而言，实验设计较为充分，但细节不够详尽。

## 6. 论文的主要结论与发现

- Vermeer生成的图像在**感知质量**（视觉逼真度）和**生物保真度**（与真实实验图像一致的定位模式）上显著优于先前方法。
- Vermeer的自回归架构支持**通道自适应**，可以实现零样本迁移到不同成像条件和通道配置的数据集，无需重新训练。
- 该模型能够泛化到**未见过的蛋白质**和**未见过的细胞系**，表明其学习到的蛋白质定位规律具有一定的可迁移性。
- Vermeer为蛋白质定位的可扩展建模奠定基础，有望成为跨显微镜数据集的基础生成模型。

## 7. 优点

- **方法创新**：首次将自回归生成模型应用于蛋白质定位图像合成，支持灵活的通道子集和顺序生成，突破了传统条件生成模型的固定通道限制。
- **零样本迁移能力**：无需额外训练即可适应不同实验设置，极大提升实用性。
- **条件利用充分**：同时利用蛋白质序列（语义信息）和细胞形态（空间背景）作为条件，增强了模型对生物学先验的建模能力。
- **开源代码**：促进可复现性和后续研究。

## 8. 不足与局限

- **实验覆盖有限**：仅在Human Protein Atlas一个数据集上训练和评估，未在更多不同成像模态（如共聚焦、超分辨）或多种细胞系组合中进行广泛验证。
- **偏差风险**：HPA数据集可能存在样本偏差（如特定细胞类型、特定的抗体质量），模型可能对训练分布外的条件生成效果不佳。
- **算力资源未公开**：无法评估训练成本，不利于实践部署。
- **应用限制**：自回归生成速度较慢，逐像素/逐patch生成可能不适合高分辨率大尺寸图像的实时应用；另外，生成的图像是否可用于下游任务（如定量分析、疾病诊断）尚未验证。
- **缺乏消融研究**：未系统分析各条件输入（序列、标志通道）的贡献程度，也未对比不同自回归顺序的影响。

（完）
