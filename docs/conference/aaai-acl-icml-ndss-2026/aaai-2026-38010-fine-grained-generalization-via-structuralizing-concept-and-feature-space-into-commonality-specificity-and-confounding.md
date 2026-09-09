---
title: "Fine-Grained Generalization via Structuralizing Concept and Feature Space into Commonality, Specificity and Confounding"
title_zh: 通过将概念与特征空间划分为共性、特异性与混杂的细粒度泛化
authors: "Zhen Wang, Jiaojiao Zhao, Qilong Wang, Yongfeng Dong, Wenlong Yu"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38010/41972"
tags: ["query:few-shot"]
score: 8.0
evidence: 细粒度域泛化方法，将特征分解为共性、特异性和混杂以泛化到未见域且无需微调
tldr: 细粒度域泛化比常规域泛化更难，因为域偏移会抑制细微类别线索并使性能明显下降。受人类认知中同时利用共有与特有属性的机制启发，该文将概念和特征空间结构化为共性、特异性和混杂三部分。这种结构化显式解耦域偏移来源与类别线索，在未见域上无需目标微调即可分类。实验显示该方法能有效保留关键类别特征，改善细粒度跨域泛化。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38010/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 871, \"height\": 523, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38010/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1779, \"height\": 987, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38010/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 868, \"height\": 904, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38010/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 876, \"height\": 778, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38010/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1468, \"height\": 931, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38010/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 869, \"height\": 442, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38010/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 808, \"height\": 230, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38010/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 787, \"height\": 190, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38010/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 725, \"height\": 192, \"label\": \"Table\"}]"
motivation: 域偏移下细粒度模型对类别线索过于敏感，关键特征易被抑制，现有模型又缺少共性与特有属性的利用。
method: 借鉴认知机制，将概念与特征空间划分为共性、特异性和混杂三个部分进行结构化学习。
result: 该方法能防止关键类别特征被抑制，在细粒度未见域分类中获得更稳健的性能。
conclusion: 为细粒度域泛化提供了显式解耦框架，可作为无需目标微调的跨域部署参考。
---

## Abstract
Fine-Grained Domain Generalization (FGDG) presents greater challenges than conventional domain generalization due to the subtle inter-class differences and relatively pronounced intra-class variations inherent in fine-grained recognition tasks. Under domain shifts, the model becomes overly sensitive to fine-grained cues, leading to the suppression of critical features and a significant drop in performance. 
Cognitive studies suggest that humans classify objects by leveraging both common and specific attributes, enabling accurate differentiation between fine-grained categories. However, current deep learning models have yet to incorporate this mechanism effectively. Inspired by this mechanism, we propose Concept-Feature Structuralized Generalization (CFSG). This model explicitly disentangles both the concept and feature spaces into three structured components: common, specific, and confounding segments. 
To mitigate the adverse effects of varying degrees of distribution shift, we introduce an adaptive mechanism that dynamically adjusts the proportions of common, specific, and confounding components. 
In the final prediction, explicit weights are assigned to each pair of components. 
Extensive experiments on three single-source benchmark datasets demonstrate that CFSG achieves an average performance improvement of 9.87% over baseline models and outperforms existing state-of-the-art methods by an average of 3.08%. Additionally, explainability analysis validates that CFSG effectively integrates multi-granularity structured knowledge and confirms that feature structuralization facilitates the emergence of concept structuralization.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
细粒度域泛化方法，将特征分解为共性、特异性和混杂以泛化到未见域且无需微调。

### 2. 核心内容
细粒度域泛化比常规域泛化更难，因为域偏移会抑制细微类别线索并使性能明显下降。受人类认知中同时利用共有与特有属性的机制启发，该文将概念和特征空间结构化为共性、特异性和混杂三部分。这种结构化显式解耦域偏移来源与类别线索，在未见域上无需目标微调即可分类。实验显示该方法能有效保留关键类别特征，改善细粒度跨域泛化。

### 3. 对应检索需求
learning a model that can generalize to unseen domains without fine-tuning。

### 4. 来源与原文
- Source：AAAI-2026-Accepted
- OpenReview：[https://ojs.aaai.org/index.php/AAAI/article/view/38010](https://ojs.aaai.org/index.php/AAAI/article/view/38010)
