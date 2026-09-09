---
title: "Simulating Distribution Dynamics: Liquid Temporal Feature Evolution for Single-Domain Generalized Object Detection"
title_zh: 模拟分布动态：面向单域广义目标检测的液态时序特征演化
authors: "Zihao Zhang, Yang Li, Aming Wu, Yahong Han"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38306/42268"
tags: ["query:few-shot"]
score: 7.0
evidence: 在单一源域训练并面向多个未知目标域检测，不接触目标域数据即可获得跨域泛化能力
tldr: 面向单源域广义目标检测的方法通常用离散数据增强或静态扰动来扩充数据多样性，却难以刻画真实场景中天气、光照导致的连续渐变的域偏移。为此本文提出液态时序特征演化机制，让模型模拟特征分布随时间的连续变化，从而捕捉更细粒度的跨域差异。该方法不依赖目标域数据或微调，可提升检测器对多个未知域的泛化能力，为动态域偏移建模提供了新思路。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 单源域广义目标检测需迁移至多个未知域，但离散增广与静态扰动无法刻画真实世界域偏移的连续渐变过程。
method: 通过液态时序特征演化模拟特征分布的连续变化，使模型感知更细粒度的跨域分布差异。
result: 在未知目标域检测场景中，检测器可捕获动态跨域差异从而获得更强的免微调泛化能力。
conclusion: 揭示建模域偏移的连续动态比离散扰动更贴近现实，为免微调跨域泛化提供了新策略。
---

## Abstract
In this paper, we focus on Single-Domain Generalized Object Detection (Single-DGOD), aiming to transfer a detector trained on one source domain to multiple unknown domains.
Existing methods for Single-DGOD typically rely on discrete data augmentation or static perturbation methods to expand data diversity, thereby mitigating the lack of access to target domain data. However, in real-world scenarios such as changes in weather or lighting conditions, domain shifts often occur continuously and gradually. 
Discrete augmentations and static perturbations fail to effectively capture the dynamic variation of feature distributions, thereby limiting the model's ability to perceive fine-grained cross-domain differences.
To this end, we propose a new method, i.e., Liquid Temporal Feature Evolution, which simulates the progressive evolution of features from the source domain to simulated latent distributions by incorporating temporal modeling and liquid neural network–driven parameter adjustment. Specifically, we introduce controllable Gaussian noise injection and multi-scale Gaussian blurring to simulate initial feature perturbations, followed by temporal modeling and a liquid parameter adjustment mechanism to generate adaptive modulation parameters, enabling a smooth and continuous adaptation across domains.
By capturing progressive cross-domain feature evolution and dynamically regulating adaptation paths, our method bridges the source-unknown domain distribution gap, significantly boosting generalization and robustness to unseen shifts.
Significant performance improvements on the Diverse Weather dataset and Real-to-Art benchmark demonstrate the superiority of our method.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
在单一源域训练并面向多个未知目标域检测，不接触目标域数据即可获得跨域泛化能力。

### 2. 核心内容
面向单源域广义目标检测的方法通常用离散数据增强或静态扰动来扩充数据多样性，却难以刻画真实场景中天气、光照导致的连续渐变的域偏移。为此本文提出液态时序特征演化机制，让模型模拟特征分布随时间的连续变化，从而捕捉更细粒度的跨域差异。该方法不依赖目标域数据或微调，可提升检测器对多个未知域的泛化能力，为动态域偏移建模提供了新思路。

### 3. 对应检索需求
learning a model that can generalize to unseen domains without fine-tuning。

### 4. 来源与原文
- Source：AAAI-2026-Accepted
- OpenReview：[https://ojs.aaai.org/index.php/AAAI/article/view/38306](https://ojs.aaai.org/index.php/AAAI/article/view/38306)
