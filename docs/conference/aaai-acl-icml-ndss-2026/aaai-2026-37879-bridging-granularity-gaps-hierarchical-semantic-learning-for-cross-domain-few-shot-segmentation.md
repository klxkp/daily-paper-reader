---
title: "Bridging Granularity Gaps: Hierarchical Semantic Learning for Cross-domain Few-shot Segmentation"
title_zh: 弥合粒度差距：面向跨域小样本分割的层次化语义学习
authors: "Sujun Sun, Haowen Gu, Cheng Xie, Yanxu Ren, Mingwu Ren, Haofeng Zhang"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/37879/41841"
tags: ["query:few-shot"]
score: 8.0
evidence: 明确面向跨域小样本任务，处理源/目标域分布差异与少量标注，任务为分割而非分类，但主题高度重合
tldr: 跨域小样本分割旨在仅用少量标注样本分割目标域未见类别，但现有方法只注重风格差异，忽略分割粒度差异，导致语义判别力不足。本文提出层次化语义学习框架，引入双风格随机化模块与层次化语义挖掘模块，同时弥合风格差距与语义粒度差距，增强目标域新类别的特征可分性。实验证明了该框架在跨域小样本分割任务上的有效性。该工作为跨域小样本学习提供了兼顾粒度感知的新视角，对分类任务具有借鉴意义。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37879/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 827, \"height\": 597, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37879/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1760, \"height\": 1019, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37879/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 857, \"height\": 562, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37879/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 858, \"height\": 583, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37879/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1842, \"height\": 761, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37879/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 714, \"height\": 294, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37879/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 812, \"height\": 256, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37879/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 865, \"height\": 217, \"label\": \"Table\"}]"
motivation: 现有跨域小样本分割方法多只关注领域风格差异，忽略语义粒度差异，导致目标域新类别特征的判别性不足。
method: 提出层次化语义学习框架，采用双风格随机化和层次化语义挖掘，同时弥合风格差距与粒度差距。
result: 在跨域小样本分割基准上验证了该框架能有效提升目标域新类别的分割性能与语义判别性。
conclusion: 同时刻画风格与语义粒度差异是跨域小样本分割改进的关键，相关思想亦可迁移至跨域小样本分类。
---

## Abstract
Cross-domain Few-shot Segmentation (CD-FSS) aims to segment novel classes from target domains that are not involved in training and have significantly different data distributions from the source domain, using only a few annotated samples, and recent years have witnessed significant progress on this task. However, existing CD-FSS methods primarily focus on style gaps between source and target domains while ignoring segmentation granularity gaps, resulting in insufficient semantic discriminability for novel classes in target domains. Therefore, we propose a Hierarchical Semantic Learning (HSL) framework to tackle this problem. Specifically, we introduce a Dual Style Randomization (DSR) module and a Hierarchical Semantic Mining (HSM) module to learn hierarchical semantic features, thereby enhancing the model's ability to recognize semantics at varying granularities. DSR simulates target domain data with diverse foreground-background style differences and overall style variations through foreground and global style randomization respectively, while HSM leverages multi-scale superpixels to guide the model to mine intra-class consistency and inter-class distinction at different granularities. Additionally, we also propose a Prototype Confidence-modulated Thresholding (PCMT) module to mitigate segmentation ambiguity when foreground and background are excessively similar. Extensive experiments are conducted on four popular target domain datasets, and the results demonstrate that our method achieves state-of-the-art performance.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
明确面向跨域小样本任务，处理源/目标域分布差异与少量标注，任务为分割而非分类，但主题高度重合。

### 2. 核心内容
跨域小样本分割旨在仅用少量标注样本分割目标域未见类别，但现有方法只注重风格差异，忽略分割粒度差异，导致语义判别力不足。本文提出层次化语义学习框架，引入双风格随机化模块与层次化语义挖掘模块，同时弥合风格差距与语义粒度差距，增强目标域新类别的特征可分性。实验证明了该框架在跨域小样本分割任务上的有效性。该工作为跨域小样本学习提供了兼顾粒度感知的新视角，对分类任务具有借鉴意义。

### 3. 对应检索需求
Papers central to 查找跨域小样本分类相关论文, especially work that connects or combines: classification task where training and test domains differ and only a few labeled samples are available; distribution mismatch between source and target domains causing performance degradation; techniques for adapting a model from a source domain to a target domain with different data distribution; learning a model that can generalize to unseen domains without fine-tuning; What methods are proposed to handle domain shift in few shot classification tasks; How can meta learning be applied to cross domain few shot classification.

### 4. 来源与原文
- Source：AAAI-2026-Accepted
- OpenReview：[https://ojs.aaai.org/index.php/AAAI/article/view/37879](https://ojs.aaai.org/index.php/AAAI/article/view/37879)
