---
title: An AI-Powered Trisomy 21 Research Assistant
title_zh: 基于人工智能的21三体综合征研究助手
authors: "NANDI, S., Sundararajan, Z., Subirana-Granes, M., Espinosa, J. M., Pividori, M., Sullivan, K. D., Galbraith, M. D., Costello, J."
date: 2026-06-11
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.08.730893v1.full.pdf"
tags: ["query:agent"]
score: 7.0
evidence: 基于LLM和RAG的唐氏综合症研究助手
tldr: 唐氏综合征相关文献超过34000篇，追踪最新进展极具挑战。通用大语言模型依赖训练数据，缺乏具体证据。为此，开发了T21 Research Assistant，采用章节感知的检索增强生成（RAG）系统，优先从论文的Results部分检索实验证据，并使用NVIDIA Nemotron模型生成结构化回答。专家评估显示其BERTScore F1为0.712，召回率0.758，性能与领先模型相当甚至更优。该系统为唐氏综合征研究提供了可靠的信息检索工具。
source: biorxiv
selection_source: fresh_fetch
motivation: 唐氏综合征文献快速增多，通用LLM检索缺乏对实验证据的针对性，需构建能优先利用Results部分的RAG系统。
method: 从PMC开放获取唐氏综合征文献（含327篇NIH INCLUDE论文）构建索引，采用多阶段流水线：查询验证、章节感知检索（优先Results）、重排、综合与引用验证，基于NVIDIA Nemotron生成回答。
result: 在专家问题集上，BERTScore F1达0.712，召回率0.758，性能与领先的专有及开源模型相当或更优。
conclusion: 章节感知RAG系统有效提升了实验证据的检索可靠性，为唐氏综合征研究者提供了实用助手工具。
---

## 摘要
唐氏综合征由21三体引起，会增加多种并发疾病的风险。截至2026年初，PubMed中收录的相关出版物超过34,000篇，跟上这一不断扩大的文献量极具挑战性。虽然通用大语言模型被广泛用于信息检索，但它们通常依赖广泛的训练数据而非特定证据。检索增强生成（RAG）通过将模型输出与源文本关联，提高了回答的严谨性和可靠性。在研究中，源文本是经同行评审的文章。标准实现将所有手稿章节同等对待，使得背景文本与实验结果排名相同。为了使模型输出聚焦于有实验支持的回答，我们开发了T21研究助手，这是一个感知章节的RAG系统，优先处理结果章节，将回答扎根于原始实验证据。该系统仅从PubMed Central的1,789篇开放获取的唐氏综合征出版物中提取信息，包括327项NIH INCLUDE资助的研究，并使用多阶段流水线进行查询验证、检索、重排序、综合和引用验证。该系统基于NVIDIA Nemotron模型构建，生成结构化的、带引用的回答。使用专家策划的问题进行的评估显示了强劲的性能，BERTScore F1达到0.712，召回率为0.758，与领先的专有和开源模型相当或更优。T21研究助手可在以下网址获取：https://bioinformatics.cuanschutz.edu/t21-res-assi/

## Abstract
Down syndrome, caused by trisomy 21, increases the risk of diverse co-occurring conditions. With more than 34,000 related publications indexed in PubMed as of early 2026, keeping pace with this expanding literature is challenging. While general-purpose large language models are widely used for information retrieval, they often rely on broad training data rather than specific evidence. Retrieval-augmented generation (RAG) improves rigor and reliability of responses by linking model outputs to source texts. In research, source texts are peer-reviewed articles. Standard implementations treat all manuscript sections equally, allowing background text to rank as highly as experimental results. To focus model outputs on experimentally supported responses, we developed the T21 Research Assistant, a section-aware RAG system that prioritizes Results sections to ground responses in primary experimental evidence. The system draws exclusively from 1,789 open-access Down syndrome publications from PubMed Central, including 327 NIH INCLUDE-funded studies, and uses a multistage pipeline for query validation, retrieval, reranking, synthesis, and citation verification. Built on NVIDIA Nemotron models, it generates structured, cited responses. Evaluation using expert-curated questions demonstrated strong performance, achieving a BERTScore F1 of 0.712 and recall of 0.758, comparable to or exceeding leading proprietary and open-source models. T21 Research Assistant is available at: https://bioinformatics.cuanschutz.edu/t21-res-assi/