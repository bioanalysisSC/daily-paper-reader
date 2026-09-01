---
title: "NucEL: Single-Nucleotide ELECTRA-Style Genomic Pre-training for Efficient and Interpretable Representations"
title_zh: NucEL：单核苷酸ELECTRA式基因组预训练实现高效可解释表征
authors: "Ke Ding, Brian Parker, Jiayu Wen"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/36982/40944"
tags: ["query:gene-perturb"]
score: 4.0
evidence: 基因组语言模型预训练方法，可作为扰动预测推理的骨干
tldr: 针对遮蔽语言建模（MLM）式基因组预训练存在部分监督、预训练与微调不匹配以及高计算成本的问题，NucEL提出首个ELECTRA式基因组预训练框架，通过生成器与判别器配合对所有序列位置进行全监督学习。该方法在提升表示质量的同时降低了计算开销，并为基因组下游任务提供了更高效、可解释的基础模型。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 现有基因组预训练如DNABERT和Nucleotide Transformer依赖MLM，存在监督不充分、预训练与微调不一致且计算成本高的问题。
method: NucEL采用ELECTRA式预训练，用生成器替换部分token，由判别器识别所有位置的原始替换token，实现全位置监督。
result: 实验表明NucEL在多个基因组下游任务上优于MLM式方法，且训练效率更高，表示更具可解释性。
conclusion: 该框架为基因组基础模型提供了一种高效且可解释的预训练新范式，有望支持多种下游生物学预测任务。
---

## Abstract
Pre-training large language models on genomic sequences has become a powerful approach for learning biologically meaningful representations. While masked language modeling (MLM)-based approaches, such as DNABERT and Nucleotide Transformer (NT), achieve strong performance, they are hindered by inefficiencies due to partial token supervision, pre-training/fine-tuning mismatches, and high computational costs. We introduce NucEL, the first ELECTRA-style pre-training framework for genomic foundation models, which overcomes these challenges. Through a discriminator network identifying tokens modified by a generator, NucEL achieves comprehensive token-level supervision across all sequence positions, thereby markedly improving training efficiency relative to the partial supervision of masked positions inherent in MLM frameworks. By integrating ModernBERT’s architectural advancements, including hybrid local-global attention and flash attention mechanisms, NucEL establishes an optimized BERT architecture for genomic sequence modeling. Unlike traditional methods that tokenize genomic sequences into 6-mers, NucEL implements single-nucleotide tokenization, enabling fine-grained resolution and improving both efficiency and interpretability. Pre-trained on the human genome only, NucEL achieves state-of-the-art performance on benchmark datasets across diverse downstream tasks in both human and non-human species, including regulatory element identification (e.g., promoters, enhancers), transcription factor binding prediction in human and mouse, open chromatin region classification, and histone modification profiles, surpassing MLM-based models of similar size and rivaling models 25 times larger, such as NT. Ablation studies provide critical insights into tokenization and masking strategies, optimizing ELECTRA-style pretraining for DNA sequences. Attention analyses reveal NucEL’s superior ability to capture biologically relevant sequence motifs compared to NT, offering valuable insights into its hierarchical learning process and regulatory element modeling capabilities. This work highlights the potential of ELECTRA-style pretraining as an efficient and effective strategy for advancing genomic representation learning with broad implications for future genomic research.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
基因组语言模型预训练方法，可作为扰动预测推理的骨干。

### 2. 核心内容
针对遮蔽语言建模（MLM）式基因组预训练存在部分监督、预训练与微调不匹配以及高计算成本的问题，NucEL提出首个ELECTRA式基因组预训练框架，通过生成器与判别器配合对所有序列位置进行全监督学习。该方法在提升表示质量的同时降低了计算开销，并为基因组下游任务提供了更高效、可解释的基础模型。

### 3. 对应检索需求
large language model for gene perturbation prediction inference。

### 4. 来源与原文
- Source：AAAI-2026-Accepted
- OpenReview：[https://ojs.aaai.org/index.php/AAAI/article/view/36982](https://ojs.aaai.org/index.php/AAAI/article/view/36982)
