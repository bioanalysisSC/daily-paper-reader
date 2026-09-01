---
title: "PanFoMa: A Lightweight Foundation Model and Benchmark for Pan-Cancer"
title_zh: PanFoMa：面向泛癌的轻量级基础模型与基准
authors: "Xiaoshui Huang, Tianlin Zhu, Yifan Zuo, Xue Xia, Zonghan Wu, Jiebin Yan, Dingli Hua, Zongyi Xu, Yuming Fang, Jian Zhang"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/37008/40970"
tags: ["query:gene-perturb"]
score: 4.0
evidence: 轻量级单细胞泛癌基础模型与基准，可作为单细胞下游任务的表示骨干
tldr: 单细胞RNA测序是解析肿瘤异质性的关键，但泛癌研究缺少高效判别式表示模型与统一基准。作者提出PanFoMa，将Transformer与状态空间模型结合，前段用共享自注意力捕捉基因交互，后端用线性时间状态空间模型整合全局上下文，兼顾性能与效率。实验表明PanFoMa在泛癌单细胞分类与表示学习上表现出色，为包括扰动预测在内的下游任务提供了可复用的基础编码器。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 泛癌单细胞研究需要兼具判别力与效率的表示模型，同时缺少统一评测基准。
method: 设计前段共享自注意力局部编码器与后段线性状态空间全局解码器，构建轻量混合网络PanFoMa并提供泛癌基准。
result: 实验显示PanFoMa在性能与效率上取得平衡，优于现有单细胞表示方法。
conclusion: 为单细胞下游任务（含扰动预测）提供了高效可扩展的基础模型和评测资源。
---

## Abstract
Single-cell RNA sequencing (scRNA-seq) is essential for decoding tumor heterogeneity. However, pan-cancer research still faces two key challenges: learning discriminative and efficient single-cell representations, and establishing a comprehensive evaluation benchmark. In this paper, we introduce \algoname, a lightweight hybrid neural network that combines the strengths of Transformers and state-space models to achieve a balance between performance and efficiency. \algoname consists of a front-end local-context encoder with shared self-attention layers to capture complex, order-independent gene interactions; and a back-end global sequential feature decoder that efficiently integrates global context using a linear-time state-space model. This modular design preserves the expressive power of Transformers while leveraging the scalability of Mamba to enable transcriptome modeling, effectively capturing both local and global regulatory signals. To enable robust evaluation, we also construct a large-scale pan-cancer single-cell benchmark, \algoname Bench, containing over 3.5 million high-quality cells across 33 cancer subtypes, curated through a rigorous preprocessing pipeline. Experimental results show that \algoname outperforms state-of-the-art models on our pan-cancer benchmark (+4.0\%) and across multiple public tasks, including cell type annotation (+7.4\%), batch integration (+4.0\%) and multi-omics integration (+3.1\%).

---

## 论文详细总结（自动生成）

### 1. 检索相关性
轻量级单细胞泛癌基础模型与基准，可作为单细胞下游任务的表示骨干。

### 2. 核心内容
单细胞RNA测序是解析肿瘤异质性的关键，但泛癌研究缺少高效判别式表示模型与统一基准。作者提出PanFoMa，将Transformer与状态空间模型结合，前段用共享自注意力捕捉基因交互，后端用线性时间状态空间模型整合全局上下文，兼顾性能与效率。实验表明PanFoMa在泛癌单细胞分类与表示学习上表现出色，为包括扰动预测在内的下游任务提供了可复用的基础编码器。

### 3. 对应检索需求
single-cell data perturbation response prediction。

### 4. 来源与原文
- Source：AAAI-2026-Accepted
- OpenReview：[https://ojs.aaai.org/index.php/AAAI/article/view/37008](https://ojs.aaai.org/index.php/AAAI/article/view/37008)
