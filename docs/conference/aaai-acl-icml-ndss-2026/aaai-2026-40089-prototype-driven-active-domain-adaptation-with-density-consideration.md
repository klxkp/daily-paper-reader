---
title: Prototype-Driven Active Domain Adaptation with Density Consideration
title_zh: 考虑密度的原型驱动主动域适应
authors: "Zeyu Zhang, Chun Shen, Qiang Ma, Meng Kang, Shuai Lü"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/40089/44050"
tags: ["query:few-shot"]
score: 7.0
evidence: 主动域适应，通过密度与原型准则挑选信息样本并在域偏移下适配源模型
tldr: 主动域适应希望只标注少量目标样本来最大化适配收益，但很多方法仅看模型输出而忽略源/目标特征关系。该文提出PDADA，利用密度感知域性与原型驱动信息性两类准则挑选最有价值的目标样本。该方法还结合类别不平衡和簇松散处理，使小标注预算下的域适应更有效。实验表明所提选择标准在域偏移条件下优于常见主动选择策略，为跨域小样本适配提供借鉴。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-40089/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 604, \"height\": 432, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-40089/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1582, \"height\": 670, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-40089/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 626, \"height\": 478, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-40089/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 822, \"height\": 365, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-40089/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 785, \"height\": 345, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-40089/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 796, \"height\": 355, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-40089/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 882, \"height\": 652, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-40089/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1834, \"height\": 629, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-40089/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1834, \"height\": 419, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-40089/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 880, \"height\": 379, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-40089/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 832, \"height\": 182, \"label\": \"Table\"}]"
motivation: 现有主动域适应只使用模型输出，未考虑源/目标域特征关系，可能选出无信息的目标样本。
method: 提出双准则原型主动选择：密度感知域性衡量域内密度，原型驱动信息性衡量对类原型的增量价值。
result: 该策略可挑选更具代表性样本并缓解类不平衡与簇松散问题，提升适配效果。
conclusion: 主动选择应结合源/目标特征关系，为少标注跨域适配提供了更高效途径。
---

## Abstract
Active domain adaptation (ADA) aims to select a small set of target samples for annotation and use them for training to maximally boost the adaptation performance. However, most existing ADA methods only rely on the original output of the model, without considering the relationship between the source and target domain features, which may lead to selecting uninformative samples. In this paper, we propose an effective ADA framework: Prototype-Driven Active Domain Adaptation with density consideration (PDADA). It selects the most valuable target samples in the presence of domain shift through two criteria: Density-Conscious Domainness (DCD) and Prototype-Driven Informativeness (PDI). Furthermore, considering the class imbalance and cluster looseness issues in sample selection and domain adaptation, we develop a Class Balanced Expansion (CBE) algorithm and the Adversarial Active Domain Adaptation via Protecting Structured Information (AADA-PSI). Extensive experiments demonstrate that under the cooperation of the above components, PDADA outperforms previous methods on several challenging benchmarks and can be generalized to multi-source active domain adaptation setting.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
主动域适应，通过密度与原型准则挑选信息样本并在域偏移下适配源模型。

### 2. 核心内容
主动域适应希望只标注少量目标样本来最大化适配收益，但很多方法仅看模型输出而忽略源/目标特征关系。该文提出PDADA，利用密度感知域性与原型驱动信息性两类准则挑选最有价值的目标样本。该方法还结合类别不平衡和簇松散处理，使小标注预算下的域适应更有效。实验表明所提选择标准在域偏移条件下优于常见主动选择策略，为跨域小样本适配提供借鉴。

### 3. 对应检索需求
techniques for adapting a model from a source domain to a target domain with different data distribution。

### 4. 来源与原文
- Source：AAAI-2026-Accepted
- OpenReview：[https://ojs.aaai.org/index.php/AAAI/article/view/40089](https://ojs.aaai.org/index.php/AAAI/article/view/40089)
