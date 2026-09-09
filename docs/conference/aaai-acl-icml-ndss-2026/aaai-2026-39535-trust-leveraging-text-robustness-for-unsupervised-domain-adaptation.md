---
title: "TRUST: Leveraging Text Robustness for Unsupervised Domain Adaptation"
title_zh: TRUST：利用文本鲁棒性进行无监督域适应
authors: "Mattia Litrico, Mario Valerio Giuffrida, Sebastiano Battiato, Devis Tuia"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/39535/43496"
tags: ["query:few-shot"]
score: 6.0
evidence: 利用语言模态作为鲁棒信号，引导视觉模型在地理等复杂分布偏移下完成无监督域适应
tldr: 针对背景与物体外观同时显著变化的地理等复杂分布偏移下无监督域适应性能退化的问题，TRUST利用文本描述对域偏移更鲁棒的属性，为目标样本生成伪标签，并以归一化CLIP相似度估计不确定性，从而引导视觉模型适应目标域。所提出的多模态引导策略可缓解经典UDA在复杂跨域场景中的失效问题，为借助语言模态支撑视觉域适应提供了新思路。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 现有无监督域适应在经典分布偏移上有效，但在背景和物体外观差异显著的复杂偏移下仍会退化，需要引入更鲁棒的语言模态。
method: 用目标样本的文本描述生成伪标签，结合归一化CLIP相似度的不确定性估计，以语言鲁棒性引导视觉模型适应目标域。
result: 在复杂跨域场景中提升视觉模型的域适应能力，缓解传统UDA在显著外观变化下的失效问题。
conclusion: 表明文本鲁棒性是视觉域适应中可利用的强信号，为复杂分布偏移的适应提供了可行方向。
---

## Abstract
Recent unsupervised domain adaptation (UDA) methods have shown great success in addressing classical domain shifts (e.g., synthetic-to-real), but they still suffer under complex shifts (e.g. geographical shift), where both the background and object appearances differ significantly across domains. Prior works showed that the language modality can help in the adaptation process, exhibiting more robustness to such complex shifts. In this paper, we introduce TRUST, a novel UDA approach that exploits the robustness of the language modality to guide the adaptation of a vision model. TRUST generates pseudo-labels for target samples from their captions and introduces a novel uncertainty estimation strategy that uses normalised CLIP similarity scores to estimate the uncertainty of the generated pseudo-labels. Such estimated uncertainty is then used to reweight the classification loss, mitigating the adverse effects of wrong pseudo-labels obtained from low-quality captions. To further increase the robustness of the vision model, we propose a multimodal soft-contrastive learning loss that aligns the vision and language feature spaces, by leveraging captions to guide the contrastive training of the vision model on target images. In our contrastive loss, each pair of images acts as both a positive and a negative pair and their feature representations are attracted and repulsed with a strength proportional to the similarity of their captions. This solution avoids the need for hardly determining positive and negative pairs, which is critical in the UDA setting. Our approach outperforms previous methods, setting the new state-of-the-art on classical (DomainNet) and complex (GeoNet) domain shifts. The code is available at https://github.com/MattiaLitrico/TRUST-Leveraging-Text-Robustness-for-Unsupervised-Domain-Adaptation.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
利用语言模态作为鲁棒信号，引导视觉模型在地理等复杂分布偏移下完成无监督域适应。

### 2. 核心内容
针对背景与物体外观同时显著变化的地理等复杂分布偏移下无监督域适应性能退化的问题，TRUST利用文本描述对域偏移更鲁棒的属性，为目标样本生成伪标签，并以归一化CLIP相似度估计不确定性，从而引导视觉模型适应目标域。所提出的多模态引导策略可缓解经典UDA在复杂跨域场景中的失效问题，为借助语言模态支撑视觉域适应提供了新思路。

### 3. 对应检索需求
techniques for adapting a model from a source domain to a target domain with different data distribution。

### 4. 来源与原文
- Source：AAAI-2026-Accepted
- OpenReview：[https://ojs.aaai.org/index.php/AAAI/article/view/39535](https://ojs.aaai.org/index.php/AAAI/article/view/39535)
