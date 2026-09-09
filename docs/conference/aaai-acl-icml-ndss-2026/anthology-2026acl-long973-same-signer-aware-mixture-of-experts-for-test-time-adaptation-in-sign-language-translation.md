---
title: "SAME: Signer-Aware Mixture-of-Experts for Test-Time Adaptation in Sign Language Translation"
title_zh: SAME：面向手语翻译的基于手语者感知专家混合的测试时自适应
authors: "Lujia Yang, Weicai Yan, Yongbo He, Qifei Zhang, Tao Jin, Jinshan Zhang, Meng Xi, Jianwei Yin"
date: 2026-07-01
pdf: "https://aclanthology.org/2026.acl-long.973.pdf"
tags: ["query:few-shot"]
score: 5.0
evidence: 面向手语翻译提出测试时适应，无需目标标注即可应对手语者、光照和背景等域偏移
tldr: 手语翻译在真实部署中会因为手语者、光照和背景等差异出现域偏移，监督微调又受限于标注样本稀少。文章提出首个面向手语翻译的测试时适应方法SAME，利用考虑手语者身份的专家混合结构，在不需要标签的情况下快速适应域偏移，克服现有无监督方法依赖批统计或长时适应的局限。该工作将测试时适应从图像分类推广到更复杂的序列翻译任务，展示了其在低资源跨域场景的适用性。
source: ACL-2026-Long
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-long/anthology-2026acl-long973/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 783, \"height\": 531, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026acl-long973/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1638, \"height\": 663, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026acl-long973/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 791, \"height\": 431, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026acl-long973/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 803, \"height\": 337, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026acl-long973/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 804, \"height\": 859, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026acl-long973/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1511, \"height\": 509, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026acl-long973/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 695, \"height\": 431, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026acl-long973/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1468, \"height\": 498, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026acl-long973/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 838, \"height\": 300, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long973/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1606, \"height\": 580, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long973/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1681, \"height\": 697, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long973/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 762, \"height\": 363, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long973/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1046, \"height\": 433, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long973/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1432, \"height\": 362, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long973/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 810, \"height\": 460, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long973/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 630, \"height\": 317, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long973/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 775, \"height\": 365, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long973/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1130, \"height\": 475, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long973/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1150, \"height\": 558, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long973/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 569, \"height\": 361, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long973/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1652, \"height\": 2355, \"label\": \"Table\"}]"
motivation: 手语翻译存在手语者、光照、背景等分布变化，监督微调标注稀缺，现有无监督适应方法不适用。
method: 提出测试时适应框架SAME，基于手语者感知的专家混合模型，无需标签即可快速适配分布偏移。
result: 首次在手语翻译中实现无需标注的快速域适应，优于需要批统计或长时适应的已有方法。
conclusion: 证明测试时适应能有效处理手语翻译域偏移，为标注受限的序列跨域任务提供了新范式。
---

## Abstract
Sign language translation (SLT) is essential for bridging communication between the deaf and hearing communities, but real-world deployment suffers from domain shift such as signer variability, lighting, and background changes. Supervised fine-tuning is impractical due to limited labeled data, and existing unsupervised adaptation methods require batch statistics or long adaptation. We introduce Test-Time Adaptation (TTA) for SLT, enabling rapid adaptation to domain shift without the need for labeled data. To the best of our knowledge, this is the first study to explore TTA in SLT. Existing TTA methods predominantly focus on image classification tasks and lack a comprehensive strategy for handling domain shift in SLT. In response, we introduce SAME, a plug-and-play, signer-aware Mixture-of-Experts (MoE) TTA architecture for SLT. SAME inserts lightweight MoE modules after multiple encoder layers. Gates are conditioned on signer features and stabilized with unsupervised regularizers, effectively decoupling domain shift across encoder depths while enabling personalized adaptation. Experiments show that SAME outperforms existing TTA methods and can enhance the capabilities of multiple SLT models.

---

## 论文详细总结（自动生成）

### 论文总结：SAME——面向手语翻译的测试时自适应方法

#### 1. 论文的核心问题与整体含义

- **研究动机与背景**：手语翻译（SLT）是连接聋人与听力社会的重要技术。然而在真实部署中，SLT 模型会遭遇显著的域偏移（domain shift），表现为：
  - 手语者的个体差异（手型、动作速度、运动范围等）；
  - 光照条件变化；
  - 背景杂乱或动态变化。
- 上述域偏移会导致模型翻译质量显著下降，这在辅助场景中不可接受。
- 传统的应对方案，如使用目标域标签进行有监督微调，在真实部署中并不现实——因为标签获取代价高昂且难以实时处理。
- 现有的无监督域适应方法也存在明显限制：
  - 依赖批统计信息（batch statistics），在流式/在线推理场景中不可用；
  - 需要较长时间的自适应过程，引入不稳定因素。
- **论文的整体含义**：该工作是第一个将测试时自适应（Test-Time Adaptation, TTA）引入 SLT 的研究。目标是在不借助目标域标签的前提下，让预训练的 SLT 模型在推理阶段根据无标注样本快速适应新的手语者及偏离分布的数据，缓解域偏移问题。这一研究为标注严重受限的序列跨域任务——尤其是有复杂动作语义的SLT——提供了处理域偏移的全新范式。

#### 2. 论文提出的方法论

- **核心框架**：SAME（Signer-Aware Mixture-of-Experts，手语者感知的专家混合架构）——一个即插即用的 TTA 方法。
- **关键技术步骤**：
  1. **深度级域偏移解耦**：
     - 在 SLT 编码器的每一层之后插入轻量级 SAME 模块。
     - 每个 SAME 由多个专家 + 一个直通分支构成。
     - 域偏移被分解到不同编码器深度和不同专家路径上，浅层与深层特征以互补方式各自适应。
  2. **轻量 LoRA 专家设计**：
     - 每个专家以低秩矩阵 A_j ∈ R^{r×d} 和 B_j ∈ R^{d×r} 实现 LoRA 适配器。
     - 对输入表示 h_t 做变换 e_j(h_t) = (α/r)·B_j·A_j·h_t。
     - 超参数 r 为低秩维度，α 为缩放因子，防止优化不稳定。
  3. **稀疏手语者感知路由**：
     - 通过预训练 MLP 提取 512 维的手语者特征向量 s（在 TTA 中冻结，作为稳定的先验）。
     - 门控网络融合隐层状态 h_t 与手语者特征 s，生成 TopK 稀疏路由：
       - z(h_t, s) = W_g·[h_t; s] + b_g
       - G(h_t, s) = Softmax(TopK(z(h_t, s) + R_noise, k))
     - 支持帧级（frame-wise）路由，不同时间帧可激活不同专家，以捕捉手语中不同语素（gloss）转换等细粒度时变特征。
  4. **有监督 MoE 初始化**：
     - 初始化阶段使用小规模有标签源域子集来训练 SAME。
     - 优化目标包括 SLT 交叉熵任务损失 L_SLT 与专家多样性损失 L_div：
       - L_div 通过构造专家输出的协方差矩阵与单位矩阵的 Frobenius 差来鼓励专家之间正交互补，防止专家坍缩。
     - 总初始化损失：L_init = L_SLT + λ_div·L_div
  5. **三种无监督 TTA 目标**：
     - **熵最小化（EM）**：鼓励模型产生置信度高的预测（降低输出分布熵）；
     - **最小类别混淆（MCC）**：最小化目标域不同类别输出之间的混淆程度，增强判别性；
     - **伪标签监督（PLS）**：将冻结的源模型输出的伪标签作为软约束，避免模型偏离源域太远、发生灾难性遗忘。
     - 总 TTA 损失：L_TTA = λ_EM·L_EM + λ_MCC·L_MCC + λ_PLS·L_PLS

#### 3. 实验设计

- **数据集**：三个主流手语翻译 benchmark：
  1. **Phoenix-2014T**：德国手语气象播报视频（带词注释与德语文本）；
  2. **CSL-Daily**：大规模中国手语日常对话数据；
  3. **How2Sign**：美国手语多模态数据集（搭配 / 对应英文句子）。
- **域偏移设置**：以手语者为划分依据，构建源域/目标域：
  - Phoenix-2014T：signer 1–6 为源域（6,120 样本），signer 7–9 为目标域（2,091 样本）；
  - CSL-Daily：signer 0–6 为源域（15,388 样本），signer 7–9 为目标域（5,266 样本）；
  - How2Sign：signer 5–8 为源域（28,655 样本），signer 1–4 & 9–11 为目标域（6,474 样本）。
- **评估指标**：BLEU-1 到 BLEU-4，取多个目标手语者的平均值。
- **对比的基准 TTA 方法**：
  - 优化类：TENT、EATA、SAR、AEO；
  - 模型类：CoTTA、BeCoTTA。
- **适配的 SLT 模型**（验证即插即用性）：
  - 基于手语词注释：SLRT、MMTLB、TS-SLT；
  - 无词注释：GFSLT-VLP、Sign2GPT、GloFE-VN、SLT-IV、Uni-Sign。

#### 4. 资源与算力

- 论文仅明确提到一句话：“All TTA experiments are conducted on a single NVIDIA RTX 4090 GPU”。
- **未明确报告**：（a）SAME 模块初始化阶段所需的具体训练时长；（b）每个数据集的运行耗时明细；（c）在 RTX 4090 上完成全部实验所需的总 GPU 小时数；（d）不同基线方法的具体能耗开销；
- 其他为公平性所做的实验（对比模型整合、9 个 SLT 原框架的重新训练）也需要大量算力，但具体参数未说明。

#### 5. 实验数量与充分性

- **总体实验数量**：非常全面，覆盖了多数据集、多基线、多主干、多模块消融：
  - 主干对比：3 个数据集 × 多个 SLT 架构（基础 transformer baseline 与 9 个既有模型框架）；
  - 各种消融：适应部位消融（表 4）、组件消融（表 5）、损失消融（表 6）、Top-k 消融（表 7）、超参数（专家数与 LoRA 秩）敏感性分析、手语者特征鲁棒性分析、损失权重敏感性等；
  - 额外提供了定性案例分析、专家行为可视化、跨数据集特征分布可视化等。
- **充分性评估**：
  - **优点**：考虑了离线指标（BLEU）、推理延迟和计算量（GFLOPs）；对比了不同 TTA 方法（源模型一致的基准）和多个现代 SLT 框架（验证即插即用通用性）。
  - **不足**：高成本消融实验（表 5、表 6、表 7）仅在 Phoenix-2014T 上做单次运行，未说明跨数据集的可迁移性。三个数据集的总体平均 BLEU 都只取三粒种子的均值，没有统计显著检验（如引导置信区间）；来自 How2Sign baseline 的评估设置相对更简单，与真实复杂 ASL 场景不可直接对应；如何2Sign 的特殊源-目标分配跳过了 signer 0 和 signer 12，是否有潜在选择偏见未讨论。
  - **公平性**：使用统一的 transformer 基线及相同划分、相同的标准化设置，公平性较好；在复现既有 SLT 方法时，作者声明所有模型都使用相同划分重新训练，规避了权重的混淆因素，是合理的。
  - 综合来看，实验丰富度高，但若在更多数据集上利用均值±方差、统计显著性及多样性更强的源/目标划分做系统验证，则结论会更牢靠。

#### 6. 论文的主要结论与发现

- SAME 是第一个将测试时自适应成功应用到手语翻译场景的方法，在所有对比 TTA 基线上一致地提升 BLEU-1～BLEU-4 分数：
  - Phoenix-2014T 上比源模型 BLEU-4 提升 2.73；
  - CSL-Daily 上提升 2.21。
- SAME 具备跨 SLT 架构的即插即用普适性：
  - 覆盖从简单 transformer baseline 到复杂 SLT 框架（TS-SLT、Uni-Sign 等）都产生正向影响；
  - 无注释模型（如 GFSLT-VLP）获得的提升幅度尤其可观。
- 稀疏 MoE 框架的有效性充分体现了：

  - 对多个 LoRA 专家、手语者感知门控和有监督初始化等各自环节的消融及验证，表明他们缺一不可；
  - 深度级设计的洞见（仅调归一化层效果较弱、全文微调耗时长）是实现轻量级 TTA 的关键。
- 未加监督的目标函数方面，EM、MCC、PLS 相互补充（去掉任一个都会明显下降）。
- 专家行为可视化表明：
  - 不同手语者的专家使用子集有显著差异；
  - 不同帧可激活不同专家，说明该机制能够根据手语中不同词素/动作模式自适应选择专家；
  - 使用 top-1 路由能够最稳定地适配，增加 K 值反而削弱专家专一性。

#### 7. 优点

- **领域填补性**：首次提出 SLT 的测试时自适应能力，较好地将 TTA 从视觉分类延伸到有潜在时序与语义复杂性的序列生成问题。
- **方法论上高度自洽**：设计方案框架完整顺畅，即
  - 域偏移在编码器深度和专家路径上进行双维解耦；
  - 手语者信息作为条件进入路由，配合冻结预训练骨干保证稳定域适应。
- **低参数量、高效率性**：

  - SAME 仅调整 0.63% 的参数；
  - 推理延迟显著低于 SAR 和 BeCoTTA，GFLOPs 也为可接受水平。
- **强收敛能力/高稳定性**：与全文微调（适应过程需要 15 步才能稳定）不同，SAME 只需 5 步即可得到最优结果。
- **即插即用和大面积跨模型验证**：在跨手语（德语、中文、英语）和跨 SLT 架构（词注释主模型 & 大模型/前后端混合方式等）的多组实验中均验证了其效果。
- **系统的实验设计**：代码复现的信息具体（分层对照架构），超参数均有分析（如专家数量、秩、Top-k、损失权重等），在可贡献性与透明性上优于大量仅给单一结果的同类文章。
- **清晰可视化与证据链**：将手语者特征降维可视化、专家使用情况热力图和随时间变化的门控分布都展示出来，为路由假设提供了证据。

#### 8. 不足与局限

- **实验覆盖范围有限**：
  - 三大数据集均以“哪一位手语者”作为区分源/目标的标准并未覆盖硬性环境偏移（背景、相机位置、动态照度突变）及多源混合偏移等场景；
  - 尤其是真实世界往往同时发生多因素偏移。
- **在流式/噪声场景的鲁棒性未被验证**：几乎完全延续已有 TTA 中相对纯源的引入序贯样本流程，没有直接测试长视频中的累积误差、错误预测对外传播导致的不稳定性。
- **初始化依赖额外的有标签数据**：虽然数量很少（小规模源域子集），但论文没有给出这一开销在完全无监督约束下的可替代方案。
- **实时部署的限制**：因为是流式适应（每样本都需梯度迭代更新），存在额外的计算开销——本文虽然测量延迟，但未在严格实时约束下（处理 1 分钟的输入不超过 1 分钟等）进行系统验证。
- **超参数与稳定的阈值敏感性没有充分跨域进行讨论**：在单数据集上的最佳专家数量与门控 Top-k 选择如果导入新的数据集是否需要重新调整，论文尚未给出清晰“迁移建议”。
- **Ethics 讨论不充分**：作者认识到了确保稳定性的问题，但没有具体展开如何制定“人工介入”的人机边界，以及如何应对遇到恶意/不实输入或者对手语者为个体特征的过度特性化等风险。
- 计算方法与公正性相关陈述相对简短，能否完整复现其含 9 个背骨模型的全部实验仍有现实条件负荷问题，但这并不构成对该方法本身逻辑的否定。

（完）
