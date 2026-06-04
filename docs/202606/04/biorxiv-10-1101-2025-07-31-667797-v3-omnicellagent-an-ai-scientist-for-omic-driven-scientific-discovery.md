---
title: "OmniCellAgent: An AI Scientist for Omic-Driven Scientific Discovery"
title_zh: OmniCellAgent：面向组学驱动的科学发现的AI科学家
authors: "Huang, D., Li, H., Li, W., Zhang, H., Xu, T., Lu, Y., Fang, K., Xu, Z., Chen, J., Dickson, P., Sardiello, M., Buchser, W., Cooper, J. D., Cruchaga, C., Eghtesady, P., Li, G., Goedegebuure, P., DeNardo, D., Ding, L., Fields, R. C., Zhan, M., Miller, J. P., Province, M., Chen, Y., Payne, P., Li, F."
date: 2026-06-02
pdf: "https://www.biorxiv.org/content/10.1101/2025.07.31.667797v3.full.pdf"
tags: ["query:agent"]
score: 9.0
evidence: 面向组学驱动科学发现的多智能体AI框架
tldr: 生物医学发现中，识别相关组学数据集并利用先验知识解释结果对产生新假设至关重要，但现有AI代理需用户预定义数据集，过程耗时且对非计算研究者不友好。本文提出OmniCellAgent多智能体框架，基于大规模单细胞RNA-seq资源，自主检索整合跨组织条件的疾病与对照数据集，并集成先验知识代理和专家代理进行系统目标注释与下游解释。在多个疾病评估中，该框架能识别相关数据集、优先排序有生物学意义的目标并生成证据支持的假设。结果表明，多智能体AI可降低组学驱动发现障碍，加速精准医学假设生成。
source: biorxiv
selection_source: fresh_fetch
motivation: 针对现有AI代理需要用户预定义疾病特定数据集、过程耗时且对非计算研究者不友好的问题。
method: 提出OmniCellAgent多智能体框架，基于大规模单细胞RNA-seq数据自主检索整合数据集，集成先验知识代理和领域专家代理进行目标注释与解释。
result: 在多个疾病设置中，OmniCellAgent成功识别相关数据集、优先排序生物学有意义目标并生成证据支持的假设。
conclusion: 多智能体AI系统可降低组学驱动发现的门槛，加速精准医学中的假设生成。
---

## 摘要
在生物医学科学发现中，识别相关的组学数据集并利用来自数据库和文献的先验知识解释分析结果，对于产生新假设至关重要。尽管最近的AI代理支持自动化组学分析和文献检索，但它们通常需要用户预先定义和整理疾病特定数据集，这一过程仍然具有挑战性且耗时，尤其对于非计算研究人员而言。在此，我们提出OmniCellAgent，这是一个基于大规模单细胞RNA测序（scRNA-seq）资源构建的多智能体AI框架，能够自主检索、整合和分析跨组织与疾病状态的多种细胞类型相关的疾病及对照数据集。此外，OmniCellAgent整合了一个生物医学先验知识代理，用于利用 curated 的数据库和文献进行系统靶标注释，以及领域特定专家代理用于对高优先靶标进行下游解读。通过聚合各代理的证据，该框架生成结构化分析报告和数据驱动的假设。我们在多种疾病设置下评估了OmniCellAgent，展示了其识别相关数据集、优先考虑具有生物学意义的靶标并生成全面、有证据支持的假设的能力。我们的结果表明，多智能体AI系统可以降低组学驱动的发现的障碍，并加速精准医学中的假设生成。

## Abstract
In biomedical scientific discovery, identifying relevant omics datasets and interpreting analysis results using prior knowledge from databases and literature are essential for generating novel hypotheses. Although recent AI agents support automated omics analysis and literature retrieval, they typically require users to predefine and curate disease-specific datasets, which is a process that remains challenging and time-consuming, particularly for non-computational researchers. Herein we present OmniCellAgent, a multi-agent AI framework built on large-scale single-cell RNA sequencing (scRNA-seq) resources that autonomously retrieves, integrates and analyzes disease and control-related datasets of diverse cell types across tissues and conditions. Moreover, OmniCellAgent incorporates a biomedical prior knowledge agent for systematic target annotation using curated databases and literature, as well as domain-specific expert agents for downstream interpretation of high-priority targets. By aggregating evidence across agents, the framework generates structured analytical reports and data-driven hypotheses. We evaluate OmniCellAgent across multiple disease settings, demonstrating its ability to identify relevant datasets, prioritize biologically meaningful targets and produce comprehensive, evidence-supported hypotheses. Our results suggest that multi-agent AI systems can reduce barriers to omics-driven discovery and accelerate hypothesis generation in precision medicine.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 论文的核心问题与整体含义
- **背景**：生物医学科学发现中，识别相关组学数据集并利用数据库和文献中的先验知识解释分析结果，对于产生新假设至关重要。
- **问题**：现有AI代理虽然支持自动化组学分析和文献检索，但通常要求用户预先定义和整理疾病特定数据集，这一过程仍然具有挑战性且耗时，尤其对非计算研究人员不友好。
- **整体含义**：本文提出OmniCellAgent多智能体AI框架，旨在降低组学驱动发现的障碍，加速精准医学中的假设生成。

## 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：基于大规模单细胞RNA测序(scRNA-seq)资源，构建多智能体AI框架，使其能够自主检索、整合和分析跨组织与疾病状态的多种细胞类型相关的疾病及对照数据集。
- **关键技术细节**：
  - **自主检索与整合**：无需用户预定义数据集，框架自动查找并整合相关疾病与对照数据。
  - **生物医学先验知识代理**：利用curated数据库和文献进行系统靶标注释。
  - **领域特定专家代理**：对高优先靶标进行下游解读。
  - **证据聚合**：各代理贡献证据，最终生成结构化分析报告和数据驱动的假设。
- **公式或算法流程**：原文未提供具体数学公式或伪代码，仅描述模块化流程（检索→整合→注释→解读→报告生成）。

## 3. 实验设计：使用了哪些数据集/场景，benchmark，对比方法
- **数据集与场景**：在“多种疾病设置”下评估OmniCellAgent，具体疾病类型未在摘要中列举；数据来源为“大规模单细胞RNA-seq资源”（具体资源名称未给出）。
- **Benchmark**：未明确提及标准基准，展示能力主要为定性展示（识别数据集、优先靶标、生成假设）。
- **对比方法**：未与其他现有方法（如单一AI代理、传统手动分析）进行定量比较。

## 4. 资源与算力
- **文中未明确说明**：未提及使用的GPU型号、数量、训练时长等计算资源。

## 5. 实验数量与充分性
- **实验数量**：仅提到“在多种疾病设置下评估”，未给出具体疾病数、数据集数量或独立重复次数。
- **充分性与客观性**：信息不足，无法判断实验是否充分、客观或公平；缺乏消融实验、鲁棒性测试及与基线方法的对比。

## 6. 论文的主要结论与发现
- OmniCellAgent能成功识别相关数据集、优先排序具有生物学意义的目标，并生成全面、有证据支持的假设。
- 多智能体AI系统可有效降低组学驱动发现的障碍，加速精准医学的假设生成。

## 7. 优点
- **自动化程度高**：无需用户手动检索和整理数据集，降低非计算研究人员的使用门槛。
- **多智能体协作**：整合先验知识代理与领域专家代理，提升靶标注释和解释的深度。
- **大规模数据基础**：基于scRNA-seq资源，覆盖多组织、多条件，具备广泛适用性。
- **结构化输出**：生成分析报告和数据驱动假设，便于验证与后续研究。

## 8. 不足与局限
- **实验细节缺失**：未列出具体疾病案例、数据规模、性能指标（如召回率、准确率），验证不充分。
- **缺乏对比分析**：未与基线方法（如单一LLM代理、传统生物信息学流程）进行定量对比，难以评估相对优势。
- **泛化性与鲁棒性**：未讨论框架在不同数据噪声、样本量不足或跨物种场景下的表现。
- **先验知识偏差**：依赖curated数据库和文献，可能引入已报道知识的偏差，忽略潜在新发现。
- **计算开销与可解释性**：未提及运行时间、资源消耗，也未深入分析多智能体决策的可解释性。

（完）
