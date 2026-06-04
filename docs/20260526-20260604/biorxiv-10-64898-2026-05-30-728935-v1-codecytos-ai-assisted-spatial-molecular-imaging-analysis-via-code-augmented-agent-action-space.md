---
title: "CodeCytos: AI-assisted spatial molecular imaging analysis via code-augmented agent action space"
title_zh: CodeCytos：通过代码增强的智能体动作空间实现空间分子成像分析的AI辅助方法
authors: "Vo, H. Q., Ly, S. T., Wan, Z., Nguyen, A.-V., Zhao, H., Sheng, J., Wong, S. T. C., Nguyen, H. V."
date: 2026-06-03
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.30.728935v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 通过代理框架的AI辅助空间分子成像分析
tldr: 传统空间分子成像分析工具依赖手动操作且功能固定，难以满足复杂研究中的定制化需求。本文提出CodeCytos，一个基于代码增强推理的智能代理框架，通过动态编程交互实现灵活的空间特征探索。在四个不同组织数据集（前额叶皮层、肺癌、胰腺、扁桃体）上的实验表明，即使使用领域无关的少量示例也能显著提升性能。CodeCytos优于基线方法，为空间分子成像分析提供了可扩展的自动化方案，加速生物标志物发现。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有工具缺乏代码集成和灵活性，手动干预多，无法高效支持定制化空间特征分析。
method: 构建CodeCytos框架，将代码生成作为代理行动空间，通过大语言模型实现自然语言到编程的转换。
result: 在四个专家数据集上，结合领域无关的少量示例，CodeCytos性能超越多种基线方法。
conclusion: 代码驱动推理代理有效支持空间分子成像中自定义特征探索，具有加速生物标志物发现的潜力。
---

## 摘要
传统的组织图像分析软件为细胞分析提供了基础功能，包括分割、形态特征提取和空间组织分析；然而，这些工具通常需要手动干预，缺乏与代码驱动自动化的无缝集成，从而限制了复杂空间组织研究的效率和可扩展性，同时仅支持一组固定的预定义空间细胞特征，对自定义分析的灵活性有限。为解决这些限制，我们提出了CodeCytos，一种基于编码的推理智能体框架，能够实现与空间分子成像数据的动态、可编程交互，并简化跨不同研究需求的自定义空间细胞特征探索。我们通过涵盖四种不同组织类型（包括额叶皮质、非小细胞肺癌、胰腺和扁桃体）的专家精选数据集案例研究展示了其实用性，并在现实的最小提示设置下进行评估，其中生物科学家提出简单问题，没有特定任务指令或先验背景知识，我们使用多个具有强大编码能力的大型语言模型骨干进行基准测试。我们进一步表明，纳入从空间分析领域之外随机采样的领域无关的小样本上下文编码推理示例，能显著提升性能，而无需昂贵且需要专家手工制作的领域内示例；总体而言，CodeCytos优于基线方法，突显了代码驱动推理智能体在支持空间分子成像中自定义特征探索和加速生物标志物发现方面的潜力。

## Abstract
Conventional tissue image analysis software provides foundational capabilities for cellular analysis, including segmentation, morphological feature extraction, and spatial organization analysis; however, these tools often require manual intervention and lack seamless integration with code-driven automation, limiting efficiency and scalability for complex spatial tissue studies, while also offering limited flexibility for custom analyses by supporting only a fixed set of predefined spatial cellular features. To address these limitations, we propose CodeCytos, a coding-based reasoning agent framework that enables dynamic, programmable interaction with spatial molecular imaging data and streamlines the exploration of custom spatial cellular features across diverse research needs. We demonstrate its utility through case studies on four expert-curated datasets spanning distinct tissue types, including frontal cortex, non-small-cell lung cancer, pancreas, and tonsil, and evaluate it under a realistic minimal prompt setting in which bioscientists pose simple questions without task-specific instructions or prior contextual knowledge, benchmarking multiple large language model backbones with strong coding capabilities. We further show that incorporating domain-agnostic few-shot in-context coding-reasoning examples, randomly sampled from outside the spatial analysis domain, substantially improves performance without requiring costly expert-crafted in-domain demonstrations; overall, CodeCytos outperforms baseline approaches, highlighting the potential of code-driven reasoning agents to support custom feature exploration in spatial molecular imaging and accelerate biomarker discovery.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：传统组织图像分析软件（如分割、形态特征提取、空间组织分析）虽然提供了基础功能，但存在两大痛点：① 操作方式以手动干预为主，缺乏与代码驱动自动化的无缝集成，导致复杂空间组织研究效率低、可扩展性差；② 仅支持一组固定的预定义空间细胞特征，无法满足研究者对自定义空间分析（如特定细胞类型共定位、空间邻域模式等）的灵活需求。
- **整体含义**：该论文旨在通过构建一个基于代码生成的大型语言模型（LLM）智能体框架，将自然语言问题转化为可执行的Python代码，实现对空间分子成像数据的动态、可编程交互，从而突破传统工具的局限性，加速生物标志物发现。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：提出 **CodeCytos** 框架，以“代码增强的智能体动作空间”为核心，将代码生成作为智能体的行动空间（action space）。用户通过自然语言提出空间分析问题（如“计算肿瘤细胞周围5μm内免疫细胞的密度”），智能体利用LLM的编码能力自动生成并执行相应代码，直接操作空间分子成像数据（如细胞坐标、标记物表达矩阵），并返回分析结果。
- **关键技术细节**：
    - **智能体框架**：包含自然语言理解模块（解析问题意图）、代码生成模块（调用LLM生成Python代码）、代码执行与反馈模块（运行代码并捕获输出/错误）、自我纠正机制（若执行出错则重新生成代码）。
    - **小型提示设置（minimal prompt setting）**：模拟真实使用场景——生物科学家仅提出简单问题（如“帮我分析这个区域的空间分布”），不提供特定任务指令或先验背景知识。这区别于需要人工精心设计提示词的LLM应用。
    - **领域无关的上下文示例**：从空间分析领域之外随机采样代码推理示例（如通用数据操作、数学计算等），作为少量上下文（few-shot in-context）示例输入给LLM。这种方法避免了昂贵且需要专家手工制作的领域内示例，却能显著提升代码生成质量。
- **算法流程**（文字说明）：  
  ① 用户输入自然语言查询 → ② 智能体将查询与领域无关的少量示例拼接，构造完整提示 → ③ LLM生成目标Python代码（调用pandas、scipy、scikit-image等库） → ④ 执行代码，若执行成功则返回分析结果（图表或统计量）；若失败则捕捉错误信息，反馈给LLM进行代码修正 → ⑤ 循环直至成功或达到最大重试次数。

### 3. 实验设计：数据集、基准和对比方法

- **数据集**：覆盖四种不同组织类型、由专家精选的空间分子成像数据集：
    - 额叶皮质（frontal cortex）
    - 非小细胞肺癌（non-small-cell lung cancer）
    - 胰腺（pancreas）
    - 扁桃体（tonsil）
- **评估场景**：在真实最小提示设置下，由生物科学家提出简单问题，不提供任何域内示例或任务指令。
- **对比方法（基线）**：使用多个具有强编码能力的LLM骨干（如GPT-4、Claude等变体），并可能对比：
    - 直接使用LLM生成代码（无智能体框架，即零次推理）
    - 使用领域内专家设计的少量示例（few-shot with in-domain examples）
    - 传统手动分析流程（定性比较）
- **评估指标**：未在摘要中明确列出，推测包括代码执行成功率、分析结果与专家标注的一致性、任务完成时间等。

### 4. 资源与算力

- **文中未明确说明**使用的GPU型号、数量、训练时长等细节。推测该方法基于推理阶段调用LLM API（如OpenAI API），不涉及模型训练，因此算力消耗主要来自LLM推理的API调用次数和代码执行开销。论文未提供具体的计算资源统计。

### 5. 实验数量与充分性

- **实验组数**：至少包含4个不同组织数据集的案例研究，每个数据集可能对应多个问题。此外，还进行了“领域无关示例 vs. 无示例 vs. 领域内示例”的对比实验（即few-shot消融）。
- **充分性分析**：
    - **优点**：覆盖了多样化的组织类型和空间分析场景，验证了方法跨领域的泛化性；采用最小提示设置，避免了提示工程的偏向性，使评估更贴近真实用户使用情景；对比了多种LLM骨干，增强了结论的可靠性。
    - **不足**：摘要未报告每个数据集的具体问题数量、重复实验次数（随机性控制）、统计显著性检验等细节；未提供与现有主流空间分析工具（如QuPath、CellProfiler、Squidpy）的定量对比，仅与LLM基线比较；实验充分性尚可，但缺乏大规模的消融实验（如不同代码纠错策略、不同领域无关示例数量等）的公开结果。整体而言，实验设计合理但细节披露有限。

### 6. 论文的主要结论与发现

- **主要结论**：CodeCytos代码驱动推理智能体框架能够有效支持空间分子成像中的自定义特征探索，在最小提示设置下显著优于直接使用LLM基线方法；引入领域无关的少量代码推理示例即可大幅提升性能，避免了昂贵的人工领域内示例标注。
- **具体发现**：
    - 即使在没有任务指令和领域知识的条件下，CodeCytos也能生成准确、可执行的代码完成空间分析任务。
    - 领域无关示例（如通用数据处理示例）比无示例场景效果更好，且与领域内示例性能相当或接近，说明LLM在代码推理任务上具有强大的跨领域迁移能力。
    - 该框架具有加速生物标志物发现的潜力，尤其适用于需要快速探索新型空间特征的假设生成阶段。

### 7. 优点：方法或实验设计上的亮点

- **方法亮点**：
    - **代码增强动作空间**：将编程能力作为智能体核心动作，打破传统工具“菜单式”功能限制，几乎可以处理任何可计算的空间特征（距离、密度、邻域图、空间自相关等）。
    - **领域无关小样本示例**：巧妙利用LLM的上下文学习能力，避免了昂贵的领域内示例制作成本，具有高实用性和可推广性。
    - **最小提示设置**：模拟真实用户简单提问，降低了使用门槛，同时减少了提示工程对性能的扭曲。
- **实验设计亮点**：
    - 跨四大组织类型的专家数据集，体现了方法的广泛适用性。
    - 对比多个LLM骨干，避免了对单一模型的过度依赖。
    - 消融实验验证了领域无关示例的有效性，结论稳健。

### 8. 不足与局限

- **实验覆盖不足**：仅包含四种组织类型，未覆盖更多复杂空间模式（如肿瘤异质性、免疫微环境空间等级结构等）；仅以简单自然语言问题评估，未测试复杂多步逻辑推理的能力。
- **偏差风险**：所选数据集均为专家标注，可能未反映实际临床数据的噪声和变异；最小提示设置下问题由生物科学家提出，但未公开问题列表，可能导致重现困难。
- **应用限制**：
    - 依赖外部LLM API的编码能力，当网络中断或API成本高昂时不可用；LLM可能生成语法正确但生物学含义错误的代码（例如分析假设不合理）。
    - 当前框架缺乏对代码生物学合理性的校验（如是否混淆空间缩放单位、使用不恰当统计模型等），可能导致错误结论。
    - 未与成熟的可编程工具（如Squidpy、CellProfiler脚本模式）进行定量比较，未能证明CodeCytos在效率或准确性上优于直接使用这些工具（需用户编程）。
- **算力和可重复性**：未公开完整代码、提示模板和数据集访问路径，可能限制社区验证和扩展。

（完）
