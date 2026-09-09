---
title: "Rethinking the Flow-based Gradual Domain Adaptation: A Semi-Dual Optimal Transport Perspective"
title_zh: 流式渐进域适配再思考：半对偶最优传输视角
authors: "Zhichao Chen, Zhan Zhuang, Yunfei Teng, Hao Wang, Fangyikang Wang, Zhengnan Li, Tianqiao Liu, Haoxuan Li, Zhouchen Lin"
date: 2026-04-30
pdf: "https://openreview.net/pdf/80183c65651f06969943f9119a5971ef2c0cdeb9.pdf"
tags: ["query:few-shot"]
score: 8.0
evidence: 通过中间域将模型从源域逐步迁移到目标域以缓解分布偏移
tldr: 渐进域适应通过中间域将模型从源域平滑迁移到目标域，然而真实中间域常缺失或无效，需要合成中间样本。现有流模型以样本级似然训练会丢弃有用信息，影响适应效果。本文提出熵正则化的半对偶最优传输方法，直接从样本构造中间分布，避免流模型信息损失，以更稳健地缓解源域与目标域间的分布偏移。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 流式渐进域适应的似然估计会丢弃中间域信息，且合成中间域的方式不够有效。
method: 提出熵正则化半对偶最优传输机制，直接从样本构造中间域，替代传统样本级似然的流训练。
result: 避免训练中的信息丢弃，在源到目标域分布偏移下获得更优的渐进适应表现。
conclusion: 为渐进域适应中的中间域合成与模型迁移提供新的最优传输理论视角。
---

## Abstract
Gradual domain adaptation (GDA) aims to mitigate domain shift by progressively adapting models from the source domain to the target domain via intermediate domains. However, real intermediate domains are often unavailable or ineffective, necessitating the synthesis of intermediate samples. Flow-based models have recently been used for this purpose by interpolating between source and target distributions. Notably, their training typically relies on sample-based log-likelihood estimation, which can discard useful information and thus degrade GDA performance. The key to addressing this limitation is constructing the intermediate domains via samples directly. To this end, we propose an $\underline{\text{E}}$ntropy-regularized $\underline{\text{S}}$emi-dual $\underline{\text{U}}$nbalanced $\underline{\text{O}}$ptimal $\underline{\text{T}}$ransport (E-SUOT) framework to construct intermediate domains. Specifically, we reformulate flow-based GDA as a Lagrangian dual problem and derive an equivalent semi-dual objective that circumvents the need for likelihood estimation. However, the dual problem leads to an unstable min–max training procedure. To alleviate this issue, we further introduce the entropy regularization to convert it into a more stable sequential optimization procedure. Based on this, we propose a novel GDA training framework and provide theoretical analysis in terms of stability and generalization. Finally, extensive experiments are conducted to demonstrate the efficacy of the E-SUOT framework.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义

- **研究背景**：渐进域适应（Gradual Domain Adaptation, GDA）旨在通过一系列中间域，将模型从源域逐步迁移到目标域，从而有效缓解源域与目标域之间较大的分布偏移（domain shift）。
- **核心痛点**：
  - 现实场景中**真实中间域往往不可得**，或者即便存在也未必能有效帮助模型迁移，因此需要**合成中间样本**。
  - 近期流模型（flow-based models）被用于此目的，通过在源域与目标域分布之间插值来构建中间域。然而，流模型的训练通常依赖**基于样本的对数似然估计**，这种训练方式会**丢弃有用的分布信息**，进而限制 GDA 的性能表现。
- **核心问题**：如何**绕过样本级似然估计的信息丢弃问题**，更直接、更稳健地从样本构造中间域。

## 2. 提出的方法论

- **核心思想**：直接从样本构造中间域，不依赖流模型的样本级似然训练，从而避免信息丢失。
- **具体框架**：提出 **熵正则化半对偶非平衡最优传输（E-SUOT, Entropy-regularized Semi-dual Unbalanced Optimal Transport）** 框架，用于构造中间域。
- **关键技术细节**：
  1. **流式 GDA 重写为拉格朗日对偶问题**：作者将流式 GDA 重新表述为一个拉格朗日对偶问题，推导出等价的**半对偶目标函数**，从而绕开对似然估计的需求。
  2. **引入熵正则化**：由于原始对偶问题会带来**不稳定的最小-最大（min-max）训练过程**，作者引入熵正则化将之转化为**更稳定的序列化优化过程**。
  3. **新训练框架**：基于上述推导，提出了一种**新型 GDA 训练框架**，并给出了**稳定性和泛化性方面的理论分析**。
- 整体方法从**最优传输视角**切入，为 GDA 中中间域合成与模型迁移提供了新思路。

## 3. 实验设计

- 原文摘要仅提到进行了 **“extensive experiments”（广泛实验）** 以验证 E-SUOT 框架的有效性，并未在摘要中列出具体数据集、基准或对比方法。
- **Benchmark**：未在提供文本中明确具体使用的基准数据集。
- **对比方法**：文本中未详细列举对比对象，推测应与现有 GDA 方法（如其他基于流模型的中间域合成方法、传统 GDA 方法等）进行比较。

## 4. 资源与算力

- **论文提供的文本中未明确说明**所使用的 GPU 型号、数量、训练时长等算力信息。
- 由于可见材料仅为摘要层面，缺少实验章节的算力披露；若需了解详细资源信息，需查阅论文正文的实验章节。

## 5. 实验数量与充分性

- 摘要中声称进行了大量实验，但可见部分**没有给出具体实验数量**。
- 缺少对**消融实验**（如熵正则化的贡献、不同正则化系数的影响、理论结果的验证等）的细节描述。
- 就当前可见信息而言，**难以全面评估实验的充分性与公平性**；但论文被 ICML-2026 接收且评审分数 8.0 分，一定程度上侧面反映了实验设计获得了审稿人的认可。
- 完整的实验充分性判断需要依赖论文正文及附录中提供的具体数据与实验设置。

## 6. 主要结论与发现

- **核心结论**：基于熵正则化的半对偶非平衡最优传输（E-SUOT）框架避免了流模型在训练中因样本级似然估计导致的信息丢弃问题，在源域到目标域分布偏移的场景下取得了更优的渐进域适应性能。
- **理论贡献**：为渐进域适应中的中间域合成与模型迁移提供了新的**最优传输理论视角**。
- **方法贡献**：将不稳定的对偶 min-max 训练过程转化为稳定的序列化优化，提升了方法的可训练性和稳定性。

## 7. 优点

- **问题切入精准**：指出现有流式 GDA 以样本级对数似然为训练目标会丢弃有用分布信息，切中方法论要害。
- **理论视角新颖**：将 GDA 重写为最优传输的拉格朗日对偶问题，从理论上重新定义了中间域构造，避免了先合成中间样本再训练模型的割裂流程。
- **工程可控性强**：引入熵正则化将不稳定的 min-max 过程变为稳定的序列优化，兼顾理论与实际可训练性。
- **理论保障**：提供了稳定性和泛化性的理论分析，使方法不仅具有经验支撑，也具有理论依据。
- **评审认可度高**：获得 ICML-2026 接受，OpenReview 分数 8.0，说明整体工作质量较受认可。

## 8. 不足与局限

- **信息可见性有限**：提供的文本仅为 Abstract，无法获取方法细节和完整的实验内容，对实验深度和具体效果难以全面评估。
- **实验细节缺失**：缺少具体数据集信息、基准设置、对比方法及统计显著性检验等信息。
- **算力资源未披露**：没有说明训练所需的计算资源，不利于可重复性评估。
- **潜在偏差风险**：作为工作投稿方提供的元数据（如 motivation、method、result 等），可能存在一定程度的**自我评价偏乐观倾向**。
- **应用限制**：总结中未讨论方法的适用范围和限制性问题，例如对高维图像数据是否稳定、熵正则化系数敏感性、以及对长距离分布偏移的有效性边界等。
- 从元数据标签来看，该论文被标为 **query:few-shot**，但文本摘要中未直接讨论 few-shot 场景，若其在实验中使用 few-shot 设置，那么该元数据标签与摘要表述之间的衔接也值得关注。

---

（完）
