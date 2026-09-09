---
title: Unified Interaction Consistency Learning for Single-Source Domain-Generalized Object Detection in Urban Scene
title_zh: 面向城市场景单源域泛化目标检测的统一交互一致性学习
authors: "Peng Zhang, Xiang Yuan, Gong Cheng"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38263/42225"
tags: ["query:few-shot"]
score: 8.0
evidence: 单源域泛化目标检测，学习类内域不变表示以应对训练与部署环境的分布差异
tldr: 神经网络目标检测在白天晴好等训练条件与夜间雨天等现实部署场景之间因分布差异产生定位不精确和分类错误。论文提出统一交互一致性学习（UICL）框架，通过跨域交互机制在原始分支与增强分支之间交换区域提议，丰富实例级特征多样性，从而学习类内域不变表示。该方法面向单源域泛化，无需目标域标注，即可提升模型对夜间、雨雾等未见视觉条件下目标检测的鲁棒性，为城市场景中的可靠部署提供了有效方案。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38263/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 876, \"height\": 539, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38263/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1844, \"height\": 598, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38263/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 880, \"height\": 422, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38263/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1830, \"height\": 827, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38263/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1846, \"height\": 665, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38263/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 836, \"height\": 412, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38263/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 877, \"height\": 578, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38263/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 875, \"height\": 516, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38263/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1846, \"height\": 255, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38263/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 873, \"height\": 409, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38263/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 886, \"height\": 138, \"label\": \"Table\"}]"
motivation: 训练条件如白天晴与部署条件如夜间雨之间的分布差异会导致目标定位和分类错误，域泛化困难。
method: 提出统一交互一致性学习框架，跨域交换原始与增强分支的区域提议，学习类内域不变的实例级表示。
result: 在未见天气或场景条件下改善目标检测的定位与分类，增强单源域泛化能力。
conclusion: 以交互一致性约束域不变表示，可有效解决单源域泛化目标检测中的分布偏移问题。
---

## Abstract
Domain generalization remains a critical challenge for deploying neural networks, particularly in out-of-distribution object detection. The distributional discrepancy between training (e.g., daytime-sunny) and the realistic condition (e.g., night-rainy) inevitably produces imprecise localization and wrong classification. To address these issues, we propose a unified interaction consistency learning (UICL) framework, a novel single-source domain-generalized method designed to learn intra-class domain-invariant representations. Specifically, we put forth a cross-domain interaction mechanism to exchange region proposals between original and augmented pipelines, enriching the diversity of instance-level representations. Building upon this, we propose prediction-guided consistency learning to unify the interaction mechanism and harmonize the cross-domain representations, contributing to a discriminative prediction distribution under domain shift. In addition, we devise a cyclic interaction resilient detection strategy, which mitigates inaccurate predictions suffering from partial occlusion and ambiguous boundaries among different domains. Extensive experiments evidence that UICL significantly improves the robustness of detectors over several target domains, achieving state-of-the-art generalization performance on the diverse weather benchmark.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
单源域泛化目标检测，学习类内域不变表示以应对训练与部署环境的分布差异。

### 2. 核心内容
神经网络目标检测在白天晴好等训练条件与夜间雨天等现实部署场景之间因分布差异产生定位不精确和分类错误。论文提出统一交互一致性学习（UICL）框架，通过跨域交互机制在原始分支与增强分支之间交换区域提议，丰富实例级特征多样性，从而学习类内域不变表示。该方法面向单源域泛化，无需目标域标注，即可提升模型对夜间、雨雾等未见视觉条件下目标检测的鲁棒性，为城市场景中的可靠部署提供了有效方案。

### 3. 对应检索需求
learning a model that can generalize to unseen domains without fine-tuning。

### 4. 来源与原文
- Source：AAAI-2026-Accepted
- OpenReview：[https://ojs.aaai.org/index.php/AAAI/article/view/38263](https://ojs.aaai.org/index.php/AAAI/article/view/38263)
