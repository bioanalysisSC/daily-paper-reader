---
title: Scalable Single-Cell Gene Expression Generation with Latent Diffusion Models
title_zh: 基于潜在扩散模型的可扩展单细胞基因表达生成
authors: "Giovanni Palla, Sudarshan Babu, Payam Dibaeinia, James D Pearce, Donghui Li, Aly A Khan, Theofanis Karaletsos, Jakub M. Tomczak"
date: 2026-04-30
pdf: "https://openreview.net/pdf/86ba29aafb9ac3b6caa7ae8a802438307e12d2ee.pdf"
tags: ["query:gene-perturb"]
score: 7.0
evidence: 生成式单细胞表达建模支持虚拟细胞模拟
tldr: 计算建模单细胞基因表达对于理解细胞过程至关重要，但现有生成模型常对基因施加人为顺序或使用浅层网络。本文提出可扩展的潜在扩散模型scLDM，利用统一多倍交叉注意力模块保持数据的可交换性，实现标准化的单细胞表达生成。相比现有方法，scLDM在保持基因可交换性的同时实现了更真实的表达分布建模，具有可扩展性。该模型为虚拟细胞建模与后续扰动响应预测提供了基础工具。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 现有单细胞基因表达生成模型受制于人为基因排序和浅层架构，难以生成真实表达谱。
method: 提出潜在扩散模型scLDM，采用固定大小潜在变量与统一多倍交叉注意力模块，保持基因可交换性。
result: 在单细胞表达生成上实现了可扩展且更真实的生成效果。
conclusion: 为单细胞表达建模和虚拟细胞模拟提供了一种可扩展的生成方法，可直接支持扰动预测等下游任务。
---

## Abstract
Computational modeling of single-cell gene expression is crucial for understanding cellular processes, but generating realistic expression profiles remains a major challenge. This difficulty arises from the count nature of gene expression data and complex latent dependencies among genes. Existing generative models often impose artificial gene orderings or rely on shallow neural network architectures. We introduce a scalable latent diffusion model for single-cell gene expression data, which we refer to as scLDM, that respects the fundamental exchangeability property of the data. Our VAE uses fixed-size latent variables leveraging a unified Multi-head Cross-Attention Block (MCAB) architecture, which serves dual roles: permutation-invariant pooling in the encoder and permutation-equivariant unpooling in the decoder. We enhance this framework by replacing the Gaussian prior with a latent diffusion model using Diffusion Transformers and linear interpolants, enabling high-quality generation with multi-conditional classifier-free guidance. We show its superior performance in a variety of experiments for both observational and perturbational single-cell data, as well as downstream tasks like cell-level classification.

---

## 论文详细总结（自动生成）

# 《基于潜在扩散模型的可扩展单细胞基因表达生成》论文总结

## 1. 核心问题与整体含义
- **研究背景**：单细胞基因表达的计算建模是理解细胞过程的重要基础。能够生成真实、可扩展、有条件可控的表达谱，是构建“虚拟细胞”、预测扰动响应和进行细胞状态模拟的关键前提。
- **核心难题**：基因表达数据天然是高维的计数型数据，基因之间存在复杂的潜在依赖关系。然而，现有生成模型存在两个主要缺陷：一是通过人为固定基因顺序建模，破坏了数据的**可交换性（exchangeability）**；二是依赖浅层网络架构，表达能力和生成质量有限。
- **总体意义**：本文提出的潜在扩散模型（scLDM）尊重基因表达数据的交换性，在保持可扩展性的同时实现了更高保真的生成，为虚拟细胞建模和扰动预测等下游任务提供了通用基础工具。

## 2. 方法论
- **核心思想**：在 VAE 框架下，先将高维基因表达压缩为固定大小的潜在变量，再用扩散模型替代高斯先验进行高质量生成，同时通过统一的多头交叉注意力模块保证潜在表征和生成过程均保持基因可交换性。
- **关键模块**：
  - **编码器**：使用统一 Multi-head Cross-Attention Block（MCAB）进行**置换不变池化（permutation-invariant pooling）**，使任意基因顺序都能映射到同一固定的潜在表示。
  - **解码器**：MCAB 反向执行**置换等变解池化（permutation-equivariant unpooling）**，将潜在变量还原为完整基因表达谱，避免人为预设基因顺序。
  - **潜在扩散模型**：使用 Diffusion Transformers 和**线性插值（linear interpolants）** 作为生成先验，替代传统高斯先验，提升生成质量。
  - **多条件无分类器引导（multi-conditional classifier-free guidance）**：支持观测与扰动等多类型条件输入，增强生成的可控性。
- **算法流程**（文字描述）：
  1. 编码阶段：输入基因表达谱，经 MCAB 置换不变池化得到固定维度的潜在变量 z；
  2. 扩散阶段：对 z 进行前向加噪，训练 Diffusion Transformer 学习反向去噪过程；
  3. 条件生成：在采样时通过多条件无分类器引导，从噪声中恢复潜在变量；
  4. 解码阶段：用 MCAB 置换等变解池化将潜在变量重建为完整的基因表达谱。

## 3. 实验设计
- **数据集与场景**：实验覆盖三大类任务——**观测性单细胞数据**（常规表达谱生成）、**扰动性单细胞数据**（如基因扰动后的表达预测）、以及**下游任务**（如细胞类型分类）。
- **Benchmark**：摘要中未明确列出使用的具体基准数据集名称（如 PBMC、TCGA 等），也未说明是否使用公共标准评测基准。
- **对比方法**：摘要仅提到现有生成模型存在基因人为排序和浅层架构的问题，但未列出对比方法的具体名称（如 scVI、scDiffusion、scVAE 等）。
- **评估指标**：未指明具体评价指标（如重构准确性、分布相似度、分类准确率等）。

## 4. 资源与算力
- **未明确说明**：论文摘要中未提到 GPU 型号、数量、训练时长、参数量或能耗等计算资源信息。
- 从方法本身（Diffusion Transformers）推断，训练成本通常较高，但由于信息缺失，无法给出量化结论。

## 5. 实验数量与充分性
- **实验数量**：摘要提到“various experiments”（多样化实验），覆盖观测、扰动和下游分类三个场景，但未给出具体实验组数、消融实验设置或统计显著性检验。
- **充分性评估**：
  - 场景覆盖较为全面（观测/扰动/下游），具有较强的实践导向；
  - 然而，由于未披露数据集详情、对比方法、评价指标和消融研究，难以判断实验结果的客观性与公平性，也缺少对不同模型复杂度和资源消耗的对比分析。

## 6. 主要结论与发现
- scLDM 在单细胞表达生成上达到了**可扩展且更真实**的效果，同时严格保持基因可交换性；
- 相比现有方法，scLDM 生成的表达分布更加真实，且在观测性、扰动性数据及细胞分类等下游任务上表现更优；
- 模型具备良好的扩展性，能够适应大规模基因集合，为虚拟细胞建模提供了可用的生成式基础工具。

## 7. 优点
- **设计动机明确**：以数据固有的可交换性为第一性原则，避免了基因排序带来的归纳偏置；
- **架构创新**：MCAB 同时承担编码器中的置换不变池化和解码器中的置换等变解池化，统一高效；
- **生成能力强**：将潜在扩散模型引入单细胞领域，显著优于传统浅层 VAE 或生成模型；
- **条件控制灵活**：多条件无分类器引导支持复杂实验条件（如多个扰动）的联合控制；
- **可扩展性**：固定大小的潜在变量使模型计算与基因数量解耦，支持大规模基因组的实际应用。

## 8. 不足与局限
- **实验细节缺失**：摘要中未披露具体数据集、对比方法、评估指标及消融实验，难以验证方法的通用性和优势显著性，存在**评估完整性不足**的风险；
- **交换性假设的适用边界**：模型假设基因完全可交换，但真实调控网络可能存在方向性或模块位序结构，该假设是否影响表达谱保真度尚需讨论；
- **信息瓶颈风险**：固定大小潜在变量可能成为信息瓶颈，对超大规模基因图谱（如全基因组）的保真度限制未做分析；
- **鲁棒性问题未讨论**：未涉及批次效应、测序深度差异、噪声分布偏移等单细胞数据常见问题；
- **可复现性受限**：未披露计算资源、代码或超参数，限制了后续工作的复现与对比；
- **应用范围**：论文仅展示生成和分类任务，对于下游更复杂任务（如扰动响应预测精度、药效模拟）的适配性与落地方案需要更多验证。

（完）
