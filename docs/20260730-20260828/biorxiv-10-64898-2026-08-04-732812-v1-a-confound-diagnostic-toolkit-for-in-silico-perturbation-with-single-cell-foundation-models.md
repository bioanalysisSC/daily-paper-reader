---
title: A confound-diagnostic toolkit for in silico perturbation with single-cell foundation models
title_zh: 用于单细胞基础模型计算扰动的混杂诊断工具包
authors: "Qiu, R., Zhao, M. M."
date: 2026-08-07
pdf: "https://www.biorxiv.org/content/10.64898/2026.08.04.732812v1.full.pdf"
tags: ["query:gene-perturb"]
score: 9.0
evidence: 诊断通过删除单细胞基础模型基因token进行原位扰动时的混杂因素
tldr: 针对单细胞基础模型删除基因token的原位扰动，嵌入差值可能仅反映基因身份等混杂而非生物敲除效应，提出一套混杂诊断工具包，集成保留增量测试、响应调整、覆盖门控、文库大小诊断与去循环状态位移分析，并数值复现冻结Geneformer引擎。在Frangieh与Replogle数据集上，原生嵌入差值无超越基因身份的可复现增益，信号注入校准显示其低于检测下限。该框架帮助判断基础模型扰动读数何时值得生物学解释。
source: biorxiv
selection_source: fresh_fetch
motivation: 基础模型原位扰动在零样本场景下的嵌入响应可能只是基因身份、文库大小等混杂的反映，需先验证其是否含有超越这些混杂的真实生物信号。
method: 结合保持增量测试、响应调整、覆盖门控、文库大小诊断与去循环状态位移分析，并数值复现冻结Geneformer的扰动引擎，形成可复用的混杂诊断工具包。
result: 在Frangieh与Replogle数据集上，原生嵌入增量未提供超越基因身份的可复现提升；信号注入校准确认其低于检测下限，阳性结果可归因于文库大小结构与普遍响应性。
conclusion: 该框架可评估基础模型扰动读数是否值得生物学解读，避免将混杂效应误认为真实敲除响应。
---

## 摘要
从细胞输入序列中删除一个基因token提供了一种便捷的原生策略来进行计算扰动，但由此产生的嵌入差值可能并不代表生物学的敲除响应。表面效应反而可能反映基因身份、普遍响应性、有限的标记化覆盖范围、文库大小污染或循环状态评分。在这里，我们提出了一个混杂诊断框架，结合了留出增量测试、响应性调整、覆盖门控、文库大小诊断和去循环状态偏移分析，并配以数值匹配的冻结Geneformers扰动引擎的重实现。在Frangieh和Replogle数据集以及线性和非线性读数上，原生嵌入差值除了基因身份之外没有提供可重复的留出改进。信号注入校准表明，该测试能够检测注入的残余信号，而原生增量仍低于其检测下限。匹配对照将表面阳性归因于原始计数文库大小结构、广泛的响应性和自参考评分，而覆盖范围限制了扰动的适用性和估计稳定性，但并未建立生物特异性。这种模型可适应的框架有助于确定何时基础模型的扰动读数值得进行生物学解释。

动机：基础模型的计算扰动可以在没有匹配实验数据时预测扰动效应。然而，在零样本设置下，嵌入衍生的响应可能反映基因身份、普遍响应性、标记化限制、文库大小伪影或循环状态评分，而不是生物敲除效应。因此，我们开发了一个可复用的混杂诊断框架，应用匹配对照来测试原生扰动读数是否包含超越这些混杂因素的信息，并值得进行生物学解释。

## Abstract
Deleting a gene token from a cells input sequence offers a convenient native strategy for in silico perturbation, but the resulting embedding delta may not represent a biological knockout response. Apparent effects can instead reflect gene identity, universal responsiveness, limited tokenization coverage, library-size contamination, or circular state scoring. Here, we present a confound-diagnostic framework combining held-out increment testing, responsiveness adjustment, coverage gating, library-size diagnostics, and de-circularized state-shift analysis, together with a numerically matched reimplementation of frozen Geneformers perturbation engine. Across Frangieh and Replogle datasets and linear and nonlinear readouts, the native embedding delta provided no reproducible held-out improvement beyond gene identity. Signal-injection calibration showed that the test detected injected residual signal, whereas native increments remained below its detection floor. Matched controls traced apparent positives to raw-count library-size structure, broad responsiveness, and self-referential scoring, while coverage constrained perturbation applicability and estimate stability without establishing biological specificity. This model-adaptable framework helps determine when foundation-model perturbation readouts warrant biological interpretation.

MotivationFoundation-model in silico perturbation could predict perturbation effects when matched experimental data are unavailable. However, in zero-shot settings, embedding-derived responses may reflect gene identity, universal responsiveness, tokenization limits, library-size artifacts, or circular state scoring rather than biological knockout effects. We therefore developed a reusable confound-diagnostic framework that applies matched controls to test whether native perturbation readouts contain information beyond these confounds and warrant biological interpretation.

---

## 论文详细总结（自动生成）

## 1. 核心问题与整体含义

- 单细胞基础模型（如 Geneformer、scGPT、scFoundation）可通过删除细胞输入序列中的目标基因 token 实现零样本原位扰动，所得嵌入差值（embedding delta）被当作预测敲除响应的读数。
- 论文的核心问题：这种原生嵌入差值是否真正反映生物敲除效应，还是仅仅反映了基因身份、普遍响应性、tokenization 覆盖不足、文库大小伪影或循环评分等混杂因素。
- 整体含义：在缺乏匹配实验数据的情况下，若不加诊断直接使用基础模型扰动读数，可能将混杂信号误认为真实生物学响应。该研究旨在提供一个可复用的混杂诊断框架，帮助判断何时值得对这类扰动读数进行生物学解释。

## 2. 方法论

- 核心思想：通过一组“匹配对照”测试，检验原生嵌入差值在控制已知混杂后是否仍携带额外信息。
- 关键技术细节：
  - 数值匹配的 Geneformer 扰动引擎重实现（path-D）：逐细胞基因余弦相似度响应，与官方 InSilicoPerturber 输出达到 Pearson r > 0.999999、最大绝对误差 3×10⁻⁷，确保后续可控重采样。
  - 保留增量测试（held-out increment testing）：以未扰动基因嵌入为基因身份基线，比较加入 768 维敲除嵌入差值后的留出性能提升（Δr）；使用 5 折交叉验证，评估模型包括岭回归、MLP、梯度提升树。
  - 信号注入校准：构造与基线残差具有已知相关 c 的合成特征，确定检测下限（c* ≈ 0.20）；并用真实分半 CCND1 效应作为阳性对照，确认测试确实能恢复真实扰动信号。
  - 普遍响应性调整：计算基因跨多个扰动的平均绝对响应，作为普遍响应性基线，检验显著性模式是否仍具有扰动特异性。
  - 文库大小诊断：比较 raw-count log2FC 与 size-factor 归一化（DESeq2/PyDESeq2，apeglm 收缩）的伪 bulk 差异表达目标，识别测序深度伪影。
  - 去循环状态位移分析：构建跨基因投影矩阵，将基因 A 的敲除投影到基因 B 的实验扰动轴上，避免“删除的基因同时定义评分轴”的循环问题。
  - 覆盖率门控：定义目标 token 出现在 top-4096 输入序列中的细胞比例，作为适用性与估计稳定性约束。

## 3. 实验设计

- 数据集：
  - Frangieh Perturb-CITE-seq（黑色素瘤患者细胞，CRISPR-Cas9 敲除）。
  - Replogle K562 CRISPRi（essential-scale 与 genome-scale Perturb-seq）。
  - 均使用 scPerturb 协调后的 h5ad 文件。
- Benchmark / 参考目标：
  - 伪 bulk 聚合后经 DESeq2（PyDESeq2）估计的 log2 fold change，以非靶向对照为参考组；raw-count log2FC 仅作为文库大小诊断，不作为主目标。
- 主要扰动案例：
  - Frangieh：CCND1 敲除（主案例）。
  - Replogle：HSPA9、SUPT6H、CSE1L、DHX15、GATA1（覆盖不同生物过程，其中 GATA1 因重复少仅作支持性证据）。
- 对比方法 / 基线：
  - 基因身份基线（未扰动基因嵌入） vs 基线+嵌入增量（多种线性与非线性读取器）。
  - 探索性读数还对比了方向性评分、768 维嵌入探针、显著性评分，以及 raw-count 目标与 DESeq2 目标。
- 控制实验：
  - 信号注入校准、真实信号阳性对照、随机噪声对照。
  - 普遍响应性 vs 特异性分析（232 个 Frangieh 扰动）。
  - 文库大小结构分析（CCND1–TIMP1 相关性的归一化前后变化）。
  - 去循环同通路 vs 交叉通路投影比较（GATA1）。
  - 覆盖率分布与受控子采样收敛分析（217 个 Frangieh 目标）。

## 4. 资源与算力

- 文中未明确提及 GPU 型号、数量、训练时长或具体算力开销。
- 仅说明使用了冻结的 Geneformer V2-104M 模型（12 层 Transformer，隐藏维度 768，token 词汇约 20,271），未进行微调；在缓存 path-D 响应后，下游重采样分析使用 NumPy 实现，避免了重复运行 transformer 模型。
- 可推断计算量主要集中在模型前向传播与 token 删除操作，但具体资源消耗未报告。

## 5. 实验数量与充分性

- 实验数量较多：涵盖 2 个独立数据集、至少 6 个扰动程序、3 种读取模型、信号注入校准、真实信号阳性对照、普遍响应性分析、文库大小诊断、去循环状态位移分析、覆盖率分析等。
- 充分性评价：
  - 正面：设计包含正对照（真实信号可被检出）和负对照（噪声无增量），说明“原生增量无增益”并非由于测试不灵敏；匹配对照系统性地排除了多种混杂解释。
  - 客观性：所有报告相关均为 5 折交叉验证的留出估计，in-sample 结果不作为证据；模型超参数与随机种子固定；伪 bulk 重复避免细胞层面伪重复。
  - 局限性：实证范围仅限冻结 Geneformer 原生 token 删除，未覆盖微调模型、解码器架构、推理时引导或替代扰动算子；GATA1 伪 bulk 重复仅 3 个，细胞状态分析使用 K562 扰动轴而非独立参考。这些限制了结论向外推广的强度，但不影响主要结论。

## 6. 主要结论与发现

- 原生嵌入差值在 Frangieh 与 Replogle 数据集上，对所有线性/非线性读取器均未提供超越基因身份基线的可复现留出增量，Δr 接近零（如 CCND1 Δr = −0.004）。
- 信号注入校准确认测试能够检测注入的残余信号（c* ≈ 0.20 时可检出），但原生增量仍低于检测下限；真实分半 CCND1 效应产生明确正增量（Δr = +0.092 ± 0.016），而原生增量与随机噪声均落在零信号带内。
- 表观阳性结果可被明确归因于混杂：
  - 基因身份与基线表达结构本身具有较高可预测性（raw-count 目标上基因身份基线 r=0.693）。
  - 显著性模式主要反映普遍响应性（普遍响应性与绝对 CCND1 效应 Spearman ρ=+0.868，而嵌入位移大小与生物效应大小呈负相关 ρ=−0.45）。
  - raw-count log2FC 目标受文库大小结构影响（CCND1–TIMP1 相关性从 −0.600 变为 +0.060）。
  - GATA1 状态位移在去循环后不呈预期的通路特异性（交叉通路投影大于同通路投影）。
- Tokenization 覆盖率是适用性和估计稳定性的约束（中位覆盖 47%，JAK2 仅 2.3%），但提高覆盖率并不建立生物特异性。

## 7. 优点

- 提出了一套系统化、可复用的混杂诊断流程，明确列出了每个诊断对应的混杂因素、报告指标和缺失后果，实践性强。
- 数值匹配的 path-D 重实现使受控子采样成为可能，能够隔离“贡献细胞数量”对估计的影响。
- 采用信号注入校准与真实信号阳性对照，验证了测试的灵敏度，使“无增量”结论更有说服力。
- 实验设计注重公平性：留出评估、特征标准化限制在训练折、超参数固定、伪 bulk 定义避免伪重复。
- 框架不局限于 Geneformer，可适配其他基于 token 的基础模型，只需调整对应适用性检查。

## 8. 不足与局限

- 实证范围有限：仅测试冻结 Geneformer 原生 token 删除，未覆盖微调模型、解码器架构、推理时引导、替代扰动算子或更复杂的细胞状态参考。
- GATA1 分析受限于伪 bulk 重复数少（3 个），只能作为支持性证据；去循环状态分析未使用独立的分化/功能状态轴，可能降低普适性。
- 覆盖率-估计分析基于探索性读取器，验证的是估计稳定性而非生物准确性。
- 未报告算力消耗细节，不利于评估实际部署成本。
- 结论不代表所有单细胞基础模型或扰动策略都无效，但提示原生 token 删除应被视为假设生成工具，而非已证实的生物学敲除模拟。

（完）
