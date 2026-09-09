---
title: Divide-and-Conquer Decoupled Network for Cross-Domain Few-Shot Segmentation
title_zh: 面向跨域少样本分割的分治解耦网络
authors: "Runmin Cong, Anpeng Wang, Bin Wan, Cong Zhang, Xiaofei Zhou, Wei Zhang"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/37338/41300"
tags: ["query:few-shot"]
score: 8.0
evidence: 跨域少样本分割，解耦类别相关与域相关特征以应对少量标注下的域偏移
tldr: 跨域少样本分割既要识别新类别，又要在极少标注下适应未见域，而编码器特征常纠缠域相关与类别相关信息。针对该问题，提出分而治之解耦网络DCDNet，其中对抗-对比特征分解模块把骨干特征分解为类别相关的私有表示和域相关的共享表示。该解耦能降低域偏移对特征可迁移性的干扰，并支持在新域快速适应。结果表明其能改善跨域少样本分割性能，为跨域小样本特征学习提供一般性思路。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37338/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 881, \"height\": 420, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37338/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1846, \"height\": 870, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37338/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 856, \"height\": 588, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37338/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1823, \"height\": 708, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37338/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 721, \"height\": 245, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37338/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 720, \"height\": 206, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37338/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 719, \"height\": 281, \"label\": \"Table\"}]"
motivation: 编码器特征将域相关信息和类别信息纠缠，限制了向未见过域泛化和快速适应的能力。
method: 提出DCDNet，利用对抗-对比特征分解将特征拆为类别相关私有表示和域相关共享表示。
result: 解耦后的特征缓解域偏移影响，在少量标注下提升了未见域的适应效果与分割性能。
conclusion: 对抗与对比结合的解耦可提高跨域小样本特征的可迁移性，并适用于其他识别任务。
---

## Abstract
Cross-domain few-shot segmentation (CD-FSS) aims to tackle the dual challenge of recognizing novel classes and adapting to unseen domains with limited annotations. However, encoder features often entangle domain-relevant and category-relevant information, limiting both generalization and rapid adaptation to new domains. To address this issue, we propose a Divide-and-Conquer Decoupled Network (DCDNet). In the training stage, to tackle feature entanglement that impedes cross-domain generalization and rapid adaptation, we propose the Adversarial-Contrastive Feature Decomposition (ACFD) module. It decouples backbone features into category-relevant private and domain-relevant shared representations via contrastive learning and adversarial learning. Then, to mitigate the potential degradation caused by the disentanglement, the Matrix-Guided Dynamic Fusion (MGDF) module adaptively integrates base, shared, and private features under spatial guidance, maintaining structural coherence. In addition, in the fine-tuning stage, to enhanced model generalization, the Cross-Adaptive Modulation (CAM) module is placed before the MGDF, where shared features guide private features via modulation ensuring effective integration of domain-relevant information. Extensive experiments on four challenging datasets show that DCDNet outperforms existing CD-FSS methods, setting a new state-of-the-art for cross-domain generalization and few-shot adaptation.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
跨域少样本分割，解耦类别相关与域相关特征以应对少量标注下的域偏移。

### 2. 核心内容
跨域少样本分割既要识别新类别，又要在极少标注下适应未见域，而编码器特征常纠缠域相关与类别相关信息。针对该问题，提出分而治之解耦网络DCDNet，其中对抗-对比特征分解模块把骨干特征分解为类别相关的私有表示和域相关的共享表示。该解耦能降低域偏移对特征可迁移性的干扰，并支持在新域快速适应。结果表明其能改善跨域少样本分割性能，为跨域小样本特征学习提供一般性思路。

### 3. 对应检索需求
distribution mismatch between source and target domains causing performance degradation。

### 4. 来源与原文
- Source：AAAI-2026-Accepted
- OpenReview：[https://ojs.aaai.org/index.php/AAAI/article/view/37338](https://ojs.aaai.org/index.php/AAAI/article/view/37338)
