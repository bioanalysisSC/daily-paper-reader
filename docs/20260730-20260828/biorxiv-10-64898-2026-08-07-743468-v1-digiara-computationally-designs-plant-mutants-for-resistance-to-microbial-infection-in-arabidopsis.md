---
title: DigiAra Computationally Designs Plant Mutants for Resistance to Microbial Infection in Arabidopsis
title_zh: DigiAra计算设计抗微生物感染的拟南芥突变体
authors: "Bai, T., Cui, S., You, Y."
date: 2026-08-07
pdf: "https://www.biorxiv.org/content/10.64898/2026.08.07.743468v1.full.pdf"
tags: ["query:gene-perturb"]
score: 9.0
evidence: 模拟遗传扰动的转录效应并筛选候选突变体
tldr: 植物育种依赖多年田间筛选，耗时费力且效率低下，缺乏计算设计工具。DigiAra提出模拟评分筛选流程，融合局部基因交互与全局转录状态建模，预测遗传扰动和微生物感染的转录变化。在整合四百九十五个样本训练下，预测精度达零点四九，重现非自身响应程序，并筛选出二十七个增强抗性的敲除靶点，其中九个已有文献支持。该工作为拟南芥突变体计算设计提供了开放有效平台。
source: biorxiv
selection_source: fresh_fetch
motivation: 植物育种依赖多年田间筛选，过程低效且成本高昂，亟需计算工具辅助设计。
method: 构建模拟-评分-筛选流程，融合局部基因交互与全局转录建模，并整合多源转录组数据。
result: 预测未扰动表达变化相关达0.49，重现非自身响应，筛选出27个抗性敲除，9个获文献支持。
conclusion: 该框架为拟南芥突变体计算设计提供有效方案，并可扩展至作物抗性育种。
---

## 摘要
植物育种是一个资源密集型的过程，需要多代重复栽培和选择才能培育出具有理想性状的品种，然而能够支持这一过程的计算工具仍然有限。在此，我们介绍了DigiAra，一个基于人工智能的框架，用于设计具有目标性状（尤其是增强微生物抗性）的拟南芥突变体。DigiAra实现了S3流程——模拟、评分和筛选：它模拟遗传扰动和微生物感染的转录效应，通过生物通路分析对预测的反应进行相关性状评分，并在多个水平上筛选候选扰动。通过这种方式，DigiAra使得在拟南芥中计算探索遗传扰动和多种微生物感染的全基因组效应成为可能。为了开发DigiAra，我们解决了两个基本挑战。在方法论上，我们引入了一种混合架构，将局部基因水平相互作用建模与全局转录状态建模相结合，以预测扰动引起的拟南芥转录状态变化。从数据角度看，我们建立了一个标准化流程，用于整理、协调和处理一个整合的拟南芥-微生物转录组数据集，该数据集包含来自26个项目的495个样本。因此，DigiAra能准确预测由未观察到的遗传扰动和微生物感染诱导的基因表达变化，达到了0.49的皮尔逊相关系数。此外，它重现了通用非自身反应（GNSR），这是一个24基因程序，反映了跨细菌扰动的广泛转录重编程。在一项独立研究中，预测的模式触发免疫通路评分进一步与细菌载量相关，皮尔逊相关系数为0.57。最后，我们应用DigiAra通过全基因组筛选鉴定了27个基因敲除，这些敲除被预测能增强对丁香假单胞菌番茄致病变种DC3000（Pst DC3000）的抗性，同时限制生长受损，其中9个得到了已发表研究的支持。总之，这些结果确立了DigiAra作为拟南芥突变体计算设计的有效框架。我们已在https://github.com/youlab2025/DigiAra公开提供我们的实现。

## Abstract
Plant breeding is a resource-intensive process that requires repeated cultivation and selection across multiple generations to develop varieties with desirable traits, yet computational tools capable of supporting this process remain limited. Here, we present DigiAra, an AI-based framework for designing Arabidopsis thaliana mutants with targeted traits, particularly enhanced microbial resistance. DigiAra implements an S3 pipeline--simulation, scoring, and screening: it simulates the transcriptional effects of genetic perturbations and microbial infections, scores the predicted responses in terms of relevant traits through biological pathway analysis, and screens candidate perturbations at multiple levels. In doing so, DigiAra enables the computational exploration of the genome-wide effects of genetic perturbations and diverse microbial infections in Arabidopsis. To develop DigiAra, we address two fundamental challenges. Methodologically, we introduce a hybrid architecture that integrates local gene-level interaction modeling with global transcriptional-state modeling to predict perturbation-induced changes in the Arabidopsis transcriptional state. From a data perspective, we establish a standardized pipeline for curating, harmonizing, and processing an integrated Arabidopsis-microbe transcriptional dataset comprising 495 samples from 26 projects. As a result, DigiAra accurately predicts gene-expression changes induced by unobserved genetic perturbations and microbial infections, achieving a Pearson correlation of 0.49. Moreover, it recapitulates the general non-self response (GNSR), a 24-gene program reflecting broad transcriptional reprogramming across bacterial perturbations. In an independent study, the predicted pattern-triggered immunity pathway scores further correlate with bacterial load, with a Pearson correlation of 0.57. Lastly, we deploy DigiAra to identify 27 gene knockouts through genome-wide screening that are predicted to enhance resistance to Pseudomonas syringae pv. tomato DC3000 (Pst DC3000) while limiting growth compromise, 9 of which are supported by published studies. Together, these results establish DigiAra as an effective framework for the computational design of Arabidopsis mutants. We have made our implementation openly available at https://github.com/youlab2025/DigiAra.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **行业痛点**：植物育种是一个资源密集型过程，需要多代重复栽培和田间筛选，周期长、成本高、效率低下。
- **现有缺口**：尽管育种流程高度依赖经验与田间试验，能够辅助这一过程的计算设计工具仍然十分有限。
- **核心动机**：亟需一个可计算、可扩展的框架，让研究人员能够在实验之前，就在计算机上探索遗传扰动（如基因敲除）对目标性状（如微生物抗性）的影响。
- **研究目标**：构建一个名为 **DigiAra** 的 AI 框架，用于在模式植物拟南芥（*Arabidopsis thaliana*）中计算设计具有增强微生物抗性等目标性状的突变体，为作物抗性育种提供可迁移的计算范式。

## 2. 论文提出的方法论

- **总体架构：S3 流程（模拟—评分—筛选，Simulation-Scoring-Screening）**
  - **模拟（Simulation）**：预测给定遗传扰动（如单基因敲除）和微生物感染（如细菌侵染）下的全基因组转录变化。
  - **评分（Scoring）**：通过生物通路分析（如模式触发免疫 PTI 通路）对预测的转录响应进行性状相关评分，判断该扰动是否有利于目标性状。
  - **筛选（Screening）**：在全基因组水平上对候选扰动进行筛选，识别能增强抗性且不显著影响生长的基因敲除靶点。
- **核心模型：混合架构（Hybrid Architecture）**
  - **局部基因水平交互建模**：捕捉基因与基因之间的局部调控关系（如共表达模块、调控网络边）。
  - **全局转录状态建模**：捕捉整个转录组的整体状态变化（如处理条件、发育阶段等全局因子）。
  - 将两者融合，同时获得局部生物学信息与全局系统性信息，从而准确预测扰动引起的转录状态变化。
- **数据处理流程**：建立了一套标准化的整理、协调与处理流程，将来自 26 个项目的 495 个拟南芥-微生物转录组样本整合为一个统一的数据集，用于模型训练和评估。

## 3. 实验设计

- **训练数据集**：整合的拟南芥-微生物转录组数据集，包含 26 个项目、495 个样本，覆盖多种遗传扰动与多种微生物感染条件。
- **基准与评估场景**：
  - **预测未观测扰动/感染的表达变化**：在未参与训练的遗传扰动和微生物感染条件下测试模型，以皮尔逊相关系数衡量预测值与原位表达变化的一致性（结果：0.49）。
  - **重现通用非自身反应（GNSR）**：检验模型能否重现一个由 24 个基因组成的、广泛细菌扰动的通用转录重编程程序。
  - **独立研究验证**：在一项独立的实验中，用模型预测 PTI 通路评分，并与实际细菌载量计算相关性（皮尔逊相关系数：0.57）。
  - **全基因组筛选**：应用模型对全基因组基因敲除进行筛选，识别能够增强对 *Pst DC3000* 抗性且限制生长受损的靶点。
- **对比方法**：论文摘要中未明确提及其他基线方法的对比（如传统差异表达分析、单一图神经网络或仅全局模型等），因此无法确认是否做了系统性方法学对比。

## 4. 资源与算力

- **未明确说明**：论文提供的摘要和元数据中**没有**提及使用的 GPU 型号、数量、训练时长、显存占用或计算集群规模等算力信息。
- 考虑到模型规模和数据量（495 个样本），推测训练成本不会过于庞大，但论文文本中未给出任何具体数字。

## 5. 实验数量与充分性

- **实验组数**：
  - 模型预测精度评估（未观测扰动/感染）。
  - GNSR 24 基因程序重现。
  - PTI 通路评分与细菌载量的独立相关系数评测。
  - 全基因组敲除筛选（筛选出 27 个基因，其中 9 个获文献支持）。
- **充分性分析**：
  - **覆盖面较好**：包含了预测能力和生物学可解释性验证（GNSR 重现）、外部表型验证（细菌载量）以及实际育种靶点筛选（文献验证），形成了较为完整的证据链。
  - **缺少消融实验**：摘要中未提及对混合架构（局部 vs 全局）的消融分析，无法判断每个组件的独立贡献。
  - **未提及其他模型对比**：没有与已有的回归模型、图神经网络或传统统计方法进行公开基准比较，公平性难以从摘要层面确认。
  - **筛选靶点验证率**：27 个靶点中仅 9 个（约 1/3）有文献支持，剩余靶点缺乏实验验证，筛选的精确率有待进一步考察。

## 6. 论文的主要结论与发现

- DigiAra 能**准确预测**由未观测遗传扰动和微生物感染引起的基因表达变化（Pearson 0.49）。
- 模型能够**重现 GNSR**（24 基因通用非自身反应程序），表明其预测不限于表面相关性，而是捕捉到了有生物学意义的系统性转录重编程。
- 在独立研究中，**PTI 通路评分与细菌载量显著相关**（Pearson 0.57），说明基于通路的评分可作为抗性表型的有效代理。
- 全基因组筛选得到 **27 个预测可增强 *Pst DC3000* 抗性的基因敲除靶点**，其中 9 个已有文献支持，证明了该框架的实际筛选价值。
- 总体而言，DigiAra 被确立为拟南芥突变体计算设计的**有效框架**，并已开源其实现。

## 7. 优点

- **创新性架构**：将局部基因交互建模与全局转录状态建模结合的混合架构，在方法学上有明显创新，兼顾了精细调控与系统性状态变化。
- **数据工程量扎实**：整合 26 个项目、495 个样本并建立标准化梳理流程，解决了多源转录组数据异质性这一实际障碍，为其他类似工作提供了数据范式。
- **完整且可落地的 S3 流程**：从模拟、评分到筛选，形成了一条可执行的完整计算设计流水线，直接面向育种实际需求。
- **多维度验证**：不仅报告了预测精度，还通过 GNSR 生物学程序重现、独立表型数据关联以及文献靶点回溯，从多个角度交叉验证了模型的可靠性与实用性。
- **开放共享**：公开代码仓库（GitHub），利于复现和社区扩展。

## 8. 不足与局限

- **物种局限**：目前仅基于拟南芥数据训练和验证，虽然拟南芥是模式植物，但迁移到作物（如水稻、小麦、玉米）时仍需重新训练和适配跨物种转移能力。
- **预测精度有限**：Pearson 0.49 说明仍有较大部分表达变化方差未能解释，对弱效应扰动或复杂环境互作的预测可靠性有待提升。
- **缺乏消融与对比实验**：摘要中未展示混合架构各组件的消融分析，也未见与现有方法的系统性对比，这削弱了方法学贡献的说服力。
- **筛选靶点验证率不高**：27 个预测靶点中 18 个未见文献支持，可能存在较多假阳性，需要湿实验进一步确认。
- **生长代价评估粗略**：虽然声称筛选时限制生长受损，但摘要未给出量化指标或具体评估方式，对"抗性-生长权衡"的处理缺乏细节。
- **算力与资源信息缺失**：未报告训练时间、硬件配置等信息，不利于其他研究者评估复现成本。
- **实验验证闭环缺失**：所有结果均为计算预测，论文中未提及对任何候选突变体开展实际生物学验证实验，因此严谨地说，这是一个计算框架的方法论文，其生物学落地仍需实验确认。

（完）
