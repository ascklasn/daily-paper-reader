---
title: Automatic Bevacizumab Response Prediction in Ovarian Cancer from Digital Pathology Images via Novel AI-based Computational Pipeline
title_zh: 基于新型人工智能计算流程的数字病理图像自动预测卵巢癌贝伐珠单抗反应
authors: "Alsaiari, A., Turki, T., Taguchi, Y.-h."
date: 2026-05-29
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.29.721782v2.full.pdf"
tags: ["query:hmm"]
score: 7.0
evidence: 利用数字病理图像进行卵巢癌药物反应预测
tldr: "卵巢癌药物反应预测对治疗至关重要，但现有诊断方法困难且耗时。本文提出基于HOG特征、Fisher线性判别降维和SVR回归的计算管道，用于预测贝伐珠单抗反应。在病理图像数据上，径向核SVR比最佳Transformer模型ViT提升17% AUC，比最佳CNN模型MobileNetV2提升14.9%。该方法显著提升了妇科癌症药物反应预测性能。"
source: biorxiv
selection_source: fresh_fetch
motivation: 解决卵巢癌药物反应预测中传统病理诊断困难、耗时且现有工具不完善的问题。
method: 提取病理图像HOG特征，经Fisher线性判别降维后，采用支持向量回归（SVR）并搭配不同核函数进行预测。
result: "径向核SVR（SVRD+R）的AUC比最佳Transformer模型ViT提升17%，比最佳深度学习模型MobileNetV2提升14.9%。"
conclusion: 所提AI计算管道在预测妇科癌症药物反应任务上可行性高且效果优越。
---

## 摘要
卵巢癌是一种妇科癌症，如果发生转移且未早期发现，可能导致女性死亡。因此，准确预测卵巢癌的药物反应是必要的。妇科病理学家通过检查组织异常并为患者提供报告；然而，这一诊断过程（1）难以进行；（2）需要经验；以及（3）耗时。此外，现有工具不完善。因此，我们提出了一种计算流程，以改进对卵巢癌药物反应的预测。首先，我们从癌症影像档案库下载了与卵巢癌对贝伐珠单抗反应相关的数字病理图像。我们对图像采用方向梯度直方图，构建特征向量，并使用Fisher线性判别分析通过降维改变数据表示。将降维后的数据用于回归分析，采用支持向量回归结合多种核函数，并计算ROC曲线下面积（AUC）。实验结果通过基于Transformer的模型（ViT和Swin）以及其他深度学习模型（VGG16、ResNet50、InceptionV3、MobileNetV2和EfficientNetB6）进行验证。我们使用径向核的方法（命名为SVRD+R）相比表现最佳的基于Transformer的模型（ViT）将AUC性能提高了17%。同样，与基于深度学习的最佳模型（MobileNetV2）相比，AUC性能提高了14.9%。这些结果证明了可行性，表明通过所提出的人工智能计算流程诱导的模型在研究与妇科癌症相关的预测问题时可以带来优越的性能。

## Abstract
Ovarian cancer is a gynecological cancer, which, if metastasized and not detected early, can cause death among women. Therefore, accurate prediction of drug responses to ovarian cancer is needed. A gynecological pathologist inspects abnormality in tissues and provides a report for patients; however, this diagnostic process (1) is difficult to undertake; (2) requires experience; and (3) is time-consuming. Moreover, existing tools are imperfect. Hence, we present a computational pipeline to improve predictions of drug response pertaining to ovarian cancer. First, we downloaded digital pathology images pertaining to ovarian responses to bevacizumab from the Cancer Imaging Archive Repository. We employed a histogram of oriented gradients for images, constructed feature vectors, and used Fishers linear discriminant analysis to alter data representations through dimensionality reduction. This reduced-dimensionality data was used for regression analysis, employing support vector regression coupled with various kernels and calculating the area under the ROC curve (AUC). Experimental results were validated using transformerbased models (ViT and Swin) and other deep learning (DL) models (VGG16, ResNet50, InceptionV3, MobileNetV2, and EfficientNetB6). Our approach using a radial kernel (named SVRD+R) improved AUC performance by 17% compared to the best-performing transformer-based model (ViT). Likewise, AUC performance improved by 14.9% when compared against the best DL-based model (MobileNetV2). These results demonstrate feasibility, showing that induced models via the presented AI-based pipeline can lead to superior performance when investigating prediction problems pertaining to gynecologic cancer studies.

MSC92B05; 68T09