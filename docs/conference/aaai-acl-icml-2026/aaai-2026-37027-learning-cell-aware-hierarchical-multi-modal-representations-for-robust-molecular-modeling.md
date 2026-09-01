---
title: Learning Cell-Aware Hierarchical Multi-Modal Representations for Robust Molecular Modeling
title_zh: 学习细胞感知的层次多模态表示以实现稳健分子建模
authors: "Mengran Li, Zelin Zang, Wenbin Xing, Junzhou Chen, Ronghui Zhang, Jiebo Luo, Stan Z. Li"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/37027/40989"
tags: ["query:gene-perturb"]
score: 5.0
evidence: 融合细胞响应的层次多模态分子建模表示学习
tldr: 该文指出现有分子建模常忽略细胞形态和基因表达等细胞响应，且缺乏跨分子-细胞-基因组层次的依赖建模。为此提出CHMR框架，联合学习分子的局部-全局结构与细胞响应的多模态表示，显式建模层次依赖，从而实现更稳健的分子性质预测。实验验证了细胞感知多模态信息对理解化学扰动传播和药物效应预测的价值。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 化学扰动对生物系统的影响需要通过细胞响应如形态和基因表达来体现，现有细胞感知方法存在模态缺失和层次建模不足。
method: 提出CHMR框架，联合建模分子与细胞响应的局部-全局依赖，捕获分子、细胞和基因组层次的层级关系。
result: 实验表明CHMR在分子性质预测上更稳健，验证了细胞感知层次建模的价值。
conclusion: 为融合细胞响应的分子建模提供了层次多模态表示学习框架。
---

## Abstract
Understanding how chemical perturbations propagate through biological systems is essential for robust molecular property prediction. While most existing methods focus on chemical structures alone, recent advances highlight the crucial role of cellular responses such as morphology and gene expression in shaping drug effects. However, current cell-aware approaches face two key limitations: (1) modality incompleteness in external biological data, and (2) insufficient modeling of hierarchical dependencies across molecular, cellular, and genomic levels. We propose CHMR (Cell-aware Hierarchical Multi-Modal Representations), a robust framework that jointly models local-global dependencies between molecules and cellular responses and captures latent biological hierarchies via a novel tree-structured vector quantization module. Evaluated on public benchmarks spanning 696 tasks, CHMR outperforms state-of-the-art baselines, yielding average improvements of 3.6% on classification and 17.2% on regression tasks. These results demonstrate the advantage of hierarchy-aware, multi-modal learning for reliable and biologically grounded molecular representations, offering a generalizable framework for integrative biomedical modeling.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
融合细胞响应的层次多模态分子建模表示学习。

### 2. 核心内容
该文指出现有分子建模常忽略细胞形态和基因表达等细胞响应，且缺乏跨分子-细胞-基因组层次的依赖建模。为此提出CHMR框架，联合学习分子的局部-全局结构与细胞响应的多模态表示，显式建模层次依赖，从而实现更稳健的分子性质预测。实验验证了细胞感知多模态信息对理解化学扰动传播和药物效应预测的价值。

### 3. 对应检索需求
predicting the effects of gene perturbations on cellular state。

### 4. 来源与原文
- Source：AAAI-2026-Accepted
- OpenReview：[https://ojs.aaai.org/index.php/AAAI/article/view/37027](https://ojs.aaai.org/index.php/AAAI/article/view/37027)
