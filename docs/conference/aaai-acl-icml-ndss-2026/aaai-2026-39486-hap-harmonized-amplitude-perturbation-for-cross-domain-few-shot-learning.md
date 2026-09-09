---
title: "HAP: Harmonized Amplitude Perturbation for Cross-Domain Few-Shot Learning"
title_zh: HAP：面向跨域少样本学习的谐波幅度扰动
authors: "Wenqian Li, Pengfei Fang, Hui Xue"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/39486/43447"
tags: ["query:few-shot"]
score: 10.0
evidence: 面向跨域少样本分类，直接在频域处理源/目标域分布偏移
tldr: 跨域少样本学习常因源域与目标域分布差异显著而性能下降，现有方法偏重空间对齐却忽视频域失衡。作者发现频带离散化导致谱塌缩，并通过有效秩量化这一现象。为此提出谐波幅度扰动HAP，调节幅度谱以保持频谱多样性，从而减轻域偏移带来的过拟合与特征退化。实验验证HAP可提升跨域少样本分类性能，为该方向提供频域视角的新方案。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39486/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 842, \"height\": 589, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39486/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 875, \"height\": 772, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39486/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 868, \"height\": 394, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39486/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1734, \"height\": 852, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39486/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1847, \"height\": 775, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-39486/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1829, \"height\": 790, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-39486/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1830, \"height\": 795, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-39486/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 878, \"height\": 502, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-39486/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1829, \"height\": 739, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-39486/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 875, \"height\": 285, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-39486/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 878, \"height\": 402, \"label\": \"Table\"}]"
motivation: 现有跨域少样本方法集中于空间对齐，忽略频域幅度差异导致低频谱主导和谱塌缩，限制泛化。
method: 提出谐波幅度扰动HAP，结合有效秩度量来抑制谱塌缩，增强频域表示多样性。
result: 实验验证HAP能有效缓解跨域偏移下的谱塌缩并提升少样本分类精度。
conclusion: 表明频域扰动是跨域少样本学习的一种有前景的补充手段，值得后续深入研究。
---

## Abstract
Cross-Domain Few-Shot Learning (CD-FSL) remains a significant challenge due to substantial distribution shifts between source and target domains. While prior approaches primarily focus on spatial alignment, they often overlook discrepancies in the frequency domain. In this paper, we reveal frequency band discretization as a key phenomenon, characterized by intra-domain low-frequency dominance, inter-domain amplitude divergence, and limited high-frequency variation. This spectral disharmony biases models toward low-frequency components, leading to spectral collapse. We quantify spectral collapse via the effective rank, a principled measure of spectral diversity. To mitigate spectral collapse, we propose Harmonized Amplitude Perturbation (HAP), a frequency-domain augmentation strategy that perturbs the amplitude spectrum via frequency-aware gains sampled from Harmonized Distributions, while fixing the phase spectrum to maintain semantic integrity. Extensive experiments on both Cross-Domain Few-Shot Image Classification and Object Detection benchmarks demonstrate that HAP effectively increases spectral diversity and consistently improves generalization, outperforming state-of-the-art methods without introducing extra model complexity.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
面向跨域少样本分类，直接在频域处理源/目标域分布偏移。

### 2. 核心内容
跨域少样本学习常因源域与目标域分布差异显著而性能下降，现有方法偏重空间对齐却忽视频域失衡。作者发现频带离散化导致谱塌缩，并通过有效秩量化这一现象。为此提出谐波幅度扰动HAP，调节幅度谱以保持频谱多样性，从而减轻域偏移带来的过拟合与特征退化。实验验证HAP可提升跨域少样本分类性能，为该方向提供频域视角的新方案。

### 3. 对应检索需求
classification task where training and test domains differ and only a few labeled samples are available。

### 4. 来源与原文
- Source：AAAI-2026-Accepted
- OpenReview：[https://ojs.aaai.org/index.php/AAAI/article/view/39486](https://ojs.aaai.org/index.php/AAAI/article/view/39486)
