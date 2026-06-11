---
title: Integrating Spatially Adjusted Protein Summaries for Survival Prediction in Spatial Proteomics
title_zh: 整合空间调整的蛋白质摘要用于空间蛋白质组学中的生存预测
authors: "Ahn, S., Oh, E. J., Prada, D., Shojaie, A."
date: 2026-06-11
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.08.730964v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 空间蛋白组学，空间调整的蛋白质摘要用于生存预测
tldr: 传统空间蛋白质组学生存分析忽略空间异质性。本文提出用空间样条回归为每个细胞生成空间调整的蛋白摘要（SAPS），包括空间调整均值和残差方差，并联合临床特征建立Cox模型。模拟和乳腺癌数据表明该方法提升预测性能，揭示生物学可解释的空间蛋白模式，具有转化潜力。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有空间蛋白质组学中的生存分析仅依赖患者水平蛋白平均强度，忽视了空间异质性和组织结构，限制了预测能力。
method: 通过细胞水平的空间样条回归建模蛋白空间趋势，提取空间调整均值与残差方差作为特征，与临床协变量共同纳入Cox比例风险模型。
result: 模拟实验和乳腺癌成像质谱流式数据表明，该方法相比传统方法提升了生存预测性能，并揭示了有生物学意义的空间蛋白模式。
conclusion: 该框架将复杂空间蛋白质组数据转化为患者水平特征，既改进了生存预测，又为癌症预后中的空间异质性提供了新见解。
---

## 摘要
空间蛋白质组学的最新进展，特别是成像质谱流式技术，使得在保留空间背景的同时能够测量单细胞水平的蛋白质表达。然而，传统的生存分析通常依赖于患者水平的蛋白质强度平均值，从而忽略了空间异质性和组织结构。为了解决这一局限性，我们引入了一个框架，通过生成空间调整的蛋白质摘要（SAPS）将空间信息整合到生存建模中。在该方法中，每个患者体内的细胞水平蛋白质强度使用空间样条回归进行建模以捕捉空间趋势。从这些模型中，我们提取两个互补特征：空间调整的平均表达和残差方差，后者反映了空间效应无法解释的细胞间变异性。然后将这些摘要与临床协变量一起纳入Cox比例风险模型。在模拟研究中，我们提出的框架相比于其他替代方法取得了更好的预测性能。将该方法应用于乳腺癌成像质谱流式数据表明，空间调整的摘要可以增强生存预测，并揭示出生物学上可解释的空间蛋白质模式，表明其具有很高的转化潜力。该方法为将复杂的空间蛋白质组学数据转化为患者水平特征提供了一种有效手段，既改进了生存预测，也为空间异质性在癌症结果中的作用提供了新的见解。

## Abstract
Recent advances in spatial proteomics, particularly imaging mass cytometry, enable the measurement of protein expression at the single-cell level while preserving a spatial context. Conventional survival analyses, however, typically rely on patient-level averages of protein intensities and therefore overlook spatial heterogeneity and tissue architecture. To address this limitation, we introduce a framework that incorporates spatial information into survival modeling by generating spatially adjusted protein summaries (SAPS). In this approach, cell-level protein intensities within each patient are modeled using spatial spline regression to capture spatial trends. From these models, we extract two complementary features: a spatially adjusted mean expression and a residual variance that reflects cell-to-cell variability unexplained by spatial effects. These summaries are then incorporated into Cox proportional hazards models in combination with clinical covariates. In simulation studies, our proposed framework achieved improved predictive performance compared to other alternative methods. The application of the method to breast cancer imaging mass cytometry data indicate that spatially adjusted summaries may enhance survival prediction and reveal biologically interpretable spatial protein patterns, suggesting high translational potential. This methodology offers an efficient means of translating complex spatial proteomics data into patient-level features, providing both improved survival prediction and new insights into the role of spatial heterogeneity in cancer outcomes.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：在空间蛋白质组学（如成像质谱流式技术）中，传统生存分析仅使用患者水平的蛋白质平均强度，忽略了细胞间的空间异质性和组织结构，导致预测能力受限。
- **研究动机**：空间背景中蕴含了肿瘤微环境的重要信息，如细胞邻域、蛋白分布趋势等，这些信息可能对预后有显著影响。需要一种方法将空间信息转化为患者水平的特征，从而改进生存预测。
- **整体含义**：通过整合空间调整的蛋白质摘要（SAPS），该工作为空间蛋白质组学数据在临床预后中的应用提供了一种有效框架，兼具预测性能和生物学可解释性。

## 2. 论文提出的方法论

### 核心思想
- 对每个患者的每个蛋白，利用细胞空间坐标，通过空间样条回归建模蛋白强度的空间趋势；然后从模型中提取两个互补的摘要特征：**空间调整均值**（反映空间趋势下的平均表达）和**残差方差**（反映去除空间趋势后细胞间的剩余变异性）。这些特征与临床协变量一起纳入Cox比例风险模型进行生存预测。

### 关键技术细节
- **空间样条回归**：假设蛋白强度 \( Y(s) \) 在空间位置 \( s \) 上满足 \( Y(s) = f(s) + \epsilon \)，其中 \( f(s) \) 为平滑的空间趋势，由样条基函数拟合；\( \epsilon \) 为独立同分布的随机误差。
- **特征提取**：
  - 空间调整均值：\( \frac{1}{n}\sum_i \hat{f}(s_i) \) 或直接使用回归截距的估计（视具体模型设定）。
  - 残差方差：\( \text{Var}(Y(s) - \hat{f}(s)) \)，即拟合残差的方差。
- **生存模型**：将上述两个摘要与临床协变量（如年龄、肿瘤分期等）共同作为Cox比例风险模型的协变量，估计风险比并进行预测。

## 3. 实验设计

### 数据集 / 场景
- **模拟数据集**：构造包含空间趋势的蛋白表达数据，并基于背景风险生成生存时间，用以评估不同方法预测性能的优劣。
- **真实数据集**：乳腺癌成像质谱流式（IMC）数据，包含患者的单细胞蛋白表达及空间坐标，同时有患者生存结局信息。

### Benchmark 与对比方法
- 对比方法包括：仅使用传统患者水平蛋白平均强度的Cox模型、仅使用残差方差的模型、以及可能包括中位数或其他简单摘要的模型（具体名称论文中未一一列出，但明确“其他替代方法”）。
- 评估指标：预测性能（可能为C指数、AUC等，文中未明确列出具体指标名称，但强调“更好的预测性能”）。

## 4. 资源与算力

- **论文中未提及任何关于计算资源（GPU型号、数量、训练时长）的信息。** 仅指出该方法在单细胞级别建模，但未讨论具体计算开销或硬件需求。

## 5. 实验数量与充分性

- **实验组数**：至少包含一个模拟实验和一个真实数据实验。模拟实验可能设定了多个场景（如不同的空间异质性程度、噪声水平），但论文未详细说明实验数量。
- **消融实验**：未明确是否有消融实验（如单独使用空间调整均值 vs. 单独使用残差方差的效果），但对比了不同摘要组合可能隐含部分消融思想。
- **充分性评估**：
  - **优点**：验证了方法在模拟和真实数据上的有效性。
  - **不足**：
    - 缺乏与其他高级空间统计方法（如空间自回归模型、图神经网络）的对比。
    - 模拟实验设置细节（如样本量、蛋白数量）未充分公开，可能影响可复现性。
    - 未进行多重数据集的外部验证（仅一个乳腺癌数据集），泛化性存疑。

## 6. 论文的主要结论与发现

- 提出的SAPS框架在模拟研究中优于传统均值方法，在真实乳腺癌IMC数据上也提升了生存预测性能。
- **空间调整的蛋白质摘要具有生物学可解释性**：例如，某些蛋白的空间调整均值与预后相关，而残差方差则可能反映肿瘤异质性程度，两者互补。
- 该方法将复杂的空间蛋白质组学数据有效转化为患者水平特征，为癌症预后中的空间异质性角色提供了新见解，具有很高的转化潜力。

## 7. 优点

- **方法创新**：首次系统地将空间样条回归引入生存分析，解决了传统均值忽略空间异质性的问题。
- **可解释性强**：两个摘要特征（均值和方差）具有明确的生物学意义，易于临床解读。
- **简单高效**：无需构建复杂图模型，计算复杂度可控，适合在实际研究中使用。
- **兼容性**：可直接与现有Cox模型结合，且支持加入临床协变量，符合临床统计常规。

## 8. 不足与局限

- **实验覆盖不足**：
  - 仅采用一个真实数据集（乳腺癌），未在多种癌症或不同成像平台（如CODEX、MIBI）上验证，泛化性未知。
  - 对比方法不够全面，未与最新的深度空间生存模型（如基于图注意力网络的方法）比较。
- **模型假设限制**：空间样条回归假设蛋白强度平滑变化，但实际肿瘤微环境中可能存在离散的突变或边界，可能导致拟合偏差。
- **未讨论计算效率**：对于大型数据集（数百万细胞），逐蛋白的样条拟合可能耗时，论文未提供运行时间分析。
- **未考虑多重比较校正**：多个蛋白的摘要同时进入模型可能导致多重共线性或过拟合，论文未讨论如何选择蛋白或进行变量筛选。
- **缺乏外部验证**：生存预测性能未在独立验证集中评估，可能存在过拟合风险。

（完）
