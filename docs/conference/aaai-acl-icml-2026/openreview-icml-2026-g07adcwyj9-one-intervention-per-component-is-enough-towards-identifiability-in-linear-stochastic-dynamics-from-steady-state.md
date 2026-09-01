---
title: "One Intervention per Component is Enough: Towards Identifiability in Linear Stochastic Dynamics from Steady State"
title_zh: 每个组件一次干预足矣：从稳态数据识别线性随机动力学参数
authors: Saber Salehkaleybar
date: 2026-04-30
pdf: "https://openreview.net/pdf/5ef70df3c27b60c498418d0ace7087407c632f16.pdf"
tags: ["query:gene-perturb"]
score: 7.0
evidence: 以基因扰动实验为动机，研究从稳态干预数据识别系统参数的可辨识性
tldr: 在基因扰动等场景中往往只能获取稳态快照数据，难以用传统随机微分方程估计方法反推系统参数。论文证明在系统漂移图的每个强连通分量上做一次干预即可（在温和谱条件下）恢复Ornstein-Uhlenbeck过程的所有参数（至多差一个全局尺度）。该可辨识性结果为使用稳态干预数据推断基因调控动态提供了理论基础。这对大规模基因扰动实验的参数估计与扰动效应建模有直接指导意义。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 大规模基因扰动实验常只有稳态快照数据，传统依赖时间序列的估计方法不再适用，需要从干预稳态数据识别动力学参数。
method: 利用图结构的强连通分量分解，证明每个强连通分量只需一次干预即可在生成意义上辨识OU过程全部参数，并给出谱条件。
result: 理论上建立了线性随机动力学从稳态观测和干预数据的可辨识性结果，放宽了对时间轨迹数据的需求。
conclusion: 为基于稳态快照的基因扰动数据推断调控系统提供了保证，可支撑后续扰动响应预测模型的构建。
---

## Abstract
We study the problem of recovering the parameters of a multivariate Ornstein–Uhlenbeck (OU) process from steady-state observational and interventional data. In many applications, such as large-scale gene perturbation experiments, only stationary “snapshot” measurements are available, making standard stochastic differential equation estimation methods that rely on time-series trajectories inapplicable. We first establish an identifiability result: one intervention per strongly connected component (SCC) of the drift graph suffices to recover all OU process parameters generically up to a global scaling factor. This holds provided that the SCC condensation graph is connected with a single root and certain spectral nondegeneracy assumptions hold. We propose a recursive learning algorithm that orders SCCs topologically and, for each component, isolates its marginal dynamics and solves a linear system derived from the steady-state moment equations, leveraging parameters recovered for upstream components. Building on this theoretical foundation, we propose a regularized least-squares estimator that jointly minimizes residuals of the steady-state mean and covariance equations across observational and interventional data. Experiments on synthetic and real datasets demonstrate the effectiveness of our method in recovering parameters and predicting unseen interventions.

---

## 论文详细总结（自动生成）

# 中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究背景**：在大规模基因扰动实验中，通常只能获取干预后的稳态“快照”数据，而难以获得完整的随时间演化的轨迹数据。传统基于随机微分方程（SDE）的参数估计方法严重依赖时间序列，因此在这种情况下不再适用。
- **核心问题**：能否仅从稳态观测数据和干预数据中，识别（identify）一个多元 Ornstein–Uhlenbeck（OU）过程的全部参数？如果可以，至少需要多少次干预、在哪些位置进行干预？
- **整体意义**：该问题直接关系到从稳态基因扰动数据推断基因调控网络动态结构的可行性。论文给出了肯定回答：在温和的谱条件下，对漂移图（drift graph）的每个强连通分量（SCC）进行一次干预，即可在“生成意义”上恢复所有 OU 过程参数（至多差一个全局缩放因子）。这为使用稳态快照数据进行基因调控推断提供了理论基础。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：利用漂移图（drift graph）的强连通分量（SCC）分解，将整体系统按因果/依赖层级进行划分；通过对每个 SCC 施加一次干预，可以在拓扑排序下逐层恢复参数。
- **技术细节**：
  - 将 OU 过程的参数（漂移矩阵、扩散协方差等）与稳态均值、稳态协方差方程联系起来。
  - 利用稳态矩方程（steady-state moment equations），从观测和干预数据中构建关于未知参数的线性方程组。
  - 关键在于：先恢复上游 SCC 的参数，再将其作为已知量代入下游 SCC 的方程，从而避免高阶非线性耦合。
- **识别性条件**：
  - SCC 凝聚图（condensation graph）必须连通且具有单一根（single root）。
  - 满足一定的谱非退化假设（spectral nondegeneracy），避免参数不可分辨的退化情形。
- **算法流程**：
  1. 对漂移图做 SCC 分解，得到拓扑排序。
  2. 对每个 SCC 分别设计一次干预实验（在生成模型意义下）。
  3. 按照拓扑顺序，对每个 SCC 提取其边际稳态动力学。
  4. 基于稳态均值与协方差方程，利用已恢复的上游参数构建并求解线性系统。
  5. 最后引入正则化最小二乘估计器，在观测和干预数据上联合最小化稳态均值与协方差方程的残差，得到最终参数估计。
- **估计器**：基于上述识别性理论，提出正则化最小二乘估计器，可同时拟合观测数据和干预数据的稳态矩约束。

## 3. 实验设计：使用的数据集 / 场景、benchmark、对比方法

- **数据集 / 场景**：论文提到进行了“合成数据与真实数据”上的实验。
  - 合成数据：用于验证算法在已知真实参数下的恢复效果。
  - 真实数据：与基因扰动或调控网络相关的数据集（具体名称、规模在摘要中未给出）。
- **Benchmark**：摘要中没有明确列出基准数据集或标准对比对象。
- **对比方法**：摘要中没有提及与哪些已有方法进行了对比，仅说明了所提方法的有效性。

## 4. 资源与算力

- **未明确说明**：论文摘要和元数据中未提及 GPU 型号、数量、训练时长、计算集群等任何算力资源信息。
- 因此，关于资源与算力无法给出具体总结。

## 5. 实验数量与充分性

- **实验数量**：摘要仅概括性地提到“在合成和真实数据集上的实验”，未给出具体实验组数、消融实验数量或不同设置的数量。
- **充分性分析**：
  - **不足**：缺少对算法在噪声水平、SCC 数量、图规模、干预强度等维度上的系统实验描述；未报告与其他估计方法的比较结果。
  - **客观性**：从摘要看，实验结论宣称“有效”，但缺乏可验证的细节（如误差指标、参数恢复精度等），因此难以判断实验的全面性和公平性。

## 6. 论文的主要结论与发现

- **可辨识性结论**：在漂移图的每个强连通分量上施加一次干预，即可在生成意义上识别出 OU 过程的全部参数（至多差一个全局缩放因子），前提是 SCC 凝聚图连通且只有单一根，并满足谱非退化条件。
- **算法可行**：提出的递归学习算法能够按拓扑顺序逐步恢复参数，并借助正则化最小二乘估计器在真实数据上取得良好效果。
- **理论价值**：这一结果放宽了对时间序列轨迹数据的依赖，使稳态快照数据也可用于动态系统参数推断，为基因调控网络建模提供了新的理论基础。

## 7. 优点：方法或实验设计上的亮点

- **理论突破**：首次（或在该框架下）证明了每个 SCC 一次干预即可实现可辨识性，干预次数需求达到下界意义，效率高。
- **方法合理**：利用 SCC 依赖结构进行递归分解，将整体非线性问题转化为逐层线性问题，简洁且可扩展。
- **适用范围广**：针对稳态快照数据，解决了大规模基因扰动实验中的实际瓶颈。
- **联合优化**：同时利用均值与协方差方程的残差，提高了参数估计的信息利用率。

## 8. 不足与局限

- **实验细节缺失**：摘要未提供实验设置细节，包括数据规模、图类型、噪声条件、对比基线、误差度量等，难以评估方法的实际性能边界。
- **假设较强**：需要 SCC 凝聚图连通且单一根、谱非退化等条件，在真实生物网络中是否总能满足尚需验证。
- **全局尺度模糊**：参数至多差一个全局缩放因子，这在实际生物学解释中可能带来不确定性（例如基因调控强度的绝对大小不可知）。
- **未提及鲁棒性**：没有讨论观测噪声、缺失数据、干预不完全（如部分 CRISPR 扰动泄漏）等情况下的表现。
- **缺少外部验证**：未与其他因果推断或动态系统识别方法进行比较，无法说明相对优势。

（完）
