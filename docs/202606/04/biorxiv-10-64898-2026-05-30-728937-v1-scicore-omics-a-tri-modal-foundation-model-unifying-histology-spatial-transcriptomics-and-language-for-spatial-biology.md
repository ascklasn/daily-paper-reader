---
title: "SciCore-Omics: a tri-modal foundation model unifying histology, spatial transcriptomics and language for spatial biology"
title_zh: SciCore-Omics：统一组织学、空间转录组学和语言的空间生物学三模态基础模型
authors: "Xiao, X., Li, Y., Zeng, Z., Yan, Y., Liu, Z., Xiang, Y., Ye, Z., Ying, J., Xie, L., He, F."
date: 2026-06-03
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.30.728937v1.full.pdf"
tags: ["query:hmm"]
score: 9.0
evidence: 连接组织学、空间转录组和语言的三模态基础模型，用于空间生物学
tldr: "组织学图像与空间转录组数据难以大规模对齐和联合解释，现有模型仅能两两连接模态，限制了分子状态推断。提出首个三模态基础模型SciCore-Omics，构建15万+空间点配对数据集进行三阶段渐进训练，融合图像、基因表达与生物语言。在基因表达预测和空间域识别任务上相对最强基线提升23.6%-80.9%，零样本病理分类准确率超GPT-5 6.16个百分点，专家验证其仅基于H&E图像的分子推理能力。该方法为计算病理学和空间生物学提供了更通用可解释的基础模型。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有基础模型仅连接组织学与组学或语言中的两两模态，无法联合推断分子状态和解码空间组织。
method: 构建15万点空间配对图像-基因-文本数据集，采用三阶段渐进训练统一三个模态。
result: "基因表达预测和空间域识别提升23.6%-80.9%，零样本病理分类超GPT-5 6.16个百分点，专家验证其H&E分子推理能力。"
conclusion: 首个三模态基础模型有效桥接组织形态与分子状态，为计算病理学和空间生物学提供更通用可解释的框架。
---

## 摘要
组织形态学与空间转录组学捕捉组织生物学的互补方面，但它们之间的关系在大规模上仍难以提取、对齐和解释。现有的基础模型通常仅成对连接组织学、组学或语言，这限制了它们共同推断分子状态、解码空间组织架构以及生成具有生物学基础的解释的能力。在此，我们展示了SciCore-Omics，这是首个连接组织学图像、空间转录组学和生物学语言的三模态基础模型。我们构建了一个包含跨多个组织151,182个点的空间配对图像-基因-文本数据集，并在此数据集上对SciCore-Omics进行了三阶段渐进式训练。在基因表达预测和空间域识别方面，相比最强的外部基线，SciCore-Omics在特定任务指标上实现了23.6%到80.9%的相对提升。它在组织病理学分类中进一步展示了强大的零样本泛化能力，在四个基准测试中的平均准确率上比GPT-5高出6.16个百分点。在10例乳腺癌病例的专家评估中，证实了其仅基于H&E染色的病例级分子推理能力。总之，我们的方法表明，三模态框架能够有效桥接组织形态学和分子状态，为计算病理学和组学分析提供了一个更通用且可解释的基础模型。

## Abstract
Histomorphology and spatial transcriptomics capture complementary aspects of tissue biology, but their relationships remain difficult to extract, align, and interpret at scale. Existing foundation models typically connect histology, omics, or language only pairwise, which limits their capacity to jointly infer molecular states, decode spatial tissue organization, and generate biologically grounded explanations. Here, we show SciCore-Omics, the first tri-modal foundation model linking histology images, spatial transcriptomics, and biological language. We constructed a spatially paired image-gene-text dataset comprising 151,182 spots across multiple tissues and performed a three-stage progressive training of SciCore-Omics on this dataset. Across gene expression prediction and spatial domain recognition, SciCore-Omics achieved 23.6-80.9% relative gains in task-specific metrics over the strongest external baselines. It further showed robust zero-shot generalization in histopathology classification, outperforming GPT-5 by 6.16 percentage points in mean accuracy across four benchmarks. Expert evaluation in 10 breast cancer cases confirmed its H&E-only case-level molecular reasoning capability. Together, our method demonstrates that a tri-modal framework can effectively bridge histomorphology and molecular state, providing a more general and interpretable foundation model for computational pathology and omics analysis.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **背景**：组织学图像（H&E染色）揭示组织形态结构和病理改变，空间转录组学在保留空间位置的同时测量局部基因表达，两者提供互补视角。但现有基础模型仅能**两两连接**模态（如组织学-组学、组织学-语言、组学-语言），缺乏一个**统一框架**来联合推断分子状态、解码空间组织架构并生成具有生物学基础的自然语言解释。
- **核心问题**：如何在一个生成式框架内，将组织形态学、空间基因表达和生物语义有效融合，实现跨尺度的可解释推理。
- **整体含义**：构建首个**三模态**基础模型 SciCore-Omics，以语言为中心，通过共享的自回归令牌空间统一三个模态，为计算病理学和空间组学分析提供更通用、更可解释的基础。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 2.1 核心思想
以**语言模型为中枢**，将组织学图像和基因表达通过模态特定编码器投影到语言模型隐藏空间，形成统一的令牌序列，支持灵活的条件输入和多任务输出。

### 2.2 模型架构
- **视觉分支**：采用视觉编码器（如ViT）提取图像特征，经Resampler模块转换为固定数量（64个）的视觉虚拟令牌，再通过投影层映射到语言模型（基于MiniCPM-V）的隐藏维度（3584）。
- **基因分支**：采用Nicheformer作为基因编码器，将基因表达谱（1500维）编码为分子嵌入，经**Q-Former**压缩为32个基因虚拟令牌，再投影到语言空间。
- **语言骨干**：基于MiniCPM-V的解码器，将文本令牌、视觉虚拟令牌和基因虚拟令牌拼接后自回归生成回答。
- **参数规模**：总共约**8.5B**参数。

### 2.3 三阶段渐进训练策略
1. **Stage I：组织学-文本对齐**（约503K图像，28.52M文本句子）  
   - 使用病理教科书和PubMed Central等来源的图像-文本对，预训练视觉分支和语言主干，学习组织形态与病理术语的对应。
2. **Stage II：基因-文本对齐**（约51,602基因-文本对）  
   - 从公共转录组资源构建基因表达谱到结构化生物描述（高表达基因、富集通路、组织元数据）的映射，训练基因编码器和投影模块。
3. **Stage III：三模态联合对齐**（151,182个空间点三联体）  
   - 使用空间转录组数据的H&E图像补丁、配对基因表达和基于证据的生物描述，联合优化所有模态。同时混合通用图像-文本和指令跟随样本防止灾难性遗忘。
- **训练目标**：组合**自回归生成损失**（标准语言模型损失）和**多模态对比损失**（InfoNCE，用于图像-文本、基因-文本、图像-基因配对）。
- **强化学习后处理**：采用轻量级离线奖励加权强化学习，改善输出格式一致性和证据忠实度，但非核心对齐步骤。

### 2.4 分子基础语义配对（transcriptome-to-language supervision）
- 自动化生成配对的生物描述：从每个空间点的基因表达中提取高表达基因、标志基因、ssGSEA富集通路，结合组织元数据，用GPT-4口头化（仅用于格式转化，不引入额外知识），形成图像-基因-文本三联体。

## 3. 实验设计：数据集、 benchmarks、对比方法

### 3.1 数据集与任务
| 任务 | 数据集 | 规模与关键信息 |
|------|--------|----------------|
| 基因表达预测（从H&E推断） | 正常人类心脏空间转录组（Human Heart Cell Atlas） | 39个切片，10折交叉验证（按切片分），预测top 50高表达基因 |
| 空间域识别 | 人类背外侧前额叶皮层（DLPFC） | 12个切片（8训练/4验证），手动皮层层注释，评估macro-F1 |
| 零样本组织病理学分类 | MHIST（二分类）、BACH（四类）、CRC100K（九类）、PatchCamelyon（二分类） | 封闭集零样本，准确率 |
| 病理视觉问答 | PathVQA | 约4998张图像，32,795对问答，开/闭式得分 |
| 病例级H&E推理 | 内部10例乳腺癌（H&E全切片+ Ki-67 IHC和病理报告作为参考） | 专家评估6个维度（准确性、推理完整性、证据质量等） |

### 3.2 对比方法
- **基因表达预测**：OmiCLIP、Hist2ST、HisToGene、BLEEP
- **空间域识别**：Nicheformer、Geneformer、scGPT、scVI、PCA（作为嵌入基线）；CellWhisperer、Cell2Sentence（文本生成基线）
- **病理分类与VQA**：LLaVA-Med、BioMedGPT、PathGen-LLaVA、Quilt-LLaVA、GPT-4o、GPT-5、Qwen3-VL、MMQ、M2I2等
- **所有方法采用原始实现或官方代码，在相同数据划分和预处理下进行比较**

### 3.3 评估指标
- 基因表达：Pearson相关系数（PCC）、均方误差（MSE）
- 空间域识别：macro-F1（嵌入线性探测）、准确率（生成式提取）
- 病理分类：准确率（封闭集零样本）
- 文本生成：BLEU-4、ROUGE-L、BERTScore F1
- VQA：开/闭式标准答案匹配

## 4. 资源与算力
- **硬件**：8 张 NVIDIA A800 GPU（每张40GB显存）
- **训练配置**：full fine-tuning，混合精度 bfloat16，梯度累积步数16，有效 batch size = 8（per-device batch size=1，累积16步）× 8 GPU = 8？实际每步累积后较大。学习率5e-4，cosine调度，warmup 0.1，weight decay 0.01，最大序列长度2048。
- **训练阶段**：Stage I 和 II 各2 epoch，Stage III 2 epoch。未报告具体训练时间（小时数）。
- **参数规模**：~8.5B，可部署于机构GPU服务器。

## 5. 实验数量与充分性
- **实验数量**：涵盖5类主要任务（基因表达预测、空间域识别、病理分类、VQA、病例推理），每类都有多个数据集或设定。
- **消融实验**：
  - 训练阶段消融：对比Stage I/II/III的文本生成质量（BLEU-4从0.024升至0.791）。
  - 模态消融：空间域识别中对比 image-only、gene-only、joint image-gene（macro-F1分别为0.801、0.496、0.850）。
  - 冻结 vs 微调视觉编码器：基因表达预测中LP vs FT（PCC从0.3679升至比OmiCLIP高23.6%）。
- **充分性**：
  - **优点**：多种任务和多数据集评估，消融设计清晰，对比基线全面（包括经典方法和最新SOTA）。采用交叉验证（心脏任务）避免空间泄漏。
  - **不足**：
    - 许多对比方法仅报告了官方已发布的结果或直接运行，但有些未进行超参数调优（论文声称使用官方实现和相同预处理）。
    - 零样本分类和VQA任务未报告置信区间或多次运行的标准差（仅报告一次结果？）。论文指出只有跨benchmark的均值标准差。
    - 病例级推理仅10例，专家评估主观性强，未报告评估者间一致性。
    - 某些对比方法（如GPT-5）参数未知，公平性存疑（但它们是通用模型，可接受）。

## 6. 论文的主要结论与发现
1. **三模态统一有效**：首次证明组织学、空间转录组和语言可在生成式框架中对齐，在多个任务上取得显著提升。
2. **基因表达预测**：在正常人类心脏数据集上，基于H&E预测基因表达，SciCore-Omics微调后PCC相对OmiCLIP提高23.6%，MSE降低15.8%。
3. **空间域识别**：在DLPFC上，联合图像-基因嵌入的macro-F1达到0.850，比最强外部嵌入基线（Nicheformer等）高出80.9%；生成式预测准确率0.497，优于所有单模态或双模态基线。
4. **零样本病理分类**：在4个H&E基准上平均准确率达56.46%，超越GPT-5（50.30%）和GPT-4o（45.36%）。
5. **H&E病例级推理**：在10例乳腺癌专家评估中，SciCore-Omics获得最高综合评分（3.67 vs Qwen3-VL的3.04），能够从低倍寻找肿瘤区域到高倍描述核异型等，并给出与Ki-67一致的增殖状态推断。
6. **解释性**：语言输出提供了形态与分子关联的语义解释，UMAP可视化显示特定通路在对应模态嵌入中有结构组织。

## 7. 优点：方法或实验设计上的亮点
- **首次三模态统一**：填补了组织学-组学-语言三者结合的空白，且采用生成式架构，支持灵活的多任务。
- **渐进训练策略**：逐步对齐各模态，避免直接高维对齐的困难，并减少了灾难性遗忘。
- **分子基础的语义配对**：自动化、可扩展地构建图像-基因-文本训练数据，无需人工标注，且保证了生物忠实性。
- **广泛评估**：涵盖从分子级（基因表达）到组织级（分类）再到病例级的推理，跨多个组织类型，对比基线全面（包括近期SOTA如OmiCLIP、Nicheformer、GPT-5等）。
- **开放贡献**：代码和模型权重将公开（Hugging Face），数据集来源清晰，可复现性较好。
- **临床潜力**：通过专家评估的病例推理展示了实际应用可能。

## 8. 不足与局限
- **训练数据精细度有限**：主要依赖组织类型标签和转录组衍生描述，缺少细胞类型组成、病理亚型、临床可行性等细粒度标注，限制了对复杂生物机制的推理。
- **病例级推理规模小**：仅10例内部乳腺癌，回顾性设计，无法得出临床有效性的确定结论。评估主观，未报告评分者间信度。
- **实验统计严谨性不足**：部分任务（如零样本分类）仅报告单次运行结果，无多次重复或置信区间；消融实验未报告多次训练的标准差。
- **基因表达预测平滑化**：模型预测的基因表达图谱相对于真实值较为平滑，可能在细节上丢失（如论文图3c散点图所示）。
- **空间域边界误差**：预测误差多出现在相邻区域边界，这是因为此处有形态连续性和转录状态混合，方法难以完美区分。
- **对比方法的公平性**：部分基线（如GPT-5）为闭源，参数规模可能远大于SciCore-Omics（8.5B），在零样本比较中仍能胜出CRC100K但总体落后；但作者控制了提示模板一致。
- **未在单一疾病上进行闭环验证**：评估分散在多种生物学背景下，未形成从分子到表型的完整疾病叙事。
- **训练时间和能耗未报告**：仅给出硬件配置，未提供训练时长、能耗或推理速度，难以比较效率。

## （完）
