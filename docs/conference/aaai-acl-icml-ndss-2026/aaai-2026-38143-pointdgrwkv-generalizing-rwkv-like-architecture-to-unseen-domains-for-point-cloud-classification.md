---
title: "PointDGRWKV: Generalizing RWKV-like Architecture to Unseen Domains for Point Cloud Classification"
title_zh: PointDGRWKV：将RWKV类架构推广至未见域点云分类
authors: "Hao Yang, Qianyu Zhou, Haijia Sun, Xiangtai Li, Xuequan Lu, Lizhuang Ma, Shuicheng YAN"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38143/42105"
tags: ["query:few-shot"]
score: 7.0
evidence: 域泛化用于点云分类，以RWKV架构泛化到未见域但无少样本设置
tldr: 为让点云分类模型泛化到未见域，已有域泛化工作多基于卷积、Transformer或Mamba，但各有感受野、算力或长程依赖局限。该文首次探索RWKV结构在点云域泛化中的潜力，指出固定方向token shift会引入域偏差，阻碍泛化。调整架构后模型无需对目标域微调即可用于新的点云域。实验表明这种线性复杂度全局建模架构有效，但它不涉及小样本分类，与核心需求只在域泛化目标上有一定关联。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 域泛化点云分类现有架构难兼顾全局感受野、线性复杂度与有效长程建模，RWKV直接迁移会因固定方向token shift产生偏差。
method: 设计适配点云域泛化的RWKV式架构，修正固定方向token shift带来的不可泛化问题。
result: 架构改进使点云模型可以无需目标域微调而在未见域上获得更好精度。
conclusion: 为域泛化点云分类提供了高效架构选择，但没有结合少样本场景，适用范围仍需调整。
---

## Abstract
Domain Generalization (DG) has been recently explored to enhance the generalizability of Point Cloud Classification (PCC) models toward unseen domains. Prior works are based on convolutional networks, Transformer or Mamba architectures, either suffering from limited receptive fields or high computational cost, or insufficient long-range dependency modeling. RWKV, as an emerging architecture, possesses superior linear complexity, global receptive fields, and long-range dependency. In this paper, we present the first work that studies the generalizability of RWKV models in DG PCC. We find that directly applying RWKV to DG PCC encounters two significant challenges: RWKV's fixed direction token shift methods, like Q-Shift, introduce spatial distortions when applied to unstructured point clouds, weakening local geometric modeling and reducing robustness. In addition, the Bi-WKV attention in RWKV amplifies slight cross-domain differences in key distributions through exponential weighting, leading to attention shifts and degraded generalization. To this end, we propose PointDGRWKV, the first RWKV-based framework tailored for DG PCC. It introduces two core modules to enhance spatial modeling and cross-domain robustness, while maintaining RWKV's linear efficiency. In particular, we present Adaptive Geometric Token Shift to model local neighborhood structures to improve geometric context awareness. In addition, Cross-Domain key feature Distribution Alignment is designed to mitigate attention drift by aligning key feature distributions across domains. Extensive experiments on multiple benchmarks demonstrate that PointDGRWKV achieves state-of-the-art performance on DG PCC.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
域泛化用于点云分类，以RWKV架构泛化到未见域但无少样本设置。

### 2. 核心内容
为让点云分类模型泛化到未见域，已有域泛化工作多基于卷积、Transformer或Mamba，但各有感受野、算力或长程依赖局限。该文首次探索RWKV结构在点云域泛化中的潜力，指出固定方向token shift会引入域偏差，阻碍泛化。调整架构后模型无需对目标域微调即可用于新的点云域。实验表明这种线性复杂度全局建模架构有效，但它不涉及小样本分类，与核心需求只在域泛化目标上有一定关联。

### 3. 对应检索需求
learning a model that can generalize to unseen domains without fine-tuning。

### 4. 来源与原文
- Source：AAAI-2026-Accepted
- OpenReview：[https://ojs.aaai.org/index.php/AAAI/article/view/38143](https://ojs.aaai.org/index.php/AAAI/article/view/38143)
