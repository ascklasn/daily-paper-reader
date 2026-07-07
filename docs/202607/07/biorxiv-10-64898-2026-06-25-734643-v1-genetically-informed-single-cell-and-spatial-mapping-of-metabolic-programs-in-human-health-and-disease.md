---
title: Genetically informed single-cell and spatial mapping of metabolic programs in human health and disease
title_zh: 遗传信息指导的单细胞与空间代谢程序图谱在人类健康与疾病中的应用
authors: "Xu, H., Huang, G., Zhang, L., Liu, W., Wu, Q., Chen, M., Zhao, D., Zhang, Y., Xu, A."
date: 2026-06-29
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.25.734643v1.full.pdf"
tags: ["query:spatialprot"]
score: 6.0
evidence: 利用遗传信息进行代谢程序的空间映射
tldr: 现有转录组代谢模型难以直接评估单个代谢物与细胞状态的关系，尤其细胞外信号代谢物。为此提出gmMAP框架，整合代谢物GWAS与单细胞/空间转录组，预测内源代谢过程并揭示外源代谢物与细胞功能状态关联。在人类肾脏发育、小鼠器官及24种正常组织验证，并发现泛癌代谢重编程和溃疡性结肠炎代谢重塑。gmMAP连接遗传代谢特征与细胞状态、组织空间及病理，提供多尺度代谢图谱。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有代谢模型无法直接关联单个代谢物与细胞状态，尤其外源信号代谢物，需新方法整合遗传信息与单细胞空间转录组。
method: 提出gmMAP框架，整合代谢物GWAS统计量与单细胞/空间转录组，并引入通量平衡模型评估全局代谢活动。
result: 在肾脏发育、多器官稳态及炎症、24种正常组织中验证准确性，揭示29种泛癌代谢重编程和溃疡性结肠炎基质代谢重塑。
conclusion: gmMAP能一致地连接遗传代谢特征与细胞状态、空间组织及病理，为代谢机制研究提供通用工具。
---

## 摘要
定义细胞类型特异的内源性代谢特征、细胞水平代谢状态的空间分布以及细胞对外源代谢物的反应，对于理解疾病机制至关重要。然而，现有基于转录组的代谢模型主要推断细胞内反应或通路水平的活动，因此无法直接评估单个代谢物水平与细胞状态之间的关联，尤其是对于作为信号分子在细胞外发挥作用而非作为代谢底物进入细胞的代谢物。为克服这一问题，我们引入了gmMAP（遗传信息指导的代谢物特征在单细胞与空间组织中的映射），该框架整合了代谢物GWAS汇总统计数据与单细胞和空间转录组，以细胞和空间分辨率绘制代谢程序。值得注意的是，gmMAP能够预测内源性代谢过程的激活，同时揭示外源代谢物与多种细胞功能状态之间的内在关联。为进一步捕捉细胞代谢网络的连通性，我们结合了基于约束的代谢通量模型来评估整体代谢活性。为了评估gmMAP的准确性和泛化能力，我们将该框架应用于涵盖人类发育、生理稳态、炎症和癌症的代表性生物学情境中。在人类肾脏发育过程中，gmMAP捕捉到了动态代谢程序，并通过配对的转录组和代谢组参考数据集进行了验证，支持其在代谢物识别和代谢流推断中的可靠性。在器官水平上，gmMAP重建了稳态和自身免疫性炎症条件下17个小鼠器官的空间代谢物分布模式，并将gmMAP进一步扩展到24种正常人类组织，生成了器官和细胞分辨率的多尺度代谢图谱。在疾病背景下，gmMAP揭示了29种泛癌细胞群中的代谢重编程，并识别了溃疡性结肠炎中外源代谢物与炎症相关基质代谢重塑之间的潜在联系。总之，gmMAP能够持续地将遗传信息指导的代谢物特征与细胞状态、空间组织结构和疾病病理联系起来。

## Abstract
Defining cell-type-specific endogenous metabolic features, the spatial distribution of cell-level metabolic states and cellular responses to exogenous metabolites is very important for understanding disease mechanisms. However, existing transcriptome-based metabolic models primarily infer intracellular reaction or pathway-level activities, and therefore cannot directly assess associations between individual metabolite levels and cellular states, particularly for metabolites that act extracellularly as signalling molecules rather than entering cells as metabolic substrates. To overcome this problem, we introduce the gmMAP (Genetically informed metabolite trait mapping across single-cell and spatial tissues), a framework that integrates metabolite GWAS summary statistics with single-cell and spatial transcriptomes to map metabolic programmes at cellular and spatial resolution. Notably, the gmMAP enables the prediction of endogenous metabolic process activation while also revealing intrinsic associations between exogenous metabolites and diverse cellular functional states. To further capture the connectivity of cellular metabolic networks, we incorporated a constraint-based metabolic flux model to evaluate global metabolic activity. To evaluate the accuracy and generalizability of gmMAP, we applied the framework across representative biological contexts spanning human development, physiological homeostasis, inflammation and cancer. In human kidney development, the gmMAP captured dynamic metabolic programmes, which was validated using paired transcriptomic and metabolomic reference datasets, supporting its reliability in metabolite identification and metabolic-flow inference. At the organ level, the gmMAP reconstructed spatial metabolite distribution patterns across 17 mouse organs under homeostatic and autoimmune inflammatory conditions, and further extension of gmMAP to 24 normal human tissues generated a multi-scale metabolic atlas at both organ and cellular resolutions. In disease settings, gmMAP revealed metabolic reprogramming across 29 pan-cancer cell populations, and identified potential links between exogenous metabolites and inflammation-associated stromal metabolic remodelling in ulcerative colitis. Together, gmMAP can consistently connect genetically informed metabolite traits with cell states, spatial tissue organization and disease pathology.