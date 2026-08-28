---
title: "RiboRep: Replicate-Aware Cross-Modal Transformers for Codon-Resolved Ribosome Density Prediction"
title_zh: "RiboRep: 用于密码子分辨率核糖体密度预测的复制感知跨模态Transformer"
authors: "Kuo, A., Yue, Z., Ku, W.-S., Chen, H."
date: 2026-08-07
pdf: "https://www.biorxiv.org/content/10.64898/2026.08.03.742524v1.full.pdf"
tags: ["query:gene-perturb"]
score: 8.0
evidence: 明确面向扰动响应与分子状态模拟，服务于生物数字孪生
tldr: 核糖体谱分析提供核苷酸分辨率翻译测量，但现有预测多在密码子水平，丢失关键细粒度信号。RiboRep作为重复感知跨模态Transformer，通过双流卷积、RoPE自注意力、非对称交叉注意力和重复感知标记，联合建模RNA序列与参考核糖体占用。在细菌、酵母、植物数据集上取得竞争性或更优性能，尤其植物重复丰富数据。该框架支持重建和模拟翻译状态，助力翻译感知分子数字孪生。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有核糖体密度预测多在密码子水平操作，丢失细粒度翻译信号，难以支持翻译感知数字孪生的构建。
method: 提出RiboRep，采用双流卷积编码器、RoPE自注意力、非对称交叉注意力及重复感知条件标记，联合建模RNA序列与核糖体占用。
result: 在细菌、酵母和植物数据集上取得竞争性或更优性能，尤其在重复丰富的植物数据集上表现突出。
conclusion: 为翻译感知的分子数字孪生奠定基础，可模拟核糖体占用景观和条件特异调控程序。
---

## 摘要
核糖体谱分析能够在核苷酸分辨率下对翻译进行全基因组测量，并提供不同生物学条件下细胞蛋白质合成的动态视图。现有的计算方法主要基于密码子级别的表示，可能丢失对建模上下文依赖性细胞反应至关重要的细粒度翻译信号。这种预测性翻译建模对于新兴的生物数字孪生越来越重要，因为准确模拟分子状态动力学需要表征细胞适应、扰动反应和表型进展。我们提出了RiboRep，一种用于密码子分辨率核糖体密度预测的复制感知跨模态Transformer。RiboRep使用双流卷积编码器、基于RoPE的自注意力、非对称交叉注意力和复制感知条件令牌，联合建模核苷酸分辨率的RNA序列和参考核糖体占用信号。通过显式建模复制特异性变异并将序列上下文与实验观测的翻译活性整合，RiboRep提供了一个跨生物学条件重建和模拟翻译状态的框架。在细菌、酵母和植物核糖体谱数据集上，RiboRep与现有基线相比取得了竞争性或改进的性能，在复制丰富的植物数据集上尤其有显著提升。消融研究进一步证明了局部密码子感知特征提取、复制感知条件和门控读出的重要性。除了预测性能之外，所提出的框架为翻译感知的分子数字孪生奠定了基础，能够以密码子分辨率建模核糖体占用景观、扰动诱导的翻译反应和条件特异性调控程序。

## Abstract
Ribosome profiling enables genome-wide measurement of translation at nucleotide resolution and provides a dynamic view of cellular protein synthesis under diverse biological conditions. Existing computational approaches primarily operate on codon-level representations, potentially losing fine-grained translational signals critical for modeling context-dependent cellular responses. Such predictive translational modeling is increasingly important for emerging biological digital twins, where accurate simulation of molecular-state dynamics is required to characterize cellular adaptation, perturbation response, and phenotype progression. We present RiboRep, a replicate-aware cross-modal transformer for codon-resolved ribosome density prediction. RiboRep jointly models nucleotide-resolution RNA sequences and reference ribosome occupancy signals using dual-stream convolutional encoders, RoPE-based self-attention, asymmetric cross-attention, and replicate-aware conditioning tokens. By explicitly modeling replicate-specific variation and integrating sequence context with experimentally observed translational activity, RiboRep provides a framework for reconstructing and simulating translational states across biological conditions. Across bacterial, yeast, and plant ribosome profiling datasets, RiboRep achieves competitive or improved performance compared with existing baselines, with particularly strong gains on replicate-rich plant datasets. Ablation studies further demonstrate the importance of local codon-aware feature extraction, replicate-aware conditioning, and gated readout. Beyond predictive performance, the proposed framework establishes a foundation for translation-aware molecular digital twins capable of modeling ribosome occupancy landscapes, perturbation-induced translational responses, and condition-specific regulatory programs at codon resolution. 1