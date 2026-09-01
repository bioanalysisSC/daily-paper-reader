---
title: "Beyond Independent Genes: Learning Module-Inductive Representations for Single-Cell Gene Perturbation Prediction"
title_zh: 超越独立基因：面向单细胞基因扰动预测的模块归纳表示学习
authors: "Jiafa Ruan, Ruijie Quan, Xu Liyang, Zongxin Yang, Yi Yang"
date: 2026-04-30
pdf: "https://openreview.net/pdf/5ddd173df6e8db1c4528d0dfe740ea452ff437d7.pdf"
tags: ["query:gene-perturb"]
score: 10.0
evidence: 面向单细胞基因扰动预测的模块归纳表示学习
tldr: 该文指出现有基因扰动预测方法大多假设基因独立或依赖静态先验，难以刻画扰动后基因程序的动态重组。为此提出scBIG框架，通过基因关系聚类从数据中归纳协同基因程序，并学习模块归纳表示来预测单细胞转录组对遗传扰动的响应。实验表明scBIG在基因扰动预测任务上显著优于现有方法，为功能基因组学中的扰动响应建模提供了显式程序级解决方案。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 基因扰动响应往往是协调的程序级变化，现有方法基于独立基因建模且依赖静态先验，无法捕捉动态重组。
method: 提出scBIG框架，通过基因关系聚类从数据中归纳基因程序，并学习模块归纳表示以预测扰动转录响应。
result: 实验证明scBIG能更好地预测单细胞基因扰动后的转录响应，优于现有方法。
conclusion: 为单细胞基因扰动预测提供了一种显式建模基因程序协调性的新方法。
---

## Abstract
Predicting transcriptional responses to genetic perturbations is a central problem in functional genomics. 
In practice, perturbation responses are rarely gene-independent but instead manifest as coordinated, program-level transcriptional changes among functionally related genes. 
However, most existing methods do not explicitly model such coordination, due to gene-wise modeling paradigms and reliance on static biological priors that cannot capture dynamic program reorganization.
To address these limitations, we propose scBIG, a module-inductive perturbation prediction framework that explicitly models coordinated gene programs. scBIG induces coherent gene programs from data via Gene-Relation Clustering, captures inter-program interactions through a Gene-Cluster-Aware Encoder, and preserves modular coordination using structure-aware alignment objectives. These structured representations are then modeled using conditional flow matching to enable flexible and generalizable perturbation prediction.
Extensive experiments on multiple single-cell perturbation benchmarks show that scBIG consistently outperforms state-of-the-art methods, particularly on unseen and combinatorial perturbation settings, achieving an average improvement of 6.7% over the strongest baselines. The code is available at https://github.com/ttruan2426-dot/scBIG.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义

- **研究背景**：预测遗传扰动（如基因敲除、过表达）后的转录组响应是功能基因组学的核心问题，对于理解基因调控机制、药物靶点发现和精准医学具有重要意义。近年来，单细胞测序技术的发展使得在单细胞分辨率下研究扰动响应成为可能。
- **核心挑战**：
  - 真实的基因扰动响应并非独立基因的简单叠加，而是表现为功能相关基因之间**协调的、程序级的转录变化**（即"基因程序"的协同重组）。
  - 现有方法大多采用基因独立建模范式（gene-wise modeling），将每个基因单独预测，**忽略了基因间的协同关系**。
  - 已有方法常依赖静态生物学先验知识（如预先定义的通路/调控网络），但这些静态先验**无法捕捉扰动后基因程序的动态重组与重编程**。
- **研究意义**：该工作将基因扰动预测从"独立基因回归"推进到"协调基因程序建模"的新范式，为理解扰动响应的系统级机制提供了可解释的程序级解决方案。

## 2. 方法论

论文提出 **scBIG**（单细胞模块归纳扰动预测框架），核心思想是：**从数据中显式归纳出协同的基因程序，并学习模块级的归纳表示，进而建模程序间的交互并预测扰动后的转录响应**。

主要技术流程（文字说明）：

1. **基因关系聚类（Gene-Relation Clustering）**：从数据中自适应地归纳出协同表达的基因模块（即基因程序），而非依赖预先定义的通路。通过聚类将高维基因空间划分为若干有意义的协同程序。
2. **基因簇感知编码器（Gene-Cluster-Aware Encoder）**：在归纳出的基因程序结构之上，设计专门的编码器以捕捉**程序间（inter-program）的交互关系**，从而建模基因程序的整体协调性。
3. **结构感知对齐目标（Structure-Aware Alignment Objectives）**：通过结构感知的对齐损失引导模型保持基因模块的协调一致性，确保学习到的模块表示在训练和预测中保持一致的结构性质。
4. **条件流匹配（Conditional Flow Matching, CFM）**：在模块化表示的基础上，使用条件流匹配生成模型来灵活地预测扰动后的转录组分布，从而实现**更通用的预测能力**（包括未见过的扰动和组合扰动）。

整体框架将"模块归纳"与"深度生成模型"相结合，实现了从基因程序级理解到转录组预测的端到端学习。

## 3. 实验设计

- **数据集/基准（Benchmark）**：使用**多个公开的单细胞基因扰动基准数据集**。具体数据集名称在摘要中未列出，但涵盖了常用的扰动预测benchmark（如 Perturb-seq 类数据）。
- **实验场景**：
  - **已知扰动的预测**（基础场景）
  - **未见扰动的预测**（unseen perturbations，泛化性测试）
  - **组合扰动预测**（combinatorial perturbations，多基因同时扰动的复杂场景）
- **对比方法**：与**当前最先进（state-of-the-art）的基线方法**进行对比，涵盖现有主流的独立基因建模方法和基于静态先验的方法。

## 4. 资源与算力

- **文中未明确说明**所消耗的计算资源信息。
- 摘要及提供的元数据中**没有提及**GPU型号、数量、训练时长、参数规模等细节。
- 从方法来看，scBIG使用了聚类、编码器与流匹配生成模型，估计需要GPU加速训练，但由于作者未披露，无法给出具体算力配置。

## 5. 实验数量与充分性

- **实验数量**：摘要中提及在"多个单细胞扰动基准"上进行"大量实验"，但未给出具体的实验组数。从摘要推断至少包括：基础预测实验、未见扰动实验、组合扰动实验，以及与多类基线方法的对比。
- **消融实验**：摘要中未明确提及消融实验，但作为ICML接收论文，通常应包括对各组件（聚类模块、编码器、对齐损失、流匹配）的消融分析——不过这一信息在提供的文本中无法确认。
- **充分性与公平性评估**：
  - 摘要声称在**多个**基准上一致优于SOTA，且平均提升6.7%，说明实验覆盖了多个独立场景，具有一定的充分性；
  - 但具体基线数、数据集规模、统计显著性测试、误差棒等细节**未提供**，无法完全评估其对比的公平性和稳健性；
  - 在**未见扰动**和**组合扰动**两个最具挑战性的场景上均取得提升，增强了结果的可信度。

## 6. 主要结论与发现

- scBIG通过显式建模**基因程序的协调性**（而非独立基因），能够在单细胞基因扰动预测任务上显著优于现有最先进方法。
- **关键发现**：
  - 基因程序级建模比独立基因建模更符合真实扰动响应的生物学本质；
  - 从数据中归纳基因程序（而非依赖静态先验）可以更好地捕捉扰动后的**动态重组**；
  - 模块化归纳表示在**未见扰动**和**组合扰动**的泛化场景中尤其有效。
- 平均在最强基线上提升 **6.7%**，验证了方法论的优越性。
- 代码已开源（https://github.com/ttruan2426-dot/scBIG），便于复现和后续研究。

## 7. 优点

- **范式创新**：首次将"模块归纳表示"引入单细胞扰动预测，突破了独立基因建模和静态先验依赖的双重限制，在方法论上具有新颖性。
- **生物学可解释性**：通过聚类归纳出协同基因程序，使得模型不仅预测准确，还能揭示扰动响应中哪些基因模块被协同调控，具有潜在的可解释价值。
- **动态性捕捉**：从数据中学习基因程序而非依赖预定义通路，能更好地反映扰动后的程序重组，适应不同扰动条件下的动态变化。
- **生成式建模**：使用条件流匹配（而非简单回归），能够建模转录组响应的高维分布特征，提供更灵活和概率性的预测。
- **泛化能力突出**：在最具挑战性的unseen和combinatorial perturbation设置下依然取得显著提升，说明方法具有良好的外推能力。
- **代码开源**：有利于社区复现和后续扩展。

## 8. 不足与局限

- **计算复杂度**：基因聚类 + 编码器 + 流匹配的串联框架可能引入较高的计算开销，文中未讨论大规模基因组的可扩展性。
- **实验细节透明度不足**：提供的信息中缺少具体数据集规模、基因数量、细胞数量、基线方法列表和具体评估指标，读者难以完全复现或验证实验结果。
- **消融实验不明**：未在摘要中明确各组件（聚类、对齐损失、流匹配）的独立贡献，难以判断每个设计选择的具体重要性。
- **偏差风险**：如果基准数据集集中于特定细胞类型或特定扰动类型，模型的泛化性可能只在这些范围内有效，需要更多异质数据验证。
- **生物验证缺失**：虽然方法具有可解释性潜力，但摘要中未提及对发现的基因程序进行独立生物学验证（如是否与已知通路/调控网络吻合）。
- **实际应用距离**：目前仍属于计算预测层面，尚未展示在真实湿实验中的验证或闭环应用。

（完）
