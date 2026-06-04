---
title: "MedMisBench: Measuring Epistemic Resilience of LLMs Under Misleading Medical Context"
title_zh: MedMisBench：衡量LLMs在误导性医疗语境下的认知韧性
authors: "Zhou, H., Zou, X., Wu, J., Wu, S., Segal, B. M., Niebuhr, T. E., Amro, S., Petrus, M., Momin, S., Cardoso Pinto, A., Niesen, R., Wegner, L. S., Darji, D., Koo, J. M., Fieggen, J., Narain, K., Zeng, M., Clifton, L., Shapiro, L., Liu, F., Clifton, D. A."
date: 2026-05-28
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.25.727671v1.full.pdf"
tags: ["query:agent"]
score: 8.0
evidence: 在误导性医疗上下文下测量LLM韧性
tldr: "大语言模型在医学考试中表现优异，但患者常将其建议用于健康决策。然而，当注入误导性上下文时，模型放弃正确答案的现象普遍存在。为此，我们构建了MedMisBench测试集，包含10,932个医学问题和48,889对误导上下文，发现模型准确率从71.1%骤降至38.0%，攻击成功率51.5%，其中权威性虚假信息攻击成功率达69.5%。该基准揭示了现有评估忽视认知韧性的盲点，对医疗AI安全评估具有重要警示意义。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有医学评估只测量知识掌握程度，忽略模型在误导信息下保持正确判断的能力。
method: 构建MedMisBench数据集，含1万+医学问题和4.8万误导上下文对，通过注入权威性、例外等类型虚假信息测试模型韧性。
result: "11个模型配置下，误导攻击成功率达51.5%，准确率下降33.1个百分点；临床专家评估38.2%案例存在严重潜在危害。"
conclusion: 需将认知韧性纳入医学LLM评估体系，现有高评分不代表安全临床决策能力。
---

## 摘要
大型语言模型（LLMs）现已在医学执照考试中达到专家级分数，这促使人们产生一种假设，即高分意味着安全的医疗判断，而患者越来越多地使用它们来获取健康建议。我们证明了这一假设是脆弱的：当误导性语境被注入到LLMs原本能正确回答的问题中时，它们会放弃正确答案。我们将这种在对抗性语境下保持正确判断的能力称为认知韧性，并引入了MedMisBench来衡量这一能力。MedMisBench包含10,932个医学问题项和48,889个误导性语境-选项对，涵盖医学推理、代理能力和患者旅程评估。在11种模型配置下，原始问题的平均准确率从71.1%下降至焦点误导语境下的38.0%，攻击成功率为51.5%。最具破坏性的注入是正式的、像规则一样的虚构内容：权威框架下的虚假信息攻击成功率达到69.5%，例外毒化主张达到64.1%。一个由来自7个国家的14名临床医生组成的专家小组在38.2%的审查案例中识别出严重的潜在危害。MedMisBench暴露了LLMs在医疗环境评估中的一个结构性盲点：现有基准衡量的是模型知道什么，而不是它们在误导性语境下是否能保持正确的医疗判断。

## Abstract
Large language models (LLMs) now reach expert-level scores on medical licensing exams, encouraging the assumption that high scores imply safe medical judgment while patients increasingly use them for health advice. We show this assumption is fragile: when misleading context is injected into questions that LLMs originally answer correctly, they abandon the correct answer. We call the ability to maintain correct judgment under adversarial context epistemic resilience, and introduce MedMisBench to measure it. MedMisBench contains 10,932 medical question items and 48,889 misleading context-option pairs spanning medical reasoning, agentic capability, and patient-journey evaluation. Across 11 model configurations, mean accuracy falls from 71.1% on original questions to 38.0% under focused misleading context, with 51.5% attack success. The most damaging injections are formal, rule-like fabrications: authority-framed falsehoods reach 69.5% attack success and exception-poisoning claims reach 64.1%. A 14-member clinical panel from 7 countries identified serious potential harm in 38.2% of reviewed cases. MedMisBench exposes a structural blind spot in LLM evaluation in medical settings: existing benchmarks measure what models know, but not whether they preserve correct medical judgment under misleading context.1