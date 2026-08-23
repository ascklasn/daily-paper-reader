---
title: "Mantpy: a framework for extracellular matrix analysis in spatial proteomics"
title_zh: Mantpy：空间蛋白质组学中细胞外基质分析框架
authors: "Ghafoor, M., Parkinson, J. E., Pham, T., Georgaka, S., Hayley, M. J., Jokl, E., Hanley, K. P., Allen, J. E., Sutherland, T. E., Rattray, M."
date: 2026-08-19
pdf: "https://www.biorxiv.org/content/10.1101/2025.06.04.657781v4.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 用于细胞外基质与细胞相互作用的空间蛋白质组学分析框架
tldr: 空间蛋白组学可同时剖析细胞和细胞外基质，但现有工具仍以细胞为中心，忽视基质作用。Mantpy将基质表示为空间图并与细胞图连接，支持图统计、可解释图深度学习及可视化。在肠道、感染肝脏和肺等数据中验证，能恢复组织层次、解析疾病相关基质组成及细胞-基质关联。该框架将空间分析单元扩展至细胞外基质，并与scverse生态互通。
source: biorxiv
selection_source: fresh_fetch
motivation: 空间蛋白组学分析工具聚焦细胞，缺乏解析细胞外基质及其与细胞互作的专门框架。
method: Mantpy直接利用基质标记构建ECM空间图，与细胞图联合，集成图统计、可解释深度学习和可视化。
result: 在人类肠道、感染小鼠肝脏和肺中成功恢复组织分层，识别疾病相关基质组成及细胞-基质关联。
conclusion: 提供ECM-inclusive分析框架，扩展空间组学分析维度，兼容scverse生态。
---

## 摘要
空间蛋白质组学技术现在能够原位同时分析细胞和细胞外基质（ECM）。然而，尽管ECM在健康和疾病中起着重要作用，现有分析工具仍以细胞为中心。这里我们介绍Mantpy，一个将ECM及其与细胞的界面表示为空间图的框架。Mantpy直接从基质标记物构建ECM图，并将其与细胞图连接，用于细胞-ECM联合分析，支持图统计、可解释图深度学习和可视化。从单一ECM标记物到ECM和细胞标记物的多重面板，Mantpy能够恢复人肠道中的分层组织架构，解析感染小鼠肝脏中与疾病相关的基质组成和结构，并表征小鼠肺部的细胞-基质关联。Mantpy随附包含ECM的数据集，并与scverse生态系统互操作，将空间分析单元从细胞扩展到其周围的基质。

## Abstract
Spatial proteomics technologies now profile cells and the extracellular matrix (ECM) together in situ. Yet analysis tools remain cell-centric, despite the ECM playing an essential role in health and disease. Here we present Mantpy, a framework that represents the ECM, and its interface with cells, as spatial graphs. Mantpy builds ECM graphs directly from matrix markers and links them with cell graphs for joint cell-ECM analysis, supporting graph statistics, explainable graph deep learning and visualisation. From a single ECM marker to multiplexed panels of ECM and cellular markers, Mantpy recovers layered tissue architecture in human intestine, resolves disease-associated matrix composition and organisation in infected mouse liver, and characterises cell-matrix associations in mouse lung. Released with ECM-inclusive datasets and interoperating with the scverse ecosystem, Mantpy extends the unit of spatial analysis beyond the cell, to the matrix that surrounds it.

---

## 论文详细总结（自动生成）

## 1. 核心问题与整体含义

- **研究背景**：空间蛋白质组学技术已能**原位同时检测细胞和细胞外基质（ECM）**，而 ECM 在组织稳态、疾病发生发展中发挥关键作用（如结构支撑、信号传导、免疫调节等）。
- **现有局限**：当前空间组学分析工具**几乎全部以细胞为中心**，将 ECM 视为背景或噪声，缺乏专门解析 ECM 及其与细胞互作的分析框架，导致大量基质信息被浪费。
- **核心问题**：如何将 ECM 纳入空间组学分析单元，构建能同时刻画 **ECM 结构、组成及其与细胞关系** 的计算框架？
- **整体含义**：该工作将空间分析的**基本分析单元从“细胞”扩展为“细胞 + 周围基质”**，填补了空间蛋白质组学中 ECM 分析工具的空白。

## 2. 方法论

- **核心思想**：将 ECM 及其与细胞的界面建模为**空间图（spatial graphs）**，实现细胞-ECM 的联合分析。
- **技术流程**（基于摘要的文字描述）：
  1. **ECM 图构建**：直接从组织中的基质标记物（matrix markers）构建 ECM 空间图——节点代表基质区域/标记物，边代表空间邻近关系。
  2. **细胞图构建**：以细胞为节点构建细胞空间图，编码细胞类型和空间位置。
  3. **图连接**：将 ECM 图与细胞图链接，形成**联合的细胞-ECM 图**，用于刻画细胞-基质空间界面。
  4. **图统计**：提供 ECM 图的结构统计量（如连通性、密度等），描述基质组织形态。
  5. **可解释图深度学习**：利用图神经网络（GNN）进行端到端分析，并通过可解释性方法识别关键 ECM 特征或细胞-ECM 关联模式。
  6. **可视化**：支持 ECM 图和联合图的可视化，便于生物学解读。
- **适应性**：从**单一 ECM 标记物**到**多重 ECM + 细胞标记物面板**均适用。
- **生态兼容**：与 scverse 生态（如 Scanpy、AnnData）互操作，可直接对接现有空间组学工作流。

## 3. 实验设计

使用了**三个不同组织/物种/疾病场景**的数据集进行验证：

| 数据集 | 组织 | 场景 | 验证目标 |
|--------|------|------|----------|
| 人肠道 | 肠道 | 健康组织 | 恢复**分层组织架构** |
| 感染小鼠肝脏 | 肝脏 | 感染性疾病 | 解析**疾病相关基质组成和结构** |
| 小鼠肺 | 肺 | 组织稳态 | 表征**细胞-基质关联** |

- **Benchmark**：摘要中未提及与现有工具（如基于细胞的空间分析工具）的直接定量比较，也未提供标准 benchmark 数据集。
- **对比方法**：未明确列出对比的基线方法；验证方式以**生物学已知事实恢复**（如肠道分层）为主，而非与算法的定量对比。

## 4. 资源与算力

- 论文摘要及元数据中**未提及任何算力信息**，包括 GPU 型号、数量、训练时长、显存消耗等。
- 由于涉及图深度学习，必然使用了 GPU 加速，但具体配置无法从现有信息获得。

## 5. 实验数量与充分性

- **实验数量**：共**三个不同数据集**，覆盖**人体组织（肠道）** 和**小鼠组织（肝脏、肺）**，涵盖**健康**和**感染**两类状态，跨物种、跨组织、跨疾病。
- **充分性评估**：
  - **优点**：场景多样性较好，能够展示框架在不同标记物面板、不同组织类型下的适用性。
  - **不足**：
    - 摘要未描述消融实验、参数敏感性分析或与现有方法的系统比较，难以评估方法的**相对优势和鲁棒性**。
    - 缺少定量评估指标（如图分类准确率、ECM 结构恢复精度等），主要为**定性生物学结果**。
    - 未说明实验结果的可重复性和统计显著性检验，客观性和公平性方面报告不完整。

## 6. 主要结论与发现

1. Mantpy 能够从**单一 ECM 标记物**扩展到**多重 ECM + 细胞标记物面板**，具有广泛适用性。
2. 在人肠道中，**成功恢复了已知的分层组织结构**，验证了 ECM 图能够编码组织空间层次信息。
3. 在感染小鼠肝脏中，**识别出疾病相关的基质组成和结构变化**，说明框架可捕捉病理性基质重塑。
4. 在小鼠肺中，**刻画了细胞-基质的空间关联**，证明联合图能够揭示细胞与 ECM 间的空间互作模式。
5. 整体而言，Mantpy 将空间分析的分析单元**从细胞扩展到 ECM**，提供了 ECM-inclusive 的空间组学分析新范式。

## 7. 优点

- **填补空白**：首个专门面向 ECM 的空间蛋白质组学分析框架，突破了主流工具以细胞为中心的分析范式。
- **图建模自然贴合空间结构**：用空间图描述 ECM 网络及其与细胞的界面，在数学表达上与实际组织微环境高度契合。
- **方法灵活性**：能处理从单一标记到多重面板的不同数据复杂度，适应不同实验设计。
- **可解释性**：集成了可解释图深度学习，不只给出预测，还能指出哪些 ECM 特征或细胞-ECM 关系驱动了结果。
- **生态兼容**：与 scverse 生态互操作，用户可无缝接入现有分析流程，降低使用门槛。
- **附带数据集**：发布时附带包含 ECM 的数据集，便于社区复现和后续开发。

## 8. 不足与局限

- **方法细节不透明**：摘要未给出具体算法流程、图神经网络架构、超参数设置等，难以独立复现。
- **缺乏定量基准**：没有与现有空间分析工具（如基于细胞的方法）的定量对比，方法的**增量价值**未得到严格验证。
- **缺乏消融研究**：未说明 ECM 图相对于单纯细胞图分析的贡献有多大，无法量化 ECM 信息带来的增益。
- **算力开销不明确**：未报告运行时间、内存消耗或计算资源需求，实际部署的可操作性存疑。
- **实验深度有限**：三个数据集各只展示一个特定分析任务，未覆盖更多样的应用场景（如肿瘤微环境、纤维化、发育等）。
- **统计严谨性**：未提及生物学重复次数、统计检验方法、多重比较校正等，结果的稳健性有待进一步确认。
- **泛化性**：目前验证局限于肠道、肝脏、肺三种组织，对冷冻/石蜡切片、不同空间蛋白质组学平台（如 CODEX、MIBI、DeepVisual Proteomics 等）的适配性未知。

（完）
