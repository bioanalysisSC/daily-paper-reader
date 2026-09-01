---
title: Learning Adaptive Perturbation-Conditioned Contexts for Robust Transcriptional Response Prediction
title_zh: 学习自适应扰动条件上下文用于稳健的转录响应预测
authors: "Yinhua Piao, Hyomin Kim, Seonghwan Kim, Yunhak Oh, Junhyeok Jeon, Sang-Yeon Hwang, Jaechang Lim, Woo Youn Kim, Chanyoung Park, Sungsoo Ahn"
date: 2026-04-30
pdf: "https://openreview.net/pdf/becaf1b2205773e8bf2494a1cd75952f53d83eb6.pdf"
tags: ["query:gene-perturb"]
score: 9.0
evidence: 直接针对单细胞数据中基因扰动的鲁棒转录响应预测
tldr: 预测基因扰动的高维转录响应时，信号稀疏且噪声大，现有方法常出现均值坍缩，即仅预测全局平均表达。本文提出AdaPert，通过可微节点选择抽取稀疏的扰动特异子图，并抑制非响应基因的虚假变异，同时突出关键差异。该方法能生成可解释的扰动特异转录响应预测，显著减少假阳性，为基因扰动效应建模提供了新的鲁棒方法。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 现有扰动响应预测常出现均值坍缩，将全局平均表达误作扰动特异响应，且生物知识图谱的静态先验会传播噪声。
method: 提出AdaPert，通过可微节点选择抽取扰动特异稀疏子图，并结合自适应上下文抑制非响应基因中的虚假变异。
result: 相比现有方法，AdaPert生成了更准确且可解释的扰动特异转录响应，降低了假阳性。
conclusion: 该工作为基因扰动转录响应预测提供了鲁棒且可解释的新方法，可用于功能基因组学扰动效应研究。
---

## Abstract
Predicting high-dimensional transcriptional responses to genetic perturbations is challenging because signals are sparse and experimental noise is severe. Existing methods often suffer from mean collapse, achieving high correlation by predicting the global average expression rather than perturbation-specific responses, which yields false positives and poor interpretability. Methods that add biological knowledge graphs typically treat them as dense, static priors shared across perturbations, propagating noise. We propose AdaPert, which counters mean collapse by extracting a sparse, perturbation-specific subgraph via differentiable node selection, then suppressing spurious variation in non-responsive genes while emphasizing differentially expressed ones. Across multiple benchmarks, AdaPert outperforms existing baselines, with the largest gains on DEG-aware metrics.

---

## 论文详细总结（自动生成）

### 1. 核心问题与整体含义

- **核心问题**：预测基因扰动后产生的高维转录组响应是功能基因组学的重要任务，但信号稀疏、实验噪声强烈，使得该任务极具挑战。
- **现有缺陷**：
  - 已有模型常出现**均值坍缩（mean collapse）**现象，即模型并没有学习到扰动特异的转录变化，而是倾向于输出全局平均表达谱。这类模型虽然在常用相关性指标上表现良好，但实质上掩盖了真实的差异表达信号，导致**高假阳性**和**低可解释性**。
  - 融合生物知识图谱的方法通常将图谱视为**跨扰动共享的稠密静态先验**，这种设计不仅无法区分扰动特异的子网络，反而会**传播噪声**，进一步模糊真正的响应信号。
- **整体含义**：该工作挑战了“平均表达即预测”的伪成功，呼吁更严格、更真实的扰动响应评估，并提出了一个能同时提升鲁棒性与可解释性的新框架。

### 2. 方法论

- **方法名称**：AdaPert（Adaptive Perturbation-Conditioned Contexts）。
- **核心思想**：放弃静态稠密背景，改而**动态抽取稀疏的扰动特异子图**，并以扰动条件作为上下文，以区分响应基因与非响应基因。
- **关键技术细节**：
  1. **可微节点选择（Differentiable Node Selection）**：以端到端可微方式从大规模基因网络中筛选出与该扰动高度相关的节点，构建稀疏子图，避免无关基因带来的噪声干扰。
  2. **扰动条件上下文（Perturbation-Conditioned Contexts）**：针对每个具体扰动生成自适应上下文表示，使模型能够根据当前扰动调整预测行为。
  3. **非响应基因抑制与差异基因强调**：在解码预测结果时，主动抑制非响应基因上的虚假变异，同时放大差异表达基因的信号，从机制上缓解均值坍缩。
- **算法流程（文字说明）**：
  1. 输入扰动信息与基因表达背景；
  2. 通过可微节点选择模块抽取扰动特异稀疏子图；
  3. 结合扰动条件上下文编码子图特征；
  4. 生成转录响应预测，并在损失函数或解码阶段强化差异表达基因、抑制非响应基因的波动；
  5. 以端到端方式联合训练，同时优化预测精度与DEG感知质量。

### 3. 实验设计

- **数据集 / 场景**：作者声明在**多个基准数据集**上进行了验证，尤其强调使用**DEG-aware指标**（即考虑差异表达基因的度量），但摘要中未列出具体数据集名称。
- **基准与指标**：
  - 使用传统相关性指标（如皮尔逊相关）用于和已有方法对比；
  - 重点引入/突出**DEG-aware指标**，用于衡量模型在差异表达基因上的预测质量，避免均值坍缩造成的虚高相关。
- **对比方法**：摘要未列出具体基线名称，但提及“existing baselines”，推测包括典型的转录响应预测模型以及基于生物知识图增强的方法。

### 4. 资源与算力

- 原文摘要与元数据中**未明确提及**使用的GPU型号、GPU数量、训练时长等算力信息。
- 这是当前文本信息的一项缺失，若需复现或评估其训练成本，需参考论文正文或补充材料。

### 5. 实验数量与充分性

- **实验数量**：摘要仅概括性地描述为“多个基准”，未给出具体实验组数或消融实验数量，无法从当前文本获得精确统计。
- **充分性与公平性**：
  - 从评分（9.0，ICML-2026录用）及摘要表述来看，实验具备一定的系统性和对比性；
  - **优势**：重点使用DEG-aware指标评估，能更真实反映扰动特异响应质量；
  - **不足**：摘要未提供基线方法的细节、消融研究的具体设计、统计显著性检验等信息，限制了对其实验充分性和公平性的独立判断。

### 6. 主要结论与发现

- AdaPert在多个基准上**优于现有基线方法**。
- 在**DEG-aware指标**上的提升最为显著，说明其能更好地捕捉真正的差异表达信号。
- AdaPert能够生成**更准确且可解释**的扰动特异转录响应预测，有效缓解均值坍缩问题。
- 该方法显著**降低假阳性率**，对功能基因组学的扰动效应研究具有实用价值。

### 7. 优点

- **问题针对性明确**：直击现有方法的均值坍缩顽疾，从根本上反思评价指标与模型目标是否一致。
- **稀疏建模**：通过可微节点选择抽取扰动特异子图，避免静态知识图谱传播噪声。
- **扰动自适应**：引入扰动条件上下文，使模型能针对不同扰动动态调整行为。
- **可解释性增强**：输出与特定扰动相关的子图和基因，便于生物学家理解作用机制。
- **更严格的评估**：强调DEG-aware指标，推动领域向真实信号方向改进，而非迎合全局相关。

### 8. 不足与局限

- **数据集细节缺失**：本次提供的摘要中未列出具体基准名称及数据规模，难以评估其泛化覆盖范围。
- **算力信息空白**：未报告训练资源，不利于判断方法的可复现性与实际部署成本。
- **消融分析未展示**：没有明确说明节点选择、上下文模块等各组件的单独贡献与敏感性分析。
- **生物验证有限**：摘要未提到湿实验验证或已知扰动数据库的交叉验证，其生物学真实意义仍有待进一步确认。
- **DEG标注依赖**：DEG-aware指标的使用依赖于可靠的差异表达基因注释，若标注存在偏差可能影响评估公正性。

（完）
