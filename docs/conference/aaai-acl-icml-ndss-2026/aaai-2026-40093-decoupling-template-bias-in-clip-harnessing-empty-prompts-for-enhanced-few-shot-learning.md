---
title: "Decoupling Template Bias in CLIP: Harnessing Empty Prompts for Enhanced Few-Shot Learning"
title_zh: 解耦CLIP中的模板偏差：利用空提示增强小样本学习
authors: "Zhenyu Zhang, Guangyao Chen, Yixiong Zou, Zhimeng Huang, Yuhua Li"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/40093/44054"
tags: ["query:few-shot"]
score: 4.0
evidence: 提升小样本分类精度与鲁棒性，但未涉及训练/测试领域不一致的跨域场景
tldr: CLIP在小样本分类中，模板与样本的相似度会引入偏差，使模型依赖模板邻近度而非真实类别对齐，降低精度与鲁棒性。作者提出空提示框架，用不含类别信息的空文本捕获无偏模板特征，并通过两阶段训练在预训练阶段揭示并缓解模板偏差。实验表明该方法能有效抵消模板偏差，提升少样本分类的性能与稳定性。该工作为CLIP小样本分类提供了简洁实用的提示学习策略。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: CLIP小样本分类中模板-样本相似度偏差会误导模型，使其过度依赖模板位置而非真实类别对齐，影响精度与鲁棒性。
method: 设计空提示文本以捕获无偏模板特征，并采用两阶段训练揭示并降低模板偏差，改善少样本分类。
result: 实验表明该方法能有效抵消模板偏差，在多个小样本分类基准上提升准确率与鲁棒性。
conclusion: 空提示是一种简单有效的提示学习方法，能解耦CLIP中的模板偏差，增强少样本分类性能。
---

## Abstract
The Contrastive Language-Image Pre-Training (CLIP) model excels in few-shot learning by aligning visual and textual representations. Our study shows that template-sample similarity (TSS), defined as the resemblance between a text template and an image sample, introduces bias. This bias leads the model to rely on template proximity rather than true sample-to-category alignment, reducing both accuracy and robustness in classification.
We present a framework that uses empty prompts, textual inputs that convey the idea of “emptiness” without category information. These prompts capture unbiased template features and offset TSS bias. The framework employs two stages. During pre-training, empty prompts reveal and reduce template-induced bias within the CLIP encoder. During few-shot fine-tuning, a bias calibration loss enforces correct alignment between images and their categories, ensuring the model focuses on relevant visual cues.
Experiments across multiple benchmarks demonstrate that our template correction method significantly reduces performance fluctuations caused by TSS, yielding higher classification accuracy and stronger robustness.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
提升小样本分类精度与鲁棒性，但未涉及训练/测试领域不一致的跨域场景。

### 2. 核心内容
CLIP在小样本分类中，模板与样本的相似度会引入偏差，使模型依赖模板邻近度而非真实类别对齐，降低精度与鲁棒性。作者提出空提示框架，用不含类别信息的空文本捕获无偏模板特征，并通过两阶段训练在预训练阶段揭示并缓解模板偏差。实验表明该方法能有效抵消模板偏差，提升少样本分类的性能与稳定性。该工作为CLIP小样本分类提供了简洁实用的提示学习策略。

### 3. 对应检索需求
classification task where training and test domains differ and only a few labeled samples are available。

### 4. 来源与原文
- Source：AAAI-2026-Accepted
- OpenReview：[https://ojs.aaai.org/index.php/AAAI/article/view/40093](https://ojs.aaai.org/index.php/AAAI/article/view/40093)
