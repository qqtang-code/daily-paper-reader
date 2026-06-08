---
title: "ShorterBetter: Guiding Reasoning Models to Find Optimal Inference Length for Efficient Reasoning"
title_zh: ShorterBetter：引导推理模型找到最优推理长度以实现高效推理
authors: "Jingyang Yi, Justin Wang, Sida Li"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=MJvwM5dBZM"
tags: ["query:mm-cot"]
score: 5.0
evidence: 基于强化学习的推理链长度优化以减少过度思考
tldr: 长CoT虽然提升推理能力，但导致过度思考与冗余。本文提出ShorterBetter强化学习方法，让推理模型自动学习最优推理长度（SOL），无需人工标注。通过定义样本最优长度（SOL）作为最短正确响应的长度，并以此作为奖励信号，训练模型在保持准确率的同时缩短推理链。实验表明该方法显著减少推理步骤。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-mjvwm5dbzm/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1440, \"height\": 750, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mjvwm5dbzm/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1506, \"height\": 477, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mjvwm5dbzm/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1447, \"height\": 438, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mjvwm5dbzm/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 866, \"height\": 414, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mjvwm5dbzm/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1007, \"height\": 470, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mjvwm5dbzm/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1417, \"height\": 917, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mjvwm5dbzm/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1008, \"height\": 500, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mjvwm5dbzm/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1435, \"height\": 422, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mjvwm5dbzm/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1448, \"height\": 639, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-mjvwm5dbzm/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1444, \"height\": 498, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mjvwm5dbzm/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1228, \"height\": 313, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mjvwm5dbzm/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1278, \"height\": 207, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mjvwm5dbzm/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1445, \"height\": 206, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mjvwm5dbzm/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 665, \"height\": 459, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mjvwm5dbzm/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 856, \"height\": 517, \"label\": \"Table\"}]"
motivation: 长CoT推理存在过度思考问题，需要自动优化推理长度以提高效率。
method: 定义样本最优长度（SOL），基于RL训练模型自主生成该长度的CoT。
result: 在多个推理任务上验证了方法能有效缩短推理链而不牺牲准确率。
conclusion: 为推理模型长度优化提供了自动化方案，有助于实际部署。
---

## Abstract
Recent models such as OpenAI o1 and DeepSeek-R1 have demonstrated strong performance on reasoning-intensive tasks by generating extended Chain-of-Thought (CoT) traces. While longer reasoning helps with thorough exploration of solution paths for complex problems, it also often leads to inefficient and redundant outputs—a phenomenon commonly described as $\textit{overthinking}$.  In this paper, we propose $\texttt{ShorterBetter}$, a simple yet effective reinforcement learning method that enables reasoning models to learn their own optimal CoT lengths without manual supervision. We define the $\textit{Sample Optimal Length}$ (SOL) as the length of the shortest correct response among multiple generations, which serves as a dynamic reward signal to guide the model toward efficient reasoning. Applied to DeepSeek-Distill-Qwen-1.5B/7B as base models, $\texttt{ShorterBetter}$ achieves 50\%-80\% reduction in output lengths in both in-domain and out-of-domain reasoning tasks while maintaining accuracy. Our reasoning trace analysis shows that $\texttt{ShorterBetter}$ refines the structure of the reasoning traces by reducing unnecessary repetition, excessive self-verification, and over-exploration of alternatives.

---

## 论文详细总结（自动生成）

# 论文总结：ShorterBetter: Guiding Reasoning Models to Find Optimal Inference Length for Efficient Reasoning

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：大规模语言模型（如 OpenAI o1、DeepSeek-R1）通过生成长链思维（Chain-of-Thought, CoT）提升了推理能力，但过长的推理轨迹往往包含大量冗余、重复、自我验证和过度探索，导致计算效率低下，这种现象称为“过度思考”（overthinking）。
- **背景**：现有方法如 L1、O1-Pruner 等通过人工设定长度预算或与参考模型对比来强制缩短推理，但缺乏自适应性和灵活性。
- **研究目标**：提出一种无需人工监督、能自动引导推理模型找到“最优推理长度”（Optimal Length, OL）的方法，在保持或提升准确率的前提下大幅减少输出长度。

## 2. 方法论

### 2.1 核心思想
- **定义样本最优长度（Sample Optimal Length, SOL）**：对于同一个问题，生成多个候选响应，将其中最短的正确响应的长度作为该问题的 SOL。若组内无正确响应，则取平均长度作为中性基线。
- **奖励函数设计**：  
  \[
  r(y_j) = \alpha \cdot \mathbb{I}(y_j = y^*) - \beta \cdot |\ell(y_j) - \ell_{\text{SOL}}(G(x_i))|
  \]  
  其中 \(\alpha\) 调控正确性奖励权重，\(\beta\) 调控长度惩罚强度。该奖励同时鼓励生成正确且接近 SOL 的响应。

### 2.2 关键技术细节
- 使用 **Group Relative Policy Optimization (GRPO)** 进行策略优化：在每组 \(n\) 个样本内计算归一化优势，并通过裁剪的 PPO 目标与 KL 散度约束更新策略。
- **自适应特性**：SOL 完全由当前模型的采样结果动态确定，无需人工给定长度阈值；能反映问题难度和模型能力的变化。
- **对失败案例的处理**：当组内无正确响应时，以平均长度作为 SOL，避免模型偏向“欠思考”或“过度思考”。

### 2.3 算法流程（文字说明）
1. 对每个 prompt 生成 \(n\) 个 rollouts；
2. 使用验证器判定每个响应的正确性；
3. 计算组内的 SOL；
4. 根据公式计算每个响应的奖励；
5. 在组内归一化奖励得到优势值；
6. 计算 GRPO 损失并更新策略参数。

## 3. 实验设计

- **训练数据集**：DeepScaleR-preview（40K 数学问题），涵盖 AIME、AMC、Omni-MATH、Still 等。
- **评估基准（Benchmark）**：
  - 域内任务（in-domain）：AIME、Olympiad-Bench、AMC、Minerva（数学推理）。
  - 域外任务（out-of-domain）：MathQA、MMLU、BBH、LiveCodeBench、MBPP、HumanEval（包括数学、常识、编码等）。
- **对比方法**：
  - DeepSeek-R1-Distill-Qwen-1.5B/7B（基座模型）；
  - Qwen2.5-1.5B/7B-Instruct（非推理模型）；
  - Training Efficient（Arora & Zanette, 2025）；
  - O1-Pruner（Luo et al., 2025a，仅 7B 版本）。
- **评价指标**：准确率、平均输出长度、Accuracy-Efficiency (AE) Score（综合长度压缩与准确率保持的复合指标）。
- **消融实验**：
  - 去掉正确性奖励、始终以最短响应为长度目标；
  - 保留正确性奖励但始终以最短响应为目标；
  - 无正确响应时以最短响应代替平均长度；
  - 完全去掉正确性奖励项（\(\alpha=0\)）观察 SOL 自身作用。

## 4. 资源与算力

- **ShorterBetter-1.5B**：使用 4 块 A100 GPU，训练约 16 小时。
- **ShorterBetter-7B**：使用 8 块 A100 GPU，训练不到 12 小时。
- **推理阶段**：设置最大输出长度为 16K tokens（1.5B 训练时限制 6K，7B 限制 5K，但均值很快低于限制）。

## 5. 实验数量与充分性

- **多组实验覆盖**：
  - 在两个模型规模（1.5B / 7B）上训练；
  - 在 8 个以上不同任务上评估（域内 4 个 + 域外 7 个）；
  - 对比 4 种基线方法；
  - 进行 4 组消融实验（含不同 \(\alpha\) 值和奖励设计变体）；
  - 对 7B 模型还对比了 O1-Pruner。
- **充分性与公平性**：
  - 所有基准测试均采用相同评估设置（temperature=0.9，单次生成）。
  - 域外任务完全不在训练数据中，确保泛化能力测试的公平性。
  - 使用 LLM-as-judge 进行推理结构分析，并通过人工验证 2064 条语句（94.23% 一致性），增强分析可靠性。
  - 实验设计系统、结果清晰，但未报告误差条（受计算成本限制），可能影响统计显著性判断。

## 6. 主要结论与发现

- **长度大幅缩减**：1.5B 模型在域内任务平均缩短 77.6%~79.2%，域外缩短 75.5%~77.0%。7B 模型域内缩短约 62.1%，域外缩短约 62.3%。
- **准确率保持甚至提升**：1.5B 域内准确率提升约 2.5%~3.2%，域外略有下降（-0.8%~-1.6%）；7B 域内准确率提升 7.1%，域外基本持平（-0.48%）。
- **推理结构优化**：
  - 模型在首次得到正确答案后，后续冗余输出比例显著降低（15%~20%）。
  - 关键推理（Pivotal Reasoning）和有效计算（Productive Elaboration）比例上升，非实质性语句、自我验证和探索替代方案比例下降。
- **消融验证**：仅用最短响应长度作为目标会导致训练崩溃；SOL 机制本身已隐含正确性信号，但显式正确性奖励对稳定性能至关重要。

## 7. 优点

- **无需人工标注**：SOL 完全数据驱动，自动适应问题难度和模型能力，无需手动设置长度预算。
- **简洁有效**：方法核心定义清晰，奖励函数简单，与 GRPO 结合自然。
- **强泛化能力**：在完全不参与训练的域外任务上同样实现大幅长度缩减，且性能损失极小。
- **推理结构分析新颖**：引入 LLM-as-judge 自动化分析推理内容分类，并辅以人类验证，为理解模型行为提供了可解释的工具。

## 8. 不足与局限

- **适用范围限制**：当前方法主要针对答案可验证的任务（数学、代码），对于开放生成任务（如创意写作）的应用尚处理论层面，未实验验证。
- **模型规模局限**：仅在 1.5B 和 7B 模型上测试，更大规模模型（如 70B+）上的效果和训练稳定性未知。
- **训练稳定性风险**：消融实验显示错误的奖励设计（如直接使用最短长度）会导致训练崩溃，说明超参数（特别是 \(\alpha\)）需要谨慎调整。
- **未评估噪声与误差传播**：论文未讨论在更长推理链中模型可能因压缩而引入新错误的风险；仅基于整体准确率表明无显著下降。
- **缺乏统计置信度**：未报告误差条或多次运行的结果，单次训练评估可能隐藏随机性影响。
- **计算资源需求**：虽然比蒸馏模型训练更高效，但 RL 训练仍需多 GPU 资源，对资源紧张团队不友好。

（完）
