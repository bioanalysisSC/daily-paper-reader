---
title: Gene Incremental Learning for Single-Cell Transcriptomics
title_zh: 单细胞转录组学中的基因增量学习
authors: "Jiaxin Qi, Yan Cui, Jianqiang Huang, Gaogang Xie"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/37062/41024"
tags: ["query:gene-perturb"]
score: 4.0
evidence: 单细胞转录组中的基因增量学习
tldr: 该文注意到计算机视觉中的类别增量学习研究众多，而基因作为token同样具有增长性却很少被研究。作者以大规模单细胞转录组数据为例，提出基因增量学习流水线并建立相应评估，发现基因级遗忘问题同样存在。这项工作为单细胞模型适应不断增长的基因集合提供了新思路。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 现有增量学习研究聚焦于视觉类别，而对基因这类token的增长性研究很少，导致单细胞转录组模型难以适应新基因并存在遗忘问题。
method: 针对单细胞转录组数据集，构建基因增量学习流水线并提出相应评估方法，研究基因级遗忘问题。
result: 实验发现基因增量学习中遗忘问题同样存在，流水线能有效缓解并展示了评估标准。
conclusion: 为单细胞转录组模型适应新基因提供了一种增量学习范式。
---

## Abstract
Classes, as fundamental elements of Computer Vision, have been extensively studied within incremental learning frameworks. In contrast, tokens, which play essential roles in many research fields, exhibit similar characteristics of growth, yet investigations into their incremental learning remain significantly scarce. This research gap primarily stems from the holistic nature of tokens in language, which imposes significant challenges on the design of incremental learning frameworks for them. To overcome this obstacle, in this work, we turn to a type of token, gene, for a large-scale biological dataset—single-cell transcriptomics—to formulate a pipeline for gene incremental learning and establish corresponding evaluations. We found that the forgetting problem also exists in gene incremental learning, thus we adapted existing class incremental learning methods to mitigate the forgetting of genes. Through extensive experiments, we demonstrated the soundness of our framework design and evaluations, as well as the effectiveness of the method adaptations. Finally, we provide a complete benchmark for gene incremental learning in single-cell transcriptomics.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
单细胞转录组中的基因增量学习。

### 2. 核心内容
该文注意到计算机视觉中的类别增量学习研究众多，而基因作为token同样具有增长性却很少被研究。作者以大规模单细胞转录组数据为例，提出基因增量学习流水线并建立相应评估，发现基因级遗忘问题同样存在。这项工作为单细胞模型适应不断增长的基因集合提供了新思路。

### 3. 对应检索需求
single-cell data perturbation response prediction。

### 4. 来源与原文
- Source：AAAI-2026-Accepted
- OpenReview：[https://ojs.aaai.org/index.php/AAAI/article/view/37062](https://ojs.aaai.org/index.php/AAAI/article/view/37062)
