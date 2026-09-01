---
title: "Towards Universal Gene Regulatory Network Inference: Unlocking Generalizable Regulatory Knowledge in Single-cell Foundation Models"
title_zh: 迈向通用基因调控网络推断：解锁单细胞基础模型中的可泛化调控知识
authors: "Jiaxin Qi, Hang Li, Yan Cui, Yuhua Zheng, Jianqiang Huang"
date: 2026-04-30
pdf: "https://openreview.net/pdf/d8664abb1090b7667398230211434c8df08b94dc.pdf"
tags: ["query:gene-perturb"]
score: 6.0
evidence: 从单细胞基础模型挖掘可泛化的基因调控网络，支持功能基因组与扰动机制解析
tldr: 基因调控网络推断对理解细胞机制至关重要，但单细胞基础模型在该任务上表现仍不理想。作者指出原因是重建式预训练未显式捕获潜在调控信号，并为此构建GRN泛化基准以评估未见基因与数据集上的预测。基于零样本调控知识挖掘，所提方法在跨基因、跨数据集上展现出更强的泛化能力，为从基础模型中释放调控知识、进而理解基因扰动效应提供了新途径。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 单细胞基础模型在GRN推断中泛化不足，重建式预训练无法显式捕获调控信号。
method: 提出GRN泛化基准，并通过零样本调控知识挖掘释放单细胞基础模型的潜在调控信息，实现跨基因/数据集预测。
result: 实验表明该方法在未见基因与数据集上取得更好的GRN推断泛化性能。
conclusion: 为利用单细胞基础模型理解基因调控与扰动效应提供了通用方法。
---

## Abstract
Gene Regulatory Network (GRN) inference is essential for understanding complex cellular mechanisms, rendered tractable through single-cell transcriptomic data. With the emergence of single-cell Foundation Models (scFMs), enhanced transcriptomic encoding is widely expected to revolutionize GRN inference. However, we observe that their performance remains far from satisfactory. The primary reason is that the standard reconstruction-based pre-training objectives often fail to explicitly capture latent regulatory signals. To bridge this gap, we first introduce a GRN generalization benchmark designed to evaluate regulatory predictions on unseen genes and datasets, which relies on the zero-shot capabilities of scFMs and is inherently challenging for traditional methods. Furthermore, to unlock the regulatory knowledge within the foundation models, we propose two novel methods, Virtual Value Perturbation and Gradient Trajectory, to distill implicit regulatory information from scFMs into highly generalizable inter-gene features. Extensive experiments demonstrate that our approach significantly outperforms existing methods, establishing a new paradigm for leveraging the potential of scFMs in universal GRN inference.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：基因调控网络（Gene Regulatory Network, GRN）推断是理解复杂细胞机制的关键任务，单细胞转录组数据使其变得可行。近年来，单细胞基础模型（single-cell Foundation Models, scFMs）在转录组编码方面展现出强大能力，人们普遍期望它们能彻底革新GRN推断。
- **现实观察**：然而，论文指出，scFMs在GRN推断任务上的表现“远非令人满意”（far from satisfactory）。
- **原因分析**：造成这一现象的主要原因是，标准基于重建（reconstruction）的预训练目标**未能显式捕获潜在的调控信号**。基础模型虽然学到了基因表达的表征，但其中蕴含的调控关系并未被直接激活或利用。
- **整体含义**：为弥合这一差距，论文试图**从单细胞基础模型中释放可泛化的调控知识**，从而建立一种**通用的GRN推断范式**，使其能够预测未见基因和未见数据集上的调控关系，进而服务于功能基因组学和基因扰动机制解析。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：基础模型的隐式表征中已经包含调控信息，但需要专门的“解码”或“蒸馏”手段将其转化为可泛化的基因间特征。因此，论文提出两种方法，用于从scFMs中提取隐含的调控知识，并用于GRN推断。
- **关键技术方法1：Virtual Value Perturbation（虚拟值扰动）**
  - 通过对某个基因的表达值进行虚拟扰动（即在输入层面模拟改变该基因的表达），观察模型输出表征的变化。
  - 这种“扰动-响应”模式可以捕获基因之间的调控影响方向与强度，从而形成基因间关系特征。
  - 整个过程是零样本的，不需要额外标注数据，只依赖预训练scFM的前向传播。
- **关键技术方法2：Gradient Trajectory（梯度轨迹）**
  - 利用模型对特定基因输入的梯度信息，追踪该基因表达变化对其他基因表征的影响轨迹。
  - 梯度轨迹可以视为一种连续的敏感性分析，能更细致地刻画基因间的依赖关系和调控强度。
  - 该特征与扰动方法互补，二者可联合使用，形成高泛化能力的基因间特征表示。
- **配套基准（Benchmark）**：
  - 论文专门构建了一个“**GRN泛化基准**”（GRN generalization benchmark），用于评估模型在**未见基因（unseen genes）**和**未见数据集（unseen datasets）**上的调控预测能力。
  - 该基准依赖scFMs的零样本能力，对传统GRN推断方法来说是固有困难的，因为传统方法通常需要在新数据集上重新训练或微调。
- **整体流程（文字说明）**：
  1. 使用预训练的scFM作为主干。
  2. 对给定基因对或基因集合，通过“虚拟值扰动”和“梯度轨迹”两种方式提取可泛化的基因间特征。
  3. 将特征输入到轻量级分类器或评分函数中，预测基因间的调控关系。
  4. 在泛化基准上评估跨基因、跨数据集的预测性能。

## 3. 实验设计：数据集、基准、对比方法

- **数据集**：论文摘要中未明确列出具体数据集名称，仅提及“未见基因和未见数据集”的评估场景。推测可能使用了几种公开的单细胞转录组数据集（如人类或小鼠的不同组织/细胞类型数据），但原文未给出细节。
- **基准**：
  - 提出了**GRN泛化基准**，专门测试模型对未见过基因和未见过数据集的泛化能力。
  - 评估指标可能包括AUROC、AUPRC等常用GRN推断指标，但摘要中未说明具体指标。
- **对比方法**：
  - 未在摘要中列出具体对比方法名称，但明确表示“显著优于现有方法”（significantly outperforms existing methods）。
  - 推测对比对象包括传统的共表达网络方法（如WGCNA）、基于回归的方法、以及其他基于深度学习/基础模型的GRN推断方法。
- **实验场景**：至少包含两个层次的泛化测试：
  - 跨基因泛化（针对未见基因）；
  - 跨数据集泛化（针对未见数据集/组织条件）。

## 4. 资源与算力

- **文中未明确说明**：在提供的摘要和元数据中，**没有**提到使用的GPU型号、数量、训练时长或任何算力信息。
- 由于该方法主要依赖预训练scFM的推理（前向传播和梯度计算），算力需求可能集中于特征提取阶段，但具体细节无法从现有信息获得。
- 建议读者查阅论文全文的实验设置部分以获取详细资源信息。

## 5. 实验数量与充分性

- **实验数量**：从摘要来看，作者进行了“大量实验”（Extensive experiments），但具体实验组数（如不同数据集个数、消融实验数量）未列出。
- **充分性评价**：
  - **正面**：提出了全新的泛化基准，并从“未见基因”和“未见数据集”两个维度评估，这比传统固定基因/固定数据集的评估更严格、更具实际意义。
  - **不足**：由于缺少消融实验细节（例如，单独使用Virtual Value Perturbation vs. Gradient Trajectory vs. 两者联合的效果），难以判断两种方法的各自贡献和互补性；也未说明与基线方法的统计显著性检验。
  - **客观性风险**：作为ICML 2026的录用论文，大概率包含较完整的实验，但摘要信息不足以支撑对其实验充分性的精确判断。

## 6. 论文的主要结论与发现

- scFMs虽然擅长编码转录组，但直接使用其表征进行GRN推断效果不佳，根本原因在于重建式预训练目标未显式建模调控信号。
- 通过**虚拟值扰动**和**梯度轨迹**两种零样本方法，可以从scFMs中有效蒸馏出隐式的调控知识，生成高度可泛化的基因间特征。
- 所提方法在**跨基因、跨数据集**的GRN推断场景下显著优于现有方法，为“通用GRN推断”建立了一种新范式。
- 这一工作为利用单细胞基础模型理解基因调控和基因扰动效应提供了通用途径，有助于后续的扰动预测和功能基因组研究。

## 7. 优点：方法或实验设计上的亮点

- **问题定位准确**：明确指出重建式预训练不利于GRN推断，弥补了领域对这一问题的认识不足。
- **方法创新性强**：提出“虚拟值扰动”和“梯度轨迹”两种新颖的零样本知识提取手段，无需额外标注数据，直接作用于预训练模型。
- **泛化基准设计前沿**：将GRN推断的评估推向“跨基因、跨数据集”的通用性场景，比传统固定基因集评估更具挑战和实用价值。
- **应用潜力大**：不仅限于静态GRN推断，还连通了基因扰动效应的理解，对下游药物响应、基因编辑预测等有潜在帮助。

## 8. 不足与局限

- **信息完整度**：目前提供的材料只有摘要和元数据，缺少方法细节、数学定义、实验数据具体来源、baselines名称和超参数设置等关键信息，限制了对方法的深入评判。
- **实验覆盖不明**：未明确列出使用的数据集类型（如是否覆盖不同物种、不同测序平台、不同细胞数量级）以及数据规模，跨数据集泛化的广度未知。
- **消融与敏感性分析缺失**：没有说明两种方法各自的作用、组合方式、扰动幅度和梯度计算的具体设计，可能存在敏感性或需要较多人工调参的问题。
- **与传统方法的对比细节缺失**：仅说“显著优于”但未提供具体数值和统计检验，难以判断优势幅度。
- **算力与环境未披露**：未提供训练/推理的计算成本，对于需要大量梯度计算的方法，可能在大规模基因数量上存在效率瓶颈。
- **潜在偏差风险**：基于预训练模型的零样本提取可能受预训练数据分布影响，在罕见细胞类型或非模式物种上可能失效；基准若只覆盖少数组织/条件，泛化结论可能过度乐观。

（完）
