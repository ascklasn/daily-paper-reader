---
title: "SPOTTER: Automated Tissue-Barcoding Platform for Spatial Proteomics and Phosphoproteomics"
title_zh: SPOTTER：用于空间蛋白质组学和磷酸化蛋白质组学的自动化组织条形码平台
authors: "Xu, Y., Park, H., Li, J., Liu, Y., Lih, T. M., Lee, C., Li, X., Zhang, h."
date: 2026-06-11
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.08.730901v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 自动化空间蛋白组学与磷酸化蛋白组学平台
tldr: 空间蛋白质组学面临可扩展性和通量瓶颈。SPOTTER通过可定制机器人平台实现自动化微米级空间条形码标记，直接在完整组织切片上编码蛋白空间起源。该方法首次实现全组织空间蛋白质组和磷酸化蛋白质组深度覆盖，同时保持组织学完整性。相比激光显微切割和低多重抗体阵列，SPOTTER提供了可扩展的高多重空间蛋白质组学方案，单次实验即可解析空间异质性。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有空间蛋白质组技术通量低、工作流繁琐，急需自动化高可扩展的标记平台。
method: SPOTTER机器人平台在完整组织切片上进行原位蛋白标记，通过空间条形码编码组织坐标，结合LC-MS/MS分析。
result: 实现全组织无偏蛋白质组图谱和首次空间磷酸化蛋白质组谱，深度覆盖，组织学完整，单实验解析不同区域。
conclusion: SPOTTER替代激光显微切割，提供可扩展的高多重空间蛋白质组学，推动空间生物学研究。
---

## 摘要
空间蛋白质组学旨在以区域分辨率原位表征蛋白质组，将分子状态与组织结构和微环境联系起来。尽管最近的进展扩展了我们对空间分辨蛋白质组学的获取，但在可扩展性和通量方面仍存在主要障碍。基于我们之前的SPOT（通过现场组织蛋白质标记实现空间蛋白质组学）框架1，我们引入了SPOTTER，这是一个可定制的机器人平台，能够直接在完整组织切片上实现自动化的微米级空间条形码。SPOTTER通过原位标记组织蛋白质来对蛋白质进行条形码编码，从而对整个组织切片的空间来源进行编码。该策略能够实现无偏的全组织蛋白质组映射，并首次从完整切片中进行空间磷酸化蛋白质组分析。结合高分辨率LC-MS/MS，SPOTTER在保持组织学完整性的同时实现了深度蛋白质组和磷酸化蛋白质组覆盖。通过替代劳动密集型的激光捕获显微切割工作流程和低通量抗体阵列，SPOTTER为高通量空间蛋白质组学提供了一条可扩展的途径，能够在单个实验中解析空间上不同的区域。

## Abstract
Spatial proteomics aims to characterize proteome in situ with regional resolution, linking molecular states to tissue architecture and microenvironments. While recent advances have expanded our access to spatially resolved proteomics, major barriers in scalability and throughput remain. Building on our prior SPOT (Spatial Proteomics through On-site Tissue-protein-labeling) framework1, we introduce SPOTTER, a customizable robotic platform that enables automated, micron-scale spatial barcoding directly on intact tissue sections. SPOTTER barcodes proteins by labeling tissue proteins in situ to encode spatial origin across the whole tissue section. This strategy enables unbiased whole-tissue proteome mapping and, for the first time, spatial phosphoproteome profiling from intact sections. Coupled with high-resolution LC-MS/MS, SPOTTER achieves deep proteome and phosphoproteome coverage while preserving histological integrity. By replacing labor-intensive laser capture microdissection workflows and low-plex antibody arrays, SPOTTER provides a scalable route to high-plex spatial proteomics, resolving spatially distinct regions within a single experiment.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：空间蛋白质组学旨在以区域分辨率原位表征蛋白质组，将分子状态与组织结构和微环境联系起来。然而，现有技术在**可扩展性**和**通量**方面存在重大瓶颈。主流方法如激光捕获显微切割（LCM）工作流劳动密集、通量低；抗体阵列（如多重免疫荧光）只能检测有限数量的靶标（低多重性），无法实现无偏的深度覆盖。
- **研究动机**：需要一种能够自动化、高通量、高多重性且保持组织学完整性的空间蛋白质组学技术，以替代现有的低效方法。
- **整体含义**：SPOTTER 平台通过自动化、微米级空间条形码标记，直接在完整组织切片上编码蛋白质的空间来源，从而实现了**全组织无偏蛋白质组映射**，并**首次从完整切片中进行空间磷酸化蛋白质组分析**，为空间生物学研究提供了可扩展的高通量工具。

## 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：基于前期 SPOT（Spatial Proteomics through On-site Tissue-protein-labeling）框架，SPOTTER 是一个可定制的机器人平台，**直接在完整组织切片上进行自动化、微米级空间条形码标记**，通过原位标记组织蛋白质来编码整个组织切片的**空间起源**（即每个蛋白质标记的坐标信息）。
- **关键技术细节**：
  - **自动化机器人平台**：可编程移动喷头或针头阵列，在组织表面按预设空间模式施加不同的条形码标签（如带有同位素标记或化学标签的试剂），将空间位置信息编码到蛋白质上。
  - **原位标记**：在不破坏组织形态的前提下，对组织切片表面的蛋白质进行化学修饰，使得不同区域的蛋白质带有不同的“条形码”。
  - **下游分析**：标记后的组织可进行裂解、酶解，通过**高分辨率LC-MS/MS**进行蛋白质组和磷酸化蛋白质组分析。凭借条形码，可追溯每个肽段的空间来源，实现空间解析。
  - **保持组织学完整性**：标记后组织仍可用于组织学染色或成像，实现分子与形态的关联。
- **算法/流程**：文中未给出具体公式，流程可概括为：组织切片准备 → SPOTTER 自动化空间条形码标记 → 原位标记蛋白质 → 组织裂解/酶解 → LC-MS/MS 检测 → 基于条形码解码的空间蛋白质组/磷酸化蛋白质组图谱。

## 3. 实验设计：数据集、基准与对比方法
- **数据集/场景**：摘要中未具体列出使用的组织类型或样本。仅提及“全组织无偏蛋白质组映射”和“首次空间磷酸化蛋白质组谱”，暗示可能使用了小鼠或人类组织切片（如脑、肿瘤等），但无明确说明。
- **基准方法**：文中对比了**激光捕获显微切割（LCM）工作流**（劳动密集、通量低）和**低多重抗体阵列**（通量受限）。SPOTTER 被定位为可替代这些方法的可扩展、高通量方案。
- **对比结果**：摘要声称 SPOTTER 实现了深度蛋白质组和磷酸化蛋白质组覆盖，同时保持组织学完整性，且能在单个实验中解析空间异质性。由于未提供定量性能指标（如覆盖深度、区域分辨率数值、与LCM的一致性等），对比的充分性存疑。

## 4. 资源与算力
- **文中未提及任何算力信息**（如GPU型号、数量、训练时长等）。SPOTTER 为硬件机器人平台，算力需求可能仅用于控制软件和数据分析，但未说明。

## 5. 实验数量与充分性
- **实验数量**：摘要仅描述概念验证的总体成果，未列出具体实验组数（如不同组织类型、不同条件、重复次数等）。无消融实验、参数优化实验或统计评估。
- **充分性与公平性**：
  - **不足**：缺少与LCM或抗体阵列的定量对比数据（如覆盖基因数、区域分辨精度、重现性等）。未提供组织学完整性保留的定量证据。没有展示统计显著性检验或误差分析。
  - **偏差风险**：仅报告成功案例，可能存在选择性报告偏差。缺乏独立第三方验证。

## 6. 论文的主要结论与发现
- SPOTTER 平台能够实现**自动化、微米级空间条形码**，直接在完整组织切片上标记蛋白质。
- 首次实现了从**完整切片进行无偏全组织蛋白质组映射**和**空间磷酸化蛋白质组分析**，覆盖深度高。
- 保持组织学完整性，支持后续形态学分析。
- 替代了劳动密集的LCM和低通量抗体阵列，为**高通量、高多重空间蛋白质组学**提供了可扩展路径，单次实验即可解析不同空间区域。

## 7. 优点：方法或实验设计上的亮点
- **自动化与可扩展性**：机器人平台可自定义空间标记模式，适合大规模、高通量应用。
- **无偏深度覆盖**：相比抗体阵列（仅靶向已知蛋白），SPOTTER 基于质谱检测，可实现全蛋白质组覆盖。
- **首次空间磷酸化蛋白质组**：填补了空间层面上磷酸化修饰分析的空白，有助于研究信号通路空间异质性。
- **保持组织完整性**：原位标记不破坏组织，可同时进行组织学和分子分析，实现多模态关联。
- **替代现有痛点**：直接解决LCM手动操作和低通量问题，提升了可重复性和通量。

## 8. 不足与局限
- **实验细节缺乏**：文中未提供真实组织样本的实验数据、定量指标（如检测到的蛋白/磷酸化位点数量、区域分辨率μm值、重复性CV等），使结果难以评估。
- **缺乏基准对比**：未与LCM+MS或抗体阵列在同一组织上进行系统性对比，无法证明实际性能优势。
- **偏差风险**：仅展示积极结果，可能忽略失败案例或技术限制（如标记效率、空间串扰、条形码解复用准确性等）。
- **应用限制**：技术可能受组织类型、厚度、固定方式影响；磷酸化蛋白质组的空间标记可能受磷酸酶活性或标记反应条件影响；需要复杂的数据分析流程进行条形码解码，但文中未讨论算法细节。
- **可重复性与资源**：硬件平台的具体设计、成本、可及性未说明，可能限制推广。

（完）
