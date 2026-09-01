---
title: "scDEBART: Predicting in silico Single-Cell Perturbation Responses via Large-Scale Differential Expression Learning"
title_zh: scDEBART：通过大规模差异表达学习预测计算机单细胞扰动响应
authors: "Jieun Sung, Wankyu Kim"
date: 2026-04-30
pdf: "https://openreview.net/pdf/1361dc3f2b1c26ec2f689868b7efde2cb28688dc.pdf"
tags: ["query:gene-perturb"]
score: 10.0
evidence: 直接通过大规模差异表达学习预测单细胞扰动响应
tldr: 单细胞基础模型在海量细胞上学习基因表达模式，但在预测遗传扰动效应时往往不及简单回归模型。作者提出scDEBART，一种扰动专用的预训练框架，以基线表达为条件预测log2倍数变化，从而在大规模表达变化环境中学习基因集共变异规律。该方法直接面向单细胞扰动响应预测任务，目标是在遗传扰动效应预测上超越静态共表达重建类基础模型，为虚拟细胞建模与扰动推断提供更有效的预训练范式。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 单细胞基础模型预测遗传扰动效应常不如简单回归，原因是目标基于丢失率高的绝对表达且预训练目标只重建静态共表达。
method: 提出scDEBART扰动专用预训练框架，以基线表达为条件预测log2倍数变化，学习基因集在表达变化环境下的共调控模式。
result: 在大规模表达变化环境下训练，使模型捕捉基因共调控关系，从而提升遗传扰动响应预测的准确性。
conclusion: scDEBART为单细胞扰动预测提供了更匹配的预训练目标，有望成为扰动响应预测和虚拟细胞建模的基础模型。
---

## Abstract
Single-cell foundation models trained on millions of cells can learn gene expression patterns across diverse contexts. However, for predicting genetic perturbation effects they often underperform simple regression models. We hypothesize two potential limitations: targets defined on dropout-prone absolute expression, and pretraining objectives that reconstruct static co-expression rather than encoding how genes co-regulate under expression changes. We introduce $\textbf{scDEBART}$, a perturbation-specific pretraining framework that predicts log fold-changes (logFC) conditioned on basal expression, thereby learning how gene sets co-vary across expression-change contexts at scale. To obtain reliable estimates of expression change under technical sparsity, we compute logFC from scVI-denoised expression and restrict pretraining to genes with robust detection. Pretrained on 6.28 million expression-change profiles from 66.6 million human cells and fine-tuned on five Perturb-seq datasets, scDEBART achieves mean enrichment factor (EF) of 11.96, 4-7$\times$ higher than scGPT and GEARS (mean EF 1.74-2.99), and 71.4\% top-1 accuracy for reverse perturbation identification compared to near-zero accuracy for prior models. In cross-modal transfer to drug perturbations (SCIPLEX), the model shows dose-dependent improvement in directional alignment (cosine similarity 0.04→0.30) with above-random DEG enrichment (EF 2.91-4.32), suggesting partial transfer of learned regulatory patterns across modalities. Overall, these results indicate that large-scale pretraining on scVI-denoised expression-change profiles provides a useful inductive bias for perturbation prediction.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- 预测遗传扰动（如基因敲低/敲除）对单细胞转录组的影响，是虚拟细胞建模和药物发现中的关键任务。
- 现有单细胞基础模型（如 scGPT）在大规模细胞上预训练后，在扰动预测任务上却常不如简单的回归基线（如线性模型）。
- 作者提出两个可能原因：
  - 预训练目标使用**丢失率高的绝对表达值**，噪声大、信号不稳定；
  - 预训练目标仅重建**静态共表达结构**，没有显式编码基因在表达变化条件下的**共调控（co-regulation）**关系。
- 核心含义：预训练目标应与下游扰动预测任务对齐，即直接学习“从基线状态到扰动状态的表达变化规律”，而非仅学习静态表达模式。

## 2. 论文提出的方法论

- 核心思想：构建一个**扰动专用（perturbation-specific）**的预训练框架，以基线表达为条件，预测**log2 倍数变化（logFC）**，从而在大规模表达变化环境中学习基因集的共变异规律。
- 关键技术细节：
  - 使用 **scVI 去噪后的表达**计算 logFC，以缓解单细胞数据技术性稀疏（dropout）带来的噪声；
  - 预训练仅限制在**检测稳健的基因**上，避免低质量基因引入偏差；
  - 模型架构基于 Transformer（如 scBERT 风格），以基线表达作为条件输入，输出预测的 logFC。
- 算法流程（文字说明）：
  1. 用 scVI 对单细胞表达进行去噪，获得可靠的表达估计；
  2. 对每个细胞/扰动组合计算基线到扰动的 logFC；
  3. 在 6,280 万个表达变化谱（来自 6,660 万个人类细胞）上预训练模型，使模型学习“给定基线状态，预测表达变化”的映射；
  4. 在 Perturb-seq 数据上微调，用于下游扰动响应预测；
  5. 额外测试跨模态迁移到药物扰动（SCIPLEX）场景。

## 3. 实验设计

- 使用的数据集与场景：
  - **预训练数据**：6,660 万个人类细胞，构建 6,280 万个表达变化谱；
  - **微调与评估数据**：5 个 Perturb-seq 数据集；
  - **跨模态迁移场景**：药物扰动数据集 SCIPLEX。
- Benchmark 任务：
  - 遗传扰动响应预测（预测扰动后的基因表达变化）；
  - 反向扰动识别（给定扰动后的表达谱，识别是哪种扰动）；
  - 跨模态药物扰动方向对齐与 DEG 富集。
- 对比方法：
  - **scGPT**（单细胞基础模型代表）；
  - **GEARS**（专门用于扰动预测的图神经网络方法）；
  - 简单回归基线（文中提到优于这些基线）。

## 4. 资源与算力

- 论文中**未明确说明**使用的 GPU 型号、数量、训练时长等算力细节；
- 仅提及预训练数据规模（6,660 万人类细胞、6,280 万表达变化谱），未涉及具体硬件配置或训练成本；
- 如需要复现相关信息，需查阅论文附录或联系作者获取。

## 5. 实验数量与充分性

- 实验组数概览：
  - 主实验：5 个 Perturb-seq 数据集上的扰动响应预测；
  - 反向扰动识别任务（用于验证模型是否真正学习了扰动的“指纹”信息）；
  - 跨模态迁移实验（SCIPLEX 药物扰动），包含剂量依赖性分析；
  - 与 scGPT、GEARS 的对比实验。
- 充分性与公平性分析：
  - **优点**：多数据集、多任务评估，尤其是反向扰动识别和跨模态迁移，增加了实验的广度和说服力；
  - **不足之处**：
    - 文中**未提及明确的消融实验**（如去掉 scVI 去噪、不使用稳健基因筛选、仅用绝对表达而非 logFC 等），因此难以量化每个设计选择的单独贡献；
    - 对比方法数量有限（scGPT、GEARS），未与更多最新模型或简单基线做更细粒度对比；
    - 跨模态迁移虽然展示了改进（余弦相似度 0.04→0.30），但绝对值仍较低，说明迁移能力是“部分”的。

## 6. 论文的主要结论与发现

- 提出 scDEBART 后，在 Perturb-seq 微调下达到：
  - 平均富集因子（EF）= **11.96**；
  - 比 scGPT 和 GEARS（EF 1.74-2.99）高出 **4-7 倍**；
  - 反向扰动识别 top-1 准确率达 **71.4%**，而先前模型几乎为 0%。
- 跨模态迁移到药物扰动（SCIPLEX）中：
  - 方向一致性（余弦相似度）从 0.04 提升到 0.30，呈剂量依赖性改善；
  - DEG 富集因子在 2.91-4.32，高于随机水平。
- 核心结论：在大规模 **scVI 去噪后的表达变化谱**上预训练，为扰动预测提供了有效的归纳偏置（inductive bias），比静态共表达重建更匹配扰动响应的下游任务。

## 7. 优点

- **任务对齐的预训练目标**：直接预测 logFC，而非重建绝对表达，与下游扰动预测高度一致；
- **数据预处理可靠**：利用 scVI 去噪解决 dropout 问题，并限制在稳健基因上，提升标签质量；
- **大规模预训练**：6,660 万细胞、6,280 万表达变化谱，提供了丰富多样的表达变化上下文；
- **模型简单但效果显著**：虽然架构基于已有 Transformer，但预训练目标的设计带来了大幅提升（EF 提升 4-7 倍）；
- **多维度验证**：不仅做扰动预测，还设计了反向扰动识别、跨模态药物扰动迁移，验证模型学到的表征具有可迁移性。

## 8. 不足与局限

- **算力信息缺失**：未说明训练所需的 GPU 数量、型号、时长，复现成本和可行性未知；
- **消融实验不足**：未系统评估 scVI 去噪、稳健基因筛选、logFC 目标等各个设计因素的独立贡献；
- **对比方法有限**：仅与 scGPT 和 GEARS 对比，未涵盖更多新近基础模型或更简单的回归/机器学习基线；
- **跨模态迁移仍有限**：药物扰动的方向对齐余弦相似度仅 0.30，虽优于随机但仍有较大提升空间；
- **适用范围未明确**：主要验证于人类细胞和 Perturb-seq/SCIPLEX，在其他物种、其他扰动类型（如 CRISPR 激活、化学扰动）上的泛化能力未知；
- **预训练数据的“变化谱”含义需进一步说明**：文末总结中数据规模（628 万 vs 6660 万细胞）存在表述混淆，部分细节需要从附录或后续版本中澄清。

（完）
