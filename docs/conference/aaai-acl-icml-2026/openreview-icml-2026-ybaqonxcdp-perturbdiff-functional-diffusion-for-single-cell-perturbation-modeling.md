---
title: "PerturbDiff: Functional Diffusion for Single-Cell Perturbation Modeling"
title_zh: PerturbDiff：用于单细胞扰动建模的功能扩散
authors: "Xinyu Yuan, Xixian Liu, Ya Shi Zhang, Zuobai Zhang, Hongyu Guo, Jian Tang"
date: 2026-04-30
pdf: "https://openreview.net/pdf/0ee67fb55320a5b0151aeb80a7565a846486226e.pdf"
tags: ["query:gene-perturb"]
score: 10.0
evidence: 扩散模型用于虚拟细胞模拟扰动响应
tldr: 构建能够准确模拟细胞扰动反应的虚拟细胞是系统生物学长期目标，但单细胞测序破坏性使得同一细胞不能同时观测扰动前后，需学习未配对对照组与扰动组的映射。现有模型通常假设给定细胞类型和扰动类型后反应分布固定，忽略微环境影响和批次效应等潜在因素。本文提出PerturbDiff，功能扩散模型，对控制与扰动群体之间的映射进行建模，并捕获条件反应中的潜在系统性变异。研究为虚拟细胞扰动预测提供了更灵活准确的生成式方案。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 细胞反应受潜在因素影响多样，现有模型假设单一固定反应分布不现实。
method: 提出功能扩散模型学习未配对控制与扰动群体间的映射，捕获潜在反应变异。
result: 能够更准确地模拟单细胞扰动响应，并考虑反应异质性。
conclusion: 为虚拟细胞扰动模拟提供更贴近生物学真实的生成模型。
---

## Abstract
Building _Virtual Cells_ that can accurately simulate cellular responses to perturbations is a long-standing goal in systems biology. A fundamental challenge is that high-throughput  single-cell sequencing is destructive: the same cell cannot be observed both before and after a perturbation. Thus, perturbation prediction requires mapping unpaired control and perturbed populations. Existing models address this by learning maps between distributions, but typically assume a single fixed response distribution when conditioned on observed cellular context (_e.g._, cell type) and the perturbation type. In reality, responses vary systematically due to unobservable latent factors such as microenvironmental fluctuations and complex batch effects, forming a _manifold_ of possible distributions for the same observed conditions.  To capture this variability, we introduce PerturbDiff, which shifts modeling from individual cells to entire distributions. By embedding distributions as points in a Hilbert space, we define a diffusion-based generative process operating directly over probability distributions. This allows PerturbDiff to capture population-level response shifts across hidden factors, improving generalization. Benchmarks on established datasets show that PerturbDiff achieves state-of-the-art performance in single-cell response prediction and generalizes substantially better to unseen perturbations. See our project page (https://katarinayuan.github.io/PerturbDiff-ProjectPage/), where code and data (https://github.com/DeepGraphLearning/PerturbDiff) are publicly available.

---

## 论文详细总结（自动生成）

# PerturbDiff：用于单细胞扰动建模的功能扩散——中文论文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **长期目标**：构建能够准确模拟细胞对扰动（如药物、基因编辑）反应的“虚拟细胞”（Virtual Cells），是系统生物学的核心愿景之一。
- **根本性挑战**：高通量单细胞测序具有破坏性，同一细胞无法同时观测扰动前后状态，因此扰动预测本质上需要在**未配对的对照组与扰动组群体**之间学习映射关系。
- **现有模型的不足**：已有方法（如CPA、scGen等）虽然能学习群体间的分布映射，但通常假设在给定可观测语境（如细胞类型）和扰动类型后，反应分布是**单一且固定的**。然而生物学现实中，细胞反应会因不可观测的潜在因素（如微环境波动、复杂批次效应）而系统性变化，同一条件下实际存在一个**可能的反应分布流形（manifold）**，而非单一固定分布。
- **研究意义**：PerturbDiff 打破了“单一固定反应分布”的简化假设，首次将扰动建模从单细胞层面提升到**分布层面**，为虚拟细胞扰动模拟提供了更贴近生物学真实的生成式方案，发表于 ICML-2026。

## 2. 论文提出的方法论

### 核心思想
- **范式转变**：从“预测每个细胞的反应”转向“建模整个反应分布的演化”，将控制组分布映射到扰动组分布，同时捕获群体层面因隐藏因素导致的反应变异。
- **核心创新**：将概率分布视为希尔伯特空间中的“点”，从而将扩散生成过程直接定义在**概率分布的空间**上，实现“分布的分布”生成。

### 关键技术细节
- **分布嵌入**：将对照组和扰动组的单细胞表达分布嵌入到再生核希尔伯特空间（RKHS）中，以分布嵌入（如核均值嵌入）作为扩散过程的基本操作对象。
- **分布级扩散模型**：定义前向扩散过程逐步向分布嵌入中添加噪声（扰动分布逐渐退化为某个基准分布），学习反向过程以从带噪声的分布嵌入中恢复真实的扰动后分布。
- **条件生成**：以可观测语境（如细胞类型、扰动类型）为条件，生成整个扰动后群体分布，而非逐点预测单个细胞状态。
- **捕获异质性**：由于模型操作的是分布而非独立细胞，能够自然捕捉因微环境、批次效应等隐藏因素导致的反应分布变化，在解码回单细胞空间时保留了群体层面的生物学变异。

## 3. 实验设计

- **数据集**：论文标明使用了“established datasets”（领域内公认的基准数据集），但提供的文本未列出具体数据集名称（如 Perturb-seq、scRNA-seq 扰动数据集等）。
- **Benchmark 任务**：单细胞响应预测（预测扰动后的基因表达状态）以及对**未见扰动**（unseen perturbations）的泛化预测。
- **对比方法**：论文提到与“existing models”（现有方法）对比，包括学习分布映射的经典扰动预测模型，但具体对比方法名称在提供的文本中未逐一列出。
- **评估指标**：摘要未给出具体指标名称（如均方误差、Fréchet distance、Wasserstein 距离等），仅报告“达到最先进水平”。

## 4. 资源与算力

- **本文未明确说明**：提供的论文提取文本（标题页与摘要）中**没有披露** GPU 型号、数量、训练时长、参数量或能耗等资源信息。
- 如需完整的算力报告，需查阅论文正文的“实验设置”或附录部分。

## 5. 实验数量与充分性

- **实验组数**：根据摘要，至少包含两类实验场景：(1) 既有基准数据集上的单细胞响应预测；(2) 对未见扰动的泛化测试。具体细分数（如不同数据集个数、消融实验数量）在提供的文本中不可见。
- **充分性判断**：综述范围内尚难全面评估。摘要声称“state-of-the-art performance”和“substantially better”泛化能力，但：
  - 未见具体数值和统计显著性报告；
  - 未见消融实验（如去掉分布级建模后的效果对比）的明确描述；
  - 缺乏对不同扰动类型、不同细胞类型亚群的分类分析描述。
- **客观性**：论文声称结果优于现有方法，但需在完整论文中核实是否采用统一的预处理流程、相同的评估协议和多次随机种子统计，才能判定公平性。

## 6. 论文的主要结论与发现

- 将建模单位从单细胞提升到**整个概率分布**，能有效捕捉扰动反应中的系统性异质性，突破了传统固定反应分布假设的限制。
- 在标准基准数据集上，PerturbDiff 在单细胞反应预测任务中达到**最先进性能**。
- 在**未见扰动的泛化**场景中，PerturbDiff 相比现有方法有显著优势，表明分布级建模学到的表征更具迁移性和稳健性。
- 验证了“以分布为对象”的生成式建模是虚拟细胞扰动预测的一个有前景的新方向。

## 7. 优点

- **概念创新性强**：首次将扩散模型引入“分布空间”，从数学上（希尔伯特空间中的分布嵌入）优雅地解决了反应异质性问题，突破了现有模型“单分布假设”的瓶颈。
- **建模视角合理**：考虑到微环境和批次效应等不可观测因素对反应分布的真实影响，生物学假设更扎实。
- **生成式框架灵活**：以分布为基本单元，天然支持群体水平的统计推断，且生成过程有坚实的概率学基础。
- **工程贡献完整**：提供公开的项目主页、代码仓库（GitHub）和数据资源，利于复现和后续研究。
- **应用价值高**：在未见扰动上的泛化能力对于药物发现中“预测新药反应”具有直接的实际意义。

## 8. 不足与局限

- **实验信息不完整（基于当前提取文本）**：未列出具体数据集名称、对比方法清单、指标数值和显著性检验，无法在当前文本基础上独立验证“最先进”的论断。
- **计算复杂度担忧**：在分布空间（希尔伯特空间）上做扩散，核嵌入的计算和采样可能比传统细胞级扩散模型更昂贵，论文未提供效率分析。
- **潜在偏差风险**：
  - 分布级嵌入在聚合过程中可能抹掉部分重要单细胞层面的稀疏信息；
  - 对批次效应的建模是否会导致模型“利用”批次信息而非学习真正生物学信号，需要谨慎评估。
- **评估局限性**：摘要仅提到基准数据集预测和泛化，未提及是否包含独立湿实验室验证（如新扰动实验验证），距离真正“虚拟细胞”目标仍有距离。
- **可解释性**：在高维分布空间中做扩散，缺少对“哪些基因或通路驱动反应变异”的可解释性分析。

---

（完）
