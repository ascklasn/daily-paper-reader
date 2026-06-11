---
title: "MedMisBench: Measuring Epistemic Resilience of LLMs Under Misleading Medical Context"
title_zh: MedMisBench：在误导性医疗情境下测量LLM的认知韧性
authors: "Zhou, H., Zou, X., Wu, J., Wu, S., Yu, J., Segal, B. M., Niebuhr, T. E., Amro, S., Petrus, M., Momin, S., Cardoso Pinto, A., Niesen, R., Wegner, L. S., Darji, D., Koo, J. M., Fieggen, J., Narain, K., Zeng, M., Clifton, L., Shapiro, L., Liu, F., Clifton, D. A."
date: 2026-06-10
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.25.727671v3.full.pdf"
tags: ["query:agent"]
score: 8.0
evidence: 在误导性医学背景下衡量LLM韧性的基准，包含智能体能力评估
tldr: "大型语言模型在医学执照考试中取得高分，但注入误导上下文后正确答案被放弃。MedMisBench基准包含10932道医学题目和48889个误导上下文-选项对，测试模型在对抗情境下的判断韧性。11个模型配置的平均准确率从71.1%降至38.0%，攻击成功率51.5%，其中权威框架的虚假信息攻击成功率69.5%。临床专家评审发现38.2%案例存在严重潜在危害，揭示现有评估忽视误导情境下判断能力的结构性盲点。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有评估只测知识，忽视LLMs在误导上下文下能否保持正确医学判断。
method: 构建MedMisBench基准，含10932道题和48889个误导对，覆盖推理、智能体、患者旅程。
result: "平均准确率从71.1%降至38.0%，攻击成功率51.5%；权威虚假信息攻击成功率69.5%。"
conclusion: 需将误导情境下判断能力纳入LLM医学评估，避免高分数掩盖安全隐患。
---

## 摘要
大型语言模型（LLM）现已在医学执照考试中达到专家级分数，这鼓励了人们认为高分意味着安全医疗判断的假设，同时患者越来越多地使用它们获取健康建议。我们表明这一假设是脆弱的：当误导性上下文被注入到LLM原本正确回答的问题中时，它们会放弃正确答案。我们将这种在对抗性语境下保持正确判断的能力称为认知韧性，并引入MedMisBench来测量它。MedMisBench包含10,932个医学问题项目与48,889个误导性上下文-选项对，涵盖医学推理、智体能力和患者旅程评估。在11个模型配置中，平均准确率从原始问题的71.1%下降到聚焦误导性上下文下的38.0%，攻击成功率为51.5%。最具破坏性的注入是形式化、规则式的捏造：权威框架下的错误陈述达到69.5%的攻击成功率，例外毒化声明达到64.1%。来自7个国家的14人临床专家小组在38.2%的审查案例中识别出严重的潜在危害。MedMisBench暴露了医学环境中LLM评估的一个结构性盲点：现有基准衡量模型知道什么，但并不衡量它们在误导性上下文中是否保持正确的医学判断。

## Abstract
Large language models (LLMs) now reach expert-level scores on medical licensing exams, encouraging the assumption that high scores imply safe medical judgment while patients increasingly use them for health advice. We show this assumption is fragile: when misleading context is injected into questions that LLMs originally answer correctly, they abandon the correct answer. We call the ability to maintain correct judgment under adversarial context epistemic resilience, and introduce MedMisBench to measure it. MedMisBench contains 10,932 medical question items and 48,889 misleading context-option pairs spanning medical reasoning, agentic capability, and patient-journey evaluation. Across 11 model configurations, mean accuracy falls from 71.1% on original questions to 38.0% under focused misleading context, with 51.5% attack success. The most damaging injections are formal, rule-like fabrications: authority-framed falsehoods reach 69.5% attack success and exception-poisoning claims reach 64.1%. A 14-member clinical panel from 7 countries identified serious potential harm in 38.2% of reviewed cases. MedMisBench exposes a structural blind spot in LLM evaluation in medical settings: existing benchmarks measure what models know, but not whether they preserve correct medical judgment under misleading context.