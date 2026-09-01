---
title: "Many Needles in a Haystack: Active Hit Discovery for Perturbation Experiments"
title_zh: 大海捞针：扰动实验中的主动命中发现
authors: "Andrea Rubbi, Arpit Merchant, Samuel Ogden, Amir Akbarnejad, Pietro Lio, Sattar Vakili, Mohammad Lotfollahi"
date: 2026-04-30
pdf: "https://openreview.net/pdf/a8d729f2e7151966430037653ee6bbe2ae1a4e4e.pdf"
tags: ["query:gene-perturb"]
score: 5.0
evidence: 高通量基因扰动实验中的主动命中发现
tldr: 该文针对高通量基因扰动实验中预算有限的问题，将命中发现形式化为序贯实验设计，提出Probability-of-Hit采集函数，直接按候选扰动表型效应超过阈值的概率进行排序。相比纯探索和贝叶斯优化，该方法能在有限预算内发现更多高价值扰动，为功能基因组学中的扰动筛选提供了高效的主动学习策略。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 高通量基因扰动实验预算有限，目标是尽可能多地发现表型效应超过阈值的扰动，而现有策略或低效或过分关注单一最优值。
method: 将命中发现形式化为序贯实验设计问题，提出Probability-of-Hit采集函数，根据扰动候选超过阈值的概率排序。
result: 实验表明所提采集函数在有限预算内能发现更多超出阈值的扰动，优于纯探索与贝叶斯优化。
conclusion: 为基因扰动实验的高效命中筛选提供了新方法。
---

## Abstract
High-throughput gene perturbation experiments can test several genetic interventions in parallel, yet experimental budgets remain limited. A central goal is hit discovery: identifying as many perturbations as possible whose phenotypic effect exceeds a predefined threshold. Pure exploration strategies are statistically inefficient, wasting budget on low-value regions. Bayesian optimization methods offer a principled alternative but target a single global optimum, over-exploiting dominant modes while neglecting other high-value regions. We formalize hit discovery as a sequential experimental design problem and propose Probability-of-Hit, an acquisition function that directly targets threshold exceedance by ranking candidates according to their posterior probability of being a hit. We prove asymptotic optimality of this approach and demonstrate strong empirical performance on both synthetic benchmarks and real biological immunology datasets, including upto 6.4\% improvement over baselines on the Schmidt IL-2 dataset.

---

## 论文详细总结（自动生成）

## 论文详细中文总结

### 1. 核心问题与整体含义（研究动机和背景）
- 高通量基因扰动实验可以并行测试多种遗传干预，但实验预算（可执行的扰动次数）仍然有限。
- 核心目标为**命中发现（Hit Discovery）**：在有限预算内，尽可能多地识别出表型效应超过预设阈值的基因扰动。
- 现有方法存在明显不足：
  - **纯探索策略**：统计效率低，大量预算被浪费在低价值区域。
  - **贝叶斯优化方法**：原则上更优，但通常优化单一全局最优值，易过度利用主导模式，忽略其他同样高价值的区域。
- 论文将命中发现重新形式化为**序贯实验设计问题**，以直接匹配“寻找所有超阈值扰动”这一实际目标。

### 2. 方法论：核心思想、关键技术细节与算法流程
- **核心思想**：不再追求单一最优解，而是直接估计每个候选扰动“成为命中”的概率，并按此概率排序，以指导下一轮实验。
- **提出采集函数**：**Probability-of-Hit（命中概率）**。
  - 基于高斯过程等代理模型，计算候选扰动的后验概率，判断其表型效应是否超过预设阈值。
  - 排序依据为 `P(效应 > 阈值 | 观测数据)`。
- **序贯实验设计流程**（文字说明）：
  1. 初始化：在少量扰动上做预实验，获得初始观测。
  2. 训练代理模型：根据已有数据拟合表型效应与扰动特征之间的映射。
  3. 计算采集函数：对所有未测试候选扰动，计算其命中后验概率。
  4. 选择下一批扰动：选取命中概率最高的若干候选进行并行实验。
  5. 更新数据集，重复步骤 2–4，直到预算耗尽。
- **理论保证**：论文证明了该方法**渐近最优性**（asymptotic optimality），即在无限预算下能够恢复所有真实命中。

### 3. 实验设计：数据集、Benchmark 与对比方法
- **数据集 / 场景**：
  - 合成基准（synthetic benchmarks）：用于验证方法在受控条件下的行为。
  - 真实生物学数据集：**Schmidt IL-2 数据集**（免疫学相关基因扰动实验）。
- **对比方法**：
  - 纯探索策略（随机/均匀采样等，文中未具体展开）。
  - 标准贝叶斯优化方法（以单一最优值为目标）。
- **评估指标**：在有限预算下发现的“命中”数量（即表型效应超过阈值的扰动数）。
- **主要结果**：在 Schmidt IL-2 数据集上，相比基线方法获得了最高 **6.4% 的提升**。

### 4. 资源与算力
- 论文摘要及元数据中**未明确说明**使用的 GPU 型号、数量、训练时长或总计算开销。
- 由于本文属于主动学习/序贯实验设计方向，计算开销通常集中于高斯过程等代理模型的训练，规模可能较小；但具体资源信息缺失，无法给出确切结论。

### 5. 实验数量与充分性
- 从已有信息看，实验包括：
  - 合成基准测试；
  - 一个真实免疫学数据集（Schmidt IL-2）上的验证。
- 但论文摘要中**未提及消融实验、不同预算规模对比、阈值敏感性分析、多种初始化策略**等细节。
- **充分性评估**：当前可见的实验覆盖范围有限，无法全面验证方法在不同数据规模、不同阈值、不同预算下的泛化能力。虽然真实数据集上有提升，但仅一个公开数据集，证据强度一般。若正文中包含更多实验（如多个数据集或多种基线），则另当别论，但根据提供的材料无法判断。

### 6. 主要结论与发现
- 将命中发现形式化为序贯实验设计问题，并直接优化“超过阈值概率”是一种有效策略。
- 提出的 Probability-of-Hit 采集函数在有限预算下能发现更多超出阈值的扰动，显著优于纯探索和标准贝叶斯优化。
- 该方法具有渐近最优性，具备理论支撑。
- 在真实免疫学数据集上实现了最高 6.4% 的命中率提升，展示了实际应用价值。

### 7. 优点
- **问题定义准确**：直接针对“命中发现”而非“单一最优值”，更贴合生物学扰动筛选的实际需求。
- **方法直观且可解释**：使用后验概率排序，自然平衡探索与利用，且易于引入并行实验。
- **理论保证**：提供了渐近最优性证明，增强了方法的可靠性。
- **实践验证**：在合成和真实数据上均有积极表现，特别是真实数据集上的改进具有实际意义。
- **应用前景**：适用于功能基因组学中的大规模扰动筛选，可有效节省实验成本。

### 8. 不足与局限
- **实验验证的广度和深度不够明确**：摘要仅提及一个真实数据集，缺乏多数据集、多种扰动类型、不同阈值和预算设置的系统评估。
- **基线的代表性不明**：对比的“纯探索”和“贝叶斯优化”的具体版本、超参数设置、公平性细节未在摘要中给出。
- **未报告计算资源**：难以评估方法的实际运行成本。
- **可能存在的偏差风险**：若代理模型假设不当（如高斯过程先验与实际表型分布不匹配），命中概率估计可能失真；论文未讨论模型的鲁棒性。
- **实际生物学约束考虑不足**：真实实验中存在批次效应、噪音、基因间相互作用等，摘要中未讨论方法如何应对这些干扰。

（完）
