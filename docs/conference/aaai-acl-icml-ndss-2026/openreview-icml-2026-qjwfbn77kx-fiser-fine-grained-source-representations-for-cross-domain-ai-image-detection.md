---
title: "FiSeR: Fine-Grained Source Representations for Cross-Domain AI Image Detection"
title_zh: FiSeR：面向跨域AI图像检测的细粒度源表示
authors: "Shan Zhang, Yongxin He, Mingming Zhang, Huiwen Tian, Lei Ma"
date: 2026-04-30
pdf: "https://openreview.net/pdf/9e76dc58ad80ab020de1935bd9a69f89c1d00268.pdf"
tags: ["query:few-shot"]
score: 8.0
evidence: 跨域图像检测面临域偏移导致性能下降，论文学习可迁移表示以泛化到未见数据集
tldr: 真实世界合成图像检测在域偏移下性能明显下降，原因在于分类头过拟合训练域伪影。FiSeR利用生成器多样性这一结构事实，设计层次化对比学习，既拉开自然与合成特征的距离，又保留生成器身份信息，从而获得更可迁移的表示。该方法使决策准则在未知域上保持稳定，有效缓解跨域检测性能下降，展示了学习可迁移表示对鲁棒性的关键作用。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 真实场景合成图像检测器在域偏移下泛化较差，分类头容易过拟合训练域伪影导致性能下降。
method: 提出层次化对比学习框架，增强自然与合成图像特征的可分性，同时保留生成器身份信息以学习可迁移表示。
result: 在未见数据集上改善了特征可分性并使决策准则更稳定，缓解跨域性能下降。
conclusion: 学习结构化的可迁移表示可使分类边界对域偏移更鲁棒，提升跨域AI图像检测的实用能力。
---

## Abstract
Real-world synthetic image detectors often generalize poorly under domain shift despite strong in-domain performance. Using unsupervised UMAP projections, we find that natural and synthetic features remain partially separable on unseen datasets, yet performance still drops, suggesting that the classification head overfits to training-domain artifacts.
Therefore, the key is to learn more transferable representations so that the decision criterion is more stable and robust to domain shifts. Based on the structural fact that synthetic images are produced by diverse generators, we propose a hierarchical contrastive learning framework that improves the separability between natural and synthetic images while preserving generator identity information. It jointly optimizes (i) a coarse contrastive objective between natural and synthetic images and (ii) a fine contrastive objective among synthetic images using generator identities.
Trained on WildFake, our method achieves an average AUROC gain of +10.22 on cross-domain evaluation over Chameleon, AIGIBench, Community Forensics, and GenImage under the same settings as the strong baseline DIRE. For few-shot adaptation, we freeze the backbone and fit an SVM head on 10 labeled samples per class, improving AUROC by +10.64 on AIGIBench and +17.41 on Chameleon, averaged over 12 widely used detectors. Our code is publicly available at: https://github.com/heyongxin233/FiSeR.

---

## 论文详细总结（自动生成）

# FiSeR：面向跨域AI图像检测的细粒度源表示——论文详细总结

## 1. 核心问题与整体含义

- **背景与动机**：随着扩散模型、GAN等生成技术的快速发展，AI合成图像已深度渗透互联网生态，由此引发虚假信息、版权侵害、社会信任危机等一系列问题。然而，现有的合成图像检测器虽然在“训练域内”表现优异，却在**跨域（domain shift）场景**下——即面对训练时未见过的生成模型或新数据集时——泛化能力急剧下降，严重制约了实际部署价值。
- **关键观察**：论文通过无监督UMAP投影发现，**自然图像与合成图像的特征在新的未见数据集上其实仍然保持部分可分性**，但检测性能依然明显下滑。这一证据表明，性能下降的主要瓶颈不在于特征本身丧失了区分度，而在于**分类头过拟合了训练域特有的伪影（artifacts）**，导致决策准则在域迁移后失效。
- **核心论点**：要提升跨域鲁棒性，关键在于**学习更可迁移的表示（representation）**，而非仅仅改进分类器结构或增加数据增强。如果底层特征本身携带生成器无关的、结构化的可分信息，那么即便是简单的分类头，也能在未知域上保持稳定的决策边界。
- **整体意义**：该项工作将研究视角从“设计更强的检测器”转向“设计更可迁移的表征”，为跨域AI图像检测提供了一条以**表示学习**为核心的新路径，对真实世界开放环境下的伪造内容治理具有重要参考价值。

## 2. 方法论：核心思想、技术细节与流程

### 2.1 核心思想

论文基于一个简单但重要的**结构性事实**：合成图像并非来自同一个生成器，而是由**多种多样的生成器**（如Diffusion系列、GAN系列等）各自独立产生，且不同生成器在特征空间中会形成各自的身份簇。因此，合理的表示应当满足两个层次的结构约束：

- **粗粒度**：自然图像与合成图像在特征空间中必须清晰可分；
- **细粒度**：不同生成器的合成图像应当保留各自的身份信息，形成有结构的簇内分布。

### 2.2 技术框架：层次化对比学习

基于上述洞察，论文提出了 **FiSeR（Fine-Grained Source Representations）**，即一个层次化对比学习框架，核心由两个互补的对比目标构成，并联合优化：

- **粗粒度对比目标（Coarse Contrastive Objective）**  
  拉大自然图像与合成图像之间的特征距离，使两者在表示空间中形成区隔明显的两大分布。这一目标保障了特征在“自然 vs 合成”这一核心判别维度上的可分性。

- **细粒度对比目标（Fine Contrastive Objective）**  
  以**生成器身份（generator identity）** 为监督信号，约束同源生成器的合成图像在特征空间中互相靠近、不同生成器的合成图像互相远离。这一目标保留了合成图像内部的结构信息，使模型学习到的特征不是仅针对特定生成器的浅层伪影，而是具有更一般化语义的深层表征。

- **联合优化**：两个目标在同一骨干网络（backbone）上协同训练。粗粒度约束保证了高层判别方向不偏移，细粒度约束则通过保留生成器身份的更多结构，增强表征的丰富度和迁移性——两者相互作用，共同抑制分类头对训练域伪影的过拟合。

### 2.3 训练与适配流程（文字化描述）

1. **预训练阶段**：在源域数据集（如WildFake）上，以层次化对比学习为目标训练骨干特征提取器，得到可迁移的通用表示空间。
2. **线性评估/检测阶段**：在冻结骨干的基础上，训练一个简单的线性分类头完成自然/合成二分类判别。
3. **少样本适应阶段（Few-shot Adaptation）**：冻结预训练骨干，仅使用**每类10个带标签样本**训练一个SVM分类头，即可快速适配新数据集。

## 3. 实验设计

### 3.1 数据集与Benchmark设定

- **源域训练数据**：WildFake数据集（用于预训练特征提取器及分类头）。
- **跨域评估数据**：
  - **Chameleon**
  - **AIGIBench**
  - **Community Forensics**
  - **GenImage**

这些数据集涵盖了不同生成模型、不同图像类别、不同处理管线，构成了测试跨域泛化能力的多样基准集合。

### 3.2 对比方法与基准

- **主对比基准**：以强基线 **DIRE** 为参照，在相同实验设置下进行跨域评估。
- **少样本适应对比**：论文在AIGIBench和Chameleon上，报告了其方法对 **12种广泛使用的检测器** 的平均AUROC提升，表明FiSeR学习到的表示可作为一种通用的骨干特征，赋能多种下游检测方法。

### 3.3 主要评价指标

- **AUROC**（ROC曲线下面积），用于衡量检测器在正负类别上的排序能力，是伪造检测领域公认的标准指标。

## 4. 资源与算力

- 论文提供的原文内容中**未明确披露**训练所使用的具体GPU型号、数量、训练时长、显存占用等硬件与算力信息。
- 也**未提及**预训练总耗时或对比方法复现所需的算力投入。
- 若读者需要复现该方法，算力需求只能从方法本身推断（对比学习训练通常依赖单卡或多卡现代GPU），但原文没有给出精确数字。

## 5. 实验数量与充分性

- **主跨域实验**：在4个未见数据集（Chameleon、AIGIBench、Community Forensics、GenImage）上进行，相较于DIRE平均AUROC提升+10.22，覆盖面较广且数据集多样性较好。
- **少样本适应实验**：在AIGIBench和Chameleon两个数据集上，以每类10样本的设定，对12种已有检测器报告平均AUROC提升（AIGIBench +10.64、Chameleon +17.41），验证了所学表征的通用性与即插即用能力。
- **可视化实验**：利用UMAP进行特征空间投影，从经验层面验证了“特征仍然可分、性能却下降”的问题诊断，为方法设计提供了实证依据。
- **充分性评估**：
  - **优点**：实验横跨多个主流跨域检测基准，且少样本实验评估范围覆盖12种检测器，对比幅度大，结论具有较好的说服力；在统一设置下与DIRE对照，具有相对的公平性。
  - **不足**：论文摘要和元数据中未见清晰的**消融实验**描述（如单独去除粗粒度/细粒度目标的效果、不同骨干网络的影响、不同少样本数量的敏感性等），也未见在**更大规模真实互联网数据**上的验证。此外，训练集仅依赖WildFake单一源域，源域多样性对结果的影响尚不明确。

## 6. 主要结论与发现

- 跨域AI图像检测的性能下降，根源不在于特征不可分，而在于分类头过拟合了训练域特有伪影——UMAP可视化为这一论断提供了直接证据。
- 通过**层次化对比学习**——在拉开自然/合成距离的同时保留生成器身份信息——学到的特征表示具有更强的跨域可迁移性，使得下游分类准则在未知数据集上仍然稳定。
- FiSeR方法在4个跨域数据集上较DIRE取得平均+10.22的AUROC增益；在少样本条件下（每类10样本）冻结骨干+SVM，能显著提升AIGIBench与Chameleon上12种检测器的检测性能，展示了其作为通用预训练表征的潜力。
- 最终结论：**结构化的可迁移表示，比复杂的分类头更能有效对抗域偏移**，这为跨域伪造检测提供了新的研究范式。

## 7. 优点

- **问题诊断精准**：通过无监督特征的UMAP可视化准确定位了性能损失的真正来源（分类头过拟合）而非表象（特征不具备可分性），方法论上逻辑严密。
- **方法设计巧妙**：利用“合成图像由多样生成器产生”这一领域内普遍存在的结构性事实，设计粗+细两层对比目标，在无额外标注负担的前提下实现更丰富的监督信号，思路新颖且自然。
- **关注特征而非模型**：将优化重心从分类器转移到骨干表征，契合了跨域泛化的本质需求，也为后续研究者提供了可借鉴的范式。
- **迁移通用性强**：少样本实验横跨12种检测器，验证了FiSeR孪生的特征可以嵌入既有检测框架并带来增益，具有较强的实用价值。
- **完整开源**：代码已公开于GitHub，研究可复现性高。

## 8. 不足与局限

- **计算资源缺乏透明性**：未报告实验所需的GPU配置和训练开销，对资源受限的研究团队不友好。
- **消融实验信息缺失**：从已有信息中无法判断粗粒度目标和细粒度目标各自的独立贡献、二者是否存在最优平衡比、以及该方法对骨干结构或对比学习超参数的敏感性。
- **源域单一性**：仅在WildFake上进行预训练。不同源域（如GenImage作为训练源域）对迁移效果的影响有待考察；源域本身的规模与多样性是否足以支撑“通用表示”仍需更多验证。
- **评测局限**：跨域评测虽然使用了4个公开数据集，但仍然属于学术基准环境，尚未在真实社交媒体平台（带压缩、截屏、二次编辑等）的复杂退化条件下进行验证，应用边界尚未厘清。
- **潜在偏差风险**：由于特征是面向“生成器身份”结构化的，如果新出现的生成器与已有生成器在特征分布上差异过大，细粒度层次的增益是否会减弱甚至消失，仍是未回答问题；论文也未对最坏情况下的泛化失败模式展开讨论。
- **元数据中标注了与few-shot相关的tag**，但摘要中少样本实验仅覆盖2个数据集，样本量有限，少样本适配的稳健性结论需要更大范围的验证。

（完）
