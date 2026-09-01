---
title: What Makes a Representation Good for Single-Cell Perturbation Prediction?
title_zh: 什么样的表示对单细胞扰动预测是好的？
authors: "Wenkang Jiang, Yuhang Liu, Yichao Cai, Erdun Gao, Jiayi Dong, Ehsan Abbasnejad, Lina Yao, Javen Qinfeng Shi"
date: 2026-04-30
pdf: "https://openreview.net/pdf/87c4564ac98f6dc7a0f98c0582d84b95a17b175e.pdf"
tags: ["query:gene-perturb"]
score: 10.0
evidence: 为单细胞遗传扰动预测提出通用表示学习框架PerturbedVAE
tldr: 单细胞基因表达被与扰动无关的信息主导，而扰动特异的信号非常稀疏，导致现有表征容易混杂或丧失预测力。为此作者提出PerturbedVAE通用框架，显式分离扰动不变与扰动特异信息，解决信号不均衡问题。实验表明该框架能够学习可泛化的扰动预测表征，在多种单细胞扰动预测任务上超过现有方法，为因果表示学习和基础模型应用于基因扰动预测提供了新视角。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 现有方法难以应对单细胞数据中扰动不变信息占主导、扰动特异信号稀疏的问题，导致预测泛化性差。
method: 提出PerturbedVAE，通过显式分离扰动不变与扰动特异信息来平衡信号，学习可泛化的单细胞扰动预测表示。
result: 实验证明PerturbedVAE在单细胞扰动预测上取得更优的泛化性能，超越多种对比方法。
conclusion: 为单细胞扰动预测提供了新的表示学习准则与框架，推动该类模型的设计。
---

## Abstract
Single-cell perturbation modeling is fundamental for understanding and predicting cellular responses to genetic perturbations. However, existing approaches, from causal representation learning to foundation models, often struggle with an overlooked challenge: gene expression is dominated by perturbation-invariant information, while perturbation-specific signals are intrinsically sparse. As a result, learned representations either entangle invariant and perturbation-specific information, leading to spurious and non-generalizable predictors, or suppress perturbation-specific signals altogether, rendering them ineffective for prediction. To address this, we propose PerturbedVAE, a general framework designed to resolve this signal imbalance. The framework explicitly separates perturbation-specific information from dominant invariant structure and recovers causal representations to effectively utilize such information for prediction. We further provide an identifiability analysis that characterizes the conditions under which sparse perturbation effects can be reliably recovered, thereby clarifying how the framework can be concretely specified under such conditions. Empirically, PerturbedVAE achieves state-of-the-art performance on a widely used benchmark across multiple evaluation settings, yielding significant gains on out-of-distribution combinatorial predictions and uncovering interpretable perturbation-response programs.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究背景**：单细胞扰动建模是理解和预测细胞对遗传扰动响应的基础性任务，在药物发现、疾病治疗和功能基因组学中具有重要应用。
- **核心挑战**：现有方法（从因果表示学习到基础模型）普遍忽视了一个关键问题——**基因表达数据中绝大多数信息是与扰动无关的（perturbation-invariant）**，而扰动特异的信号（perturbation-specific）本质上非常稀疏。这种信号不平衡导致两种典型失败模式：
  - 学习到的表示将不变信息与扰动特异信息纠缠在一起，产生虚假且无法泛化的预测器；
  - 或者完全压制扰动特异信号，使表示对预测任务无效。
- **核心问题**：什么样的表示对单细胞扰动预测是好的？如何克服信号不平衡，学习可泛化的扰动预测表示？
- **整体含义**：本文对此提出了系统的回答——好的表示应当显式分离扰动不变与扰动特异信息，并提供理论条件说明稀疏扰动效应何时可被可靠恢复。

## 2. 论文提出的方法论

- **方法名称**：**PerturbedVAE**——一个通用的表示学习框架。
- **核心思想**：通过显式分离扰动不变信息与扰动特异信息，解决单细胞数据中信号不平衡的问题，从而恢复可用于预测的因果表示。
- **关键设计**：
  - 将基因表达分解为两个子空间：一个捕获主导的、扰动不变的结构信息；另一个捕获稀疏的、扰动特异的信息。
  - 两个子空间在编码过程中被显式分离，避免纠缠。
  - 在解码/预测阶段，利用分离后的扰动特异信息进行下游预测任务。
  - 提供了**可辨识性分析（identifiability analysis）**，刻画了稀疏扰动效应可以被可靠恢复的条件，为框架在具体场景下的实例化提供了理论指导。

## 3. 实验设计

- **数据集**：使用了广泛使用的公开 benchmark（摘要中未给出具体数据集名称，如 Perturb-CITE-seq 等，但标注为 “widely used benchmark”）。
- **评估场景**：
  - 多种评估设置（multiple evaluation settings）；
  - 重点包括**分布外组合预测（out-of-distribution combinatorial predictions）**——即测试集中包含训练时未见过的扰动组合。
- **对比方法**：涵盖了从因果表示学习到基础模型的多种现有方法（具体方法名称在摘要中未逐一列出）。
- **结果**：PerturbedVAE 在多个评估设置下达到 **state-of-the-art** 水平，在分布外组合预测任务上取得显著提升，并能够发现可解释的扰动响应程序（interpretable perturbation-response programs）。

## 4. 资源与算力

- 提供的材料（摘要和元数据）中**未明确说明**所使用的GPU型号、数量、训练时长或算力资源。
- 由于本文是 ICML-2026-Accepted 的论文，完整正文中可能包含实验细节，但在当前提供的文本范围内无法获取相关信息。

## 5. 实验数量与充分性

- **实验数量**：摘要显示实验涵盖了：
  - 多个评估设置；
  - 分布外组合预测任务；
  - 可解释性分析（扰动响应程序的发现）。
- **充分性评估**：
  - 从摘要来看，实验覆盖了核心的泛化性评测（尤其OOD组合预测）和模型可解释性，兼具预测性能与科学发现两个维度；
  - 但由于当前文本未提供详细实验数量、具体数据集规模、基线细节和消融实验信息，无法完全判断实验的完备程度；
  - 总体而言，基于“state-of-the-art”和“多个评估设置”的描述，实验设计是**合理的**，但更全面的评价需要参考完整论文。

## 6. 论文的主要结论与发现

- 单细胞基因表达中，扰动不变信息占主导地位、扰动特异信号稀疏，这是导致现有方法泛化性能差的关键原因。
- 好的扰动预测表示应**显式分离扰动不变与扰动特异信息**，而非将它们纠缠在一起或压制扰动特异信号。
- PerturbedVAE 框架能够有效解决信号不平衡问题，在单细胞扰动预测任务上取得最优的泛化性能。
- 提供了稀疏扰动效应可恢复性的理论条件，为后续方法设计提供了理论支撑。
- 学习到的表示能够揭示可解释的扰动响应程序，说明模型不仅预测准确，还具备生物学可解释性。

## 7. 优点

- **问题洞察深刻**：精准识别了单细胞扰动预测中“信号不平衡”这一关键痛点，切中现有方法的要害。
- **方法设计简洁有效**：显式分离不变与特异信息的思路清晰、通用，作为一个通用框架可适配多种下游任务和模型架构。
- **理论与实验双重验证**：既提供了可辨识性分析（理论保证），又通过实验验证了实际效果，增强说服力。
- **泛化能力突出**：在分布外组合预测任务上的显著提升，说明模型真正学到了可泛化的因果表示，而非过拟合已知扰动组合。
- **可解释性**：发现的扰动响应程序具有生物学意义的可解释性，推动模型从“黑箱预测”走向“科学发现”。

## 8. 不足与局限

- **实验细节未知**：基于现有文本无法获知具体的数据集名称、数据规模、评估指标和消融实验细节，难以完全评估方法的稳健性和各组件贡献。
- **对比方法覆盖不全**：摘要未列出完整的基线方法列表，无法确认对比的充分性和公平性。
- **泛化边界**：可辨识性分析给出了理论条件，但这些条件在实际数据中的满足程度尚不清楚，可能限制方法在极端稀疏或高噪声场景下的适用性。
- **计算成本**：框架引入显式的分离机制，可能增加模型复杂度和训练成本，而文中未提供相关资源消耗信息。
- **生物学验证深度**：虽然发现了可解释的扰动响应程序，但尚不清楚这些发现是否经过湿实验验证。
- **单细胞数据的批次效应等技术噪音**可能仍然影响分离效果的鲁棒性——摘要中未讨论这一实际应用中常见的问题。

---

（完）
