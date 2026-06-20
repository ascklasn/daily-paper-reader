---
title: scIsoAgent enables autonomous isoform-resolved characterization and sequence-informed interpretation of long-read single-cell transcriptomes
title_zh: scIsoAgent实现长读长单细胞转录组的自主异构体分辨表征与序列知情解读
authors: "Zhao, C., Liu, M., Li, X., Li, D., Xu, Y., Wang, Z."
date: 2026-06-16
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.11.731519v1.full.pdf"
tags: ["query:agent"]
score: 8.0
evidence: 基于LLM的科学智能体用于长读单细胞转录组
tldr: 长读长单细胞转录组测序能解析异构体以揭示基因功能异质性，但现有分析工作流碎片化，缺乏可重复性。scIsoAgent作为LLM驱动的自主科学代理，采用阶段感知规划与持久计算上下文，将异构体输入自动转化为可执行的交互式分析流程。相比通用LLM基线，该方法在从规划到执行的连续性上显著提升，在真实数据中复现已发表研究的关键发现，并进一步将差异转录本使用事件延伸为具有序列信息的功能假设。scIsoAgent衔接全长异构体序列与模型推断的转录本属性，连接观测到的异构体使用与潜在序列功能后果，为异构体分辨发现与生物学解释提供可重复工作流。
source: biorxiv
selection_source: fresh_fetch
motivation: 长读长单细胞RNA-seq分析缺乏可重复的异构体分辨工作流，现有LLM代理不适用于此类任务。
method: 提出scIsoAgent，利用LLM的阶段感知规划和持久计算上下文，自动构建可追踪的异构体分析流程并支持交互解释。
result: 相比通用LLM基线，scIsoAgent显著提升分析连续性；在真实数据中复现主要发现，并延伸差异转录本使用为序列功能假说。
conclusion: scIsoAgent将碎片化长读长单细胞分析转化为连贯可重现的工作流，实现异构体分辨表征与序列解释的关联。
---

## 摘要
可变异构体使用可以独立于总基因表达改变基因功能，因此需要在单细胞分辨率下解析转录异构体。长读长单细胞RNA测序通过将细胞身份与转录异构体和序列水平特征联系起来，满足了这一需求。充分发挥其生物学价值需要可重复的工作流程，将专业的长读长分析与生物学解读相结合。现有基于大语言模型的生物医学智能体支持通用组学分析，但并非为异构体分辨的长读长单细胞工作流而设计。在此，我们提出scIsoAgent，一个自主的、由大语言模型驱动的科学智能体，用于长读长单细胞RNA-seq分析。scIsoAgent将异质的长读长单细胞输入转化为可追溯的异构体分辨工作流，采用阶段感知规划和持久计算上下文来支持执行与解读。在互补评估中，与通用大语言模型基线相比，这种设计提高了从分析规划到可执行、交互式工作流的连续性。在实际数据再分析中，scIsoAgent恢复了已发表长读长单细胞资源的主要发现，并将一个代表性的差异转录本使用事件扩展为基于序列的功能假说。通过将全长异构体序列与模型推断的转录本属性联系起来，scIsoAgent连接了观察到的异构体使用与潜在的序列水平功能后果。这些结果表明，自主科学智能体可以将碎片化的长读长单细胞分析转化为连贯、可重复的工作流，用于异构体分辨的发现和生物学解读。

## Abstract
Alternative isoform usage can alter gene function independently of total gene expression, creating a need to resolve transcript isoforms at single-cell resolution. Long-read single-cell RNA sequencing meets this need by linking cellular identity to transcript isoforms and sequence-level features. Realizing its full biological value requires reproducible workflows that connect specialized long-read analysis with biological interpretation. Existing large language model (LLM)-based biomedical agents support general omics analysis, but are not designed for isoform-resolved long-read single-cell workflows. Here, we present scIsoAgent, an autonomous LLM-powered scientific agent for long-read single-cell RNA-seq analysis. scIsoAgent turns heterogeneous long-read single-cell inputs into traceable isoform-resolved workflows, using stage-aware planning and persistent computational context to support both execution and interpretation. Across complementary evaluations, this design improved the continuity from analysis planning to executable, interactive workflows compared with general-purpose LLM baselines. In real-data reanalysis, scIsoAgent recovered major findings from published long-read single-cell resources and extended a representative differential transcript usage event into a sequence-informed functional hypothesis. By linking full-length isoform sequences with model-inferred transcript properties, scIsoAgent connects observed isoform usage with potential sequence-level functional consequences. These results demonstrate that autonomous scientific agents can transform fragmented long-read single-cell analysis into coherent, reproducible workflows for isoform-resolved discovery and biological interpretation.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：可变异构体使用（alternative isoform usage）能独立于总基因表达改变基因功能，因此需要在单细胞分辨率下解析转录异构体。长读长单细胞RNA测序（long-read single-cell RNA-seq）可将细胞身份与转录异构体和序列水平特征关联，但其分析工作流高度碎片化、缺乏可重复性，且现有基于大语言模型（LLM）的生物医学智能体仅支持通用组学分析，未针对异构体分辨的长读长单细胞工作流设计。
- **整体含义**：开发一种自主、可重复的异构体分辨分析工作流，将专业的长读长分析与生物学解读衔接，从而充分发挥长读长单细胞转录组的生物学价值。

## 2. 论文提出的方法论：核心思想、关键技术细节、算法流程

- **核心思想**：利用LLM作为自主科学智能体，将异构的长读长单细胞输入自动转化为可追溯的异构体分辨工作流，并支持执行与交互式解读。
- **关键技术细节**：
  - **阶段感知规划（stage-aware planning）**：将分析过程划分为不同阶段，每个阶段由LLM根据当前上下文生成相应的分析步骤，避免单次规划的长尾错误。
  - **持久计算上下文（persistent computational context）**：在分析过程中保持计算状态和中间结果，使LLM能基于先前执行结果进行后续规划和解读。
- **算法/流程说明**（文字描述）：
  1. 输入：长读长单细胞数据（如原始测序文件、细胞条形码、异构体注释等）。
  2. 阶段感知规划：LLM依次生成各分析阶段（如质控、比对、定量、差异分析）的具体命令或脚本。
  3. 执行：每个命令通过持久计算上下文执行，输出中间结果并更新上下文。
  4. 解读：LLM基于最终结果和全长异构体序列，推断转录本属性（如结构域、编码潜能），连接观察到的异构体使用与潜在序列功能后果，形成功能假说。
  5. 输出：可追溯的分析流程报告和序列知情解读。

## 3. 实验设计

- **数据集/场景**：
  - 使用了已发表的长读长单细胞资源（真实数据）进行再分析，检验能否恢复原始研究的主要发现。
  - 未明确提及数据集名称或规模（如细胞数量、组织类型）。
- **Benchmark**：
  - 以通用LLM基线（如未专门优化的GPT-4等）作为对比方法。
- **对比方法**：
  - 通用大语言模型基线（未具体命名）。
- **评估指标**：
  - 从分析规划到可执行、交互式工作流的**连续性**（continuity）（即规划成功率、执行连贯性等）。

## 4. 资源与算力

- **文中未明确说明**所使用的GPU型号、数量、训练时长等算力资源。
- 仅提及scIsoAgent基于LLM（可能是调用预训练模型API或本地部署），但未给出具体硬件配置或训练开销。

## 5. 实验数量与充分性

- **实验数量**：论文仅提及两方面的评估——互补评估（complementary evaluations）和真实数据再分析。未列出具体实验组数、消融实验或不同参数设置。
- **充分性分析**：
  - 优势：在真实数据中复现了已发表发现，并延伸出序列功能假说，体现了方法的实际效用。
  - 不足：缺乏与多种现有长读单细胞分析工具的直接对比；未进行系统性的消融实验（如去掉阶段感知或持久上下文的影响）；未在多数据集上验证泛化性；实验数量较少，统计效力和可复现性有待增强。

## 6. 论文的主要结论与发现

- scIsoAgent通过阶段感知规划和持久计算上下文，在分析规划到执行的全链条连续性上显著优于通用LLM基线。
- 在真实数据再分析中，scIsoAgent成功恢复了已发表长读长单细胞资源的主要发现。
- 能将一个代表性的差异转录本使用事件扩展为基于序列的功能假说，实现“观察到的异构体使用”与“潜在序列功能后果”的关联。
- **总体结论**：自主科学智能体可将碎片化的长读长单细胞分析转化为连贯、可重现的工作流，用于异构体分辨的发现和生物学解读。

## 7. 优点：方法或实验设计上的亮点

- **方法亮点**：
  - 首次将LLM智能体应用于长读长单细胞转录组分析，填补了异构体分辨工作流自动化的空白。
  - 阶段感知规划+持久计算上下文的设计，有效解决了通用LLM在复杂多步分析中的规划断裂和上下文丢失问题。
  - 将全长异构体序列与模型推断的转录本属性关联，赋予差异分析以序列功能解读能力。
- **实验亮点**：
  - 在真实数据上验证了复现能力，且展示了向新生物假说的延伸，体现了方法的实用价值。

## 8. 不足与局限

- **实验覆盖有限**：仅使用一个已发表资源进行再分析，未在多个不同组织/条件的数据集上验证；未与现有长读单细胞专用工具（如FLAMES、bambu等）进行端到端对比。
- **缺乏消融实验**：未定量评估阶段感知规划和持久计算上下文的各自贡献，无法确定哪些组件最关键。
- **偏差风险**：LLM可能生成看似合理但实际错误的分析步骤或功能解读，存在幻觉风险。论文未讨论如何验证LLM生成结果的可靠性。
- **应用限制**：依赖外部LLM（可能收费或需联网），且需要用户具备一定的生物信息学知识来提供初始输入。未提供公开可用的代码或演示平台。
- **可重复性**：未公开实验的具体数据、超参数和随机种子，其他研究者难以复现结果。
- **算力与效率**：未见时间/资源开销对比，对于大规模数据集（如数万细胞）的扩展性未知。

（完）
