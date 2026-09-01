---
title: "SPATIA: Multimodal Generation and Prediction of Spatial Cell Phenotypes"
title_zh: SPATIA：空间细胞表型的多模态生成与预测
authors: "Zhenglun Kong, Mufan Qiu, John Boesen, xiang lin, Sukwon Yun, Tianlong Chen, Manolis Kellis, Marinka Zitnik"
date: 2026-04-30
pdf: "https://openreview.net/pdf/6df30389ec5230663a3ec26c469b76e419fb5a42.pdf"
tags: ["query:gene-perturb"]
score: 4.0
evidence: 多模态生成与预测空间细胞表型，与虚拟细胞/组织建模间接相关
tldr: 空间转录组带来细胞图像、基因表达与空间上下文等多模态数据，但现有方法往往孤立分析或分辨率有限。作者提出SPATIA，学习从细胞到组织的统一空间感知表示，并通过置信度感知OT重加权与形态-表达对齐实现空间条件生成。实验表明SPATIA能多级别预测细胞表型并生成空间上下文一致的细胞状态，为虚拟组织/细胞建模提供了多模态基础。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 图像空间转录组多模态数据未被联合利用，难以在细胞到组织尺度统一建模表型。
method: 提出多级生成与预测模型，融合形态、表达和空间上下文，并结合置信度感知OT重加权与形态-表达对齐进行空间条件生成。
result: 实验显示SPATIA在空间细胞表型预测和生成上优于现有方法，实现跨尺度多模态建模。
conclusion: 为空间转录组的虚拟细胞表型建模提供了统一框架。
---

## Abstract
Understanding how cellular morphology, gene expression, and spatial context jointly shape tissue function is a central challenge in biology. Image-based spatial transcriptomics technologies now provide high-resolution measurements of cell images and gene expression profiles, but existing methods typically analyze these modalities in isolation or at limited resolution. 
We address the problem by introducing SPATIA, a multi-level generative and predictive model that learns unified, spatially aware representations by fusing morphology, gene expression, and spatial context from the cell to the tissue level. SPATIA also incorporates a spatially conditioned generative framework with confidence-aware OT reweighting and morphology-profile alignment for modeling target-state morphology distributions. Specifically, we propose a confidence-aware flow matching objective that reweights weak optimal-transport pairs based on uncertainty. We further apply morphology-profile alignment to encourage biologically meaningful image generation, enabling the modeling of microenvironment-dependent phenotypic transitions. We assembled a multi-scale dataset consisting of 25.9 million cell-gene pairs across 17 tissues. We benchmark SPATIA against 18 models across 12 tasks, spanning categories such as phenotype generation, annotation, clustering, gene imputation, and cross-modal prediction. SPATIA achieves improved performance over state-of-the-art models, improving generative fidelity by 8\% and predictive accuracy by up to 3\%.

---

## 论文详细总结（自动生成）

# SPATIA：空间细胞表型的多模态生成与预测（ICML 2026 论文总结）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：细胞形态（morphology）、基因表达（gene expression）与空间上下文（spatial context）如何共同决定组织功能，是生物学中的核心挑战。
- **背景局限**：基于图像的空间转录组技术（image-based spatial transcriptomics）虽然能提供高分辨率的细胞图像和基因表达谱，但现有方法通常**孤立分析各模态**或**分辨率有限**，未能充分利用多模态信息进行细胞到组织尺度的统一建模。
- **研究意义**：该问题直接关系到虚拟细胞/组织建模，若能实现多模态统一表征，则有望推动空间转录组学中细胞表型的预测与生成，为理解微环境依赖的表型转变提供计算基础。

## 2. 论文提出的方法论

- **总体框架**：SPATIA 是一个多级别（multi-level）的生成与预测模型，通过融合形态、基因表达和空间上下文，学习从细胞到组织层级的统一空间感知表征。
- **核心技术一：空间条件生成框架**——引入空间条件约束的生成模型，用于建模目标状态的形态分布。
- **核心技术二：置信度感知 OT 重加权（Confidence-aware OT reweighting）**——提出一种新的流匹配（flow matching）目标函数，根据不确定性对最优传输（Optimal Transport, OT）对中的弱匹配样本进行重新加权。这一设计的动机是：弱匹配的传输对更容易引入噪声，根据置信度调整权重可提升生成稳定性与质量。
- **核心技术三：形态-表达对齐（Morphology-profile alignment）**——通过约束生成的细胞图像与对应的基因表达谱在语义上保持一致，鼓励生成生物学上有意义的图像，从而实现对微环境依赖的表型转变进行建模。
- **算法流程概述**：模型以细胞图像、基因表达和空间坐标作为输入，经编码器提取统一空间感知表征；在生成端，使用流匹配模型学习从噪声到目标形态分布的映射，并通过置信度感知 OT 对传输路径进行修正；最后通过形态-表达对齐损失约束生成结果与表达谱的语义一致性。

## 3. 实验设计

- **数据规模**：构建了一个多尺度数据集，包含**17 种组织、约 2590 万细胞-基因对（25.9 million cell-gene pairs）**。
- **Benchmark 覆盖**：在 **12 个任务**上对模型进行系统评测，任务类型涵盖：
  - 表型生成（phenotype generation）
  - 细胞注释（annotation）
  - 聚类（clustering）
  - 基因插补（gene imputation）
  - 跨模态预测（cross-modal prediction）
- **对比方法**：与 **18 个现有模型**进行对比，覆盖了空间转录组学和相关领域的主流基线方法。

## 4. 资源与算力

- 论文原文**未明确说明**所使用的 GPU 型号、数量、训练时长等具体算力配置。
- 仅能推断该工作需要处理千万级细胞-基因对的多组织数据，对算力有一定需求，但具体硬件与训练成本无从考证，这是信息透明性方面的一个缺口。

## 5. 实验数量与充分性

- **实验数量**：数据覆盖 17 种组织，任务覆盖 12 项，对比方法达 18 种，实验规模较为可观。
- **充分性评估**：从任务多样性（生成、预测、注释、聚类、插补、跨模态）来看，实验设计较为全面，能够从多个维度验证模型的有效性。但论文文本中未展示详细的消融实验（如去掉置信度 OT 重加权或形态-表达对齐后的性能变化），因此对技术组件各自贡献的验证不透明。
- **客观性与公平性**：与 18 种基线模型对比，比较范围较广；但由于未提供详细的实验配置和统计显著性检验信息，公平性难以完全确认。

## 6. 论文的主要结论与发现

- SPATIA 在空间细胞表型的**生成保真度**上相较 SOTA 模型提升 **8%**。
- 在**预测准确性**上相较 SOTA 模型提升高达 **3%**。
- 实验证明 SPATIA 能实现跨尺度（细胞到组织）的多模态建模，在表型生成、注释、聚类、基因插补和跨模态预测等多个任务上优于现有方法。
- 该工作为空间转录组数据的虚拟细胞表型建模提供了一个**统一框架**，展示了多模态融合与空间条件生成在生物组织建模中的潜力。

## 7. 优点

- **多模态深度融合**：将形态、表达与空间上下文三者联合建模，打破了以往"各模态孤立分析"的局限。
- **创新性算法设计**：置信度感知 OT 重加权是对流匹配框架的一个新改进，针对弱匹配样本进行自适应降权，思路新颖且具有通用性。
- **生物学可解释性导向**：通过形态-表达对齐强化生成图像的生物学意义，而非仅追求视觉保真度。
- **多尺度统一建模**：从单细胞到组织的跨级别统一表征，具备良好的泛化潜力。
- **大规模数据支撑**：2590 万细胞-基因对、17 组织的数据集为模型评估提供了坚实基础。

## 8. 不足与局限

- **算力信息缺失**：未披露任何关于 GPU、训练成本、推理效率的信息，不利于复现与资源评估。
- **消融实验不透明**：文本中未明确展示各组件（置信度重加权、形态-表达对齐等）的独立消融结果，技术贡献的因果归因不完全清晰。
- **组织覆盖有限**：虽然包含 17 种组织，但与人体全部组织类型相比仍属有限子集，跨组织泛化能力有待进一步验证。
- **多模态类型局限**：仅涉及图像、表达和空间位置三类模态，未纳入蛋白组学、表观基因组学等其他信息模态。
- **数据集规模不确定性**："2590 万细胞-基因对"的具体计数方式和覆盖范围（是否含重复样本等）不明确。
- **领域限制**：作为一项计算生物学工作，其结论的生物学验证（如湿实验验证生成的细胞形态是否真实存在于组织）在文中未提及。

（完）
