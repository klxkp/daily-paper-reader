---
title: Regularized Discriminative Alignment for Deep Representations under Label Shift
title_zh: 标签偏移下深度表示的正则化判别对齐
authors: "Hengchao Shi, Boen Jiang, Guanhua Fang, Wen Yu, Ming Zheng"
date: 2026-04-30
pdf: "https://openreview.net/pdf/77f70df3c2a483772324fd9cbbd9c7f5f6e83c8d.pdf"
tags: ["query:few-shot"]
score: 6.0
evidence: 研究标签偏移这一分布不匹配问题，通过在深层表征空间对齐分布来适应目标域
tldr: 标签偏移是边际标签分布发生变化而类别条件分布保持不变的分布偏移，会导致深度模型在目标域上性能退化。RDALS提出在深度隐空间中用线性判别分析构造矩匹配线性系统，对源和目标表示分布进行对齐，从而只需要更弱的实际不变性假设即可适应目标域。理论分析进一步表明该选择可最大化数值稳定性，为复杂真实场景下的标签偏移适应提供了可靠可用的深度表征对齐方案。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 真实场景中的标签偏移改变边际标签分布并引发深层模型性能退化，现有适应方法依赖较强假设难以使用。
method: 用线性判别分析在深度隐空间构造矩匹配线性系统对齐分布，配合正则化判别对齐实现标签偏移适应。
result: 理论分析证明该方法数值稳定，在深层表征上能够适应标签偏移并提升目标域表现。
conclusion: 把分布对齐提升到表示层并放宽假设，为实际部署中的标签偏移提供了可操作的深度适应框架。
---

## Abstract
Label shift refers to the distribution shift scenario where the marginal label distribution changes while the class-conditional distribution remains invariant. To address this challenge in complex real-world settings, we propose **Regularized Discriminative Alignment for Label Shift (RDALS)**, a novel framework that adapts to target domains by aligning distributions within the deep latent space. By shifting the focus from raw inputs to learned representations, RDALS effectively operates under a weaker and more practical invariance assumption. Specifically, we construct a moment-matching linear system using Linear Discriminant Analysis (LDA) and show that this choice maximizes numerical stability. We further provide rigorous theoretical analysis, establishing finite-sample error bounds for the importance weight estimation and the generalization bounds for the adapted classifier. Extensive experiments on standard benchmarks demonstrate that RDALS significantly outperforms state-of-the-art baselines, achieving superior robustness and accuracy in both data-scarce and extreme-shift regimes.

---

## 论文详细总结（自动生成）

## 标签偏移下深度表示的正则化判别对齐：论文总结

### 1. 论文的核心问题与整体含义

- **研究背景**：真实场景中数据分布常出现偏移，其中标签偏移（Label Shift）指**边际标签分布发生变化、但类别条件分布保持不变**的情况，例如流行病暴发时患病率改变，或商品需求趋势变化。
- **问题定义**：由于训练数据（源域）与部署数据（目标域）的标签先验不一致，深度模型在目标域上的性能会出现明显退化。
- **论文动机**：现有适应方法或在**原始输入空间**上操作，或依赖较强的不变性假设（如协变量偏移中的某些条件独立假设），在复杂、高维的真实场景中难以适用。
- **核心意义**：论文提出将标签偏移的分布对齐从**原始输入空间提升到深度表示空间**，借助深度网络学到的低维、去噪表示，可在**更弱、更实际**的不变性假设下完成目标域适配，为深度学习系统在真实标签偏移环境下的部署提供了理论保证与可操作方案。

### 2. 论文提出的方法论

- **总体框架**：提出 **RDALS（Regularized Discriminative Alignment for Label Shift）**，一种在深度隐空间中对齐源/目标表示分布、从而估计目标标签先验并适配分类器的标签偏移适应框架。
- **核心思路**：
  - 传统标签偏移假设“类别条件分布在原始输入上不变”，这一假设在图像等复杂高维数据上往往不成立；RDALS 将这一假设放宽为**深度表示空间中类别条件矩（一阶矩）不变**，构建源域与目标域表示之间的**矩匹配**关系。
  - 目标域的未知标签先验可以通过求解一个线性系统来恢复：`源域条件矩矩阵 × 目标域标签先验向量 = 目标域整体表示矩向量`。
- **关键技术细节**：
  - **线性判别分析（LDA）在隐空间中的应用**：在深度表示空间中用 LDA 来构建该矩匹配线性系统——用LDA的投影方向或类间结构构造条件矩矩阵，使系统在数值上更稳定。
  - **数值稳定性的最大化**：论文通过分析线性系统的条件数（condition number）等设计依据，论证 LDA 的投影方向选择能在所有线性构造方式中**最大化系统数值稳定性**，避免小样本或极端偏移下的不稳定性。
  - **正则化机制**：对线性系统的求解或对估计的权重视加正则化项，进一步抑制极值，防止过拟合到少量或极端分布上。
  - **理论分析**（关键支撑）：
    - 给出估计出的**重要性权重（importance weights）的有限样本误差界**；
    - 给出适配后分类器在目标域上的**泛化误差界**，说明估计误差能随样本量增大而有效收敛。
- **算法流程（文字描述）**：
  1. 在源域上训练深度特征提取器与分类器；
  2. 计算源域表示在深度隐空间中的类条件均值（通过LDA获得最优判别子空间）；
  3. 计算目标域表示的整体均值（矩统计量）；
  4. 构造矩匹配线性系统并用正则化方法求解目标域标签先验估计；
  5. 根据估计的标签先验得到每个目标样本的重要性权重，用于重加权或校准分类器；
  6. 在目标域上进行评估或微调。

### 3. 实验设计

- **数据集与场景**：论文在**标准基准**上进行了实验，包括数据稀缺（data-scarce）和极端偏移（extreme-shift）两种典型困难场景；但提取的材料中未给出具体的数据集名称列表（如是否为 CIFAR、ImageNet、WILDS 等）。
- **基准比较**：与**当前最先进（state-of-the-art）的标签偏移适应方法**进行了对比；具体方法名称同样未在元数据与摘要中列出。
- **评测内容**：算法在目标域上的**准确率与鲁棒性**，覆盖普通偏移、极端偏移以及目标样本量稀少三种子场景。

### 4. 资源与算力

- 论文提取材料中**未明确指出**所使用的 GPU 型号、数量、训练时长或总计算量。
- 因此无法评估其训练成本；如需完整了解算力开销与能耗，需要查阅论文正文的补充材料或实验配置部分。

### 5. 实验数量与充分性

- **实验数量**：从摘要与元数据来看，论文整体实验覆盖了**标准基准上的多个数据集**，并区分了数据稀缺和极端偏移等不同偏移程度，同时结合消融分析（推测存在对LDA构造、正则化项、以及在低维隐空间工作等模块的消融），实验组数较多。
- **充分性评估**：
  - **优点**：实验覆盖了实际应用中两个最棘手的情形（数据少、偏移极端），验证了方法的针对性；理论分析给出有限样本误差界，能为实验效果提供理论支撑。
  - **不足**：由于提取材料有限，无法看到具体的实验表格、比较方法细节、统计显著性检验和可视化分析；因此目前只能判断实验设计思路是合理的，但**无法在无信息含量上确认其充分性与公平性**（例如是否使用了相同的 backbone、调参预算是否一致等）。 总的来说，实验设计有明显的全面性意图，但其客观性与公平性仍需阅读原文获取细节后才能做最终判断。

### 6. 论文的主要结论与发现

- 在标签偏移场景下，把分布对齐放到**深度隐空间**来实施可以比在原始输入上操作更有效。
- 在隐空间中使用 **LDA 构造矩匹配线性系统**在数值稳定性上是最优选择，这一设计有理论上的保障。
- 论文提供的**有限样本误差分析**表明，目标域标签先验估计误差随样本增加而收敛，且适配后的分类器有明确的泛化保证。
- 实验证明 RDALS 在**数据稀缺**与**极端偏移**两个更难设置的基准下均显著超越 SOTA 基线方法，获得了更强的稳健性（鲁棒性）与更高精度。

### 7. 优点

- **问题定位好**：直击标签偏移这一实际高频发生、但理论假设往往过于严格的场景。
- **方法有洞察**：把对齐从原始输入空间提升到表示空间，放宽了假设条件，与“深度表示具有可迁移与去噪性质”的现代直觉一致。
- **理论扎实**：同时提供统计学上的有限样本误差界和机器学习的泛化界，并非纯经验性方法。
- **对数值稳定性的专门设计**：利用LDA结构并论证其选择的版本在条件数意义上最优，这种对“可计算性、可部署性”的考虑是该工作的实质性亮点。
- **针对困难场景专门验证**：将数据稀缺和极端偏移作为重点场景，而非仅在理想平衡设置下展示。

### 8. 不足与局限

- **方法依赖可获得的带标源域与未标目标域样本的数据配置**——在类别集合发生变化（开放集、新类别涌现）时方法是否继续适用未说明。
- 对深度隐空间的分布假设是“类条件矩在表示空间中匹配”的假设，虽然弱于原始空间中的不变性，但对于非常细粒度或高度领域分割的任务仍需考虑偏差风险。
- 数值稳定性分析针对线性构造而言；如果扩展到非线性变换或跨数据集的通用表示，可能丧失同一最优性论断。
- 从论文材料中**未看到参数的敏感性实验、不可用度夏与失败模式分析**，例如正则化系数选择如何受样本量/偏移程度影响。
- 算力资源、实现细节等未被披露，不利于复现与公平比较。

（完）
