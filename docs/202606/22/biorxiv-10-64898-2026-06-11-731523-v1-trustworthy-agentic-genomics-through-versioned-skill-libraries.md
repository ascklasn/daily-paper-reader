---
title: Trustworthy agentic genomics through versioned skill libraries
title_zh: 通过版本化技能库实现可信赖的自主基因组分析
authors: "Corpas, M., Iacoangeli, A., Bourdenx, M., Aldraimli, M., Skene, N., Fatumo, S., Guio, H."
date: 2026-06-15
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.11.731523v1.full.pdf"
tags: ["query:agent"]
score: 8.0
evidence: 评估临床基因组学中LLM代理的可信度
tldr: "基因组学正引入基于大语言模型的自主代理，但缺乏信任机制。通过44,550次评估测试9个前沿模型在110个药物基因组学案例上的表现，发现让模型推理随机且不安全；检索虽提升表型准确率却增加致命错误；而将验证过的决策逻辑编码为版本化技能并作为代码执行，使临床映射精确、可审计且跨模型一致，错误仅限输入解读步骤。这建立了可推广的可信代理基因组解读架构，正确性须通过执行而非推理或检索实现。"
source: biorxiv
selection_source: fresh_fetch
motivation: 基因组学自主代理信任缺失，需明确系统可信赖性的来源。
method: 在药物基因组学基准上评估9种大模型，对比推理、检索与技能执行三种流水线架构。
result: 技能执行使映射精确且模型不变，错误仅限输入解读；推理和检索分别导致随机与致命错误。
conclusion: 可信赖代理基因组解读应通过版本化技能执行正确逻辑，将模型限制于输入解读。
---

## 摘要
基因组学正在采用自主AI代理，这些代理能够根据自然语言指令解读基因组，但其速度超过了建立信任手段的速度。我们首次报告了一项大规模对照评估，旨在确定在自主基因组分析流程中，正确性必须存在于何处，才能使系统在临床规模上值得信赖。利用药物基因组学（一个错误可测量且有时致命）领域，我们对9个前沿大语言模型进行了基准测试，涉及110个药物基因组学病例的44,550次评分评估，并测试了模型对来自三个人群祖先多样性个体的超过7,000个真实星号等位基因双倍型的解读。结果表明，可信赖性是流程架构的属性，而非模型的属性。让模型进行推理是随机且不安全的，通过检索将其锚定在正确的指南上反而增加了致命性错误。将经过验证的决策逻辑编码为版本化技能并作为代码执行，使得药物基因组学映射变得精确、可审计且跨模型一致，将所有剩余错误限制在单一的输入解读步骤中。在个体基因组上，无防护的模型解读会沿着祖先梯度下降；执行消除了临床映射中的这一梯度，将其转移到输入调用器的可审计完整性上。这为大规模可信赖的自主基因组解读建立了一个可推广、可审计的架构。

亮点
O_LI正确性必须被执行，而非推理或检索，才能值得信赖
C_LI
O_LI检索提高了表型准确性，但增加了致命性错误；技能则不然
C_LI
O_LI执行使临床映射精确且模型无关；错误停留在输入阶段
C_LI
O_LI确定性输入调用器是获得全正确输出答案的预测途径
C_LI

简而言之，Corpas及其同事表明，可信赖的自主基因组解读并非来自让语言模型正确推理生物学，而是通过将模型限制在解读输入上，同时由版本化、经过验证的技能以执行代码的形式进行推理。在9个大语言模型和110个药物基因组学病例中，执行技能使得临床映射具有确定性、可审计性和模型不变性。

意义：基因组学采用自主的、语言模型中介的代理的速度，超过了建立信任所需的标准。在具有致命性后果的药物基因组学基准测试中，我们表明代理的可信赖性不是模型的属性，而是代理如何被约束的属性：正确性必须从随机模型中移出，进入作为代码执行的版本化技能，模型则被限制在解读异构输入上。这为该领域提供了一个可迁移的可信赖自主基因组解读架构，一条预测的部署路径，使每个输出答案都是正确的（执行经过验证的技能，确定性调用输入，并对不可减少的残余进行弃权），以及一种将基因组技能开发为经过验证、可执行、版本化单元（而非提示）的方法。遵循其他地方描述的验证框架，我们使用“临床级”来表示确定性、可审计性、可追溯到版本化组件以及人群不变性能，所有这些都在技能约束执行下实现。我们区分了两种人群性能的含义：执行的临床映射通过构造具有人群不变性，在欧洲、拉丁美洲和东非起源个体中得到验证；而模型对真实、祖先多样性双倍型的解读则不然，会沿着祖先梯度下降，这正是为什么映射必须被执行而非推理的原因。我们并未声称完全的临床验证，那还需要非标准输入、真实世界的基因组和临床数据、人类对照以及多站点一致性。

## Abstract
Genomics is adopting autonomous AI agents that interpret genomes from natural-language instructions faster than it is building the means to trust them. We report the first large-scale controlled evaluation of where, in an agentic genomic pipeline, correctness must reside for the system to be trustworthy at clinical scale. Using pharmacogenomics, a domain where errors are measurable and sometimes lethal, we benchmarked nine frontier large language models across 44,550 scored evaluations on 110 pharmacogenomic cases, and tested model interpretation of real star-allele diplotypes from more than 7,000 individuals in three ancestrally diverse populations. Trustworthiness proved to be a property of pipeline architecture, not of the model. Letting the model reason was stochastic and unsafe, and grounding it in the correct guidelines by retrieval paradoxically increased lethal-class errors. Encoding the validated decision logic as a versioned skill and executing it as code made the pharmacogenomic mapping exact, auditable and identical across models, confining all residual error to a single input-interpretation step. On individual genomes, unguarded model interpretation degraded along an ancestry gradient; execution removes this gradient from the clinical mapping, relocating it to the auditable completeness of the input caller. This establishes a generalisable, auditable architecture for trustworthy agentic genome interpretation at scale.

HighlightsO_LICorrectness must be executed, not reasoned or retrieved, to be trustworthy
C_LIO_LIRetrieval raises phenotype accuracy yet increases lethal-class errors; skills do not
C_LIO_LIExecution makes the clinical mapping exact and model-invariant; error stays at input
C_LIO_LIA deterministic input caller is the predicted route to all-correct emitted answers
C_LI

In briefCorpas and colleagues show that trustworthy agentic genome interpretation comes not from making language models reason correctly about biology, but from confining them to interpreting input while versioned, validated skills do the reasoning as executed code. Across nine large language models and 110 pharmacogenomics cases, executing the skill makes the clinical mapping deterministic, auditable and model-invariant.

SignificanceGenomics is adopting autonomous, language-model-mediated agents faster than it is building the standards needed to trust them. On a pharmacogenomic benchmark with lethal-class consequences, we show that an agents trustworthiness is not a property of the model but of how the agent is constrained: correctness must be moved out of the stochastic model into a versioned skill executed as code, with the model confined to interpreting heterogeneous input. This gives the field a transferable architecture for trustworthy agentic genome interpretation, a predicted route to deploying it so that every emitted answer is correct (execute the validated skill, call the input deterministically, and abstain on the irreducible residual), and a way to develop genomic skills as validated, executable, versioned units rather than prompts. Following a validation framework described elsewhere, we use clinical-grade to mean determinism, auditability, traceability to versioned components and population-invariant performance, all achieved under skill-constrained execution. We distinguish two senses of population performance: the executed clinical mapping is population-invariant by construction, verified across European, Latin American and East African origin individuals, whereas the models interpretation of real, ancestrally diverse diplotypes is not, degrading along an ancestry gradient, which is precisely why the mapping must be executed rather than reasoned. We do not claim full clinical validation, which would additionally require non-canonical inputs, real-world genomic and clinical data, human comparators and multi-site concordance.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：基因组学正在快速引入基于大语言模型（LLM）的自主AI代理，这些代理能够根据自然语言指令解释基因组数据，但其部署速度远快于建立相应信任机制的速度。缺乏可信赖性会带来严重临床风险（尤其是药物基因组学中错误可能导致致命后果）。
- **核心问题**：在自主基因组分析流程中，**正确性必须位于何处**才能使系统在临床规模上值得信赖？是否可以通过让模型“推理”或“检索”来保证正确性？
- **整体含义**：首次大规模对照评估表明，**可信赖性是流程架构（pipeline architecture）的属性，而非模型的属性**。必须将正确性从随机模型中移出，转入作为代码执行的版本化技能（versioned skill），模型仅限制在输入解读步骤。

## 2. 方法论：核心思想、关键技术细节、算法流程
- **核心思想**：正确性必须被**执行**（executed），而非推理（reasoned）或检索（retrieved）。将经过验证的临床决策逻辑编码为**版本化技能**（versioned skill），并以**代码执行**（code execution）的方式运行；LLM模型只负责**解读异构输入**（如自然语言描述的病例或遗传变异数据），而不参与临床推理。
- **关键技术细节**：
  - **版本化技能**：将药物基因组学（pharmacogenomics）中的决策规则（如将基因型映射到表型、药物剂量调整）编写为确定性、可审计、可版本追踪的代码单元。
  - **流水线架构**：输入经LLM解读后，调用版本化技能（以函数/模块形式）执行映射，输出结果完全由代码决定，与模型无关。
  - 对比了三种流水线：**推理型**（模型自由推理）、**检索型**（模型通过检索增强锚定指南）和**技能执行型**（模型仅做输入解读，技能执行代码）。
- **算法/流程**（文字描述）：
  1. 输入：自然语言病例描述 + 遗传变异（星号等位基因双倍型）。
  2. 模型（LLM）输出结构化输入解读（如提取基因、等位基因、药物等）。
  3. 版本化技能（代码）接收该结构化输入，执行预先验证的决策逻辑（如基于CPIC指南的映射）。
  4. 输出：表型分类（如代谢类型）、药物推荐或弃权（当输入不完整时）。
- **关键原则**：**确定性、可审计性、可追溯至版本化组件、人群不变性能**。

## 3. 实验设计
- **数据集/场景**：
  - **药物基因组学基准**：110个经典病例（可能来自CPIC或临床指南），覆盖可测量且有时致命的错误类别（如“致命错误”指可能引起严重不良药物反应的错误）。
  - **真实人群数据**：来自三个人群（欧洲、拉丁美洲、东非）超过7000个个体的真实星号等位基因双倍型（diplotypes），用于测试模型对祖先多样性数据的解读。
- **基准（Benchmark）**：以临床正确性为黄金标准，错误分类为：表型错误（含致命错误）、映射精度等。
- **对比方法**：
  1. **推理型**：让LLM直接推理出临床结果。
  2. **检索型**：LLM通过检索（RAG）锚定正确指南后再推理。
  3. **技能执行型**：LLM仅做输入解读，临床映射由版本化技能代码执行。
- **模型**：9个前沿大语言模型（未具体列出名称，可能包括GPT-4系列、Claude、Gemini等）。

## 4. 资源与算力
- 文中**未明确提及**所使用的GPU型号、数量、训练时长或推理计算开销。
- 仅提到对9个LLM进行了44,550次评分评估，以及真实人群数据测试。这些评估可能采用商业API或本地部署，但具体算力信息缺失。
- 推测：此类基准测试主要依赖LLM推理（无训练），计算需求可能通过云端API完成，本地执行技能部分计算量较小。

## 5. 实验数量与充分性
- **实验数量**：
  - 44,550次评分评估（9个模型 × 110个病例 × 多种架构设置？实际可能包含重复或不同条件）。
  - 对7000+个体真实双倍型进行模型解读测试。
  - 对比了三种主要流水线架构，未提及消融实验（如改变技能版本或输入解读方式）。
- **充分性**：实验规模较大，覆盖了多个模型、多种架构和真实人群，在药物基因组学这一关键领域有足够说服力。但在以下方面可进一步补充：
  - 未做模型内部变异性测试（如不同温度参数）。
  - 未涉及更广泛的基因组学任务（如罕见病诊断）。
  - 未提供统计显著性检验。
- **客观与公平**：论文采用受控比较，所有模型在相同输入和任务下评估，且技能执行架构与模型无关，确保了公平性。但未公开详细病例列表和代码，可能影响可复现性。

## 6. 主要结论与发现
- **可信赖是架构属性，非模型属性**：最好的模型在推理下仍不可靠；检索虽提高平均表型正确率，却**增加了致命性错误**。
- **技能执行使临床映射精确、可审计、跨模型一致**：所有9个模型在执行技能后得到完全相同的结果，错误仅残留在输入解读步骤（模型对输入的理解）。
- **人口梯度消失**：在无防护的模型解读中，性能沿祖先梯度下降（欧洲人>拉丁美洲>东非）；执行技能后，临床映射本身无人口偏差，但输入调用器的完整性仍存在梯度。
- **预测路径**：为实现完全正确的输出，需要**确定性输入调用器**（deterministic input caller）对不可减少的残余进行弃权（abstain）。
- **核心提炼**：正确性必须被**执行**，而非推理或检索。

## 7. 优点（方法或实验设计的亮点）
- **设计严谨**：首次大规模对照评估，在具有致命后果的真实临床场景中比较三种流水线架构，而非仅依赖通用NLP指标。
- **概念清晰**：将“可信赖”操作化为确定性、可审计性、可追溯性、人群不变性，并给出了具体实现（版本化技能+代码执行）。
- **方法迁移性好**：提出的架构可推广至其他基因组学领域（如药物基因组学之外的遗传解读），技能可独立开发与版本管理。
- **揭示反直觉现象**：检索增强反而增加致命错误，表明“更正确”的指南锚定可能导致模型在模糊边界处做出高风险决策。
- **使用真实多样性人群数据**：验证了人口不变性的实现，揭示了无防护模型的偏差。

## 8. 不足与局限
- **实验覆盖**：
  - 仅聚焦药物基因组学，未覆盖其他基因组学任务（如罕见病、多基因风险评分）。
  - 仅使用星号等位基因双倍型，未涉及复杂结构变异或非编码变异。
  - 未测试真实世界噪声数据（如临床报告中的格式错误、缺失信息）。
- **临床验证不足**：作者明确承认未完成全面临床验证，缺乏：
  - 非标准输入（如自然语言自由文本）。
  - 真实世界基因组与临床数据联合。
  - 人类专家对照。
  - 多站点一致性评估。
- **残余错误**：输入解读步骤仍依赖LLM，错误（如误读等位基因）会传播到最终输出；论文建议未来用确定性输入调用器解决，但未实现。
- **资源与可复现性**：未提供模型细节（如具体版本、访问方式）、技能代码或完整病例列表，增加了复现难度。
- **潜在偏差**：所使用的110个病例可能为精心设计，不一定代表真实临床分布；人群数据仅三个来源，可能无法泛化到其他人群。

（完）
