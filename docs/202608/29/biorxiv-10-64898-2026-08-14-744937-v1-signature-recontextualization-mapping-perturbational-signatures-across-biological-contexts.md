---
title: "Signature Recontextualization: Mapping perturbational signatures across biological contexts"
title_zh: 特征重情境化：跨生物情境映射扰动特征
authors: "Chen, A. D., Girke, T., Monti, S."
date: 2026-08-19
pdf: "https://www.biorxiv.org/content/10.64898/2026.08.14.744937v1.full.pdf"
tags: ["query:gene-perturb"]
score: 8.0
evidence: 提出跨情境扰动签名预测的基准框架，直接评估扰动效应在不同生物学情境下的预测
tldr: 扰动转录组学中，跨生物学背景的扰动特征预测是转化应用的关键挑战。为此提出了“特征重语境化”基准框架，定义三种目标数据覆盖情景，系统评估投影法、网络传播、深度学习及基础模型。结果发现projectCor与netProp等简洁方法在多个任务上持平或超越复杂模型，且可预测性与通路保守性、响应强度及基线相似性相关。所有代码与数据以R包sigRecon开源。
source: biorxiv
selection_source: carryover_cache
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-08-14-744937-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1687, \"height\": 638, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-08-14-744937-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1705, \"height\": 1070, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-08-14-744937-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1601, \"height\": 2251, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-08-14-744937-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1669, \"height\": 1090, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-08-14-744937-v1/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1693, \"height\": 1372, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-08-14-744937-v1/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1686, \"height\": 1190, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-08-14-744937-v1/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1292, \"height\": 1233, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-08-14-744937-v1/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1615, \"height\": 302, \"label\": \"Table\"}]"
motivation: 跨背景扰动特征预测缺乏统一基准，现有评估任务和指标不一致，限制方法比较与模型选择。
method: 提出包含三种目标数据覆盖情景的基准框架，并评估projectCor、netProp、scGPT、STACK等基线方法在四个扰动数据集上的表现。
result: 简洁的投影与网络传播方法在多数任务上匹配或超越深度学习模型，性能差异与通路保守性、响应强度及源-目标基线相似性相关。
conclusion: 发布开源R包sigRecon，提供可复现的跨背景扰动特征预测基准，表明模型复杂度并非跨背景泛化的关键。
---

## 摘要
扰动转录组学是理解基因功能和药物效应的强大工具，然而预测扰动在不同生物情境中如何表现仍是一个核心挑战，限制了从模型系统向临床相关组织的转化。尽管对该问题的兴趣日益增长，但基准测试工作一直受到评估任务不一致、指标异质性以及扰动类型和生物系统评估范围有限的阻碍。在此，我们引入了一个跨情境扰动特征预测的基准测试框架（我们将此任务定义为特征重情境化），该框架基于预测任务的明确定义、目标数据可用性以及以特征恢复为中心的评估指标。该框架在三种目标情境数据模式下评估预测性能：（1）仅对照，即仅测量目标情境中的对照谱；（2）低覆盖率，即测量目标情境中有限子集的扰动；（3）高覆盖率，即测量目标情境中的大多数扰动。这种设计能够系统评估预测性能如何依赖于目标情境样本量，同时为比较方法提供标准化基础。我们评估了新开发的基于投影（projectCor）和基于网络（netProp）的方法，以及基于深度学习的基础模型（scGPT、STACK）和统计基线。该基准测试涵盖四个多样的扰动数据集：细胞系中的CRISPR敲除和药物扰动，以及来自DrugMatrix的大鼠组织体内化学扰动，将评估从孤立的细胞系模型扩展到组织水平反应。在各种任务中，投影和网络传播方法在扰动类型和生物情境方面表现出很强的灵活性，并在多种情况下达到或超过深度学习和基础模型的性能，这表明模型复杂性并不固有地改善跨情境泛化。我们进一步表明，扰动可预测性随通路保守性、转录反应强度以及源情境和目标情境之间的基线相似性而显著变化。所有数据集、方法和评估工具均以开源R包（sigRecon）的形式发布，为可重复的基准测试和未来方法开发提供了基础。

## Abstract
Perturbational transcriptomics is a powerful tool for understanding gene function and drug effects, yet predicting how perturbations manifest across different biological contexts remains a central challenge, limiting translation from model systems to clinically relevant tissues. Despite growing interest in this problem, benchmarking efforts have been hindered by inconsistent evaluation tasks, heterogeneous metrics, and limited assessment across perturbation types and biological systems. Here, we introduce a benchmarking framework for cross-context perturbation-signature prediction (a task we define as signature recontextualization), grounded in explicit definitions of the prediction task, target-data availability, and evaluation metrics centered on signature recovery. The framework evaluates prediction performance across three target-context data regimes: (1) control only, where only control profiles from the target context are measured; (2) low coverage, where a limited subset of perturbations in the target context are measured; and (3) high coverage, where most perturbations in the target context are measured. This design enables systematic assessment of how prediction performance depends on target-context sample size while providing a standardized basis for comparing methods. We evaluate newly developed projection-based (projectCor) and network-based (netProp) methods alongside deep learning-based foundation models (scGPT, STACK) and statistical baselines. The benchmark spans four diverse perturbational datasets: CRISPR knockdowns and drug perturbations in cell lines, plus in vivo chemical perturbations in rat tissues from DrugMatrix, extending evaluation beyond isolated cell-line models to tissue-level responses. Across tasks, projection and network propagation approaches show strong flexibility across perturbation types and biological contexts, and in several cases match or exceed the performance of deep learning and foundation models, suggesting that model complexity does not inherently improve cross-context generalization. We further show that perturbation predictability varies substantially with pathway conservation, transcriptional response strength, and baseline similarity between source and target contexts. All datasets, methods, and evaluation utilities are released as an open-source R package (sigRecon), providing a foundation for reproducible benchmarking and future method development.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 一、核心问题与整体含义（研究动机与背景）

- **研究背景**：扰动转录组学（perturbational transcriptomics）是理解基因功能和药物效应的有力工具，通过测量基因扰动或药物处理后的转录组变化，揭示生物学机制。
- **核心挑战**：预测同一扰动在不同生物情境（如不同细胞系、组织、物种或疾病状态）中的转录组特征表现，是该领域向临床应用转化的关键瓶颈。例如，细胞系模型中发现的药物效应能否预测其在真实组织中的反应，直接关系到药物研发和精准医疗。
- **现存问题**：尽管跨情境扰动预测的研究兴趣日益增长，但该领域的基准测试工作长期受阻于三大障碍：
  1. **评估任务不一致**：不同研究对“跨情境预测”的定义各异，缺乏统一的任务框架；
  2. **评价指标异质性**：各研究使用不同的评估指标，结果难以直接比较；
  3. **评估覆盖有限**：已有评估多局限于特定扰动类型（如仅药物或仅基因敲除）和特定生物系统（如单一细胞系），缺乏跨扰动类型、跨生物系统的系统评估。
- **论文定位**：为了解决上述问题，论文提出了“特征重情境化”（signature recontextualization）这一明确定义的基准框架，旨在为跨生物情境的扰动特征预测提供标准化、可复现的评估基础，推动该领域方法论的发展和公平比较。

## 二、论文提出的方法论

### 核心思想

论文的核心思想是将“跨情境扰动特征预测”重新定义为一个可操作、可量化、可比较的标准化任务——**特征重情境化**。该框架围绕三个关键维度进行构建：

1. **预测任务的明确定义**：给定在“源情境”（source context）中观察到的一组扰动特征，预测这些扰动在“目标情境”（target context）中的转录组响应特征。
2. **目标数据可用性的系统划分**：根据目标情境中已有的实验数据覆盖程度，将预测任务划分为三种模式，以模拟实际应用中的不同场景。
3. **以特征恢复为中心的评估指标**：使用标准化的相关性指标衡量预测特征与实测特征之间的一致性，聚焦于“特征恢复”（signature recovery）能力。

### 三种目标情境数据覆盖情境的划分

- **模式一：仅对照（Control Only）**：目标情境中仅测量了对照（未处理）样本的转录组谱，没有任何扰动数据可用。这是最具挑战性的预测场景，要求方法完全依赖源情境信息和目标情境的基线状态进行推断。
- **模式二：低覆盖率（Low Coverage）**：目标情境中测量了有限子集的扰动（如5%-20%的扰动），需要对未测量的扰动进行预测。该模式模拟了实际研究中常见的“部分数据”情景，评估方法在少量目标数据辅助下的预测能力。
- **模式三：高覆盖率（High Coverage）**：目标情境中测量了大多数扰动（如80%以上），只需预测少数遗漏的扰动。该模式评估方法在目标数据充足时的最终预测性能，也是检验方法“上限”的依据。

### 评估的关键技术细节

- **投影法（projectCor）**：利用源情境与目标情境中共同测量的配对数据（如对照样本），计算相关性或回归关系，将源情境的扰动特征“投影”到目标情境空间中。
- **网络传播法（netProp）**：利用先验分子相互作用网络（如蛋白质-蛋白质相互作用网络），将源情境的扰动信号通过网络传播（network propagation）扩散到目标情境的基因上，从而重构目标情境中的扰动特征。
- **评估指标**：以特征恢复为中心，使用皮尔逊相关等指标计算预测特征向量与实测特征向量的相关性，衡量预测准确性。

## 三、实验设计

### 数据集

论文构建的基准测试覆盖了四个多样化的扰动数据集，涵盖不同的扰动类型和生物系统：

| 数据集 | 扰动类型 | 生物系统 |
|--------|----------|----------|
| CRISPR 敲除数据集 | 基因扰动（CRISPR knockdown） | 细胞系 |
| 药物扰动数据集 | 化合物/药物处理 | 细胞系 |
| DrugMatrix 大鼠数据集 | 体内化学扰动 | 大鼠组织（多个组织） |

- 包含**体外（in vitro）细胞系模型**和**体内（in vivo）组织水平反应**两类系统，将评估从孤立的细胞系扩展到真实的组织反应，增强了基准的生态效度。
- DrugMatrix 数据提供了多组织、多化合物的系统评估，覆盖了更接近临床应用的场景。

### Benchmark 设计

- 基准框架整合了前述三种目标情境数据覆盖模式（对照仅、低覆盖率、高覆盖率），在不同目标数据可用性水平下系统评估各方法的预测性能。
- 所有评估基于标准化的“特征恢复”指标，确保方法之间的公平比较。

### 对比方法

论文对比了四类方法，从简洁的统计方法到复杂的深度学习模型：

1. **投影法**：projectCor（论文新提出的方法）；
2. **网络传播法**：netProp（论文新引入的方法）；
3. **深度学习基础模型**：scGPT、STACK（大规模预训练模型）；
4. **统计基线**：包括均值预测、零预测等简单统计方法作为参照。

## 四、资源与算力

- **论文未明确说明**使用的GPU型号、数量、训练时长等具体算力资源信息。
- 文中仅提及使用了深度学习基础模型（如scGPT、STACK），但未详述其微调或推理所需的硬件配置。
- **关于这一点需要指出**：由于论文目标是基准测试方法的比较，而非大规模模型训练，其算力需求可能以推理（inference）和轻量微调为主，但具体资源消耗信息在原文中未披露，无法定量评估。

## 五、实验数量与充分性

### 实验数量

- 论文进行了**系统性的跨数据集、跨扰动类型、跨生物系统**的基准评估：
  - 4个主要扰动数据集（CRISPR敲除、细胞系药物、DrugMatrix大鼠组织）；
  - 3种目标数据覆盖模式（对照仅、低覆盖率、高覆盖率）；
  - 对比4类方法（投影、网络传播、深度学习基础模型、统计基线）；
  - 包含多层次的分析维度（不同扰动类型、不同组织、不同覆盖程度）。
- 此外，论文还进行了**可预测性归因分析**，考察了通路保守性、转录反应强度和源-目标基线相似性等因素与预测性能之间的关系。

### 充分性评估

- **优点**：
  - 数据覆盖广，跨越细胞系到组织层面，涵盖基因扰动和药物扰动；
  - 任务划分清晰，三种数据覆盖模式构成了系统性的困难梯度；
  - 评估指标统一、标准化，提高了公平性和可比性。
- **潜在不足**：
  - 所评估的深度学习基础模型数量有限（仅scGPT和STACK两个），可能不足以代表当前快速发展的基础模型全貌；
  - 未提及对评估结果进行统计显著性检验或置信区间分析，无法判断某些性能差异是否具有统计学意义；
  - 未明确说明是否进行了多次随机重复（如不同的扰动脉冲划分）以消除采样偏差。

## 六、主要结论与发现

1. **简洁方法表现优异**：在各类任务中，投影法（projectCor）和网络传播法（netProp）在不同扰动类型和生物情境中表现出很强的灵活性和适应性，并在多种场景下匹配或超越深度学习基础模型（scGPT、STACK）的性能。
2. **模型复杂度并非关键因素**：该结果表明，模型复杂性并不固有地改善跨情境泛化能力——简洁、可解释的方法在跨情境预测任务中具有强大竞争力。
3. **可预测性的决定因素**：扰动可预测性显著受以下因素影响：
   - **通路保守性**：源与目标情境之间共享的通路越保守，预测越准确；
   - **转录反应强度**：扰动引起的转录组变化幅度越大（反应越强烈），越容易被预测；
   - **源-目标基线相似性**：源情境与目标情境之间的基线（未扰动状态）转录组谱越相似，跨情境预测效果越好。
4. **框架适用性**：三种数据覆盖模式的设定实现了对预测性能如何依赖于目标情境样本量的系统评估，为标准化的方法比较提供了坚实基础。

## 七、优点

1. **统一基准框架**：提出了首个明确定义、可复现的跨情境扰动特征预测基准框架，解决了此前评估任务不一致和指标异质性问题。
2. **数据覆盖全面**：跨越体外细胞系和体内组织两个层面，涵盖基因扰动和化学扰动两种类型，显著增强了评估结果的生态效度和推广性。
3. **任务设计合理**：三种目标数据覆盖模式的划分符合实际应用需求，从“仅对照”到“高覆盖率”构成了自然的难度梯度，能系统地评估方法在不同目标数据可用性下的表现。
4. **方法对比公平**：从简单的统计基线到复杂的深度学习基础模型，方法梯度覆盖合理，能够有效回答“模型复杂度与跨情境泛化能力之间的关系”这一关键科学问题。
5. **开源可复现**：所有数据集处理流程、方法实现和评估工具均以开源R包（`sigRecon`）的形式发布，极大方便了社区复现和后续方法开发。
6. **结论有洞察力**：发现简洁方法可与复杂模型匹敌、以及可预测性与通路保守性/基线相似性的关联，为理解跨情境泛化机制的深层因素提供了新视角。

## 八、不足与局限

1. **预印本阶段限制**：论文为bioRxiv预印本（2026年8月），尚未经过同行评审，结论需在正式发表后进一步确认。
2. **基础模型覆盖不全面**：仅评估了scGPT和STACK两个深度学习基础模型，而当前领域内还有大量其他基础模型（如Geneformer、scFoundation等）未被纳入比较，可能影响“深度学习不占优”这一结论的普适性。
3. **算力信息缺失**：未披露深度学习方法的具体训练/推理算力消耗，无法评估方法比较中的资源效率维度。
4. **统计严谨性存疑**：未报告重复实验的次数、置信区间或统计检验结果，难以判断方法间性能差异的显著性。
5. **覆盖的组织和物种有限**：尽管包含大鼠组织数据，但尚未涉及人类原代组织、疾病状态组织或更多样化的细胞类型，向临床转化的外推仍需谨慎。
6. **评估指标单一**：以特征恢复（相关性）为核心指标，未纳入下游任务实用性（如通路富集恢复、药物重定位效果）或预测的可解释性评估，可能忽略了不同方法在应用层面的差异化价值。
7. **方法可扩展性未知**：生成性/投影性方法在处理大型数据集或极端情境（如完全未见的目标组织类型）时的扩展性和鲁棒性尚未充分讨论。

（完）
