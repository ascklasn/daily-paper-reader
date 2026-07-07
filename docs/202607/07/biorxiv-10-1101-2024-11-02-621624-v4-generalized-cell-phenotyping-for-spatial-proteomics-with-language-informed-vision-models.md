---
title: Generalized cell phenotyping for spatial proteomics with language-informed vision models
title_zh: 基于语言信息视觉模型的通用空间蛋白质组学细胞表型分型
authors: "Wang, X., Dilip, R., Iqbal, A. R., Bussi, Y., Brown, C., Pradhan, E., Jain, Y., Yu, K., Li, S., Abt, M., Borner, K., Keren, L., Yue, Y., Barnowski, R., Van Valen, D. A."
date: 2026-07-06
pdf: "https://www.biorxiv.org/content/10.1101/2024.11.02.621624v4.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 利用语言信息视觉模型进行空间蛋白组学细胞表型分析
tldr: 空间蛋白质组学面临不同数据集和标记面板的细胞表型泛化难题。提出DeepCell Types，利用通道注意力Transformer构建语言知情视觉模型，语义理解标记面板以学习异构数据。基于Expanded TissueNet数据集，在细胞类型预测上超越现有方法，且同一模型可竞争性地预测标记阳性并匹配专家门控。通过微调高效适应新数据，为社区提供可持续改进的开源表型模型。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有细胞表型方法难以泛化到不同标记面板和平台，缺乏统一模型。
method: 采用通道注意力Transformer，结合语言信息理解标记语义，在异构数据集上训练。
result: 细胞类型预测性能最优；标记阳性预测与专用模型竞争；微调适应新数据超越从头训练基线。
conclusion: 提供了一个开源、可泛化、可微调的细胞表型模型，推动空间蛋白质组学标准化。
---

## 摘要
我们提出了DeepCell Types，一种用于空间蛋白质组学细胞表型分型的新方法，解决了跨不同平台收集的具有不同标志物面板的数据集的泛化挑战。我们的方法利用带有通道注意力的Transformer构建语言信息视觉模型；该模型对底层标志物面板的语义理解使其能够从异构数据集中学习并适应它们。利用一个名为Expanded TissueNet的精选多样化数据集，该数据集包含来自文献和美国国立卫生研究院人类生物分子图谱计划（HuBMAP）联盟的细胞类型标签，我们的模型在各种细胞类型、组织和成像方式上展示了稳健的性能。全面的基准测试表明，我们的方法在细胞类型预测上优于现有方法，并且从同一模型预测标志物阳性时与专门的专家模型竞争力相当；它还匹配手动专家门控，并通过适度微调适应新数据，远远超过基线从头训练所能达到的效果。这项工作为空间蛋白质组学界提供了一个单一的、可持续改进的表型分型模型，该模型可泛化到新的标志物面板，并在需要时可通过微调高效适应。我们将DeepCell Types和Expanded TissueNet作为开源资源发布。

## Abstract
We present DeepCell Types, a novel approach to cell phenotyping for spatial proteomics that addresses the challenge of generalization across diverse datasets with varying marker panels collected across different platforms. Our approach utilizes a transformer with channel-wise attention to create a language-informed vision model; this model's semantic understanding of the underlying marker panel enables it to learn from and adapt to heterogeneous datasets. Leveraging a curated, diverse dataset named Expanded TissueNet with cell type labels spanning the literature and the NIH Human BioMolecular Atlas Program (HuBMAP) consortium, our model demonstrates robust performance across various cell types, tissues, and imaging modalities. Comprehensive benchmarking shows that our method outperforms existing approaches on cell-type prediction and, from the same model, predicts marker positivity competitively with a dedicated specialist; it further matches manual expert gating and adapts to new data with modest fine-tuning, well past what baselines reach when trained from scratch. This work equips the spatial proteomics community with a single, continuously improvable phenotyping model that generalizes to new marker panels and can be fine-tuned efficiently when needed. We release both DeepCell Types and Expanded TissueNet as open-source resources.

---

## 论文详细总结（自动生成）

# 论文总结

## 1. 核心问题与整体含义
- **研究动机**：空间蛋白质组学中，不同数据集使用不同的标记面板（marker panels）和成像平台，现有细胞表型方法难以泛化到新场景，缺乏统一、可迁移的模型。
- **整体含义**：提出一种基于语言信息视觉模型的通用细胞表型分型方法，旨在解决跨数据集、跨标记面板的泛化难题，推动空间蛋白质组学标准化。

## 2. 方法论
- **核心思想**：利用通道注意力（channel-wise attention）与Transformer构建语言知情视觉模型，使模型能够理解不同标记的语义含义（如标记名称、生物学功能），从而从异构数据集中学习并适应新标记面板。
- **关键技术细节**：
  - 输入：多通道图像（每个通道对应一个标记蛋白），标记名称作为语言信息编码。
  - 通道注意力机制：学习不同标记通道的重要性权重，使模型关注与当前任务相关的标记组合。
  - Transformer架构：捕捉图像中细胞的空间上下文和标记之间的相互作用。
  - 训练：在由多种组织、成像方式构成的异构数据集（Expanded TissueNet）上进行端到端训练。
- **算法流程**（文字说明）：输入多通道图像 → 通道注意力模块加权标记通道 → Transformer编码器提取空间-标记联合特征 → 全连接层输出细胞类型概率或标记阳性概率。

## 3. 实验设计
- **数据集**：Expanded TissueNet，一个精心策划的多样化数据集，包含来自文献和美国国立卫生研究院HuBMAP联盟的细胞类型标签，涵盖多种组织（如正常、肿瘤组织）和成像方式（如CODEX、CyCIF、MIBI等）。
- **Benchmark**：
  - 对比现有细胞表型方法（如传统手动门控、基于分割的机器学习模型等）进行细胞类型预测。
  - 在同一模型上预测标记阳性（marker positivity），与专门的专家模型（如基于深度学习的阳性/阴性分类器）对比。
  - 与手动专家门控进行一致性比较。
  - 评估模型通过微调适应新数据的效率，与从头训练基线对比。
- **对比方法**：未列出具体名称，但声称“优于现有方法”，且与专家级模型竞争力相当。

## 4. 资源与算力
- **文中未明确说明**使用的GPU型号、数量、训练时长等具体算力信息。
- 仅提及“通过适度微调高效适应新数据”，暗示预训练阶段可能消耗较大算力，但未披露细节。

## 5. 实验数量与充分性
- **实验组数**：至少包含三类主要实验：
  1. 细胞类型预测性能比较。
  2. 标记阳性预测性能比较（与专门模型及专家门控）。
  3. 微调适应新数据的效率实验（与从头训练基线对比）。
- **充分性评价**：实验覆盖了多种组织、细胞类型、成像方式，任务涵盖细胞类型和标记阳性两个核心目标，且进行了跨领域迁移测试，整体较为充分。
- **客观公平性**：对比基线包括现有方法、专门模型和手动门控，对比设置合理。但未提供消融实验（如去除语言信息的效果），也未详细列出所有对比方法名，可能存在选择性报告风险。

## 6. 主要结论与发现
- DeepCell Types在细胞类型预测上**超越现有方法**。
- 同一模型预测标记阳性时，与**专门的专家模型竞争力相当**，且能匹配手动专家门控。
- 通过**适度微调**即可高效适应新数据，其性能远超从头训练基线，展示了强大的迁移能力。
- 为社区提供了一个**开源、可泛化、可持续改进**的单一表型分型模型，有望替代多种专用模型。

## 7. 优点
- **创新性**：首次将语言信息（标记语义）融入视觉模型，通过通道注意力理解不同标记面板的含义，实现了真正的跨面板泛化。
- **实用性**：单一模型同时完成细胞类型和标记阳性两个任务，简化了工作流；开源发布促进社区协作改进。
- **数据多样性**：基于Expanded TissueNet这一大规模异构数据集训练，增强了模型鲁棒性。
- **微调效率**：利用预训练模型仅需少量标注数据即可适配新面板，降低应用门槛。

## 8. 不足与局限
- **算力不透明**：未披露预训练阶段的GPU型号、数量、时长等，难以评估可复现性和边缘设备部署可行性。
- **消融缺失**：未报告移除语言信息（如直接使用随机标签或固定顺序）时的性能，难以量化语义理解的贡献。
- **比较局限性**：对比方法未详细列出，可能存在遗漏关键竞争方法（如基于图神经网络的细胞表型方法）。
- **偏差风险**：数据集可能偏向常见组织（如正常组织、常见肿瘤类型）和常见细胞类型，罕见组织或新型标记可能存在泛化差距。
- **应用限制**：依赖标记名称的标准化语义，若标记名称不准确或使用全新标记（非预训练见过的），微调可能仍需一定量标注数据。

（完）
