---
title: Leveraging Lineage Barcodes as Natural Augmentations for Contrastive Learning of Cell Fate in scRNA-seq Data
title_zh: 利用谱系条形码作为自然增强进行scRNA-seq数据中细胞命运的对比学习
authors: "Shizhao Joshua Yang, Yixin Wang, Kevin Z. Lin"
date: 2026-04-30
pdf: "https://openreview.net/pdf/9ac53adbde3fe75a73dce9529f48bb9031dfe2c9.pdf"
tags: ["query:gene-perturb"]
score: 4.0
evidence: 利用谱系条形码进行单细胞命运对比学习，可迁移至扰动响应预测
tldr: 单细胞谱系追踪数据中，分化程序常与细胞周期等无关过程混淆。本文提出谱系感知对比学习LCL，将可遗传的谱系条形码视为自然数据增强，用于分离谱系特异的命运信号。该方法采用半监督架构对齐未标记细胞，并向临床数据集迁移谱系结构。它属于细胞命运预测的方法，对理解扰动后细胞状态变化具有参考价值，但并未直接涉及基因扰动预测。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 细胞命运决定信号常被细胞周期等无关过程混淆，难以从谱系追踪中分离。
method: 提出谱系感知对比学习LCL，将谱系条形码作为自然增强，在半监督架构中学习命运相关表示。
result: 能更好分离谱系特异信号，并可迁移到无条形码的临床数据。
conclusion: 为单细胞细胞命运建模提供了新对比学习框架，可作为基因扰动响应预测的辅助方法。
---

## Abstract
Deciphering how cells commit to future fates is essential for developing precision therapeutics that can reprogram stem cells or modulate immune functions. However, isolating these fate-determining signals in single-cell lineage tracing (scLT) remains challenging because differentiation programs are often confounded by unrelated processes like the cell cycle. To address this, we introduce Lineage-aware Contrastive Learning (LCL), a framework that treats inheritable lineage barcodes as a "natural" data augmentation to isolate subtle, lineage-specific signals. LCL utilizes a semi-supervised architecture to align unlabeled cells, facilitating the transfer of lineage structures to clinical datasets where explicit barcoding is unavailable. We demonstrate LCL’s utility by predicting future cell-type compositions from early-time points, effectively modeling longitudinal fate commitment from cross-sectional data. Benchmarking on hematopoietic and fibroblast systems shows that LCL significantly outperforms standard models like scVI, establishing contrastive learning as a scalable paradigm for understanding and potentially manipulating cellular differentiation.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究背景**：理解细胞如何承诺并走向未来命运（cell fate commitment），是开发精准疗法（如重编程干细胞、调控免疫功能）的关键基础。
- **核心问题**：在单细胞谱系追踪（single-cell lineage tracing, scLT）数据中，分化程序信号常常与无关过程（如细胞周期）混淆，导致难以分离出真正决定细胞命运的特异性信号。
- **整体意义**：若能有效从谱系追踪数据中提取命运决定信号，就能实现从早期时间点预测未来的细胞类型组成，从而用横截面数据建模纵向命运承诺过程，为理解和操纵细胞分化提供可扩展的新范式。

## 2. 论文提出的方法论：核心思想、关键技术细节与算法流程

- **方法名称**：**LCL（Lineage-aware Contrastive Learning，谱系感知对比学习）**。
- **核心思想**：将**可遗传的谱系条形码（lineage barcodes）视为一种“自然”数据增强**。同一谱系内的细胞共享相同条形码，这天然构成了对比学习中的正样本对；通过拉近同谱系细胞表征、推远不同谱系细胞表征，可以隔离出谱系特异的命运信号。
- **关键技术细节**：
  - 采用**半监督架构**：对有谱系条形码标注的细胞进行对比学习，同时对无标注细胞进行对齐/一致性约束。
  - 通过这种设计，模型能够将学到的谱系结构**迁移到没有显式条形码的临床数据集**上。
- **算法流程（文字说明）**：
  1. 输入 scRNA-seq 谱系追踪数据，每个细胞携带基因表达谱与谱系条形码；
  2. 以条形码为监督信号构建正负样本对，进行对比学习；
  3. 对未标记细胞施加半监督对齐损失，使表征空间保持连贯；
  4. 训练完成后，利用早期时间点的表达数据预测未来细胞类型组成。

## 3. 实验设计：数据集 / 场景、基准与对比方法

- **数据集 / 系统**：造血系统（hematopoietic）和成纤维细胞系统（fibroblast）两个生物学系统。
- **任务场景**：
  - 从早期时间点预测未来细胞类型组成；
  - 将谱系结构迁移至无条形码的临床数据。
- **对比方法**：标准模型如 **scVI** 等基线方法。
- **评估方式**：以未来细胞类型组成的预测准确性等为 benchmark 指标。

## 4. 资源与算力

- **说明**：基于当前提供的信息（摘要与元数据），**文中未明确说明**使用的 GPU 型号、数量、训练时长等算力资源细节。
- 若需完整的资源消耗评估，需查阅论文正文的实验设置或补充材料。

## 5. 实验数量与充分性

- **已提及的实验**：
  - 两个不同生物学系统（造血、成纤维细胞）上的 benchmark；
  - 与 scVI 等标准模型的性能对比；
  - 向临床无条形码数据的迁移实验。
- **充分性评价**：
  - 数据集覆盖了两个系统，具有一定代表性；但覆盖范围有限，尚不足以全面证明方法的普适性。
  - 元数据中未明确提及**消融实验**（如去掉对比学习、去掉半监督对齐等），若正文中缺失，会影响对方法各组件贡献的归因分析。
  - 公平性：需要进一步确认是否与 scVI 在相同网络结构、训练预算、超参数调优条件下比较，才能判断是否公平。

## 6. 论文的主要结论与发现

- LCL 能够**显著优于 scVI 等标准模型**，在细胞命运预测任务上表现更佳。
- 将谱系条形码作为自然数据增强，是**分离谱系特异信号**的有效策略。
- 对比学习可作为一种**可扩展的范式**，用于理解乃至操纵细胞分化过程。
- 该方法具有迁移能力，能将谱系结构知识从带条形码的实验数据传递到无条形码的临床数据。

## 7. 优点

- **思想新颖**：将谱系条形码类比为“自然增强”，是对比学习在生物学数据上的巧妙应用，区别于传统人工增强策略。
- **方法实用**：采用半监督架构，能利用大量未标记数据，并支持迁移到临床数据集，实用性较强。
- **任务有深度**：从横截面数据建模纵向命运承诺，解决了实际实验成本高、难以长期追踪的痛点。
- **基准选择合理**：选择了造血和成纤维细胞等经典分化系统进行验证，具有一定的生物学参考价值。
- **有应用潜力**：虽然未直接做基因扰动预测，但为扰动响应预测提供了可参考的表示学习方法。

## 8. 不足与局限

- **算力信息缺失**：未报告训练资源（GPU 型号/数量/时长），影响复现成本评估。
- **实验覆盖有限**：仅两个生物学系统，结论的普适性有待更多细胞类型和物种验证。
- **与基因扰动的关联不直接**：该方法本身是细胞命运表示学习框架，并非直接的基因扰动响应预测方法；与扰动预测的结合仅是潜在方向，缺乏直接实验验证。
- **对比方法单一**：仅提到 scVI 等标准模型，未提及与更多最新单细胞表示学习方法或专门命运预测模型的对比。
- **消融与敏感性分析不明确**：元数据中未显示对损失函数各组件、条形码噪声、数据规模等变量的消融实验与鲁棒性分析。
- **生物学解释性**：对比学习得到的表征可能缺乏显式的生物学可解释性，需额外验证学到的信号是否确实对应已知的谱系决定因子。

（完）
