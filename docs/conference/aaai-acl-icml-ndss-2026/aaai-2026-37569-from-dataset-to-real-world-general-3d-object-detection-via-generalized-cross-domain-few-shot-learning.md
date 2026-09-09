---
title: "From Dataset to Real-world: General 3D Object Detection via Generalized Cross-domain Few-shot Learning"
title_zh: 从数据集到真实世界：基于广义跨域小样本学习的通用三维目标检测
authors: "Shuangzhi Li, Junlong Shen, Lei Ma, Xingyu Li"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/37569/41531"
tags: ["query:few-shot"]
score: 8.0
evidence: 提出三维目标检测中的广义跨域小样本任务，在新域仅用少量标注适应常见类和新类
tldr: 激光雷达三维检测模型常因公开数据物体多样性有限而难以泛化到真实环境。作者提出三维目标检测中首个广义跨域小样本任务，希望在新域仅用少量标注同时适应常见类和新类。联合框架利用图像引导的多模态融合，将2D开放集语义经视觉语言模型注入3D流程，并用物理感知框搜索增强2D与3D对齐，从而稳定学习目标域语义。该工作把跨域小样本学习从图像检测拓展到三维点云检测，为解决数据集到真实世界分布鸿沟提供了新范式。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37569/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 799, \"height\": 280, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37569/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1540, \"height\": 775, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37569/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 847, \"height\": 289, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37569/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 787, \"height\": 247, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37569/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1756, \"height\": 302, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37569/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1830, \"height\": 511, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37569/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 814, \"height\": 319, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37569/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 437, \"height\": 182, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37569/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 380, \"height\": 182, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37569/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 861, \"height\": 262, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37569/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 878, \"height\": 218, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37569/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 880, \"height\": 261, \"label\": \"Table\"}]"
motivation: 三维检测模型因公开数据集物体多样性有限难以泛化到真实世界，且现有跨域小样本设置未兼顾常见类与新类。
method: 提出广义跨域小样本检测框架，用视觉语言模型将2D开集语义注入3D流程，并结合物理感知框搜索在极少量标注下学习目标语义。
result: 在少量新域标注的条件下稳定学习常见类与新类的目标语义，提升真实世界三维检测的泛化能力。
conclusion: 将广义跨域小样本学习引入三维检测，证明多模态语义桥接能缓解真实世界标注稀缺造成的领域鸿沟。
---

## Abstract
LiDAR-based 3D object detection models often struggle to generalize to real-world environments due to limited object diversity in existing datasets. To tackle it, we introduce the first generalized cross-domain few-shot (GCFS) task in 3D object detection, aiming to adapt a source-pretrained model to both common and novel classes in a new domain with only few-shot annotations. We propose a unified framework that learns stable target semantics under limited supervision by bridging 2D open-set semantics with 3D spatial reasoning. Specifically, an image-guided multi-modal fusion injects transferable 2D semantic cues into the 3D pipeline via vision-language models, while a physically-aware box search enhances 2D-to-3D alignment via LiDAR priors. To capture class-specific semantics from sparse data, we further introduce contrastive-enhanced prototype learning, which encodes few-shot instances into discriminative semantic anchors and stabilizes representation learning. Extensive experiments on GCFS benchmarks demonstrate the effectiveness and generality of our approach in realistic deployment settings.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
提出三维目标检测中的广义跨域小样本任务，在新域仅用少量标注适应常见类和新类。

### 2. 核心内容
激光雷达三维检测模型常因公开数据物体多样性有限而难以泛化到真实环境。作者提出三维目标检测中首个广义跨域小样本任务，希望在新域仅用少量标注同时适应常见类和新类。联合框架利用图像引导的多模态融合，将2D开放集语义经视觉语言模型注入3D流程，并用物理感知框搜索增强2D与3D对齐，从而稳定学习目标域语义。该工作把跨域小样本学习从图像检测拓展到三维点云检测，为解决数据集到真实世界分布鸿沟提供了新范式。

### 3. 对应检索需求
What methods are proposed to handle domain shift in few shot classification tasks。

### 4. 来源与原文
- Source：AAAI-2026-Accepted
- OpenReview：[https://ojs.aaai.org/index.php/AAAI/article/view/37569](https://ojs.aaai.org/index.php/AAAI/article/view/37569)
