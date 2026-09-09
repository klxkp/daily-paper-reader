---
title: "Decompose and Attribute: Boosting Generalizable Open-Set Object Detection via Objectness Score"
title_zh: 分解与归因：利用目标性分数提升可泛化开集目标检测
authors: "Yuxuan Yuan, Lichen Wei, Luyao Tang, Chaoqi Chen, Zheyuan Cai, Yue Huang, Xinghao Ding"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38220/42182"
tags: ["query:few-shot"]
score: 6.0
evidence: 通过解耦域风格与语义结构，使检测模型更好泛化到未见域和新类别
tldr: 开集目标检测需识别已知类并定位未见类，真实场景常伴随域偏移，而源域表示将风格与语义纠缠，损害泛化。为此提出DOAT框架，利用小波特征分解分离域特有风格与语义结构，并引入目标性分数辅助检测，使模型在未见域和新类别上具有更强泛化性，为开集检测在分布外场景中的应用提供了新思路。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 现有开集检测常忽略域偏移，源训练表示中风格与语义纠缠，损害未见域与新类别泛化。
method: 提出联合分解-归因框架，用小波分解剥离域特有风格，引入目标性分数辅助开集检测。
result: 在域偏移与开放类别同时存在时，有效提升对未见域和未见类目标的检测能力。
conclusion: 表明将域风格与语义内容解耦是提升开集检测跨域泛化的重要方向。
---

## Abstract
Open-set object detection (OSOD) aims to recognize known object categories while localizing previously unseen instances. However, real-world scenarios often involve co-occurring domain shifts and novel object categories. Existing OSOD methods typically overlook domain shifts, relying on source-trained representations that entangle domain-specific style with semantic content, thereby hindering generalization to both unseen domains and novel categories. To address this challenge, we propose a unified framework, termed DecOmpose and ATtribute (DOAT), which disentangles domain-specific style from semantic structure, thereby facilitating generalizable object detection. DOAT employs wavelet-based feature decomposition to separate style information from high-frequency structural details, thus enabling an explicit separation of domain and category shifts. To account for domain shift, the low-frequency components are perturbed within a style subspace to simulate diverse domain appearances. For unknown object discovery, the high-frequency components are utilized to estimate objectness scores via an attribution mechanism that fuses wavelet energy with semantic distance to known-category prototypes. Extensive experiments on standard open-set benchmarks have demonstrated the superior generalization performance of DOAT.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
通过解耦域风格与语义结构，使检测模型更好泛化到未见域和新类别。

### 2. 核心内容
开集目标检测需识别已知类并定位未见类，真实场景常伴随域偏移，而源域表示将风格与语义纠缠，损害泛化。为此提出DOAT框架，利用小波特征分解分离域特有风格与语义结构，并引入目标性分数辅助检测，使模型在未见域和新类别上具有更强泛化性，为开集检测在分布外场景中的应用提供了新思路。

### 3. 对应检索需求
learning a model that can generalize to unseen domains without fine-tuning。

### 4. 来源与原文
- Source：AAAI-2026-Accepted
- OpenReview：[https://ojs.aaai.org/index.php/AAAI/article/view/38220](https://ojs.aaai.org/index.php/AAAI/article/view/38220)
