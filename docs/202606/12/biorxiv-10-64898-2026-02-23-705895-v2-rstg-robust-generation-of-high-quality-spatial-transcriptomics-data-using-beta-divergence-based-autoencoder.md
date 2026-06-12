---
title: "RSTG: Robust Generation of High Quality Spatial Transcriptomics Data using Beta Divergence Based AutoEncoder"
title_zh: RSTG：基于Beta散度自编码器的高质量空间转录组数据鲁棒生成
authors: "Halder, A., Ghosh, A., Bandyopadhyay, S."
date: 2026-06-12
pdf: "https://www.biorxiv.org/content/10.64898/2026.02.23.705895v2.full.pdf"
tags: ["query:spatialprot"]
score: 7.0
evidence: 鲁棒地生成高质量空间转录组数据
tldr: 空间转录组数据分析面临数据不足和噪声干扰的挑战，现有生成模型对异常值敏感。本文提出RSTG，采用β-ELBO损失的自动编码器，通过变分推断学习数据鲁棒分布。在MERFISH等数据集上，RSTG在细胞位置恢复和噪声污染下均表现优异。该方法实现了高质量且稳定的数据生成，为后续分析提供了可靠基础。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有空间转录组生成模型在噪声（如异常值）环境下生成质量差，缺乏鲁棒性。
method: 提出RSTG，基于β散度的变分自动编码器，使用β-ELBO损失进行鲁棒密度估计。
result: 在多个数据集上，RSTG在细胞位置恢复和抗噪声（白噪声、批次效应等）任务中性能优于现有方法。
conclusion: RSTG能够鲁棒生成高质量空间转录组数据，适用于含噪声的真实场景。
---

## 摘要
空间转录组数据分析的关键挑战之一是缺乏足够的数据来训练模型。为了解决这一不足，研究人员开发了多种生成模型，在受控环境中生成合成空间转录组样本。然而，这些模型在存在噪声（如异常值）时往往无法即用生成。为应对这一挑战，我们提出了RSTG（鲁棒空间转录组生成器），一种采用β-ELBO损失的自编码器，用于生成逼真且高质量的空间转录组序列。我们的模型通过变分推断近似数据的潜在分布，从而揭示其内在结构，实现更具可解释性和鲁棒性的密度估计。我们验证了RSTG在多个任务上的有效性，包括恢复二维空间和位置域中的细胞位置。我们的方法在多个数据集（包括使用MERFISH、MERSCOPE和Visium技术生成的脑和肝样本）上，定性和定量地展示了改进的性能。我们进一步通过用异常（如白噪声、批次效应和缺失值）污染部分数据，以及在一个真实退化的样本上，展示了RSTG对异常值的鲁棒性。结果表明，即使在训练数据被污染的情况下，我们的提议在各种实验设置中以及与现有方法相比，仍能保持高质量和稳定性。

## Abstract
One of the key challenges in spatial transcriptomics data analysis is the lack of sufficient data to train models. To address this shortcoming, multiple generative models have been developed to generate synthetic spatial transcriptomics samples in a controlled environment. However, these models often fail in out-of-the-box generation in the presence of noise (such as outliers). To tackle this challenge, we propose RSTG (Robust Spatial Transcriptomic Generator), an autoencoder that incorporates the {beta}-ELBO loss, to generate realistic and high-quality spatial transcriptomic sequences. Our model uncovers data' intrinsic structure by approximating its underlying distribution through variational inference, resulting in more interpretable and robust density estimation. We validate the effectiveness of RSTG across multiple tasks, including the recovery of cellular positions in both the 2D spatial and location domains. Our method shows improved performance, both qualitatively and quantitatively, across multiple datasets, including brain and liver samples generated using MERFISH, MERSCOPE, and Visium technologies. We further illustrate the robustness of RSTG to outliers by contaminating a portion of the data with anomalies (such as white noise, batch effects, and dropouts) as well as on a real-life degraded sample. The results show that our proposal maintains high quality and stability even when the training data are contaminated, across a variety of experimental settings and in comparison with existing approaches.