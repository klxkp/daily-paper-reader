---
title: Return of Frustratingly Easy Unsupervised Video Domain Adaptation
title_zh: MetaTrans：回归简单的无监督视频域适应
authors: "Pengfei Wei, Yiqun Sun, zhiqiang xu, Yiping Ke, Lawrence B. Hsieh"
date: 2026-04-30
pdf: "https://openreview.net/pdf/f74c60b1a3b2e5d4ce77e526fc81cd89ccb7e9cb.pdf"
tags: ["query:few-shot"]
score: 6.0
evidence: 提出极简的无监督视频域适应方法，通过时间-静态相减模块分别消除跨域视频的空间与时序差异
tldr: 无监督视频域适应是重要但尚未充分探索的问题，现有方法往往引入复杂目标。论文提出极其简洁的MetaTrans方法，学习目标仅包含两个基础损失项，同时利用时间-静态相减模块在模型架构层面分别剥离跨域视频的空间差异与时序差异。该设计在多个跨域动作识别任务上带来显著的绝对性能提升，证明将空间与时序域差异解耦后，简单目标也能实现强适应效果。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 无监督视频域适应中空间与时序差异交织，现有方法复杂且难以分离这两类域偏移。
method: 用时间-静态相减模块分别消除空间与时序域差异，仅保留两个基础损失项作为学习目标。
result: 在跨域动作识别等多项视频域适应任务上取得显著的绝对性能提升，验证了简洁设计的高效性。
conclusion: 将视频域偏移分解为空间与时序两部分并配以极简目标，为无监督视频域适应提供了易扩展的高效路线。
---

## Abstract
Unsupervised video domain adaptation (UVDA) is a practical but under-explored problem.
In this paper, we propose a frustratingly easy UVDA method, called \emph{MetaTrans}.
Specifically, \emph{MetaTrans} adopts a concise learning objective that contains only two fundamental loss terms.
Despite the simplicity of the learning objective, \emph{MetaTrans} embodies an advanced UVDA idea, that is, handling the spatial and temporal divergence of cross-domain videos separately, through a subtle model architecture design.
By implementing a temporal-static subtraction module, \emph{MetaTrans} effectively removes spatial and temporal divergence.
Extensive empirical evaluations, particularly on various cross-domain action recognition tasks, show substantial absolute adaptation performance enhancement and significantly superior relative performance gain compared with state-of-the-art UVDA baselines.

---

## 论文详细总结（自动生成）

# 论文总结

## 1. 核心问题与整体含义（研究动机和背景）

- 无监督视频域适应（UVDA）是一个**实用但尚未充分探索**的问题。
- 当视频数据在不同域（如不同场景、拍摄条件、动作风格）之间迁移时，标签信息不可用，模型需要借助源域知识完成目标域任务。
- 与图像域适应不同，视频中同时存在**空间差异**（外观、背景等）与**时序差异**（动作节奏、帧间动态等），且二者相互交织，导致适应过程更具挑战。
- 现有 UVDA 方法往往设计复杂的目标函数或训练流程，但效果仍有限。
- 论文的核心动机是探索一种**极其简洁**、却能够有效应对空间与时序双重偏移的 UVDA 方法。

## 2. 论文提出的方法论

- **方法名称**：MetaTrans（回归简单的无监督视频域适应方法）。
- **核心思想**：将跨域视频之间的差异解耦为两部分——**空间差异**和**时序差异**，并在模型架构层面分别处理，而不是通过复杂目标函数强行对齐。
- **学习目标**：仅包含**两个基础损失项**，没有额外复杂的对抗损失、循环一致性等组件。
- **关键模块**：**时间-静态相减模块（temporal-static subtraction module）**。
  - 该模块用于“剥离”视频中的动态信息与静态信息，从而分别消除跨域的空间与时序差异。
  - 通过这一设计，模型可以避免空间差异与时序差异相互干扰，使两个基础损失项能够高效发挥作用。
- **整体流程**（根据摘要的文字描述推断）：
  1. 输入跨域源视频和目标视频；
  2. 利用时间-静态相减模块分解出空间相关表征与时序相关表征；
  3. 对分解后的表征施加两个基础损失项（可能分别对应空间对齐与时序对齐）进行优化；
  4. 完成源域到目标域的知识迁移。
- 摘要中未给出详细的公式或算法伪代码，但强调学习目标之“简单”和架构设计之“精妙”，即**用架构而非损失复杂度来解决问题**。

## 3. 实验设计：数据集、场景与对比方法

- **任务场景**：主要围绕**跨域动作识别**（cross-domain action recognition）任务展开。
- **数据集**：摘要中只提到“各种跨域动作识别任务”（various cross-domain action recognition tasks），但**未列出具体数据集名称**（如 UCF101/HMDB51、EPIC-KITCHENS 等常见基准）。
- **Benchmark**：未明确指出使用哪个/哪些标准 benchmark，只描述了跨域动作识别设置。
- **对比方法**：摘要称与 **state-of-the-art UVDA baselines（最先进的无监督视频域适应基线）** 进行了比较，但**未列出具体方法名称**。
- 评价指标为适应后的绝对性能提升和相对性能增益。

## 4. 资源与算力

- 摘要及可见元数据中**未提及任何算力相关信息**，例如 GPU 型号、数量、训练时长、显存消耗等。
- 因此，无法从现有内容中获知该方法的计算资源开销；若需要评估效率，需查阅原文实验章节。

## 5. 实验数量与充分性

- 摘要称进行了“广泛的实证评估”（extensive empirical evaluations），同时明确报告了“显著的绝对性能提升”和“优于 SOTA 基线的相对收益”。
- 但可见内容中**没有列出具体的实验组数**，也没有提到是否包含消融实验、灵敏度分析、跨数据集泛化实验、不同骨干网络测试等。
- 由于论文是 ICML-2026 已接收论文，完整版本应当包含更充分的实验；**但仅依据提供的摘要，无法判断实验的完整性和公平性**（例如基线是否公平调参、是否使用相同的骨干网络、重复次数等均未说明）。
- 总体而言，摘要中的实验信息过于简略，不足以做深入的方法学评估。

## 6. 论文的主要结论与发现

- 通过**时间-静态相减模块**将空间与时序域差异解耦，是解决 UVDA 的有效思路。
- 即便学习目标仅包含两个基础损失项，**简洁的优化目标也可以实现强适应效果**，一反“必须设计复杂目标”的直觉。
- 在跨域动作识别任务上，MetaTrans 相比现有 SOTA UVDA 方法取得了**显著的绝对性能提升**和**更高的相对性能增益**。
- 论文主张：将视频域偏移显式分解为空间与时序两大可分离部分，是构建高效、易扩展 UVDA 算法的途径。

## 7. 优点

- **方法极度简洁**：学习目标只有两个基础损失，易于实现和复现，降低了训练调参难度。
- **思想先进**：在架构层面解耦空间与时序差异，而非依赖复杂损失对抗，具有清晰的理论直觉。
- **性能突出**：在多个跨域动作识别设置下均获得明显提升，证明方法的有效性和泛化性。
- **可扩展性强**：极简目标 + 模块化架构设计，为后续 UVDA 工作提供了易插入、易扩展的基础组件。
- 标题与表述（“Frustratingly Easy”）强调了方法易用性，具有较强实用价值。

## 8. 不足与局限

- **可复现信息不足**：当前提供的文本中缺少具体数据集、基线方法、网络结构、超参数设置等关键细节，难以直接复现或客观比较。
- **实验细节缺失**：没有展示消融实验、可视化分析、参数敏感性分析，无法证明时间-静态相减模块和各损失项的单独贡献。
- **场景覆盖有限**：虽然摘要声称“各种跨域动作识别任务”，但未提及多域/开放域/部分域等更复杂设置，也未涉及其他视频任务（如视频语义分割、视频检测）的验证。
- **可能存在的偏差风险**：如果对比基线未经过同等调优或仅比较弱基线，则“SOTA 提升”的结论可能受影响；现有摘要中未确认基线公平性。
- **理论分析不足**：没有给出为何“两个基础损失 + 模块化减法”能够对齐空间与时序的理论解释或收敛性分析，更多依赖经验结论。
- **资源与效率信息缺失**：无法评估模型在训练和推理阶段的实际成本。

（完）
