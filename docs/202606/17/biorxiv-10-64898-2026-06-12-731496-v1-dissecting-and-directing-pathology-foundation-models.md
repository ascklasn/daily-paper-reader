---
title: Dissecting and directing pathology foundation models
title_zh: 剖析与引导病理学基础模型
authors: "Kim, C., Kaczmarzyk, J., Savant, D., Zhao, Z., Koo, P., Lee, S.-I."
date: 2026-06-16
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.12.731496v1.full.pdf"
tags: ["query:hmm"]
score: 9.0
evidence: 通过稀疏自编码器实现可解释和可控制的病理基础模型
tldr: 病理基础模型是数字病理学的核心，但其嵌入缺乏可解释性。本文提出PICASSO框架，利用稀疏自编码器将嵌入分解为可解释视觉概念，在32种癌症、1.2亿组织补片上训练出首个泛癌形态概念图谱。该框架支持模型行为审计、生物标志物发现（如肺腺癌EGFR突变相关形态）、技术伪影抑制及反事实嵌入生成，将基础模型转变为可解释的发现平台。
source: biorxiv
selection_source: fresh_fetch
motivation: 病理基础模型的嵌入不可解释，限制了临床信任和科学发现，需要可解释且可控的框架。
method: PICASSO使用稀疏自编码器将病理基础模型嵌入分解为人类可理解的视觉概念，在32种癌症类型的1.2亿组织补片上训练。
result: 首个泛癌组织形态概念图谱，实现了临床模型审计、发现肺腺癌EGFR突变形态标志物、关联空间转录组、抑制技术伪影及生成反事实嵌入。
conclusion: PICASSO提供了将病理基础模型转化为可解释、可控平台的原理框架，促进机制洞察与科学发现。
---

## 摘要
基础模型是数字病理学的核心，将组织学图像编码为密集嵌入，以促进诊断分类、分子改变预测和临床结局建模。然而，这些嵌入的不透明性使得基于基础模型的系统成为“黑箱”，限制了其在临床转化中的可信度以及在科学发现中的实用性。在此，我们提出PICASSO（通过稀疏字典学习构建的病理图像概念图谱），这是一个使病理学基础模型可解释和可控的框架。PICASSO使用稀疏自编码器将基础模型嵌入分解为人类可解释的视觉概念。它在32种癌症类型的超过1.2亿个组织斑块上进行训练，产生了首个泛癌种的组织形态学概念图谱。我们证明，PICASSO通过暴露学习表示中的可解释结构并支持概念级干预，使得基础模型嵌入的多种下游应用成为可能。它通过揭示驱动预测的形态学特征，实现对临床模型行为的审计。除了透明性和验证之外，PICASSO还能发现新的生物学见解；例如，它识别出“钉突状”上皮形态是肺腺癌中EGFR突变的一个先前未被认识的生物标志物。通过将PICASSO衍生的概念与空间转录组学联系起来，我们揭示了形态模式与基因表达程序之间的关联。此外，PICASSO允许抑制与技术伪影相关的概念，从而减少模型对虚假信号的依赖。最后，PICASSO能够对学习到的概念进行受控操作，生成用于探索性治疗分析的反事实嵌入，例如调节肿瘤浸润淋巴细胞密度以评估对预测生存结局的影响。总之，PICASSO提供了一个原则性框架，将病理学基础模型转化为用于机制洞察和发现的平台。

## Abstract
Foundation models (FMs) are central to digital pathology, encoding histology images into dense embeddings for facilitating diagnostic classification, molecular alteration prediction, and clinical outcome modeling. However, the opacity of these embeddings renders FM-based systems "black boxes," limiting their trustworthiness for clinical translation and utility for scientific discovery. Here, we introduce PICASSO (Pathology Image Concept Atlas built via SparSe dictiOnary learning), a framework that makes pathology FMs interpretable and controllable. PICASSO decomposes FM embeddings into human-interpretable visual concepts using a sparse autoencoder. It is trained on more than 120 million tissue patches across 32 cancer types, producing the first pan-cancer atlas of histomorphological concepts. We demonstrate that PICASSO enables diverse downstream applications of FM embeddings by exposing interpretable structure within learned representations and supporting concept-level intervention. It enables auditing of clinical model behavior by revealing the morphological features driving predictions. Beyond transparency and validation, PICASSO enables the discovery of new biological insights; for example, it identified hobnailing epithelial morphology as a previously unrecognized biomarker of EGFR mutations in lung adenocarcinoma. By linking PICASSO-derived concepts with spatial transcriptomics, we uncover associations between morphological patterns and gene expression programs. Furthermore, PICASSO allows suppression of concepts associated with technical artifacts, thereby reducing model reliance on spurious signals. Finally, PICASSO enables controlled manipulation of learned concepts to generate counterfactual embeddings for exploratory therapeutic analysis, such as modulating tumour-infiltrating lymphocyte density to assess impacts on predict survival outcomes. Together, PICASSO provides a principled framework for transforming pathology FMs into platforms for mechanistic insight and discovery.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：病理学基础模型（Foundation Models, FMs）将组织学图像编码为高维密集嵌入，广泛应用于诊断分类、分子预测和生存建模。但这些嵌入是“黑箱”，缺乏可解释性，限制了在临床转化中的可信度和科学发现。
- **背景**：现有病理AI系统依赖FM嵌入，但其内部编码的视觉概念不明；模型预测可能依赖虚假信号（如技术伪影）；缺乏与下游分子通路的结构性联系。
- **研究动机**：开发一种统一框架，将不透明嵌入转化为人类可理解的视觉概念，并支持对这些概念进行显式控制，从而实现模型审计、生物标志物发现、伪影抑制和虚拟实验。

## 2. 论文提出的方法论

### 核心思想
- 使用**稀疏自编码器（Sparse Autoencoder, SAE）** 将病理FM的密集嵌入分解为稀疏线性组合的基向量，每个基向量对应一个人类可解释的“概念节点”。
- 训练一个**大规模泛癌概念图谱**（PICASSO），覆盖32种癌症类型，超过1.2亿组织斑块。
- 开发**Emb2Img**（扩散模型），将FM嵌入映射回真实组织学图像，通过受控调制概念激活来可视化形态变化，实现动态解释。

### 关键技术细节
- **SAE结构**：
  - 编码器：\( \mathbf{c}_i = \mathrm{TopK}(\mathbf{W}_E \mathbf{z}_i) \)，其中 \(\mathbf{z}_i \in \mathbb{R}^{d}\)（\(d=1280\)），\(\mathbf{c}_i \in \mathbb{R}^{h}\)（\(h=40960\)，扩展比32），稀疏度 \(k=30\)（保留前k个最大激活）。
  - 解码器：\( \hat{\mathbf{z}}_i = \mathbf{W}_D \mathbf{c}_i \)。
  - 损失函数：均方误差（MSE）最小化原始嵌入与重构嵌入差异。
- **选择稀疏度**：通过比较不同k（10,30,50,80,100）下的重构方差，选择 \(k=30\)（解释>80%方差，同时保持高稀疏性）。
- **Emb2Img**：基于Stable Diffusion v2，用FM嵌入替换文本嵌入作为条件，在VAE潜空间操作；使用分类器无指导（scale=6.5），PNDM调度器，50步训练/100步推理。
- **概念解释协议**：结合最大激活斑块示例和Emb2Img生成的渐进扰动图像，由病理学家验证每个概念的形态学含义。

## 3. 实验设计

### 数据集
- **训练PICASSO**：TCGA，11603张H&E全切片图像(WSI)，32种癌症类型，提取153,889,118个不重叠斑块(256x256像素，20×倍率，物理尺寸128×128μm)。80%/10%/10%分训练/验证/测试集（同一幻灯片不跨分割）。
- **下游任务数据集**：
  - CAMELYON16（淋巴结转移检测，400张WSI）
  - TCGA LUAD/LUSC（非小细胞肺癌亚型）
  - TCGA BRCA（受体状态预测：HER2, PR, ER）
  - TCGA COAD/READ（微卫星不稳定性MSI）
  - TCGA LUAD（EGFR突变预测）
  - EBRAINS（IDH突变预测，795患者，873样本）
  - TCGA BRCA/SKCM（生存预测）
- **空间转录组学**：HEST-1k数据集，包括4个乳腺癌淋巴结样本（10x Visium）和2个肺腺癌样本（10x Xenium）。
- **伪影实验**：手动标注2000个斑块（1000伪影/1000干净）。
- **TIL模拟**：使用淋巴细胞检测器自动标注100,000斑块。

### Benchmark与对比方法
- **概念解构基准**：PCA（主成分分析）、k-means聚类，对比重构方差和下游预测一致性（KL散度）。
- **下游任务性能**：对比不同FM（Virchow2, UNI2, GigaPath, ResNet50）在多个临床任务上的AUROC和C-index（补充材料提及）。
- **消融实验**：审计肿瘤检测模型时，按Integrated Gradients重要性降序禁用概念，观察预测翻转比例；随机顺序作为基线。

### 实验场景
1. **忠实度评估**：嵌入层（方差解释）和下游预测层（KL散度）。
2. **泛癌概念图谱**：14种癌症类型的概念激活热力图。
3. **模型审计**：CAMELYON16肿瘤检测模型，用Integrated Gradients归因于概念。
4. **EGFR突变预测审计**：发现钉突状形态学概念。
5. **伪影去除**：训练L1逻辑回归识别伪影概念，干扰后恢复敏感度。
6. **虚拟TIL试验**：增加淋巴细胞概念激活，用生存模型比较风险评分。

## 4. 资源与算力

- **SAE训练**：
  - 1个NVIDIA A40 GPU
  - 5个epoch，batch size 2048，学习率1e-4，Adam优化器
  - 总训练时间：**14小时10分钟**
- **Emb2Img训练**：
  - 4个NVIDIA A40 GPU（PyTorch DDP分布式训练，混合精度fp16）
  - 有效batch size 1024（每GPU batch size=16，梯度累积16步）
  - 16000优化步，学习率1e-4，AdamW，梯度裁剪1.0
  - 总训练时间：**5天22小时**
- **下游模型训练**：未明确给出具体GPU时间，仅提及使用单GPU（A40）和训练细节（如ABMIL，batch size=1 WSI，学习率1e-4）。

## 5. 实验数量与充分性

- **实验数量**：论文覆盖多个数据集、多个任务、多组对比实验。具体包括：
  - 忠实度评估（与PCA, k-means不同成分数对比，n=10000/100000测试样本，带置信区间）。
  - 14种癌症类型概念图谱（6812张WSI，每张WSI使用CONCH过滤肿瘤区域）。
  - EGFR突变关联统计（n=530患者，皮尔逊r检验）。
  - 伪影去除成功率（n=100人工检查，Wilson score CI）。
  - 伪影干扰实验：10次随机分裂训练/测试，报告均值与95%置信区间。
  - 虚拟TIL试验：n=76患者，Mann-Whitney U检验。
- **充分性评估**：
  - **充分**：在不同概念数量下比较重构性能；在多个下游任务上验证；有消融实验（概念重要性排名和翻转率）；有统计显著性检验；与人（病理学家）合作验证概念解释。
  - **公平性**：对比方法经典且合理（PCA, k-means）；下游任务基准包括多种FM；数据划分避免泄漏（按患者/幻灯片分割）。但未在非TCGA独立队列上验证泛癌概念图谱（仅部分下游任务使用了外部数据如CAMELYON16、EBRAINS）。
  - **局限**：主要依赖TCGA数据，可能存在机构偏差；病例数相对较小（EGFR突变预测n=530）；虚拟TIL试验依赖于生存模型的质量，未进行实际生物学验证。

## 6. 论文的主要结论与发现

- **PICASSO核心结论**：稀疏自编码器可高忠实度地将病理FM嵌入分解为人类可解释的稀疏概念（k=30解释>80%方差，下游KL散度<0.01）。
- **泛癌图谱**：首次系统构建了32种癌症类型的形态学概念图谱，揭示癌症类型相似性（如GBM与LGG，COAD与READ，UCEC与OV），并发现共享和特异概念。
- **模型审计**：通过概念级归因，揭示肿瘤检测模型主要依赖“肿瘤细胞密度”和“淋巴细胞-肿瘤细胞混合”等可解释特征，禁用前5个概念即可翻转>80%的预测。
- **新生物标志物发现**：EGFR突变预测模型依赖于“钉突状（hobnailing）上皮形态”，两个相关概念分别对应肿瘤-间质结构和恶性上皮特征，通过空间转录组学关联到CXCR4、ACE2等基因和免疫/迁移通路。
- **伪影抑制**：选择性关闭“组织折叠”概念，在反向相关测试集上将敏感度从0.612恢复至0.950，证明可有效减轻捷径学习。
- **虚拟临床试验**：通过增加淋巴细胞概念，模拟TIL治疗，生存模型预测的风险评分显著降低（Mann-Whitney U p=4.35e-31）。

## 7. 优点

- **方法论创新**：将稀疏自编码器（SAE）应用于病理嵌入，结合Emb2Img扩散模型实现概念级动态可视化，克服了静态示例解释不足的问题。
- **大规模泛癌训练**：120M+斑块，覆盖32种癌症，首次构建泛癌组织形态概念图谱，具有广泛的代表性。
- **多应用场景展示**：从模型审计、生物标志物发现、伪影去除到虚拟临床试验，展示了框架的通用性和实践价值。
- **临床验证意识**：与病理学家密切合作验证概念含义，确保概念映射到标准形态学术语。
- **开源可复现**：代码将在发表后公开，数据来自TCGA等公开资源，使用了SAELens等开源工具。

## 8. 不足与局限

- **概念抽象层次单一**：所有概念是原子级，而组织形态往往具有层次结构（如腺体-细胞-核），缺乏分层表示。
- **数据依赖性**：主要基于TCGA（美国机构），可能不反映全球病理多样性；外部验证仅部分任务使用非TCGA数据（CAMELYON16, EBRAINS）。
- **下游模型限制**：虚拟TIL试验和生存预测依赖于线性/基于注意力的ABMIL模型，其预测准确性有限，不能完全替代真实临床试验。
- **计算资源需求大**：Emb2Img训练5天以上，SAE训练14小时，仍需较多GPU资源。
- **伪影识别不够自动**：需训练辅助模型（L1逻辑回归）来筛选伪影概念，而非完全无监督。
- **缺乏前瞻性临床验证**：发现的生物标志物（如钉突状EGFR标志）未在独立队列或前瞻性研究中验证。

（完）
