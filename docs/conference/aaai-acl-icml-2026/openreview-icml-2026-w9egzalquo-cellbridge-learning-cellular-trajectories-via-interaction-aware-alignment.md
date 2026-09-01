---
title: "CellBRIDGE: Learning Cellular Trajectories via Interaction-Aware Alignment"
title_zh: CellBRIDGE：通过交互感知对齐学习细胞轨迹
authors: "Silas Ruhrberg Estévez, Nicolas Huynh, Tennison Liu, Roderik M. Kortlever, Gerard I. Evan, David L. Bentley, Mihaela van der Schaar"
date: 2026-04-30
pdf: "https://openreview.net/pdf/887aeca6724901e89d85f6b834a19a0915bbc3b1.pdf"
tags: ["query:gene-perturb"]
score: 4.0
evidence: 利用交互感知最优传输推断单细胞轨迹，与细胞动态建模间接相关
tldr: 从群体快照推断细胞动态是单细胞计算的难题，标准最优传输仅用基因表达距离，忽略细胞间配体-受体通信。作者提出CellBRIDGE，在特征距离基础上引入细胞间交互信号，构建更具生物学意义的最优传输代价。实验表明该方法能够更准确地刻画细胞轨迹和状态转变，为理解细胞命运决定和构建虚拟细胞动态模型提供支持。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 标准最优传输推断单细胞轨迹时忽略细胞间信号通信，导致耦合生物学意义不足。
method: 在最优传输目标中引入配体-受体交互驱动的正则项，改进基因表达距离，获得交互感知的细胞轨迹对齐。
result: 实验证明交互感知对齐能够推断出更符合生物学的细胞状态转换轨迹。
conclusion: 为单细胞群体快照的动态推断提供了新的建模思路，可辅助虚拟细胞构建。
---

## Abstract
Inferring dynamics from population snapshots is a fundamental challenge in machine learning and biology. In scRNA-sequencing (scRNA-seq), destructive measurements preclude direct tracking of individual cells across time, making trajectory inference underdetermined. Optimal Transport (OT) provides a principled framework for snapshot alignment, but a long-standing modeling question is which cost functions yield biologically meaningful couplings. Standard OT approaches rely on gene-expression distances, implicitly treating cells as independent points and neglecting structured cell-cell communication mediated by ligand-receptor signaling. We introduce CellBRIDGE (Cell-Based Regularized Interaction-Driven Gene Expression), which augments feature-based OT with a directed, typed interaction cost derived from ligand-receptor activity. By explicitly modeling cell-cell communication, CellBRIDGE improves cross-snapshot couplings and downstream trajectory estimates across synthetic and real scRNA-seq datasets relative to feature-only baselines. Notably, CellBRIDGE enables mechanistically interpretable in silico perturbations: on lung cancer data, silencing specific ligand-receptor pairs induces trajectory shifts that recapitulate expected effects of targeted pathway inhibition.

---

## 论文详细总结（自动生成）

## 1. 核心问题与整体含义

- **研究背景**：单细胞 RNA 测序（scRNA-seq）是破坏性测量，无法直接追踪单个细胞随时间的变化，因此从群体快照（population snapshots）推断细胞动态本质上是欠定问题。
- **核心问题**：最优传输（Optimal Transport, OT）为快照对齐提供了原理性框架，但关键瓶颈在于选择何种代价函数才能产生具有生物学意义的耦合（coupling）。传统 OT 仅使用基因表达距离，将细胞视为独立点，忽略了细胞间由配体-受体（ligand-receptor）信号介导的结构化通信。
- **论文意义**：提出将细胞间通信纳入 OT 代价，实现更符合真实生物学过程的轨迹推断，为理解细胞命运决定和构建虚拟细胞动态模型提供新思路。

## 2. 方法论

- **方法名称**：CellBRIDGE（Cell-Based Regularized Interaction-Driven Gene Expression），即“基于细胞、交互驱动的基因表达正则化”。
- **核心思想**：在特征距离（基因表达距离）之外，引入由配体-受体活动驱动的**有向、类型化交互代价**，显式建模细胞-细胞通信，从而改进跨快照的耦合。
- **关键技术细节**：
  - 将配体-受体信号转化为细胞间的交互强度，并作为 OT 代价函数的补充项。
  - 采用“交互感知”的正则化，使最优传输不仅考虑表达相似性，还考虑细胞间的通信关系。
  - 最终得到的耦合矩阵具有更强的生物学解释性，下游轨迹估计更准确。
- **流程要点**：输入多个时间点的单细胞快照 → 计算基因表达距离 → 计算配体-受体交互代价 → 组合成统一代价 → 求解正则化最优传输 → 输出细胞状态转换轨迹。

## 3. 实验设计

- **数据集/场景**：
  - 合成 scRNA-seq 数据集（用于验证方法有效性的模拟数据）。
  - 真实 scRNA-seq 数据集（文中提及肺癌数据作为下游应用场景）。
- **Benchmark**：以“仅使用特征（feature-only）”的 OT 基线方法作为对比基准。
- **对比方法**：feature-only baselines（未引入交互信号的经典 OT 方法）。
- **下游任务**：
  - 跨快照耦合质量评估。
  - 轨迹估计精度。
  - 机制可解释的 in silico 扰动实验：在肺癌数据上沉默特定配体-受体对，观察轨迹变化是否重现靶向通路抑制的预期效果。

## 4. 资源与算力

- 论文摘要和元数据中**未明确说明** GPU 型号、数量、训练时长、显存占用等算力信息。
- 推测实验属于中等规模计算任务（单细胞数据 + 最优传输求解通常不需要大规模分布式训练），但具体资源配置无法从现有内容确认。

## 5. 实验数量与充分性

- **实验数量**：从摘要看至少包含：
  - 合成数据集上的验证实验；
  - 真实 scRNA-seq 数据集上的对比实验；
  - 肺癌数据上的扰动实验（相当于一个应用性案例）。
- **充分性评估**：
  - **优点**：覆盖了合成和真实数据，并包含下游扰动验证，形成“基础验证 + 应用验证”的闭环。
  - **不足**：缺少消融实验的具体描述（如交互代价权重敏感性、不同类型配体-受体信号的贡献等）；未报告统计显著性、重复次数和误差条；对比基线仅为 feature-only OT，范围较窄；未与其他先进的轨迹推断方法（如 Waddington-OT、CellRank、TrajectoryNet 等）进行比较。
  - **公平性风险**：没有说明基线是否经过同等调优，也没有说明是否使用相同的预处理和超参数设置。

## 6. 主要结论与发现

- 在合成和真实 scRNA-seq 数据上，CellBRIDGE 相比仅用基因表达特征的 OT 基线，能够显著提升跨快照耦合质量和下游轨迹估计的准确性。
- 显式建模细胞间通信（配体-受体信号）使轨迹推断更符合真实生物学。
- 在肺癌数据上进行 in silico 扰动时，沉默特定配体-受体对可引发轨迹偏移，且该偏移能重现靶向通路抑制的预期效应，证明方法具有机制可解释性和药物干预预测潜力。

## 7. 优点

- **方法新颖**：首次将配体-受体介导的细胞间交互信号纳入 OT 代价，弥补了传统方法忽略细胞通信的缺陷。
- **生物学合理性**：代价函数不再依赖纯表达距离，而是直接反映细胞间信号通信，更贴近真实生物过程。
- **机制可解释**：支持 in silico 扰动实验，能够模拟基因沉默/通路抑制对细胞命运的影响，对虚拟细胞建模和靶点发现具有实用价值。
- **适用性广**：可推广到其他依赖快照对齐的生物学动态推断问题。

## 8. 不足与局限

- **实验覆盖有限**：仅提及合成数据和肺癌数据，缺乏多个真实数据集、不同组织/疾病场景的验证，泛化能力有待证明。
- **对比基线不充分**：仅与 feature-only OT 对比，未与当前主流轨迹推断方法（如基于图的方法、基于深度生成模型的方法）比较，说服力有限。
- **缺乏消融与敏感性分析**：未说明交互代价的具体形式、权重选择、配体-受体数据库来源对结果的影响。
- **未讨论计算可扩展性**：大规模单细胞数据（数十万细胞）下，交互项计算可能成为瓶颈，但论文未提及优化策略。
- **偏差风险**：配体-受体数据库本身可能不完整或存在组织特异性偏差，可能影响交互代价的准确性；扰动实验仅证明“相关性”而非“因果性”，且未与真实实验数据直接对比。
- **信息不完整**：资源与算力、详尽实验设置、代码可用性等未在摘要中体现，影响可复现性评估。

（完）
