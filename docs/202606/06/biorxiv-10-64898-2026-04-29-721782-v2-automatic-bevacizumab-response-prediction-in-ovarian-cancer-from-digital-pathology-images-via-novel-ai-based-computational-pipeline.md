---
title: Automatic Bevacizumab Response Prediction in Ovarian Cancer from Digital Pathology Images via Novel AI-based Computational Pipeline
title_zh: 基于新型AI计算流程的数字病理图像自动预测卵巢癌贝伐珠单抗反应
authors: "Alsaiari, A., Turki, T., Taguchi, Y.-h."
date: 2026-05-29
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.29.721782v2.full.pdf"
tags: ["query:hmm"]
score: 8.0
evidence: 使用深度学习流水线从数字病理全切片图像预测药物反应
tldr: "卵巢癌药物反应预测对治疗至关重要，但传统病理诊断耗时且依赖经验。本文提出基于数字病理图像的计算流程：提取方向梯度直方图特征，经Fisher线性判别分析降维后，使用径向核支持向量回归预测贝伐珠单抗反应。该方法在AUC上比最佳Transformer模型ViT提升17%，比最佳深度学习模型MobileNetV2提升14.9%，展现了AI在妇科癌症研究中的优越性能。"
source: biorxiv
selection_source: fresh_fetch
motivation: 解决卵巢癌药物反应预测中人工病理诊断困难、耗时且准确率低的问题。
method: 采用方向梯度直方图特征提取、Fisher线性判别分析降维，结合径向核支持向量回归进行预测。
result: "所提SVRD+R方法AUC比ViT高17%，比MobileNetV2高14.9%。"
conclusion: 基于AI的计算流程能有效提升卵巢癌药物反应预测性能，优于主流深度学习模型。
---

## 摘要
卵巢癌是一种妇科癌症，如果发生转移且未及早发现，可能导致女性死亡。因此，准确预测卵巢癌的药物反应是必要的。妇科病理学家通过检查组织异常并为患者提供报告，但这一诊断过程（1）难以进行；（2）需要经验；（3）耗时。此外，现有工具并不完善。因此，我们提出了一种计算流程来改进卵巢癌药物反应的预测。首先，我们从癌症影像档案库下载了与卵巢癌对贝伐珠单抗反应相关的数字病理图像。我们对图像采用方向梯度直方图，构建特征向量，并使用Fisher线性判别分析通过降维改变数据表示。将降维后的数据用于回归分析，采用支持向量回归结合多种核函数，并计算ROC曲线下面积（AUC）。实验结果使用基于Transformer的模型（ViT和Swin）以及其他深度学习模型（VGG16、ResNet50、InceptionV3、MobileNetV2和EfficientNetB6）进行验证。我们的方法使用径向核函数（命名为SVRD+R）与性能最佳的基于Transformer的模型（ViT）相比，AUC性能提高了17%。同样，与最佳基于深度学习的模型（MobileNetV2）相比，AUC性能提高了14.9%。这些结果证明了可行性，表明通过所提出的基于AI的计算流程诱导的模型在研究与妇科癌症相关的预测问题时，可以带来优越的性能。

MSC 92B05；68T09

## Abstract
Ovarian cancer is a gynecological cancer, which, if metastasized and not detected early, can cause death among women. Therefore, accurate prediction of drug responses to ovarian cancer is needed. A gynecological pathologist inspects abnormality in tissues and provides a report for patients; however, this diagnostic process (1) is difficult to undertake; (2) requires experience; and (3) is time-consuming. Moreover, existing tools are imperfect. Hence, we present a computational pipeline to improve predictions of drug response pertaining to ovarian cancer. First, we downloaded digital pathology images pertaining to ovarian responses to bevacizumab from the Cancer Imaging Archive Repository. We employed a histogram of oriented gradients for images, constructed feature vectors, and used Fishers linear discriminant analysis to alter data representations through dimensionality reduction. This reduced-dimensionality data was used for regression analysis, employing support vector regression coupled with various kernels and calculating the area under the ROC curve (AUC). Experimental results were validated using transformerbased models (ViT and Swin) and other deep learning (DL) models (VGG16, ResNet50, InceptionV3, MobileNetV2, and EfficientNetB6). Our approach using a radial kernel (named SVRD+R) improved AUC performance by 17% compared to the best-performing transformer-based model (ViT). Likewise, AUC performance improved by 14.9% when compared against the best DL-based model (MobileNetV2). These results demonstrate feasibility, showing that induced models via the presented AI-based pipeline can lead to superior performance when investigating prediction problems pertaining to gynecologic cancer studies.

MSC92B05; 68T09