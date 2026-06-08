---
title: Label-free 3D virtual histology of human formalin-fixed paraffin-embedded (FFPE) prostate needle biopsies with propagation-based phase-contrast micro-CT (PBCT)
title_zh: 基于传播的相位对比显微CT的人福尔马林固定石蜡包埋前列腺穿刺活检无标记三维虚拟组织学
authors: "Sugarman, A. L., Vanselow, D. J., Chen, G., Clark, E., Parkinson, D., La Riviere, P., Silverman, J., Warrick, J., Cheng, K. C. C."
date: 2026-06-07
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.28.728215v2.full.pdf"
tags: ["query:spatialprot"]
score: 7.0
evidence: 三维虚拟组织学用于空间组织分析
tldr: "传统组织学基于2D切片，存在采样不足和无法完整评估3D结构的局限。本研究采用传播相位衬度显微CT（PBCT）对人FFPE前列腺穿刺活检进行无标记3D虚拟组织学成像，实现0.5微米各向同性分辨率。PBCT重建能区分良性组织及Gleason 3、4、5级前列腺癌，并通过cycleGAN生成虚拟H&E染色。该方法无破坏性，能获取3D组织构架，避免切片伪影，有望推动肿瘤定量分析并改善临床评估。"
source: biorxiv
selection_source: fresh_fetch
motivation: 传统组织学依赖2D切片，采样有限且无法完整评估3D细胞体积和组织构架。
method: "采用传播相位衬度显微CT（PBCT）对FFPE前列腺穿刺活检进行无标记3D成像，结合cycleGAN生成虚拟H&E染色。"
result: "PBCT区分良性组织及Gleason 3-5级前列腺癌，虚拟H&E染色与真实组织学一致。"
conclusion: PBCT实现无破坏性3D虚拟组织学，避免采样和切片伪影，为肿瘤定量分析提供新途径。
---

## 摘要
一个多世纪以来，从肿瘤活检中评估临床结果的目标一直基于二维组织切片（仅代表所收集样本的一小部分）的组织形态学。其力量源于组织学的1) 细胞类型的无偏差表征，2) 允许跨细胞类型表征健康和疾病状态的亚细胞分辨率，以及3) 允许评估肿瘤异质性的多毫米视野。然而，组织学对物理切片的依赖限制了对三维细胞体积和组织结构的评估。在此，我们使用基于传播的相位对比显微CT（PBCT）创建了残余福尔马林固定、石蜡包埋（FFPE）前列腺穿刺活检的三维组织学图像。得到的各向同性、灰度、0.5微米体素矩阵用于探索三维虚拟组织学区分良性前列腺组织和Gleason分级3、4、5级前列腺腺癌等诊断类别的潜力。数字切片堆叠（总计5微米“切片”）的最大强度投影使我们能够研究对应于显微CT成像后实际连续H&E染色组织切片的虚拟切片。与组织学一样，我们的PBCT重建使我们能够区分良性前列腺组织的非浸润性和波状腺体、Gleason 3级的浸润性圆形腺体、Gleason 4级的筛状结构以及Gleason 5级的粉刺样坏死。与组织学不同，显微CT使我们能够在体积背景下进一步探测三维组织结构。使用定制的Neuroglancer多平面和三维渲染界面实现了样本体积的用户友好探索。稀疏训练的cycleGAN从未染色的显微CT重建中生成了合理的虚拟H&E染色。与基于组织切片的组织学不同，基于显微CT的虚拟组织学提供了癌细胞和组织结构（包括腺体空间）的无损三维表征，且无组织学的欠采样或切割伪影。这些发现证明了基于PBCT的前列腺癌三维虚拟组织学的可行性，并建议探索衍生出的肿瘤特性定量分析，以潜在促进患者护理。

## Abstract
For over a century, the goal of estimating clinical outcome from tumor biopsies has been based on histomorphology of 2D tissue slices that represent a small fraction of collected samples. Its power derives from histologys 1) unbiased representation of cell types, 2) subcellular resolution that allows the characterization of health and disease states across cell types, and 3) multi-millimeter fields of view that allow assessment of tumor heterogeneity. Histologys dependence upon physical slices, however, limits assessment of 3-dimensional cellular volumes and tissue architecture. Here, we used propagation-based phase-contrast micro-CT (PBCT) to create 3D histological images of residual formalin-fixed, paraffin-embedded (FFPE) prostate needle biopsies. The resulting isotropic, grey-scale, 0.5 micron voxel matrices were used to explore the potential of for the 3D virtual histology to distinguish diagnostic categories including benign prostatic tissue and prostatic adenocarcinoma of Gleason patterns 3, 4, and 5. Maximum intensity projections of stacks of digital slices totaling 5 microns "slices" allowed the study of virtual sections corresponding to actual serial H&E-stained sections of tissue cut after micro-CT imaging. Like histology, our PBCT reconstructions allowed us to distinguish between non-infiltrative and undulating glands of benign prostatic tissue, infiltrative round glands of Gleason pattern 3, cribriform structures of Gleason pattern 4, and comedonecrosis of Gleason pattern 5. Unlike histology, micro-CT allowed us to further probe 3D tissue architecture in volumetric context. User-friendly exploration of sample volumes was achieved using a customized Neuroglancer multiplanar and 3D rendering interface. Sparsely trained cycleGAN produced plausible virtual H&E staining from the unstained micro-CT reconstructions. Unlike tissue-section based histology, micro-CT-based virtual histology yields nondestructive 3D characterization of cancer cell and tissue architecture, including glandular spaces, without the undersampling or cutting artifacts of histology. These findings demonstrate the feasibility of PBCT-based 3D virtual histology of prostate cancer and suggest the exploration of derived quantitative analyses of tumor properties for potential contributions to patient care.