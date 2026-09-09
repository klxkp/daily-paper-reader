---
title: "StyleProto: Style-Augmented Prototype Learning for Cross-Domain Few-Shot Object Detection"
title_zh: StyleProto：跨域小样本目标检测的风格增强原型学习
authors: "Xi Yang, Quantao Xie"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38160/42122"
tags: ["query:few-shot"]
score: 9.0
evidence: 跨域小样本检测中，用风格增强原型学习处理域偏移与有限标注共同导致的风格偏差和特征混淆
tldr: 跨域小样本目标检测同时面临域偏移和标注样本稀缺，少量支持样本既不能覆盖目标域风格多样性，又容易造成物体与背景及物体之间的特征混淆。为此StyleProto提出风格增强原型学习，从具有多样视觉风格的支持样本中构造风格感知原型，并通过空间加权与判别性融合进行精炼。该方法有效缓解了风格偏差与特征混淆带来的性能下降，为跨域小样本检测提供了更可靠的原型表达，可直接迁移到跨域小样本分类等低资源视觉任务。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38160/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 870, \"height\": 424, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38160/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1626, \"height\": 1005, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38160/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 864, \"height\": 330, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38160/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1821, \"height\": 580, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38160/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1515, \"height\": 1433, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38160/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 886, \"height\": 607, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38160/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 876, \"height\": 403, \"label\": \"Table\"}]"
motivation: 跨域小样本检测中，域偏移与标注稀缺会使支持样本风格偏差大、特征混淆明显，极大影响检测性能。
method: 构造风格感知原型并进行空间加权与判别融合，用支持样本的多样风格缓解风格偏差和特征混淆。
result: 在跨域小样本检测任务上有效降低风格偏差与特征混淆，提升少样本目标检测的稳定性与泛化性能。
conclusion: 风格增强原型的策略为跨域小样本视觉任务提供了一种可借鉴的克服双重困难的方法。
---

## Abstract
Cross-Domain Few-Shot Object Detection (CD-FSOD) faces significant challenges due to the dual issues of domain shift and limited labeled samples. One major challenge is style bias, caused by limited support samples that fail to represent the target domain’s style diversity. Another is feature confusion, which stems from distribution shifts and limited supervision, manifesting as both object-background ambiguity and object-object confusion. To address these challenges, we propose Style-Augmented Prototype Learning (StyleProto), which constructs style-aware prototypes from support samples with diverse visual styles, and refines them via spatial weighting and discriminative fusion. Specifically, our StyleProto consists of three components: (1) Style Generation Augmentation (SGA); (2) Semantic-Focused Prototype Construction (SPC); (3) Hierarchical Prototype Fusion Aggregator (HPFA). SGA synthesizes style-diverse yet semantically consistent training samples by recombining style statistics from the support set, thus improving robustness to unseen styles. SPC aggregates support features using spatial attention to highlight object semantics and suppress background noise, yielding cleaner and more distinctive class prototypes. HPFA leverages query-guided attention to integrate discriminative support features, enhancing prototype representations with richer class-specific details. Extensive experiments on multiple benchmarks demonstrate that StyleProto consistently outperforms existing state-of-the-art methods.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
跨域小样本检测中，用风格增强原型学习处理域偏移与有限标注共同导致的风格偏差和特征混淆。

### 2. 核心内容
跨域小样本目标检测同时面临域偏移和标注样本稀缺，少量支持样本既不能覆盖目标域风格多样性，又容易造成物体与背景及物体之间的特征混淆。为此StyleProto提出风格增强原型学习，从具有多样视觉风格的支持样本中构造风格感知原型，并通过空间加权与判别性融合进行精炼。该方法有效缓解了风格偏差与特征混淆带来的性能下降，为跨域小样本检测提供了更可靠的原型表达，可直接迁移到跨域小样本分类等低资源视觉任务。

### 3. 对应检索需求
What methods are proposed to handle domain shift in few shot classification tasks。

### 4. 来源与原文
- Source：AAAI-2026-Accepted
- OpenReview：[https://ojs.aaai.org/index.php/AAAI/article/view/38160](https://ojs.aaai.org/index.php/AAAI/article/view/38160)
