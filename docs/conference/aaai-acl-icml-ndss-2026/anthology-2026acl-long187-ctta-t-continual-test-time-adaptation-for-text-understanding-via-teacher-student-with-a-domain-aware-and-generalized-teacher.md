---
title: "CTTA-T: Continual Test-Time Adaptation for Text Understanding via Teacher-Student with a Domain-aware and Generalized Teacher"
title_zh: CTTA-T：使用域感知与泛化教师的师生网络实现文本持续测试时适应
authors: "Tianlun Liu, Zhiliang Tian, Zhen Huang, Xingzhi Zhou, Wanlong Yu, Tianle Liu, Feng Liu, Dongsheng Li"
date: 2026-07-01
pdf: "https://aclanthology.org/2026.acl-long.187.pdf"
tags: ["query:few-shot"]
score: 4.0
evidence: 面向未观测文本域的持续测试时适应方法，虽不属少样本分类，但处理域偏移的思路可借鉴
tldr: 文本理解应用常受域偏移影响，现有测试时适应往往只能处理固定测试域。论文面向更实际的持续测试时适应（CTTA）场景，即测试阶段出现一系列未见文本域。当前CTTA方法难以抑制跨域误差累积并提升对未见域的泛化。为此提出CTTA-T，采用具有域感知和泛化能力的教师网络的师生结构，在线适应序列化的未见域，从而降低误差累积并提升对未知域的适应能力，为文本理解在动态域偏移下的部署提供了更实用的范式。
source: ACL-2026-Long
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-long/anthology-2026acl-long187/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 812, \"height\": 354, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026acl-long187/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1648, \"height\": 779, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026acl-long187/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 803, \"height\": 323, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026acl-long187/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 811, \"height\": 302, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026acl-long187/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 808, \"height\": 290, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026acl-long187/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1400, \"height\": 636, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026acl-long187/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1570, \"height\": 933, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026acl-long187/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1653, \"height\": 292, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long187/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1651, \"height\": 782, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long187/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1655, \"height\": 442, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long187/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 796, \"height\": 276, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long187/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 795, \"height\": 166, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long187/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1650, \"height\": 433, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long187/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 800, \"height\": 115, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long187/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 796, \"height\": 207, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long187/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1651, \"height\": 473, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long187/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1649, \"height\": 546, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long187/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1661, \"height\": 445, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long187/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1644, \"height\": 294, \"label\": \"Table\"}]"
motivation: 文本理解的测试域通常依次出现且不可预知，现有域适应和TTA难以处理持续未见域，误差累积问题严重。
method: 提出CTTA-T师生框架，设计域感知且泛化的教师网络，在线适应连续出现的未见文本域并抑制误差传播。
result: 在文本理解的持续测试时适应场景中减少跨域误差累积，提升对未见域的处理能力。
conclusion: 面向未见文本域序列的师生持续适应能显著提高文本模型在动态域偏移下的鲁棒性与泛化能力。
---

## Abstract
Text understanding application often suffers from domain shifts. To handle testing domains, domain adaptation (DA) is trained to adapt to a fixed and observed testing domain; a more challenging paradigm, test-time adaptation (TTA), cannot access the testing domain during training and online adapts to the testing samples during testing, where the samples are from a fixed domain. We aim to explore a more practical and underexplored scenario, continual test-time adaptation (CTTA) for text understanding, which involves a sequence of testing (unobserved) domains in testing. Current CTTA methods struggle in reducing error accumulation over domains and enhancing generalization to handle unobserved domains: 1) Noise-filtering reduces accumulated errors but discards useful information, and 2) accumulating historical domains enhances generalization, but it is hard to achieve adaptive accumulation. In this paper, we propose a CTTA-T (continual test-time adaptation for text understanding) framework adaptable to evolving target domains: CTTA-T adopts a teacher-student framework, where the teacher is equipped with domain awareness and generalization for evolving domains. To improve teacher predictions, we propose a refine-then-filter based on dropout-driven consistency, which calibrates predictions and removes unreliable guidance. For the adaptation–generalization trade-off, we construct a domain-aware teacher by dynamically accumulating cross-domain semantics via incremental PCA, which continuously tracks domain shifts. Experiments show CTTA-T excels baselines.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **问题背景**：真实世界中的自然语言处理应用常面临持续性的域偏移（continual domain shift）。现有模型大多假设训练与测试数据分布一致，这在实践中难以成立；而模型部署后，测试域往往以序列形式/持续演变地出现（如电影评论模型在线测试餐厅评论或书籍评论）。
- **现有范式的局限**：
  - 域适应（DA）需要在训练阶段接触目标域数据，现实中难以满足；
  - 测试时适应（TTA）虽然能够在测试阶段在线适应，但假设目标域固定不变，无法应对持续演变的文本域。
- **所研究的空白**：论文面向持续测试时适应（CTTA）这一更具实际意义但尚未被充分探索的文本理解场景，既要应对"测试域按序未知出现"的挑战，又要解决"不可累积误差"的矛盾。
- **挑战归纳**：① 持续域偏移放大噪声累积，导致模型崩溃；② 现有方法在过滤噪声（避免误差累积）的同时，常丢弃有用的目标域信息；③ 固定权重的教师更新策略既难以感知域间偏移，也难以动态获取目标域语义。

## 2. 论文提出的方法论：核心思想、关键技术细节与算法流程

论文提出 **CTTA-T 框架**，基于"教师-学生"结构，并让教师模型具备**域感知能力**和**泛化能力**：

- **师生框架基础**（§3.1）：
  - 学生模型（θS）在当前样本上快速适应当前域，通过优化与教师输出的交叉熵（soft label 蒸馏）完成更新；
  - 教师模型（θT）作为稳定知识汇聚器，渐进式融合学生累计信息，提供可靠的伪标签并引导学生的适应过程。
- **Refine-then-Filter（RFP）模块**（§3.2）：
  - 基于 dropout 驱动的预测一致性（consistency），区分并抑制两类不确定性：
    - 认知不确定性（EU）→ 通过对多次随机前向传播形成的预测矩阵做 SVD 分解，构建**预测一致性向量 s**，并据此在训练/蒸馏前**校准教师输出的概率分布**（refine 阶段）；
    - 偶然不确定性（AU）→ 根据一致性向量中选择的 `s_max < threshold` 截断低一致性样本，从源头上**抑制噪声样本的传播**（filter 阶段）；
  - 思路优势：只做简单的熵过滤不够区分模型的不自信与数据本身的噪声，需显式建模两种不确定性来源。
- **域感知教师模块（CDA）**（§3.3）：
  - 使用增量式主成分分析（IPCA）在线更新所有历史样本的协方差矩阵及其主成分空间，在数据"不落盘/可流式"的条件下持续监测域偏移；
  - 通过主成分空间变化量的 Frobenius 范数（∥ΔV∥F²）定义域间的语义距离；
  - 替代原本固定的 EMA 权重 α：当语义距离大时，减少教师对旧知识的依赖、增大向学生/当前域的迁移系数；当语义距离小时，保留历史域知识、避免过拟合当前域，从而动态平衡"域适应"和"域泛化"。
- **随机恢复模块（SRT）**（§3.4）：
  - 以伯努利分布抽取掩码，将教师的部分参数随机原位恢复至源模型参数值（θ0），周期性注入源域通识知识，防止适应到噪声或虚拟任务上去；
  - 与 CDA 互补，CDA 负责向新域靠拢，SRT 负责维系通识表征。

## 3. 实验设计：数据集、benchmark 对比方法

- **Benchmark 贡献**：论文指出目前尚无面向文本理解的 CTTA benchmark，故自主构建了跨多个领域的文本理解 CTTA benchmark，覆盖两类任务流：
  1. **阅读理解（QA）流**：包含 11 个子任务，分别来自 Robust QA（含自然/合成两种噪声，每种又含语音、键盘、翻译三类误差）、MRQA（Search 和 Trivia）、Cross-lingual QA（中文、阿拉伯语、西班牙语翻译集）；该流又被划分为 Short Sequence（7 子任务）与 Long Sequence（11 子任务），各含 3 种随机排列（共 Orders 1~6 种实例）。
  2. **情感分析（SA）流**：以 IMDb 作为英文源域，并加入跨语言的 Multilingual-Sentiment-Classification（中文、阿拉伯语、西班牙语、日语、俄语）与跨领域的评论情感判别，总计 7 个连续子任务。
- **对比方法**：
  - 经典 TTA/CTTA 方法：Tent、OIL、CoTTA、SAR、SoTTA、REM；
  - 强基线 Anti-CF；
  - 两个骨干模型：基础版 XLM-RoBERTa-base + 鲁棒性微调版 xTune；
  - LLM 对比（GPT-4 Turbo、o3、Gemini 2.5 Pro）采用 zero-shot prompt。
- **评估指标**：EM（严格精确匹配）与 F1（部分匹配/缓解小错）。

## 4. 资源与算力

- 正文没有明确披露训练的总 GPU 数量，然而补充资料指出**所有实验均在“NVIDIA N800 GPU”上进行**，并使用 PyTorch 实现；
- 相关工程设置：batch size = 16，AdamW 优化器，learning rate = 1e-5（所有方法统一），每种实验跑 3 次随机种子取平均；
- 说明：除 GPU 型号外，下文没有透露总 GPU 数与训练时长（或总吞吐时间——仅给出单样本的动作级耗时），故算力层面的披露不够完整。

## 5. 实验数量与充分性

论文组织了较丰富且分层化的实验：

1. **主结果实验**：6 个任务流（长短序列 × 各3种乱序）× 2 种骨干 × EM、F1 两指标，整体共 12 组对照表格（Tab.1）；
2. **消融实验**：四个模块逐一剥离（A/B/C → 完整 CTTA-T），覆盖短序列与长序列，验证 CDA、RFP、SRT 三个子模块各自作用（Tab.2、Tab.9）；
3. **针对问题点的定向分析实验**：
   - 误差累积/模型崩溃分析（性能曲线对比，long/short sequence）；
   - 过滤策略消融（无过滤、置信度过滤、RFP 只 refine 不过滤）；
   - CDA 动态权重 vs 固定权重（α=0/0.5/0.99/1.0）对比实验结果（性能曲线随时间变化、仿真领域突变时刻 t=10/15/19）；
   - 时效成本对比（单位 sample 耗时）；
   - LLM zero-shot 对比表格；
   - 超参敏感性分析（对 γ、τ 做二维扫描，图8）；
4. **强基线 Anti-CF 的对照组**（补充实验）；
5. **稳定性分析**（对比各方法在相同序列不同乱序下的方差）与显著性检验（所有结果 t-test p-value < 0.01）。

- **充分性与客观性评价**：
  - 优点：实验布局系统，将“持续偏移/噪声累积/跨域泛化/实时成本/LLM 大模型对比/伪标签噪声过滤”等关键指标均纳入检验，消融充分，且顺序敏感性被方差与 6 种顺序排列显式覆盖；
  - 不足之处：无法保证全部实验都在同一 GPU 卡与同种运行环境下进行（同一张 N800 上跑完全部 6 种排列 + 全部基线是否可行并不明确）；与 LLM 的对比只做静态 zero-shot 状态，并没有允许 LLM 在线更新（CTTA setting），因此优劣比较只建立在“单次动态微调模型 vs 冻住的巨型 LLM”前提下。

## 6. 主要结论与发现

- 在文本理解 CTTA 场景下，CTTA-T 方法综合表现优于全部基线，平均（两种骨干）相对基础版显著提升：与 SAR 相比 EM 平均 +3.96%、F1 +4.19%；与 REM 相比 EM +12.31%、F1 +13.08%；
- CTTA-T 在持续性偏移过程中保持平稳、几乎无崩溃现象，而 CoTTA、Tent、SAR 等基线普遍出现较早崩溃或后期陡降（如图 3 / 附录 H）；
- 基线方法在某些工作流（特别是长序列或高噪声任务）上严重失败（如 Tent 掉到不足 10% EM），说明现有 TTA 方法不天然适用于 CTTA；
- 对更弱的骨干模型 base-backbone，CTTA-T 仍保持较强且相对性能稳定（波动方差最低），说明该方法对教师初始质量不那么敏感；
- RFP 的 refine 与 filter 功能、CDA 的动态知识累积能力、SRT 的通识回归均对性能有重要贡献（去掉任何一个都有稳定降幅）；
- 额外发现：在固定权重 EMA 设置下（甚至 α=0.99）面对突变域偏移时模型恢复慢甚至崩溃，而 CDA 动态权重能快速恢复/保持性能。

## 7. 优点

- **问题定义有前瞻性与实际意义**：将 CTTA 从视觉向 NLP 拓展，贴近现实中的持续域偏移（模型上线后跨主题、跨语种、噪声成因变化等场景）。
- **方法设计的出发点细致**：明确区分并同时处理“认知不确定性（由模型不了解导致）”与“偶然不确定性（由数据带入的噪声）”两种误差来源；refine/filter 两阶段在方法逻辑上自然成立。
  - refine 既贡献分数又过滤样本，既抑制了错误主导教师信号，又留住有用域信息；
- **技术组合具备现代性与自洽性**：IPCA 小空间在线跟踪语义域、动态 EMA 权重与随机恢复源参数，在理论和工程上都容易解释也较易部署；
- **补充推导完整**：全文附带大量详尽的数学分析（B节为 IPCA 敏感性和域距离推导，C 节为 RFP 的一致性上界）；对每种主要结论都有相应的补充实验与证明；
- **严谨性**：实验中考虑了 6 种序列顺序、两个骨干模型、t-test 证实主要结论。对比基线齐全（经典方法、训练增强基线、LLM），同时给出一致的时间开销对比，显示出不只是追求分数、也关注应用成本。

## 8. 不足与局限

- 实验覆盖范围有限，较集中于 QA/阅读理解/情感分析三类任务。论文在 Limitations 中自己承认没有覆盖更完整的文本理解任务宽度（如文本生成、检索/排序、推理类任务等）。
- 关于域偏移的理论性更强、通用的保障条件（任何域偏移是否满足上界与动态权重规则）仍未彻底证明，仍属“经验上稳健，理论上启发式”的层面。
- 资源与可复现细节不够完整：没有说明“具体集群配置/卡数/总运行时长”，没有公开用于 benchmark 全部任务划分的指令与预处理代码，细节隐于附录；对应复现成本较高。
- 与 LLM 的比较存在不对称性：LLM 仅用零样本、无法在线学习；并没有做 LLM+CTTA的对照，也无法判断该方法在大模型动态场景的优势；它更像一个 fair 的固定提示比较条件。
- 计算开销虽已压低，但仍然引入额外前向计算（N 次 MC dropout），进一步增大对低算力端侧部署的难度；
- 方法中的注意力集中在教师端，当初始源模型本身已虚标偏差或伪标签存在系统性偏差（例如类目先验倾斜）时，所提出的过滤方法并不深入处理这种“系统偏差/确认偏差”风险。

**（完）**
