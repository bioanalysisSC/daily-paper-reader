---
title: "LLM4Cell: Taxonomy and Evaluation of LLM and Agentic Models for Single-Cell Biology"
title_zh: LLM4Cell：单细胞生物学中大语言模型与智能体模型的分类与评估
authors: "Sajib Acharjee Dip, Adrika Zafor, Bikash Kumar Paul, Uddip Acharjee Shuvo, Muhit Islam Emon, Xuan Wang, Liqing Zhang"
date: 2026-07-01
pdf: "https://aclanthology.org/2026.acl-long.1942.pdf"
tags: ["query:gene-perturb"]
score: 9.0
evidence: 统一梳理面向单细胞生物学的LLM与智能体模型，将扰动建模和药物反应预测纳入任务映射
tldr: 大语言模型正被广泛用于单细胞数据分析，但各类模型在模态、家族和评估上高度碎片化。LLM4Cell系统调研了58个面向单细胞研究的基础模型和智能体模型，将其划分为五个家族，并映射到细胞注释、轨迹推断、扰动建模和药物反应预测等八项关键任务。该综述统一了LLM单细胞模型的分类与评测口径，有助于理解大语言模型在基因扰动预测推理中的适用性和局限。为相关方向的研究提供了导航式的基准参考。
source: ACL-2026-Long
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-long/anthology-2026acl-long1942/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1637, \"height\": 874, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026acl-long1942/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1422, \"height\": 1269, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026acl-long1942/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1453, \"height\": 610, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026acl-long1942/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1629, \"height\": 2288, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026acl-long1942/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1557, \"height\": 791, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026acl-long1942/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1565, \"height\": 790, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long1942/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1477, \"height\": 321, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long1942/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1654, \"height\": 800, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long1942/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1685, \"height\": 399, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long1942/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1813, \"height\": 1600, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long1942/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1806, \"height\": 389, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long1942/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1812, \"height\": 1943, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long1942/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1810, \"height\": 2209, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long1942/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1812, \"height\": 2249, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long1942/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1809, \"height\": 775, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long1942/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1811, \"height\": 1417, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long1942/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1812, \"height\": 886, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long1942/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1833, \"height\": 1411, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long1942/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1811, \"height\": 2277, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long1942/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1812, \"height\": 2097, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long1942/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1813, \"height\": 2233, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long1942/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1810, \"height\": 2457, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long1942/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1811, \"height\": 2442, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long1942/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1813, \"height\": 2059, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long1942/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1812, \"height\": 2262, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long1942/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1809, \"height\": 2451, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long1942/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1811, \"height\": 2459, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026acl-long1942/table-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1814, \"height\": 2165, \"label\": \"Table\"}]"
motivation: 单细胞生物学中LLM与智能体模型进展迅速但碎片化，缺少统一分类和评估框架，尤其需要梳理扰动建模相关方法。
method: 系统性调研58个模型，按基础、文本桥、空间/多模态、表观基因组和智能体五类组织，并映射到八项分析任务。
result: 揭示了LLM在单细胞多种任务（含扰动建模和药物反应）上的现有能力与评估现状，给出分类与任务对照图。
conclusion: 为研究人员选择和使用用于基因扰动预测等任务的大语言模型提供了系统指南与评估基础。
---

## Abstract
Large language models (LLMs) and emerging agentic frameworks are beginning to influence single-cell biology by enabling natural-language interfaces, generative annotation, and multimodal data integration. However, progress remains fragmented across data modalities, model families, and evaluation practices. LLM4Cell presents a unified survey of 58 foundation and agentic models developed for single-cell research, spanning RNA, ATAC, multi-omic, and spatial modalities. We organize these methods into five families foundation, text-bridge, spatial/multimodal, epigenomic, and agentic and map them to eight key analytical tasks, including annotation, trajectory inference, perturbation modeling, and drug-response prediction. Drawing on over 40 public datasets, we analyze benchmark coverage, data diversity, and ethical or scalability constraints, and synthesize reported capabilities across ten domain-level dimensions related to biological grounding, multimodal alignment, fairness, privacy, and interpretability. By explicitly linking datasets, modeling paradigms, and evaluation domains, LLM4Cell provides an integrated perspective on language-driven single-cell analysis and highlights open challenges in standardization, interpretability, and trustworthy model development.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义

- **研究背景**：大语言模型（LLM）和新兴智能体（agentic）框架正在进入单细胞生物学领域，用于自然语言交互、生成式细胞注释、多模态数据整合等任务。
- **核心问题**：该领域进展高度碎片化——模型在数据模态（RNA、ATAC、多组学、空间组学）、模型家族、训练范式、评估标准上差异巨大，导致跨模型比较、复现和可信度判断都变得困难。
- **整体含义**：现有综述多以模型架构或提示策略为主线，忽略了“数据—模型—评估”之间的耦合关系。LLM4Cell 采用数据与评估为中心的视角，试图厘清当前单细胞 LLM 与智能体模型到底“真正理解了什么”，以及在生物 grounding、推理能力、公平性和可解释性等方面存在哪些结构性缺口。
- **论文定位**：面向 NLP 与生物学两个社区，提供统一的分类法、数据集目录和十维度评估框架，以支撑未来标准化基准与可信模型开发。

## 2. 论文提出的方法论

- **统一综述框架**：对 58 个代表性方法进行系统梳理，并建立“模态—grounding 类型—智能体能力—主要任务—领域质量”五个正交维度的分类体系。
- **五大家族分类**：
  - **Foundation Models（基础模型）**：如 scGPT、Geneformer、scFoundation，主要通过大规模 scRNA-seq 的掩码基因预测或排序重构学习可迁移细胞/基因表征。
  - **Text-Bridge & Ontology LLMs（文本桥接/本体模型）**：如 GenePT、CellLM、Cell2Sentence，显式地将分子嵌入与自然语言或本体概念对齐，提升可解释性和零样本注释能力。
  - **Spatial & Multimodal FMs（空间/多模态模型）**：如 TransformerST、OmiCLIP、Nicheformer，融合空间坐标、组织学图像或多种组学模态。
  - **Epigenomic & Regulatory FMs（表观基因组/调控模型）**：如 EpiFoundation、EpiBERT、GeneMamba、GET，建模染色质可及性和调控关系。
  - **Agentic Frameworks（智能体框架）**：如 scAgent、CellVerse、EpiAgent，将预训练编码器与 LLM 控制器、工具调用和多步推理结合。
- **八项核心任务映射**：注释与本体映射、轨迹与扰动建模、多组学整合、空间映射与反卷积、调控网络与通路推断、跨物种迁移、生成模拟、药物反应预测。
- **十维度评估准则**：生物 grounding、批次效应、多组学对齐、轨迹/扰动、跨物种泛化、公平性、可解释性、隐私、可扩展性、新兴/智能体范式；每项按“Present / Partial / Absent”三级标注，且仅依据原文明确报告的证据，不进行外推。

## 3. 实验设计

- **数据集**：汇总 40+ 公开数据集，覆盖 RNA 图谱（Tabula Sapiens、Tabula Muris、HCA、HLCA）、ATAC/染色质数据（Cusanovich 小鼠图谱、人类成体/胎儿 scATAC、ENCODE）、多组学配对数据（TEA-seq、DOGMA-seq、CITE-seq、Multiome Benchmark Pack）、空间数据（Visium、Slide-seqV2、MERFISH、Stereo-seq、HEST-1k、HESCAPE、STimage-1K4M）、扰动/药物反应数据（Replogle 2022 Perturb-seq、sci-Plex、Virtual Cell Challenge），以及植物单细胞数据集（scPlantDB、E-CURD-4）。
- **Benchmark 方式**：不进行统一预处理或重训练，而是以原始论文报告的评估结果为依据，记录每个模型在各任务和十个评估维度上的覆盖情况，形成 `S2_Method_Domains` 注册表。
- **对比逻辑**：将 58 个模型按家族、任务、模态进行交叉比较，并特别对比 agentic 与非 agentic 模型在任务覆盖和领域覆盖上的差异（如 agentic 更侧重注释、公平性和新兴范式，非 agentic 更侧重生物 grounding、批次效应和轨迹/扰动任务）。
- **补充基准建议**：提出一个轻量级“参考面板”基准——每个任务选取 1–2 个常用数据集（如 PBMC、Visium DLPFC、sci-Plex），选择少量代表性模型进行标准化评估，用于验证综述层面的定性结论。

## 4. 资源与算力

- **论文未明确报告统一的训练算力信息**。作者指出，不同原始研究对模型规模、训练成本、硬件需求、预处理流程的报告极不一致，因此无法进行直接的资源对比或元分析。
- 文中个别信息点包括：
  - CellFM 展示了在 1 亿个人类细胞上的训练可行性；
  - 部分高效架构（如 xTrimoGene、GeneMamba、scMamba）旨在降低内存和计算成本；
  - 常见模型参数量下限为 ≥10M，但具体 GPU 型号、数量、训练时长等均未系统披露。

## 5. 实验数量与充分性

- **数量层面**：覆盖 58 个模型、40+ 数据集、8 项任务、10 个评估维度，并提供了详细附录（模型比较表、数据集汇总表），在综述类工作中规模较大。
- **充分性评价**：
  - **优点**：分类体系细致，数据集覆盖面广，不仅包括主流 RNA 图谱，还纳入空间、表观、植物和扰动数据；评估过程采用双人独立标注、第三人仲裁的流程，并发布可审计的注册表，增强了可复现性。
  - **不足**：所有评估基于原文作者自报的能力和结果，存在明显的“报告偏差”——模型可能被高估或低估取决于原始论文的实验严格程度；没有进行独立复现或统一基准测试；未计算形式化的标注一致性指标；原始研究间数据集、指标、预处理差异巨大，因而无法做量化元分析，只能做定性趋势判断。
  - **结论**：作为综述和分类学工作，实验设计是合理的，但作为“评估”而言，更像是对报告实践的映射，而非严格意义上的公平横向评测。

## 6. 论文的主要结论与发现

- **推理/自主性宣称往往超过实际评估**，尤其是智能体系统缺少标准化基准，多步推理和工具使用仍较脆弱，提示词敏感性和工具序列不稳定性是常见失败模式。
- **性能提升更常与数据规模和配对模态相关，而非架构创新本身**；大规模 RNA 图谱和配对多组学数据是表现提升的主要驱动因素。
- **语言 grounding 能改善可解释性，但并不能可靠地带来生物学因果性**，除非显式加入约束或推理层。
- **智能体方法目前仅在注释类任务上表现最稳定**，在其他任务上相对非智能体的优势并不明确。
- **评估不均衡**：注释和整合任务已有较成熟基准；轨迹推断、药物反应、智能体推理缺少标准化协议；跨物种和隐私相关任务覆盖严重不足。
- **数据偏差严重**：人类和小鼠的免疫细胞/常见组织数据占主导，植物、微生物、稀有细胞和多样化人群数据稀缺，限制泛化并带来公平性风险。
- **可解释性仍是短板**：多数基础模型只提供注意力可视化或基因排序，缺乏因果透明度；隐私保护（如联邦学习）几乎未被采用。

## 7. 优点

- **数据与评估中心视角**：不同于以架构为中心的综述，系统地把数据集、模型家族和评估实践联系起来，揭示数据可用性如何约束模型能力宣称。
- **分类法清晰且务实**：五大家族划分、八项任务映射、十维度评估准则均具有较强操作性，并明确区分“模型设计意图”与“实证评估证据”。
- **智能体作为独立类别**：将 agentic/tool-augmented 系统作为一等方法类别处理，并分析其失败模式，比既有综述更完整。
- **可复现性和可审计性设计**：发布机器可读的补充注册表，明确标注 Present/Partial/Absent，并说明边界案例判定规则（如 text-bridge 与 multimodal 的区分标准），允许读者重新聚合和扩展。
- **面向跨社区可读性**：为 NLP 和生物学读者都提供了术语解释、分层导航和结构化摘要。

## 8. 不足与局限

- **依赖原始论文自报证据**：未进行独立复现或统一评估，结论受报告偏差影响；作者也承认这项工作是“快照”式综述。
- **缺少正式定量分析**：由于各研究间数据集、指标、预处理不一致，无法进行效果量估计或统计显著性检验，只能给出定性趋势。
- **计算效率与超参敏感性未评估**：模型大小、训练成本、硬件需求等信息普遍缺失，限制了实用性参考价值。
- **资源和数据覆盖仍有缺口**：部分临床和专有空间数据因访问限制未纳入；非动物（植物、微生物）资源仍稀缺。
- **评估维度偏“是否被报告”而非“表现好坏”**：Domains Covered 计数表示覆盖数而非质量，可能被误读为模型优劣。
- **标注过程未提供形式化一致性指标**，虽然采用双人标注和仲裁，但未报告 inter-annotator agreement。
- **伦理风险提示充分但未提供解决方案**：数据隐私、模型幻觉、数据偏倚等风险被列出，但论文本身不提出联邦学习、公平性约束等具体缓解手段。

（完）
