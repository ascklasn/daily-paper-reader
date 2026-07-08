---
title: Benchmarking large language models for ACMG/AMP variant interpretation and variant calling
title_zh: 评测大型语言模型在ACMG/AMP变异解读和变异检出中的表现
authors: "Corpas, M."
date: 2026-07-05
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.30.735646v1.full.pdf"
tags: ["query:agent"]
score: 9.0
evidence: 用于基因组变异解读的代理式LLM基准ClawBench
tldr: 基因组工作流中，智能体大语言模型在变异调用和临床解读中的应用仅以准确率评估，无法揭示流程中的故障来源。ClawBench框架通过时间盲化truth集和失败闭合证据合约，在完整管线中归因每个结果至产生它的架构层，评估有效性、安全性、溯源性和可重复性。结果表明危险误分类罕见且模型不变，不同变异类别受不同层速率限制，变异调用的差异在于信任属性而非能力。该框架证明可信赖性是管线架构属性，而非模型本身，为领域提供了可移植、抗污染的归因单元。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有评估仅用准确率单一指标，无法判断系统安全性及故障来源，需要能归因失败于架构层的全面基准。
method: 提出ClawBench框架，采用时间盲化truth集和失败闭合证据合约，评估有效性、安全性、溯源性和可重复性。
result: 危险误分类罕见且模型不变；LOF变异受阈值限制，错义受证据形成限制；调用差异源于信任属性，开源模型有合规差距。
conclusion: 相同结果可源于不同故障模式，可信赖性是管线架构属性而非模型，ClawBench提供抗污染的归因单位。
---

## 摘要
智能体式大型语言模型越来越多地应用于基因组工作流程，从变异检出到临床解读，然而它们仅通过准确性这一单一指标进行评估，该指标无法说明系统是否安全，也无法指出工作流程中故障的起源。我们提出了ClawBench框架，该框架将每个结果归因于产生它的架构层，横跨标准管道的两部分。两个设计选择消除了使智能体基因组学难以评估的混淆因素：一个时间盲化的真相集，其中每个评分的ClinVar标签仅在所有被测试模型的训练截止日期之后才首次可用；以及一个故障封闭的证据契约，阻止证据与真相标签形成循环。我们在约束梯度下评估有效性、安全性、来源和可重复性，而不仅仅是准确性，该约束梯度将正确性从模型先验转移到执行和验证的代码中。

我们展示了三点。第一，危险的错误分类罕见且与模型无关，是执行架构的控制先决条件而非前沿，而编造的证据是可测量的，并通过执行被中和。第二，不同的变异类别受到不同层的速率限制：功能丧失变异受确定性组合器阈值的限制，稀有错义变异受证据形成的限制，其中证据获取是不对称且有上限的，而强度分配是一个可恢复的层，朴素的强度许可提示会混淆它。第三，对于变异检出，不同模型之间的区别不在于它们是否能规划一个管道（所有模型都能），而在于信任属性：固定性、来源、可审计性和可重复性，这些属性向验证执行单调递增；一个本地的开放权重模型重现了安全结果，但满足结构化输出和来源契约的频率远低于前沿模型，这体现的是符合性差距而非能力或安全差距。端到端的连接将失败归因于整个工作流程，将一个未检出的变异与传播的基因型错误以及一个正确检出但错误解读的变异区分开来。

ClawBench表明，表面上相同的结果源于不同且可独立测量的失败模式，并且智能体基因组学中的可信度是管道架构的属性而非模型的属性，为该领域提供了一个可移植、抗污染的归因单元。

## Abstract
Agentic large language models are increasingly used across the genomic workflow, from variant calling to clinical interpretation, yet they are evaluated by accuracy alone, a single figure that cannot say whether a system is safe or where in the workflow a failure originates. We present ClawBench, a framework that attributes each outcome to the architectural layer that produced it across both halves of the canonical pipeline. Two design choices remove the confounds that make agentic genomics hard to evaluate: a temporally blinded truth set, in which every scored ClinVar label first became available only after the training cutoff of every model tested, and a fail-closed evidence contract that blocks evidence circular with the truth label. We score validity, safety, provenance and reproducibility, not accuracy alone, under a constraint gradient that relocates correctness from a models prior into executed, validated code.

We show three things. First, dangerous misclassification is rare and model-invariant, a controlled precondition of the executed architecture rather than a frontier, while fabricated evidence is measurable and is neutralised by execution. Second, different variant classes are rate-limited by different layers: loss-of-function variants by the deterministic combiner threshold, and rare missense by evidence formation, where evidence acquisition is asymmetric and capped and strength assignment is a recoverable layer that naive strength-licensing prompts confound. Third, for variant calling the arms separate not on whether a model can plan a pipeline, which all do, but on trust properties, pinning, provenance, auditability and reproducibility, which climb monotonically toward validated execution; and a local open-weight model reproduces the safety result yet meets the structured-output and provenance contract far less often than frontier models, a conformance gap rather than a capability or safety gap. An end-to-end join attributes failures across the whole workflow, separating a missed call from a propagated genotype error from a correctly called but misinterpreted variant.

ClawBench shows that apparently identical outcomes arise from distinct, independently measurable failure modes, and that trustworthiness in agentic genomics is a property of the pipeline architecture rather than of the model, providing a portable, contamination-resistant unit of attribution for the field.

---

## 论文详细总结（自动生成）

# 论文详细总结：Benchmarking large language models for ACMG/AMP variant interpretation and variant calling

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：智能体式大型语言模型（Agentic LLMs）正被用于基因组变异解读与变异检出，但这些系统的评估仅依赖“准确率”单一指标。该指标无法判断系统是否安全，也无法指明故障在流程中的具体来源。例如，一个误分类的变异可能导致治疗不当或延误。
- **背景问题**：现有基准存在两大混淆因素：一是模型可能在预训练中记忆了变异的公开分类（数据污染）；二是从同源数据库（如ClinVar）检索证据会形成循环，夸大表面能力。
- **核心需求**：需要一个能归因每个输出到具体架构层、排除污染和循环证据、并评估安全性、来源、可重复性等多维度的框架。

## 2. 论文提出的方法论：核心思想、关键技术细节、算法流程

### 核心思想
- **ClawBench框架**：将变异解读管线划分为三个模块（安全控制、证据形成、决策形成），共六个层次，每个输出来自特定层。用约束梯度（constraint gradient）逐步将正确性从模型先验转移到已验证执行的代码中。

### 关键技术细节
1. **时间盲化真相集（Temporally Blinded Truth Set）**：
   - 只使用在**所有被测试模型训练截止日期之后**才首次可用的ClinVar标签。
   - 采用“首次可用性”确定机制：通过连接ClinVar提交历史，仅当证明标签首次出现晚于有效截止日期才纳入。
   - 有效截止日期：最晚模型截止日期（GPT-5.2: 2025-08-31） + 90天安全余量 → 2025-11-29。
   - 结果：从166,437个候选条目中筛选出**6,929个时间盲化变异**，所有标签距模型训练截止至少91天。

2. **故障封闭证据契约（Fail-Closed Evidence Contract）**：
   - 在技能执行（skill-execution）条件下，模型输出必须满足机器可读契约。
   - 禁止使用断言代码（PP5, BP6），禁止证据来源为ClinVar（PS1, PM5），禁止与真相标签同源的证据家族（ClinGen Expert Panels, LOVD）。
   - 违反任一规则则提交无效（fail-closed），而非宽容解释。

3. **约束梯度条件**：
   - **自由（free）**：仅凭模型先验返回分类。
   - **技能推理（skill-reasoning）**：模型基于固定临床变异报告规范推理。
   - **技能执行（skill-execution）**：模型仅返回结构化ACMG证据代码，由确定性引擎组合。
   - **真相提供（truth-supplied）**：作为上限对照。

4. **归因机制**：
   - 从技能执行复现中为每个变异计算四个标志，映射到架构层：
     - `safety_clean`：无致命错误（良性与致病互换）。
     - `combiner_sensitive`：不同组合器（Richards规则 vs Tavtigian积分系统）给出不同模态类别。
     - `assignment_unstable`：不同复现给出不同证据集。
     - `evidence_insufficient`：真相确定但确定性引擎仍返回VUS（证据不足）。
   - 按优先级归因：危险 > 证据不足 > 组合器敏感 > 赋值不稳定 > 已解决。

5. **确定性组合器**：
   - Richards规则计数逻辑和Tavtigian积分系统（自然标定：非常强8分，强4分，中等2分，支持1分，良性代码取负，总分映射类别）。

6. **获取臂（Acquisition Arm）**：在技能执行条件下，提供给模型完整、真实、非循环的外部证据（Ensembl VEP注释、校准的REVEL、AlphaMissense等），检验获取层对减少证据不足的作用。

7. **校准臂（Calibration Arm）**：在获取臂基础上增加一条指令（PM2应使用2015年基线中等强度而非SVI 2020降级），检验强度分配是否可恢复。

### 算法流程（文字描述）
- 输入：变异坐标、基因、参考基因组。
- 步骤1：根据时间盲化真相集筛选出待测变异。
- 步骤2：在三个约束条件（自由、技能推理、技能执行）下使用模型生成输出。
- 步骤3：技能执行输出进入故障封闭契约验证 → 有效代码集。
- 步骤4：有效代码集分别通过两个确定性组合器得到两个分类。
- 步骤5：计算四个归因标志，输出每个变异的层归因标签。
- 步骤6：对稀有错义变异执行获取臂和校准臂对比实验。
- 步骤7：对GIAB基准样本执行变异检出任务，评估信任属性（固定性、来源、可审计性、可重复性）。

## 3. 实验设计：数据集、场景、基准、对比方法

### 数据集
- **ClinVar变异解读**：使用ClinVar 2026-06-15快照，筛选两星及以上GRCh38变异，共6,929个时间盲化变异。其中分三档：
  - Tier A（功能丧失或常见，高自动化潜力）：894个。
  - Tier B（错义或其他蛋白质改变，中等）：2,906个。
  - Tier C（同义、内含子等）：3,129个。
- **GIAB变异检出**：使用Genome in a Bottle (GIAB) 标准样本（HG002、HG003、HG004等），染色体20作为开发测试。

### 场景（实验设置）
- **解读实验**：
  - 核心归因：从Tier A中抽取231个变异，由三个前沿模型（GPT-5.2、Claude Sonnet 4.5、Gemini 2.5 Flash）分别在自由、技能推理、技能执行条件下各做5次复现（共231×3×3×5约10,395次调用）。
  - 归因语料库：281个变异（501个LoF、195个错义、147个其他），跨3个模型共843条记录。
  - 获取臂：27个Tier B稀有错义变异（24个确定 + 3个VUS对照），使用Claude Sonnet 4.5（5次复现），对比薄证据（仅遗传后果+群体频率）与富证据（完整VEP校准注释）。
  - 校准臂：相同27个变异，加上PM2强度指令，Claude Sonnet 4.5 + GPT-5.2各5次复现。
- **变异检出实验**：
  - 四个臂：自由、技能推理、技能执行（调用nf-core/sarek + GATK HaplotypeCaller）、人工最佳实践参考。
  - 在GIAB HG002 chr20上运行，使用rtg vcfeval评分，预注册8种故障标签。
  - 开放权重臂：Qwen 3.6 35B本地模型，在231个Tier A变异上运行（单次复现）。

### 基准
- 主要对比维度：准确率（5级一致率）、危险错误率、编造证据率、归因层分布、信任属性（引脚固定、来源、可审计性、可重复性）。

### 对比方法
- 模型间：GPT-5.2 vs Claude Sonnet 4.5 vs Gemini 2.5 Flash vs Qwen 3.6 35B。
- 条件间：自由 vs 技能推理 vs 技能执行。
- 组合器间：Richards规则 vs Tavtigian积分系统。

## 4. 资源与算力

- **文中未明确说明具体GPU型号、数量、训练时长或推理耗电**。
- 提到的资源：模型通过统一适配器调用（处理限流和重试）；开放权重模型Qwen 3.6 35B在本地设备上运行（on-device），使用冻结核验权重。前沿模型通过付费API调用。
- 注意：论文强调框架可移植、不依赖付费端点，开放权重模型使得基准可在本地复现。

## 5. 实验数量与充分性

### 实验数量
- **核心解读实验**：231个Tier A变异 × 3个模型 × 3个条件 × 5复现 = 约10,395次模型调用（最终报告可评分数量各异，如Claude Sonnet 4.5技能执行1150/1155份可评分）。
- **归因语料库**：281个变异 × 3模型 = 843条归因记录。
- **获取臂**：27个变异 × 2个条件（薄/富） × 5复现 = 270次调用。
- **校准臂**：27个变异 × 3个条件（薄/富/校准） × 2个模型（Claude+GPT） × 5复现 ≈ 810次调用（部分条件）。
- **变异检出**：GIAB chr20上4个臂 × 数种预注册标签分析，另加开放权重单次复现。

### 充分性与公平性
- **充分性**：实验设计系统，覆盖了解读和检出两大环节，包含多模型、多条件、多复现，并专门设计获取和校准消融实验。但存在局限（见第8点）。
- **公平性**：
  - 时间盲化确保标签无污染。
  - 故障封闭契约防止循环证据。
  - 模型适配器统一处理错误与限流，避免掩蔽问题。
  - 开放权重臂证明基准不依赖付费API。
  - 但开放权重仅单次复现，复现变异性未知；变异检出仅在chr20上验证，未覆盖全基因组。

## 6. 论文的主要结论与发现

1. **准确率不足以评估安全性**：所有条件的5级一致率约48-55%，但危险误分类率仅0.3-2.2%，且模型间差异小，属于“受控先决条件”而非前沿能力。
2. **编造证据可测量且可通过执行中和**：Claude Sonnet 4.5编造率0%，GPT-5.2 17%，Gemini 2.5 Flash 13%的提交包含ClinVar来源的编造代码。在技能执行下，这些编造代码被契约剥离，转化为安全弃权（不确定意义），危险率未升高。
3. **不同变异类别受不同层速率限制**：
   - 功能丧失（LoF）变异：74%对组合器阈值敏感（Richards规则 vs 点系统差异，主要针对PVS1+PM2配置）。
   - 稀有错义变异：55%证据不足（真相确定但模型无法形成足够证据），其次是赋值和校准问题。
   - 安全意识在所有类别中为99-100%。
4. **获取层是真实但不对称且有上限的**：在24个确定稀有错义变异中，提供甲骨文证据只解决了7个（全部在良性侧），致病侧无进展。理论上限为9/24（因非循环证据可达到的点数有限）。
5. **强度分配层可通过确定性重评分恢复，但朴素提示易受提示混淆**：将PM2从支持调至中等强度（2015基线）可恢复2个致病变异，且良性无退化。然而，直接提示模型“使用中等”会导致模型将其应用到其他变异（良性侧误用），造成净恶化。因此强度分配层是可恢复的（通过架构干预），而非模型自身更好表现。
6. **变异检出中信任属性而非能力区分不同臂**：所有模型都能规划正确流程（计划有效性无差异），但自由代理无固定、无来源、不可审计；技能执行臂在所有信任维度上通过。开放权重模型重现了安全性，但在结构化输出和来源契约上高比例不合格（93%被拒绝），体现的是符合性差距而非能力差距。
7. **端到端归因可行性**：将检出层与解读层连接，可将一个变异的失败归因于“未检出”“传播基因型错误”“正确检出但解读层限制”或“危险误分类”。在GIAB样本上重叠的16个变异均为良性，缺少致病端到端案例，但方法论成立。

## 7. 优点

- **创新性**：提出层归因框架替代单一准确率，首次系统分离智能体基因组学中的多个独立故障模式。
- **方法严谨性**：时间盲化+故障封闭契约有效解决了数据污染和循环证据两大混淆，成为可移植、抗污染的基准。
- **全面评估**：涵盖安全性、可复现性、来源、可审计性等多维度，而不仅仅是准确率。
- **实用导向**：框架可被任何实验室应用于自己的智能体管道中，找出限制其变异的层，与模型无关。
- **公平性考量**：开放权重模型使得基准不依赖付费API，社区可自由复现；预注册故障标签和确定性分类器减少自由度。
- **消融实验设计**：获取臂和校准臂分离证据形成中的获取与强度分配子层，并且排除提示泄漏影响。
- **结果透明**：报告了编造率、无效提交率等负面指标，而非仅报告理想结果。

## 8. 不足与局限

- **变异检出实验仅限于chr20**：未覆盖全基因组，也未进行多样本交叉主机可复现性测试。
- **开放权重模型仅单次复现**：无法估计变异性，且执行臂覆盖率低（93%被拒）限制了结论的统计效力。
- **端到端归因缺乏致病案例**：由于GIAB样本来自健康个体，重叠均为良性，无法展示真实致病变异的联合归因。可考虑使用临床队列或可控插入。
- **Eequity分析仅基于1-2个基因组**：声称F1无大差异但精度和假阳性率存在差异，作者指出样本量不足，无法做出人群级结论。跨度仅欧洲、德系犹太、东亚，缺少非洲、南亚、美洲原住民等。
- **时间盲化仅排除标签记忆**：模型仍可能接触过底层证据（如人群频率、功能数据），这些不属于评估目标回路但难以完全排除。
- **组合器敏感性分析仅使用一种PVS1原子强度**：未考虑PVS1自身强度决策树（可进一步细化LoF类归因）。
- **校准臂的双模型结果源于算术属性而非独立经验复制**：两个模型提交的代码集结构相似，导致重评分结果一致，不构成独立复制。
- **技能执行下无效提交率较高（尤其是Gemini 44.8%和Qwen 92.6%）**：这本身是测量结果，但也意味着许多模型无法通过契约，基准的“技能执行”条件可能对某些模型过严。

（完）
