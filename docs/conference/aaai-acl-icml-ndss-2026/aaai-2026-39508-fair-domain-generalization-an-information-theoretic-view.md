---
title: "Fair Domain Generalization: An Information-Theoretic View"
title_zh: 公平域泛化：一种信息论视角
authors: "Tangzheng Lian, Guanyu Hu, Dimitrios Kollias, Xinyu Yang, Oya Celiktutan"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/39508/43469"
tags: ["query:few-shot"]
score: 7.0
evidence: 目标是让模型在未见目标域上同时降低期望风险与公平违规，实现免微调泛化
tldr: 现有域泛化方法往往只最小化未见目标域上的期望风险而忽视公平性，公平性方法又往往未建模域偏移。本文研究公平域泛化问题，目标是在未见目标域同时降低期望风险与公平性违规，并为多类别分类与多组敏感属性推导出互信息上界。该上界既给出理论刻画，也为训练跨域公平且鲁棒的分类器提供了可操作的优化依据。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39508/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 870, \"height\": 748, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39508/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 707, \"height\": 867, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39508/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1834, \"height\": 618, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-39508/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 817, \"height\": 427, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-39508/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 878, \"height\": 580, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-39508/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 863, \"height\": 168, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-39508/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 873, \"height\": 171, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-39508/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1842, \"height\": 204, \"label\": \"Table\"}]"
motivation: 域泛化方法通常忽略算法公平性，公平性方法又缺少对域偏移的建模，导致二者在未见域上难以兼得。
method: 提出公平域泛化框架，推导期望风险与公平违规的互信息上界，以同时约束域泛化性能与公平性。
result: 在多种多类分类与多组敏感属性设定下获得理论保证，为训练公平且鲁棒的域泛化模型提供依据。
conclusion: 从信息论角度为公平域泛化提供了可操作的优化目标和理论基础。
---

## Abstract
Domain generalization (DG) and algorithmic fairness are two key challenges in machine learning. However, most DG methods focus solely on minimizing expected risk in the unseen target domain, without considering algorithmic fairness. Conversely, fairness methods typically do not account for domain shifts, so the fairness achieved during training may not generalize to unseen test domains. In this work, we bridge these gaps by studying the problem of Fair Domain Generalization (FairDG), which aims to minimize both expected risk and fairness violations in unseen target domains. We derive novel mutual information-based upper bounds for expected risk and fairness violations in multi-class classification tasks with multi-group sensitive attributes. These bounds provide key insights for algorithm design from an information-theoretic perspective. Guided by these insights, we propose a practical method that solves the FairDG problem through Pareto optimization. Experiments on real-world vision and language datasets show that our method achieves superior utility–fairness trade-offs compared to existing approaches.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
目标是让模型在未见目标域上同时降低期望风险与公平违规，实现免微调泛化。

### 2. 核心内容
现有域泛化方法往往只最小化未见目标域上的期望风险而忽视公平性，公平性方法又往往未建模域偏移。本文研究公平域泛化问题，目标是在未见目标域同时降低期望风险与公平性违规，并为多类别分类与多组敏感属性推导出互信息上界。该上界既给出理论刻画，也为训练跨域公平且鲁棒的分类器提供了可操作的优化依据。

### 3. 对应检索需求
learning a model that can generalize to unseen domains without fine-tuning。

### 4. 来源与原文
- Source：AAAI-2026-Accepted
- OpenReview：[https://ojs.aaai.org/index.php/AAAI/article/view/39508](https://ojs.aaai.org/index.php/AAAI/article/view/39508)
