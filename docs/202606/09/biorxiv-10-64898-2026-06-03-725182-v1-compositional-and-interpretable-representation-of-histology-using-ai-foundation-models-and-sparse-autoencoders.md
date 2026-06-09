---
title: Compositional and interpretable representation of histology using AI foundation models and sparse autoencoders
title_zh: 利用AI基础模型和稀疏自编码器实现组织学的可组合与可解释表示
authors: "Zhao, Z., Maliga, Z., Ogbonna, E. C., Talemi, S. R., Coy, S., Gagne, A., Lumamba, K., Solomon, I. H., Santagata, S., Steyn, A. J. C., Naidoo, T., Sorger, P. K."
date: 2026-06-06
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.03.725182v1.full.pdf"
tags: ["query:hmm"]
score: 8.0
evidence: 利用计算病理学基础模型和稀疏自编码器生成可解释组织学表征
tldr: "组织病理学中H&E染色图像分析依赖深度学习，但现有计算病理模型缺乏生物学可解释性，难以用于分子空间图谱研究。本文提出一种结合基础模型与稀疏自编码器的人机交互框架，自动分解模型嵌入并识别可解释的形态特征。在肺结核和肺癌中，该方法加速了专家解读并揭示了组织微环境，成功整合了2D/3D组织结构与分子空间数据。该工作显著提升了病理分析的透明度和可解释性。"
source: biorxiv
selection_source: fresh_fetch
motivation: 解决计算病理模型特征不可解释、难以融合分子空间图谱的问题。
method: 利用基础模型提取组织图像嵌入，经稀疏自编码器分解为可解释形态特征，结合人机交互迭代优化。
result: 在肺结核和肺癌中自动识别可解释组织特征，加速专家标注，实现与分子空间图谱的多维整合。
conclusion: 实现了组织学表示的可组合性与可解释性，为形态-分子空间联合分析提供新范式。
---

## 摘要
苏木精和伊红染色的组织切片光学显微镜已作为组织病理学的基础超过150年，并且在诊断和研究中仍然至关重要。高复合空间分析方法的发展能够在单细胞分辨率下测量蛋白质和RNA表达，增强但并未取代H&E成像，即使在研究领域也是如此。基于深度学习的计算病理学模型有望进一步提高H&E成像的价值，但以生物学术语解释这些模型仍然具有挑战性。因此，它们在空间分析研究中未得到广泛使用。在此，我们描述了一种人机交互的计算框架，该框架利用CPath基础模型和稀疏自编码器来分解FM嵌入，并自动识别H&E图像中的多样化、人类可解释的组织病理学特征。当FM-SAE建模应用于结核病和肺癌等肺部疾病时，人机交互增强并加速了专家解释。此外，得到的注释提供了一种形态学感知方法，将二维和三维中尺度组织结构与分子空间分析相结合。

## Abstract
Light microscopy of tissue sections stained with hematoxylin and eosin (H&E) has been the foundation of histopathology for over 150 years and remains essential for diagnosis and research. The development of high-plex spatial profiling approaches able to measure protein and RNA expression at single-cell resolution augments but does not replace H&E imaging, even in research. Computational pathology (CPath) models based on deep learning promise to further increase the value of H&E imaging but interpreting these models in biological terms remains challenging. As a result, they are not widely used in spatial profiling studies. Here we describe a human-in-the-loop computational framework that leverages CPath foundation models (FMs) and sparse autoencoders (SAEs) to decompose FM embeddings and automatically identify diverse, human-interpretable histopathology features in H&E images. When FM-SAE modeling was applied to pulmonary diseases such as tuberculosis and lung cancer, human-machine interaction augmented and accelerated expert interpretation. Moreover, the resulting annotations provide a morphology-aware approach to integrating 2D and 3D mesoscale tissue architectures with molecular spatial profiling.