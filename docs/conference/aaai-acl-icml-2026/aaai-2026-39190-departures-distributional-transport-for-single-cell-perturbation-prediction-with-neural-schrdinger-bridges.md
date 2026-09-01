---
title: "Departures: Distributional Transport for Single-Cell Perturbation Prediction with Neural Schrödinger Bridges"
title_zh: 基于神经薛定谔桥的单细胞扰动预测分布传输方法
authors: "Changxi Chi, Yufei Huang, Jun Xia, Jiangbin Zheng, Yunfan Liu, Zelin Zang, Stan Z. Li"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/39190/43151"
tags: ["query:gene-perturb"]
score: 9.0
evidence: 直接使用分布传输方法预测单细胞扰动响应
tldr: 单细胞扰动预测因同一细胞无法同时观测扰动前后状态而面临数据不成对问题。现有方法往往缺乏显式条件或依赖先验空间间接对齐，难以精确建模扰动。本文提出基于神经薛定谔桥的分布传输方法，直接连接扰动前后分布，实现精准的单细胞扰动结果预测。该方法为基因功能分析和药物候选筛选提供了有力工具，是单细胞扰动响应预测的重要进展。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 单细胞数据不成对且现有神经生成传输模型缺少显式条件或依赖先验空间，限制了对扰动的精确建模。
method: 提出基于神经薛定谔桥的分布传输方法，近似求解扰动前后分布的传输映射，实现对不成对单细胞扰动数据的建模。
result: 实验表明该方法能够有效预测单细胞扰动后的表达状态，相比现有方法提升了扰动建模的精度。
conclusion: 该工作为单细胞扰动预测提供了新的分布传输范式，有助于基因功能解析与药物研发。
---

## Abstract
Predicting single-cell perturbation outcomes directly advances gene function analysis and facilitates drug candidate selection, making it a key driver of both basic and translational biomedical research. However, a major bottleneck in this task is the unpaired nature of single-cell data, as the same cell cannot be observed both before and after perturbation due to the destructive nature of sequencing. Although some neural generative transport models attempt to tackle unpaired single-cell perturbation data, they either lack explicit conditioning or depend on prior spaces for indirect distribution alignment, limiting precise perturbation modeling. In this work, we approximate Schrödinger Bridge (SB), which defines stochastic dynamic mappings recovering the entropy-regularized optimal transport (OT), to directly align the distributions of control and perturbed single-cell populations across different perturbation conditions. Unlike prior SB approximations that rely on bidirectional modeling to infer optimal source-target sample coupling, we leverage Minibatch-OT based pairing to avoid such bidirectional inference and the associated ill-posedness of defining the reverse process. This pairing directly guides bridge learning, yielding a scalable approximation to the SB. We approximate two SB models, one modeling discrete gene activation states and the other continuous expression distributions. Joint training enables accurate perturbation modeling and captures single-cell heterogeneity. Experiments on public genetic and drug perturbation datasets show that our model effectively captures heterogeneous single-cell responses and achieves state-of-the-art performance.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
直接使用分布传输方法预测单细胞扰动响应。

### 2. 核心内容
单细胞扰动预测因同一细胞无法同时观测扰动前后状态而面临数据不成对问题。现有方法往往缺乏显式条件或依赖先验空间间接对齐，难以精确建模扰动。本文提出基于神经薛定谔桥的分布传输方法，直接连接扰动前后分布，实现精准的单细胞扰动结果预测。该方法为基因功能分析和药物候选筛选提供了有力工具，是单细胞扰动响应预测的重要进展。

### 3. 对应检索需求
single-cell data perturbation response prediction。

### 4. 来源与原文
- Source：AAAI-2026-Accepted
- OpenReview：[https://ojs.aaai.org/index.php/AAAI/article/view/39190](https://ojs.aaai.org/index.php/AAAI/article/view/39190)
