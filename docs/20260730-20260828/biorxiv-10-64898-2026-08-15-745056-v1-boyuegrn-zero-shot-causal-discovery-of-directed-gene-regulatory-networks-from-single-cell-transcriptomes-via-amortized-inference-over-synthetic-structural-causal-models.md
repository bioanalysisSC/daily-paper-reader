---
title: "BoYueGRN: Zero-shot causal discovery of directed gene regulatory networks from single-cell transcriptomes via amortized inference over synthetic structural causal models"
title_zh: BoYueGRN：通过合成结构因果模型的摊销推断从单细胞转录组进行有向基因调控网络的零样本因果发现
authors: "Wu, J., Shen, Y.-Q."
date: 2026-08-20
pdf: "https://www.biorxiv.org/content/10.64898/2026.08.15.745056v1.full.pdf"
tags: ["query:gene-perturb"]
score: 6.0
evidence: 从单细胞转录组零样本发现因果基因调控网络，为扰动效应建模提供因果结构支撑
tldr: 现有GRN推断需针对每个数据集重新优化，且难以判定因果方向。BoYueGRN仅在合成结构因果模型上训练，通过摊销推断对任意新数据单次前向传递即可输出边概率和调控方向，并用TF中心滑动窗口扩展到全转录组。在BEELINE基准及两个CRISPRi Perturb-seq筛查中，方向准确率达0.86-0.95，并可重建疾病特异的GRN动态。该工作开创了一次训练、跨数据集复用的新范式。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有GRN推断工具需对每个新数据集重新拟合，且多数无法推断因果方向。
method: 在10000个合成结构因果模型上训练，摊销推断单次前向传递输出边概率和方向，并用TF中心滑动窗口扩展到全转录组。
result: 在BEELINE基准上零样本性能强，两个Perturb-seq方向准确率0.86和0.95，并能重建跨五病27万细胞的特异GRN动态。
conclusion: BoYueGRN开创了一次训练、跨数据集复用的范式，为图谱规模疾病调控动态映射铺路。
---

## 摘要
从单细胞RNA-seq推断基因调控网络（GRN）传统上依赖于每个数据集的优化。现有工具必须针对每个新数据集重新拟合，且大多数无法推断因果调控方向。在此，我们提出BoYueGRN，一种仅在10,000个合成结构因果模型上训练的摊销因果发现框架。对于任何未见过的数据集，单次前向传播即可返回边概率和调控方向，而转录因子中心的滑动窗口与非对称融合将该固定大小模型扩展到全转录组覆盖。BoYueGRN在BEELINE基准测试中表现出强大的零样本性能。在两个独立的全基因组CRISPRi Perturb-seq筛选中，保留边上的方向准确度分别达到0.86和0.95。重建的跨五种疾病（涵盖超过270,000个细胞）的细胞类型和阶段特异性GRN动态产生了可通过实验检验的生物学假设。BoYueGRN将定向GRN推断重新定义为一次训练、跨数据集复用的范式。通过将网络重建与每数据集优化解耦，该范式为跨人类疾病的系统性、图谱规模调控动态映射开辟了道路。

## Abstract
Gene regulatory network (GRN) inference from single-cell RNA-seq conventionally relies on per-dataset optimization. Existing tools must be refit for every new dataset, and the majority fail to infer causal regulatory directions. Here we present BoYueGRN, an amortized causal discovery framework trained exclusively on 10,000 synthetic structural causal models. For any unseen dataset, a single forward pass returns edge probabilities and regulatory directions, while TF-centric sliding windows with asymmetric fusion extend this fixed-size model to full-transcriptome coverage. BoYueGRN demonstrates strong zero-shot performance across BEELINE benchmarks. On two independent genome-wide CRISPRi Perturb-seq screens, directional accuracy on retained edges reaches 0.86 and 0.95. Reconstructed cell-type- and stage-specific GRN dynamics across five diseases spanning more than 270,000 cells yield experimentally testable biological hypotheses. BoYueGRN reframes directed GRN inference as a train-once, reuse-across-datasets paradigm. By decoupling network reconstruction from per-dataset optimization, this paradigm opens the door to systematic, atlas-scale mapping of regulatory dynamics across human diseases.