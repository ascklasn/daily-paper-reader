---
title: "CodeCytos: AI-assisted spatial molecular imaging analysis via code-augmented agent action space"
title_zh: "CodeCytos: 通过代码增强的智能体动作空间进行AI辅助空间分子成像分析"
authors: "Vo, H. Q., Ly, S. T., Wan, Z., Nguyen, A.-V., Zhao, H., Sheng, J., Wong, S. T. C., Nguyen, H. V."
date: 2026-06-03
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.30.728935v1.full.pdf"
tags: ["query:agent"]
score: 9.0
evidence: 基于编码推理的智能代理用于空间分子成像分析
tldr: 传统组织空间分子成像分析软件依赖手动操作且功能固定，难以满足复杂研究的定制化需求。本文提出CodeCytos，一种基于编码推理的智能体框架，通过代码增强动作空间实现动态可编程交互，显著提升自动化与灵活性。在额叶皮层、非小细胞肺癌、胰腺和扁桃体四种专家精选数据集上，CodeCytos优于基线方法，且仅需领域无关的少样本编码示例即可大幅改善性能。该工作展示了代码动作智能体在辅助定制特征探索和加速生物标志物发现中的巨大潜力。
source: biorxiv
selection_source: fresh_fetch
motivation: 传统分析工具手动且功能固定，缺乏自动化和定制性，限制复杂空间分子成像研究的效率与可扩展性。
method: 提出CodeCytos框架，利用编码推理智能体通过生成代码动态操作数据，实现可编程的自动化分析。
result: 在四种不同组织数据集上，CodeCytos超越基线，且领域无关的少样本示例显著提升性能。
conclusion: 代码智能体能有效辅助空间分子成像的定制特征探索，有望加速生物标志物发现。
---

## 摘要
传统的组织图像分析软件为细胞分析提供了基础功能，包括分割、基本形态特征提取和空间组织分析。然而，这些工具通常需要人工干预，并且与代码驱动的自动化集成不足，限制了复杂空间组织研究的效率和可扩展性。此外，它们对自定义分析的灵活性有限，因为它们通常只支持一组固定的预实现空间细胞特征。为了解决这些限制，我们提出了CodeCytos，一个基于编码的推理智能体框架，能够实现与空间分子成像数据的动态、可编程交互，以提高自动化和定制化。CodeCytos旨在简化自定义空间细胞特征的探索，并适应多样化的研究需求。我们通过在四个来自不同组织类型的专家策划数据集（额叶皮层、非小细胞肺癌、胰腺和扁桃体）上的案例研究来展示其效用。我们在现实的最小提示设置下评估CodeCytos，其中生物科学家提出简单问题，没有任务特定指令或关于空间细胞分析的上下文信息，并比较了多个具有强大编码能力的LLM主干。我们进一步表明，结合定制的、领域无关的少样本上下文编码推理示例（在空间分析领域之外随机采样的演示）可以显著提高性能，而无需昂贵的、专家制作的领域内演示。总体而言，CodeCytos优于基线方法，凸显了代码动作智能体在空间分子成像中辅助自定义特征探索和加速生物标志物发现的潜力。

## Abstract
Conventional tissue image analysis software provides foundational capabilities for cellular analysis, including segmentation, basic morphological feature extraction, and spatial organization analysis. However, these tools often require manual intervention and are not well integrated with code-driven automation, limiting efficiency and scalability for complex spatial tissue studies. In addition, they offer limited flexibility for custom analyses, as they typically support only a fixed set of pre-implemented spatial cellular features. To address these limitations, we propose CodeCytos, a coding-based reasoning agent framework that enables dynamic, programmable interaction with spatial molecular imaging data, to improve automation and customization. CodeCytos is designed to streamline the exploration of custom spatial cellular features and adapt to diverse research needs. We demonstrate its utility through case studies on four expert-curated datasets from distinct tissue types: frontal cortex, non-small-cell lung cancer, pancreas, and tonsil. We evaluate CodeCytos under a realistic minimal prompt setting, where bioscientists pose simple questions without task-specific instructions or contextual information about spatial cellular analysis, and benchmark multiple LLM backbones with strong coding capabilities. We further show that incorporating tailored, domain-agnostic few-shot in-context coding-reasoning examples (randomly sampled demonstrations outside the spatial analysis domain) can substantially improve performance without requiring costly, expert-crafted in-domain demonstrations. Overall, CodeCytos outperforms baseline approaches, highlighting the potential of code-action agents to assist with custom feature exploration in spatial molecular imaging and to accelerate biomarker discovery.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：传统的组织图像分析软件（如分割、形态特征提取、空间组织分析）虽然提供了基础功能，但存在两大痛点：一是需要大量手动干预，且与代码驱动的自动化集成不足，导致复杂空间组织研究的效率和可扩展性受限；二是这些工具功能固定，仅支持一组预实现的空间细胞特征，对自定义分析的灵活性很差，难以适应多样化的研究需求。
- **整体含义**：为了解决上述局限，作者提出一种基于编码推理的智能体框架（CodeCytos），旨在实现与空间分子成像数据的动态、可编程交互，从而提升自动化和定制化能力，简化自定义空间细胞特征的探索，并加速生物标志物的发现。

## 2. 论文提出的方法论

- **核心思想**：利用编码推理智能体（coding-based reasoning agent），通过生成可执行代码动态操作空间分子成像数据，实现可编程的自动化分析。智能体根据用户的简单自然语言问题（无任务特定指令或上下文信息）自主生成代码，执行特征提取、统计计算、可视化等任务。
- **关键技术细节**：
  - 框架名为 **CodeCytos**，由大语言模型（LLM）作为推理主干，结合代码增强的动作空间（code-augmented agent action space）。
  - 智能体在“最小提示”（minimal prompt）设置下运行：用户仅提供简单问题，没有任务指令或空间细胞分析的上下文信息。
  - 为了进一步提升性能，引入了**定制化的、领域无关的少样本上下文编码推理示例**：这些示例来自空间分析领域之外的随机采样演示（例如其他编程任务），而非昂贵的专家制作的领域内演示。通过上下文学习（in-context learning），帮助LLM理解代码推理模式。
  - 方法不依赖特定公式或复杂算法流程，而是依靠LLM的代码生成能力与执行环境（如Python库）的交互。文字流程：用户输入 → LLM生成代码 → 执行代码 → 返回结果或可视化 → 可迭代修正。

## 3. 实验设计

- **数据集**：四个来自不同组织类型的专家策划数据集：
  - 额叶皮层（frontal cortex）
  - 非小细胞肺癌（non-small-cell lung cancer）
  - 胰腺（pancreas）
  - 扁桃体（tonsil）
- **基准设置（Benchmark）**：在“现实的最小提示”下评估，生物科学家提出简单问题，无任务特定指令或空间细胞分析上下文。比较了多个具有强大编码能力的LLM主干（如GPT-4等，具体型号未在元数据中列出，但可推断）。
- **对比方法**：基线包括直接使用LLM生成答案而无代码执行的方法，或者无少样本示例的版本等。论文提到“CodeCytos优于基线方法”，但未列举具体基线名称（从摘要推断可能包括标准LLM问答、无代码智能体等）。

## 4. 资源与算力

- **文中未明确说明**：摘要和元数据中未提及使用GPU型号、数量、训练时长等算力信息。可能是基于现有LLM API（如OpenAI）进行推理，而非训练；或实验完全在CPU上运行代码执行。需指出这一点。

## 5. 实验数量与充分性

- **实验数量**：在四个数据集上进行了案例研究，每个数据集对应一个简单问题环境（具体问题数未明说）。此外，进行了消融实验：比较有无定制少样本示例的效果，以及不同LLM主干的对比。
- **充分性、客观性、公平性**：
  - 数据集覆盖四种不同组织类型，具有一定多样性。
  - 采用最小提示设置，模拟真实用户场景，避免了过度人为指导，设置公平。
  - 少样本示例采用领域无关的随机采样，避免了过拟合到特定领域，增加了泛化性验证。
  - 但缺少与更多传统工具或更复杂基线的系统比较，也没有提供精确的性能指标（如准确率、F1分数等），仅定性说明“优于基线”。实验规模较小（四个数据集，简单问题），未在更大规模和更多样化的任务上验证。

## 6. 论文的主要结论与发现

- CodeCytos框架在四个不同组织类型的数据集上均优于基线方法，证明了代码动作智能体在空间分子成像中的潜力。
- 加入定制化的、领域无关的少样本上下文编码推理示例（非领域内示例）可以显著提升性能，无需昂贵的专家标注。
- 编码推理智能体能够有效辅助自定义特征探索，有望加速生物标志物发现。

## 7. 优点：方法或实验设计上的亮点

- **创新性**：将代码增强的智能体动作空间应用于空间分子成像分析，实现了动态、可编程的交互，突破了传统工具的功能固化限制。
- **实用性**：采用最小提示设置，降低用户使用门槛，生物科学家仅需提出简单问题即可获得分析结果。
- **少样本策略巧妙**：使用领域无关的编码推理示例，避免了昂贵且难以获取的领域内专家演示，展示了跨领域迁移的零样本/少样本能力。
- **多组织类型验证**：涵盖大脑、肺癌、胰腺、扁桃体，一定程度上验证了方法的通用性。

## 8. 不足与局限

- **实验覆盖有限**：仅四个数据集、每数据集单一问题场景，缺乏大规模、多任务、多难度级别的系统评估。
- **性能指标不明确**：摘要仅定性声称“优于基线”，未给出量化结果（如成功率、执行准确性、用户满意度等），难以客观判断改善幅度。
- **缺乏与传统工具对比**：未与主流分析软件（如QuPath、CellProfiler等）或现有AI方法（如基于视觉的端到端模型）进行比较。
- **资源与效率未评估**：未讨论代码生成耗时、执行开销、LLM调用成本等实际部署问题。
- **潜在偏差风险**：数据集均为专家策划，可能无法代表真实世界的噪声和异质性；且问题简单，未涉及复杂空间推理任务（如细胞间相互作用、空间模式发现）。
- **应用限制**：依赖LLM的代码生成能力，若LLM产生错误代码或幻觉，可能导致不可靠结果；领域无关示例的有效性可能随问题类型变化。

（完）
