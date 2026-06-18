---
title: "Orion: Towards Lab Automation with Computer-Using Agents"
title_zh: Orion：迈向使用计算机代理的实验室自动化
authors: "Ma, C., Trinh, L., Bucci, M., Regev, A., Wang, H."
date: 2026-06-16
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.13.732095v1.full.pdf"
tags: ["query:agent"]
score: 9.0
evidence: Orion是一个用于生物医学图像分析的计算机使用AI代理，直接相关医学AI代理框架
tldr: "实验室发现通常依赖计算工作流连接实验数据与分析、解释和假设生成，但这些工作流受限于专用软件的劳动密集使用和图形界面视觉检查。Orion通过结合大语言模型、终端执行、GUI控制和自适应多步推理，在共享计算环境中自动执行端到端分析。在基准测试中，其在生物医学数据库和文献检索任务上准确率超过90%，并学会了使用CellProfiler和QuPath进行定量分析。在100小时自主探索大型扰动成像数据集时，Orion生成了52份研究报告，人类科学家从中优先筛选出22个合理的机制假设。该成果表明计算机使用AI代理能够大幅扩展实验室自动化范围，提供可扩展且可审计的从实验图像到定量分析、报告和生物学假设的路径。"
source: biorxiv
selection_source: fresh_fetch
motivation: 实验室计算工作流高度依赖人工操作专用软件和图形界面，效率低下且难以扩展，亟需自动化解决方案。
method: 结合大语言模型与终端执行、GUI控制及自适应多步推理，无需定制集成即可自主完成图像分析、软件操作和信息检索。
result: "生物医学检索准确率超90%，学会CellProfiler和QuPath；100小时自主探索生成52份报告，筛选出22个合理机制假设。"
conclusion: Orion证明计算机使用AI代理能显著扩展实验室自动化，提供可审计的从实验图像到分析报告和生物学假设的路径。
---

## 摘要
实验室发现越来越依赖于将实验数据与分析、解释和后续假设连接起来的计算工作流。然而，这些工作流仍然受到专用软件劳动密集型使用、通过图形用户界面的视觉检查以及跨多个来源的知识整合的限制。在此，我们提出 Orion，一个用于生物医学图像分析和解释的计算机使用 AI 代理，通过自动化实验室工作的计算层来迈向实验室自动化。Orion 在共享计算环境中将大型语言模型与终端执行、GUI 控制和自适应多步推理相结合。它可以检查视觉数据、操作标准科学软件、挖掘网络资源并执行端到端的分析和解释工作流，无需定制软件集成。在基准测试中，Orion 在生物医学数据库和文献检索任务上实现了超过 90% 的准确率，学习了使用流行工具 CellProfiler 和 QuPath 分别进行细胞和组织图像的定量分析，并促进了实验成像数据中的自主发现。在 100 小时的大规模扰动成像数据集自主探索中，Orion 生成了 52 份研究报告，其中人类科学家审查后优先选择了 22 个合理的机制假设。这些结果表明，使用计算机的 AI 代理可以显著扩展实验室自动化的范围，提供从实验成像数据到定量分析、报告和生物学基础假设的可扩展且可审计的途径。

## Abstract
Laboratory discovery increasingly depends on computational workflows that connect experimental data to analysis, interpretation and follow-up hypotheses. Yet these workflows remain constrained by labor-intensive use of specialized software, visual inspection through graphical user interfaces, and integration of knowledge across multiple sources. Here, we present Orion, a computer-using AI agent for biomedical image analysis and interpretation that moves towards lab automation by automating this computational layer of laboratory work. Orion combines large language models with terminal execution, GUI control and adaptive multi-step reasoning in a shared computing environment. It can inspect visual data, operate standard scientific software, mine web resources and conduct end-to-end analysis and interpretation workflows without requiring bespoke software integrations. Across benchmarks, Orion achieved over 90% accuracy on biomedical database and literature retrieval tasks, learned to use the popular tools CellProfiler and QuPath for quantitative analysis of cellular and tissue images, respectively, and facilitated autonomous discovery in experimental imaging data. In 100 hours of autonomous exploration of a large-scale perturbation imaging dataset, Orion generated 52 research reports, of which human scientist review prioritized 22 plausible mechanistic hypotheses. These results show that computer-using AI agents can substantially expand the reach of laboratory automation, providing a scalable and auditable route from experimental imaging data to quantitative analysis, reports and biologically grounded hypotheses.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **核心问题**：实验室发现过程严重依赖计算工作流来连接实验数据与分析、解释和假设生成，但这些工作流受限于专用软件的劳动密集型使用、通过图形用户界面（GUI）的视觉检查，以及跨多个来源的知识整合，导致效率低下、可扩展性差。
- **研究动机**：亟需自动化解决方案，以无需定制软件集成的方式，自主完成计算层面的实验分析任务。
- **整体含义**：通过计算机使用 AI 代理（Computer-Using Agent）扩展实验室自动化范围，提供从实验成像数据到定量分析、报告和生物学假设的可扩展且可审计的路径。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：构建一个名为 Orion 的 AI 代理，在共享计算环境中将大型语言模型（LLM）与终端执行、GUI 控制以及自适应多步推理相结合，从而能够检查视觉数据、操作标准科学软件、挖掘网络资源，并执行端到端的分析和解释工作流。
- **关键技术细节**：
  - 集成 LLM 作为核心推理引擎，处理自然语言指令和视觉信息。
  - 终端执行：通过命令行界面调用科学工具（如 CellProfiler、QuPath）并执行脚本。
  - GUI 控制：模拟鼠标键盘操作，直接操纵标准科学软件的图形界面。
  - 自适应多步推理：根据任务进展动态调整下一步行动，具备错误恢复和回溯能力。
  - 无需定制软件集成：所有操作依赖已有软件的常规接口，而非为代理专门改写代码。

## 3. 实验设计
- **数据集与场景**：
  - 生物医学数据库和文献检索任务（准确率>90%）。
  - 使用 CellProfiler 进行细胞图像定量分析、QuPath 进行组织图像定量分析（学习任务）。
  - 大规模扰动成像数据集的自主探索（100小时），生成了 52 份研究报告。
- **Benchmark**：文中提及在生物医学数据库和文献检索任务上进行了基准测试，但未提供具体数据集名称或标准 benchmark 名称（如 BLURB、PubMedQA 等），也未说明对比了哪些基线方法。因此，论文的基准测试可能为自定义任务或标准化检索评测。
- **对比方法**：元数据和摘要中未提及对比其他具体方法。

## 4. 资源与算力
- **文中未明确说明**：未提及使用的 GPU 型号、数量、训练时长或推理资源消耗。仅从经验可推断需要较大的 LLM 推理算力，但具体数值未给出。

## 5. 实验数量与充分性
- **实验数量**：主要包含三类实验：
  1. 生物医学检索准确率测试（单项结果 >90%）。
  2. Orion 学习使用 CellProfiler 和 QuPath 的技能验证。
  3. 大规模自主探索实验：100 小时生成 52 份报告，经人工审查优先选出 22 个合理假设。
- **充分性与客观性**：
  - 检索任务单一指标（准确率）可能不够全面（未报告召回率、F1 等），且未与其他代理或传统方法对比，难以判断相对优势。
  - 工具学习任务仅有定性描述，缺少量化指标（如学习曲线、错误率）。
  - 自主探索实验设计了固定时长（100 小时）和明确的产出（报告数、假设筛选比），相对客观，但缺乏消融实验（例如不同推理策略的影响）。
  - 整体来看，实验覆盖了典型应用场景，但对比基线缺失和消融实验不足，使得结论的推广性存疑。

## 6. 主要结论与发现
- Orion 在生物医学数据库和文献检索上准确率超过 90%，表明其具有可靠的知识检索能力。
- 成功学会了使用 CellProfiler 和 QuPath 进行定量分析，展示了端到端操作标准软件的能力。
- 在 100 小时自主探索中，从大规模扰动成像数据中生成 52 份研究报告，其中 22 个机制假设被人类科学家优先考虑，证明其能够辅助真实科学发现。
- **总体结论**：使用计算机的 AI 代理可以显著扩展实验室自动化的范围，提供可审计的从实验图像到分析报告和生物学假设的途径。

## 7. 优点
- **无需定制集成**：能够直接操作现有标准科学软件（如 CellProfiler、QuPath）及网络资源，降低了部署门槛。
- **通用性与灵活性**：结合终端执行和 GUI 控制，可适应多种软件和任务，无需为每个工具开发专用接口。
- **可审计性**：代理的推理步骤和操作记录可用于追溯，增加科学研究的透明度和可复现性。
- **高效自主探索**：100 小时内生成大量假设，远超人类手动操作的速度，显著提升高通量成像数据的分析效率。

## 8. 不足与局限
- **实验覆盖不足**：
  - 仅涉及生物医学图像分析领域，未测试其他实验室任务（如质谱数据分析、基因组变异检测）。
  - 基准测试缺少对比方法（如其他 AI 代理、传统自动化脚本），无法量化 Orion 的相对增益。
  - 未进行消融实验（如去除 GUI 控制或自适应推理的影响）。
- **潜在偏差风险**：
  - 检索准确率基于特定测试集，可能存在数据泄露或过拟合。
  - 自主探索实验中“合理假设”的筛选依赖人类专家判断，带有主观性。
- **应用限制**：
  - 依赖 LLM 的推理能力，可能出现幻觉或错误操作，尤其在复杂 GUI 交互中。
  - 100 小时探索时间较长，若遇到长任务需要更高效规划。
  - 假设生成的质量高度受限于 LLM 的知识边界和科学常识。
- **资源与算力未公开**：难以评估方法的可复制性和经济成本。

（完）
