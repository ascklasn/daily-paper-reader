---
title: Client-server interfaces enable efficient agent-driven variant calling
title_zh: 客户端-服务器接口实现高效的智能体驱动变异检测
authors: "Yu, X., Zheng, Z., CHEN, L., QIn, Z., Guo, X., He, M., Luo, R."
date: 2026-06-28
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.25.734665v1.full.pdf"
tags: ["query:agent"]
score: 8.0
evidence: 用于生物信息学中agent驱动变异调用的客户端-服务器接口
tldr: "生物信息学工具多为人类专家设计，大型语言模型代理直接使用时需大量交互解读文档。本文将深度学习变异检测工具Clair3重构为客户端-服务器系统Clair3-Connect，客户端处理基因组数据并暴露结构化代理接口，服务器仅运行推理。在APOE单倍型分型任务中，60次代理运行全部正确，token消耗减少6.8-14倍，运行时间约缩短四分之一，变异性从35%降至4%。这表明为代理设计专用接口可大幅提升效率与可靠性，应成为工具开发的一等交付物。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有生物信息学工具缺乏面向LLM代理的接口，代理需消耗大量token和步骤来理解人类文档，导致效率低下。
method: 将Clair3重构为Clair3-Connect，客户端负责基因组处理并暴露基于结构化调用的代理工具，服务器仅执行神经网络推理，通信加密。
result: "APOE分型任务中代理100%正确，token消耗降至12K（3轮调用），相比shell基线降低6.8-14倍，时间约减75%，SNP F1差异小于0.3。"
conclusion: 为生物信息学工具设计原生代理接口比第三方封装更高效可靠，应作为工具开发的核心交付物。
---

## 摘要
背景：大型语言模型（LLM）智能体越来越多地自动化生物信息学分析，但大多数现有的生物信息学工具是为人类专家独立使用而构建的。驱动此类工具的智能体必须根据面向人类的文档推理其安装、配置和执行，每个结果需要多次交互、大量令牌和工具调用。因此，方法如何向智能体暴露与方法本身同样重要。通过为这些工具设计智能体接口，智能体可以减少此类开销并提高智能体驱动分析的可靠性。发现：为测试这一设计，我们重新架构了Clair3（一个广泛使用的基于深度学习的长读段变异检测器），将其改造为客户端-服务器系统Clair3-Connect。客户端执行所有基因组学相关处理并持有可识别数据。服务器仅运行神经网络推理，客户端仅向服务器发送特征张量，而样本标识符和基因组上下文保留在客户端。客户端暴露了由模式定义、面向智能体的工具，智能体通过单个结构化调用调用这些工具。在一个APOE单倍型分型任务中，所有60次智能体运行均正确。智能体工具使用了3次交互、12K个令牌，比基于shell的基线（81K-163K个令牌）少6.8到14倍，耗时约为后者的四分之一，且稳定性高得多（令牌使用量波动4%对35%）。为了保持客户端轻量化，省略了pileup和分阶段处理，使得在50倍覆盖度下SNP F1值比标准Clair3低0.1-0.3个百分点，而互TLS和AES-256-GCM加密增加了7.2%的端到端运行时间。结论：将一个已有算法重新封装为开发者构建的、位于安全客户端-服务器边界之后的智能体工具，相比第三方封装（无法恢复只有其开发者才知道的默认设置和约定），使得LLM智能体使用起来更高效、更可靠，且更易于部署。智能体接口应成为生物信息学工具开发的一等交付物。

## Abstract
Background: Large language model (LLM) agents increasingly automate bioinformatics analyses, but most existing bioinformatics tools were built for standalone use by human experts. An agent driving such a tool must reason about its installation, configuration, and execution from documentation for human, spending many turns, tokens, and tool calls per result. How a method is exposed to an agent can therefore matter as much as the method itself. By designing agentic interfaces for these tools, agent can reduce such overhead and improve the reliability of agent-driven analyses. Findings: To test this design, we re-architected Clair3, a widely used deep-learning-based long-read variant caller, into a client-server system, Clair3-Connect. The client performs all genomics related processing and holds the identifiable data. The server runs only neural-network inference, and the client sends only feature tensors to the server, while sample identifiers and genomic context remain on the client. The client exposes schema-defined agent-facing tools that an agent invokes through single structured calls. On an APOE diplotyping task, all 60 agent runs were correct. The agentic tools used 12K tokens in 3 turns, 6.8 to 14 times fewer tokens than the shell-driven baselines (81K-163K tokens), at about a quarter the wall-clock time and far more stably (4% versus 35% token usage variation). Dropping the pileup and phasing stages to keep the client light left SNP F1 within 0.1-0.3 points of standard Clair3 by 50x coverage, while mutual TLS and AES-256-GCM encryption added 7.2% to end-to-end runtime. Conclusions: Recasting an established algorithm as developer-built, agentic tools behind a secure client-server boundary makes it more efficient, reliable, and easier to deploy for an LLM agent than a third-party wrapper, which cannot recover the defaults and conventions only its developers know. Agentic interfaces should be a first-class deliverable of bioinformatics tool development.

---

## 论文详细总结（自动生成）

# 论文结构化总结

## 1. 核心问题与整体含义

- **研究动机**：大型语言模型（LLM）智能体（agent）正被用于自动化生物信息学分析，但现有工具（如变异检测器Clair3）均基于人类专家独立使用场景设计。Agent必须通过阅读面向人类的文档来推理安装、配置和执行步骤，每次分析需多次交互、消耗大量token（81K-163K）和工具调用，效率极低且不稳定。
- **整体含义**：方法暴露给agent的方式与方法本身同等重要。为生物信息学工具设计原生agent接口（而非第三方封装）能够大幅降低开销、提升可靠性，应成为工具开发的一等交付物。

## 2. 方法论

- **核心思想**：将已有深度学习变异检测工具Clair3重构为客户端-服务器系统（Clair3-Connect），使agent通过结构化接口调用，无需理解底层shell命令和文档。
- **关键技术细节**：
  - **客户端**：执行所有基因组学相关处理（如读取、比对、特征提取），持有可识别数据（如样本标识符、基因组上下文），暴露由模式（schema）定义的面向agent的工具。Agent通过单次结构化调用（而非多轮交互）触发任务。
  - **服务器**：仅运行神经网络推理，客户端只发送特征张量，不发送可识别信息。通信采用互TLS和AES-256-GCM加密。
  - **简化处理**：为保持客户端轻量，省略了pileup和分阶段处理步骤，仅保留核心调用流程。
- **算法流程（文字说明）**：
  1. Agent向客户端发送结构化的调用请求（包含输入文件路径、参考基因组等参数）。
  2. 客户端解析请求，完成数据加载、预处理、特征提取，生成特征张量。
  3. 客户端通过加密通道将特征张量发送至服务器。
  4. 服务器运行Clair3神经网络模型，返回预测结果（如变异位点和基因型）。
  5. 客户端整合结果，返回最终输出给agent。

## 3. 实验设计

- **数据集/场景**：APOE单倍型分型任务（APOE diplotyping），使用长读段测序数据（具体数据集未详述，可能为公开或模拟数据）。
- **基准（benchmark）**：标准Clair3在shell驱动下的agent使用方式（即agent通过shell命令调用Clair3，需读取文档、配置参数等）。
- **对比方法**：
  - 基于shell的基线（agent驱动Clair3的原始流程）
  - Clair3-Connect（agent通过结构化接口调用）
- **评估指标**：任务正确率、token消耗（每轮）、运行时间、稳定性（token波动）、SNP F1分数（与标准Clair3对比）。

## 4. 资源与算力

- 文中未明确说明使用的GPU型号、数量、训练时长等具体算力信息。
- 仅提及“50倍覆盖度”下测试，以及加密操作导致端到端运行时间增加7.2%，但未给出服务器推理阶段的硬件规格。
- **注意**：本文主要关注推理阶段接口效率，不涉及Clair3模型本身的训练。

## 5. 实验数量与充分性

- **实验数量**：
  - APOE单倍型分型任务中进行了60次agent运行（全部正确）。
  - 对比了token消耗（shell基线81K-163K vs Clai3-Connect 12K），并计算了波动（35% vs 4%）。
  - 评估了SNP F1差值（比标准Clair3低0.1-0.3个百分点）。
  - 加密开销测试（运行时间增加7.2%）。
- **充分性评估**：
  - **优点**：量化指标全面（正确率、效率、稳定性、精度衰减），对比直接。
  - **不足**：仅在一个具体任务（APOE分型）上验证，未覆盖其他变异类型（如indel、结构变异）、不同覆盖度、不同测序平台、不同LLM agent（如GPT-4 vs LLaMA等）。缺乏消融实验（如接口设计选择的影响）。
  - **公平性**：Clair3-Connect由原Clair3开发者构建，能够恢复默认设置和约定，而shell基线由非开发者agent驱动，可能处于劣势（agent需自行推理）。但作者承认这一差异，强调开发者构建的接口优于第三方封装。

## 6. 主要结论与发现

- **效率提升**：agent使用Clair3-Connect仅需3轮交互、12K token，相比shell基线减少6.8-14倍；运行时间约为后者四分之一。
- **稳定性提升**：token消耗波动从35%降至4%。
- **精度保持**：SNP F1值与标准Clair3相差不超过0.3个百分点（50x覆盖度下低0.1-0.3），说明简化处理带来的精度损失可接受。
- **安全性**：通过加密和客户端保留敏感数据，实现了数据隐私保护。
- **总结论**：为生物信息学工具设计原生agent接口（如客户端-服务器架构）远优于第三方封装，应作为工具开发的一等交付物。

## 7. 优点

- **方法创新**：提出“agent接口作为一等交付物”的设计理念，将客户端-服务器架构引入生物信息学工具，分离推理与数据管理，降低了agent的交互复杂度。
- **实验量化充分**：token、时间、稳定性、精度、加密开销均有明确数值对比，支持结论。
- **安全性设计**：从设计上确保敏感基因组数据留在客户端，符合隐私合规需求。
- **开放性**：论证了开发者自身构建接口的独特优势（恢复默认设置和约定），具有实践指导意义。

## 8. 不足与局限

- **实验覆盖有限**：仅在APOE单倍型分型一个任务上验证，未测试其他变异类型（如indel、SV）、不同覆盖度（如低覆盖、高覆盖）、不同测序平台（如PacBio vs Oxford Nanopore）或与其他变异检测工具（如DeepVariant）的对比。
- **精度下降隐患**：省略pileup和分阶段处理可能在某些复杂区域（如重复序列、多等位基因位点）导致更大精度损失，文中仅报告了SNP F1差0.1-0.3，但未报告indel和整体召回率。
- **未测试不同agent**：仅使用单一agent（可能为GPT-4或类似模型）进行实验，未验证接口对不同LLM的泛化性。
- **缺少消融实验**：未单独分析schema设计、加密开销、客户端简化处理等各组件对效率/精度的影响。
- **部署复杂性**：客户端-服务器架构需要额外部署和维护（加密证书、网络配置），可能增加用户使用门槛。
- **资源信息披露不足**：未提供实验所用的GPU型号、推理时间细节，影响可复现性。

（完）
