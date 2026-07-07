---
title: "NeuroVLM: A generative vision-language framework for human neuroimaging"
title_zh: "NeuroVLM: 用于人类神经影像的生成式视觉-语言框架"
authors: "Hammonds, R., Aguirre-Chavez, J., Omoma-Edosa, B., Patel, A., Voytek, B."
date: 2026-07-01
pdf: "https://www.biorxiv.org/content/10.64898/2026.02.06.704508v3.full.pdf"
tags: ["query:hmm"]
score: 6.0
evidence: 用于神经影像的视觉语言模型，与病理学多模态模型方法类似
tldr: 神经影像研究积累了海量自然语言与激活坐标的配对数据，但缺乏联合建模方法。NeuroVLM提出了一种支持对比与生成目标的统一框架，从3万对神经影像-文本对中学习跨模态表征。在多种神经影像数据上，模型实现了文本生成影像、影像生成文本、网络标注及跨模态检索。该工作为神经影像与自然语言的双向理解提供了高效工具，有望推动自动化分析。
source: biorxiv
selection_source: fresh_fetch
motivation: 利用大量神经影像-文本对，构建统一的对比与生成框架，实现神经影像与自然语言的双向理解与生成。
method: 提出NeuroVLM模型，基于对比学习和生成目标，从30826对数据中学习文本与神经影像的联合表示。
result: 在多种神经影像数据上，模型能生成图谱、解释影像、检索相关出版物，实现了有效的跨模态转换。
conclusion: NeuroVLM为神经影像分析提供了强大的跨模态工具，有助于自动化分析和解释。
---

## 摘要
神经影像研究已经产生了数万篇将自然语言与激活坐标表配对的文章。视觉-语言模型（VLM）的最新进展提供了同时建模文本和图像的方法。在这项工作中，我们提出了NeuroVLM，一种用于学习30,826个人类神经影像-文本对的模型架构。该架构支持对比和生成目标。对比模型对神经影像和文本之间的相似性进行排序。生成模型包括文本到神经影像和神经影像到文本。这些模型在来自各种图谱的网络图像、来自不同出版物的统计图以及由坐标表创建的图像上进行了评估。这些模型能够根据给定的文本语料库生成图谱或地图，生成神经影像的文本解释，标记网络，找到与神经影像查询最相关的出版物，或找到与文本查询最相关的神经影像。

## Abstract
Neuroimaging research has produced tens-of-thousands of articles that pair natural language and activation coordinate tables. Recent advances in vision-language models (VLMs) have provided methods to model text and images simultaneously. In this work, we present NeuroVLM, a model architecture for learning from 30,826 human neuroimage-text pairs. The architecture supports contrastive and generative objectives. The contrastive model ranks similarity between neuroimages and text. The generative models include text-to-neuroimage and neuroimage-to-text. These models are evaluated on network images from a variety of atlases, statistical maps from diverse publications, and images created from coordinate tables. These models are capable of generating atlases or maps given a text corpus, generating text interpretations of neuroimages, labeling networks, finding publications most related to a neuroimage query, or finding neuroimages most related to a text query.