---
title: Cross-Domain Few-Shot Learning via Multi-View Collaborative Optimization with Vision-Language Models
title_zh: 基于多视角协同优化与视觉语言模型的跨域少样本学习
authors: "Dexia Chen, Wentao Zhang, Qianjie Zhu, Ping Hu, Weibing Li, Tong Zhang, Ruixuan Wang"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/39086/43048"
tags: ["query:few-shot"]
score: 10.0
evidence: 面向视觉语言模型的跨域少样本学习方法，用多视角协同优化应对成像域偏离
tldr: CLIP等视觉语言模型在自然图像少样本任务上表现出色，但当图像域与自然图像差异大时仍会失效。该文提出一致性引导的多视角协同优化CoMuCo，用两个功能互补的专家模块提取多视角特征，并通过协同优化提高跨域任务的适配能力。这种策略能扩展VLM到不同成像域，缓解高效微调方法在跨域任务上的不足，为跨域少样本分类提供有效方案。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39086/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 876, \"height\": 710, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39086/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1575, \"height\": 618, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39086/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 868, \"height\": 334, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39086/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1739, \"height\": 573, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39086/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1740, \"height\": 851, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39086/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 828, \"height\": 338, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39086/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1830, \"height\": 263, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39086/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 754, \"height\": 410, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-39086/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 892, \"height\": 495, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-39086/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 892, \"height\": 931, \"label\": \"Table\"}]"
motivation: 现有VLM的高效迁移方法在自然图像少样本任务收益大，但在成像域偏离的跨域任务效果有限。
method: 提出CoMuCo，使用两个互补专家模块提取多视角表示，并以一致性约束协同优化以适配跨域数据。
result: 在非自然图像的跨域少样本任务上，CoMuCo明显改善模型泛化能力并保持迁移效率。
conclusion: 多视角互补与一致性约束可弥补VLM在跨域小样本图像识别上的泛化短板。
---

## Abstract
Vision-language models (VLMs) pre-trained on natural image and language data, such as CLIP, have exhibited significant potential in few-shot image recognition tasks, leading to development of various efficient transfer learning methods. These methods exploit inherent pre-learned knowledge in VLMs and have achieved strong performance on standard image datasets. However, their effectiveness is often limited when confronted with cross-domain tasks where imaging domains differ from natural images. To address this limitation, we propose Consistency-guided Multi-view Collaborative Optimization (CoMuCo), a novel fine-tuning strategy for VLMs. This strategy employs two functionally complementary expert modules to extract multi-view features, while incorporating prior knowledge-based consistency constraints and information geometry-based consensus mechanisms to enhance the robustness of feature learning. Additionally, a new cross-domain few-shot benchmark is established to help comprehensively evaluate methods on imaging domains distinct from natural images. Extensive empirical evaluations on both existing and newly proposed benchmarks suggest CoMuCo consistently outperforms current methods.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
面向视觉语言模型的跨域少样本学习方法，用多视角协同优化应对成像域偏离。

### 2. 核心内容
CLIP等视觉语言模型在自然图像少样本任务上表现出色，但当图像域与自然图像差异大时仍会失效。该文提出一致性引导的多视角协同优化CoMuCo，用两个功能互补的专家模块提取多视角特征，并通过协同优化提高跨域任务的适配能力。这种策略能扩展VLM到不同成像域，缓解高效微调方法在跨域任务上的不足，为跨域少样本分类提供有效方案。

### 3. 对应检索需求
classification task where training and test domains differ and only a few labeled samples are available。

### 4. 来源与原文
- Source：AAAI-2026-Accepted
- OpenReview：[https://ojs.aaai.org/index.php/AAAI/article/view/39086](https://ojs.aaai.org/index.php/AAAI/article/view/39086)
