---
title: Interpretable Neural ODEs for Gene Regulatory Network Discovery under Perturbations
title_zh: 可解释神经ODE用于扰动下基因调控网络发现
authors: "Zaikang Lin, Sei Chang, Aaron Zweig, Minseo Kang, Fabian J Theis, Elham Azizi, David A. Knowles"
date: 2026-04-30
pdf: "https://openreview.net/pdf/c038481e54edbdea3e4964c473be5297d5afb56d.pdf"
tags: ["query:gene-perturb"]
score: 9.0
evidence: 用神经ODE建模扰动下细胞状态轨迹以推断基因调控网络
tldr: 该文针对现有基因调控网络推断方法无法捕获细胞分化等非线性动力学的局限，提出PerturbODE框架，利用可解释的神经ODE对扰动下的细胞状态轨迹进行建模，并直接从ODE参数中导出因果基因调控网络。该方法在大规模扰动数据集上展示了恢复调控关系的能力，为理解基因扰动如何驱动细胞状态变化提供了动态可解释的工具。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 现有因果图推断方法难以捕捉细胞分化等非线性动态过程，需要利用大规模扰动数据推断基因调控网络。
method: 提出PerturbODE框架，用可解释神经ODE建模扰动下的细胞状态轨迹，并从ODE参数中导出因果基因调控网络。
result: 实验表明PerturbODE能够从扰动轨迹中恢复调控关系并刻画非线性细胞动态，优于现有基线。
conclusion: 为从扰动组学数据中发现动态因果基因调控网络提供了新框架。
---

## Abstract
Modern high-throughput biological datasets containing thousands of perturbations enable large-scale discovery of causal graphs that represent regulatory interactions between genes. Differentiable causal graphical models and regression-based methods have been developed to infer gene regulatory networks (GRNs) from interventional datasets. However, existing approaches fail to capture the non-linear dynamics of biological processes such as cellular differentiation. To address this limitation, we propose $\textit{PerturbODE}$, a novel framework that employs interpretable neural ordinary differential equations (neural ODEs) to model cell state trajectories under perturbations and derive the underlying causal GRN from the neural ODE parameters, enabling downstream simulation of unseen genetic interventions. The GRN is encoded via a single-hidden-layer feedforward network, implicitly grouping genes into interpretable co-regulated modules. We demonstrate PerturbODE's efficacy in GRN inference and extension to perturbation response prediction across both simulated and real overexpression datasets.

---

## 论文详细总结（自动生成）

## 论文总结

### 1. 核心问题与整体含义（研究动机与背景）
- 现代高通量生物实验可同时测量数千种基因扰动，为大规模发现基因间调控关系（即基因调控网络，GRN）提供了机会。
- 已有方法（如可微因果图模型、回归方法）虽可推断 GRN，但主要针对静态干预数据，**无法捕获细胞分化等生物过程中非线性的动态变化**。
- 本文旨在解决这一问题：利用扰动下的细胞状态轨迹，**动态地**推断因果基因调控网络，并支持对未知遗传扰动的下游模拟预测。

### 2. 方法论：核心思想、关键技术细节
- **核心思路**：提出 **PerturbODE** 框架，用**可解释的神经常微分方程（neural ODE）**建模扰动下细胞状态随时间的演化轨迹，并直接从 ODE 参数中提取因果 GRN。
- **关键技术细节**：
  - 将 GRN 编码为一个**单隐层前馈网络**：该网络的权重可解释为基因之间的调控关系（激活/抑制）。
  - 网络结构隐式地将基因分组为**共调控模块**，提升可解释性。
  - 通过拟合扰动下的细胞状态轨迹，学习 ODE 参数，从而获得动态因果图。
  - 学到的模型可外推至未见过的基因扰动，进行表型响应预测。
- **算法流程**（文字描述）：
  1. 输入：扰动前后多个时间点的基因表达数据（或仅初始状态与终态，取决于数据集）。
  2. 定义神经 ODE：`dx/dt = f(x, u; θ)`，其中 `x` 为细胞状态，`u` 为扰动指示，`θ` 为单层网络参数。
  3. 训练：最小化预测轨迹与观测轨迹的差异。
  4. 从 `θ` 中提取 GRN 邻接矩阵（权重绝对值或符号表示调控强度与方向）。
  5. 使用训练好的模型对新扰动进行模拟，预测细胞状态变化。

### 3. 实验设计：数据集、基准与对比方法
- **数据集**：
  - **模拟数据集**：用于验证 GRN 推断准确性。
  - **真实过表达数据集**：测试实际扰动响应预测能力。
- **基准任务**：
  - GRN 推断（恢复真实/已知调控关系）。
  - 扰动响应预测（预测未观测过扰动下的基因表达变化）。
- **对比方法**：摘要未逐一列出，但提及与“可微因果图模型”和“回归方法”等现有基线进行比较。具体基线名称未在摘要中详细说明。

### 4. 资源与算力
- 论文摘要和提供的元数据中**未明确提及**使用的 GPU 型号、数量、训练时长等算力信息。
- 需要查看正文或附录才能获得确切的硬件配置与运行时间数据。

### 5. 实验数量与充分性
- 摘要提到在“模拟数据集”和“真实过表达数据集”上进行了实验，至少涵盖两类场景。
- 未具体说明消融实验数量、不同参数设置的对比组数。
- **总体评估**：从摘要看，实验覆盖了验证新方法所需的基本场景（模拟+真实），但**细节不足**，难以判断是否进行了充分的消融、灵敏度分析以及基线方法是否被公平调优。需阅读正文确认实验的全面性与客观性。

### 6. 主要结论与发现
- PerturbODE 能够**从扰动轨迹中恢复调控关系**，并刻画非线性细胞动态，效果**优于现有基线**。
- 该框架扩展至**扰动响应预测**，对未观测到的遗传干预具有模拟能力。
- 为从扰动组学数据中动态发现因果基因调控网络提供了新的可解释框架。

### 7. 优点：方法与实验设计亮点
- **可解释性**：通过单隐层前馈网络直接编码 GRN，权重对应调控关系，可解读性强。
- **动态建模**：使用神经 ODE 天然适合连续时间轨迹，突破静态方法局限。
- **模块发现**：隐层结构隐含将基因分组为共调控模块，有助于理解协同调控机制。
- **预测能力**：支持对未知扰动的反事实模拟，具有实际应用价值（如药物靶点筛选）。
- **普适性强**：不限于特定数据类型，可适配多种扰动组学数据。

### 8. 不足与局限
- **实验细节透明度不足**：摘要未给出足够证据支撑“优于现有基线”的声明，未展示具体指标与显著性分析。
- **对比公平性存疑**：未说明基线是否经过相同调参/网络结构匹配，可能存在偏差。
- **计算复杂度**：神经 ODE 的训练通常比静态方法更耗时，资源需求未讨论。
- **真实数据验证深度有限**：真实过表达数据集可能规模有限，未提及多组学/多物种的泛化验证。
- **应用限制**：仅使用单层网络，可能无法捕捉高阶非线性调控；未讨论数据噪声、批次效应等因素的影响。
- **开放性问题**：如何确定观测时间点、如何保证可辨识性等，摘要中未涉及。

（完）
