---
title: "CodeCytos: AI-assisted spatial molecular imaging analysis via code-augmented agent action space"
title_zh: CodeCytos：通过代码增强的智能体动作空间实现AI辅助的空间分子成像分析
authors: "Vo, H. Q., Ly, S. T., Wan, Z., Nguyen, A.-V., Zhao, H., Sheng, J., Wong, S. T. C., Nguyen, H. V."
date: 2026-06-03
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.30.728935v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 用于空间分子成像分析的代码增强AI智能体
tldr: 传统空间分子影像分析工具手动干预多、缺乏代码集成，灵活性有限。本文提出CodeCytos，一个基于编码推理的智能体框架，通过编码增强动作空间实现动态可编程分析。在四个组织数据集上，CodeCytos优于基线，且引入域外少样本编码推理示例可进一步提升性能。该工作展示了代码驱动智能体在加速定制特征探索和生物标志物发现中的潜力。
source: biorxiv
selection_source: fresh_fetch
motivation: 传统工具需手动操作且缺乏代码集成，难以高效灵活探索复杂空间组织特征。
method: 提出CodeCytos编码推理智能体框架，利用代码增强动作空间实现动态可编程交互。
result: 在四类组织数据集上优于基线，域外少样本示例进一步提升了性能。
conclusion: CodeCytos展示了代码驱动推理智能体在空间分子影像分析中的潜力，加速生物标志物发现。
---

## 摘要
传统组织图像分析软件为细胞分析提供了基础功能，包括分割、形态特征提取和空间组织分析；然而，这些工具通常需要手动干预，缺乏与代码驱动自动化的无缝集成，限制了复杂空间组织研究的效率和可扩展性，同时由于仅支持固定的一组预定义空间细胞特征，对自定义分析的灵活性有限。为应对这些限制，我们提出了CodeCytos，一个基于编码的推理智能体框架，能够与空间分子成像数据进行动态、可编程的交互，并简化跨不同研究需求的自定义空间细胞特征的探索。我们通过四个专家策划的数据集（涵盖不同组织类型，包括额叶皮层、非小细胞肺癌、胰腺和扁桃体）的案例研究展示了其实用性，并在一个现实的最小提示设置下进行评估，其中生物科学家提出简单问题，没有任务特定指令或先验上下文知识，并以多个具有强大编码能力的大型语言模型为骨干进行基准测试。我们进一步表明，引入从空间分析领域外随机采样的领域无关的少样本上下文编码推理示例，能够显著提升性能，而无需昂贵的专家手工制作的领域内演示；总体而言，CodeCytos优于基线方法，突显了代码驱动推理智能体在支持空间分子成像中自定义特征探索和加速生物标志物发现方面的潜力。

## Abstract
Conventional tissue image analysis software provides foundational capabilities for cellular analysis, including segmentation, morphological feature extraction, and spatial organization analysis; however, these tools often require manual intervention and lack seamless integration with code-driven automation, limiting efficiency and scalability for complex spatial tissue studies, while also offering limited flexibility for custom analyses by supporting only a fixed set of predefined spatial cellular features. To address these limitations, we propose CodeCytos, a coding-based reasoning agent framework that enables dynamic, programmable interaction with spatial molecular imaging data and streamlines the exploration of custom spatial cellular features across diverse research needs. We demonstrate its utility through case studies on four expert-curated datasets spanning distinct tissue types, including frontal cortex, non-small-cell lung cancer, pancreas, and tonsil, and evaluate it under a realistic minimal prompt setting in which bioscientists pose simple questions without task-specific instructions or prior contextual knowledge, benchmarking multiple large language model backbones with strong coding capabilities. We further show that incorporating domain-agnostic few-shot in-context coding-reasoning examples, randomly sampled from outside the spatial analysis domain, substantially improves performance without requiring costly expert-crafted in-domain demonstrations; overall, CodeCytos outperforms baseline approaches, highlighting the potential of code-driven reasoning agents to support custom feature exploration in spatial molecular imaging and accelerate biomarker discovery.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义

- **研究动机**：传统空间分子影像分析软件（如 QuPath、HALO、Squidpy 等）主要提供预定义的固定功能集合，生物科学家进行自定义特征探索时需要大量手动干预或求助计算科学家，效率低、可扩展性差。
- **整体目标**：提出一个能够通过自然语言查询自动生成并执行代码、实现动态可编程分析的智能体（Agent）框架，从而简化定制化空间细胞特征提取，加速生物标志物发现。
- **关键挑战**：如何让大语言模型（LLM）在无领域特定演示的前提下可靠地完成多步空间分析推理与代码执行。

### 2. 论文提出的方法论：核心思想与关键技术

- **核心思想**：融合 ReAct（推理与行动）与 CodeAct（代码动作空间）两种范式，构建一个迭代执行“思考→代码生成→代码执行→观察”循环的智能体 CodeCytos。
- **关键细节**：
  - 动作空间从自然语言扩展到可执行 Python 代码，利用 LLM 预训练的编程知识，减少对人工制作的领域内演示的依赖。
  - 每一步包含：① `<thought>` 标签内的自然语言推理；② `<code>` 标签内可执行代码；③ 执行后观察输出（结果或错误），作为下一步上下文。
  - 使用**领域无关的少样本编码-推理示例**（如普通编程问题），通过上下文学习引导智能体遵循正确的交互格式与推理模式，避免昂贵的人工领域轨迹标注。
- **算法流程（文字说明）**：智能体接收用户自然语言查询 → 解析需求 → 迭代执行“推理→生成代码→执行并观察→更新上下文”直至任务完成或达到最大步数（10步）。

### 3. 实验设计：数据集、基准与对比方法

- **数据集**：
  - 四种组织类型：额叶皮层（Frontal Cortex）、非小细胞肺癌（NSCLC）、胰腺（Pancreas）、扁桃体（Tonsil），每类包含 20 个视野（FOV）图像。
  - 专家策划问题集：总计 548 个问题，覆盖 5 大类空间特征（NND & 距离、局部邻域、空间统计、结构与 ROI、图与拓扑），共 10,960 个图像-问题对。
- **基准（Benchmark）**：在“最小提示”设置下评估（问题无任务说明或上下文），强调智能体自主推断能力。
- **对比方法**：
  - **工具增强 LLM 基线**：① 无 CoT；② 零样本 CoT；③ 少样本 CoT。
  - **CodeCytos 变体**：① 零样本（原始 CodeAct）；② 单样本；③ 少样本编码-推理示例。
  - **LLM 骨干**：Qwen2.5-Coder-32B、Qwen3-Coder-30B、Facebook CWM、Devstral-Small、Devstral-2-123B、Kimi-Linear-48B、GLM-4.5-Air。
  - **额外验证**：在原始 CodeAct 基准 M3ToolEval（82 个多步任务）上测试相同少样本示例的效果。

### 4. 资源与算力

- 文中未明确提及使用的 GPU 型号、数量或训练时长，仅指出使用 **vLLM** 或 **SGLang** 进行推理部署，未说明具体硬件配置。因此算力成本不透明。

### 5. 实验数量与充分性

- 实验数量很大：4 个数据集 × 7 种 LLM 骨干 × 6 种设置（3 种基线 + 3 种 CodeCytos）= 168 组主要实验，加上 M3ToolEval 上的额外验证和按特征类别的深入分析。
- 评估指标全面：成功率、pass@k（k=5,10,20）以及新提出的 AUP@k（Pass@k 曲线下面积），覆盖单次和多次尝试场景。
- 消融比较丰富：对比有无 CoT、少样本 vs 零样本、领域内 vs 领域外示例等。
- **充分性与客观性**：实验设计较为严谨，使用最小提示避免提示工程偏差；不同 LLM 骨干结果一致显示 CodeCytos+少样本最优；但未测试实际生物学家交互场景或鲁棒性（如对抗性问题），且所有实验基于同一批专家代码作为金标准，可能存在偏差风险。

### 6. 论文的主要结论与发现

- CodeCytos（少样本 CodeAct 变体）在所有四个数据集上一致超越所有基线，包括工具增强 LLM 的各种 CoT 变体。
- **关键发现**：即使少样本示例完全来自空间分析领域之外（即领域无关），仍能显著提升 CodeAct 智能体的性能，尤其对开源 LLM 骨干（如 Qwen2.5-Coder、Devstral-Small、Devstral-2-123B）效果明显。
- 在 M3ToolEval 上，领域无关的少样本示例同样带来改善（虽然幅度小于空间分析任务），进一步验证了方法的一般性。
- 不同 LLM 骨干表现差异显著，Devstral-2-123B 和 GLM-4.5-Air 在少样本设置下达到最高 AUP@k（约 0.81-0.86）。

### 7. 优点

- **方法创新**：首次将 CodeAct 范式系统性地应用于空间分子成像分析，并提出利用领域无关的少样本编码-推理示例作为低成本通用引导策略。
- **实践意义**：显著降低生物科学家自定义分析的入门门槛，无需编程专家编写专用代码即可探索新特征。
- **评估严谨**：采用最小提示、多指标（成功率、pass@k、AUP@k）、多数据集、多 LLM 骨干的全面对比，结论稳健。
- **开源友好**：展示了开源 LLM 骨干（甚至非顶尖模型）在添加简单少样本示例后性能大幅提升，具有实际部署价值。
- **代码与数据公开承诺**：将公开数据集和代码，促进复现与后续研究。

### 8. 不足与局限

- **计算资源未公开**：未说明 GPU 型号、数量、训练时长，复现成本不明确，也无法评估实际部署的硬件需求。
- **少样本示例的选择**：本文仅使用随机采样的领域外示例，未系统探究示例数量、内容相似性、顺序等对性能的影响，优化空间尚未探索。
- **某些模型与任务上改进有限**：如对 Facebook CWM 的某些子任务（图形与拓扑、位置/形状特征），少样本示例未带来提升甚至略有下降，说明方法对某些架构不够鲁棒。
- **实验覆盖仍有缺口**：仅依赖专家撰写的代码作为金标准，可能存在编码风格或偏差；未测试智能体在交互式实时使用（如多轮对话、用户纠正）中的表现；未评估失败模式及自纠错能力。
- **应用限制**：当前框架对 LLM 的编程能力有强依赖，如果骨干模型编码能力弱或生成错误代码过大，性能会急剧下降；另外，物理尺度假设（如 1 pixel = 1 μm）可能不适用于所有成像设置，需要用户额外校正。

（完）
