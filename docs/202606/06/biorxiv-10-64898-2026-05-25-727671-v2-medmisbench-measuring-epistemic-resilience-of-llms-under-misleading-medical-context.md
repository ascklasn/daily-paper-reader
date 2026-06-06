---
title: "MedMisBench: Measuring Epistemic Resilience of LLMs Under Misleading Medical Context"
title_zh: "MedMisBench: 衡量大语言模型在误导性医疗上下文下的认知韧性"
authors: "Zhou, H., Zou, X., Wu, J., Wu, S., Segal, B. M., Niebuhr, T. E., Amro, S., Petrus, M., Momin, S., Cardoso Pinto, A., Niesen, R., Wegner, L. S., Darji, D., Koo, J. M., Fieggen, J., Narain, K., Zeng, M., Clifton, L., Shapiro, L., Liu, F., Clifton, D. A."
date: 2026-05-29
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.25.727671v2.full.pdf"
tags: ["query:agent"]
score: 7.0
evidence: 评估LLM在误导性医疗上下文下的鲁棒性，涉及智能体能力
tldr: "大型语言模型在医学考试中达到专家级分数，但患者越来越多地将其用于健康建议。研究发现，当在原本正确回答的问题中注入误导性上下文时，模型会放弃正确答案。为此提出MedMisBench基准，包含10932个医学问题和48889个误导上下文-选项对，评估模型的认知韧性。实验显示，11个模型平均准确率从71.1%降至38.0%，攻击成功率达51.5%，其中权威性虚假信息攻击成功率达69.5%。该基准暴露了现有评估的结构性盲点，即只测知识而非在误导下保持正确判断的能力。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有LLM医学评估只关注知识正确性，忽略误导性上下文下保持正确判断的认知韧性。
method: 构建MedMisBench数据集，包含误导上下文-选项对，涵盖推理、代理能力和患者旅程评估。
result: "11个模型在聚焦误导下准确率从71.1%降至38.0%，51.5%攻击成功，权威性虚假信息达69.5%。"
conclusion: "LLM在医学场景存在结构性盲点，需评估认知韧性而非仅知识，临床专家认定38.2%案例有严重潜在危害。"
---

## 摘要
大语言模型现已在医学执照考试中达到专家级分数，这鼓励了人们假设高分意味着安全的医疗判断，而患者越来越多地使用它们寻求健康建议。我们表明这一假设是脆弱的：当误导性上下文被注入到LLM最初正确回答的问题中时，它们会放弃正确答案。我们将这种在对抗性上下文中保持正确判断的能力称为认知韧性，并引入MedMisBench来衡量它。MedMisBench包含10,932个医学问题项目和48,889个误导性上下文-选项对，涵盖医学推理、代理能力和患者旅程评估。在11种模型配置下，平均准确率从原始问题的71.1%下降到聚焦误导性上下文下的38.0%，攻击成功率为51.5%。最具破坏性的注入是形式化的、规则式的捏造：权威框架下的虚假信息攻击成功率达69.5%，例外投毒主张达64.1%。来自7个国家的14名临床专家小组在38.2%的审查案例中识别出严重的潜在危害。MedMisBench揭示了医疗环境下LLM评估的结构性盲点：现有基准衡量模型知道什么，但不衡量它们在误导性上下文中是否保持正确的医学判断。

## Abstract
Large language models (LLMs) now reach expert-level scores on medical licensing exams, encouraging the assumption that high scores imply safe medical judgment while patients increasingly use them for health advice. We show this assumption is fragile: when misleading context is injected into questions that LLMs originally answer correctly, they abandon the correct answer. We call the ability to maintain correct judgment under adversarial context epistemic resilience, and introduce MedMisBench to measure it. MedMisBench contains 10,932 medical question items and 48,889 misleading context-option pairs spanning medical reasoning, agentic capability, and patient-journey evaluation. Across 11 model configurations, mean accuracy falls from 71.1% on original questions to 38.0% under focused misleading context, with 51.5% attack success. The most damaging injections are formal, rule-like fabrications: authority-framed falsehoods reach 69.5% attack success and exception-poisoning claims reach 64.1%. A 14-member clinical panel from 7 countries identified serious potential harm in 38.2% of reviewed cases. MedMisBench exposes a structural blind spot in LLM evaluation in medical settings: existing benchmarks measure what models know, but not whether they preserve correct medical judgment under misleading context.1