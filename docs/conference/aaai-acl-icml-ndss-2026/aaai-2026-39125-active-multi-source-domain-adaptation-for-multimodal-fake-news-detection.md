---
title: Active Multi-source Domain Adaptation for Multimodal Fake News Detection
title_zh: 面向多模态假新闻检测的主动多源域适应
authors: "Yanping Chen, Weijie Shi, Mengze Li, Yue Cui, Jiaming Li, Ruiyuan Zhang, Hao Chen, Hanghui Guo, Shimin Di, Ziyi Liu, Jia Zhu, Jiajie Xu"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/39125/43087"
tags: ["query:few-shot"]
score: 8.0
evidence: 面向多模态假新闻检测的多源域适应，主动标注少量目标样本以缓解分布偏移
tldr: 多模态假新闻检测常因新闻语义和欺骗模式在源域与目标域之间的偏移而性能明显下降，也常过度依赖人工标注。作者提出ADOSE主动多源域适应框架，主动标注一小部分目标样本，并基于精炼特征设计多专家分类器网络来分别应对域间变化。该方法在少量目标标注条件下提升了跨域检测性能，缓解了域偏移带来的性能退化，为多源假新闻检测提供了可行思路。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39125/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 268, \"height\": 190, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39125/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 207, \"height\": 191, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39125/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1739, \"height\": 997, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39125/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 851, \"height\": 438, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39125/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 790, \"height\": 369, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39125/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 704, \"height\": 584, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-39125/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 719, \"height\": 447, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-39125/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1648, \"height\": 811, \"label\": \"Table\"}]"
motivation: 新闻域多样性使跨域检测性能下降或严重依赖标注，现有方法无法同时解决域偏移和标注成本问题。
method: 提出ADOSE框架，结合主动标注少量目标样本与基于精炼特征的多专家分类器网络来适应多个源域。
result: 在少量目标样本标注下改善多模态假新闻检测的跨域性能，缓解语义与欺骗模式偏移问题。
conclusion: 主动标注与多专家分类相结合可降低标注成本并有效应对多源域偏移。
---

## Abstract
Multimodal fake news detection plays a crucial role in combating online misinformation. The inherent domain diversity of news in the real world has driven the development of cross-domain detection methods. However, these detection methods either suffer from significant performance degradation due to semantic and deception pattern shifts between the training (source) and test (target) domains or heavily rely on annotated labels. To address the problems, we propose ADOSE, an active multi-source domain adaptation framework for multimodal fake news detection which actively annotates a small subset of target samples to improve detection performance. Specifically, for domain shifts, we design a multi-expert classifier network based on refined features to comprehensively capture and adapt to the semantic space and deception patterns of news across different domains. To maximize adaptation performance with limited annotation cost, we propose a least-disagree uncertainty selector equipped with a diversity calculator for selecting the most informative samples. The selector leverages the uncertainty of inconsistent predictions before and after perturbations by multiple classifiers as an indicator of unfamiliar samples. It further incorporates diversity scores derived from multi-view features to ensure the chosen samples achieve maximal coverage of target domain features. The extensive experiments on multiple datasets show that ADOSE outperforms existing domain adaptation methods by 2.45% ~ 9.1%, indicating the superiority of our model.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
面向多模态假新闻检测的多源域适应，主动标注少量目标样本以缓解分布偏移。

### 2. 核心内容
多模态假新闻检测常因新闻语义和欺骗模式在源域与目标域之间的偏移而性能明显下降，也常过度依赖人工标注。作者提出ADOSE主动多源域适应框架，主动标注一小部分目标样本，并基于精炼特征设计多专家分类器网络来分别应对域间变化。该方法在少量目标标注条件下提升了跨域检测性能，缓解了域偏移带来的性能退化，为多源假新闻检测提供了可行思路。

### 3. 对应检索需求
techniques for adapting a model from a source domain to a target domain with different data distribution。

### 4. 来源与原文
- Source：AAAI-2026-Accepted
- OpenReview：[https://ojs.aaai.org/index.php/AAAI/article/view/39125](https://ojs.aaai.org/index.php/AAAI/article/view/39125)
