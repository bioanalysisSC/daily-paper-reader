---
title: "Beyond Continuity: Simulation-free Reconstruction of Discrete Branching Dynamics from Single-cell Snapshots"
title_zh: 超越连续性：从单细胞快照无模拟重建离散分支动力学
authors: "Junda Ying, Yuxuan Wang, Bowen Yang, Peijie Zhou, Lei Zhang"
date: 2026-04-30
pdf: "https://openreview.net/pdf/08547660f43ba7c30c8f9e80b3b51f73caa9a2e9.pdf"
tags: ["query:gene-perturb"]
score: 6.0
evidence: 从单细胞快照无模拟重建离散分支动力学，可用于虚拟细胞建模
tldr: 针对单细胞快照数据只能破坏性采样的问题，作者提出非平衡薛定谔桥（USB），一种免模拟的动态学习框架，在单细胞分辨率下整合随机性与出生-死亡等非保守质量效应，重建离散分支轨迹。相比连续流体假设的均衡最优传输方法，USB能更真实地刻画谱系分支与命运决定，为从快照数据构建虚拟细胞动态模型提供了新的计算工具。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 现有单细胞轨迹推断多将细胞群视为连续流体，难以刻画结构离散、出生死亡等离散特征，需要更精细的单细胞动态建模。
method: 提出非平衡薛定谔桥（USB）的免模拟框架，结合随机扩散和非平衡质量变化，在单细胞水平重建离散分支动力学。
result: 该框架有效整合随机性和非保守效应，在理解谱系分支和细胞命运决定上优于基于连续流体的最优传输方法。
conclusion: USB为单细胞快照下的细胞动态重建提供了新途径，有望用于虚拟细胞建模和生物学系统仿真。
---

## Abstract
Inferring cellular trajectories from destructive snapshots is complicated by the challenges of stochasticity and non-conservative mass dynamics such as cell proliferation and apoptosis. Existing unbalanced Optimal Transport (OT) methods treat mass as a continuous fluid, performing inference at the population level. However, this macroscopic view often fails to capture the discrete, jump-like nature of birth-death events at single-cell resolution, which is essential for understanding lineage branching and fate decisions.  We present **Unbalanced Schrödinger Bridge (USB)**, a simulation-free framework for learning underlying dynamics that effectively integrates both stochastic and unbalanced effects which also models the discrete, jump-like birth–death dynamics at single-cell resolution. Theoretically, USB provides a tractable solution to the Branching Schrödinger Bridge (BSB) problem, offering a rigorous microscopic interpretation where individual cells undergo both Brownian motion and discrete birth-death jumps. Technically, the method implements an efficient solver by introducing a simulation-free training objective that effectively scales to high-dimensional omics data. Empirically, we demonstrate on both simulated and real-world datasets that USB not only achieves trajectory reconstruction performance better than or comparable to deterministic baselines but also uniquely enables realistic discrete simulation of birth-death dynamics at single-cell resolution.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机与背景）

- **研究背景**：单细胞测序技术通常具有破坏性，即细胞在被测量时已经死亡，因此研究者只能获取某一时刻的“快照”数据，而无法直接追踪单个细胞随时间的变化。如何在这样的快照数据中重建细胞动态轨迹，是单细胞生物学中的一个核心挑战。
- **已有方法的不足**：现有方法（尤其是基于非平衡最优传输（Unbalanced Optimal Transport, OT）的方法）通常将细胞群体视为**连续流体**，在群体水平上进行推断。这种宏观视角忽略了单细胞分辨率下细胞增殖（birth）与凋亡（death）等事件具有**离散、跳跃式**特征，而这些离散特性恰恰是理解**谱系分支（lineage branching）** 与**细胞命运决定（fate decision）** 的关键。
- **核心问题**：如何构建一个能够同时整合随机性（stochasticity）与非保守质量效应（如出生-死亡过程），并且能在单细胞分辨率下刻画离散分支动力学的学习框架。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：作者提出 **非平衡薛定谔桥（Unbalanced Schrödinger Bridge, USB）** ，这是一个**免模拟（simulation-free）** 的动态学习框架。它不对细胞群做连续流体近似，而是在单细胞水平上，将细胞的动态建模为**布朗运动（连续随机扩散）** 与**离散出生-死亡跳跃**的组合。
- **理论贡献**：论文为 **分支薛定谔桥（Branching Schrödinger Bridge, BSB）** 问题提供了可解的方案，赋予了该问题一个严格的微观解释：每个细胞既经历布朗运动，也经历离散的出生-死亡跳跃。
- **技术实现**：引入一种**免模拟的训练目标**（即不需要通过前向模拟随机过程来训练模型），使求解器能够高效扩展到高维组学数据（如单细胞转录组）。这一设计是该方法在实际数据上可行的关键。

## 3. 实验设计

- **数据集**：作者在**模拟数据集（simulated datasets）** 和**真实世界数据集（real-world datasets）** 上进行了验证。
- **Benchmark 与对比方法**：与**确定性基线方法**（包括基于连续流体假设的非平衡最优传输等方法）进行了对比，考察轨迹重建性能。
- **评估指标**：重点评估（1）轨迹重建的准确性；（2）是否能够实现单细胞分辨率的**离散出生-死亡动力学仿真**（这是基线方法不具备的能力）。

## 4. 资源与算力

- 论文摘要与元数据中**未明确说明**实验所使用的 GPU 型号、数量、训练时长或具体算力资源。
- 需要指出：由于本轮分析仅能基于论文摘要与元数据（PDF 提取内容为验证页面），因此无法获取更详细的实验环境信息。

## 5. 实验数量与充分性

- 根据已有信息，实验涵盖**模拟数据 + 真实数据**两类场景，并进行了与确定性基线的性能对比。
- 目前可见信息中**未提及消融实验**的设计（例如：随机性分量 vs. 离散出生-死亡分量各自的贡献；免模拟训练目标的有效性验证等）。
- 客观评价：实验设计覆盖了基础验证需求，但对于 ICML 级别论文而言，**若缺少系统性的消融研究和敏感性分析，充分性可能略显不足**；不过由于信息有限，此结论需谨慎表述。
- 公平性方面：考虑了与现有方法的对比，但无法判断超参数调优与基线实现是否完全公平。

## 6. 主要结论与发现

- **性能优势**：在轨迹重建任务上，USB 的表现**优于或可比于**确定性基线方法。
- **独特能力**：USB 是唯一能够在单细胞分辨率下**真实地模拟离散出生-死亡动力学**的方法，这一能力对于研究谱系分支和命运决定至关重要。
- **理论价值**：为分支薛定谔桥问题提供了可计算的理论解，连接了随机扩散过程与离散分支过程。
- **应用前景**：该方法为从快照数据构建**虚拟细胞动态模型**提供了新的计算工具。

## 7. 优点

- **方法创新性强**：打破了以往将细胞群视为连续流体的范式，首次在单细胞层面将连续扩散与离散出生-死亡事件统一在一个可解框架中。
- **理论严谨**：将问题形式化为分支薛定谔桥问题，并给出了可处理的解，兼具理论深度与实用性。
- **实用性高**：免模拟的训练设计使得方法能够扩展到高维组学数据，具有实际落地价值。
- **能力差异化**：不仅能重建轨迹，还能进行单细胞分辨率的离散动力学模拟，这是传统最优传输方法无法实现的功能。

## 8. 不足与局限

- **信息不完整**：由于本轮可用的论文信息有限（仅有摘要与元数据），无法全面评估方法的细节、实验设计完整性和技术局限性。
- **算力信息缺失**：论文未交代训练成本与硬件需求，难以评估其资源门槛。
- **消融与敏感性分析未见**：没有看到对随机性、出生-死亡项、超参数等关键设计组件的消融验证。
- **真实数据验证范围有限**：未明确说明真实数据集的种类（如具体组织/疾病类型）、规模及技术平台，难以判断泛化能力。
- **适用边界有待探讨**：该方法的理论假设（布朗运动 + 离散跳跃）在何种生物学场景下成立、偏离这些假设时鲁棒性如何，目前信息不足以判断。
- **与现有工具的对比深度**：是否与当前最先进的轨迹推断工具（如 Waddington-OT、CellRank 等）进行了充分对比，尚不明确。

（完）
