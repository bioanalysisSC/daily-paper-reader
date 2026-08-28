---
title: "VariantFlux: A genotype-first modelling workflow for predicting the impact of genetic variations on human metabolism"
title_zh: VariantFlux：一种基因型优先的建模工作流程，用于预测遗传变异对人类代谢的影响
authors: "Nazem-Bokaee, H."
date: 2026-08-09
pdf: "https://www.biorxiv.org/content/10.64898/2026.08.03.740213v1.full.pdf"
tags: ["query:gene-perturb"]
score: 6.0
evidence: 利用基因组规模代谢建模预测遗传变异对代谢的影响
tldr: 人类遗传变异如何影响器官代谢仍不清楚。VariantFlux将有害变异转化为基因剂量锚定的通量约束，构建个性化肾脏代谢模型。对千人基因组计划两千五百四十七人的分析显示，尽管约百分之五十代谢基因被预测有害，超过百分之九十七模型仍维持基线生长，表明代谢具有强稳健性。该流程从基因组直接预测器官通量表型，为精准医学提供机制性工具。
source: biorxiv
selection_source: fresh_fetch
motivation: 人类遗传变异如何影响器官代谢尚不清楚，需要将基因组变异与代谢表型直接关联的机制性方法。
method: 提出VariantFlux，将变异效应整合到肾脏特异性基因组代谢模型，通过基因剂量锚定约束模拟敲除和敲低。
result: 对二千五百四十七人分析显示，尽管大量有害变异，超过百分之九十七模型维持生长，但个体间具有独特的通量重布线模式。
conclusion: VariantFlux能从基因组直接预测器官通量表型，为精准医学和疾病风险预测提供机制性方案。
---

## 摘要
人类遗传变异是器官代谢的主要决定因素，但自然发生的变异如何塑造定量代谢表型仍不清楚。我们提出了VariantFlux，一个将祖先感知的变异解释整合到基因组规模代谢建模中的工作流程，以生成个性化的、变异约束的肾脏重建模型。使用Human1 v1.19模型，我们构建了一个受482种代谢物约束的肾脏特异性基线模型，并分析了1000基因组计划中的2547个个体，其中约50%的代谢基因被至少三种计算工具预测为有害。这些在祖先间负担略有差异的变异被转化为基因剂量锚定的通量约束，用于纯合敲除和分级杂合敲低。尽管存在广泛的扰动，>97%的模型保持了基线生长，表明代谢具有强大的稳健性。然而，个体基因组表现出独特的通量重布线模式，频繁出现个体特异性的通量增加事件，而共享的通量减少反应较少。有限的祖先聚类表明代谢反应主要由独特的变异组合驱动。VariantFlux将人类基因组与器官水平的通量表型联系起来，为精准医学、药物基因组学和疾病风险预测提供了支持。

概念进展：我们提出了VariantFlux，一个基因型优先的框架，将预测的变异效应直接整合到基因组规模代谢网络中，以生成个性化的、器官特异性的通量表型。与基于关联的代谢组学研究不同，这种自下而上的方法能够探索性地、机制性地预测自然发生的遗传变异如何重塑人类代谢。

## Abstract
Human genetic variation is a major determinant of organ metabolism, yet how naturally occurring variants shape quantitative metabolic phenotypes remains unclear. We present VariantFlux, a workflow that integrates ancestry-aware variant interpretation into genome-scale metabolic modelling to generate personalised, variant-constrained kidney reconstructions. Using the Human1 v1.19 model, we built a kidney-specific baseline model constrained by 482 metabolites and analysed 2,547 individuals from the 1000 Genomes Project, in whom [~]50% of metabolic genes were predicted damaging by at least three computational tools. These variants, whose burden differed subtly across ancestries, were translated into gene-dosage-anchored flux constraints for homozygous knockouts and graded heterozygous knockdowns. Despite widespread perturbation, >97% of models preserved baseline growth, indicating strong metabolic robustness. Yet individual genomes exhibited distinct flux-rewiring patterns, with frequent individual-specific gain-of-flux events and fewer shared loss-of-flux reactions. Limited ancestry clustering suggests metabolic responses are driven mainly by unique variant combinations. VariantFlux links human genomes to organ-level flux phenotypes, enabling precision medicine, pharmacogenomics, and disease risk prediction.

Conceptual advanceWe present VariantFlux, a genotype-first framework that integrates predicted variant effects directly into genome-scale metabolic networks to generate personalised, organ-specific flux phenotypes. Unlike association-based metabolomics studies, this bottom-up approach enables exploratory, mechanistic prediction of how naturally occurring genetic variation reshapes human metabolism.