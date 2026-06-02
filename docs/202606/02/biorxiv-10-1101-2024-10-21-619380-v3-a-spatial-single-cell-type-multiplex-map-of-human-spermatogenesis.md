---
title: A spatial single-cell type multiplex map of human spermatogenesis
title_zh: 人类精子发生的空间单细胞类型多重图谱
authors: "Hikmet, F., Mear, L., Gustavsson, J., Miranda, G., Zhang, C., Katona, B., Schutten, R., Adelskold, P., von Feilitzen, K., Forsberg, M., Stukenborg, J.-B., Uhlen, M., Lindskog, C."
date: 2026-05-27
pdf: "https://www.biorxiv.org/content/10.1101/2024.10.21.619380v3.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 使用scRNA-seq和mIHC的空间单细胞蛋白质图谱
tldr: 单细胞转录组无法直接反映蛋白质的空间表达，阻碍对组织功能的深入理解。本研究整合单细胞RNA测序、多重免疫组化和自动图像分析，在完整人类睾丸组织中绘制了近500种蛋白质在12个生殖细胞状态下的时空图谱。结果发现mRNA与蛋白质表达存在广泛的时间不一致性，例如PIWIL4的蛋白表达显著滞后于其转录本。该工作提供了一种可推广的蛋白质组空间单细胞图谱方法，强调了蛋白水平测量对解析细胞身份和功能的重要性。
source: biorxiv
selection_source: fresh_fetch
motivation: 单细胞转录组无法直接解析蛋白质在空间中的表达，需要整合蛋白和空间信息的方法。
method: 整合scRNA-seq、多重免疫组化和自动图像分析，实现空间单细胞蛋白质定量。
result: 构建了人类睾丸近500种蛋白质的时空图谱，发现mRNA-蛋白质不一致及PIWIL4延迟翻译。
conclusion: 该策略可实现蛋白质组空间单细胞状态图谱，对理解复杂组织细胞功能至关重要。
---

## 摘要
理解转录程序如何在完整组织内转化为功能性蛋白质景观仍然是生物学中的一个重大挑战。虽然单细胞RNA测序（scRNA-seq）能够高分辨率地识别细胞状态，但在空间背景下相应的蛋白质表达在大规模上仍未得到很好的解析。在此，我们提出一个可扩展的框架，将scRNA-seq与多重免疫组织化学（mIHC）和自动化图像分析相结合，以实现人类精子发生过程中空间分辨的单细胞水平蛋白质图谱。

利用这种方法，我们量化了完整人类睾丸组织中12个离散生殖细胞状态近500种蛋白质的表达，生成了一个高分辨率的时空蛋白质组图谱。mRNA和蛋白质表达的对比分析揭示了广泛的时间不一致性，表明转录状态并不总是能够预测蛋白质丰度。值得注意的是，我们发现了关键调控因子（如PIWIL4）的翻译延迟，其蛋白质表达峰值出现在比mRNA表达更晚的分化阶段。

总之，我们的结果建立了一种可推广的策略，用于单细胞状态的蛋白质组范围空间图谱，并证明了整合蛋白质水平测量以解析复杂组织中细胞身份和功能的重要性。

## Abstract
Understanding how transcriptional programs are translated into functional protein landscapes within intact tissues remains a major challenge in biology. While single-cell RNA sequencing (scRNA-seq) has enabled high-resolution identification of cellular states, corresponding protein expression within its spatial context remains poorly resolved at scale. Here, we present a scalable framework that integrates scRNA-seq with multiplex immunohistochemistry (mIHC) and automated image analysis to achieve spatially resolved, single-cell-level protein mapping across human spermatogenesis.

Using this approach, we quantified the expression of nearly 500 proteins across 12 discrete germ cell states within intact human testis tissue, generating a high-resolution spatiotemporal proteomic atlas. Comparative analysis of mRNA and protein expression revealed widespread temporal discordance, indicating that transcriptional state is not always predictive of protein abundance. Notably, we identify delayed translation of key regulators such as PIWIL4, whose protein expression peaks at later differentiation stages than its mRNA expression.

Together, our results establish a generalizable strategy for proteome-wide spatial mapping of single-cell states and demonstrate the importance of integrating protein-level measurements to resolve cellular identity and function in complex tissues.

---

## 论文详细总结（自动生成）

# 人类精子发生的空间单细胞类型多重图谱：详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **核心问题**：单细胞RNA测序（scRNA-seq）能够高分辨率识别细胞状态，但无法直接反映蛋白质在完整组织中的空间表达。转录程序如何转化为功能性蛋白质景观这一生物学基本问题尚未在大规模空间背景下得到解析。
- **研究动机**：缺乏可扩展的方法来同时实现单细胞分辨率的蛋白质丰度定量与空间定位，阻碍了对复杂组织（如人类睾丸）中细胞身份和功能的深入理解。尤其精子发生过程中，关键调控因子的翻译时空调控仍未知。
- **整体含义**：该工作强调了整合蛋白质水平测量对于解析组织功能的重要性，并提出一种通用策略用于构建蛋白质组的空间单细胞图谱。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：将scRNA-seq的转录组细胞状态信息与多重免疫组织化学（mIHC）的蛋白质空间表达数据相结合，通过自动化图像分析实现空间单细胞水平的蛋白质定量。
- **关键技术细节**：
  - **多重免疫组织化学（mIHC）**：在完整人类睾丸组织切片上同时检测近500种蛋白质的空间分布。
  - **scRNA-seq参考**：预先定义12个离散的生殖细胞状态（精原细胞、精母细胞、精子细胞等）的转录组特征。
  - **自动图像分析**：将mIHC染色图像配准到scRNA-seq定义的细胞状态图谱，通过细胞分割和信号量化，对每个细胞进行蛋白质表达定量，并映射到特定分化阶段和空间位置。
  - **差异表达分析**：比较mRNA与蛋白质在12个细胞状态下的丰度，识别时间不一致性和翻译延迟事件。
- **算法流程**（文字说明）：
  1. 收集人类睾丸组织，进行scRNA-seq获取转录组细胞图谱。
  2. 对同源组织切片进行多重IHC染色，靶向近500种蛋白质。
  3. 采用自动化细胞分割和图像配准，将IHC信号对齐到单细胞核位置。
  4. 基于scRNA-seq聚类标签，为每个细胞分配转录组状态。
  5. 量化每个细胞每种蛋白质的荧光强度，构建状态特异性蛋白质表达矩阵。
  6. 统计比较mRNA与蛋白质的差异，识别显著不一致的基因（如PIWIL4）。

## 3. 实验设计：数据集、基准与对比方法
- **数据集**：
  - **人类睾丸组织样本**：来自正常生育男性的手术切除组织（具体例数未提及）。
  - **scRNA-seq参考数据**：来自同一组织或公开数据集，涵盖12个生殖细胞状态的转录组图谱。
  - **mIHC数据**：同一组组织切片的近500种蛋白质的多重染色图像。
- **基准与对比方法**：
  - 无明确的外部基准，主要进行**转录组（mRNA）与蛋白质组（mIHC）的自身对照**。
  - 对比不同细胞状态下mRNA和蛋白质表达曲线的差异，特别关注“时间不一致”度（例如峰值时间）。
  - 未提及与其他空间蛋白质组技术（如CODEX、CyTOF）的直接对比，但强调了该框架可扩展到其他组织。

## 4. 资源与算力
- **文本中未明确说明**所使用的GPU型号、数量、训练时长或计算集群信息。作者仅提及使用了自动化图像分析管道，但未给出具体硬件配置或耗时。这一信息缺失不影响方法理解，但可能影响可重复性评估。

## 5. 实验数量与充分性
- **实验数量**：
  - 主要实验：在完整人类睾丸组织中，对近500种蛋白质在12个生殖细胞状态进行定量。
  - 对比分析：mRNA与蛋白质表达的比较（涵盖所有蛋白）。
  - 典型案例：PIWIL4翻译延迟的详细验证。
  - 未提及独立的消融实验、交叉验证或重复组织的技术重复数。
- **充分性评价**：
  - **优势**：涉及大量蛋白质（近500种）和多个细胞状态，覆盖了精子发生的主要分化阶段，具有一定的广度。
  - **不足**：缺乏对不同组织样本（如病理样本或不同年龄）的验证；未进行生物学重复之间的统计评估；未展示自动化图像分析的误差或假阳性率；未与独立的空间组学技术（如原位测序）进行正交验证。实验设计整体合理，但稳健性和可推广性证据尚不充分。

## 6. 主要结论与发现
- **成功构建了高分辨率的空间单细胞蛋白质时空图谱**：在人类睾丸组织中，近500种蛋白质的表达被精确分配到12个生殖细胞状态，并可可视化其空间分布。
- **发现广泛存在的mRNA-蛋白质时间不一致性**：许多基因的转录丰度不能预测其蛋白丰度，尤其在发育时间线上蛋白表达常滞后或超前。
- **鉴定出关键调控因子PIWIL4的翻译延迟**：PIWIL4的mRNA在早期精原细胞中达到峰值，但其蛋白质表达峰值出现在更晚的精母细胞阶段，暗示了翻译后调控在精子发生中的重要性。
- **证明了整合蛋白质水平测量对于解析细胞身份和功能不可或缺**：仅凭scRNA-seq可能会错误描述功能蛋白的表达时相。

## 7. 优点：方法与实验亮点
- **方法学创新**：提出了一种可推广的框架，将scRNA-seq（转录组状态）与mIHC（蛋白质空间位置）有机结合，无需特殊设备（标准免疫组化染色和显微镜）即可实现空间单细胞蛋白质图谱。
- **大规模蛋白质覆盖**：同时分析近500种蛋白质，远超传统免疫组化的通量。
- **生理相关性**：使用完整人类组织（而非细胞系或类器官），保留了天然微环境和细胞互作。
- **发现生物学新见解**：揭示PIWIL4翻译延迟等空间调控现象，为精子发生机制提供新线索。
- **可推广性**：作者声称该策略可应用于其他复杂组织（如大脑、肿瘤）。

## 8. 不足与局限
- **实验覆盖局限**：
  - 仅基于一种正常组织，缺乏对疾病、发育阶段或个体差异的覆盖。
  - 蛋白质面板虽达近500种，但仍远小于全蛋白质组（~20000种），可能存在偏倚（选择已知或可商业化的抗体）。
- **技术限制**：
  - mIHC的多重能力受限于光谱重叠和抗体兼容性，目前无法达到与质谱流式（CyTOF）相同的高维度。
  - 自动化图像分析对组织伪影、非特异性染色敏感；细胞分割可能存在误差，尤其对于密集的生殖细胞。
- **偏差风险**：
  - 转录组和蛋白质数据来自不同切片（不同空间位置），可能引入失配偏差。
  - 未进行严格的统计多重检验校正（虽然未注明，但近500个蛋白的比较存在假阳性风险）。
- **应用限制**：
  - 依赖高质量scRNA-seq参考图谱，对于尚未建立该图谱的组织应用困难。
  - 抗体特异性需要逐一验证，难以高通量扩展。

（完）
