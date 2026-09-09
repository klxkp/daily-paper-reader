---
title: "MPA: Multimodal Prototype Augmentation for Few-Shot Learning"
title_zh: MPA：用于少样本学习的多模态原型增强
authors: "Liwen Wu, Wei Wang, Lei Zhao, Zhan Gao, Qika Lin, Shaowen Yao, Zuozhu Liu, Bin Pu"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/39909/43870"
tags: ["query:few-shot"]
score: 4.0
evidence: 面向仅有少数标注样本的少样本分类，但未讨论域间分布差异
tldr: 少样本学习旨在从极少量标注样本中识别新类，现有方法多只依赖视觉模态，直接由原始支持图计算原型，缺少多模态信息。本文提出多模态原型增强框架MPA，通过大语言模型生成多样化的类别描述，结合层次化多视角增强与自适应不确定类吸收模块，丰富类别表征，从而提升少样本新类识别性能。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 主流少样本方法仅用视觉模态从原始支持图像中计算原型，缺乏跨模态语义与细粒度类别判别信息。
method: 提出MPA框架，以大语言模型生成多样化描述，并配合层次多视角增强和不确定类吸收模块增强原型。
result: 融入多模态语义增强后，少样本分类精度获得提升，尤其在类别差异细微时更有效。
conclusion: 说明利用语义生成与多视角增强是改善少样本分类原型质量的有效方向。
---

## Abstract
Recently, Few-shot Learning (FSL) has become a popular task that aims to recognize new classes from only a few labeled examples and has been widely applied in fields such as natural science, remote sensing, and medical images.
However, most existing methods focus only on the visual modality and compute prototypes directly from raw support images, which lack comprehensive and rich multimodal information.
To address these limitations, we propose a novel Multimodal Prototype Augmentation FSL framework called MPA, including LLM-based Multi-Variant Semantic Enhancement (LMSE), Hierarchical Multi-View Augmentation (HMA), and an Adaptive Uncertain Class Absorber (AUCA). 
LMSE leverages large language models to generate diverse paraphrased category descriptions, enriching the support set with additional semantic cues. 
HMA exploits both natural and multi-view augmentations to enhance feature diversity (e.g., changes in viewing distance, camera angles, and lighting conditions). 
AUCA models uncertainty by introducing uncertain classes via interpolation and Gaussian sampling, effectively absorbing uncertain samples. 
Extensive experiments on four single-domain and six cross-domain FSL benchmarks demonstrate that MPA achieves superior performance compared to existing state-of-the-art methods across most settings. Notably, MPA surpasses the second-best method by 12.29% and 24.56% in the single-domain and cross-domain setting, respectively, in the 5-way 1-shot setting.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
面向仅有少数标注样本的少样本分类，但未讨论域间分布差异。

### 2. 核心内容
少样本学习旨在从极少量标注样本中识别新类，现有方法多只依赖视觉模态，直接由原始支持图计算原型，缺少多模态信息。本文提出多模态原型增强框架MPA，通过大语言模型生成多样化的类别描述，结合层次化多视角增强与自适应不确定类吸收模块，丰富类别表征，从而提升少样本新类识别性能。

### 3. 对应检索需求
classification task where training and test domains differ and only a few labeled samples are available。

### 4. 来源与原文
- Source：AAAI-2026-Accepted
- OpenReview：[https://ojs.aaai.org/index.php/AAAI/article/view/39909](https://ojs.aaai.org/index.php/AAAI/article/view/39909)
