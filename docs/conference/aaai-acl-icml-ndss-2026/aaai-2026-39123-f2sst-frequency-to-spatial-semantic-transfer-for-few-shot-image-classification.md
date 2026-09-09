---
title: "F2SST: Frequency-to-Spatial Semantic Transfer for Few-Shot Image Classification"
title_zh: F2SST：面向少样本图像分类的频域到空间语义迁移
authors: "Xueyi Chen, Bangjun Wang, Jiaqing Fan, Li Zhang, Fanzhang Li"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/39123/43085"
tags: ["query:few-shot"]
score: 4.0
evidence: 属于小样本分类方法但未涉及训练与测试域不同的分布偏移
tldr: 小样本图像分类在监督有限时难以学习充分特征，而现有引入语义先验的方法或有歧义或依赖外部资源。该文将频域视为隐式且任务自适应的语义来源，提出F2SST频域到空间语义迁移框架，用频谱信息增强特征表达。实验表明该方法可提升少样本分类性能，但它未涉及跨域分布偏移，因此与核心需求的关联有限。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 现有少样本方法依赖类名或知识图谱等外部语义，存在歧义和资源开销问题。
method: 提出F2SST框架，把频域当作隐式语义，并将频谱特征迁移到空间增强少样本特征学习。
result: 实验表明利用频域语义可在小样本图像分类上取得性能增益。
conclusion: 说明频域可作为少样本分类无需外部知识的语义补充，但需扩展至跨域设置才更契合目标。
---

## Abstract
Few-shot image classification (FSIC) aims to recognize novel categories from only a few labeled examples, making it inherently challenging under limited supervision. Existing approaches have attempted to alleviate this issue by incorporating explicit semantics like class names or knowledge graphs to guide learning. However, such methods often encounter semantic ambiguity due to their dependence on either overly simplistic semantic priors or resource-intensive external knowledge sources, which limits their potential. In this paper, we explore the frequency domain as an implicit and task-adaptive source of semantic information. We propose F2SST, a Frequency-to-Spatial Semantic Transfer framework that enhances feature learning by leveraging spectral signals as hidden semantics. Specifically, F2SST applies Fast Fourier Transform (FFT) to extract phase-invariant global frequency descriptors, followed by a lightweight Gated Spectral Attention (GSA) module that selectively emphasizes class-relevant frequency components. These enhanced spectral cues are then integrated into the spatial stream through a class-guided fusion mechanism, enabling more robust and semantically aligned representations. Extensive experiments on four standard benchmarks (miniImageNet, tieredImageNet, CIFAR-FS and FC100)  demonstrate that F2SST consistently improves performance, validating the effectiveness of frequency-domain semantics in FSIC.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
属于小样本分类方法但未涉及训练与测试域不同的分布偏移。

### 2. 核心内容
小样本图像分类在监督有限时难以学习充分特征，而现有引入语义先验的方法或有歧义或依赖外部资源。该文将频域视为隐式且任务自适应的语义来源，提出F2SST频域到空间语义迁移框架，用频谱信息增强特征表达。实验表明该方法可提升少样本分类性能，但它未涉及跨域分布偏移，因此与核心需求的关联有限。

### 3. 对应检索需求
classification task where training and test domains differ and only a few labeled samples are available。

### 4. 来源与原文
- Source：AAAI-2026-Accepted
- OpenReview：[https://ojs.aaai.org/index.php/AAAI/article/view/39123](https://ojs.aaai.org/index.php/AAAI/article/view/39123)
