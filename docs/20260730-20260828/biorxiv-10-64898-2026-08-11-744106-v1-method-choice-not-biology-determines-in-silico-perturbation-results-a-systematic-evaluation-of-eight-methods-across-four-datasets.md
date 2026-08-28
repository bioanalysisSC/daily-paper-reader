---
title: "Method Choice, Not Biology, Determines In Silico Perturbation Results: A Systematic Evaluation of Eight Methods Across Four Datasets"
title_zh: 决定计算扰动结果的是方法选择而非生物学：跨四个数据集的八种方法的系统评估
authors: "Wenjie, G., Wu, S., Hu, G., Yang, Z., Wang, Z., Cai, J., Mao, J."
date: 2026-08-19
pdf: "https://www.biorxiv.org/content/10.64898/2026.08.11.744106v1.full.pdf"
tags: ["query:gene-perturb"]
score: 9.0
evidence: 对单细胞转录组扰动预测方法进行系统评估，直接比较八种方法
tldr: 大多数单细胞转录组扰动预测方法仅在单一数据集验证，可靠性未知。系统评估八种方法于四个数据集，发现六种方法无法检测转录因子到通路信号，仅CellOracle和DDIM稳定有效。方法选择可逆转结论，CRISPRi验证显示预测方向与实验不符，揭示稳态相关与因果扰动的根本差距。提供方法选择指南并识别不同失败模式。
source: biorxiv
selection_source: fresh_fetch
motivation: 大多数单细胞扰动预测方法仅在单一数据集验证，缺乏跨方法、跨数据集的系统评估。
method: 系统评估八种方法（覆盖六种数学框架）在四个数据集上的表现，并结合CRISPRi验证与诊断分析。
result: "仅CellOracle和DDIM检测到转录因子-糖酵解方向调控，方法间结论可反相关（rho=-0.811），CRISPRi验证预测方向仅40.9%一致。"
conclusion: 方法选择显著影响结果，当前预测与实验因果方向存在鸿沟，建议采用交叉通路验证和方向感知基准测试。
---

## 摘要
大多数用于单细胞转录组学的计算扰动方法仅在单个数据集上进行了验证，其可靠性和泛化能力尚不清楚。通过对涵盖四种数据集、跨越六种数学框架的八种方法进行系统的跨方法、跨数据集基准测试，我们发现八种方法中有六种（包括广泛使用的基于VAE和张量分解的方法）未能产生可检测的转录因子（TF）到通路信号。只有CellOracle和DDIM一致地检测到TF到糖酵解的方向性调控。在PBMC单核细胞中的跨通路分析揭示了除糖酵解外生物学上一致的TF-通路关联（SPI1→糖酵解富集4.4倍，FOS→AP-1靶基因富集4.4倍），SOX9作为生物学特异性对照（无通路富集）。仅方法选择就能逆转生物学结论：DDIM和scTenifoldKnk的排序显著负相关（ρ=-0.811，p=0.027）。在K562细胞中的CRISPRi Perturb-seq验证证实TF敲低抑制糖酵解基因表达（JUN Δ=-1.72，CEBPB Δ=-1.59，SPI1 Δ=-1.57，FOS Δ=-0.70），但CellOracle预测的扰动方向与实验方向不匹配（一致性40.9%，与随机无差异），揭示了稳态相关性与因果扰动之间的根本差距。使用VAE潜在空间分析、相关性分布比较和基因-基因图分析进行的诊断分析识别出失败方法的不同失败模式：VAE潜在空间竞争（STAT3信噪比0.44 vs SPI1 4.25）、相关性噪声（TF-糖酵解|r|=0.038与背景|r|=0.047无法区分）和图非特异性（富集0.84倍）。一项受控消融实验表明，在DDIM之前添加GRN先验并未提高靶标召回率（所有TF的Δ=0），证实性能差异是多因素的。这些发现为方法选择建立了初步指导，包括跨通路验证、方向感知基准测试和最低数据要求（≥500个细胞，≥1,000个高变基因）。

## Abstract
Most in silico perturbation methods for single-cell transcriptomics have been validated only on individual datasets, leaving their reliability and generalizability unknown. Through systematic cross-method, cross-dataset benchmarking of eight methods spanning six mathematical frameworks across four datasets, we find that six of eight methods--including widely used VAE-based and tensor decomposition approaches--fail to produce detectable transcription factor (TF)-to-pathway signals. Only CellOracle and DDIM consistently detected TF-to-glycolysis directional regulation. Cross-pathway analysis in PBMC monocytes revealed biologically coherent TF-pathway associations beyond glycolysis (SPI1[-&gt;]glycolysis 4.4x enrichment, FOS[-&gt;]AP-1 targets 4.4x), with SOX9 serving as a biological specificity control (no pathway enrichment). Method choice alone could reverse biological conclusions: DDIM and scTenifoldKnk rankings were significantly anti-correlated ({rho}=-0.811, p=0.027). CRISPRi Perturb-seq validation in K562 cells confirmed TF knockdown suppresses glycolysis gene expression (JUN {delta}=-1.72, CEBPB {delta}=-1.59, SPI1 {delta}=-1.57, FOS {delta}=-0.70), but CellOracle-predicted perturbation directions did not match experimental directions (40.9% agreement, not different from chance), revealing a fundamental gap between steady-state correlation and causal perturbation. Diagnostic analyses using VAE latent space profiling, correlation distribution comparison, and gene-gene graph analysis identified distinct failure modes in unsuccessful methods: VAE latent space competition (STAT3 signal-to-noise 0.44 vs. SPI1 4.25), correlation noise (TF-glycolysis |r|=0.038 indistinguishable from background |r|=0.047), and graph non-specificity (0.84x enrichment). A controlled ablation experiment showed that adding a GRN prior to DDIM did not improve target recall (delta=0 for all TFs), confirming that performance differences are multi-factorial. These findings establish preliminary guidance for method selection, including cross-pathway validation, direction-aware benchmarking, and minimum data requirements ([&ge;]500 cells, [&ge;]1,000 HVGs).

---

## 论文详细总结（自动生成）

## 中文详细总结

### 一、论文的核心问题与整体含义（研究动机和背景）

- **研究背景**：单细胞转录组学的计算扰动预测（in silico perturbation）方法近年来快速发展，有望通过计算手段预测基因扰动后的转录组变化，从而加速疾病机制研究和药物靶点发现。
- **核心问题**：绝大多数此类方法仅在单一数据集上验证，从未在统一框架下系统比较其跨数据集、跨方法的泛化能力和可靠性。方法选择是否会影响结论？哪些方法真正有效？预测结果与实验因果方向是否一致？
- **整体含义**：该论文通过大规模系统评估揭示了一个严峻事实——**决定计算扰动结果的是方法选择而非生物学本身**。同一生物学问题在不同方法下可能得出完全相反（甚至负相关）的结论，这对此领域的可信度和应用前景提出了根本性挑战。

### 二、论文提出的方法论（核心思想、技术细节、算法流程）

- **核心思想**：建立统一的基准测试框架——在同一数据集上运行多种方法，以"转录因子（TF）→通路（如糖酵解）"的方向性调控信号为统一检验指标，并通过CRISPRi实验验证预测方向，从而区分方法的真实效能。
- **覆盖的六种数学框架**：
  - **基于VAE（变分自编码器）的方法**：利用潜在空间表征细胞状态并推断扰动效应。
  - **基于张量分解的方法**：将基因-细胞-扰动关系分解为张量因子。
  - **基于GRN（基因调控网络）的方法**：如CellOracle，利用调控网络推断扰动的影响传播。
  - **基于扩散模型的方法**：如DDIM，通过逆向扩散过程生成扰动后状态。
  - **基于图网络的方法**：利用基因-基因图结构传播扰动信号。
  - **基于回归/统计相关的方法**：利用相关性或回归系数推断因果关系。
- **八种具体方法（涵盖上述框架）**：
  - **CellOracle**：基于GRN的图扩散方法，利用转录因子结合位点构建调控网络，模拟TF扰动的下游信号传播。
  - **DDIM**（Denoising Diffusion Implicit Models）：扩散模型，生成扰动后的基因表达状态。
  - **两种基于VAE的方法**：通过编码器-解码器框架学习表达潜空间，通过扰动潜变量预测表达变化。
  - **基于张量分解的方法**（如scTenifoldKnk）：利用张量/Tucker分解构建基因调控网络并推断敲除效应。
  - 其余方法涉及图网络、统计相关等不同数学框架。
- **诊断分析技术路径**：
  - **VAE潜在空间剖面分析**：检查TF在潜空间中的信噪比（signal-to-noise ratio），发现有效TF（SPI1信噪比4.25）与无效TF（STAT3信噪比0.44）之间的显著差异。
  - **相关性分布对比**：将TF-糖酵解基因的相关系数分布与背景相关系数分布对比，评估相关性噪声水平。
  - **基因-基因图分析**：评估图传播的特异性（富集倍数是否显著高于1）。
- **受控消融实验**：在DDIM之前添加GRN先验，检验先验信息是否能提升靶标召回率——结果所有TF的Δ=0，证明性能差异是多因素共同作用而非单一因素。

### 三、实验设计（数据集、Benchmark、对比方法）

- **数据集**：共四个数据集：
  - **PBMC单核细胞数据**：用于跨通路分析，验证糖酵解以外TF-通路关联（如SPI1→糖酵解、FOS→AP-1靶基因）。
  - **K562细胞CRISPRi Perturb-seq数据**：用于实验验证——真实TF敲低后测量糖酵解基因表达变化，与计算预测方向进行对比。
  - 另外两个数据集未在摘要中详细说明，但覆盖不同组织/细胞类型，用于交叉验证。
- **Benchmark设定**：以"TF→糖酵解通路"的方向性调控信号作为统一检验标准，即以已知的生物学调控关系（如SPI1调控糖酵解基因）作为金标准，检验各方法能否恢复这些已知关系。
- **对比方法**：共八种方法，覆盖六种数学框架（VAE、张量分解、GRN、扩散模型、图网络、统计回归），包括广泛使用的VAE-based方法和张量分解方法。

### 四、资源与算力

- **论文中未明确报告**：未提及具体的GPU型号、GPU数量、训练时长、显存消耗等计算资源信息。
- **可推断的情况**：鉴于使用四个中等规模单细胞数据集（最低要求≥500细胞、≥1,000高变基因），计算负担中等，推断可能在单张/少量GPU上即可完成，但具体信息不可得。
- **建议**：学术论文应报告训练时长和硬件配置以支持可重复性，这一缺失是本次评估透明性的小遗憾。

### 五、实验数量与充分性（是否充分、客观、公平）

- **主要实验组**：
  - **主基准实验**：8种方法 × 4个数据集 = 32个方法-数据集组合。
  - **跨通路分析**：在PBMC中验证糖酵解之外的TF-通路关联（SPI1→糖酵解4.4倍富集、FOS→AP-1靶基因4.4倍富集、SOX9阴性对照无富集）。
  - **CRISPRi验证**：K562细胞中真实TF敲低（JUN、CEBPB、SPI1、FOS）的糖酵解基因表达测量，与CellOracle预测方向对比。
  - **诊断实验**：VAE潜在空间信噪比分析、相关性分布比较、基因-基因图特异性分析。
  - **受控消融实验**：在DDIM上添加GRN先验，检验靶标召回率变化。
  - **方法间排序相关性分析**：DDIM与scTenifoldKnk的相关性（ρ=-0.811）。
- **充分性评估**：
  - **优点**：跨方法、跨数据集、多维度（检测、方向、机制）的系统设计，在同类基准测试研究中鲜有如此规模。CRISPRi验证将计算预测与真实实验因果性对照，是极强的验证设计。
  - **不足**：
    - CRISPRi验证仅在K562细胞、4个TF中进行，样本量偏小，结果可能受细胞类型特异性影响。
    - 四种数据集的具体组织类型和细胞数量未完全公开，可能限制泛化性判断。
    - 八种方法的超参数调优是否同等充分未明确说明："公平性"可能存在争议（某些方法可能未达到最优性能）。
    - 仅一个通路（糖酵解）作为主要交叉验证指标，糖酵解的特异性可能使某些方法天然占优或处劣。

### 六、论文的主要结论与发现

1. **六种方法失败，仅两种有效**：八种方法中有六种（包括广泛使用的VAE-based和张量分解方法）无法检测到可重复的TF→通路信号；只有**CellOracle**和**DDIM**能一致检测到TF到糖酵解的方向性调控。
2. **方法选择可逆转生物学结论**：DDIM与scTenifoldKnk的基因排序显著负相关（Spearman ρ=-0.811，p=0.027），意味着同一生物学问题用不同方法得到完全相反的结论。
3. **跨通路一致性仅限于有效方法**：CellOracle/DDIM在PBMC中检测到的TF-通路关联具有生物学一致性（SPI1→糖酵解4.4倍富集、FOS→AP-1靶基因4.4倍富集），阴性对照SOX9无富集。
4. **关键鸿沟：稳态相关 ≠ 因果扰动**：CRISPRi实验证实TF敲低确实抑制糖酵解基因表达（JUN Δ=-1.72、CEBPB Δ=-1.59、SPI1 Δ=-1.57、FOS Δ=-0.70），但CellOracle预测方向与实际实验方向的一致性仅**40.9%**，与随机猜测无异——这揭示基于稳态相关性构建的方法无法预测真实因果扰动方向。
5. **失败方法具有不同的失败模式**：
   - VAE潜空间竞争：STAT3信噪比0.44 vs SPI1信噪比4.25，弱信号TF被强信号TF淹没。
   - 相关性噪声：TF-糖酵解|r|=0.038与背景|r|=0.047不可区分，信号湮没于噪声中。
   - 图非特异性：富集仅0.84倍（<1），信号传播无靶向性。
6. **性能差异是多因素共同作用**：消融实验显示在DDIM前添加GRN先验对靶标召回率无改善，说明方法间差异不能简单归因于是否使用了GRN先验等信息。

### 七、优点（方法和实验设计的亮点）

- **系统性和全面性**：首次在统一框架下对八种方法、六种数学框架、四个数据集进行系统评估，是目前单细胞扰动预测领域最全面的基准测试之一。
- **实验因果验证**：引入CRISPRi Perturb-seq实验数据作为金标准，将计算预测与真实实验扰动直接对比——这是本领域稀缺且高价值的验证方式。
- **诊断分析深入**：不止于"谁好谁坏"的排名，而是通过VAE潜空间剖面、相关性分布对比、图特异性分析等诊断手段，揭示失败方法的深层机制，为后续方法改进提供了方向。
- **消极结果的价值**：明确指出广泛使用的VAE和张量分解方法在此任务中失效，以及稳态相关与因果扰动的不可调和差距——这类结论对领域极有价值。
- **实用指南输出**：给出了具体建议，包括跨通路验证、方向感知基准测试和最低数据要求（≥500细胞、≥1,000高变基因），具有实际操作指导意义。

### 八、不足与局限

- **验证覆盖有限**：CRISPRi验证仅限K562细胞系和4个TF，所有基因敲低均显示为抑制作用，缺乏激活类扰动验证，方向一致性评估可能受限于单一效应模式。
- **通路偏窄**：以糖酵解为唯一核心检验通路，糖酵解基因的表达动态、调控密度可能不同于其他通路，可能导致各方法在此特定通路上的表现不等于全局表现。
- **方法调优公平性存疑**：八种方法的超参数是否经过同等程度的调优未说明。某些方法可能因调优不足而被低估，或反之。
- **资源报告缺失**：未报告GPU型号、数量、训练时长，降低可重复性和成本评估能力。
- **数据集细节不完整**：四个数据集的组织来源、细胞数量、处理流程等信息在摘要层面呈现不足。
- **预印本局限**：该论文发表在bioRxiv预印本服务器，尚未经过同行评审，结论需待正式发表后的审阅确认。
- **最小数据阈值缺乏推导依据**：≥500细胞、≥1,000高变基因的要求是如何推导出的，在摘要中未展示支持证据。
- **方法选择指南仍属初步**：作者自己也承认仅是初步指导，需要在更多数据集、更多扰动类型上验证。

---

（完）
