---
title: "EfficientFSL: Enhancing Few-Shot Classification via Query-Only Tuning In Vision Transformers"
title_zh: EfficientFSL：通过查询样本微调增强视觉Transformer少样本分类
authors: "Wenwen Liao, Hang Ruan, Jianbo Yu, Bing Song, Yuansong Wang, Xiaofeng Yang"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/39519/43480"
tags: ["query:few-shot"]
score: 4.0
evidence: 面向仅有少量标签样本的少样本分类，但未涉及训练与测试域不同的跨域偏移
tldr: 大型Vision Transformer在少样本分类中优于小网络，但微调需要大量GPU显存与时间。为此，本文提出EfficientFSL，一种仅微调查询样本的轻量少样本分类框架，充分利用预训练模型已有的表示与理解能力。在保持高分类精度的同时，该方法显著降低计算开销，使大模型更适用于低资源真实场景。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 大型模型微调成本高，阻碍少样本分类在低资源场景的实际部署。
method: 提出仅对查询样本进行微调的EfficientFSL，冻结骨干并高效利用预训练知识完成少样本分类。
result: 与传统全量微调相比性能相当但显存和训练时间大幅降低，取得较优的少样本精度。
conclusion: 为大型预训练模型在少样本低资源分类中的高效适配提供了实用路径。
---

## Abstract
Large models such as Vision Transformers (ViTs) have demonstrated remarkable superiority over smaller architectures like ResNet in few-shot classification, owing to their powerful representational capacity. However, fine-tuning such large models demands extensive GPU memory and prolonged training time, making them impractical for many real-world low-resource scenarios. To bridge this gap, we propose EfficientFSL, a query-only fine-tuning framework tailored specifically for few-shot classification with ViT, which achieves competitive performance while significantly reducing computational overhead. EfficientFSL fully leverages the knowledge embedded in the pre-trained model and its strong comprehension ability, achieving high classification accuracy with an extremely small number of tunable parameters. Specifically, we introduce a lightweight trainable Forward Block to synthesize task-specific queries that extract informative features from the intermediate representations of the pre-trained model in a query-only manner. We further propose a Combine Block to fuse multi-layer outputs, enhancing the depth and robustness of feature representations. Finally, a Support-Query Attention Block mitigates distribution shift by adjusting prototypes to align with the query set distribution.  With minimal trainable parameters, EfficientFSL achieves state-of-the-art performance on four in-domain few-shot datasets and six cross-domain datasets, demonstrating its effectiveness in real-world applications.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
面向仅有少量标签样本的少样本分类，但未涉及训练与测试域不同的跨域偏移。

### 2. 核心内容
大型Vision Transformer在少样本分类中优于小网络，但微调需要大量GPU显存与时间。为此，本文提出EfficientFSL，一种仅微调查询样本的轻量少样本分类框架，充分利用预训练模型已有的表示与理解能力。在保持高分类精度的同时，该方法显著降低计算开销，使大模型更适用于低资源真实场景。

### 3. 对应检索需求
classification task where training and test domains differ and only a few labeled samples are available。

### 4. 来源与原文
- Source：AAAI-2026-Accepted
- OpenReview：[https://ojs.aaai.org/index.php/AAAI/article/view/39519](https://ojs.aaai.org/index.php/AAAI/article/view/39519)
