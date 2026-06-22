---
title: "Optics-free reconstruction of shapes, images and volumes with DNA barcode proximity graphs"
title_zh: 基于DNA条形码邻近图谱的无光学重建形状、图像与体积
authors: "Liao, H., Kottapalli, S., Huang, Y., Chaw, M., Gehring, J., Waltner, O., Phung-Rojas, M., Daza, R. M., Matsen, F. A., Trapnell, C., Shendure, J., Srivatsan, S. R."
date: 2026-06-15
pdf: "https://www.biorxiv.org/content/10.1101/2024.08.06.606834v3.full.pdf"
tags: ["query:spatialprot"]
score: 7.0
evidence: 通过DNA条形码邻近图实现空间基因组学
tldr: 现有测序空间基因组学方法依赖坐标标记表面，制备耗时且限制面积。本文提出SCOPE，一种无光学方法，利用DNA条形码珠间的扩散和连接生成嵌合分子，通过体外测序重建相对位置。成功重建2D形状（如Nike logo）、2D图像（Snellen视力表）和3D体积（玩具熊等模具），分辨率由测序深度、珠尺寸和扩散动力学决定。该方法自动化、无仪器依赖，为空间重建提供可扩展新途径。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有测序空间方法需坐标标记表面，制备复杂且面积受限，亟需简化、无光学的替代方案。
method: SCOPE利用扩散的“发送”寡核苷酸与固定的“接收”寡核苷酸生成嵌合分子，经体外测序构建邻近图，反推空间位置。
result: 在包含104-106个微米级珠的多种2D形状、图像和3D体积上实现自动重建，分辨率由测序深度等参数决定。
conclusion: 无需光学设备，空间重建自动化且可扩展至大视场和体积，为空间基因组学提供新范式。
---

## 摘要
空间基因组学技术包括成像和测序方法。基于测序的空间方法通常需要涂有坐标相关DNA条形码的表面，但这些条形码与空间坐标的物理配准具有挑战性，需要高密度打印寡核苷酸或对随机沉积的携带DNA条形码的珠子进行原位测序/探针检测。因此，基于测序的空间基因组学方法可用的表面积受到打印或解码坐标标记表面所需的时间、人力、成本和仪器的限制。为了解决这一挑战，我们开发了SCOPE（通过寡核苷酸邻近编码的空间重建），一种受DNA显微镜启发的无光学方法。通过SCOPE，二维形状、二维图像或三维体积内DNA条形码珠子的相对位置可以从扩散的“发送器”和固定的“接收器”寡核苷酸形成的嵌合分子的离体测序中推断出来。为了展示该方法的潜力，我们应用SCOPE重建了由10^4-10^6个20-100微米DNA条形码珠子定义的二维形状、二维图像或三维体积，包括类似耐克标志的不对称“swoosh”（44平方毫米）、“彩色”斯内伦视力表（704平方毫米）以及泰迪熊、星星、蝴蝶或立体字母的三维模具表面拓扑（75-100立方毫米）。每个生成的“DNA条形码邻近图谱”都以自动化方式计算重建，跨越视场，分辨率由测序深度、珠子大小和扩散动力学决定，而非微阵列或显微镜仪器时间。由于真实形状已知，这些数据集可能特别有助于这一新兴领域进一步开发计算算法。

## Abstract
Spatial genomics technologies include imaging- and sequencing-based methods. Sequencing-based spatial methods typically require surfaces coated with coordinate-associated DNA barcodes, but the physical registration of these barcodes to spatial coordinates is challenging, necessitating either high density printing of oligonucleotides or in situ sequencing/probing of randomly deposited, DNA-barcode-bearing beads. As a consequence, the surface areas available to sequencing-based spatial genomic methods are constrained by the time, labor, cost and instrumentation required to either print or decode a coordinate-tagged surface. To address this challenge, we developed SCOPE (Spatial reConstruction via Oligonucleotide Proximity Encoding), an optics-free, DNA microscopy-inspired method. With SCOPE, the relative positions of DNA-barcoded beads within a 2D shape, 2D image or 3D volume are inferred from the ex situ sequencing of chimeric molecules formed from diffusing "sender" and tethered "receiver" oligonucleotides. To demonstrate the potential of this approach, we applied SCOPE to reconstruct 2D shapes, 2D images or 3D volumes defined by 104-106 x 20-100 {micro}m DNA barcoded beads, including an asymmetric "swoosh" resembling the Nike logo (44 mm2), a "color" Snellen eye chart (704 mm2) and the surface topology of 3D molds of a teddy bear, star, butterfly or block letter (75-100 mm3). Each of the resulting "DNA barcode proximity graphs" was computationally reconstructed in an automated fashion, across fields of view and at resolutions that were determined by sequencing depth, bead size and diffusion kinetics, rather than by microarray or microscope instrument time. Because the ground truth shapes are known, these datasets may be particularly useful for the further development of computational algorithms by this nascent field.