---
title: Client-server interfaces enable efficient agent-driven variant calling
title_zh: 客户端-服务器接口实现高效代理驱动的变异识别
authors: "Yu, X., Zheng, Z., CHEN, L., QIn, Z., Guo, X., He, M., Luo, R."
date: 2026-06-28
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.25.734665v1.full.pdf"
tags: ["query:agent"]
score: 8.0
evidence: LLM代理用于变异检测，设计代理接口减少开销
tldr: 大语言模型代理自动化生物信息学分析时，现有工具为人类设计导致交互开销大。将Clair3重构为客户端-服务器系统Clair3-Connect，客户端处理基因组数据并暴露代理工具，服务器仅运行神经网络推理。在APOE分型任务中，代理驱动的60次运行全部正确，token消耗仅为Shell驱动的6.8-14倍，时间约四分之一且更稳定。这表明代理接口应成为生物信息学工具开发的一等产出。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有生物信息学工具为人类专家设计，LLM代理驱动时需要大量交互，效率低且不可靠。
method: 将Clair3重构为客户端-服务器系统Clair3-Connect，客户端处理基因组数据并暴露代理工具，服务器仅运行神经网络推理。
result: "APOE分型任务中代理60次运行全部正确，token消耗较Shell驱动减少6.8-14倍，时间约四分之一，变异度从35%降至4%。"
conclusion: 开发者构建的代理接口比第三方封装更高效可靠，应成为生物信息学工具开发的一等产出。
---

## 摘要
背景：大型语言模型代理日益自动化生物信息学分析，但大多数现有生物信息学工具是为人类专家独立使用而构建的。代理驱动此类工具时必须从针对人类的文档中推理其安装、配置和执行，每个结果消耗大量轮次、令牌和工具调用。因此，方法如何暴露给代理可能与方法本身同样重要。通过为这些工具设计代理接口，代理可以减少此类开销并提高代理驱动分析的可靠性。发现：为测试此设计，我们将广泛使用的基于深度学习的长读长变异识别工具Clair3重新架构为客户端-服务器系统Clair3-Connect。客户端执行所有基因组学相关处理并持有可识别数据。服务器仅运行神经网络推理，客户端仅向服务器发送特征张量，而样本标识符和基因组上下文保留在客户端。客户端暴露基于模式的代理面向工具，代理通过单个结构化调用调用这些工具。在APOE单倍型分型任务中，所有60次代理运行均正确。代理工具在3轮交互中使用12K令牌，比shell驱动基线（81K-163K令牌）少6.8至14倍，实际时间约为四分之一，且更加稳定（令牌使用变化4%对比35%）。为保持客户端轻量化而省略pileup和phasing阶段后，SNP F1值在50×覆盖度下仍保持在标准Clair3的0.1-0.3分以内，而相互TLS和AES-256-GCM加密使端到端运行时间增加7.2%。结论：将既有算法重构为开发者构建的、位于安全客户端-服务器边界后的代理工具，相比第三方封装（无法恢复仅其开发者知晓的默认值和约定），使其对LLM代理更高效、更可靠且更易部署。代理接口应成为生物信息学工具开发的一等交付物。

## Abstract
Background: Large language model (LLM) agents increasingly automate bioinformatics analyses, but most existing bioinformatics tools were built for standalone use by human experts. An agent driving such a tool must reason about its installation, configuration, and execution from documentation for human, spending many turns, tokens, and tool calls per result. How a method is exposed to an agent can therefore matter as much as the method itself. By designing agentic interfaces for these tools, agent can reduce such overhead and improve the reliability of agent-driven analyses. Findings: To test this design, we re-architected Clair3, a widely used deep-learning-based long-read variant caller, into a client-server system, Clair3-Connect. The client performs all genomics related processing and holds the identifiable data. The server runs only neural-network inference, and the client sends only feature tensors to the server, while sample identifiers and genomic context remain on the client. The client exposes schema-defined agent-facing tools that an agent invokes through single structured calls. On an APOE diplotyping task, all 60 agent runs were correct. The agentic tools used 12K tokens in 3 turns, 6.8 to 14 times fewer tokens than the shell-driven baselines (81K-163K tokens), at about a quarter the wall-clock time and far more stably (4% versus 35% token usage variation). Dropping the pileup and phasing stages to keep the client light left SNP F1 within 0.1-0.3 points of standard Clair3 by 50x coverage, while mutual TLS and AES-256-GCM encryption added 7.2% to end-to-end runtime. Conclusions: Recasting an established algorithm as developer-built, agentic tools behind a secure client-server boundary makes it more efficient, reliable, and easier to deploy for an LLM agent than a third-party wrapper, which cannot recover the defaults and conventions only its developers know. Agentic interfaces should be a first-class deliverable of bioinformatics tool development.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：大语言模型（LLM）代理正越来越多地用于自动化生物信息学分析流程。然而，现有生物信息学工具几乎都是为人类专家独立使用而设计的（如通过shell命令、复杂参数、文档解释等）。当LLM代理驱动这些工具时，需要从面向人类的文档中推理安装、配置、运行步骤，导致大量交互轮次、令牌消耗和工具调用，效率低下且不可靠。
- **核心问题**：工具如何暴露给代理，可能与方法本身同等重要。当前缺乏针对代理优化的接口设计，需要探索一种“代理友好”的接口范式，减少开销并提升可靠性。
- **整体含义**：提出并验证了一种客户端-服务器架构的代理接口设计，表明由工具开发者原生构建的代理接口（而非第三方封装）能显著提升代理驱动的生物信息学分析的效率与稳定性。该设计应成为生物信息学工具开发的一等交付物。

## 2. 论文提出的方法论：核心思想、关键技术细节、算法流程

- **核心思想**：将既有深度学习变异识别工具Clair3重构为客户端-服务器系统（Clair3-Connect），客户端处理所有基因组学相关计算并持有可识别数据，服务器仅运行神经网络推理。客户端暴露基于模式（schema-defined）的代理面向工具，代理通过单个结构化调用调用这些工具，从而大幅减少交互开销。
- **关键技术细节**：
  - **客户端**：负责基因组数据读取、特征提取、BAM/FASTA处理等，保留样本标识符和基因组上下文。暴露代理工具（如`call_variants`），接受结构化输入（如参考基因组路径、BAM路径、输出目录等），返回标准化输出（如VCF文件路径）。
  - **服务器**：仅接收特征张量进行神经网络推理，不接触原始基因组数据。使用相互TLS（mTLS）和AES-256-GCM加密保护通信。
  - **与标准Clair3对比**：为了保持客户端轻量化，省略了pileup和phasing阶段（这些阶段在服务器端实现或简化），但通过实验验证SNP F1值在50×覆盖度下仍在标准Clair3的0.1-0.3分以内。
  - **代理调用流程**：代理只需一次结构化调用即可完成变异识别任务，而传统shell驱动方式需要多次交互（如安装、配置、参数调优、结果解析等）。

## 3. 实验设计：数据集/场景、benchmark、对比方法

- **测试场景**：APOE单倍型分型任务（APOE diplotyping）——一个典型的生物信息学分析任务，涉及变异识别与分型。
- **数据集**：未明确说明使用的具体测序数据来源，但提及了长读长测序数据（Clair3本身针对长读长）。
- **Benchmark**：对比两种驱动方式：
  - **Shell驱动基线**：代理直接使用shell命令调用标准Clair3，需要多次交互（包括安装、配置、运行、解析）。
  - **代理工具（Clair3-Connect）**：代理通过客户端暴露的单一结构化工具调用完成。
- **对比指标**：令牌消耗（token usage）、交互轮次（turns）、端到端时间（wall-clock time）、运行稳定性（令牌使用变异度）、正确率（agent runs correctness）。
- **附加实验**：评估客户端轻量化（省略pileup和phasing）对变异识别准确率的影响（SNP F1值对比标准Clair3）；评估加密开销（mTLS + AES-256-GCM导致的端到端时间增加百分比）。

## 4. 资源与算力

- **文中明确提及**：未详细说明训练Clair3模型所使用的GPU型号、数量或训练时长。论文主要关注代理接口的改进，而非模型训练本身。Clair3本身是已有公开模型，论文中可能直接使用预训练模型进行推理。
- **服务器端推理**：需要GPU进行神经网络推理，但未指定具体GPU型号和数量。客户端可运行在CPU上。
- **加密开销**：mTLS + AES-256-GCM使端到端运行时间增加7.2%，说明额外算力消耗较小。
- **总体**：算力信息不够详细，但强调了客户端轻量化设计（省略pileup和phasing）以降低资源需求。

## 5. 实验数量与充分性

- **主要实验数量**：
  - APOE分型任务：代理驱动60次运行（全部正确），对比shell驱动（未明确次数，但应足够统计）。
  - 准确率对比：在50×覆盖度下，评估SNP F1值（省略pileup/phasing vs 标准Clair3），未给出具体数据集数目和交叉验证。
  - 加密开销：一个端到端时间对比实验。
- **充分性评估**：
  - **优点**：60次重复运行充分证明了代理接口的稳定性和正确率；对比了令牌消耗和时间，数据有统计学意义（变异度4% vs 35%）。
  - **不足**：仅在一个任务（APOE分型）上测试，未在其他变异识别场景（如全基因组、不同覆盖度、不同测序平台）验证；未与其他代理接口设计（如第三方封装）进行系统对比（仅与shell驱动基线对比）；消融实验仅针对pileup+phasing，缺乏对客户端其他组件的独立测试；未在不同LLM代理（如GPT-4、Claude等）上验证通用性。

## 6. 论文的主要结论与发现

- **主要结论**：将既有算法重构为开发者构建的、位于安全客户端-服务器边界后的代理工具，相比第三方封装，对LLM代理更高效、更可靠且更易部署。代理接口应成为生物信息学工具开发的一等交付物。
- **具体发现**：
  - 代理工具在3轮交互中使用12K令牌，比shell驱动基线（81K-163K令牌）少6.8至14倍。
  - 实际运行时间约为shell驱动的四分之一，且稳定性显著提升（令牌使用变异度4% vs 35%）。
  - 所有60次代理运行均正确，而shell驱动可能因交互错误导致失败（文中未明确比较正确率，但强调稳定性）。
  - 为保持客户端轻量化而省略pileup和phasing后，SNP F1值在50×覆盖度下仍保持在标准Clair3的0.1-0.3分以内，准确率损失可接受。
  - 安全加密通信带来的额外开销仅7.2%，不影响实际应用。

## 7. 优点：方法或实验设计上的亮点

- **方法创新**：将生物信息学工具重构为客户端-服务器架构，首次系统性提出代理接口应原生设计而非封装，体现了工程化思维。
- **降低代理交互复杂度**：通过单一结构化调用替代多轮shell命令，大幅减少令牌消耗和推理时间，使代理更可靠。
- **安全与隐私设计**：客户端持有原始基因组数据，服务器仅接收特征张量，并通过mTLS和AES-256-GCM加密，保护敏感数据。
- **实验设计严谨**：60次重复运行以评估稳定性，令牌消耗和时间数据对比直观；加密开销单独量化。
- **结果说服力强**：令牌消耗降低6.8-14倍，时间降低约75%，稳定性从35%变异降至4%，效果显著。

## 8. 不足与局限

- **实验覆盖不足**：仅测试一个任务（APOE分型），且未在不同覆盖度、不同变异类型（如INDEL、结构变异）上验证，通用性存疑。
- **省略pileup和phasing的代价**：虽然SNP F1损失在0.1-0.3分，但对于高精度应用（如临床诊断）可能不可接受；且未评估对INDEL准确率的影响。
- **代理依赖假设**：实验仅使用了某个特定的LLM代理（未指明具体模型），未验证在不同代理（如不同模型、不同提示策略）下的泛化能力。
- **对比基线单一**：仅对比了shell驱动基线，未与第三方封装的代理接口（如LangChain工具、BioBERT等）对比，无法证明“开发者构建”优于“第三方封装”的结论。
- **缺少可重复性细节**：未提供具体数据集、代码库、超参数等，实验可复现性较差。
- **算力信息缺失**：未说明推理所用GPU型号和数量，难以评估实际部署成本。

（完）
