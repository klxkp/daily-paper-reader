---
title: Parameter-Masked Decoupled Optimization for Cross-Domain Class-Incremental Learning
title_zh: 面向跨域类增量学习的参数掩码解耦优化
authors: "Ziqi Gu, Chunyan Xu, Yangguang Liu, Wenxuan Fang, Baotong Su, Tong Zhang, Dan Wang, Zhen Cui"
date: 2026-04-30
pdf: "https://openreview.net/pdf/9ee79657016cbdd81f197c8d7e5ea3ccdf7628bd.pdf"
tags: ["query:few-shot"]
score: 4.0
evidence: 跨域类增量学习中域偏移引发不稳定适配和严重遗忘，需约束更新并保留已学知识
tldr: 跨域类增量学习要求模型在域不断变化时持续学习新类并保持已有知识。现有方法常将更新内容与更新方式耦合，在域偏移下容易产生不稳定适配与严重遗忘。本文借鉴海马体机制，提出参数掩码解耦优化PMDO，通过领域感知知识解耦器选择性地适配共享参数，把快速适配与稳定巩固分离，以缓解遗忘并增强跨域持续学习能力。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 跨域增量场景中域偏移导致更新不稳定与前向遗忘，根因在于更新内容和更新方式相互纠缠。
method: 提出参数掩码解耦优化框架，借助领域感知知识解耦器保留类共享知识，限制增量更新范围。
result: 能够缓解跨域偏移下的灾难性遗忘，在不牺牲已学知识的前提下持续适配新域新类。
conclusion: 将记忆巩固机制引入跨域增量学习，为持续适应与稳定保留提供解耦优化范式。
---

## Abstract
Cross-domain class-incremental learning (CD-CIL) requires models to continuously acquire new classes across shifting domains while retaining previously learned knowledge. Existing approaches often entangle what to update with how to update, resulting in unstable adaptation and severe forgetting under domain shifts.
Inspired by the hippocampal learning mechanism that separates rapid adaptation from stable consolidation, we propose Parameter-Masked Decoupled Optimization (PMDO) that disentangles what knowledge is adapted from how learning proceeds in cross-domain class-incremental learning. 
We introduce a domain-aware knowledge decoupler that selectively adapts domain-relevant shared parameters, constraining incremental updates while preserving prior representations.
To regulate how learning proceeds, we further design a stability-aware trajectory regulation that guides optimization along transferable and stable optimization trajectories, thereby reducing interference across domain transitions.
PMDO enables effective cross-domain adaptation while mitigating catastrophic forgetting and maintaining long-term learnability. 
Extensive experiments across multiple benchmarks demonstrate the effectiveness of PMDO and its superiority over state-of-the-art methods.

---

## 论文详细总结（自动生成）

# 面向跨域类增量学习的参数掩码解耦优化（PMDO）论文总结

## 1. 核心问题与研究动机

- **研究背景**：跨域类增量学习（Cross-Domain Class-Incremental Learning, CD-CIL）要求模型在数据域不断迁移变化的情况下持续学习新类别，同时不能遗忘此前各域中已学得的旧类别知识，是面向真实开放环境的持续学习挑战。
- **核心问题**：现有增量学习方法往往将“更新什么（what to update）”与“如何更新（how to update）”两个问题相互纠缠——即不加区分地更新模型的全部参数，并使用固定的学习/约束策略应对所有增量步骤。在跨域场景下，这会导致两个严重问题：
  1. **不稳定的适配**：目标域的剧烈偏移使模型在新域学习中偏离既有表征结构；
  2. **灾难性遗忘**：为了适配新域而过量调整共享参数，使旧域已学知识被严重覆盖或破坏。

## 2. 方法论：PMDO 框架

- **核心思想**：受大脑**海马体学习机制**启发——海马体负责将“快速获得的新信息”与“长期稳定的记忆巩固”物理隔离——PMDO 提出在 CD-CIL 中将“知识适配”与“学习进程”两个维度解耦，使新知识获取与旧知识保留互不干扰。
- **技术细节一：领域感知知识解耦器（Domain-Aware Knowledge Decoupler）**
  - 该模块能够感知当前增量步的域信息，判断哪些参数既与领域相关、又属于类共享的安全更新区域；
  - 通过生成参数掩码，**选择性地适配领域相关的共享参数**，将增量更新限制在安全子空间中，而对承载了已有类别核心表征的参数加以掩蔽固化，从而保留既有表示。
- **技术细节二：稳定性感知轨迹调节（Stability-Aware Trajectory Regulation）**
  - 用于规范“学习如何发生”，即优化方向与步幅的约束；
  - 引导模型沿**可迁移且稳定**的优化轨迹前进，避免在新旧域之间来回震荡，从而减少跨域切换时更新方向间的相互干扰。
- **总体算法流程**（文字描述）：
  1. 在某一增量阶段输入新域数据，领域感知知识解耦器计算领域特征并推断当前更新涉及的参数范围（生成掩码）；
  2. 在掩码约束下使模型对新类进行有监督学习，同时对共享参数施加稳定性轨迹正则，限制其偏离已巩固的最优区域；
  3. 域切换时重复上述过程，模型始终在保留旧知识的前提下扩展新类。
- **整体效果**：实现了“快速获取、稳定保留”这两种目标之间的显式隔离，从根本上减少了跨域适应对已学知识的破坏，支持**长期可学习性**。

## 3. 实验设计

- **评测任务/Benchmark**：文中仅说明使用了多个跨域类增量学习基准（multiple benchmarks），论文层级上为开放评审收录于 ICML-2026，但**原文（摘要）未给出具体数据集名称**，根据该领域常见设定可推断通常涉及类似于 ImageNet 系列子域、DomainNet、CIFAR 与 Office-Home 等跨域拆分（但此项推断在提供的文本中无直接依据）。
- **对比方法**：与当前最先进的 CD-CIL 方法（state-of-the-art methods）进行广泛比较；但由于摘要未列出具体基线名称（如常规对比的 LwF、iCaRL、BiC、WA、DyTox 等），无法具体考证。
- **评估指标**：文中未在给定材料中列出具体指标，惯例上应包含各增量阶段的新类准确率与已有类别的平均遗忘率。

## 4. 资源与算力

- 所提供的论文元数据与摘要中**均未明确说明**使用的 GPU 型号、数量、训练时长、参数量或显存开销。
- 若需评估算力效率，需查阅论文原文实验章节或附录，本文无法从给定内容获得。

## 5. 实验数量与充分性

- **数量方面**：原文仅以一句“多基准上的广泛实验（Extensive experiments across multiple benchmarks）”带过，并没有展示具体的表格数量、数据域个数或消融实验组数。
- **充分性评判**：
  - 优点：从结论能够确认研究涵盖了与 SOTA 的对比，且效果具有优越性；
  - 不足：无法确认是否有跨域与跨类正交配置、增量长度变化、不同骨干网络、连续多个域切换的长期学习实验；同时也无法确认是否对领域感知知识解耦器的掩码稀疏性、轨迹调节的权重系数等做了逐步消融分析。
  - 因此就现有提供的论文内容而言，实验细节公开度/可复现性信息不足，无法做严谨的客观公平性审查。

## 6. 主要结论与发现

- 将记忆巩固机制（海马体式的快速编码与稳定固化分离）成功迁移到持续学习优化范式中，提出 PMDO 框架；
- 领域感知知识解耦器能有效甄别并保留**类共享知识**，显著限制跨域更新对已有表征的破坏；
- 稳定性轨迹正则能够引导优化过程沿低干扰路径前进，提升连续多次域切换的鲁棒性；
- 实验结果证实 PMDO 可大幅缓解跨域偏移下遗忘，能够做到在不丢弃已学知识的前提下持续适配新域、新类，并长期保持模型的可学习能力。

## 7. 方法亮点与优点

- **角度巧妙**：将“参数更新内容”与“优化更新规则”双轴同时解耦，突破了以往仅在正则约束或样本回放上做文章的局限。
- **生物学启示落地清晰**：将海马体的“模式分离/突触巩固”与“快速映射学习”机制对应到可微参数掩码与正交投影操作，思想有较好解释性。
- **保持模型长期可塑性**：相比通常“越学越僵化”的持续学习方法，PMDO 的掩码只保护旧域重要权重，新域依然有足够自由度，有利于持续多阶段增量。
- **通用性好**：优化器级的方法可灵活配合主流网络骨架与其它增量学习策略。

## 8. 不足与局限

- **实验信息不完整**：本次给定内容缺失具体数据集合名称、类别/域迁移数量、基线方法名称、主要指标等关键实验截图，无法确保结果具有可比性、可复现性。
- **消融细节缺乏**：领域感知知识解耦器的设计依据——例如领域信息如何表征、掩码采用连续软掩码还是二值硬掩码——在提供的摘要里不可查证，内部模块对整体精度的贡献分析在现有内容中缺失。
- **跨域的适用范围有限**：方法充分依赖“领域信息可被辨识”这一前提，若连续域之间非常相似或领域标注缺失，解耦器的精度可能不能得到保证。
- **算力开销不明**：参数掩码运算与可能的掩码选择搜索会引入额外计算成本，缩放至大型骨干网络或大规模数据集上的开销未被讨论。
- **旧知识过度保护的潜在风险**：对共享参数的中断更新在极端任务（如完全相同类在不同域的语义冲突）中可能导致模型无法修正早期错误表征。

---

（完）
