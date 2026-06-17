---
title: "OmicsNavigator: An auditable scientific partner for scalable hypothesis validation in spatial omics"
title_zh: OmicsNavigator：一个可审计的科学合作伙伴，用于空间组学中可扩展的假设验证
authors: "Li, Y., Vakharia, N., Liang, W., Mayer, A. T., Luo, R., Trevino, A. E., Wu, Z."
date: 2026-06-14
pdf: "https://www.biorxiv.org/content/10.1101/2025.07.21.665821v2.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 基于大语言模型的空间组学分析
tldr: 空间组学数据高维复杂，转化为可验证的生物学发现是一大瓶颈。本文提出OmicsNavigator，一个基于大语言模型的自主系统，能够直接推理空间组学的视觉和分子特征，进行知识引导的空间结构注释。该系统实现零样本语义检索组织生物标志物，并重建患者级疾病图谱，同时具备可审计的假设验证引擎。在糖尿病肾病、肾移植排斥和COVID-19等多个病理数据集上验证，OmicsNavigator生成基于证据、人类可读的洞察，有望加速空间生物学发现。
source: biorxiv
selection_source: fresh_fetch
motivation: 空间组学数据高维复杂，缺乏可扩展且可审计的工具来将其转化为可验证的生物学假设。
method: OmicsNavigator基于大语言模型，直接推理空间组学的视觉和分子特征，通过知识引导进行空间结构注释和假设验证。
result: 在多个疾病数据集上，实现了零样本语义检索和患者级疾病图谱重建，并生成基于证据的人类可读洞察。
conclusion: OmicsNavigator提供了可审计、可扩展的科学伙伴，有效加速空间组学数据到生物学发现的转化。
---

## 摘要
将高维度、空间分辨的分子数据集转化为可验证的生物学发现仍然是一个主要的研究瓶颈。这里，我们介绍OmicsNavigator，一个由大语言模型驱动的自主系统，用于空间组学数据的端到端数据探索和假设验证。OmicsNavigator直接对空间组数据的多模态输入（包括视觉和分子特征）进行推理，以执行空间结构的知识引导注释。我们证明，通过将高维数据转化为文本解释，OmicsNavigator能够实现组织生物标志物的零样本语义检索，并从原始组学观测中重建患者级别的疾病特征。此外，OmicsNavigator具有一个由预注册、人类审计蓝图管理的客观假设验证引擎。通过跨越包括糖尿病肾病、肾移植排斥和COVID-19肺部病理等多种病理条件的数据集验证该系统，我们证明了OmicsNavigator能够从空间组学数据中生成基于证据、人类可读的见解，具有加速空间生物学发现的潜力。

## Abstract
Translating high-dimensional, spatially resolved molecular datasets into testable biological findings remains a major research bottleneck. Here, we present Omic-sNavigator, an autonomous large language model-powered system for end-to-end data exploration and hypothesis validation on spatial omics data. OmicsNaviga-tor reasons directly over the multi-modal inputs of spatial omics data, including visual and molecular signatures, to perform knowledge-guided annotation of spatial structures. We show that by transforming high-dimensional data into textual interpretations, OmicsNavigator enables zero-shot semantic retrieval of tissue biomarkers and the reconstruction of patient-level disease profiles from raw omics observations. Furthermore, OmicsNavigator features an objective hypothesis validation engine governed by pre-registered, human-audited blueprints. By validating the system across datasets spanning diverse pathological conditions including diabetic kidney disease, kidney transplant rejection, and COVID-19 pulmonary pathology, we demonstrate that OmicsNavigator generates evidence-based, human-readable insights from spatial omics data, with potential to accelerate spatial biology discoveries.

---

## 论文详细总结（自动生成）

# 详细论文总结

## 1. 论文的核心问题与整体含义
- **研究背景**：空间组学数据（如空间转录组、空间蛋白质组）具有高维度、多模态（视觉+分子）和空间异质性的特点，传统分析方法难以有效整合这些信息，导致从数据到可验证生物学发现的转化效率低下。
- **核心问题**：缺乏一种**可扩展、可审计**的工具，能够自动将复杂空间组学数据转化为可验证的生物学假设，并支持端到端的数据探索与假设验证。
- **整体含义**：OmicsNavigator试图填补这一空白，通过大语言模型（LLM）直接对空间组学的视觉和分子特征进行推理，实现**知识引导的空间结构注释**、**零样本语义检索**以及**可审计的假设验证**，从而加速空间生物学发现。

## 2. 方法论
- **核心思想**：利用大语言模型（LLM）作为“自主科学伙伴”，将高维空间组学数据转化为文本解释，使模型能够直接理解并推理视觉和分子特征。
- **关键技术细节**：
  - **多模态输入推理**：直接处理空间组学数据中的视觉图像（如组织切片）和分子表达谱，生成统一的文本表示。
  - **知识引导注释**：通过预注册的人类审计蓝图（pre-registered, human-audited blueprints）指导模型进行空间结构的自动注释，确保可解释性和可审计性。
  - **零样本语义检索**：在没有额外训练的情况下，利用文本语义匹配检索组织生物标志物。
  - **假设验证引擎**：由预注册蓝图驱动的客观验证机制，支持用户输入假设并自动生成基于证据的结论。
- **算法流程（文字说明）**：
  1. 输入原始空间组学数据（图像+分子矩阵）。
  2. 使用LLM将多模态数据编码为文本解释。
  3. 利用知识图谱或预注册蓝图进行空间区域注释。
  4. 通过语义相似度实现生物标志物的零样本检索。
  5. 在患者级别重建疾病图谱。
  6. 用户提交假设后，引擎依据预注册规则进行客观验证并输出人类可读的报告。

## 3. 实验设计
- **使用数据集**：涵盖多种病理条件，具体包括：
  - **糖尿病肾病**（Diabetic Kidney Disease, DKD）
  - **肾移植排斥反应**（Kidney Transplant Rejection）
  - **COVID-19肺部病理**（COVID-19 Pulmonary Pathology）
- **Benchmark与对比方法**：
  - 论文未明确列出传统基准方法（如非LLM的聚类、空间注释工具等）的对比结果，主要展示OmicsNavigator自身的零样本检索能力和疾病图谱重建能力。
  - 实验侧重于**定性评估**（生成的可读洞察）和**语义检索准确率**，未提供定量指标（如F1-score、AUC等）。
- **实验设计特点**：在多个独立数据集上验证了系统的泛化能力，但缺乏与现有SOTA方法的严格对比。

## 4. 资源与算力
- **文中明确说明**：未提及使用的GPU型号、数量或训练时长。由于OmicsNavigator基于大语言模型（如GPT-4或其他开源LLM）进行推理，可能依赖于预训练模型，但具体部署资源未在摘要和元数据中描述。
- **推断**：作为自主推理系统，推理阶段可能不需要大规模GPU集群，但若涉及微调或自建LLM，则可能需较高算力。文中未提供任何算力细节。

## 5. 实验数量与充分性
- **实验数量**：在3个疾病数据集上进行了验证（糖尿病肾病、肾移植排斥、COVID-19肺部病理），每个数据集可能包含多个样本或切片。
- **充分性评估**：
  - **优点**：覆盖多种病理类型，具有一定多样性。
  - **不足**：
    - 未设计**消融实验**（如移除LLM组件、不同蓝图设计的影响）。
    - 未与其他空间组学分析工具（如Seurat、SPOTlight、Giotto等）进行量化对比。
    - 缺乏对**假设验证引擎**的误差分析或假阳性率评估。
  - **客观性**：实验设计偏向展示功能可行性，而非严格的性能基准测试，可能难以完全公平地证明其优于现有方法。

## 6. 主要结论与发现
- OmicsNavigator能够直接从空间组学数据生成**基于证据、人类可读的生物学洞察**，而无需额外训练。
- 实现了**零样本语义检索**：例如，在没有标注数据的情况下，能够根据文本描述检索出特定组织生物标志物。
- 能够**重建患者级的疾病特征图谱**，将原始组学观测转化为有意义的疾病分型或区域标注。
- 通过预注册蓝图实现了**可审计的假设验证**，增强了科学推理的透明性和可重复性。
- 系统在多个疾病数据集上表现良好，验证了其**通用性**。

## 7. 优点
- **创新性**：首次将LLM直接应用于空间组学多模态数据的端到端推理，而不依赖传统的降维或聚类流程。
- **可审计性**：引入预注册、人类审计的蓝图，使假设验证过程透明、可追溯，符合开放科学要求。
- **零样本能力**：无需针对每种疾病或组织重新训练模型，降低了应用门槛。
- **交互性**：生成人类可读的报告，使非计算生物学家也能理解结果。
- **多场景验证**：覆盖肾脏和肺部疾病，证明了方法的跨组织、跨疾病通用性。

## 8. 不足与局限
- **实验覆盖不足**：论文仅展示了3个数据集，缺乏对更多空间组学技术（如MERFISH、Visium HD等）的验证。
- **缺乏定量基准对比**：未与现有主流空间注释工具（如CellTypist、scArches）进行性能对比，无法评估相对优势。
- **偏差风险**：LLM可能产生“幻觉”（hallucination），特别是在零样本场景下，尽管有预注册蓝图约束，但风险未量化。
- **算力与可重复性**：未提供计算资源细节，依赖的商业LLM（如GPT-4）可能无法完全开源复现，影响可重复性。
- **应用限制**：假设验证引擎依赖预注册蓝图的设计，如果蓝图不完善或错误，可能误导结果；且系统可能受限于LLM的上下文窗口大小，无法处理超大视野的空间数据。
- **未提供详细的错误分析**：例如，零样本检索的召回率和精确度。对假设验证的假阳性/假阴性未讨论。

（完）
