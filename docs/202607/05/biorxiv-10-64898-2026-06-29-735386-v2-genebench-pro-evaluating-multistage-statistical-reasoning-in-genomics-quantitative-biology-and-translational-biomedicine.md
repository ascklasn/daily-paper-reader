---
title: "GeneBench-Pro: Evaluating Multistage Statistical Reasoning in Genomics, Quantitative Biology, and Translational Biomedicine"
title_zh: GeneBench-Pro：评估基因组学、定量生物学和转化生物医学中的多阶段统计推理
authors: "Li, J. H., Ho, A. J."
date: 2026-06-30
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.29.735386v2.full.pdf"
tags: ["query:agent"]
score: 9.0
evidence: 基因组学和转化生物医学中AI agent的基准测试，评估多阶段推理
tldr: "AI在基因组学、定量生物学和转化生物医学中面临多阶段统计推理挑战。GeneBench-Pro基准测试扩展了GeneBench，纳入129个跨领域问题，要求代理自主导航分析流程。评估显示最强模型GPT-5.6 Sol Pro仅达31.5%通过率，模型常识别局部信号却未能转化为正确分析决策。该基准衡量了长期生物学推理能力，揭示了当前模型在此类任务中的可靠性不足。"
source: biorxiv
selection_source: fresh_fetch
motivation: 评估AI代理在复杂多阶段科学分析中的真实统计推理能力，尤其在基因组学等生命科学领域。
method: 构建包含129个多阶段推理问题的基准，问题涉及10个主要领域和21个子领域，要求代理自主完成完整分析工作流。
result: "最强模型GPT-5.6 Sol Pro通过率31.5%，Claude Opus 4.8为16.0%，模型在决策传播环节存在系统性失败。"
conclusion: 当前AI在长期生物学推理中仍不可靠，GeneBench-Pro为评估新兴推理能力提供了关键基准。
---

## 摘要
我们推出了GeneBench-Pro，这是GeneBench的扩展和改进版本，包含跨更广泛领域的更难问题。GeneBench-Pro是一个基准测试，用于评估AI智能体在基因组学、定量生物学和转化生物医学中执行逼真的多阶段科学分析的能力，旨在捕捉计算生命科学家在必须得出一个下游科学或转化决策所依赖的结论时所面临的现实问题的复杂性。该基准包含129个评估，针对10个主要领域和21个终端子领域中具有直接实际相关性的量，以基因组学为核心。与GeneBench类似，每个问题为智能体提供简要背景、一个目标估计量和最小的其他指导；然后智能体必须导航多个依赖决策点，即实质性的推断分支，在这些分支中一个看似合理但错误的选择会改变下游分析，以识别并执行正确的分析工作流并得出正确答案。相对于GeneBench，GeneBench-Pro新增了29个问题，删除了三个问题，并对剩余100个重叠问题中的54个进行了显著重新设计。129个问题中有82个经过外部领域专家审查，他们的发现导致了对目标不够明确的问题的提示/数据修改和重新设计。十个经过外部审查的问题公开发布，50个预留问题提供给Artificial Analysis进行独立的第三方模型基准测试，其余问题保留为内部预留集。在对全部129个问题的评估中，GPT-5.6 Sol在最大推理级别的评估级通过率达到28.7%，而GPT-5.6 Sol Pro在单独报告的GPT Pro运行中达到31.5%。GPT-5.5达到12.0%，GPT-5.4达到8.9%，最强的非GPT基线Claude Opus 4.8达到16.0%。与GeneBench一样，模型通常能完成工作流的相当大部分，但在注意与行动之间存在一致差距：它们识别出局部诊断信号，但未能将影响传播到相应的分析决策。因此，模型常常选择错误的估计量，或坚持最初看似合理但实际不正确的分析路径。因此，GeneBench-Pro衡量了一种仍不可靠的新兴能力：长视界生物推理。

## Abstract
We introduce GeneBench-Pro, an expanded and improved version of GeneBench that comprises harder problems across a wider breadth of domains. GeneBench-Pro is a benchmark for AI agents performing realistic multi-stage scientific analyses in genomics, quantitative biology, and translational biomedicine which seeks to capture the complexity of real-world problems that computational life scientists face when tasked with producing a conclusion upon which a downstream scientific or translational decision is contingent. The benchmark comprises 129 evaluations targeting quantities of direct practical relevance across 10 primary domains and 21 terminal subdomains, with a genomics-centered core. Similarly to GeneBench, each problem provides the agent with brief context, a target estimand, and minimal guidance otherwise; the agent must then navigate multiple dependent decision points; i.e., substantive inferential forks where a plausible wrong choice changes the downstream analysis, to identify and execute the correct analysis workflow and arrive at the correct answer. Relative to GeneBench, GeneBench-Pro adds 29 new problems, drops three, and introduces significantly redesigned versions of 54 of the remaining 100 overlapping problems. 82 of the 129 problems were reviewed by external domain experts, whose findings led to prompt/data modifications and redesign of those problems whose targets were not sufficiently identifiable. Ten externally reviewed problems are released publicly, 50 held-out problems were provided to Artificial Analysis for independent third-party model benchmarking, and the remainder are retained as an internal holdout. In evaluations over the full 129-problem suite, GPT-5.6 Sol reaches an eval-level pass rate of 28.7% at the max reasoning level, and GPT-5.6 Sol Pro reaches 31.5% in separately reported GPT Pro runs. GPT-5.5 reaches 12.0%, GPT-5.4 reaches 8.9%, and the strongest non-GPT baseline, Claude Opus 4.8, reaches 16.0%. As with GeneBench, models often complete substantial portions of the workflow but exhibit a consistent gap between noticing and acting by identifying local diagnostic signals but failing to propagate the implications to the corresponding analysis decision. As a result, models often select wrong estimators or persist on initially plausible but incorrect analysis paths. GeneBench-Pro therefore measures an emerging capability of long-horizon biological reasoning that remains unreliable.

---

## 论文详细总结（自动生成）

# GeneBench-Pro：评估基因组学、定量生物学和转化生物医学中的多阶段统计推理

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：当前AI在软件工程等任务上表现强劲，但在生命科学领域，真正的瓶颈是执行多步骤、决策密集的量化分析——从可能有错误的原始数据出发，经过一系列包含统计推理和战略判断的流程，最终得到影响科研或转化决策的结论。现有基准大多只覆盖窄范围的、预设好清洗数据的单步分析，而真实科研工作更加开放、迭代且充满歧义。
- **整体意义**：GeneBench-Pro旨在填补这一空白，评估AI智能体能否自主完成**多阶段统计推理**——即从接收潜在错误的数据、进行质量控制与探索分析、选择模型与估计量、诊断并调整流程，最终输出可影响下游决策的定量答案。该基准测量的是“长期生物推理”这一新兴但尚不可靠的能力。
- **背景**：基因组学等领域数据生成成本急剧下降，但分析能力成为瓶颈；人类遗传学证据在药物靶点优先排序中的作用日益显著，可靠自动化分析有望极大加速科学研究与转化。

## 2. 方法论：核心思想、关键技术细节

### 核心思想
- 通过**构造性模拟数据**而非真实数据，确保每个问题有唯一可恢复的正确答案，避免因真实数据存在多种合理选择而导致的评判歧义。
- 每个问题模拟一个**多决策点**的推理链条：智能体必须从模拟的“脏”数据中识别出当前阶段应做的决策（如QC阈值、估计量选择、模型修正），且错误决策会传播至下游，导致最终答案错误。

### 关键技术细节
- **问题结构**：
  - 提供“最小可行提示”（MVP）：给出实验背景与目标估计量，但不规定具体分析步骤。
  - 数据以原始表格/文件形式提供（如受检者名册、质控对照、检测观察值等），模拟实验室或临床系统输出的非清洗数据。
  - 代理在隔离环境中操作，可访问标准科学Python库（numpy, pandas, scipy, sklearn, statsmodels, lifelines）及常用生信工具（PLINK, bedtools, pysam等），但无互联网连接。
- **多阶段推理**：每个问题包含3~13个依赖决策点（中位数6个），例如：
  - 在携带者筛查问题中，需先辨认报告性缺失 vs 重复片段模拟、处理相位标记、估算检测灵敏度/假阳性率，再计算残余风险，最后标准化至完整伴侣名册。
- **验证与评分**：
  - 二进制评分：只有所有字段均落在预设容差内才算通过。不提供部分分数。
  - 每个问题对每种模型进行多次独立尝试（标准组10次，Pro组5次），剔除容器/工具/格式错误的运行后计算通过率。
  - 通过消融实验验证：所有合理但错误的路径都会产生明显不同的答案，确保分数线有意义。
- **外部科学评审**：82个问题（占全部129个）由11位领域专家审查，评审内容包括可辨识性、方法实现、现实性等。根据反馈修改提示、数据甚至重新设计问题。公开的10个问题均经过评审。

## 3. 实验设计

### 数据集与场景
- **基准规模**：129个问题，覆盖10个主要领域及21个终端子领域（遗传学核心、定量遗传学、翻译与专科场景、微生物与法医基因组学、分子组学等）。
- **具体场景举例**：携带者筛查残余风险计算、药物基因组学中的时间-事件分析、条件细胞类型遗传力估计、桥校准肽pQTL分析等。
- **数据来源**：全部为构造性模拟数据，通过已知的因果结构生成，确保正确答案可从代理可见数据中恢复。

### 对比方法
- **模型族**：
  - OpenAI GPT系列：GPT-5.2, GPT-5.4, GPT-5.5, GPT-5.6 Luna/Terra/Sol，以及对应的Pro（Extended）版本。
  - 非GPT模型：Claude Opus 4.8, Gemini 3.1/3.5, Grok, GLM, Kimi, DeepSeek, MiMo, Tencent, MiniMax, Qwen等。
- **推理级别**：对于GPT系列，设置了`none`、`low`、`medium`、`high`、`xhigh`、`max`共6个推理级别，以考察推理计算量对表现的影响。
- **评测方式**：每个模型-问题对运行10次（标准）或5次（Pro/Claude Opus），统计平均通过率及分布。

## 4. 资源与算力

- **论文未明确说明**使用的具体GPU型号、数量或训练时长。仅提及评估在Docker容器内的Linux环境中进行，使用标准科学计算栈，无互联网访问。未涉及模型训练过程，仅针对已有模型进行推理评测。
- 因此，无法提供算力细节。

## 5. 实验数量与充分性

- **实验数量**：共评估了60个模型配置，每个配置在129个问题上运行多次，合计实验次数巨大（标准组10×129=1290次/模型，Pro组5×129=645次/模型）。所有模型-问题对均执行。
- **消融与验证**：
  - 每个问题设计时包含消融分析：验证各种合理但不正确的分析路径是否能产生显著不同的答案，确保评分唯一性。
  - 通过外部评审（82个问题）确保科学合理性与可辨识性。
  - 对公开问题提供详细设计报告、数据生成过程、验证证据等。
- **充分性评价**：
  - **充分**：问题覆盖广泛领域，决策点数量从3到13，难度梯度合理；多次运行减少随机性；二进制评分严格，避免主观性；外部评审增加了科学可信度。
  - **局限**：二进制评分丢失了部分中间步骤的进展信息；模拟数据虽保证可辨识性，但缺乏真实数据中的文档缺口、规模效应和特异性不规则。

## 6. 主要结论与发现

- **整体表现仍低**：最强模型GPT-5.6 Sol Pro在最大推理级别下仅达到31.5%的通过率，纯主系列GPT-5.6 Sol达到28.7%。非GPT基线中Claude Opus 4.8最好（16.0%）。说明基准远未饱和。
- **推理级别影响显著**：对GPT-5.6 Sol，通过率从`none`的3.7%升至`max`的28.7%，表明增加推理计算量能显著提升表现。
- **“注意-行动”差距**：模型往往能识别局部诊断信号（如数据问题、统计异常），但未能将这些信号转化为具体的分析决策变更。例如，在药物基因组学问题中，模型可能注意到时间依赖的混淆，但无法采用适当的水疗（marginal structural model）处理。
- **模型进步方向**：更强模型（GPT-5.6 Sol相对GPT-5.5）的主要改进不在于发现信号，而在于将信号传播到下游分析方法的选择上。
- **剩余困难问题**：即使在最强模型中，仍有约46%的问题通过率为0%，仅30%的问题通过率超过50%。

## 7. 优点

- **问题设计独创性**：使用构造性模拟数据，使每个问题只有唯一可恢复的正确答案，避免了真实数据中多解性导致的评审难点。同时模拟数据的参数可精细控制错误类型、效应大小等，确保多阶段推理的链条清晰。
- **真实工作流模拟**：代理面对的是“脏”的原始数据（如未清洗的表格、模拟的批次效应、缺失值等），需要自主决定QC、模型选择、诊断与修正，贴近真实科研场景。
- **严谨的验证流程**：通过外部专家评审、消融实验、多轮agent试点和痕迹分析确保问题的科学合理性和难度恰定性。二进制评分与容差设置避免主观。
- **覆盖领域广**：从群体遗传学到临床遗传学、药物基因组学、癌症基因组学、蛋白质组学、微生物组学等10个主要领域，21个子领域，具有较好的代表性。
- **分层发布**：公开10个问题供社区使用，50个预留用于第三方独立评估，其余作为内部预留，有助于防止基准过拟合。

## 8. 不足与局限

- **模拟数据的局限性**：虽然模拟保证了可辨识性，但无法完全复现真实数据中的文档缺口、数据规模（例如百万级样本的UK Biobank）、以及分析者可能面临的真实不规则情况（如实验记录缺失、协议偏差等）。因此，在模拟上表现好不一定直接对应真实科研场景中的可靠性。
- **二进制评分丢失信息**：只有最终答案正确才记通过，对于完成了大部分正确步骤但最终错误的问题，无法提供中间进展的反馈。论文提及未来可能引入阶段级评分。
- **仅覆盖假设驱动分析型任务**：基准聚焦于QTL分析、遗传力估计、残留风险计算等“假设驱动”的统计推理，未涵盖实验设计、实验验证、或更开放的探索性科学（如假设生成），也未涉及湿实验交互。
- **决策点数量作为定性指标**：虽然每个问题有3-13个决策点，但论文未将这些数字作为严格的性能预测变量，只是作为设计元数据。
- **模型不可知性**：评估仅覆盖了有限的模型家族（主要是GPT系列与非GPT商业模型），未包含社区提出的开源agent系统或专门科学agent（如论文引用的REVERE等）。但考虑到领域，这属于当前常态。
- **成本估算粗略**：论文中提到一个人工完成一个问题约需10-40小时、100-200美元/小时，但未提供详细计算依据。
- **隐藏假设**：外部评审的82个问题被指出存在隐含假设或模糊的估计定义，虽已修正，但可能仍有未发现的问题影响某些问题的可辨识性。

（完）
