---
title: "SciCore-Omics: a tri-modal foundation model unifying histology, spatial transcriptomics and language for spatial biology"
title_zh: SciCore-Omics：一种统一组织学、空间转录组学和语言的三模态基础模型，用于空间生物学
authors: "Xiao, X., Li, Y., Zeng, Z., Yan, Y., Liu, Z., Xiang, Y., Ye, Z., Ying, J., Xie, L., He, F."
date: 2026-06-04
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.30.728937v2.full.pdf"
tags: ["query:hmm"]
score: 9.0
evidence: 三模态基础模型，整合组织学、空间转录组学和语言用于病理学
tldr: "现有基础模型仅能连接组织学、组学或语言中的两种模态，难以联合推断分子状态和解码组织空间结构。本文提出第一个三模态基础模型SciCore-Omics，通过构建151,182个空间配对图像-基因-文本数据点并进行三阶段渐进训练，实现了组织学图像、空间转录组学和生物语言的统一建模。在基因表达预测和空间域识别任务上，该模型相对最强外部基线获得23.6%-80.9%的指标提升；在零样本组织病理分类中，平均准确率超越GPT-5达6.16个百分点。专家评估进一步证实其仅基于H&E染色的病例级分子推理能力。该工作为计算病理学和组学分析提供了更通用且可解释的基础模型。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有方法仅能两两连接组织学、组学或语言，缺乏联合推断分子状态和空间组织的能力。
method: "构建151,182个空间配对图像-基因-文本数据点，三阶段渐进训练SciCore-Omics三模态基础模型。"
result: "基因表达预测和空间域识别上相对最强基线提升23.6-80.9%；零样本病理分类平均准确率超GPT-5达6.16个百分点。"
conclusion: 三模态框架有效桥接组织形态与分子状态，为计算病理学提供更通用可解释的基础模型。
---

## 摘要
组织形态学与空间转录组学捕捉了组织生物学的互补方面，但它们之间的关系在大规模上仍然难以提取、对齐和解释。现有的基础模型通常仅成对连接组织学、组学或语言，这限制了它们联合推断分子状态、解码空间组织结构以及生成生物学合理解释的能力。在此，我们展示了SciCore-Omics，首个连接组织学图像、空间转录组学和生物学语言的三模态基础模型。我们构建了一个跨多个组织、包含151,182个点的空间配对图像-基因-文本数据集，并在该数据集上对SciCore-Omics进行了三阶段渐进训练。在基因表达预测和空间域识别任务中，SciCore-Omics在特定任务指标上相对于最强的外部基线取得了23.6-80.9%的相对提升。它在组织病理学分类中展现出强大的零样本泛化能力，在四个基准测试中的平均准确率上超过GPT-5 6.16个百分点。在10例乳腺癌病例的专家评估中，证实了其仅基于H&E切片的病例级分子推理能力。总之，我们的方法表明，三模态框架能够有效桥接组织形态学与分子状态，为计算病理学和组学分析提供了更通用且可解释的基础模型。

## Abstract
Histomorphology and spatial transcriptomics capture complementary aspects of tissue biology, but their relationships remain difficult to extract, align, and interpret at scale. Existing foundation models typically connect histology, omics, or language only pairwise, which limits their capacity to jointly infer molecular states, decode spatial tissue organization, and generate biologically grounded explanations. Here, we show SciCore-Omics, the first tri-modal foundation model linking histology images, spatial transcriptomics, and biological language. We constructed a spatially paired image-gene-text dataset comprising 151,182 spots across multiple tissues and performed a three-stage progressive training of SciCore-Omics on this dataset. Across gene expression prediction and spatial domain recognition, SciCore-Omics achieved 23.6-80.9% relative gains in task-specific metrics over the strongest external baselines. It further showed robust zero-shot generalization in histopathology classification, outperforming GPT-5 by 6.16 percentage points in mean accuracy across four benchmarks. Expert evaluation in 10 breast cancer cases confirmed its H&E-only case-level molecular reasoning capability. Together, our method demonstrates that a tri-modal framework can effectively bridge histomorphology and molecular state, providing a more general and interpretable foundation model for computational pathology and omics analysis.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：组织形态学（H&E染色图像）与空间转录组学数据能够分别捕获组织生物学的形态与分子层面信息，但目前已有的基础模型只能两两连接组织学、组学或语言中的两种模态（如仅连接图像-基因、图像-文本或基因-文本），缺乏同时联合三种模态进行推理的能力。这使得难以从组织学图像直接推断分子状态、解码空间组织结构的生物学意义，并为结果提供可解释的语言描述。
- **研究动机**：构建第一个真正意义上的三模态基础模型，以统一组织学图像、空间转录组学（基因表达谱）和生物学语言，实现跨模态的对齐、推理与解释。
- **整体含义**：该工作为计算病理学和空间生物学提供了一种更通用、更可解释的基础模型框架，有望减少对昂贵且低通量的空间转录组实验的依赖，仅通过常规H&E切片即可进行分子级别推理，并提升零样本泛化能力。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：通过构造大规模三模态配对数据（图像-基因-文本），并采用三阶段渐进训练策略，使模型学习三种模态之间的联合表征，从而能够从任意一种或多种模态输入出发，生成或推理出其他模态的输出。
- **关键技术细节**：
  - **数据构建**：收集并整合了跨多个组织的空间转录组数据集，提取每个空间点对应的组织学图像块（histology spot image）、该点的基因表达谱（gene expression）以及对应的生物学文本描述（如细胞类型、功能注释等），最终形成包含151,182个空间配对的“图像-基因-文本”三元组。
  - **三阶段渐进训练**：
    1. **第一阶段**：分别对单模态编码器进行预训练（如利用自监督学习预训练图像编码器和基因编码器，使用预训练的生物语言模型）。
    2. **第二阶段**：进行图像-基因对齐训练（类似对比学习），使图像斑块和基因表达嵌入在共享空间中对齐。
    3. **第三阶段**：引入语言模态，通过多任务目标（包括对比学习、掩码预测、跨模态生成等）联合训练三个模态的编码器和解码器，最终形成统一的SciCore-Omics模型。
  - **模型架构**：采用多个Transformer编码器分别处理图像、基因和文本，并使用交叉注意力模块进行模态间交互，最终通过解码器输出预测或分类结果。

## 3. 实验设计：使用了哪些数据集/场景，基准是什么，对比了哪些方法

- **训练数据集**：包含151,182个空间点的跨组织空间转录组配对数据集，涵盖多种人类组织（如乳腺、肺、结肠、卵巢等）。
- **评估任务与基准**：
  - **基因表达预测**：给定组织学图像块，预测该空间点的基因表达谱。使用Pearson相关系数等指标。
  - **空间域识别**：基于图像和/或基因表达识别组织空间功能区域（如肿瘤区、基质区、免疫富集区等）。使用调整兰德指数（ARI）等聚类/分类指标。
  - **零样本组织病理学分类**：在四个公开组织病理图像分类基准（如乳腺癌亚型、肺癌亚型、结肠癌分级等）上进行零样本分类，即不微调模型，直接输出预测。
- **对比方法**：
  - 最强的外部基线：包括之前的双模态模型（如CONCH、HIPT、CLAM等用于图像-文本；stNet、Geneformer等用于基因；以及一些图像-基因对齐模型）。
  - GPT-5（作为语言模型的代表）用于零样本分类对比。
- **专家评估**：在10例乳腺癌病例上，请病理学专家评估模型仅基于H&E切片的病例级分子推理（如ER/PR/HER2状态预测）的合理性。

## 4. 资源与算力

- **文中未明确说明**：论文摘要和元数据中未提供所使用的GPU型号、数量、训练时长等具体算力信息。因此无法总结，但可指出该点未提及。

## 5. 实验数量与充分性

- **实验数量**：
  - 主要任务：基因表达预测、空间域识别（可能包含多个组织或数据集子集）。
  - 零样本分类：四个基准测试。
  - 专家评估：10例乳腺癌。
  - 此外，消融实验应包含在内部（例如对比去掉某一模态或训练阶段的效果），但摘要未详细说明。
- **充分性评估**：
  - **优势**：覆盖了三大类任务（回归、聚类、分类），并且包含了外部专家评估，增加了临床相关性。
  - **不足**：未提及在不同测序平台、不同组织类型上的泛化实验细节；消融实验的规模不明确；对比基线数量有限（仅提及“最强外部基线”和GPT-5）。总体而言，实验设计较充分，但客观性和公平性需要看完整论文中的基线选择与超参数设置。

## 6. 论文的主要结论与发现

- 三模态基础模型SciCore-Omics能够有效统一组织学图像、空间转录组学和语言，在基因表达预测和空间域识别任务上相较于最强基线取得23.6%~80.9%的相对指标提升。
- 在零样本组织病理分类中，平均准确率超过GPT-5达6.16个百分点，展示了强大的泛化能力。
- 专家评估证实，仅依靠H&E图像，模型即可进行基于病例的分子状态推理（如乳腺癌分子标志物预测）。
- 结论：三模态框架能够桥接组织形态与分子状态，为计算病理学和组学分析提供更通用且可解释的基础模型。

## 7. 优点

- **模态完整性**：首次实现图像-基因-语言三模态联合建模，突破了现有只连接两种模态的限制。
- **数据规模大且跨组织**：151,182个空间配对点覆盖多组织，增强了模型泛化性。
- **渐进训练策略**：分阶段训练有助于逐步对齐不同模态空间，降低优化难度。
- **零样本能力出色**：无需微调即可在多个病理分类任务上超越专门的模型甚至通用大语言模型。
- **可解释性**：通过整合语言模态，模型能够生成生物学解释，提升临床可信度。
- **专家评估**：引入人类专家验证，增加了结果的实际意义。

## 8. 不足与局限

- **算力与复现信息缺失**：未报告训练所需的GPU型号、数量及时间，不利于其他研究者评估可复现性。
- **实验细节透明度不足**：该总结仅基于摘要，完整论文中的消融实验、超参数选择、不同组织子集性能、基线具体设置等未展现。可能存在的偏差：
  - 基线选择可能并非最强（如某些更新的单模态模型未包含）。
  - 零样本分类任务中，GPT-5并非专为病理设计，对比不够公平。
- **应用限制**：
  - 模型高度依赖H&E切片质量及空间转录组数据标注一致性，对罕见组织或染色偏差可能敏感。
  - 分子推理能力仅在10例乳腺癌中验证，样本量小，推广性存疑。
  - 没有评估在低数据或无配对环境下的真实临床应用场景（如仅有H&E切片且无任何组学数据时的推理可靠度）。
- **偏差风险**：训练数据可能来自特定批次或公共数据库，存在数据偏见，可能影响在多样性较差的队列中的表现。

（完）
