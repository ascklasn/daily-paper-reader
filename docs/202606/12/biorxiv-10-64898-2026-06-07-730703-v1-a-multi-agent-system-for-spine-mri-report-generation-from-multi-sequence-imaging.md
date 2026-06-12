---
title: A multi-agent system for spine MRI report generation from multi-sequence imaging
title_zh: 一种基于多序列成像的脊柱MRI报告生成的多智能体系统
authors: "Xiao, Z., Yang, J., Sun, G., Zhang, H., Xu, H., Yao, Y., Miller, Z. D., King, W. E., Kanani, M. M., Andre, J. B., Chu, S., Zhang, M., Kinahan, P. E., Cross, N. M., Wang, S."
date: 2026-06-11
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.07.730703v1.full.pdf"
tags: ["query:agent"]
score: 8.0
evidence: 多agent系统用于医学MRI报告生成
tldr: "脊柱MRI报告生成面临多序列信息整合的挑战。本文提出SpineAgent多智能体框架，基于453,683个MRI系列预训练双编码器，并通过持续训练策略嵌入其他序列。在17个脊柱病变预测任务上平均AUROC提升10.8%，支持病理定位和图文检索。整合37个专用智能体实现可解释报告生成，经放射科专家评估取得领先性能。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有MRI分析难以有效整合多序列信息，且报告生成缺乏可解释性和通用性。
method: 预训练T1/T2编码器后引入持续训练，将其他序列嵌入统一表示；构建37个专用智能体分工完成诊断、定位和检索，最终由报告智能体生成文本。
result: "在17个病变预测任务上AUROC平均提升10.8%，报告质量经五位放射科专家评估优于现有方法。"
conclusion: SpineAgent实现了准确、可解释且泛化性强的多序列脊柱MRI报告生成，为临床自动化报告提供新范式。
---

## 摘要
脊柱病变是全球疼痛和残疾的主要原因之一。脊柱磁共振成像（MRI）是临床评估的核心，但其解读仍然复杂且耗时，需要整合多个成像序列和解剖区域的信息。尽管近年来自动MRI分析取得了进展，但有效结合多序列数据同时保留序列特异性诊断信息仍然是一个开放的挑战。在此，我们提出SpineAgent，一个基于多序列基础模型构建的脊柱MRI报告生成多智能体框架，该模型在来自32,047名患者和453,683个MRI序列的常规临床数据上训练，共计13,441,191个MRI切片。为了适应不同序列的模态，我们首先在T1和T2加权序列上分别预训练两个基于DINOv3的编码器。然后引入一种持续训练策略，学习一个合成器，利用T1和T2编码器嵌入其他序列的图像，生成整合MRI序列间多种信号的患者级嵌入。利用这些嵌入，SpineAgent实现了最先进的性能，在17个脊柱状况预测任务中，与最佳竞争方法相比，平均AUROC提高了10.8%，并在跨制造商和跨队列评估中表现出强大的泛化能力。除了分类，SpineAgent还通过识别与发现相关的切片和分割病变区域来实现病理定位。它还支持多模态图像-报告检索，为可扩展和可解释的MRI报告生成提供了坚实基础。我们进一步将SpineAgent的这些经过验证的能力整合到37个专门智能体中，用于疾病诊断、病变区域定位和临床相似病例检索。最后，我们将它们的输出作为结构化标记，整合到端到端训练用于报告生成的医学报告智能体中。通过自动化指标和五位放射科医生的专家评估，SpineAgent在脊柱MRI报告生成中取得了领先性能。总之，SpineAgent引入了一种用于多序列脊柱MRI理解的持续训练方法。通过将报告生成分解为由专门智能体处理的临床基础子任务，SpineAgent框架能够在不同成像序列和解剖区域上实现准确、可解释和泛化的脊柱MRI报告生成。

## Abstract
Spinal pathology is a leading cause of pain and disability worldwide. Spine magnetic resonance imaging (MRI) is central to clinical evaluation, yet its interpretation remains complex and time-consuming, requiring integration of information across multiple imaging sequences and anatomical regions. Despite recent advances in automated MRI analysis, effectively combining multi-sequence data while preserving sequence-specific diagnostic information remains an open challenge. Here we present SpineAgent, a multi-agent framework for spine MRI report generation built upon a multi-sequence foundation model trained on routine clinical data from 32,047 patients and 453,683 MRI series, comprising a total of 13,441,191 MRI slices. To accommodate diverse modalities of sequences, we first pre-train two DINOv3-based encoders separately on T1- and T2-weighted sequences. We then introduce a continual training strategy that learns a synthesizer to embed images of other sequences using the T1 and T2 encoders, producing patient-level embedding that integrates various signals across MRI sequences. Using these embeddings, SpineAgent achieves state-of-the-art performance, with mean 10.8% AUROC improvement across 17 spinal condition-prediction tasks compared to the best competing method, and demonstrates strong generalizability under cross-manufacturer and cross-cohort evaluation. Beyond classification, SpineAgent enables pathology localization by identifying findings-relevant slices and segmenting pathological regions. It also supports multimodal image-report retrieval, providing a solid foundation for scalable and explainable MRI report generation. We further integrate these validated capabilities of SpineAgent into 37 specialized agents for condition diagnosis, pathological-region localization, and clinically-similar-cases retrieval. Finally, we incorporate their outputs as structured tokens within a Medical Report Agent trained end-to-end for report generation. Through both automated metrics and expert evaluation by five radiologists, SpineAgent achieves leading performance in spine MRI report generation. Together, SpineAgent introduces a continual training approach for multi-sequence spine MRI understanding. By decomposing report generation into clinically grounded subtasks addressed by specialized agents, the SpineAgent framework enables accurate, interpretable and generalizable spine MRI reporting across diverse imaging sequences and anatomical regions.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：脊柱MRI解读复杂且耗时，需要整合多个成像序列（如T1、T2及对比增强序列等）和解剖区域信息。现有自动分析方法难以有效结合多序列数据，同时保留序列特异性诊断信息，导致报告生成缺乏可解释性和通用性。
- **背景**：脊柱病变是导致疼痛和残疾的主要原因，MRI是临床评估核心。自动化报告生成能减轻放射科医生负担，但现有方法在跨序列信息融合和临床推理方面存在短板。
- **整体含义**：提出SpineAgent多智能体框架，旨在通过持续训练策略整合多序列MRI信息，实现高精度、可解释且泛化性强的脊柱MRI报告生成，为临床自动化报告提供新范式。

## 2. 方法论：核心思想、关键技术细节、算法流程
- **核心思想**：将多序列MRI理解分解为多个基础子任务，由专门智能体分别处理，最后整合为结构化报告。通过“预训练+持续训练”策略构建多序列基础模型，为各智能体提供统一患者级嵌入。
- **关键技术细节**：
  - **双编码器预训练**：基于DINOv3分别在T1加权和T2加权序列上预训练两个编码器（共使用13,441,191个MRI切片）。
  - **持续训练策略**：学习一个**合成器（Synthesizer）**，利用已训练的T1和T2编码器嵌入其他序列（如STIR、T1 CE等）的图像，生成患者级嵌入，整合多序列信号。
  - **多智能体架构**：
    - 37个**专用智能体**：分别负责疾病诊断（17个病变预测任务）、病变区域定位（切片级识别和分割）、临床相似病例检索。
    - **医学报告智能体**（端到端训练）：接收各专用智能体的输出作为结构化标记，生成最终文本报告。
- **算法流程**（文字说明）：
  1. 输入多序列脊柱MRI切片。
  2. T1/T2编码器提取基础特征，合成器将其他序列特征对齐到统一表示。
  3. 生成患者级嵌入，供专用智能体执行诊断、定位、检索。
  4. 专用智能体输出结构化标记（如诊断标签、定位框、相似病例ID）。
  5. 医学报告智能体将标记组合为自然语言报告。

## 3. 实验设计：数据集、benchmark、对比方法
- **数据集**：
  - 训练数据：来自32,047名患者、453,683个MRI系列，共13,441,191个切片（常规临床数据）。
  - 评估场景：17个脊柱状况预测任务（包含病变分类）；跨制造商泛化测试；跨队列泛化测试。
- **Benchmark**：对比当前最佳竞争方法（未具体列出名称，但提及“best competing method”）。
- **报告质量评估**：自动化指标（如ROUGE、BLEU等，未明确说明具体指标）+ 五位放射科专家人工评分。
- **额外实验**：病理定位（识别相关切片和分割病变区域）、多模态图像-报告检索。

## 4. 资源与算力
- **论文未明确说明**使用的GPU型号、数量、训练时长等具体计算资源信息。
- 仅提及训练数据规模巨大（453,683个系列、1300万+切片），但未提供训练硬件细节。这是论文对可复现性支持不足的一点。

## 5. 实验数量与充分性
- **实验数量**：
  - 主分类任务：17个病变预测。
  - 泛化实验：跨制造商、跨队列。
  - 辅助任务：定位（切片识别+分割）、检索。
  - 报告生成评估：自动化指标+5位专家评价。
  - 消融实验：未在摘要中明确提及，但元数据提到“平均AUROC提升10.8%”，暗示有消融对比。
- **充分性**：实验覆盖了分类、定位、检索、报告生成等多种任务，且包含跨域泛化验证，总体较充分。
- **客观性与公平性**：对比最佳竞争方法，专家评估采用多放射科医生盲评，并报告AUROC等客观指标，设计较严谨。但未公开对比方法的具体名称，可能影响公平性评判。

## 6. 主要结论与发现
- SpineAgent在17个脊柱病变预测任务上，**平均AUROC提升10.8%**，优于最佳竞争方法。
- 在跨制造商和跨队列评估中表现出**强大的泛化能力**。
- 支持**病理定位**（识别相关切片和分割病变区域）及**图像-报告检索**，为可解释报告生成提供基础。
- 整合37个智能体后，整体报告生成质量经5位放射科专家评估取得**领先性能**。
- 提出持续训练策略有效融合多序列信息，是脊柱MRI理解的新范式。

## 7. 优点
- **持续训练策略创新性**：先预训练主要序列（T1/T2）编码器，再通过合成器嵌入其他序列，避免全量重新训练，提升了跨序列泛化能力。
- **多智能体分解**：将复杂报告生成解耦为临床子任务（诊断、定位、检索），提高了可解释性和模块化，便于验证各环节正确性。
- **大规模真实临床数据**：训练数据来自32,047名患者、1300万+切片，数据规模大，贴近实际分布。
- **跨域泛化验证**：同时进行了跨制造商和跨队列实验，增强了方法的实用性。
- **全面的任务评估**：不仅分类，还包含定位、检索和报告生成，评估维度完整。

## 8. 不足与局限
- **计算资源未披露**：未提供GPU型号、数量、训练时长等，影响复现和可扩展性评估。
- **对比方法不透明**：未列出竞争方法具体名称，读者难以判断实验设置的公平性。
- **依赖特定序列基础**：合成器依赖T1/T2编码器；若缺失T1/T2序列可能影响性能。
- **数据单一来源风险**：虽然进行了跨队列验证，但训练数据可能主要来自单一机构或特定扫描仪，存在潜在分布偏移。
- **未讨论失败案例**：未分析在哪些特定病变或序列下表现较差，缺乏误差分析。
- **未提及代码与模型开源**：若未公开，则限制临床应用和学术复现。

（完）
