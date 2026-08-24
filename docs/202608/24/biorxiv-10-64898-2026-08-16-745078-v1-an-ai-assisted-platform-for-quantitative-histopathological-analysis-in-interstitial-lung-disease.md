---
title: An AI-assisted platform for quantitative histopathological analysis in interstitial lung disease
title_zh: 人工智能辅助的间质性肺疾病定量组织病理学分析平台
authors: "Mizrahi, I., Guo, Y., He, J., Livneh, I., Stein, P., Shimron, R. B., Raz, A., Abu Saleh, M., Napso Shogan, T., Matalon, N., Hershfinkel, M., Cohen, H. A., Shemesh, A., Palty, R., Dotan, Y., Wolfenson, H., Hasson, P., Odeh, A."
date: 2026-08-19
pdf: "https://www.biorxiv.org/content/10.64898/2026.08.16.745078v1.full.pdf"
tags: ["query:hmm"]
score: 9.0
evidence: 用于全切片分析的AI辅助定量组织病理平台
tldr: 间质性肺病(ILD)的病理评估依赖半定量评分，存在主观性和采样局限。FibroSight平台结合深度学习分割与颜色特征提取，实现全叶自动化定量分析。基于博来霉素模型验证，指标与Ashcroft评分强相关且优于半自动流程，并能区分炎症与纤维化重塑。该平台提供多分区可扩展的客观量化方案，支持药物研发和转化研究。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有ILD病理评分半定量、主观、费时且采样有限，需要客观可重复的定量工具。
method: 开发FibroSight平台，联合深度学习结构分割与颜色特征提取，自动化分析天狼星红染色全叶切片。
result: 在博来霉素模型中与Ashcroft评分强相关，优于ImageJ流程，且能区分炎症和纤维化并结合人类活检验证。
conclusion: FibroSight实现多分区客观量化，为ILD的药物研发和转化研究提供可扩展分析框架。
---

## 摘要
间质性肺疾病（ILD）是一类以慢性炎症和/或纤维化为特征的异质性肺部疾病。30%–40%的ILD患者会发展为纤维化性疾病，与进行性呼吸功能下降和不良预后相关，尤其是特发性肺纤维化。目前的抗纤维化疗法可减缓疾病进展，但无法逆转纤维化，凸显了改进治疗策略的必要性。在临床前模型中进行稳健的组织病理学评估对于药物开发至关重要；然而，传统评分系统是半定量的、劳动密集、存在观察者间差异，并且依赖于有限的视野采样。在此，我们介绍了FibroSight，一个用于天狼星红染色切片中肺重构分室定量分析的独立平台。通过将基于深度学习的结构分割与基于颜色的特征提取相结合，FibroSight实现了高度自动化的全叶分析，无需复杂的计算设置。该平台量化互补的重构参数，包括实质胶原分数、实质组织密度、核面积分数、实质气腔分数，以及气道和血管相关重构。在博来霉素诱导的纤维化模型中验证后，FibroSight衍生的指标与专家Ashcroft评分高度相关，并且与组织学严重程度的关联强于基于半自动ImageJ工作流程的相应输出。该平台进一步区分了流感诱导的肺损伤中的炎症性重构与纤维性重构，并在人类ILD活检标本中展示了转化性概念验证的适用性。通过实现可扩展、可重复和多分室的组织学定量，FibroSight为肺重构的客观评估提供了一个实用框架。该方法通过整合纤维化、炎症、气道和血管相关的读数，扩展了传统的纤维化评估，支持在临床前和转化性ILD研究中更精确地分析疾病机制和治疗反应。

## Abstract
Interstitial lung diseases (ILDs) are heterogeneous pulmonary disorders characterized by chronic inflammation and/or fibrosis. 30--40% of ILD patients develop fibrotic disease that is associated with progressive respiratory decline and poor prognosis, particularly in idiopathic pulmonary fibrosis. Current antifibrotic therapies slow disease progression but do not reverse fibrosis, highlighting the need for improved therapeutic strategies. Robust histopathological evaluation in preclinical models is essential for drug development; however, conventional scoring systems are semi-quantitative, labor-intensive, subject to inter-observer variability, and rely on limited field sampling. Here, we introduce FibroSight, a standalone platform for compartment-resolved quantification of lung remodeling in Sirius Red--stained sections. By integrating deep learning--based structural segmentation with color-based feature extraction, FibroSight enables highly automated whole-lobe analysis without requiring complex computational setup. The platform quantifies complementary remodeling parameters, including parenchymal collagen fraction, parenchymal tissue density, nuclear area fraction, parenchymal airspace fraction, and airway- and vascular-associated remodeling. Validated in the bleomycin-induced fibrosis model, FibroSight-derived metrics strongly correlated with expert Ashcroft scoring and showed stronger associations with histological severity than corresponding outputs from a semi-automated ImageJ-based workflow. The platform further distinguished inflammatory from fibrotic remodeling in influenza-induced lung injury and demonstrated translational proof-of-concept applicability in human ILD biopsy specimens. By enabling scalable, reproducible, and multi-compartment histological quantification, FibroSight provides a practical framework for objective assessment of lung remodeling. This approach expands conventional fibrosis evaluation by integrating fibrotic, inflammatory, airway, and vascular-associated readouts, supporting more precise analysis of disease mechanisms and therapeutic responses in preclinical and translational ILD research.

---

## 论文详细总结（自动生成）

# 论文总结：FibroSight——间质性肺疾病定量组织病理学分析的人工智能辅助平台

## 1. 论文的核心问题与整体含义

- **研究背景**：间质性肺疾病（ILD）是一类以慢性炎症和/或纤维化为特征的异质性肺部疾病，其中约30%–40%的患者会进展为纤维化性疾病，尤其是特发性肺纤维化（IPF），预后较差。
- **临床痛点**：现有抗纤维化药物只能减缓疾病进展，无法逆转纤维化，因此需要更精准的临床前模型评估方法来支持新药研发。
- **现有评估方法的缺陷**：传统组织病理学评分系统（如Ashcroft评分）属于半定量方法，具有以下问题：
  - 劳动密集、耗时；
  - 存在观察者间差异；
  - 依赖有限视野（视野采样），无法全面反映全叶组织重构。
- **核心问题**：缺乏一种客观、可重复、可扩展的定量组织病理学分析工具，用于临床前模型中肺重构的稳健评估。
- **整体含义**：论文提出FibroSight平台，旨在通过深度学习与颜色特征提取相结合，实现全叶、多分室、自动化的纤维化/炎症定量分析，弥补传统半定量评分的不足，支持ILD药物研发和转化研究。

## 2. 论文提出的方法论

- **核心思想**：将深度学习驱动的结构分割与基于颜色的特征提取相结合，对天狼星红（Sirius Red）染色切片进行全叶自动分析，无需复杂的计算设置。
- **关键技术细节**：
  - **输入**：天狼星红染色的肺组织全切片（whole-lobe sections）。
  - **结构分割**：利用深度学习模型对肺组织结构进行分割，识别实质、气道、血管等不同分室。
  - **颜色特征提取**：基于天狼星红染色的颜色特征提取胶原含量等信息。
  - **量化参数**（互补的重构参数）：
    - 实质胶原分数（parenchymal collagen fraction）
    - 实质组织密度（parenchymal tissue density）
    - 核面积分数（nuclear area fraction）
    - 实质气腔分数（parenchymal airspace fraction）
    - 气道相关重构（airway-associated remodeling）
    - 血管相关重构（vascular-associated remodeling）
- **算法流程（文字描述）**：
  1. 对全叶切片进行数字化扫描；
  2. 深度学习模型自动分割肺结构分室；
  3. 在分割基础上提取颜色和形态学特征；
  4. 自动计算上述多种重构指标；
  5. 输出多分室定量结果，无需人工勾画或复杂编程。

## 3. 实验设计

- **数据集/场景**：
  - **主要验证场景**：博来霉素（bleomycin）诱导的肺纤维化小鼠模型——这是ILD临床前研究中最常用的纤维化模型。
  - **区分炎症与纤维化场景**：流感病毒（influenza）诱导的肺损伤模型，用于验证平台能否区分炎症性重构与纤维性重构。
  - **转化验证场景**：人类ILD活检标本（human ILD biopsy specimens），验证平台在人体样本中的适用性。
- **基准/对比方法**：
  - **专家Ashcroft评分**：作为病理学严重程度的“金标准”半定量评分，用于相关性验证。
  - **半自动ImageJ工作流程**：作为对比方法，比较其与FibroSight输出指标与组织学严重程度的相关性强弱。
- **评估方式**：
  - 计算FibroSight衍生指标与Ashcroft评分的相关性；
  - 比较FibroSight与ImageJ流程的指标与组织学严重程度的关联强度。

## 4. 资源与算力

- **未明确说明**：论文摘要和元数据中未提及所使用的GPU型号、数量、训练时长、内存等算力信息。
- 可能原因：该平台强调“无需复杂计算设置”，说明其设计面向易用性，但深度模型训练的具体硬件资源信息缺失，无法评估训练成本。

## 5. 实验数量与充分性

- **实验组数**：
  - 至少包含3个主要实验场景：博来霉素纤维化模型、流感损伤模型、人类ILD活检标本。
  - 对比实验：与Ashcroft评分相关性、与ImageJ工作流程对比。
- **充分性评估**：
  - **优点**：覆盖了临床前模型和人类样本，且对比了传统半定量评分和半自动工具，验证维度较全面。
  - **不足**：
    - 摘要中未给出具体的样本量、模型重复次数、统计显著性数值（如p值、相关系数、置信区间等）；
    - 未见消融实验（如不同分割模型、不同颜色阈值的影响）；
    - 未见多中心/多观察者一致性验证；
    - 未说明博来霉素模型中的剂量、时间点、组别等关键细节。
  - **公平性**：由于缺少详细实验设置，无法完全评估方法比较的公平性（例如ImageJ流程是否经过优化、是否使用相同的切片输入等）。

## 6. 论文的主要结论与发现

- **强相关性**：FibroSight衍生指标与专家Ashcroft评分高度相关，在博来霉素模型中有效反映纤维化严重程度。
- **优于半自动方法**：与半自动ImageJ工作流程相比，FibroSight的指标与组织学严重程度的关联更强。
- **区分炎症与纤维化**：平台能够区分流感诱导的炎症性重构与博来霉素诱导的纤维性重构，说明其不局限于单一纤维化指标。
- **转化可行性**：在人类ILD活检标本中展示了转化应用的概念验证，支持未来用于临床样本分析。
- **多分室扩展**：通过整合纤维化、炎症、气道和血管相关读数，扩展了传统纤维化评估，为客观评估肺重构提供了实用框架。

## 7. 优点

- **高度自动化**：深度学习分割与颜色特征提取相结合，实现全叶级别自动分析，减少人工干预和主观偏差。
- **全叶覆盖**：不再依赖有限视野采样，提高采样的全面性和代表性。
- **多参数、多分室定量**：不仅评估实质胶原，还涵盖组织密度、核面积、气腔分数、气道和血管相关重构，提供更全面的病理图谱。
- **独立易用平台**：无需复杂计算设置，方便非计算专业研究者使用。
- **验证扎实且有转化性**：在多个模型和人类标本中验证，并直接与现有Ashcroft评分和ImageJ方法比较，凸显实用价值。

## 8. 不足与局限

- **信息透明性不足**：论文摘要未提供详细的实验数据（如样本量、统计量、模型结构、训练细节），降低可复现性评估的可能性。
- **算力信息缺失**：深度学习模型的训练资源和成本未披露，难以判断平台的可及性和复现难度。
- **验证范围有限**：
  - 主要依赖博来霉素模型，该模型虽然常用但并不能完全代表人类ILD的复杂异质性；
  - 人类验证仅为“概念验证”，样本量可能有限；
  - 未提及对其他常见ILD模型（如基因突变模型、辐射模型）的适用性。
- **方法比较可能不公平**：对ImageJ工作流程的具体实现细节未知，可能未与其最优化配置相比。
- **应用限制**：
  - 依赖于天狼星红染色质量，不同实验室染色差异可能影响颜色特征提取的稳健性；
  - 对于非常严重的组织破坏（如蜂窝肺）或特殊病理形态，分割算法可能存在误判；
  - 目前主要面向组织学切片，是否能直接用于活体成像或其它成像方式未说明。
- **缺乏前瞻性验证**：尚未证明该平台在不同实验室、不同病理医师背景下的泛化性能。

（完）
