---
title: Learning activator-inhibitor dynamics at the cell cortex with neural likelihood ratio estimation
title_zh: 学习细胞皮层中的激活子-抑制子动力学：基于神经似然比估计
authors: "Maxian, O., Munro, E., Dinner, A."
date: 2026-07-30
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.06.722433v2.full.pdf"
tags: ["query:gene-perturb"]
score: 6.0
evidence: 基于神经网络的仿真推断用于细胞皮层激活-抑制动力学
tldr: 细胞尺度模式如何由分子相互作用产生，是细胞生物学的核心问题。本文采用神经似然比估计的模拟推断框架，通过正则化分类网络近似似然函数，从实验数据中推断F-actin组装动力学参数。关键结果发现，已知的RhoGAP功能不足以解释实验观察到的Rho活性波频率增加，提示其可能通过降低纤维成核速率来维持波。研究给出了具体可检验的预测，并展示了传统前向模型与现代神经网络推断工具结合的有效性。
source: biorxiv
selection_source: fresh_fetch
motivation: 细胞尺度模式如何从分子规则涌现，需结合实验扰动、数学建模与参数推断，而传统推断方法难以处理复杂似然。
method: 采用神经似然比估计进行模拟推断，利用正则化分类神经网络近似数据似然，并对模型误设进行鲁棒化处理。
result: 成功从实验数据推断F-actin组装动力学，发现RhoGAP已知功能不足以解释波频率变化，提出其通过降低纤维成核速率来维持波。
conclusion: 提供具体可测试预测，展示传统前向模型与神经推断结合可有效揭示细胞自组织机制。
---

## 摘要
细胞生物学中的一个关键问题是，细胞尺度的组织如何从一组给定的分子组分及其相互作用规则中涌现。鉴于其多尺度特性，解决这一问题需要结合实验扰动、数学建模和参数推断。我们利用这些领域近年来的进展，特别关注基于神经网络的模拟推断方法，来研究Rho GTP酶活性的细胞尺度模式如何由肌动蛋白丝上的分子尺度激活子-抑制子相互作用所定义。利用已有的该相互作用模型，我们证明了一个过度表达的正则化分类神经网络能够近似从特定参数集产生的数据的似然。我们表明，F-肌动蛋白组装动力学的变化可以直接从实验数据中推断出来，但前提是网络对模型错误设定的敏感性降低。我们使用该方法来解释扰动实验，其中增加RhoGAP共表达会增加非洲爪蟾卵中Rho活性波的频率和相干性。在表明RhoGAP的已知功能不足以解释实验观察到的动力学之后，我们使用神经方法提出了另一种途径，通过该途径RhoGAP可能降低细丝成核速率以维持波。我们的工作产生了具体的、可实验验证的预测，并说明了传统前向模型与现代推断工具的结合如何有助于揭示自组织机制。

## Abstract
A key question in cell biology is how cell-scale organization emerges from a given set of molecular players and rules of interaction. Given its multiscale nature, addressing this question requires a combination of experimental perturbation, mathematical modeling, and parameter inference. We leverage recent advances in each of these fields, focusing in particular on neural-network methods for simulation-based inference, to study how cell-scale patterns of Rho GTPase activity are defined by molecular-scale activator-inhibitor interactions with filamentous actin. Using an existing model of this interaction, we demonstrate that an over-expressive, regularized classification neural network can approximate the likelihood of data arising from a particular parameter set. We show that variations in F-actin assembly dynamics can be inferred directly from experimental data, but only if the network is made less sensitive to model misspecification. We use our approach to interpret perturbation experiments in which increasing RhoGAP coexpression increases the frequency and coherence of Rho activity waves in frog eggs. After showing that the known functions of RhoGAP are insufficient to explain experimentally-observed dynamics, we use neural methods to suggest an alternative pathway by which RhoGAP could decrease filament nucleation rates to sustain waves. Our work yields specific, experimentally-testable predictions and illustrates how a combination of traditional forward models and modern inference tools can aid in unraveling mechanisms of self-organization.