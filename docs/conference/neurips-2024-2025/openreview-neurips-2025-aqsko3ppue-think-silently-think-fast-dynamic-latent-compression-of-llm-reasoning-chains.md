---
title: "Think Silently, Think Fast: Dynamic Latent Compression of LLM Reasoning Chains"
title_zh: 无声思考，快速思考：LLM推理链的动态潜在压缩
authors: "Wenhui Tan, Jiaze Li, Jianzhong Ju, Zhenbo Luo, Ruihua Song, Jian Luan"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=AQsko3PPUe"
tags: ["query:mm-cot"]
score: 8.0
evidence: 通过潜在空间动态压缩推理链提高效率
tldr: 现有基于链式推理(CoT)的大型语言模型在生成详细推理步骤时计算成本高昂。本文提出CoLaR框架，通过两阶段训练在潜在空间动态压缩推理过程，将连续token的嵌入合并，并训练潜在头预测后续压缩嵌入。该方法在保持推理质量的同时显著降低计算开销，为高效推理提供了新思路。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-aqsko3ppue/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1450, \"height\": 357, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aqsko3ppue/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1449, \"height\": 429, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aqsko3ppue/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1439, \"height\": 603, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aqsko3ppue/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 660, \"height\": 390, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aqsko3ppue/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 660, \"height\": 389, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aqsko3ppue/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 956, \"height\": 559, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aqsko3ppue/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1020, \"height\": 382, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aqsko3ppue/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 689, \"height\": 406, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-aqsko3ppue/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1496, \"height\": 518, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aqsko3ppue/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1495, \"height\": 335, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aqsko3ppue/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1520, \"height\": 225, \"label\": \"Table\"}]"
motivation: 标准CoT推理链因逐token解码导致计算效率低下，限制了大规模部署。
method: 提出CoLaR框架，通过辅助下一个压缩嵌入预测目标，动态合并连续token嵌入并训练潜在头，实现推理过程的潜在空间压缩。
result: 在多个推理基准上，CoLaR在压缩比高达4倍时仍保持与原始CoT相当的准确率，同时推理速度显著提升。
conclusion: 动态潜在压缩是一种有效的推理链加速范式，可泛化至不同LLM架构。
---

## Abstract
Large Language Models (LLMs) achieve superior performance through Chain-of-Thought (CoT) reasoning, but these token-level reasoning chains are computationally expensive and inefficient.
In this paper, we introduce Compressed Latent Reasoning (CoLaR), a novel framework that dynamically compresses reasoning processes in latent space through a two-stage training approach.
First, during supervised fine-tuning, CoLaR extends beyond next-token prediction by incorporating an auxiliary next compressed embedding prediction objective. This process merges embeddings of consecutive tokens using a compression factor $c$ randomly sampled from a predefined range, and trains a specialized latent head to predict distributions of subsequent compressed embeddings. Second, we enhance CoLaR through reinforcement learning (RL) that leverages the latent head's non-deterministic nature to explore diverse reasoning paths and exploit more compact ones.
This approach enables CoLaR to: i) **perform reasoning at a dense latent level** (i.e., silently), substantially reducing reasoning chain length, and ii) **dynamically adjust reasoning speed** at inference time by simply prompting the desired compression factor.
Extensive experiments across four mathematical reasoning datasets demonstrate that CoLaR achieves 14.1% higher accuracy than latent-based baseline methods at comparable compression ratios, and reduces reasoning chain length by 53.3% with only 4.8% performance degradation compared to explicit CoT method. Moreover, when applied to more challenging mathematical reasoning tasks, our RL-enhanced CoLaR demonstrates performance gains of up to 5.4% while dramatically reducing latent reasoning chain length by 82.8%.
The code and models will be released upon acceptance.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 核心问题与整体含义（研究动机和背景）
大型语言模型（LLM）通过链式推理（CoT）实现了卓越的推理能力，但生成详细的逐token推理链导致高昂的计算成本，严重制约了推理效率和扩展性。现有优化方法要么在稀疏的token层面进行（如跳过不重要token、缩短推理步骤），要么尝试在密度的潜在空间中进行推理。但目前潜在空间推理方法（如Coconut、CODI）存在两个关键缺陷：依赖**固定长度推理链**，以及使用**确定性潜在推理过程**，缺乏探索-利用能力。为此，本文提出**Compressed Latent Reasoning (CoLaR)**框架，通过动态压缩推理链到潜在空间，同时保持探索-利用能力，在显著降低计算开销的同时维持甚至提升推理质量。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：将原始的离散推理token序列压缩为更短的潜在变量序列，每个潜在变量整合多个推理token的语义信息；通过两阶段训练实现动态压缩推理。
- **两阶段训练流程**：
  - **阶段一：监督微调 (SFT)**
    - **动态压缩**：在每个训练步，从范围 $[1, c_{max}]$ 中随机采样压缩因子 $c$，使用**嵌入压缩模块**将连续 $c$ 个推理token的嵌入通过缩放求和（除以 $\sqrt{c}$）合并为一个压缩嵌入，保持原始分布不变。
    - **语言头监督**：除了预测最终答案token外，还从每个压缩组中随机采样一个token作为标签，训练模型预测压缩推理链对应的token，提供密集监督信号。
    - **潜在头预测**：训练一个MLP作为**潜在头**，基于当前隐藏状态预测下一个压缩嵌入的均值 $\mu_{c}^{i+1}$ 和标准差 $\sigma_{c}^{i+1}$（输出概率分布，而非确定性值）。损失函数有两种候选：
      - **负对数似然 (NLL)**：$L_{latent}(i) = \frac{(e_c^i - \hat{\mu}_c^i)^2}{2\hat{\sigma}_c^i} + \log \hat{\sigma}_c^i$
      - **Soft-MSE**：结合均方误差与熵正则化（含超参数 $\alpha$），在简单数据集上提供更平衡的探索能力。
    - 总损失：$L = L_{comp} + L_{latent}$。
  - **阶段二：强化学习 (RL)**
    - 利用潜在头的不确定性，对同一问题采样 $G$ 个输出（每个输出包含潜在推理链和答案）。
    - 使用**GRPO**算法优化：基于组归一化奖励（正确为1，否则为0），鼓励正确且更紧凑的推理路径，惩罚错误或过长的路径。
    - 特别地，奖励平均到每个token/latent，促使模型在早期探索更长的路径，后期利用更短的路径。
- **推理阶段**：通过提示指定压缩因子 $c$，模型自动以潜在空间自回归推理，由潜在头预测下一个潜在变量，语言头负责判断何时终止推理并生成最终答案。

## 3. 实验设计
- **数据集与场景**：
  - **主要训练/测试**：GSM8k-Aug（约385k训练样本，1k测试样本）。
  - **域外泛化**：GSM-Hard（1k）、SVAMP（1k）、MultiArith（600）。
  - **高级推理**：MATH（7.5k训练，5k测试，涵盖代数、微积分等）。
  - **额外扩展验证**：GPQA（化学、生物、物理多选问答）。
- **Benchmark/对比方法**：
  - **显式推理**：CoT（标准微调）、TokenSkip（token级跳过）。
  - **隐式/潜在推理**：iCoT（逐步移除推理步骤）、Coconut（固定6步潜在推理）、Distill（CODI自蒸馏复现）。
- **评估指标**：准确率（Acc.%）和平均推理链长度（#L），均报告五次独立运行的95%置信区间。
- **基座模型**：Llama-3.2-1B-Instruct（冻结+LoRA，LoRA α=32, r=128），以及DeepSeek-R1-Distill-Qwen-1.5B，另扩展到Llama-3.2-8B验证可扩展性。
- **初始化**：所有潜在方法均从CoT-SFT微调权重初始化，确保公平比较。

## 4. 资源与算力
- **SFT阶段**：使用8张NVIDIA A100 GPU，总batch size 256，采用分布式数据并行。
- **RL阶段**：使用单张A100 GPU，rollout batch size 8，optimizer step batch size 4，group size G=8，clip ϵ=0.2。
- **训练时长**：最多50个epoch或12小时（以先到者为准），选择验证集最优checkpoint。
- **优化器**：AdamW，SFT学习率1e-4，RL学习率1e-6，权重衰减1e-2。

## 5. 实验数量与充分性
- **主要对比实验**：在4个GSM级数据集上，对比4种基线方法（CoT、iCoT、Coconut、Distill），CoLaR以c=5和c=2两种压缩因子测试，所有结果五次运行。
- **消融实验**：4种设置（确定性潜在头、无压缩token监督、均值池化压缩、NLL损失），在c=5和c=2下全面对比。
- **RL实验**：在MATH上使用两种基座模型，比较CoLaR-DL、CoLaR-NLL、CoLaR-NLL-RL，并含“无平均奖励”消融。
- **扩展实验**：在1B/8B模型上对比TokenSkip（表3），覆盖GSM-8k、MATH-500、GPQA。
- **动态因子分析**：训练时c∈[1,5]与固定c对比（图4），以及外推至未见因子c={2,4,6}（图5）。
- **案例与层分析**：定性解释潜在链的含义，分析不同层激活差异。
- **充分性评估**：实验覆盖广泛（多个数据集、不同模型规模、多种变体），使用多次运行和置信区间，消融设计合理，对比公平（所有方法相同初始化、相同训练资源限制），**充分且客观**。

## 6. 主要结论与发现
1. **高效率压缩**：CoLaR-5相比Coconut准确率提升**14.1%**，且推理步数更少（4.57 vs 6.00）。CoLaR-2相比显式CoT仅下降4.8%准确率，但推理链长减少**53.3%**。
2. **动态压缩有效性**：训练时随机采样c可泛化到未见压缩因子，且优于单一c训练。
3. **强化学习显著提升**：在MATH上，RL后Qwen-1.5B准确率提升**5.36%**，链长减少**82.8%**；Llama-1B提升1.80%，链长减少80.6%。
4. **探索-利用平衡**：潜在头概率性质使RL能探索正确路径，并通过平均奖励机制自动选择更短有效路径。
5. **可扩展性**：从1B到8B模型，CoLaR保持压缩优势，且RL在8B上仍有效（GPQA准确率超越CoT教师37.5% vs 35.7%）。
6. **深层计算利用**：高压缩因子使深层模型更积极参与推理，有效利用计算资源。

## 7. 优点（方法或实验亮点）
- **创新性**：首次将动态压缩因子与概率潜在头结合，实现**可变长度潜在推理**，并能通过RL进行探索-利用。
- **训练策略**：两阶段设计（SFT提供良好初始化，RL进一步优化），且SFT中未使用均值池化而是缩放求和，避免分布偏移。
- **稳定性**：软MSE损失在简单数据集上平衡NLL的过随机问题；归一化潜在目标确保训练稳定性。
- **实验严谨性**：多次运行、置信区间、公平初始化、全面消融；对压缩因子泛化能力进行了系统分析。
- **实用性**：推理时只需修改提示中的压缩因子即可调节速度，无需重新训练。

## 8. 不足与局限
- **性能天花板**：除GPQA外，CoLaR整体准确率接近显式CoT但未超越，尤其在简单问题上仍有差距（GSM8k: 40.1% vs CoT 49.4%）。当前为“近似”而非“超越”。
- **压缩因子限制**：无法泛化到非整数（如c=1.5）或大于最大训练c（如c>5）的压缩因子，归因于离散token化约束。
- **依赖基座模型质量**：RL效果与基座模型能力高度相关（Qwen-1.5B远优于Llama-1B），低质量基座可能无法发挥RL潜力。
- **社会影响风险**：虽可提升LLM服务效率，但也可能放大推理偏差或被用于生成更具说服力的虚假信息，需谨慎监控下游应用。
- **实验覆盖范围**：当前主要聚焦数学推理，尚未验证在常识推理、多步问答等更广泛任务上的表现。

（完）
