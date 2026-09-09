---
title: Intra-Image Mining and Symmetric Maximum Concept Matching for Few Shot Out-of-Distribution Detection
title_zh: 通过图像内挖掘与对称最大概念匹配的小样本分布外检测
authors: "Kaixiang Chen, Pengfei Fang, Hui Xue"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/37280/41242"
tags: ["query:few-shot"]
score: 4.0
evidence: 面向未见过或分布外样本的小样本识别，但任务目标为分布外检测，与跨域小样本分类不同
tldr: 基于视觉语言模型的零样本分布外检测受局部特征原型不完善和缺少分布外原型限制。IIM通过图像内挖掘，先选出每张图像中与类原型最相关的局部块作为正样本，再以对称最大概念匹配提升小样本分布外识别能力。该框架轻量且只需少量样本，为小样本开放环境感知提供了补充，但与面向源-目标域的跨域小样本分类问题存在本质差异。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 现有视觉语言模型零样本分布外检测受限于局部特征原型不完善且缺少分布外原型。
method: 提出图像内挖掘IIM，选择与类原型相关的局部块作为正样本，并用对称最大概念匹配进行小样本优化。
result: 以轻量方式改善零样本检测的原型缺陷，提升小样本分布外检测能力。
conclusion: 该工作属于小样本分布外检测，方法思路可借鉴，但与查询的跨域小样本分类任务弱相关。
---

## Abstract
Recent vision-language model (VLM)-based methods have achieved promising results in zero-shot out-of-distribution (OOD) detection by effectively leveraging the local patch features. However, the zero-shot nature inherently comes with two limitations: 1) imperfect local feature prototypes; 2) lack of OOD prototypes. In this paper, we propose Intra-Image Mining (IIM), a lightweight framework designed to overcome these limitations in a few-shot manner. IIM is motivated by the fact that local patches within an image often exhibit diverse semantics, with some patches deviating from the main class concept. Therefore, for each image, we first select the top-k class prototype-related patches as positive samples and leverage them to refine and optimize the local feature prototype. Then, the next top-k among the remaining patches are selected as negatives—serving as OOD signals to construct OOD prototypes. This process yields  coherent local positives and challenging negatives, effectively enhancing the model’s local feature discrimination.  
Besides, we propose a novel inference strategy named Symmetric Maximum Concept Matching (S-MCM). While existing approaches typically adopt an image-to-text scheme—comparing the image features to textual class prototypes—S-MCM further incorporate a text-to-image perspective, leading to more reliable OOD detection. We also propose two benchmarks to analyze the impact of semantic diversity within ID dataset. Built on a frozen VLM, IIM, in conjunction with S-MCM, achieves consistent gains in OOD detection on ImageNet-1k and other benchmarks, outperforming prior methods in FPR95 and AUROC across various few-shot settings.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
面向未见过或分布外样本的小样本识别，但任务目标为分布外检测，与跨域小样本分类不同。

### 2. 核心内容
基于视觉语言模型的零样本分布外检测受局部特征原型不完善和缺少分布外原型限制。IIM通过图像内挖掘，先选出每张图像中与类原型最相关的局部块作为正样本，再以对称最大概念匹配提升小样本分布外识别能力。该框架轻量且只需少量样本，为小样本开放环境感知提供了补充，但与面向源-目标域的跨域小样本分类问题存在本质差异。

### 3. 对应检索需求
learning a model that can generalize to unseen domains without fine-tuning。

### 4. 来源与原文
- Source：AAAI-2026-Accepted
- OpenReview：[https://ojs.aaai.org/index.php/AAAI/article/view/37280](https://ojs.aaai.org/index.php/AAAI/article/view/37280)
