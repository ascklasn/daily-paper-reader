---
title: Homologous recombination deficiency prediction from whole slide images using label refinement and foundation-model benchmarking in ovarian cancer
title_zh: 基于标签精炼和基础模型基准测试的卵巢癌全切片图像同源重组缺陷预测
authors: "Shah, N. A., Sarwar, M., Ullah, E."
date: 2026-06-30
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.25.734452v1.full.pdf"
tags: ["query:hmm"]
score: 9.0
evidence: 利用标签精炼和基础模型从全切片图像预测同源重组缺陷
tldr: "卵巢癌中HRD状态预测对PARPi治疗至关重要，但公开数据缺乏完整标签。本研究基于TCGA-OV冷冻切片H&E WSI，使用标签精炼（加入BRCA1甲基化）和多种病理基础模型（UNI2-h等）进行注意力多实例学习，发现WSI中包含与HRD相关的微弱形态信号，但AUROC仅0.634，缺乏临床验证，因此作为概念验证框架。"
source: biorxiv
selection_source: fresh_fetch
motivation: "评估H&E切片能否预测卵巢癌同源重组缺陷，为计算病理学提供可重复的基准。"
method: 使用TCGA-OV冷冻切片WSI，对比初始和甲基化增强的HRD标签，采用多种基础模型提取特征，通过患者级注意力多实例学习进行预测。
result: UNI2-h在精炼标签下AUROC 0.634，优于其他模型和临床基线，但预测性能有限。
conclusion: "H&E WSI存在微弱HRD信号，但AUROC仅0.63，缺乏临床标准标签，仅为概念验证框架。"
---

## 摘要
背景同源重组缺陷（HRD）在高级别浆液性卵巢癌（HGSOC）中具有临床重要性，特别是因其与铂类敏感性和聚（ADP-核糖）聚合酶抑制剂（PARPi）治疗的获益相关。然而，公共数据集很少包含诊断性苏木精和伊红（H&E）全切片图像（WSI）、经过验证的临床HRD检测结果、基因组瘢痕评分、BRCA1启动子甲基化数据以及治疗反应结果的完整组合。这为旨在从常规组织学中开发临床可解释的HRD或PARPi反应模型的计算病理学研究造成了重大障碍。

目的我们进行了一项探索性、受泄漏控制的计算病理学基准测试研究，以评估来自TCGA-OV的H&E WSI是否包含与科研级分子HRD标签相关的可测量形态学信号，以及标签精炼和病理学基础模型嵌入是否改变了预测性能。

方法我们组建了一个冷冻原发性TCGA-OV WSI队列，包括来自316名患者的717张组织切片/生物样本切片。由于与冷冻原发性队列的患者完全重叠，我们在模型选择中排除了诊断性FFPE DX切片。评估了两个HRD标签：一个基于BRCA/HR基因突变证据的初始仅突变分子标签，以及一个额外整合了BRCA1启动子甲基化的精炼甲基化增强分子标签。使用ResNet50、UNI、CONCH、Virchow2、Phikon-v2和UNI2-h编码器进行特征提取。采用基于注意力的多实例学习（ABMIL）进行以患者为袋的建模。评估采用患者级别的分组5折×5次重复分层交叉验证，共25折，bootstrap置信区间，并控制患者级别的泄漏。

结果初始仅突变标签将78名患者分类为阳性，238名阴性。精炼甲基化增强标签额外恢复了33例阳性，得到111例阳性和205例阴性患者。使用UNI2-h特征的患者级别ABMIL在精炼标签上表现最佳，AUROC为0.634（95% CI 0.571-0.698），AUPRC为0.468（95% CI 0.390-0.562），平衡准确率为0.597，敏感性为0.532，特异性为0.663，F1分数为0.494，Brier分数为0.233。校准阈值为0.512，得到TN=136，FP=69，FN=52，TP=59。比较模型表现出较低的判别力，包括使用初始标签的UNI2-h（AUROC 0.628）、Phikon-v2精炼（0.582）、Virchow2精炼（0.582）、CONCH初始（0.587）、ResNet50精炼（0.570）以及临床基线（AUROC 0.54-0.57）。

结论TCGA-OV的H&E WSI包含与科研级分子HRD状态相关的适度但可重复的形态学信号。然而，AUROC约为0.63、缺乏临床HRD检测标签、实施工作流程中缺少基因组瘢痕终点以及缺乏PARPi/铂类反应靶点，阻碍了临床解释。本研究应被视为概念验证基准框架和方法学基础，用于未来在临床策划的PARPi反应队列中进行基于H&E的预测建模。

## Abstract
BackgroundHomologous recombination deficiency (HRD) is clinically imperative in high-grade serous ovarian carcinoma (HGSOC), particularly because of its association with platinum sensitivity and benefit from poly(ADP-ribose) polymerase inhibitor (PARPi) therapy. However, public datasets rarely contain a complete combination of diagnostic haematoxylin and eosin (H&E) whole-slide images (WSIs), validated clinical HRD assay results, genomic scar scores, BRCA1 promoter methylation data, and treatment-response outcomes. This creates a major barrier for computational pathology studies seeking to develop clinically interpretable models of HRD or PARPi response from routine histology.

ObjectiveWe performed an exploratory, leakage-controlled computational pathology benchmarking study to evaluate whether H&E WSIs from TCGA-OV contain a measurable morphology-linked signal associated with research-grade molecular HRD labels, and whether label refinement and pathology foundation-model embeddings alter predictive performance.

MethodsWe assembled a frozen-primary TCGA-OV WSI cohort comprising 717 tissue-section/biospecimen slides from 316 patients. Diagnostic FFPE DX slides were excluded from model selection because of complete patient overlap with the frozen-primary cohort. Two HRD labels were evaluated: an initial mutation-only molecular label based on BRCA/HR-gene mutation evidence, and a refined methylation-enhanced molecular label that additionally incorporated BRCA1 promoter methylation. Feature extraction was performed using ResNet50, UNI, CONCH, Virchow2, Phikon-v2, and UNI2-h encoders. Patient-level attention-based multiple instance learning (ABMIL) was used with patient-as-bag modelling. Evaluation used patient-level grouped 5-fold x 5-repeat stratified cross-validation, with 25 folds total, bootstrap confidence intervals, and patient-level leakage control.

ResultsThe initial mutation-only label classified 78 patients as positive and 238 as negative. The refined methylation-enhanced label recovered 33 additional positives, resulting in 111 positive and 205 negative patients. Patient-level ABMIL using UNI2-h features achieved the strongest performance for the refined label, with AUROC 0.634 (95% CI 0.571-0.698), AUPRC 0.468 (95% CI 0.390-0.562), balanced accuracy 0.597, sensitivity 0.532, specificity 0.663, F1 score 0.494, and Brier score 0.233. The calibrated threshold was 0.512, yielding TN=136, FP=69, FN=52, and TP=59. Comparative models showed lower discrimination, including UNI2-h with the initial label (AUROC 0.628), Phikon-v2 refined (0.582), Virchow2 refined (0.582), CONCH initial (0.587), ResNet50 refined (0.570), and clinical baselines (AUROC 0.54-0.57).

ConclusionsTCGA-OV H&E WSIs contain a modest but reproducible morphology-linked signal associated with research-grade molecular HRD status. However, the AUROC around 0.63, absence of clinical HRD assay labels, lack of genomic scar endpoints in the implemented workflow, and absence of PARPi/platinum response targets prevent clinical interpretation. This study should be interpreted as a proof-of-concept benchmarking framework and methodological foundation for future H&E-based predictive modelling in clinically curated PARPi response cohorts.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：同源重组缺陷（HRD）是高级别浆液性卵巢癌（HGSOC）的重要生物标志物，与铂类化疗敏感性和PARP抑制剂（PARPi）疗效密切相关。然而，公开数据集（如TCGA-OV）缺乏完整的临床HRD检测结果、基因组瘢痕评分、BRCA1启动子甲基化数据及治疗反应标签，阻碍了从常规H&E全切片图像（WSI）直接构建临床可解释的预测模型。
- **整体含义**：本文旨在评估TCGA-OV的冷冻切片H&E WSI中是否包含与科研级分子HRD标签相关的微弱形态学信号，并验证标签精炼（加入BRCA1甲基化）及病理基础模型特征提取能否提升预测性能。研究定位为概念验证基准框架，而非临床诊断工具。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：采用患者级的弱监督学习范式，通过注意力多实例学习（ABMIL）聚合WSI的斑块特征，预测HRD状态。重点在于标签精炼（从仅突变标签扩展到包含甲基化证据）与多种病理基础模型的横向对比。
- **关键技术细节**：
  - **标签构建**：初始标签基于BRCA1/2及其他HR基因突变证据（78阳性/238阴性）。精炼标签额外整合BRCA1启动子甲基化（β值≥0.30），得到111阳性/205阴性。
  - **特征提取**：使用6种编码器：ResNet50（ImageNet预训练，2048维）、UNI（1024维）、CONCH（512维）、Virchow2（2560维）、Phikon-v2（1024维）、UNI2-h（1536维）。所有编码器输出冻结特征。
  - **模型架构**：患者级ABMIL，每个患者的所有可用冷冻切片斑块特征构成一个袋，通过注意力聚合输出患者级概率。
  - **泄漏控制**：严格按患者ID分组，采用5折×5次重复分层交叉验证（共25折），确保同一患者的任何切片不跨训练/测试集。
- **算法流程**（文字说明）：
  1. WSI预处理：组织掩膜、切片坐标生成、斑块提取。
  2. 特征提取：每个编码器独立生成HDF5特征存储。
  3. 构建患者级袋：收集同一患者所有斑块特征。
  4. 训练ABMIL模型：最小化二元交叉熵损失，使用验证集校准阈值。
  5. 评估：输出患者级OOF预测，计算AUROC、AUPRC等指标，并用bootstrap估计置信区间。

### 3. 实验设计

- **数据集**：TCGA-OV冷冻原发性组织切片/生物样本（717张WSI，来自316名患者）。排除诊断性FFPE DX切片（因患者完全重叠，不能作为独立验证集）。
- **基准**：
  - **标签对比**：初始仅突变标签 vs. 精炼甲基化增强标签。
  - **编码器对比**：ResNet50、UNI、CONCH、Virchow2、Phikon-v2、UNI2-h。
  - **临床基线**：逻辑回归（LR）和随机森林（RF）基于临床特征（如分期、分级等）。
- **对比方法**：共6种编码器×2种标签组合（共12组ABMIL模型），加上2种临床基线。主要报告UNI2-h在精炼标签下的最佳结果。
- **评估指标**：AUROC（主要判别指标）、AUPRC、平衡准确率、敏感性、特异性、F1分数、Brier分数、混淆矩阵。

### 4. 资源与算力

- **文中未明确说明**使用的GPU型号、数量、训练时长等具体算力信息。仅提到特征提取和模型训练在标准计算环境下完成，但未提供硬件细节。

### 5. 实验数量与充分性

- **实验数量**：
  - 6种编码器×2种标签 = 12组ABMIL模型，每组采用25折交叉验证（5×5重复）。
  - 临床基线2种（LR, RF）。
  - 总计14组对比实验。此外包含标签精炼前后的队列组成分析。
- **充分性**：
  - **优点**：严格的泄漏控制（患者级分组）、重复交叉验证+bootstrap CI增加了可靠性；对比了多种主流基础模型，覆盖了从传统ResNet到最新UNI2-h；标签精炼分析提供了生物学合理性。
  - **不足**：仅使用TCGA-OV单一数据集，无外部验证；数据集规模较小（n=316）；未进行超参数调优或端到端训练；未包含注意力热图的可视化分析或病理医生回顾。

### 6. 论文的主要结论与发现

- **主要发现**：TCGA-OV的H&E WSI中存在与科研级HRD分子标签相关的微弱但可重复的形态学信号。最佳模型（UNI2-h + 精炼标签）AUROC = 0.634（95% CI 0.571-0.698），AUPRC = 0.468（高于无技能基线0.351）。
- **标签精炼效果**：加入BRCA1甲基化使阳性率从24.7%升至35.1%，改变了AUPRC基线，且小幅提升AUROC（0.628→0.634）。
- **编码器对比**：UNI2-h优于其他基础模型，Phikon-v2、Virchow2、CONCH、ResNet50及临床基线均低于0.63。
- **临床解释限制**：AUROC仅0.63，远低于临床部署标准；缺乏真实HRD检测标签、基因组瘢痕评分及PARPi/铂类反应终点，无法支持临床决策。本文定位为概念验证基准。

### 7. 优点

- **严格的泄漏控制**：采用患者级分组交叉验证，避免同一患者多张切片造成的泄漏，提高结果可信度。
- **系统性的基础模型基准**：对比6种编码器（包括最新UNI2-h），提供可重复的基准结果。
- **标签精炼分析**：展示如何通过整合甲基化数据改进标签质量，类不平衡变化对AUPRC的影响，为未来研究提供方法学参考。
- **透明报告**：提供完整混淆矩阵、校准阈值、bootstrap置信区间，承认性能有限而非夸大结果。
- **开源友好**：特征提取脚本、标签文件、模型报告可获取，便于复现。

### 8. 不足与局限

- **标签局限**：科研级分子标签（仅基于突变+甲基化）不能替代临床验证的HRD检测（如LOH/TAI/LST复合评分），可能导致假阳性/假阴性。
- **缺乏外部验证**：仅使用TCGA-OV一个队列，且诊断性DX切片因患者重叠被排除，无法评估模型对常规诊断切片的泛化性。
- **性能有限**：AUROC仅0.63，敏感性0.53，特异性0.66，不具备临床实用性。
- **计算细节缺失**：未报告GPU、训练时间等算力资源，影响可复现性的完整评估。
- **未进行注意力可视化**：未保存折叠检查点，无法生成热图进行病理学定性分析。
- **无治疗反应终点**：TCGA-OV缺乏PARPi/铂类反应标签，无法建立治疗反应预测模型。
- **特征提取而非端到端训练**：使用冻结特征可能限制模型发现更细微的形态学模式。
- **样本量中等**：仅316名患者，可能不足以充分训练复杂的弱监督模型。

（完）
