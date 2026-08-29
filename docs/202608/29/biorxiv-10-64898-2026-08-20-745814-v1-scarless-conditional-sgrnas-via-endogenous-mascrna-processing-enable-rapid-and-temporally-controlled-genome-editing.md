---
title: Scarless conditional sgRNAs via endogenous mascRNA processing enable rapid and temporally controlled genome editing
title_zh: 通过内源mascRNA加工实现无疤痕条件性sgRNA，支持快速和时间可控的基因编辑
authors: "Hart, C., Devakumar, L. P. S., Saeed, K., Spruce, A., Mastrokalou, C., Lukasiak, S., Ross-Thriepland, D., Walter, D., Gupta, N."
date: 2026-08-21
pdf: "https://www.biorxiv.org/content/10.64898/2026.08.20.745814v1.full.pdf"
tags: ["query:gene-perturb"]
score: 6.0
evidence: 无疤痕条件性sgRNA平台支持时间可控基因组编辑，提升汇合扰动筛选效果
tldr: "现有Cre-loxP条件性sgRNA开关在激活后会在成熟sgRNA的5'端残留loxP疤痕序列，削弱引导效率。本文提出无疤痕条件性sgRNA平台，通过将mascRNA模块置于引导序列上游，利用Cre重组后内源RNase P/RNase Z切除残余序列，恢复天然sgRNA末端。与传统开关相比，该设计在保持严格OFF状态的同时，显著提升ON状态编辑性能，表现为更快的编辑动力学、更高的扰动渗透率和更一致的编辑效率。这种模块化策略简单通用，为时间分辨功能基因组学和汇集筛选提供了高效工具。"
source: biorxiv
selection_source: fresh_fetch
motivation: "现有Cre-loxP sgRNA开关会在成熟gRNA上留5'疤痕，损害功能；需一种保持gRNA完整性且可时间调控的编辑方法。"
method: "在引导RNA上游添加mascRNA模块，利用Cre重组后内源RNase P/Z切除loxP残留，恢复天然5'末端。"
result: 相对于常规Cre激活开关，无疤痕设计在严格OFF态下提升ON态编辑性能，包括更快动力学、更高渗透率和一致性。
conclusion: 模块化条件编辑策略保持gRNA完整性，为时间分辨功能基因组学及汇集筛选提供简便高效方案。
---

## 摘要
基因编辑的精确时间控制对于研究动态生物学过程、探究必需基因功能以及提高汇集性扰动筛选的可解释性至关重要。Cre依赖性单向导RNA（sgRNA）开关通过将向导激活与位点特异性重组偶联来提供时间调控，但现有设计在成熟sgRNA上保留了源自loxP的5'序列（疤痕），这可能损害向导功能。我们开发了一种无疤痕条件性sgRNA平台，该平台将Cre-loxP重组与内源RNA加工相结合，以在诱导后恢复天然sgRNA结构。一个MALAT1相关小胞质RNA（mascRNA）模块被定位在向导序列上游，使得在Cre介导的重组后，细胞RNase P和RNase Z去除残留的loxP衍生突出端，生成具有真实5'末端的成熟sgRNA。使用靶向内源细胞表面标志基因的向导，与常规Cre激活sgRNA开关相比，无疤痕设计保持了严格的OFF状态控制，同时提高了ON状态编辑性能，导致更快的编辑动力学、更大的扰动穿透率和更一致的编辑效率。这种模块化策略为条件性CRISPR基因组编辑提供了一种简单方法，保留了向导完整性，并且应易于适应时间分辨功能基因组学和汇集筛选应用。

## Abstract
Precise temporal control of gene editing is essential for studying dynamic biological processes, interrogating essential gene function, and improving the interpretability of pooled perturbation screens. Cre-dependent single guide RNA (sgRNA) switches provide temporal regulation by coupling guide activation to site-specific recombination, but existing designs retain a loxP-derived 5' sequence (scar) on the mature sgRNA that can impair guide function. We developed a scarless conditional sgRNA platform that combines Cre-loxP recombination with endogenous RNA processing to restore the native sgRNA architecture following induction. A MALAT1-associated small cytoplasmic RNA (mascRNA) module was positioned upstream of the guide sequence such that, after Cre-mediated recombination, cellular RNase P and RNase Z remove the residual loxP-derived overhang, generating a mature sgRNA with an authentic 5' terminus. Using guides targeting endogenous cell-surface marker genes, the scarless design maintained stringent OFF-state control while improving ON-state editing performance compared with a conventional Cre-activated sgRNA switch, resulting in faster editing kinetics, greater perturbation penetrance, and more consistent editing efficiency. This modular strategy provides a simple approach for conditional CRISPR genome editing that preserves guide integrity and should be readily adaptable to time-resolved functional genomics and pooled screening applications.