---
title: "scCBGM: Single-Cell Editing via Concept Bottlenecks"
title_zh: scCBGM：基于概念瓶颈的单细胞编辑
authors: "Alma Andersson, Aya Abdelsalam Ismail, Edward De Brouwer, Doron Haviv, Tommaso Biancalani, Kyunghyun Cho, Gabriele Scalia, Aicha BenTaieb, Hector Corrada Bravo"
date: 2026-04-30
pdf: "https://openreview.net/pdf/f9bbe8d507a99f605b5e6830d730e0c86d2540d1.pdf"
tags: ["query:gene-perturb"]
score: 9.0
evidence: 单细胞概念瓶颈生成模型，用于细胞扰动响应的反事实编辑
tldr: 针对单细胞CRISPR等高维扰动空间难以穷尽实验的问题，作者提出scCBGM，把概念瓶颈架构引入单细胞数据，通过解码器跳跃连接与交叉协方差惩罚实现可解释且解耦的细胞反事实编辑，并扩展至流匹配生成模型。该框架在编码-解码和生成两种机制下均支持概念引导的扰动预测，实验表明其能够精准编辑单个细胞的表型状态，为解读基因扰动对细胞状态的影响提供新工具，有望加速疾病机制与治疗设计研究。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 单细胞扰动组合空间巨大，实验穷举不可行，需要可解释的计算模型预测细胞对扰动的响应。
method: 将概念瓶颈架构适配到单细胞数据，采用解码器跳跃连接和交叉协方差惩罚实现解耦表示，并扩展到流匹配生成模型进行概念引导编辑。
result: 实验表明scCBGM能精准进行单细胞反事实编辑，在多种机制下均支持概念引导的扰动预测。
conclusion: 该工作为单细胞扰动响应预测提供可解释、生成式的建模框架，助力疾病与治疗研究。
---

## Abstract
Understanding cellular phenotypes and how they respond to perturbations is critical for disease biology and therapeutic design. Single-cell RNA sequencing enables characterization at cellular resolution, yet the combinatorial space of conditions makes exhaustive experimental mapping infeasible. We introduce single-cell Concept Bottleneck Generative Models (scCBGM), a framework for interpretable and precise counterfactual editing of individual cells. scCBGM adapts concept bottleneck architectures for single-cell data through decoder skip connections and a cross-covariance penalty that promotes disentanglement without dimensional constraints. We extend the framework to flow matching models, enabling concept-guided editing in both encoding-decoding and generation regimes. To enable rigorous evaluation, we develop a synthetic benchmark with ground-truth counterfactuals. Across multiple real datasets, scCBGM demonstrates superior performance in combinatorial generalization and counterfactual prediction, supported by cell-level validation on synthetic data and population-level benchmarks on real datasets.

---

## 论文详细总结（自动生成）

# scCBGM 论文详细中文总结

## 1. 核心问题与整体含义

- **研究背景**：理解细胞表型及其对扰动的响应是疾病生物学与治疗设计的关键。单细胞 RNA 测序（scRNA-seq）能够在单细胞分辨率下刻画细胞状态，但扰动的组合空间极其庞大，无法通过穷举实验进行完整映射，需要计算模型来预测未见过的扰动响应。
- **核心问题**：现有方法缺乏对扰动效应的可解释性，且难以在单细胞层面实现精准、解耦的反事实编辑。
- **整体含义**：本文提出了一种可解释、生成式的单细胞编辑框架，让研究者能对单个细胞进行"概念引导"的反事实编辑，从而在不进行全部实验的情况下推断基因扰动对细胞状态的影响，为疾病机制研究和治疗设计提供帮助。

## 2. 方法论

- **核心思想**：将**概念瓶颈（Concept Bottleneck）架构**引入单细胞数据建模，通过显式定义"概念"（可解释的细胞状态特征）作为中间表征，使模型对细胞的编辑过程可解释、可控制。
- **关键技术细节**：
  - **解码器跳跃连接（Decoder Skip Connections）**：适应单细胞数据的高维稀疏特性，改善信息流动与重建质量。
  - **交叉协方差惩罚（Cross-Covariance Penalty）**：在无维度约束的前提下促进表征解耦，使不同概念对应独立的变化方向，提升编辑的精准性。
  - **扩展到流匹配生成模型（Flow Matching）**：支持在**编码-解码**和**生成**两种机制下进行概念引导编辑，增强适用性。
- **算法流程（文字描述）**：
  1. 将单细胞转录组数据输入编码器，得到潜在概念表示；
  2. 通过交叉协方差惩罚约束概念解耦；
  3. 通过解码器（含跳跃连接）重建细胞状态；
  4. 在概念空间中对目标概念进行定向修改（扰动）；
  5. 解码修改后的概念得到反事实细胞状态，或在生成模式下用流匹配模型采样新细胞。

## 3. 实验设计

- **数据集/场景**：
  - 构建了一个**合成基准（synthetic benchmark）**，包含 ground-truth 反事实结果，用于严格的细胞级验证；
  - 在**多个真实单细胞数据集**上进行了群体级基准评估。
- **Benchmark**：组合泛化（combinatorial generalization）与反事实预测（counterfactual prediction）性能，并在合成数据上支持细胞级验证，真实数据上采用群体级验证。
- **对比方法**：摘要中未明确列出具体对比的方法名称，仅表示 scCBGM 在性能上优于现有方法；具体对比方法需查阅全文。

## 4. 资源与算力

- 摘要与元数据中**未明确说明**使用的 GPU 型号、数量、训练时长等算力信息。
- 只能推测其模型规模（概念瓶颈 + 流匹配）在标准深度学习硬件上可训练，但具体资源需求无法从本文材料中确认。

## 5. 实验数量与充分性

- **实验数量**：目前可见的实验包括一个合成基准和多个真实数据集的评估，覆盖编码-解码与生成两个机制；合成数据上有细胞级验证，真实数据上有群体级验证；另外包含交叉协方差惩罚、跳跃连接等消融性设计特征（但消融实验的数量和细节未在摘要中列出）。
- **充分性与客观性**：
  - **优点**：合成基准提供 ground-truth 反事实，能进行定量验证；多个真实数据集增强结论的普适性；
  - **不足**：真实数据集缺乏 ground-truth 反事实，只能群体级间接验证；对比方法和消融实验的细节不足，难以全面判断公平性；缺少对失败案例和边界条件的讨论。

## 6. 主要结论与发现

- scCBGM 在组合泛化和反事实预测上表现优越，能精准编辑单个细胞的表型状态。
- 概念瓶颈结合解码器跳跃连接与交叉协方差惩罚，可实现无维度约束的表征解耦，兼顾可解释性和生成能力。
- 扩展至流匹配模型后，在编码-解码和生成两种机制下均支持概念引导的扰动预测，为单细胞扰动响应建模提供了新范式。
- 总体结论：该工作提供了可解释、生成式的单细胞反事实编辑工具，有助于加速疾病机制与治疗设计研究。

## 7. 优点

- **可解释性**：概念瓶颈架构使扰动编辑过程透明，便于生物学解读。
- **方法创新**：解码器跳跃连接 + 交叉协方差惩罚，解决单细胞高维稀疏和解耦难题；扩展到流匹配生成模型，拓宽适用范围。
- **验证严谨**：合成基准提供 ground-truth 反事实验证，是评估反事实模型的重要贡献。
- **应用价值**：无需穷举实验即可预测扰动响应，对大规模扰动空间研究有实际意义。

## 8. 不足与局限

- **实验细节不足**：对比方法、消融实验数量、具体数据集名称与规模、评估指标并未详细列在摘要中，难以全面判断实验充分性与公平性。
- **真实数据验证局限**：真实数据无 ground-truth 反事实，只能群体级验证，无法精确衡量单细胞水平准确性。
- **算力信息缺失**：未报告训练资源与成本，不利于复现和扩展。
- **概念定义依赖**：概念瓶颈方法要求事先定义或可学习有意义的"概念"，这在高维未知生物学场景中可能困难。
- **推广性**：主要针对转录组数据，对其他模态（如蛋白、染色质）的适用性未提及。

（完）
