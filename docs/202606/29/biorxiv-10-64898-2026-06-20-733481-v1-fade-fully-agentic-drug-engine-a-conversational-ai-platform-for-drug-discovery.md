---
title: "F.A.D.E. (Fully Agentic Drug Engine): A Conversational AI Platform for Drug Discovery"
title_zh: F.A.D.E.（全自主药物引擎）：用于药物发现的对话式AI平台
authors: "Kantorow, J., Mani, N., Mohanraj, N. R., Zong, X."
date: 2026-06-25
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.20.733481v1.full.pdf"
tags: ["query:agent"]
score: 8.0
evidence: 多智能体药物发现平台自动化工作流
tldr: 药物发现成本高昂、周期长、失败率高，现有计算流水线碎片化且需跨学科专长。F.A.D.E.提出多智能体开源平台，通过自然语言输入自动生成候选药物，采用三分支层次架构，根据蛋白质结构数据可用性自适应选择分支，集成结构预测、口袋检测、等变扩散配体生成和亲和力估计。在EGFR和CRBP1靶点验证，生成候选药物类药性显著优于参考配体。该平台降低了计算药物发现的专业门槛。
source: biorxiv
selection_source: fresh_fetch
motivation: "药物发现平均成本超23亿美元、周期超十年且临床试验失败率超90%，现有计算工具碎片化且需深度跨学科专长。"
method: 提出F.A.D.E.多智能体平台，采用三分支层次架构，根据靶点结构数据可用性自适应选择，集成AlphaFold预测、口袋检测、等变扩散配体生成和亲和力评估。
result: 在EGFR靶点生成候选药物QED达0.85（参考配体0.46），在CRBP1靶点同样生成可成药物化合物，验证了跨靶点适用性。
conclusion: F.A.D.E.从自然语言输入即可可靠生成类药候选化合物，显著降低了计算药物发现的使用门槛。
---

## 摘要
药物发现仍然是制药管线中成本最高、时间最密集的工作之一，每种药物的平均开发成本超过23亿美元，时间跨度超过十年，临床试验中的失败率超过90%。虽然计算方法扩大了可搜索的化学空间，但目前的管线仍然分散，并且对于缺乏深厚跨学科专业知识的研究人员来说基本无法使用。这里我们提出F.A.D.E.（全自主药物引擎），一个多智能体、开源平台，将自然语言查询转化为潜在的候选药物，显著降低了先进计算药物发现的专业知识门槛。F.A.D.E.采用三分支分层架构，能够适应任何蛋白质靶点可用的结构数据水平，将结构预测、结合口袋检测、基于等变扩散的从头配体生成以及结合亲和力估计整合到一个全自动管线中。我们在两个结构不同的靶点上验证了F.A.D.E.：表皮生长因子受体激酶结构域（EGFR），一个成熟的肿瘤靶点，以及细胞视黄醇结合蛋白1（CRBP1），一个参与类视黄醇代谢的脂质结合蛋白。对于EGFR，我们生成的候选药物QED得分为0.85，而共结晶参考配体为0.46，显示出预测药物相似性的显著改善。两个靶点的结果均证实，F.A.D.E.能够从简单的自然语言输入中可靠地生成化学可处理、具有药物相似性的先导化合物，覆盖不同蛋白质类别。

## Abstract
Drug discovery remains one of the costliest and most time-intensive endeavors in the pharmaceutical pipeline, with average development costs exceeding $2.3 billion per drug, timelines spanning more than a decade, and attrition rates above 90% in clinical trials. While computational methods have expanded the searchable chemical space, current pipelines remain fragmented and largely inaccessible to researchers without deep interdisciplinary expertise. Here we present F.A.D.E. (Fully Agentic Drug Engine), a multi-agent, open-source platform that converts natural language queries into potential drug candidates, substantially lowering the expertise barrier to advanced computational drug discovery. F.A.D.E. employs a three-branch hierarchical architecture that adapts to the level of available structural data for any protein target, integrating structure prediction, binding pocket detection, equivariant diffusion-based de novo ligand generation, and binding affinity estimation into a single automated pipeline. We validate F.A.D.E. on two structurally distinct targets: the epidermal growth factor receptor kinase domain (EGFR), a well-established oncology target, and cellular retinol-binding protein 1 (CRBP1), a lipid-binding protein involved in retinoid metabolism. For EGFR, our generated candidates achieved QED scores of 0.85 compared to 0.46 for the co-crystallised reference ligand, demonstrating marked improvement in predicted drug-likeness. Results across both targets confirm that F.A.D.E. can reliably generate chemically tractable, drug-like hit compounds across diverse protein classes from simple natural language input.

---

## 论文详细总结（自动生成）

## 1. 核心问题与整体含义（研究动机与背景）
- **问题**：传统药物发现成本极高（平均超23亿美元/药）、周期长（>10年）、临床失败率超90%；
- **动机**：现有计算工具碎片化，需要深厚跨学科专业知识，普通研究人员难以使用；
- **意义**：F.A.D.E. 旨在将自然语言输入直接转化为候选药物，大幅降低计算药物发现的专业门槛，加速早期研发。

## 2. 方法论：核心思想、关键技术细节、算法流程
- **核心思想**：构建一个多智能体、开源平台，采用**三分支分层架构**，根据靶点蛋白质的结构数据可用性自适应选择分支，实现全自动管线。
- **关键技术细节**：
  - 结构预测（如 AlphaFold）
  - 结合口袋检测
  - 基于等变扩散的从头配体生成（equivariant diffusion-based de novo ligand generation）
  - 结合亲和力估计（binding affinity estimation）
- **算法流程**（文字说明）：
  1. 用户输入自然语言描述（如靶点名称）；
  2. 根据蛋白质结构数据可用性，选择三个分支之一：若已有实验结构 → 使用口袋检测与直接配体生成；若有序列无结构 → 先用AlphaFold预测结构再执行后续；若仅有序列信息 → 使用同源建模或序列特征预测；
  3. 通过等变扩散模型生成候选配体；
  4. 评估结合亲和力与药物相似性（如QED分数）；
  5. 输出候选药物列表。

## 3. 实验设计：数据集、场景、基准与对比方法
- **数据集/靶点**：两个结构不同的蛋白质靶点
  - **EGFR**（表皮生长因子受体激酶结构域）：成熟肿瘤靶点
  - **CRBP1**（细胞视黄醇结合蛋白1）：脂质结合蛋白，参与类视黄醇代谢
- **基准**：以共结晶参考配体为基准（EGFR参考配体QED=0.46）
- **对比方法**：未明确列出其他方法对比，仅展示本平台生成结果与参考配体相比的QED提升（0.85 vs 0.46）
- **场景**：跨蛋白质类别（激酶 vs 脂质结合蛋白）验证通用性

## 4. 资源与算力
- **文中未明确说明**使用的GPU型号、数量、训练时长等算力信息。

## 5. 实验数量与充分性
- **实验数量**：仅两个靶点验证，每个靶点生成候选化合物并计算QED分数。未提及消融实验或大规模测试。
- **充分性**：实验数量较少，仅初步证明概念可行；缺乏规模化的benchmark对比、多样性测试、消融研究或对扩散模型本身性能的评估。客观性和公平性有限，因为未与其他已有方法（如经典对接、其他生成模型）进行直接比较。

## 6. 主要结论与发现
- F.A.D.E. 能从简单自然语言输入可靠地生成化学可处理、具有药物相似性的先导化合物。
- 在EGFR靶点上，生成候选药物QED达0.85（参考配体0.46）；在CRBP1靶点上同样生成可成药化合物，验证了跨靶点适用性。
- 显著降低了计算药物发现的使用门槛。

## 7. 优点
- **多智能体自动化**：将结构预测、口袋检测、生成与评估整合成端到端管线，简化用户操作；
- **自适应架构**：根据已有结构数据选择分支，灵活适应不同靶点信息水平；
- **开源平台**：提高可复现性与社区应用潜力；
- **跨靶点验证**：选择两个结构迥异的靶点（激酶、脂质结合蛋白）泛化性有意义；
- **药物相似性显著提升**：生成配体QED远高于参考配体（0.85 vs 0.46），体现实用性潜力。

## 8. 不足与局限
- **实验覆盖不足**：仅两个靶点，缺乏大规模多样性验证（如不同蛋白家族、不同结合位点特征）；
- **缺乏对比**：未与其他主流方法（如AutoDock Vina、DiffDock、相关ML生成方法）进行系统比较，无法判断相对优势；
- **未讨论失败案例**：未分析生成配体是否都能有效结合、合成可行性如何；
- **未提供算力与效率信息**：无法评估实际运行成本；
- **验证指标单一**：主要依靠QED，缺乏结合亲和力实测或自由能预测等其他指标；
- **潜在偏差风险**：QED分数提升可能源于扩散模型偏好简单分子，但未必转化为更高的生物活性或更低的毒性；
- **应用限制**：目前仍为学术验证，需临床前进一步验证。

（完）
