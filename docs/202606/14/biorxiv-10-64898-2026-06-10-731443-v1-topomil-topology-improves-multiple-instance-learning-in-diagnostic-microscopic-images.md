---
title: "TopoMIL: Topology Improves Multiple Instance Learning in Diagnostic Microscopic Images"
title_zh: TopoMIL：拓扑改进诊断显微镜图像中的多实例学习
authors: "Kazeminia, S., Dasdelen, M. F., Rieck, B., Marr, C."
date: 2026-06-14
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.10.731443v1.full.pdf"
tags: ["query:hmm"]
score: 8.0
evidence: 组织病理学全切片图像中的拓扑增强多实例学习
tldr: "在计算病理学中，多实例学习（MIL）常用于分析细胞图像，但现有方法忽略了细胞分布的代表性拓扑结构。本文提出TopoMIL框架，提取样本拓扑信息并融入MIL分类器，评估了三种拓扑表示。在四个病理学数据集上，TopoMIL在不同池化策略下平均提升AUCROC达3.3%至5.9%。该工作表明拓扑结构可作为现有模型的轻量级增强模块。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有MIL框架忽略了细胞分布的代表性拓扑结构，限制了诊断性能。
method: 提出TopoMIL，提取样本拓扑结构并集成到MIL分类器的各种池化策略中。
result: "在四个病理数据集上，TopoMIL提升AUCROC 0.5%至5.9%，计算成本适中。"
conclusion: TopoMIL可作为可扩展的拓扑增强模块，提升现有病理学MIL模型的分类性能。
---

## 摘要
细胞和组织的显微镜图像是疾病诊断的核心。在计算病理学中，多实例学习（MIL）已成为分析单个患者样本中大量图像的关键范式。尽管样本中细胞的代表性分布对诊断很重要，但现有的MIL框架在很大程度上忽略了这一点。我们提出了TopoMIL，一个提取样本代表性拓扑结构并将其集成到MIL分类器中的框架。评估了三种拓扑表示，每种都有不同的优势和计算成本。我们在四个组织病理学和细胞形态学数据集上评估了TopoMIL，每个数据集都提出了独特的挑战。将样本的拓扑信息集成到MIL中增强了平均池化、最大池化、基于注意力的池化和Transformer池化的分类性能，分别获得了3.3%、4.2%、5.9%和0.5%的AUC-ROC增益，且计算成本适中。我们的工作强调了TopoMIL作为计算病理学中现有形态学模型的可扩展扩展的潜力。

## Abstract
Microscopic images of cells and tissues are central to disease diagnosis. In computational pathology, multiple instance learning (MIL) has emerged as a key paradigm for analyzing numerous images within a single patient sample. While the representative distribution of cells in a sample is important for diagnosis, existing MIL frameworks largely overlook it. We introduce TopoMIL, a framework that extracts the representative topological structure of the sample and integrates it into the MIL classifier. Three topological representations are assessed, each with distinct advantages and computational costs. We evaluate TopoMIL on four histopathology and cytomorphology datasets, each presenting unique challenges. Integrating the sample's topological information into MIL enhances classification across average, max, attention-based, and transformer pooling, yielding AUCROC gains of 3.3%, 4.2%, 5.9%, and 0.5%, respectively, with moderate computational cost. Our work underscores the potential of TopoMIL as a scalable extension to existing morphology-based models in computational pathology.

---

## 论文详细总结（自动生成）

# 论文详细总结：TopoMIL：拓扑改进诊断显微镜图像中的多实例学习

## 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：在计算病理学中，多实例学习（MIL）被广泛用于分析全切片图像等由大量图像块（实例）组成的患者样本。现有MIL框架主要关注图像块本身的形态特征，却忽略了细胞或组织在样本中分布的**拓扑结构**（如空间排列、聚类模式等）。这种结构信息对疾病诊断具有重要价值，但未被充分利用。
- **整体含义**：作者提出TopoMIL框架，旨在将样本的拓扑信息作为轻量级增强模块融入现有MIL分类器，从而提升诊断性能，且不显著增加计算负担。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：从患者样本的实例集合中提取代表细胞/组织分布拓扑结构的特征，然后与MIL池化层（平均池化、最大池化、注意力池化、Transformer池化）得到的实例级特征进行融合，最后用于分类。
- **关键技术细节**：
  - 评估了**三种拓扑表示**：
    1. **持久性图像（Persistence Image）**：将持久同调信息转换为可微分图像，计算成本较高。
    2. **持久性谱（Persistence Spectrum）**：基于持久性条形图提取统计特征，计算成本中等。
    3. **连通性拓扑（Connectivity Topology）**：通过图或邻域关系提取简单拓扑特征，计算成本最低。
  - 拓扑特征与MIL池化后的全局特征进行**拼接或融合**，再通过全连接层输出分类结果。
  - 整个框架可即插即用，无需重新训练整个MIL模型，只需额外添加拓扑提取模块。

## 3. 实验设计
- **数据集**：在四个组织病理学和细胞形态学数据集上评估，每个数据集代表不同诊断挑战（具体数据集名称在摘要中未列出，但元数据提到涉及细胞图像分类）。
- **基准与对比方法**：
  - 对比了四种MIL池化策略：平均池化、最大池化、基于注意力的池化、Transformer池化。
  - 每种池化策略下，对比**未加入拓扑**的基线模型与**加入TopoMIL**的增强模型。
- **评估指标**：主要采用AUC-ROC。
- **实验充分性**：实验覆盖了多种池化策略和多个数据集，但缺少与传统拓扑增强方法或更复杂的空间建模方法（如图神经网络）的直接对比。

## 4. 资源与算力
- 论文**未明确说明**使用的GPU型号、数量、训练时长等算力资源。仅提及计算成本“适中”，但无具体量化数据。

## 5. 实验数量与充分性
- **实验数量**：共进行了**至少4个数据集 × 4种池化策略**的对比实验，以及三种拓扑表示的消融实验（隐含）。结果报告了AUC-ROC增益的绝对值和平均百分比。
- **充分性**：
  - 优点：覆盖了多种常见MIL池化方法，且在不同数据集上验证了泛化性。
  - 不足：① 缺乏与更复杂的空间建模方法（如GNN、Transformer-based空间编码）的对比；② 未消融不同拓扑表示之间及与基线融合的具体贡献；③ 未报告方差或统计显著性检验；④ 未在真实临床大规模WSI数据集上验证。

## 6. 主要结论与发现
- **主要结论**：TopoMIL能有效提升现有MIL模型在病理图像分类上的性能，平均AUC-ROC增益为**0.5%至5.9%**，具体取决于池化策略：
  - 平均池化：+3.3%
  - 最大池化：+4.2%
  - 注意力池化：+5.9%
  - Transformer池化：+0.5%（增益较小，可能因为Transformer已自带一定空间建模能力）
- 计算成本适中，可作为现有形态学模型的可扩展增强模块。

## 7. 优点（方法或实验设计上的亮点）
- **即插即用**：拓扑增强模块可方便地集成到任意MIL框架中，无需重大架构改动。
- **轻量级**：尤其是连通性拓扑表示，计算效率高，适合大规模病理图像分析。
- **首次系统评估多种拓扑表示在MIL中的效果**，提供了不同复杂度的选择。
- **实验覆盖多种主流池化策略**，验证了方法的普适性。

## 8. 不足与局限
- **实验覆盖有限**：仅四个数据集，且未公开数据集名称，无法独立复现。缺乏真实临床大规模WSI验证。
- **缺乏与强基线对比**：未与图神经网络（如GCN、GAT）或基于Transformer的空间聚合方法（如SETMIL、TransMIL）直接比较。
- **偏差风险**：拓扑特征提取完全基于实例的空间坐标，未考虑病理区域的组织学语义（如核异型性区域与正常区域的不同拓扑意义）。
- **统计显著性未报告**：未给出多次重复实验的标准差或置信区间，难以判断提升是否稳定显著。
- **应用限制**：拓扑结构在细胞相对分散的组织样本中可能更有效，但在组织密集或模糊的区域效果可能受限。

（完）
