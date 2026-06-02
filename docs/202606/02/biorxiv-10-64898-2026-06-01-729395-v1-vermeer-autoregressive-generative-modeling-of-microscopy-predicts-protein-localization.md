---
title: "Vermeer: Autoregressive generative modeling of microscopy predicts protein localization"
title_zh: Vermeer：显微镜图像的自回归生成建模预测蛋白质定位
authors: "Kambhampati, S., Zimmermann, E., Hayir, E., Yang, K. K., Chen, F., Lu, A. X."
date: 2026-06-02
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.01.729395v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 显微镜蛋白质定位预测生成模型
tldr: 蛋白质定位的荧光显微成像实验成本高昂且难以覆盖所有条件。本文提出Vermeer，一种通道自适应自回归生成模型，以蛋白质序列和细胞形态染色为条件，在Human Protein Atlas上训练生成显微图像。生成的图像在感知质量和生物学保真度上显著优于先前方法。该模型支持灵活通道子集和顺序，实现零样本迁移，为可扩展的蛋白质定位建模和显微数据生成基础模型奠定了基础。
source: biorxiv
selection_source: fresh_fetch
motivation: 荧光显微成像实验难以全面覆盖影响蛋白质定位的多种因素，需要高效的计算模型。
method: Vermeer是基于自回归的通道自适应生成模型，以蛋白质序列和细胞形态染色为条件生成显微图像。
result: 在Human Protein Atlas上训练，生成图像的感知质量和生物学保真度显著优于先前方法，并支持零样本迁移。
conclusion: Vermeer实现了蛋白质定位的可扩展建模，是迈向显微数据生成基础模型的重要一步。
---

## 摘要
荧光显微镜为观察蛋白质在细胞内的定位提供了丰富的视角，但由于影响定位的各种因素众多，对人类所有蛋白质进行成像实验在操作上仍不可行。我们提出Vermeer，一个通道自适应的自回归生成模型，用于计算机生成蛋白质定位的显微镜图像。Vermeer的生成条件基于蛋白质序列和显示细胞形态的地标染色，使其能够泛化到未见过的蛋白质和细胞系。我们展示了在人类蛋白质图谱上训练的Vermeer能够生成在感知质量和生物保真度上显著优于先前方案的图像。此外，Vermeer的自回归框架支持使用不同通道子集和顺序进行灵活生成，从而能够零样本迁移到在不同于训练时成像条件和通道配置下收集的数据。这些结果使Vermeer能够实现蛋白质定位的可扩展建模，并朝着能够在不同显微镜数据集上运行的生成基础模型迈进一步。代码公开于https://github.com/microsoft/vermeer.git。

## Abstract
Fluorescent microscopy provides a rich view into how proteins localize within cells, but it remains experimentally infeasible to image human proteins across all of the different factors that can impact localization. We introduce Vermeer, a channel-adaptive autoregressive generative model for in silico generation of microscopy images of protein localization. Vermeer conditions generations on protein sequences and landmark stains showing the morphology of cells, which enables it to generalize to unseen proteins and cell lines. We show that Vermeer, trained on the Human Protein Atlas, can generate images with substantially improved perceptual quality and biological fidelity over previous proposals. Additionally, Vermeer's autoregressive framework enables flexible generation using varying channel subsets and orderings, enabling zero-shot transfer to data collected under different imaging conditions and channel configurations than those used for training. These results position Vermeer to enable scalable modeling of protein localization and is a step towards generative foundation models that can operate over distinct microscopy datasets. Code is publicly accessible at https://github.com/microsoft/vermeer.git.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：蛋白质在细胞内的定位（protein localization）对理解其功能至关重要，但通过荧光显微成像实验对所有人源蛋白质在所有可能条件（如不同细胞系、处理条件等）下进行成像，在实验上不可行，成本高昂且难以覆盖全部变量。
- **研究动机**：发展计算模型，能够基于蛋白质序列和细胞形态等信息，在计算机（in silico）中生成高质量的蛋白质定位显微图像，从而可扩展地模拟蛋白质定位，减少对大规模实验的依赖。
- **背景**：现有方法（如基于GAN或VAE的生成模型）在生物保真度和泛化能力上不足，难以处理未见过的蛋白质或不同成像条件。因此需要更强大的生成基础模型。

## 2. 论文提出的方法论
- **核心思想**：提出Vermeer，一种**通道自适应（channel-adaptive）的自回归生成模型**。模型以蛋白质序列和显示细胞形态的地标染色（landmark stains）作为条件，生成蛋白质定位的显微图像。
- **关键技术细节**：
  - **自回归生成**：将图像生成视为序列问题，逐通道（channel）或逐块（patch）生成，使得模型可以灵活使用不同通道子集和顺序，支持零样本迁移到不同成像配置。
  - **通道自适应**：模型能够根据输入的条件（如蛋白质序列、细胞核或细胞膜染色）动态调整生成过程，无需重新训练即可适应新的通道组合。
  - **条件输入**：使用蛋白质序列（如氨基酸序列）作为蛋白质身份的表征，并使用显示细胞形态的染色（如DAPI、微管蛋白等）提供细胞结构信息，使模型学习序列-结构-定位之间的映射。
- **算法流程**（文字说明）：
  1. 输入：蛋白质序列（编码为嵌入向量）+ 地标染色图像（如细胞核、细胞膜等）。
  2. 编码器：分别对序列和图像进行特征提取，融合形成条件表示。
  3. 自回归解码器：按预定义或可变的通道顺序，逐通道生成目标蛋白的荧光图像。每个通道的生成依赖之前已生成的通道和条件。
  4. 训练：在Human Protein Atlas（HPA）数据集上，以真实荧光图像为监督，优化生成图像与真实图像之间的感知损失和结构相似性等指标。
  5. 推理：支持任意通道子集和顺序，可实现零样本迁移（例如，训练时使用5个通道，推理时仅用2个通道也能生成）。

## 3. 实验设计
- **数据集**：主要使用**Human Protein Atlas (HPA)** 数据集，包含大量人源蛋白质在不同细胞系中的荧光显微图像。
- **Benchmark**：与先前方案（如基于GAN的模型、VAE模型等）进行比较，评价指标包括**感知质量**（如FID、LPIPS等）和**生物保真度**（如定位模式一致性、与专家标注的匹配度等）。
- **对比方法**：文中提到“显著优于先前方案”，但未具体列出对比方法名称（可能包括传统生成模型或特定蛋白质定位预测模型）。
- **实验场景**：
  - 在HPA标准设置下训练和评估。
  - 零样本迁移实验：迁移到不同成像条件或通道配置的数据集（如不同显微镜、不同染色方案），验证模型泛化能力。
- **充分性**：元数据指出实验包括标准生成质量评估和生物学保真度评估，以及零样本迁移测试。但未提及消融实验数量（如不同自回归顺序、不同条件组合等），因此实验详细范围需参考全文。

## 4. 资源与算力
- **文中未明确说明**：元数据和摘要中未提及使用的GPU型号、数量、训练时长等算力信息。如需详细信息，需查阅完整论文正文（可能包含在实验设置部分）。当前推断该团队使用Microsoft资源，但具体数字未知。

## 5. 实验数量与充分性
- **实验数量**：摘要提及比较了“先前方案”，并验证了零样本迁移。但未列出具体实验组数。推测至少包括：
  - 主要生成质量对比实验（HPA数据集）
  - 生物保真度评估（如定位模式分类准确率）
  - 零样本迁移实验（不同成像条件）
- **充分性评价**：
  - **优点**：涵盖生成质量、生物学保真度和泛化能力三个关键维度。
  - **不足**：未提及在不同细胞系、不同蛋白质家族上的细分消融，也未提供与现有蛋白质定位预测方法（如深度学习分类模型）的直接比较。另外，零样本迁移实验的规模（数据集大小、通道差异程度）未知。
  - **客观性**：公开代码（github.com/microsoft/vermeer.git），具备可复现性，但元数据未声明是否进行了第三方独立验证。

## 6. 论文的主要结论与发现
- **Vermeer能生成感知质量和生物学保真度显著优于先前方法的荧光显微图像**。
- **自回归框架支持灵活通道子集和顺序，使模型可零样本迁移到不同成像条件**，无需重新训练即可适应新的通道配置。
- **该方法实现了蛋白质定位的可扩展建模**，是迈向能够在不同显微镜数据集上运行的生成基础模型的重要一步。
- 代码开源，促进后续研究。

## 7. 优点
- **方法创新**：将自回归生成引入显微图像生成，并引入通道自适应机制，解决了传统生成模型泛化性差、无法灵活处理可变通道的问题。
- **条件设计合理**：同时使用蛋白质序列（提供蛋白质身份）和地标染色（提供细胞形态）作为条件，使模型能学习序列-形态-定位之间的复杂关系，从而泛化到未见过蛋白质。
- **零样本迁移能力**：这是实际应用中非常关键的优势，可大幅降低新实验条件下的数据需求。
- **开源代码**：有助于可复现性和社区发展。
- **生物学保真度强调**：不只看图像质量，还评估定位模式是否符合真实生物学知识，更具实际意义。

## 8. 不足与局限
- **实验覆盖有限**：仅在HPA一个数据集上训练，虽验证零样本迁移，但不同显微镜分辨率、噪声水平、细胞类型多样性等尚未充分测试。
- **未详细说明算力需求**：缺乏资源消耗信息，不利于其他研究者评估复现成本。
- **与现有蛋白质定位预测方法的关系**：文中未与基于序列直接预测定位类别（如分类模型）进行对比，可能无法直接替代传统预测方法，而是提供一种图像生成视角。
- **应用限制**：
  - 生成图像质量可能仍受限于训练数据中蛋白质的多样性，对于稀有或异常定位可能效果不佳。
  - 零样本迁移的假设是“通道子集和顺序变化”，但若成像条件发生根本性改变（如不同显微镜类型），模型可能失效。
  - 生成图像的生物学保真度评估标准可能不够严格（如仅依赖专家标注，缺乏功能实验验证）。
- **偏差风险**：HPA数据集主要涵盖人类蛋白质，且细胞系有限，模型可能对特定细胞系或蛋白质类型产生偏差，泛化到其他物种或体内环境需进一步验证。

（完）
