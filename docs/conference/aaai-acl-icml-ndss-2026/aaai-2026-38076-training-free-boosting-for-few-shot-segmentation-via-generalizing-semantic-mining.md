---
title: Training-free Boosting for Few-shot Segmentation via Generalizing Semantic Mining
title_zh: 基于泛化语义挖掘的无训练少样本分割增强
authors: "Kangyu Xiao, Zilei Wang, Yixin Zhang, Junjie Li"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38076/42038"
tags: ["query:few-shot"]
score: 4.0
evidence: 少样本语义分割利用极少量标注示例，未涉及域偏移，仅改进亲和力计算
tldr: 少样本语义分割旨在仅用极少标注示例分割新目标，现有亲和力计算只依赖支持-查询匹配，未利用查询自身语义及支持样本之间的关联。为此提出泛化语义挖掘（GSM），将亲和力推断组织为三个主要步骤，利用查询语义和支持样本间语义相关性增强亲和力图表示。该增强方法无需额外训练，即可在推理阶段提升专用分割模型和基础模型在少样本任务上的性能，拓展了亲和力建模的表达能力。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 少样本分割中现有亲和力计算仅考虑支持-查询匹配，忽略查询自身语义与支持样本间相关性，限制了表示能力。
method: 提出泛化语义挖掘，将亲和力推断分为三个步骤，挖掘查询特定语义与支持样本间的泛化语义以改进亲和力图。
result: 无需额外训练即可提升专用分割模型与基础模型在少样本分割上的性能。
conclusion: 显式挖掘泛化语义能增强推理阶段亲和力计算，是通用且有效的少样本分割增强手段。
---

## Abstract
Few-shot Semantic Segmentation (FSS) aims to segment the novel target objects with the guidance of minimal annotated reference examples. 
The affinity-based method has great advantages in the FSS inference stage for both specialist model and foundation model. However, current affinity calculation merely relies on only support-query matching, without considering the query-specific semantic or the semantic correlation among inter-support samples, which limits the representation ability of affinity map. In this paper, we propose the Generalizing Semantic Mining (GSM) that focuses on exploiting generalizing semantic to improve the affinity calculation. Concretely, we first organize the affinity-based inference into three main steps to reveal the crucial role of affinity map. To address the low-data problem, Target Semantic Reusing module considers the query sample as a proxy reference and assigns it with proxy mask identifying its most generalizing semantic regions. Then, to generate the high-fidelity proxy mask, Query-specific Semantic Modeling module pinpoints the most generalizing regions through prior semantic analysis. Finally, Representative Re-weighting module explicitly modulates affinity calculation via generalization-aware weighting. Experiments on FSS benchmarks demonstrate that our GSM can serve as a plug-and-play free lunch for both specialist models and foundation models.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
少样本语义分割利用极少量标注示例，未涉及域偏移，仅改进亲和力计算。

### 2. 核心内容
少样本语义分割旨在仅用极少标注示例分割新目标，现有亲和力计算只依赖支持-查询匹配，未利用查询自身语义及支持样本之间的关联。为此提出泛化语义挖掘（GSM），将亲和力推断组织为三个主要步骤，利用查询语义和支持样本间语义相关性增强亲和力图表示。该增强方法无需额外训练，即可在推理阶段提升专用分割模型和基础模型在少样本任务上的性能，拓展了亲和力建模的表达能力。

### 3. 对应检索需求
classification task where training and test domains differ and only a few labeled samples are available。

### 4. 来源与原文
- Source：AAAI-2026-Accepted
- OpenReview：[https://ojs.aaai.org/index.php/AAAI/article/view/38076](https://ojs.aaai.org/index.php/AAAI/article/view/38076)
