---
title: "AROMA: Augmented Reasoning Over a Multimodal Architecture for Virtual Cell Genetic Perturbation Modeling"
title_zh: AROMA：面向虚拟细胞基因扰动建模的多模态增强推理
authors: "Wang Zhenyu, Geyan Ye, Wei Liu, Man Tat Alexander Ng"
date: 2026-07-01
pdf: "https://aclanthology.org/2026.findings-acl.1594.pdf"
tags: ["query:gene-perturb"]
score: 10.0
evidence: 用多模态增强推理进行虚拟细胞基因扰动建模
tldr: 虚拟细胞建模通过计算预测基因扰动引起的分子状态变化，但现有方法推理不受约束、预测不可解释、检索信号与调控拓扑对齐弱。本文提出AROMA，多模态增强推理架构，融合文本证据、图拓扑信息和蛋白质序列特征来建模扰动-靶标依赖关系，并通过两阶段优化获得准确且可解释的预测。实验表明AROMA在准确性和可解释性上优于已有方法，为虚拟细胞扰动建模提供了新范式。
source: ACL-2026-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-findings/anthology-2026findings-acl1594/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 793, \"height\": 850, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026findings-acl1594/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1650, \"height\": 999, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026findings-acl1594/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1657, \"height\": 531, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026findings-acl1594/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1652, \"height\": 781, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026findings-acl1594/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1654, \"height\": 907, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-findings/anthology-2026findings-acl1594/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1667, \"height\": 593, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026findings-acl1594/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 795, \"height\": 178, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026findings-acl1594/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1656, \"height\": 409, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026findings-acl1594/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 808, \"height\": 257, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026findings-acl1594/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1658, \"height\": 302, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026findings-acl1594/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 815, \"height\": 467, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026findings-acl1594/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 815, \"height\": 429, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026findings-acl1594/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1661, \"height\": 271, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026findings-acl1594/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 809, \"height\": 180, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026findings-acl1594/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 810, \"height\": 742, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026findings-acl1594/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1663, \"height\": 271, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026findings-acl1594/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 813, \"height\": 360, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026findings-acl1594/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 811, \"height\": 214, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026findings-acl1594/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 815, \"height\": 464, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026findings-acl1594/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 815, \"height\": 606, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026findings-acl1594/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 811, \"height\": 286, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026findings-acl1594/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 810, \"height\": 208, \"label\": \"Table\"}]"
motivation: 现有虚拟细胞扰动建模缺乏受约束推理、可解释性和调控拓扑对齐。
method: 整合文本、图拓扑与蛋白序列特征，采用两阶段优化进行扰动-靶标依赖建模。
result: 在虚拟细胞扰动预测上同时提升准确性和可解释性。
conclusion: 为虚拟细胞基因扰动预测提供更准确且可解释的建模框架。
---

## Abstract
Virtual cell modeling predicts molecular state changes under genetic perturbations in silico, which is essential for biological mechanism studies. However, existing approaches suffer from unconstrained reasoning, uninterpretable predictions, and retrieval signals that are weakly aligned with regulatory topology. To address these limitations, we propose AROMA, an Augmented Reasoning Over a Multimodal Architecture for virtual cell genetic perturbation modeling. AROMA integrates textual evidence, graph-topology information, and protein sequence features to model perturbation-target dependencies, and is trained with a two-stage optimization strategy to yield predictions that are both accurate and interpretable. We also construct two knowledge graphs and a perturbation reasoning dataset, PerturbReason, containing more than 498k samples, as reusable resources for the virtual cell domain. Experiments show that AROMA outperforms existing methods across multiple cell lines, and remains robust under zero-shot evaluation on an unseen cell line, as well as in knowledge-sparse, long-tail scenarios. Overall, AROMA demonstrates that combining knowledge-driven multimodal modeling with evidence retrieval provides a promising pathway toward more reliable and interpretable virtual cell perturbation prediction. Model weights are available at https://huggingface.co/blazerye/AROMA. Code is available at https://github.com/blazerye/AROMA.

---

## 论文详细总结（自动生成）

## 论文总结：AROMA：面向虚拟细胞基因扰动建模的多模态增强推理

### 1. 核心问题与整体含义（研究动机与背景）

- **研究背景**：虚拟细胞建模旨在通过计算方式（in silico）预测基因扰动后细胞分子状态的变化，是生物学机制研究的核心问题。本文聚焦于基因层面的扰动预测任务：给定细胞系上下文、扰动基因和靶基因，预测靶基因是上调（Up）、下调（Down）还是非差异表达（Non-diff）。
- **现有方法的三大局限**：
  - **推理不受约束**：通用大语言模型能生成流畅解释，但缺乏生物学约束，预测不可靠；领域微调模型基于合成或弱监督推理轨迹训练，可能继承监督噪声。
  - **预测不可解释**：现有基础模型（如 GEARS、scGPT 等）只输出差异表达分数或标签，不提供预测依据和推理过程。
  - **检索信号与调控拓扑对齐弱**：检索增强方法获取的外部知识结构松散、不考虑调控方向性和多步传播，无法与从扰动基因到下游靶标的机制通路系统性对齐。
- **核心研究问题**：如何构建一个既准确又可解释的虚拟细胞基因扰动预测模型，使其预测在生物学上合理、推理过程可被人类理解，并能在知识稀疏场景下保持稳健。

### 2. 方法论：核心思想、关键技术细节

**核心思想**：扰动预测应基于结构化、查询特定的生物学证据，显式建模扰动基因与靶基因之间的依赖关系。AROMA 整合三种模态信息——文本证据、图拓扑信息、蛋白质序列特征——并通过两阶段优化实现准确且可解释的预测。整体流程分为三个阶段：

#### （1）数据构建阶段
- **Gene-KG（基因知识图谱）**：整合 STRING 和 CORUM 数据库，构建基因-基因关联网络，包含 **18,479 个节点**和 **752,612 条边**，平均度为 81.46。
- **Path-KG（通路知识图谱）**：整合 Gene Ontology 和 Reactome，构建基因-功能/通路实体关联网络，包含 **80,020 个节点**和 **441,176 条边**，平均度为 11.03。
- **PerturbReason 数据集**：基于 PerturbQA 数据集构建，包含 **超过 498k 个样本**。为每个实例检索基因功能描述、调控路径和细胞系信息，使用 DeepSeek-R1 生成与标签一致的推理轨迹，仅保留标签一致且结构有效的推理数据以减少监督噪声。

#### （2）建模阶段
- **检索增强上下文（Retrieval-Augmented Contextualization）**：构建包含三类外部证据的文本输入：
  - **基因功能描述 T_desc**：从 SUMMER 知识库检索每个基因作为扰动基因和靶基因的功能摘要；
  - **调控路径 T_path**：在 Path-KG 上使用广度优先搜索提取扰动基因到靶基因的最多 3 条最短路径；
  - **细胞系描述 T_cell**：基于 Wikipedia 构建细胞系描述库并检索对应描述。
- **多模态交互编码（Multimodal Interaction Encoding）**：
  - **结构感知图编码器**：在 Gene-KG 和 Path-KG 上分别预训练两个参数独立的 GAT 编码器，预训练目标为边预测（二分类交叉熵损失）。推理时提取扰动基因和靶基因周围的 k-hop 子图，用预训练 GAT 编码后经 mean-pooling 得到结构嵌入。
  - **蛋白质序列编码器**：使用冻结的 ESM-2（esm2_t48_15B_UR50D）编码蛋白序列，mean-pooling 得到序列嵌入。
  - **跨模态交互特征**：对每种模态（gene、path、protein）使用交叉注意力机制——将扰动基因作为查询（query）、靶基因作为键和值（key/value）——得到交互特征，再通过轻量投影器注入语言模型的 token 空间，使模型接收显式的多模态扰动-靶标交互信号。

#### （3）训练阶段（两阶段优化）
- **第一阶段——多模态监督微调（SFT）**：在 PerturbReason 数据集上执行标准自回归语言建模目标。GNN 和 ESM-2 编码器冻结，交互和投影模块全参微调，语言模型通过 LoRA 更新。
- **第二阶段——GRPO 强化学习**：对每个实例采样多条推理轨迹，定义奖励函数：预测正确得 5.0 分，错误得 −1.0；推理格式正确加 0.5；答案恰好包含一个有效类别再加 0.5。奖励在轨迹组内归一化计算优势，仅更新 LoRA 参数，其他模块全部冻结。

**关键公式**：
- 三元标签构造：基于 Wilcoxon 秩和检验和 Benjamini-Hochberg 校正的调整 p 值，结合均值表达差异 Δμ 确定 Up/Down/ND 标签。
- GAT 更新：h_i^(l+1) = ELU(Σ_{j∈N(i)} α_ij W^(l) h_j^(l))
- 边预测分数：s_uv = MLP([z_u; z_v])，预训练损失为二元交叉熵。
- 跨模态交互特征：z_inter = Softmax(Q_p K_t^T / √d_k) V_t
- SFT 损失：L_SFT = −ΣΣ log P(y_t | y_<t, X; Θ)
- GRPO 目标：L_GRPO = E[ R(τ) − β·KL(π_θ ‖ π_ref) ]

### 3. 实验设计：数据集、基准与对比方法

| 实验维度 | 具体设置 |
|---|---|
| **数据集** | PerturbQA 官方训练/测试划分；PerturbReason（498k+ 样本）用于训练；4 个人类细胞系：K562、HepG2、Jurkat、RPE1 |
| **任务** | 三分类预测：靶基因在给定扰动下为 Up / Down / Non-diff |
| **评价指标** | Macro-F1（因三分类标签不平衡） |
| **对比方法** | ① 通用 LLMs：DeepSeek-R1、OpenAI o4-mini、GPT-5、Gemini-2.5-pro、Qwen3-235B；② 领域专用基础模型：SynthPert、GAT、STATE、GEARS、scGPT、GenePT-Gene、GenePT-Prot、SUMMER |

### 4. 资源与算力

- **论文未明确说明 GPU 型号、数量和具体训练算力消耗**。
- 论文仅提到：模型在计算上较为昂贵，单次完整训练运行通常需要 **超过 30 小时**；所有实验在公开的超参数配置下进行了单次完整训练和评估。
- 基座模型选择：对比了 Deepseek-Distilled-Llama-8B、Llama3-8B、Qwen3-8B，最终采用 **Qwen3-8B** 作为语言模型基座，LoRA rank=16；ESM-2 使用 15B 参数版本；精度为 bfloat16。

### 5. 实验数量与充分性

**实验组数概览**：
- **主实验**（表 1）：在 4 个细胞系上对比 13 种基线方法，报告 ND/Up/Down 三类 F1 和平均值。
- **零样本泛化实验**（表 2）：在未见细胞系 RPE1 上的零样本评估。
- **消融实验**（表 3）：8 组变体，逐步加入 SFT、GRPO、RAG、GNN、ESM-2 各模块，并在 4 个细胞系（含 RPE1 零样本）上评估。
- **知识稀疏鲁棒性实验**（表 4 + 附录 C.4）：按基因流行度（PubMed 提及频率）和节点度（Path-KG 中连接数）分层，在 High/Mid/Low 三组上评估。
- **GRPO 轨迹数敏感性分析**（表 5）：对比 4、8、16 条采样轨迹。
- **附录补充实验**：k-hop 子图范围选择（1/2/3-hop）、3 种基座模型对比、GNN 预训练 AUROC、分层鲁棒性全细胞系结果。
- **案例研究**（附录 E）：句子级来源追溯分析和生物学有效性验证（与文献比对）。

**充分性与客观性评估**：
- **充分性较高**：实验覆盖了多细胞系、零样本泛化、消融分析、长尾鲁棒性、超参敏感性等多个维度，实验设计较为全面。
- **客观性**：基线方法使用官方实现和最佳超参数；通用 LLM 使用官方 API 版本，设置清晰。但论文承认所有结果均为**单次运行**，缺乏多次重复实验的标准差报告，可能影响统计稳健性。

### 6. 主要结论与发现

- **主实验表现**：AROMA 在平均 Macro-F1 上达到 **0.73**，显著优于所有对比方法（最佳基线 SUMMER 为 0.64，GAT 为 0.64），且在全部 4 个细胞系上均取得最高或并列最高的 ND/Up/Down F1。
- **零样本泛化**：AROMA 在未见细胞系 RPE1 上仅轻微下降（0.73 vs. 0.77 训练设置），仍优于其他模型的非零样本结果，展现强跨分布泛化能力。
- **消融分析**：各组件均有贡献——SFT 带来最大增益，GRPO 进一步提升；RAG、GNN 编码器和 ESM-2 编码器均提供互补信息，移除任一模块均导致性能明显下降。
- **知识稀疏鲁棒性**：从高流行度/高连接基因到低流行度/低连接基因，AROMA 的性能下降幅度远小于去掉 RAG 和多模态模块的变体，说明其增益来自联合建模而非记忆高频基因。
- **GRPO 敏感性**：采样轨迹数从 4 增至 16，模型性能稳步提升，16 条轨迹为最优设置。
- **核心结论**：将显式的扰动-靶标关系建模融入多模态特征、检索证据和两阶段训练的联合框架，是构建更可靠、可解释的虚拟细胞模型的可行路径。

### 7. 优点

- **创新性强的框架设计**：首次将文本证据、图拓扑结构和蛋白质序列三种模态系统性地整合到扰动预测中，通过交叉注意力显式建模扰动-靶标依赖关系。
- **可解释性突出**：不同于仅输出标签的模型，AROMA 不仅给出预测结果，还生成人类可读的推理轨迹；附录 E 的句子级来源追溯和生物学有效性分析验证了推理内容的证据支撑和文献一致性。
- **资源贡献**：构建并公开了 Gene-KG、Path-KG 两个知识图谱和 PerturbReason（498k+ 样本）推理数据集，为虚拟细胞领域提供了可复用的数据基础。
- **两阶段训练策略设计合理**：先通过 SFT 对齐多模态信息和领域知识，再用 GRPO 强化学习优化推理质量，兼顾准确性和解释质量。
- **鲁棒性验证完善**：覆盖零样本泛化、长尾知识稀疏场景，证明模型不依赖记忆高频基因。
- **广泛深入的对比实验**：对比了 5 个通用 LLM 和 8 个领域专用模型，消融实验覆盖所有核心模块。

### 8. 不足与局限

- **问题范围受限**：仅支持单基因扰动建模，无法处理多基因组合扰动（协同效应）或化学干预等更复杂场景；推理输出仅针对单个靶基因的三分类，未扩展到多下游基因的联合建模。
- **对先验知识的依赖**：模型依赖预构建的知识图谱和外部文本资源；对于注释缺失或数据库未覆盖的基因，结构性和功能性信息极度有限，预测性能会显著下降。
- **基准数据的局限性**：PerturbReason 由 DeepSeek-R1 生成推理轨迹，虽然进行了标签一致性过滤，但本质上仍可能包含合成噪声，推理质量的上限受限于生成模型的能力。
- **实验统计稳健性不足**：所有实验均为单次训练运行（论文明确说明），未报告多次重复实验的均值和方差，无法评估结果的统计显著性。
- **知识图谱边语义简化**：将不同来源、不同证据类型的边统一为无向关联边，丢失了调控方向性和因果信息，可能限制模型对调控机制的精确建模能力。
- **计算成本较高**：单次完整训练超过 30 小时，未提供 GPU 资源明细，可能影响其他研究者复现和扩展实验的成本评估。

---

（完）
