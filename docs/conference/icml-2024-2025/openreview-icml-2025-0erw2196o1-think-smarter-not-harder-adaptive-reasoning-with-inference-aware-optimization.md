---
title: "Think Smarter not Harder: Adaptive Reasoning with Inference Aware Optimization"
title_zh: 更聪明而非更费力：基于推理感知优化的自适应推理
authors: "Zishun Yu, Tengyu Xu, Di Jin, Karthik Abinav Sankararaman, Yun He, Wenxuan Zhou, Zhouhao Zeng, Eryk Helenowski, Chen Zhu, Sinong Wang, Hao Ma, Han Fang"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=0ERw2196o1"
tags: ["query:mm-cot"]
score: 6.0
evidence: 自适应控制推理链长度，优化长链推理
tldr: 当前长链推理模型在处理简单问题时也会生成冗长的推理步骤，造成不必要的计算开销。本文提出推理预算约束策略优化(IBPO)，将推理预算建模为效用最大化问题，使模型能自适应调整推理长度。实验表明，IBPO在不牺牲准确率的前提下显著缩短了推理链。该方法为高效推理提供了新思路。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-0erw2196o1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1771, \"height\": 1037, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-0erw2196o1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 720, \"height\": 295, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-0erw2196o1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 795, \"height\": 496, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-0erw2196o1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1752, \"height\": 700, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-0erw2196o1/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1563, \"height\": 647, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-0erw2196o1/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 845, \"height\": 622, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-0erw2196o1/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1765, \"height\": 463, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-0erw2196o1/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1775, \"height\": 668, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-0erw2196o1/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1425, \"height\": 691, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-0erw2196o1/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 704, \"height\": 453, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-0erw2196o1/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 863, \"height\": 341, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-0erw2196o1/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 870, \"height\": 690, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-0erw2196o1/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 885, \"height\": 675, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-0erw2196o1/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 858, \"height\": 1694, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-0erw2196o1/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 807, \"height\": 355, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-0erw2196o1/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1760, \"height\": 303, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-0erw2196o1/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 851, \"height\": 227, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-0erw2196o1/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 842, \"height\": 224, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-0erw2196o1/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 938, \"height\": 785, \"label\": \"Table\"}]"
motivation: 长链推理模型在简单问题上生成不必要的长链条，效率低下。
method: 提出IBPO算法，通过推理预算约束的效用最大化优化推理长度。
result: 模型在保持准确率的同时显著缩短了推理链长度。
conclusion: 自适应推理长度是提升推理效率的有效途径。
---

## Abstract
Solving mathematics problems has been an intriguing capability of large language models, and many efforts have been made to improve reasoning by extending reasoning length, such as through self-correction and extensive long chain-of-thoughts. While promising in problem-solving, advanced long reasoning chain models exhibit an undesired single-modal behavior, where trivial questions require unnecessarily tedious long chains of thought. In this work, we propose a way to allow models to be aware of inference budgets by formulating it as utility maximization with respect to an inference budget constraint, hence naming our algorithm Inference Budget-Constrained Policy Optimization (IBPO). In a nutshell, models fine-tuned through IBPO learn to ``understand'' the difficulty of queries and allocate inference budgets to harder ones. With different inference budgets, our best models are able to have a $4.14$\% and $5.74$\% absolute improvement ($8.08$\% and $11.2$\% relative improvement) on MATH500 using $2.16$x and $4.32$x inference budgets respectively, relative to LLaMA3.1 8B Instruct. These improvements are approximately $2$x those of self-consistency under the same budgets.

---

## 论文详细总结（自动生成）

# 论文总结：《Think Smarter not Harder: Adaptive Reasoning with Inference Aware Optimization》

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：当前长链推理模型（如 OpenAI-o1、DeepSeek-R1）在解决数学问题时，即使对简单问题也会生成冗长的推理链条，导致不必要的计算开销和碳排放。这种“单模态行为”浪费了推理资源。
- **背景**：已有研究（如 chain-of-thought、self-correction、multi-turn reasoning）表明增加推理步长能提升准确性，但未考虑按问题难度自适应分配推理预算。
- **目标**：使模型能够根据问题难度自动调整推理长度，在保持或提升准确率的同时，降低推理成本。论文将问题形式化为在推理预算约束下的效用最大化问题。

## 2. 方法论：核心思想、关键技术细节与算法流程
- **核心思想**：将推理预算视为一种资源，通过约束优化使模型对不同难度的问题分配不同长度的推理过程。具体地，将响应空间划分为两组：标准长度 CoT 响应（低预算组 G⁰）和扩展长度响应（高预算组 G⁺），并限制扩展响应的生成比例（预算 q⁺）。
- **技术框架**：基于约束强化学习（Constrained RL），提出 Inference Budget-Constrained Policy Optimization (IBPO)。核心步骤：
  - **非参空间求解**：在非参数策略空间（表格表示）中求解带约束的优化问题，得到最优分配权重 π̂*。
  - **投影到参数空间**：通过加权监督微调（weighted SFT），将 π̂* 投影到参数化策略 π_θ 上（最小化 KL 散度）。
  - **实用更新**：使用 stop-gradient 技巧避免通过 arg max 微分，最终更新为加权交叉熵损失。权重由每轮求解的整数线性规划（ILP）确定。
- **具体实现**：基于 CGPO（Constraint Generative Policy Optimization）框架，定义奖励为正确性；采用 margin reward（组间期望奖励差异）作为优化目标，以鼓励模型对难题选择扩展响应，简单题选择标准响应。
- **示例说明**：表 2 展示了 ILP 如何根据 margin 和预算约束自动选择接受哪种响应。

## 3. 实验设计：数据集、benchmark、对比方法
- **数据集**：
  - **训练**：使用 MATH 训练集（约 10k 问题）和 SDPO 数据集（Lai et al., 2024）的黄金标准响应（SCoT 格式）。
  - **测试**：MATH500（Lightman et al., 2023 的子集，500 道题）。
- **基准与对比**：
  - 基础模型：LLaMA3.1 8B Instruct。
  - 对比方法：SFT 基线（SV-SFT、ASV-SFT）、自修正方法（Self-Refine、STaR、S³C、RISE、SCoRe 等）、自一致性（majority vote / self-consistency）。
  - 包含 SFT 和 RL 两类基线，以及本文提出的 ASV-IuB（不同预算 q⁺ = 25%, 50%, 75%）。
- **评估指标**：
  - 主要指标：pass@1 准确率。
  - 效率指标：平均 trial 数 / 响应数，以及性能-预算效率（图 2a/b）。

## 4. 资源与算力
- **算力说明**：论文未明确给出总训练 GPU 小时数，但提到了：
  - 实验使用 **NVIDIA A100-80G** GPU。
  - 超参数表（附录 F）显示：RL 训练（Setup 2.2）使用 **8 节点**，batch size 4 per node，共 240 步；SFT 使用 4 节点。
  - 求解器（SciPy ILP）每轮平均耗时 <0.1 秒，计计算开销可忽略。
- **总体算力规模中等**，但未提供完整碳排放或精确时长。

## 5. 实验数量与充分性
- **实验组数**：
  - 主要实验：3 种预算配置（25%、50%、75%），每种重复多次。
  - 消融与对比：SFT 版本（ASV-SFT-α）、SV baseline、自一致性 baseline、多种自修正基线（表 3）。
  - 附加分析：训练曲线（图 2c、图 7）、预算分配按难度分布（图 2e/f）。
- **充分性评价**：
  - **优点**：全面覆盖了 SFT 和 RL 方法，对比了多个 state-of-the-art 自修正方法；展示了训练/测试集约束遵循情况；分析了效率边界（图 2a/b）。
  - **不足**：仅使用 MATH 数据集，未在更多领域（如代码、科学推理）验证；规模较小（10k prompts），可能影响分布外泛化；未与最新超长推理模型（如 GPT-o1）直接对比（但作者声明非重点）。

## 6. 主要结论与发现
- **IBPO 有效提升效率**：在 MATH500 上，ASV-IuB 在预算为 2.16× 时（q⁺=50%）提升 4.14% 绝对准确率（8.08% 相对提升），在 4.32× 时（q⁺=75%）提升 5.74%（11.2% 相对提升）。收益约为等预算下 self-consistency 的两倍。
- **自适应分配能力**：模型自动将更多扩展预算分配给难度更高的问题（图 2e/f），对简单问题使用标准 CoT。
- **约束遵循**：训练集上预算约束几乎完全遵守（图 2c），测试集上近似遵守（图 2d）。
- **SFT 不足以实现自适应**：ASV-SFT 效率低于理论边界，说明 SFT 不能内在优化资源分配，RL 是必要的。
- **SV 构造有效**：作为 G⁺ 构造的 Sequential Voting 基线，其扩展效率与自一致性相当（图 5b）。

## 7. 优点
- **方法简洁且具通用性**：从优化视角出发，最终归结为加权 SFT，与现有流行方法（RAFT、RFT）形式统一，易于扩展至其他约束类型（如公平性、专家平衡）。
- **无需额外奖励模型**：仅使用正确性（字符串匹配）作为奖励，降低实现复杂度。
- **可解释性**：ILP 的求解结果直接显示每个样本被接受或拒绝，以及预算分配情况，便于分析。
- **效率提升显著**：在几乎不降准确率的情况下，大幅减少不必要的长推理，有利于部署成本和碳足迹。

## 8. 不足与局限
- **实验覆盖有限**：仅测试数学推理，未涉及代码、科学推理等；仅使用 8B 模型，未验证更大规模。
- **分布偏移问题**：在 q⁺=75% 时测试集上几乎全选扩展响应（图 2d），导致效率无改进，说明训练集规模小可能引起过拟合。
- **构造的 G⁺ 并非最优**：Sequential Voting 仅为示意性构造，实际应用中可能需要更高效的长推理方法（如真正的超长 CoT 模型）。
- **批优化与方差**：小批量 ILP 可能带来较大方差，需通过样本累积（batch accumulation）缓解，但论文仅提出概念未深入验证。
- **可扩展性**：ILP 求解虽快，但若分组数增加或变量规模扩大，求解时间可能成为瓶颈。
- **理论分析较弱**：论文更多是算法推导和实证，未提供 regret 或收敛性证明。

（完）
