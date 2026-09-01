---
title: "GenePheno: Interpretable Gene Knockout-Induced Phenotype Abnormality Prediction from Gene Sequences"
title_zh: GenePheno：从基因序列可解释地预测基因敲除诱导的表型异常
authors: "Jingquan Yan, Yuwei Miao, Lei Yu, Yuzhi Guo, Xue Xiao, Lin Xu, Junzhou Huang"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/37114/41076"
tags: ["query:gene-perturb"]
score: 9.0
evidence: 直接从基因序列预测基因敲除诱导的表型异常
tldr: 基因敲除如何影响表型是功能基因组学的核心问题，但现有方法依赖人工整理的遗传信息，难以扩展到多种表型异常。GenePheno直接从基因序列出发，利用可解释模型同时预测基因敲除后多种表型异常是否存在，弥合序列与表型之间的模态鸿沟。实验表明其在多表型预测上优于依赖精选输入的基线方法，并具有更强的泛化性与可解释性。该工作为高通量基因扰动表型筛选提供了可行的序列级预测工具。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 现有基因敲除表型预测方法依赖人工整理遗传信息，扩展性和泛化性受限，且序列与表型间的模态鸿沟和多效性使任务困难。
method: 提出GenePheno，直接从基因序列预测基因敲除诱导的多种表型异常，利用可解释模块建模序列到表型的映射并处理多效性。
result: 在预测多种基因敲除表型异常上优于依赖精选遗传信息的方法，具备更好的扩展性和泛化能力。
conclusion: GenePheno提供了一种序列驱动的基因敲除表型预测方案，支持可扩展、假设驱动的实验设计。
---

## Abstract
Exploring how genetic sequences shape phenotypes is a fundamental challenge in biology and a key step toward scalable, hypothesis-driven experimentation. The task is complicated by the large modality gap between sequences and phenotypes, as well as the pleiotropic nature of gene–phenotype relationships. Existing sequence-based efforts focus on the degree to which variants of specific genes alter a limited set of phenotypes, while general gene knockout-induced phenotype abnormality prediction methods heavily rely on curated genetic information as inputs, which limits scalability and generalizability. As a result, the task of broadly predicting the presence of multiple phenotype abnormalities under gene knockout directly from gene sequences remains underexplored. We introduce GenePheno, the first interpretable multi-label prediction framework that predicts knockout-induced phenotypic abnormalities from gene sequences. GenePheno employs a contrastive multi-label learning objective that captures inter-phenotype correlations, complemented by an exclusive regularization that enforces biological consistency. It further incorporates a gene function bottleneck layer, offering human-interpretable concepts that reflect functional mechanisms behind phenotype formation. To support progress in this area, we curate four datasets with canonical gene sequences as input and multi-label phenotypic abnormalities induced by gene knockouts as targets. Across these datasets, GenePheno achieves state-of-the-art gene-centric Fmax and phenotype-centric AUC, and case studies demonstrate its ability to reveal gene functional mechanisms.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
直接从基因序列预测基因敲除诱导的表型异常。

### 2. 核心内容
基因敲除如何影响表型是功能基因组学的核心问题，但现有方法依赖人工整理的遗传信息，难以扩展到多种表型异常。GenePheno直接从基因序列出发，利用可解释模型同时预测基因敲除后多种表型异常是否存在，弥合序列与表型之间的模态鸿沟。实验表明其在多表型预测上优于依赖精选输入的基线方法，并具有更强的泛化性与可解释性。该工作为高通量基因扰动表型筛选提供了可行的序列级预测工具。

### 3. 对应检索需求
genetic perturbation effects in functional genomics。

### 4. 来源与原文
- Source：AAAI-2026-Accepted
- OpenReview：[https://ojs.aaai.org/index.php/AAAI/article/view/37114](https://ojs.aaai.org/index.php/AAAI/article/view/37114)
