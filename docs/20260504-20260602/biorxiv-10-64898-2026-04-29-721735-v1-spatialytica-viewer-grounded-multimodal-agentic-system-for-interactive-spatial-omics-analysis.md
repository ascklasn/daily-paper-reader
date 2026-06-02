---
title: "spatiAlytica: Viewer-Grounded Multimodal Agentic System for Interactive Spatial Omics Analysis"
title_zh: spatiAlytica：基于查看器的多模态智能体系统用于交互式空间组学分析
authors: "Das, A., Zhang, K., Song, J., Han, M., Chen, A., Meng, W., Galloway, H., Chen, P.-Y., Jo, S., Liu, Z., Hasib, M. M., Officer, A., Sinha, H., Chiu, Y.-C., Gao, S.-J., Li, L., Huang, Y."
date: 2026-05-04
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.29.721735v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 基于查看器的多模态智能体系统用于交互式空间组学分析，包括蛋白组学
tldr: 空间转录组学和蛋白质组学分析需要编程技能，现有AI代理缺乏视图背景和跨轮上下文。提出spatiAlytica，一个嵌入Napari viewer的多模态交互代理系统，结合视图序列化、代理记忆、概念映射、代码生成和空间VQA。在包含222个单轮、178个多轮和7350个图像推理问题的基准测试中，优于强基线且更高效。使非编程生物学家能通过自然语言进行迭代假设驱动分析。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有空间组学分析受限于编程需求和缺乏视图背景的AI代理，阻碍非编程生物学家进行假设驱动探索。
method: spatiAlytica集成viewer状态序列化、代理记忆、概念到数据字段映射、代码生成调试、空间VQA和解释推理，嵌入Napari viewer中。
result: 在SpatiAlyticaBench基准上全面超越基线，节省时间和令牌；案例研究复现已知空间模式并发现CD8 T细胞功能障碍进展。
conclusion: spatiAlytica为非编程生物学家提供交互式、迭代的空间组学分析能力，降低使用门槛，促进假设驱动探索。
---

## 摘要
空间转录组学和蛋白质组学能够描绘组织结构和细胞相互作用，但分析仍受限于编程需求以及缺乏查看器锚定和跨轮次上下文的以文本为中心的AI智能体。我们提出spatiAlytica，一种嵌入Napari查看器的以查看者为中心的多模态交互式智能体系统，使非编程生物学家能够通过自然语言进行迭代的、假设驱动的空间组学分析。spatiAlytica结合了查看器状态序列化、智能体记忆、生物概念到数据字段映射、代码生成与调试、空间视觉问答以及锚定解释，以支持探索性分析和解释性推理工作流程。我们引入了spatiAlyticaBench，一个全面的基准测试，涵盖222个单轮空间分析编码问题、178个多轮序列工作流问题以及7,350个基于图像的推理问题。spatiAlytica在消耗更少时间和令牌的同时，优于强大的智能体基线。对卡波西肉瘤、结直肠癌和卵巢癌的案例研究再现了已知的空间模式，并揭示了卡波西肉瘤进展过程中CD8 T细胞功能的逐步失调。

## Abstract
Spatial transcriptomics and proteomics map tissue architecture and cellular interactions, but analysis remains limited by programming demands and text-centered AI agents that lack viewer grounding and cross-turn context. We present spatiAlytica, a viewer-centric multimodal interactive agentic system embedded in the Napari viewer that enables non-programmer biologists to perform iterative, hypothesis-driven spatial omics analysis via natural language. spatiAlytica couples viewer-state serialization, agentic memory, biological concept-to-data-field mapping, code generation and debugging, Spatial VQA, and grounded interpretation to support an exploratory analysis and interpretive reasoning workflow. We introduce spatiAlyticaBench, a comprehensive benchmark spanning 222 single-turn spatial analytical coding questions, 178 multi-turn sequential workflow questions, and 7,350 image-grounded reasoning questions. spatiAlytica outperformed strong agentic baselines, while using less time and tokens. Case studies across Kaposis sarcoma, colorectal cancer, and ovarian cancer recapitulated known spatial patterns and uncovered progressive CD8 T-cell dysfunction during KS progression.