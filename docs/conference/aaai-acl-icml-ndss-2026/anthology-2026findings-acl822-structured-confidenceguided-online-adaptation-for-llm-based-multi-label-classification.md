---
title: Structured Confidence–Guided Online Adaptation for LLM-based Multi-Label Classification
title_zh: 面向LLM多标签分类的结构化置信度引导在线适应
authors: "Pengyu Xu, JingRen Hou, Liping Jing (景丽萍), Jian Yu (于剑)"
date: 2026-07-01
pdf: "https://aclanthology.org/2026.findings-acl.822.pdf"
tags: ["query:few-shot"]
score: 6.0
evidence: 指出流式测试数据分布偏移导致LLM多标签分类性能下降，并设计无参数在线适应方法
tldr: 大语言模型虽可借助上下文学习完成零样本或少样本多标签分类，但在流式测试数据上常因分布偏移和长尾标签而性能下降，静态推理无法适应动态分布。该文提出无参数更新的在线适应框架SCOTTA，用标签集局部似然构造结构化置信度，避免标准生成概率不可靠的问题，同时改进置信度缓存防止高频易例过拟合、降低标签覆盖。实验表明它能提升流式多标签分类的适应性与标签多样性，为LLM在线部署提供了轻量方案。
source: ACL-2026-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-findings/anthology-2026findings-acl822/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 809, \"height\": 316, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026findings-acl822/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1597, \"height\": 707, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026findings-acl822/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 807, \"height\": 315, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026findings-acl822/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 803, \"height\": 350, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026findings-acl822/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 804, \"height\": 353, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-findings/anthology-2026findings-acl822/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 776, \"height\": 250, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026findings-acl822/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1555, \"height\": 726, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026findings-acl822/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1382, \"height\": 304, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026findings-acl822/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1382, \"height\": 307, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026findings-acl822/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1415, \"height\": 322, \"label\": \"Table\"}]"
motivation: 流式测试数据中的分布偏移和长尾标签使LLM多标签分类性能退化，且静态推理与朴素缓存均不可靠。
method: 提出SCOTTA在线适应框架，用标签集局部似然作为结构化置信度，并设计避免过拟合的缓存机制，无需更新参数。
result: 缓解不可靠置信度与缓存过拟合，提高流式数据下的分类性能和标签覆盖率。
conclusion: 结构化置信度驱动的无参数在线适应为LLM应对分布偏移提供了有效的轻量级解决方案。
---

## Abstract
Large language models (LLMs) enable zero-shot and few-shot multi-label text classification via in-context learning, yet most approaches perform static inference and degrade under streaming test data due to distribution shift and long-tail labels. We study online test-time adaptation for LLM-based multi-label generation without any parameter updates, and identify two bottlenecks: (1) standard generation probabilities provide unreliable confidence because they ignore label competition at key decoding branches; (2) naive confidence-based caching overfits to frequent and easy examples, reducing label coverage and diversity. We propose SCOTTA, a structured confidence-guided online adaptation framework. SCOTTA introduces Label-set Local Likelihood Ratio (L3R), a label-level confidence measure that compares a target label against its valid competitors at critical decision positions. Using L3R as a unified signal, SCOTTA maintains an in-context exemplar cache via streaming submodular maximization, balancing label coverage, semantic diversity, and sample quality under a fixed context budget. Across four benchmarks, SCOTTA consistently improves Micro-F1 and Macro-F1 over strong LLM and non-LLM baselines, with the largest gains on long-tail labels.

---

## 论文详细总结（自动生成）

## 论文详细中文总结

### 1. 核心问题与研究动机

- **研究方向**：面向大语言模型（LLM）的多标签文本分类（MLTC）的在线测试时适应（Online Test-Time Adaptation, OTTA）。LLM 可通过上下文学习（ICL）在零样本/少样本设定下完成 MLTC，无需更新参数。
- **核心问题**：现有 LLM 多标签分类方法大多采用静态推理，假设测试数据独立同分布（i.i.d.）。在真实流式测试环境中，数据分布会发生偏移且存在长尾标签，静态推理会持续性能退化。
- **两个关键瓶颈**：
  - **置信度估计不可靠**：标准 token 概率聚合（序列似然、perplexity 等）用于多标签生成任务时会产生“置信度幻觉”。由于许多标签共享长公共前缀，大部分解码位置近似确定性（如命名空间 token），真正竞争仅发生在少数关键分支位置。若对这些 token 概率做朴素平均，会被确定性 token 主导，无法反映模型在真正决策点上的偏好。
  - **朴素缓存策略导致多样性退化**：基于置信度阈值的缓存、FIFO 缓存容易过拟合高频且容易的样本，造成语义冗余、标签覆盖度低、长尾泛化能力受损。
- **整体含义**：该工作论证了在**无任何参数更新**的前提下，通过结构化置信度信号与子模优化驱动的记忆缓存的耦合，可使 LLM 在流式测试数据上持续积累经验，缓解分布偏移和长尾标签带来的性能下降，为 LLM 在线部署提供了一条轻量级路径。

### 2. 方法论：SCOTTA 框架

#### 2.1 总体架构

SCOTTA（**S**tructured **C**onfidence-guided **O**nline **T**est-**T**ime **A**daptation）包含两个耦合模块：

- 输入为依次到达的测试实例流 `{x_t}`，标签集为 `Y = {y(1), ..., y(K)}`；
- 对每个 `x_t`，从当前记忆库 `S_{t-1}` 检索 k 个近邻样例注入 prompt，LLM 生成预测标签集 Ŷ(x_t)；
- 计算 L3R 置信度 C(x_t)；
- 若 C(x_t) 超过阈值 τ，则通过 SMB 更新记忆库得到 S_t；
- 全程不更新模型参数。

#### 2.2 核心模块一：L3R（Label-set Local Likelihood Ratio）

**核心思想**：生成式多标签分类的标签竞争是**稀疏且位置特定**的——多数位置属于共享前缀或确定性补全，只有少数“分支位置”真正决定了选择哪个标签路径。因此置信度应聚焦于这些关键决策位置。

**基于 LLM 解码定义**：
- 标签 y(k) 被看作 token 序列；
- 在位置 t 处，给定前缀 pref，标签 k 的竞争者集合为共享同一前缀的所有其他标签：A(k)_t = {j | pref(j)_t = pref(k)_t}；
- 定义自概率 p_self = p_t(y(k)_t)，竞争概率 p_comp = Σ_{j≠k} p_t(y(j)_t)；
- 局部似然比：`LLR_t = log((p_self + ε) / (p_comp + ε))`，ε 为平滑常数。

**位置加权机制**：
- 通过归一化自概率与竞争概率并计算二元熵 `J_t`，衡量每个位置的“竞争强度”（信息量）；
- 使用 softmax 权重 `w_t ∝ exp(αJ_t)` 对位置加权，α 控制对高信息决策点的强调程度，使共享前缀和确定性补全位置贡献更少；
- 最终 L3R 标签级置信度为加权局部似然比之和。

该度量的特点是“解码一致”（decoding-consistent）：从生成机制出发显式建模标签竞争，避免了序列整体似然的伪置信度过高问题。

#### 2.3 核心模块二：SMB（Submodular Memory Bank）

**问题形式化**：在固定预算 B 内，从候选流中维护记忆库 S，最大化一个单调子模目标：

`F(S) = λ1·F_cov(S) + λ2·F_div(S) + λ3·F_qual(S)`

**三个目标分量**：

| 分量 | 公式 | 作用 |
|------|------|------|
| 标签覆盖 F_cov | 根据标签在 S 中的频率的倒数加权覆盖项 | 鼓励长尾标签获得均衡曝光，防止高频标签坍缩 |
| 语义多样性 F_div | Σ_u max_{i∈S} cos_sim(u, i) | 在嵌入空间选择代表性样本，减少冗余 |
| 样本质量 F_qual | Σ_{i∈S} q_i | 偏好高置信度预测 |

**在线更新策略**：对新候选样例计算边际增益 Δ(i\|S)，根据当前记忆是否满进行插入或替换记忆库中对目标贡献最小的元素，具有固定基数约束下的单调子模最大化的常数因子近似保证。

#### 2.4 推理与检索

- 对测试输入 x_t 使用句子编码器编码，在 S_t−1 内做 k-NN（余弦相似度）检索；
- 检索的样例排序后格式化为 (input → label-set) 对注入 prompt；
- 保持固定上下文预算，超出 token 限制时优先截断最旧的样例。

### 3. 实验设计

#### 3.1 数据集

| 数据集 | 标签数 | 领域 | 特征 |
|--------|--------|------|------|
| MOVIE | 27 | 电影简介 | 小标签空间 |
| AAPD | 54 | 论文摘要 | 中规模标签空间 |
| RCV1 | 103 | 新闻 | 中等标签空间 |
| StackExchange (SE) | 12,892 | 问答帖子 | 极端多标签（extreme multi-label）空间 |

每个数据集随机采样 10,000 条实例进行评估，报告 **Micro-F1**（反映总体性能/高频标签）和 **Macro-F1**（反映长尾标签平均表现）。

#### 3.2 对比方法

| 方法类型 | 代表方法 |
|----------|----------|
| Embedding 零样本匹配 | RoBERTa、SimCSE、MPNet（句子嵌入检索） |
| 静态 LLM 推理 | GPT-3.5-turbo、GPT-4o、Qwen2.5-7B-Instruct、Qwen3-8B-Instruct（固定 prompt） |
| LLM 结构化多标签推理 | ICXML（候选生成+重排） |
| 伪标签/自训练 | PESCO、PIEClass |

对于 StackExchange 极端标签空间，采用与 ICXML 类似的先粗检索候选（|Yʻ|=200）再做约束生成的两阶段策略，保证对比公平。

#### 3.3 公平性与控制设计

- 所有 LLM 方法共享同一 prompt 模板、标签表述、输出约束和解码配置（temperature=0，最大生成长度 128）；
- SCOTTA 与静态推理的唯一区别是 {DEMONSTRATIONS} 字段的来源（固定 vs. 在线更新）；
- 统一输出解析与归一化规则应用于所有方法。

### 4. 资源与算力

- 论文正文对 GPU 情况描述有限。仅在附录 A.0.1 中提到开源模型 Qwen2.5-7B-Instruct 和 Qwen3-8B-Instruct 部署在 **NVIDIA A100 80GB GPU** 上；
- 未明确报告：GPU 数量、训练/推理时长、token 消耗量、API 调用成本等具体算力指标；
- 实验以 API 调用和冻结推理为主，总体算力需求属于轻量级（无需训练），但论文未给出详细的资源开销量化。

### 5. 实验数量与充分性评估

| 实验类别 | 内容 | 评估 |
|----------|------|------|
| 主实验 | 4 个数据集 × 2 指标，对比 10+ 方法 | 覆盖不同标签空间规模和长尾程度，较为系统 |
| 消融实验 | 在 GPT-3.5 和 GPT-4o 两个 backbone 上，对 SMB、L3R、全模型三类变体 × 4 数据集 | 验证了两模块各自的贡献和协同效应，实验充分 |
| 流式性能评估 | AAPD 上每 500 个样本的累积 Micro-F1/Macro-F1 变化曲线 | 直接验证在线适应随样本累积的改进趋势 |
| 参数敏感性 | k（检索样例数）和 λ1（标签覆盖权重）在两个数据集上的变化 | 验证启发式默认参数的有效性和方法的稳定性 |

**总体评估**：实验设计较为全面客观——对比方法覆盖了四个技术路线，消融验证了各模块必要性，流式曲线和敏感性分析提供了多维证据，且两个闭源 backbone 的一致结论增强了方法的泛化可信度。但 StackExchange 实验依赖两阶段候选缩减（候选仅 200 个），这意味着部分性能上限受限于候选检索质量而非 SCOTTA 本身。

### 6. 主要结论与发现

- **一致改进**：SCOTTA 在全部四个数据集、两个评价指标上稳定超越所有基线。相比最强静态 GPT-4o：MOVIE Micro-F1 +3.12、Macro-F1 +6.76；AAPD 分别 +5.21/+4.36；RCV1 分别 +2.11/+4.07；SE 分别 +5.76/+3.33。
- **长尾增益更显著**：Macro-F1 的提升幅度一致性地高于 Micro-F1，表明结构化置信度 + 子模记忆维护能有效缓解头部标签支配，提升长尾标签泛化。
- **模块协同生效**：单独使用 L3R 或 SMB 效果有限，两者组合后优于各部分的简单叠加，证明“可靠候选”（L3R）与“均衡记忆”（SMB）之间具有明确协同关系。
- **随时间持续改进**：流式曲线表明静态推理基本持平，而 SCOTTA 的累积 Micro-F1/Macro-F1 呈现单调上升，说明经验积累有效且未发生缓存退化。
- **跨模型一致性**：效果在 GPT-3.5 与 GPT-4o 上趋势一致，说明方法不依赖于特定模型架构。

### 7. 优点与亮点

- **问题洞察新颖深刻**：识别了生成式多标签分类中“标签竞争高度局部化”的特性，并以此揭示了置信度评估的固有偏差——这一诊断在方法论层面具有启发价值。
- **方法设计精妙**：
  - L3R 从解码机制出发构建置信度，有清晰的概率解释；
  - SMB 将缓存维护转化为带理论保障的流式子模最大化，在线更新策略（插入/替换）在理论上具有常数因子近似保证；
  - “谁值得复用”（L3R 置信度阈值）和“哪些值得保留”（SMB 子模目标）的统一信号设计优雅。
- **训练免费（training-free）**：完全通过 prompt 工程和缓存管理实现适应，适用第三方 API 和封闭模型场景，工程可行性较高。
- **实验严谨**：对 prompt 公平性进行了严格控制（共享模板、统一解码、统一标签空间），在两个 backbone 上独立验证，并报告了参数敏感性；提供流式分析可视化了适应过程的动态涨势。
- **超参设定具有启发式指导**：附录给出了 B ∝ c·√L、τ 按标签空间大小选择 top-p% 等实用经验法则，增强了方法的可复现性和落地价值。

### 8. 不足与局限

- **需要 token 级概率访问**：L3R 需要 logits/log-probabilities，但许多商业 LLM API 不提供此能力（论文 Limitations 中已承认），限制了方法的适用范围。
- **推理开销增加**：置信度计算、嵌入检索、子模缓存更新增加了测试时的额外计算开销，在高吞吐或超大标签空间场景下代价较高；论文未给出具体的时间开销量化。
- **依赖嵌入质量**：SMB 的语义多样性与检索质量依赖于句子编码器；嵌入方向不对齐或质量不足时，记忆库的有效性将下降。
- **伪标签累积风险**：在严重分布偏移下，“自信但错误”的预测仍可能通过阈值并进入缓存，产生错误累积；更严格的校准或验证信号可进一步提升鲁棒性。
- **评测覆盖有限**：所有评价基于采样 10,000 条实例，未报告置信区间或多次运行的方差；仅使用 GPT-3.5/GPT-4o（及部分开源 7B/8B 模型）作为 backbone，未在更大规模（如 70B+）开源模型上验证——这可能影响对方法在超大模型上的结论推广；两个开源 backbone 的实验也仅在主实验表中出现，未纳入消融验证。
- **核心对比例的表述留有余地**：对最强基线 GPT-4o 的改进可观，但没有深入分析失败案例，也没有报告不同分布偏移强度（如自然偏移 vs. 合成偏移）下的分层次表现。
- **可复现性细节不足**：句子编码器的具体型号未明确说明（仅在附录提及与 SMB 使用同一编码器），置信度阈值 τ 的 percentile 换算过程也没有完全展开。

（完）
