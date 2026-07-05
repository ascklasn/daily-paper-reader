---
title: Development of a multiplex immunofluorescence panel to study heterogenous cancer-associated fibroblast subtypes with spatial resolution
title_zh: 开发一种多重免疫荧光面板，用于研究具有空间分辨率的异质性癌症相关成纤维细胞亚型
authors: "Burley, A., Silveira, T., James, N., Salto-Tellez, M., Wilkins, A. C."
date: 2026-07-01
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.26.734718v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 空间蛋白质组学分析与多重免疫荧光
tldr: 单细胞RNA测序丢失空间信息，空间转录组成本高。本研究针对癌症相关成纤维细胞（CAF）亚型，开发了包含α平滑肌肌动蛋白、成纤维细胞激活蛋白、平足蛋白和血小板衍生生长因子受体α及CD8和泛角蛋白的多重免疫荧光面板。通过优化和验证，该面板实现了低成本、可扩展的空间蛋白质组学分析，有效区分CAF亚型，为研究肿瘤微环境空间拓扑提供了实用工具。
source: biorxiv
selection_source: fresh_fetch
motivation: 解决单细胞测序丢失空间信息及空间转录组成本高的问题，实现对癌症相关成纤维细胞亚型的空间分辨分析。
method: 设计并优化了含四个CAF标志物（SMA、FAP、PDPN、PDGFR）及CD8和pan-cytokeratin的多重免疫荧光面板，通过验证实验确保其有效性和可重复性。
result: 成功建立适用于大规模临床队列的多重免疫荧光方案，能够高分辨率区分CAF亚型。
conclusion: 该面板保留空间相互作用且成本可及，为研究CAF异质性和肿瘤微环境空间拓扑提供了可行工具。
---

## 摘要
背景：单细胞RNA测序提供了丰富的信息来探索肿瘤微环境的复杂性，但关键是肿瘤的空间拓扑结构丢失了，研究细胞相互作用受到限制。空间转录组学旨在解决这一问题，然而该技术对于从有意义的临床队列中生成数据而言，成本仍然过高。相比之下，使用多重免疫荧光进行空间蛋白质组学分析，保留了空间相互作用，成本相对可及，并且可扩展至大型临床队列，以解决强大的转化医学问题。尽管近年来多重方法取得了进展，但我们注意到癌症相关成纤维细胞（CAFs）的探索尚不详细，这可能是由于CAF异质性以及用于定义它们的标记物多样性所带来的困难。

方法：我们设计、优化并验证了一个多重免疫荧光面板，该面板结合了四种常用的CAF标记物：α-平滑肌肌动蛋白（SMA）、成纤维细胞活化蛋白（FAP）、平足蛋白（PDPN）和血小板衍生生长因子受体α（PDGFR），以及CD8和泛细胞角蛋白。在此，我们分享了我们的方法学以及为最终面板设计所采取的实践考量。我们还强调了稳健优化实验的好处。

## Abstract
BackgroundSingle cell RNA sequencing provides a wealth of information to explore the complexities of the tumour microenvironment, but crucially the spatial topology of the tumour is lost and studying cellular interactions is limited. Spatial transcriptomics aims to address this however the technique remains cost prohibitive for the generation of data from meaningfully-sized clinical cohorts. In contrast, spatial proteomic profiling with multiplex immunofluorescence, preserves spatial interactions, is relatively cost accessible, and is scalable for large clinical cohorts to address powerful translational questions. Whilst multiplex approaches have advanced in recent years, we note that cancer-associated fibroblasts (CAFs) have been explored in less detail, potentially due to difficulties associated with CAF heterogeneity and the diversity of markers used to define them.

MethodsWe designed, optimised, and validated a multiplex immunofluorescence panel that combines four frequently used CAF markers; alpha smooth muscle actin (SMA), fibroblast activation protein (FAP), podoplanin (PDPN) and platelet-derived growth factor receptor alpha (PDGFR) with CD8 and pan-cytokeratin. Here we share our methodology and the practical considerations taken to inform the final panel design. We also highlight the benefits of robust optimisation experiments.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：肿瘤微环境（TME）中的癌症相关成纤维细胞（CAFs）具有高度异质性，但单细胞RNA测序技术丢失了空间拓扑信息，而空间转录组学成本过高，难以应用于大规模临床队列。
- **核心问题**：开发一种低成本、可扩展的空间蛋白质组学方法，以高分辨率区分CAF亚型并保留细胞间的空间相互作用。
- **整体含义**：为转化医学研究提供一种实用的多重免疫荧光（mIF）面板，能够在大样本临床队列中研究CAF异质性与空间分布，从而推动对肿瘤微环境空间拓扑的理解。

## 2. 论文提出的方法论

- **核心思想**：利用多重免疫荧光（mIF）技术，组合四种常用CAF标记物（α-SMA、FAP、PDPN、PDGFRα）以及免疫细胞标记物CD8和上皮标记物泛角蛋白（pan-cytokeratin），实现CAF亚型的空间分辨检测。
- **关键技术细节**：
  - 面板设计：包含6个指标，其中4个CAF标志物用于区分不同CAF亚型，CD8标记细胞毒性T细胞，泛角蛋白标记肿瘤上皮细胞。
  - 优化与验证：通过一系列优化实验（如抗体滴定、抗原修复、信号串扰验证）确保面板的特异性和重复性。
  - 流程：依次进行多轮染色、成像和抗体剥离，最终生成多重图像。
- **公式或算法流程**：文中未涉及数学公式，实验流程为湿实验操作步骤。

## 3. 实验设计

- **使用的数据集/场景**：论文未明确提及具体临床样本或公开数据集，但表明该面板适用于大型临床队列（如肿瘤组织切片）。
- **Benchmark**：无明确的benchmark方法，但隐含对比对象为单细胞RNA测序（丢失空间信息）和空间转录组学（成本高）。
- **对比的方法**：未进行直接的算法或技术对比，主要强调mIF相对于scRNA-seq和空间转录组的优势（成本低、保留空间信息、可扩展）。

## 4. 资源与算力

- **文中未明确说明**：未提及GPU型号、数量、训练时长等任何算力信息。论文仅涉及湿实验优化，无深度学习模型训练或计算资源消耗。

## 5. 实验数量与充分性

- **实验数量**：论文主要描述了方法学开发和验证过程，但未给出具体实验组数（如不同组织类型、不同抗体组合的对比实验数量）。
- **充分性**：
  - **优点**：作者强调了“稳健优化实验的好处”，说明进行了抗体滴定、信号串扰、多重染色顺序等系统优化，这在方法学论文中较为充分。
  - **不足**：缺乏大规模临床队列的验证结果，也未与现有空间蛋白质组学平台（如CODEX、CyTOF）进行直接比较。实验覆盖范围有限，仅基于原理验证。

## 6. 论文的主要结论与发现

- 成功设计并验证了一个包含SMA、FAP、PDPN、PDGFRα、CD8和泛角蛋白的多重免疫荧光面板。
- 该面板能够以高分辨率区分CAF亚型，同时保留空间相互作用。
- 该方法成本相对可及，且可扩展至大型临床队列，为研究CAF异质性和肿瘤微环境空间拓扑提供了可行工具。

## 7. 优点

- **方法学创新**：针对CAF异质性专门设计的多重标记物组合，填补了当前mIF面板在CAF亚型研究中的空白。
- **实用性**：强调低成本、可扩展性，适合转化医学中的大规模样本分析。
- **优化策略**：提供了优化实验的实践考量，包括抗体选择、抗原修复、串扰控制等，提高了方法的可靠性和重复性。

## 8. 不足与局限

- **实验覆盖不足**：未在多个独立临床队列或不同癌种中验证，仅在方法学层面证明可行性。
- **偏差风险**：CAF标志物选择基于文献常见组合，可能遗漏某些罕见亚型或跨肿瘤特异性标志物。
- **应用限制**：
  - 多重免疫荧光技术本身存在抗体兼容性限制，最多只能同时检测6-8个指标，无法覆盖所有已知CAF亚型。
  - 缺乏与空间转录组学或单细胞RNA测序的直接结果对比，无法评估其相对于gold standard的准确性。
  - 未讨论图像分析算法（如细胞分割、空间统计）的标准化流程，可能影响结果可重复性。

（完）
