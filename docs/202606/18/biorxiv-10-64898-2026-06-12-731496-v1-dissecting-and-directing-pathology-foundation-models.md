---
title: Dissecting and directing pathology foundation models
title_zh: 剖析与引导病理基础模型
authors: "Kim, C., Kaczmarzyk, J., Savant, D., Zhao, Z., Koo, P., Lee, S.-I."
date: 2026-06-16
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.12.731496v1.full.pdf"
tags: ["query:hmm"]
score: 9.0
evidence: 通过稀疏自编码使病理基础模型可解释和可控
tldr: 病理基础模型（FM）在数字病理中广泛应用，但其嵌入的“黑箱”特性限制了临床可信度和科学发现。本文提出PICASSO框架，基于稀疏自编码器将FM嵌入分解为人类可解释的视觉概念，在32种癌种、1.2亿组织块上训练得到首个泛癌种组织形态概念图谱。PICASSO支持临床模型行为审计、生物标志物发现（如肺腺癌中EGFR突变的新标志物）、空间转录组关联、技术伪影去除及反事实嵌入生成，将病理FM转变为可解释、可控的机制发现平台。
source: biorxiv
selection_source: fresh_fetch
motivation: 病理基础模型嵌入缺乏可解释性，导致临床转化信任度不足且难以用于科学发现。
method: PICASSO使用稀疏自编码器将FM嵌入分解为视觉概念，在32种癌种、1.2亿组织块上训练得到泛癌种概念图谱。
result: PICASSO鉴定了肺腺癌中EGFR突变的新形态标志物（hobnailing上皮），并实现概念级干预抑制技术伪影、生成反事实嵌入。
conclusion: PICASSO提供了将病理FM转变为可解释、可控机制发现平台的通用框架，增强了模型透明性和生物学洞察能力。
---

## 摘要
基础模型（FMs）是数字病理学的核心，将组织学图像编码为密集嵌入，以促进诊断分类、分子改变预测和临床结局建模。然而，这些嵌入的不透明性使得基于FM的系统成为“黑箱”，限制了其在临床转化中的可信度和科学发现中的实用性。这里，我们介绍PICASSO（通过稀疏字典学习构建的病理图像概念图谱），这是一个使病理FM可解释和可控制的框架。PICASSO使用稀疏自编码器将FM嵌入分解为人类可解释的视觉概念。它在超过1.2亿个组织块（涵盖32种癌症类型）上训练，产生首个泛癌症组织形态学概念图谱。我们证明PICASSO通过揭示学习表示中的可解释结构并支持概念级干预，实现了FM嵌入的多种下游应用。它通过揭示驱动预测的形态学特征，使得能够审计临床模型行为。除了透明性和验证，PICASSO还能够发现新的生物学见解；例如，它识别出鞋钉状上皮形态是肺腺癌中EGFR突变的先前未被认识的生物标志物。通过将PICASSO导出的概念与空间转录组学联系起来，我们揭示了形态学模式与基因表达程序之间的关联。此外，PICASSO允许抑制与技术伪影相关的概念，从而减少模型对虚假信号的依赖。最后，PICASSO能够可控地操作学习到的概念以生成反事实嵌入，用于探索性治疗分析，例如调节肿瘤浸润淋巴细胞密度以评估对预测生存结局的影响。总之，PICASSO提供了一个原则性框架，将病理FM转化为用于机制洞察和发现的平台。

## Abstract
Foundation models (FMs) are central to digital pathology, encoding histology images into dense embeddings for facilitating diagnostic classification, molecular alteration prediction, and clinical outcome modeling. However, the opacity of these embeddings renders FM-based systems "black boxes," limiting their trustworthiness for clinical translation and utility for scientific discovery. Here, we introduce PICASSO (Pathology Image Concept Atlas built via SparSe dictiOnary learning), a framework that makes pathology FMs interpretable and controllable. PICASSO decomposes FM embeddings into human-interpretable visual concepts using a sparse autoencoder. It is trained on more than 120 million tissue patches across 32 cancer types, producing the first pan-cancer atlas of histomorphological concepts. We demonstrate that PICASSO enables diverse downstream applications of FM embeddings by exposing interpretable structure within learned representations and supporting concept-level intervention. It enables auditing of clinical model behavior by revealing the morphological features driving predictions. Beyond transparency and validation, PICASSO enables the discovery of new biological insights; for example, it identified hobnailing epithelial morphology as a previously unrecognized biomarker of EGFR mutations in lung adenocarcinoma. By linking PICASSO-derived concepts with spatial transcriptomics, we uncover associations between morphological patterns and gene expression programs. Furthermore, PICASSO allows suppression of concepts associated with technical artifacts, thereby reducing model reliance on spurious signals. Finally, PICASSO enables controlled manipulation of learned concepts to generate counterfactual embeddings for exploratory therapeutic analysis, such as modulating tumour-infiltrating lymphocyte density to assess impacts on predict survival outcomes. Together, PICASSO provides a principled framework for transforming pathology FMs into platforms for mechanistic insight and discovery.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

病理基础模型（Foundation Models, FMs）在数字病理学中广泛应用，能够直接将苏木精-伊红（H&E）染色图像编码为密集嵌入，用于癌症诊断、分子突变预测和生存预后建模。然而，这些嵌入是“黑箱”的——单个维度缺乏语义，视觉信息难以解读，且容易受到组织折叠、染色差异等技术伪影的干扰。这严重限制了模型在临床转化中的可信度和科学发现能力。现有解释性方法（如显著性图、静态示例）要么难以映射到语义概念，要么无法实现精细操控。因此，论文旨在开发一种框架，将病理FM的嵌入分解为人类可解释的视觉概念，并允许对这些概念进行精确控制和干预，从而提升透明性、生物机理洞察和鲁棒性。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：利用稀疏自编码器（Sparse Autoencoder, SAE）对FM嵌入进行字典学习，将每个密集嵌入分解为少量激活的“概念节点”，每个节点对应一个人类可解释的形态学特征。同时，训练一个扩散模型（Emb2Img）将嵌入逆向生成逼真的组织学图像，通过调节概念激活值可视化形态变化。
- **关键技术细节**：
    - **稀疏自编码器（SAE）**：
        - 编码器：\( \mathbf{c}_i = \operatorname{TopK}(\mathbf{W}_E \mathbf{z}_i) \)，其中 \(\mathbf{z}_i \in \mathbb{R}^d\) 为原始FM嵌入（d=1280），\(\mathbf{W}_E \in \mathbb{R}^{h \times d}\)（h=40,960，扩展倍数32），\(\mathbf{c}_i\) 为稀疏激活向量，非零元素个数为k（最终选k=30）。
        - 解码器：\( \hat{\mathbf{z}}_i = \mathbf{W}_D \mathbf{c}_i \)，\(\mathbf{W}_D \in \mathbb{R}^{d \times h}\)，重构嵌入。
        - 训练目标：最小化重构误差 \( \mathcal{L} = \frac{1}{N}\sum_i \|\hat{\mathbf{z}}_i - \mathbf{z}_i\|^2 \)。
    - **Emb2Img扩散模型**：基于Stable Diffusion v2，但条件输入为FM嵌入而非文本。将嵌入通过交叉注意力注入U-Net，在VAE潜在空间生成256×256像素的图像（训练时512×512，VAE压缩为64×64潜在图）。用于通过概念激活值调节生成反事实图像。
- **算法流程**：
    1. 训练SAE：收集超1.2亿组织块（32癌种TCGA）的FM嵌入（Virchow2），训练SAE得到概念字典和稀疏激活。
    2. 概念验证：联合病理学家，通过高激活示例和Emb2Img逐步调节观察形态变化，标注每个概念对应的形态学含义（如淋巴细胞、肿瘤细胞、组织折叠等）。
    3. 下游应用：对任意新嵌入，先通过SAE编码器得到稀疏概念向量，然后可选择性增加/抑制特定概念节点，再通过SAE解码器得到修改后的嵌入，用于后续任务或可视化。

### 3. 实验设计：使用了哪些数据集/场景，benchmark，对比方法

- **数据集**：
    - **训练数据（构建概念图谱）**：TCGA 32种癌种，11,603张H&E全切片（WSI），提取1.53亿非重叠256×256像素（20×等效）组织块，训练/验证/测试按切片划分（80%/10%/10%）。
    - **下游任务数据**：
        - 乳腺癌淋巴结转移检测：CAMELYON16（400张WSI）。
        - 非小细胞肺癌亚型（LUAD vs LUSC）：TCGA。
        - 乳腺癌受体状态（HER2/PR/ER）：TCGA。
        - 微卫星不稳定性（MSI）：TCGA COAD/READ。
        - EGFR突变预测：TCGA LUAD。
        - IDH突变预测：EBRAINS脑肿瘤数据集。
        - 生存预测：TCGA BRCA和SKCM。
    - 空间转录组：HEST-1k数据集中的乳腺癌淋巴结转移样本（4例患者，10x Visium）和肺腺癌样本（2例患者，10x Xenium）。
- **Benchmark**：下游任务中对比了不同FM（Virchow2, UNI2, GigaPath, ResNet50）的ABMIL（注意力多实例学习）模型性能，验证PICASSO分解后重构嵌入对预测精度影响极小（KL散度<0.01）。
- **对比方法**：
    - 嵌入分解保真度：对比PCA、k-means（视为字典学习），PICASSO在相同组件数下解释方差比例最高。
    - 消融实验：在CAMELYON16上训练肿瘤检测模型，利用Integrated Gradients计算概念重要性，依次禁用top-k概念观察预测翻转比例，对比随机禁用。

### 4. 资源与算力

论文明确提及：
- **SAE训练**：单个NVIDIA A40 GPU，训练5个epoch，耗时14小时10分钟，batch size=2048。
- **Emb2Img训练**：4个NVIDIA A40 GPU，使用PyTorch DDP和混合精度（fp16），batch size=1024（per GPU batch=16，梯度累积=16），训练16,000步，耗时5天22小时。
- 其他模型（如ABMIL分类器、生存模型）未详述，但通常可在单卡上数小时完成训练。

总体算力需求明确且合理。

### 5. 实验数量与充分性

- **实验组数**：
    - 保真度分析：在不同k值（10,30,50,80,100）下比较重构方差；对比PCA和k-means在不同组件数下表现。
    - 下游任务：覆盖7种分类/回归任务（转移检测、亚型、受体、MSI、EGFR、IDH、生存），每个任务10折蒙特卡洛交叉验证。
    - 概念审计与消融：在CAMELYON16上做诊断概念重要性排序及消融，展示前5个概念翻转>80%。
    - 空间转录组关联：对两个top概念分别计算Pearson相关，进行基因集富集（Enrichr）和LLM解释。
    - 伪影去除：训练logistic回归分类伪影，手动验证5个概念节点；模拟捷径学习实验中10个不同的训练-测试分割，对比原始和去噪后的灵敏度。
    - 虚拟干预（TIL模拟）：选取10个淋巴细胞概念，在TCGA BRCA上模拟增殖，用生存模型（C-index 0.705±0.063）比较76例患者处理前后风险分数。
- **充分性评价**：实验设计严谨，覆盖了从嵌入分解到多个临床任务、生物机制、伪影去除和虚拟试验的完整链条。消融实验、交叉验证、统计检验（Mann-Whitney U、Benjamini-Hochberg校正）均使用，结果稳定。但缺少与其他概念解释方法（如Concept Bottleneck Model、TCav等）的直接量化比较，部分定性分析依赖于病理学家主观评判。

### 6. 论文的主要结论与发现

1. PICASSO能够将病理FM嵌入高保真地分解为稀疏的、人类可解释的形态学概念（k=30时解释>80%方差），且重构嵌入对下游分类任务预测影响极小。
2. 构建了首个泛癌种形态概念图谱，揭示不同癌种具有独特的概念特征，且同源癌种（如LGG/GBM、COAD/READ）概念相似。
3. 在CAMELYON16肿瘤检测模型中，PICASSO成功识别出驱动预测的核心概念（如肿瘤细胞团、淋巴细胞混合区域），通过消融验证其重要性。
4. 联合空间转录组学，将概念与基因表达程序关联（如第一概念与上皮细胞标志物PIGR相关，第二概念与B细胞标志物MS4A1相关），提供分子解释。
5. **发现EGFR突变预测模型依赖的新形态标记**：鞋钉状上皮特征（hobnailing morphology），此前未被病理学关联到EGFR状态。与空间转录组关联显示与CXCR4、ACE2等基因及免疫/上皮相关通路相关。
6. 通过抑制组织折叠伪影相关概念节点，在模拟的捷径学习场景中将模型灵敏度从0.61恢复到0.95，无需重新训练。
7. 通过虚拟增加TIL概念，模拟了免疫治疗效果，显著降低了预测生存风险分数，展示了在线药物模拟的潜力。

### 7. 优点：方法或实验设计上的亮点

- **创新性**：将稀疏自编码器与扩散逆向可视化结合，首次在病理FM上实现概念级分解与可控干预，超越了传统被动解释。
- **大规模性**：在32癌种、1.2亿组织块上训练，构建通用概念图谱，覆盖广泛病理变异。
- **多维度验证**：不仅追求拟合能力，还通过临床病理学家逐概念标注、空间转录组关联、模型审计、伪影去除和虚拟试验多层面证明有效性。
- **实用性**：概念级干预无需重训练即可消除伪影、模拟治疗，具有实际部署价值。
- **透明度**：所有实验代码计划开源，数据来自公开TCGA和CAMELYON等，可复现性强。

### 8. 不足与局限：包括实验覆盖、偏差风险、应用限制

- **实验覆盖**：主要基于TCGA和CAMELYON16等公开数据集，这些数据主要来自西方人群，存在种族/地域偏差，实际临床环境中的泛化性未验证。
- **概念抽象层次**：PICASSO概念节点是单一层次的，未建模组织学的多尺度层级结构（如腺体、细胞、亚细胞组分的层次关系）。作者提出未来可扩展至层次概念。
- **下游模型依赖性**：虚拟试验和反事实分析的结论依赖于下游生存预测模型的精度和因果关系假设，无法替代真实临床试验。
- **伪影消除依赖预定义分类**：概念节点需额外训练分类器识别伪影，可能漏掉其他类型伪影（如气泡、染色不均）。
- **解释稳定性**：虽然Integrated Gradients具有公理基础，但概念重要性排序在不同切片和模型初始化间可能存在波动，未充分评估。
- **计算资源需求**：Emb2Img扩散模型训练耗时近6天（4×A40），SAE训练14小时，总体资源需求较高，可能限制小型研究团队复现。
- **缺乏与其他概念发现方法的对比**：未与Concept Bottleneck Model、CLIP-based概念等方法在解释性上量化比较，优劣不明确。

（完）
