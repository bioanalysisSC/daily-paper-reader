---
title: "Reading the Cell, Designing the Cure: Perturbation-Conditioned Molecular Diffusion for Function-Oriented Drug Design"
title_zh: 解读细胞，设计疗法：面向功能药物设计的扰动条件分子扩散
authors: "ZIYU XU, zijian zhang, Liang Wang, Zhiyuan Liu, Qiang Liu, Shu Wu, Liang Wang"
date: 2026-04-30
pdf: "https://openreview.net/pdf/efd29788b8e64965072f802e394699c7cf247bdd.pdf"
tags: ["query:gene-perturb"]
score: 7.0
evidence: 用于药物设计的扰动条件扩散，基于转录组状态转变
tldr: 该文针对靶点结构缺失或通路失调场景下的药物设计难题，将转录组扰动作为功能读数，提出多分辨率转录组引导的扩散框架CURE，在给定期望的转录组状态转变条件下生成药物分子。CURE缓解了任务的不适定性和生物学-化学跨界困难，实验证明其能生成符合目标状态的候选分子，为基于基因表达扰动的功能导向药物设计提供了新思路。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 传统药物设计依赖靶点结构，但许多疾病由失调通路引起，转录组扰动可提供系统级功能读数，值得用于药物设计。
method: 提出CURE框架，一种多分辨率转录组引导的扩散模型，以期望的转录组状态转变作为条件生成药物分子。
result: 实验表明CURE能生成符合目标转录组状态的候选分子，验证了功能导向设计的可行性。
conclusion: 该工作为基于转录组扰动的功能导向药物设计提供了新范式。
---

## Abstract
When reliable target structures are unavailable at scale or phenotypes arise from dysregulated pathways, transcriptomic perturbations provide a system-level functional readout for drug action. In this work, we formalize Transcriptome-based Drug Design (TBDD) as a generative inverse problem: designing drug molecules conditioned on desired transcriptomic state transitions. We analyze the inherently ill-posed nature of this task, which is further complicated by the profound domain gap between biology and chemistry and by the sparsity of transcriptomic signals. To address these challenges, we propose CURE (A CellUlar Response Engine), a multi-resolution transcriptome-guided diffusion framework. CURE features a specialized Transcriptome Perturbation Functional Feature Extractor (TFE) that (1) distills function-oriented perturbation embeddings from pre/post states, (2) aligns these signatures to dual chemical views to bridge the cross-modal gap, and (3) performs heterogeneity-aware aggregation to extract robust state-specific signals from noisy transcriptomic data. Extensive evaluations on both standard benchmarks and rigorous out-of-distribution protocols demonstrate that CURE consistently outperforms strong baselines in structural quality and functional consistency. Furthermore, we validate its practical utility via a zero-shot gene-inhibitor design task, highlighting the potential of phenotype-driven generative discovery.

---

## 论文详细总结（自动生成）

## 论文详细中文总结

### 1. 核心问题与整体含义（研究动机与背景）

- **背景**：传统计算机辅助药物设计通常依赖于目标蛋白的高分辨率三维结构，通过结构信息指导分子生成。然而，许多疾病并非由单一靶点异常所致，而是源于复杂的信号通路失调（dysregulated pathways），在这些场景下可靠的靶点结构往往在大规模上不可获得。
- **核心问题**：论文提出并形式化了一个新任务——**基于转录组的药物设计（TBDD, Transcriptome-based Drug Design）**，即将其视为一个生成式逆问题：**在给定期望的转录组状态转变（transcriptomic state transition）条件下，设计能够触发该转变的候选药物分子**。
- **深层挑战**：该任务天然具有严重的不适定性（ill-posed），且被两个附加难点进一步复杂化：① 生物学与化学之间存在巨大的领域鸿沟（跨模态语义对齐困难）；② 转录组信号本身的高噪声与稀疏性（sparsity）。
- **整体含义**：这项工作旨在将转录组扰动作为药物作用的系统级功能读数（functional readout），探索一条**不依赖靶点结构、以功能表型为导向**的药物设计新范式，为通路失调类疾病提供生成发现的新路径。

### 2. 论文提出的方法论

- **核心框架**：提出 **CURE（A CellUlar Response Engine）**，一种**多分辨率转录组引导的扩散模型**（multi-resolution transcriptome-guided diffusion framework），用于在转录组状态转变条件约束下生成药物分子。
- **关键模块——TFE（Transcriptome Perturbation Functional Feature Extractor）**，包含三个核心功能：
  1. **功能导向扰动嵌入蒸馏**：从给药前后的转录组状态对（pre/post states）中提取携带功能语义的扰动嵌入（perturbation embeddings），实现对“状态转变”而非单点状态的编码。
  2. **双化学视角对齐**：将转录组特征与两种不同的化学结构表征视角（dual chemical views）进行跨模态对齐，以弥合生物学序列/表型空间与化学分子空间之间的领域鸿沟。
  3. **异构感知聚合**：针对转录组数据的高噪声特性，采用异构感知聚合（heterogeneity-aware aggregation）策略，从嘈杂的转录组信号中提取稳健的状态特异信号（state-specific signals）。
- **生成机制**：以蒸馏得到的扰动特征作为条件信号，注入扩散模型的生成过程（即扰动条件分子扩散），引导模型解码出能够诱导目标转录组转变的分子结构。
- **方法论本质**：将“生物学功能要求（转录组转变）”作为唯一生成条件，跳过靶点结构这一中间环节，是生成式逆向药物设计的直接实现。

### 3. 实验设计

- **评估基准**：使用了标准基准（standard benchmarks）和严格的**分布外（OOD, out-of-distribution）**协议进行评测，重点考察模型在结构质量（structural quality）和功能一致性（functional consistency）两个维度上的表现。
- **对比方法**：与多个强基线（strong baselines）进行了系统对比（论文中未列举具体基线名称，但声称CURE持续优于这些方法）。
- **实际效用验证**：设计了一个**零样本基因抑制剂设计任务**（zero-shot gene-inhibitor design），用于验证模型在未见过的基因靶标上直接生成抑制剂的实用能力，以说明表型驱动生成发现的可落地性。
- **数据集说明**：论文提取文本中未给出具体数据集名称（如LINCS L1000、GDSC等）及详细统计信息。

### 4. 资源与算力

- **明确说明**：在提供的论文提取文本中，**未报告**任何关于算力资源的信息，包括GPU型号、GPU数量、训练时长、模型参数量或显存占用等具体训练细节。

### 5. 实验数量与充分性

- **从现有信息来看**，实验设计包含三个层次：标准基准评测、OOD泛化评测、零样本实用任务验证，覆盖面较广，兼顾了生成质量、泛化能力和实际应用价值。
- **充分性评价**：实验布局合理，OOD协议和零样本设计增强了结论的可信度；但由于文中未能提供具体的数据集数量、消融实验细节（如TFE各组件贡献的分析、不同分辨率设置的影响等），**无法完全判断实验的全面性与公平性**。就现有信息而言，实验相对充分但细节透明度有限。

### 6. 主要结论与发现

- **核心结论**：CURE在结构质量与功能一致性两个关键指标上均持续优于强基线方法，证明了多分辨率转录组引导扩散框架的有效性。
- **实践价值**：通过零样本基因抑制剂设计任务，验证了CURE在实际药物发现中的可用潜力，说明利用转录组状态转变直接驱动分子生成是可行的。
- **范式意义**：该工作为**基于转录组扰动的功能导向药物设计**提供了新范式，有望摆脱对靶点结构信息的刚性依赖，拓展生成式药物设计的应用边界。

### 7. 优点

- **问题定义具有原创性与前瞻性**：将难以解决的靶点缺失/通路失调问题转化为转录组状态转变条件下的生成问题，拓展了AI药物设计的任务范畴。
- **跨模态对齐设计巧妙**：通过扰动嵌入与双化学视图的对齐，直接应对生物-化学领域鸿沟这一核心瓶颈，方法上具有针对性。
- **工程细节考虑周全**：针对转录组数据的稀疏性与噪声，引入异构感知聚合，体现了对数据特性深入理解后做出的方法设计。
- **多分辨率引导**：从不同粒度提取转录组信息，有助于同时捕捉全局状态变化与细粒度通路信号。
- **评估严谨**：除标准基准外还包含OOD协议与零样本任务，更有力地验证了泛化能力与实用价值。

### 8. 不足与局限

- **实验细节披露不足**：提取文本未提供具体数据集名称、基线方法名称、评估指标定义、消融实验设计等关键实验细节，难以全面评估实验的严谨性与可复现性。
- **算力与实现细节缺失**：未报告训练配置、超参数敏感性分析等，不利于工业界的成本预估与复现。
- **转录组数据依赖**：模型效果高度依赖转录组数据的质量与覆盖度，在数据稀疏或批次效应严重的情况下，TFE模块的稳健性有待进一步验证。
- **零样本验证深度有限**：零样本基因抑制剂设计任务仅停留在计算生成层面，**缺乏湿实验（in vitro/in vivo）验证**，真实生物活性与药物安全性尚未确认。
- **不适定性的理论处理**：论文分析了任务的不适定性，但在方法层面对此的约束机制（如正则化、一致性约束）描述不够深入，生成结果的唯一性与可解释性仍有提升空间。
- **适用范围边界**：主要面向转录组可观测的场景，对于缺乏转录组数据或表型变化不显著的疾病领域，以及非编码调控、翻译后修饰等非转录层面的药效机制，本框架的应用范围仍有明确边界。

（完）
