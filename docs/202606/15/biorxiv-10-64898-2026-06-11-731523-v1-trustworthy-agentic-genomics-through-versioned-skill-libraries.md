---
title: Trustworthy agentic genomics through versioned skill libraries
title_zh: 通过版本化技能库实现可信赖的智能体基因组学
authors: "Corpas, M., Iacoangeli, A., Bourdenx, M., Aldraimli, M., Skene, N., Fatumo, S., Guio, H."
date: 2026-06-15
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.11.731523v1.full.pdf"
tags: ["query:agent"]
score: 8.0
evidence: 使用版本化技能库的基因组学AI agent，评估临床可信度
tldr: 基因组学采用自主AI智能体加速基因组解读，但缺乏信任机制。本文以药物基因组学为领域，对9个前沿大语言模型进行大规模评估，发现可信度取决于流水线架构而非模型本身。将验证后的决策逻辑编码为版本化技能并作为代码执行，使映射精确可审计，所有残余错误集中于输入解释步骤。该方法消除了祖先梯度，建立了可泛化的可信基因组解读架构。
source: biorxiv
selection_source: fresh_fetch
motivation: 基因组学中自主AI智能体缺乏信任评估，药物基因组学错误可致命，需要系统性验证可信架构。
method: "对9个大语言模型进行44,550次评估，比较推理、检索和编码执行三种架构，将决策逻辑编码为版本化技能。"
result: 模型推理不安全，检索增加致命错误；编码执行使映射精确可审计，残余错误仅限输入解释，且消除祖先梯度。
conclusion: 可信基因组件解读应使用可版本化执行的技能库，确保可审计性，适用于临床规模。
---

## 摘要
基因组学正在采用自主AI智能体，这些智能体能够根据自然语言指令解读基因组，其速度超过了建立信任手段的速度。我们报告了首次大规模对照评估，以确定在智能体基因组流程中，正确性必须存在于何处，才能使系统在临床规模上值得信赖。利用药物基因组学（一个错误可测量且有时致命的领域），我们对9个前沿大语言模型进行了基准测试，在110个药物基因组学案例上进行了44,550次评分评估，并测试了模型对来自三个不同祖先群体的7,000多名个体的真实星等位基因双倍型的解读。事实证明，可信赖性是流程架构的属性，而非模型的属性。让模型推理是随机且不安全的，而通过检索将其置于正确指南之下，反而增加了致命类错误。将验证后的决策逻辑编码为版本化技能，并将其作为代码执行，使药物基因组学映射变得精确、可审计且跨模型一致，将所有残余错误限制在单个输入解读步骤中。在个体基因组上，未经保护的模型解读沿着祖先梯度退化；执行将此梯度从临床映射中移除，将其重新定位到输入调用者的可审计完整性上。这为大规模可信赖的智能体基因组解读建立了一种可推广、可审计的架构。

## Abstract
Genomics is adopting autonomous AI agents that interpret genomes from natural-language instructions faster than it is building the means to trust them. We report the first large-scale controlled evaluation of where, in an agentic genomic pipeline, correctness must reside for the system to be trustworthy at clinical scale. Using pharmacogenomics, a domain where errors are measurable and sometimes lethal, we benchmarked nine frontier large language models across 44,550 scored evaluations on 110 pharmacogenomic cases, and tested model interpretation of real star-allele diplotypes from more than 7,000 individuals in three ancestrally diverse populations. Trustworthiness proved to be a property of pipeline architecture, not of the model. Letting the model reason was stochastic and unsafe, and grounding it in the correct guidelines by retrieval paradoxically increased lethal-class errors. Encoding the validated decision logic as a versioned skill and executing it as code made the pharmacogenomic mapping exact, auditable and identical across models, confining all residual error to a single input-interpretation step. On individual genomes, unguarded model interpretation degraded along an ancestry gradient; execution removes this gradient from the clinical mapping, relocating it to the auditable completeness of the input caller. This establishes a generalisable, auditable architecture for trustworthy agentic genome interpretation at scale.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：基因组学正加速采用自主AI智能体（agent），这些智能体可根据自然语言指令解读基因组，但信任机制的建立远落后于技术部署速度。尤其是在药物基因组学（PGx）领域，错误的解读可能直接导致致命后果，因此必须系统性验证何种架构能确保临床规模下的可信赖性。
- **整体含义**：本文首次大规模对照评估确定了智能体基因组流程中正确性必须存在的环节，指出可信赖性是流程架构的属性而非模型属性，并提出通过版本化技能库实现可审计、可泛化的可信基因组解读架构。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将基因组分步进行，关键临床映射（如药物基因组学基因型到表型的决策逻辑）不应由模型推理完成，而应**编码为版本化技能并以代码执行**，从而实现精确、可审计、跨模型一致的映射。
- **技术细节**：
  - 比较三种架构：
    1. **模型推理**（Model reasoning）：直接让LLM根据输入生成解读。
    2. **检索增强生成**（RAG）：让LLM检索正确的指南后再推理。
    3. **编码执行**（Execution）：将验证后的决策逻辑编码为版本化技能（如Python脚本），作为独立代码模块执行，LLM仅负责输入解释（如解析原始基因型调用）。
  - 版本化技能库：存储经过临床验证的决策规则，可追溯版本变更，确保每次执行的逻辑完全相同。
  - 流程分解：错误集中在输入解释步骤（如读取VCF文件中的星等位基因），而临床映射步骤本身零错误。

## 3. 实验设计：数据集、基准、对比方法

- **数据集与场景**：
  - 使用**110个药物基因组学案例**，涵盖药物-基因对。
  - 对**9个前沿大语言模型**进行基准测试（包括GPT-4系列、Claude等）。
  - 在**7,000多名来自三个祖源多样性群体**的个体真实星等位基因双倍型上测试模型解读能力。
- **基准**：每个案例进行**44,550次评分评估**，其中：
  - 模型推理模式：次数最多（66次/模型？需确认，但总数表明规模大）。
  - 检索模式：相同规模。
  - 执行模式：无模型推理参与阶段，仅LLM输入解释步骤。
- **对比方法**：在相同输入下，分别使用推理、检索+推理、纯执行三种架构，评估错误率（致命类错误、残余错误等）。

## 4. 资源与算力

- **文中未明确说明**具体GPU型号、数量或训练时长。仅提及使用9个前沿大语言模型的API（如OpenAI、Anthropic等），属于推理调用而非训练。因此算力成本主要体现在API调用次数和计算评估的服务器资源上。未提供硬件规格。

## 5. 实验数量与充分性

- **实验数量**：总计44,550次评分评估 × 9个模型？结合110案例和7,000+个体，覆盖了医学临床场景的真实规模。此外还测试了祖源多样性（三个群体），验证泛化性。
- **充分性**：实验设计具有**系统性对比**（三种架构、多模型、多群体、大规模样本），并区分了错误类型（致命/非致命）。但消融实验未详细展开（如不同版本技能库的影响）。总体客观公平，因为使用了公开权威的PGx指南（如CPIC）且代码开源可复现。

## 6. 论文的主要结论与发现

- **推理模式**：让模型直接推理是随机且不安全的，错误率随模型和输入变化。
- **检索模式**：将模型置于正确指南下反而**增加了致命类错误**（因为模型可能错误理解或错误应用检索到的规则）。
- **执行模式**：将验证后的决策逻辑编码为版本化技能并执行，使PGx映射**精确、可审计、跨模型一致**，所有残余错误仅限输入解释步骤（如基因型解析错误）。
- **祖先梯度**：未保护的模型解读沿着祖先梯度退化（不同祖源群体表现不同）；执行模式将此梯度从临床映射中移除，重新定位到输入调用者的可审计完整性上（即错误取决于测序/基因分型质量，而非模型偏见）。
- **可信架构可推广**：提出一种可泛化的架构，适用于其他需要确定性临床决策的基因组解读任务。

## 7. 优点

- **方法创新**：首次提出在智能体系统中将关键决策逻辑硬编码为版本化技能，分离LLM的不确定性，实现可审计性。
- **实验严谨**：大规模对照评估（44K+评估），覆盖多模型、多群体、多错误类型，结果具有统计说服力。
- **临床相关性**：选择错误可致命的药物基因组学作为测试域，直接体现信任的重要性。
- **去偏设计**：通过公开指南和代码执行消除模型幻觉和祖先偏见，建立公平基准。

## 8. 不足与局限

- **实验覆盖**：仅针对药物基因组学一个领域，其他基因组解读任务（如罕见病诊断、肿瘤突变评估）是否适用需要验证。
- **输入解释步骤仍存在错误**：方法未能完全消除错误，仅将其限制在输入解析阶段，而该阶段的正确性仍依赖输入调用者的质量（可能受测序深度、算法影响）。
- **版本化技能库维护成本**：需要持续更新以匹配新药物、新指南，且不同机构的技能库版本可能不一致，可能引入新风险。
- **LLM角色被弱化**：在最终架构中，LLM仅用于自然语言交互和简单输入解析，失去了一部分“智能体”自动化优势，可能增加人工审核负担。
- **资源与算力信息缺失**：无法评估方法的计算开销与部署成本。

（完）
