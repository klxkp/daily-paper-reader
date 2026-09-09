---
title: "Less Is Better: Sparse Instance Learning for Cross-Domain Few-Shot Object Detection"
title_zh: 少即是多：面向跨域少样本目标检测的稀疏实例学习
authors: "Yali Huang, Jie Mei, Ziyi Wu, Yiming Yang, Hongru Zhao, Mingyuan Jiu, Hichem Sahbi"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/37432/41394"
tags: ["query:few-shot"]
score: 8.0
evidence: 跨域少样本目标检测，针对域偏移和数据稀缺提出稀疏实例学习
tldr: 跨域少样本目标检测同时面对标注稀缺和源/目标域间的显著偏移，常见方法因此过拟合并使类原型含噪。该文提出SI-ViTO框架，通过双阶段稀疏模块对支撑集和查询集实例特征做稀疏化，以较少的表示获得更稳健的检测。稀疏化有助于抑制域噪声并保留关键类别信息，缓解了过拟合，为少量标注跨域检测提供了新思路。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37432/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 779, \"height\": 531, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37432/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1709, \"height\": 1088, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37432/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 576, \"height\": 419, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37432/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 860, \"height\": 516, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37432/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 878, \"height\": 353, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37432/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 801, \"height\": 1248, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37432/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1729, \"height\": 1352, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37432/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1449, \"height\": 314, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37432/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 869, \"height\": 137, \"label\": \"Table\"}]"
motivation: 跨域少样本检测中，少量样本和域偏移导致过拟合与噪声特征，难以形成判别性原型。
method: 提出SI-ViTO，在支撑集与查询集上执行双阶段实例特征稀疏，筛除域噪声，保留判别信息。
result: 实例稀疏能增强原型判别性并降低过拟合，在跨域少样本检测场景中取得更好结果。
conclusion: 证明在少样本条件下去除噪声可提升跨域目标检测能力，相关思路可迁移至其他跨域小样本任务。
---

## Abstract
Cross-Domain Few-Shot Object Detection (CD-FSOD) is an extremely challenging task due to the inherent data scarcity and substantial domain shift between the source and target domains. Existing methods often suffer from overfitting and noisy feature representations, which hinder the construction of discriminative class prototypes in the target domain. In this paper, we propose a novel framework with sparse instance learning (SI-ViTO) for CD-FSOD, which leverages instance sparsity to achieve a better detection with less representation. SI-ViTO adopts a dual-stage sparsity module, consisting of instance feature sparsity not only on the few-shot support images but also on the query images. This dual sparsity enables the model to effectively preserve salient foreground semantics and simultaneously to filter out redundant or noisy information. Furthermore, a new prototype calibration strategy is also used to dynamically refine the class prototypes with query instances to accelerate prototype adaptation. Extensive experimental results on CD-FSOD benchmarks show that SI-ViTO outperforms the state-of-the-art methods, demonstrating that less discriminative representations yield better cross-domain few-shot object detection performance than more abundant ones.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
跨域少样本目标检测，针对域偏移和数据稀缺提出稀疏实例学习。

### 2. 核心内容
跨域少样本目标检测同时面对标注稀缺和源/目标域间的显著偏移，常见方法因此过拟合并使类原型含噪。该文提出SI-ViTO框架，通过双阶段稀疏模块对支撑集和查询集实例特征做稀疏化，以较少的表示获得更稳健的检测。稀疏化有助于抑制域噪声并保留关键类别信息，缓解了过拟合，为少量标注跨域检测提供了新思路。

### 3. 对应检索需求
distribution mismatch between source and target domains causing performance degradation。

### 4. 来源与原文
- Source：AAAI-2026-Accepted
- OpenReview：[https://ojs.aaai.org/index.php/AAAI/article/view/37432](https://ojs.aaai.org/index.php/AAAI/article/view/37432)
