---
title: LLMs Can Reason Faster Only If We Let Them
title_zh: 只要允许，大语言模型就能更快推理
authors: "Bilgehan Sel, Lifu Huang, Naren Ramakrishnan, Ruoxi Jia, Ming Jin"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=uTv5rOPZr4"
tags: ["query:mm-cot"]
score: 6.0
evidence: 缩短链式思维和算法思维中的解长度
tldr: 链式思维(CoT)在复杂多步推理中表现不足，而算法思维(AoT)虽然有效但生成过长解。本文提出AoT-O3，通过监督微调AoT风格计划并结合强化学习框架来最小化解长度。实验显示AoT-O3在缩短解长度的同时保持了规划质量。该方法为高效推理提供了平衡方案。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-utv5ropzr4/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1622, \"height\": 674, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-utv5ropzr4/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 816, \"height\": 1232, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-utv5ropzr4/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1330, \"height\": 945, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-utv5ropzr4/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 485, \"height\": 201, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-utv5ropzr4/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1796, \"height\": 650, \"label\": \"Table\"}]"
motivation: 现有CoT在复杂推理中效果有限，AoT解太长。
method: AoT-O3结合监督微调和强化学习，优化解长度。
result: AoT-O3在保持规划质量的前提下显著缩短了解长度。
conclusion: 通过强化学习可有效平衡推理长度和准确性。
---

## Abstract
Large language models (LLMs) are making inroads into classical AI problems such as automated planning, yet key shortcomings continue to hamper their integration. Chain-of-Thought (CoT) struggles in complex multi-step reasoning, and Tree-of-Thoughts requires multiple queries that increase computational overhead. Recently, Algorithm-of-Thoughts (AoT) have shown promise using in-context examples, at the cost of significantly longer solutions compared to CoT.  Aimed at bridging the solution length gap between CoT and AoT, this paper introduces AoT-O3, which combines supervised finetuning on AoT-style plans with a reinforcement learning (RL) framework designed to reduce solution length. The RL component uses a reward model that favors concise, valid solutions  while maintaining planning accuracy. Empirical evaluations indicate that AoT-O3 shortens solution length by up to 80\% compared to baseline AoT while maintaining or surpassing prior performance. These findings suggest a promising pathway for more efficient, scalable LLM-based planning.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **动机**：大语言模型（LLMs）在自动规划等经典AI任务中表现不足。链式思维（CoT）在复杂多步推理中效果有限，而树状思维（ToT）虽能探索多条路径，但需多次查询，计算开销大。算法思维（AoT）通过单次查询和上下文示例表现出色，但生成的解显著长于CoT，导致高计算成本和环境负担。核心问题是如何在保持AoT性能的同时大幅缩减解长度，从而提高LLM规划的效率与可扩展性。
- **背景**：现有方法如CoT、Least-to-Most、Self-Consistency等未能显著提升规划能力。AoT引入了搜索轨迹，但存在“模仿而非真正推理”的冗余步骤。本文旨在通过强化学习（RL）引导模型生成既正确又简洁的解，桥接CoT与AoT之间的长度差距。

## 2. 方法论：核心思想、关键技术细节与算法流程

- **核心思想**：AoT-O3（命名源自C++最高编译优化级别）结合监督微调（SFT）和强化学习（RL），使用一个非LLM的奖励模型，同时优化解的准确性和简洁性（解长度）。
- **关键技术细节**：
  - **SFT阶段**：训练模型学习AoT风格的规划（状态→思考/过渡→下一状态）。使用随机但有效的搜索路径（包含探索与回溯）构建训练数据，避免依赖人类直觉。损失为标准的交叉熵损失（教师强制）。
  - **奖励模型**（实际为值模型，因每个过渡步骤视为一个动作）：
    - 对正确解：奖励 = max(1 - nα, β) + κ·1(Ti∈y*)，其中n为步数，α为步数惩罚因子，β为下限（如-0.5），κ为正确路径激励（针对包含关键过渡的步骤）。
    - 对错误解：奖励 = -1。
    - 该奖励可直接计算，无需训练额外奖励模型，降低开销，且避免模型通过延长解来获取更多总和奖励（因仅在正确解上累加扣分）。
  - **RL训练阶段**：使用REINFORCE leave-one-out（RLOO）算法，最大化期望奖励。引入KL散度惩罚约束策略与SFT模型的距离，防止性能退化。训练过程采样问题并生成完整解，根据奖励梯度更新模型。
- **算法流程**（文字说明）：
  1. 对每个训练问题，先用随机搜索生成有效解路径（包含探索步骤和最终正确路径）。
  2. 进行SFT，让模型学会AoT格式的规划。
  3. 固定SFT模型作为参考，使用RLOO在同样数据上优化奖励函数：每步生成4个样本，计算奖励，通过leave-one-out基线估计优势，更新策略参数。
  4. 推理时直接使用模型生成解，无需额外步骤。

## 3. 实验设计

- **数据集/场景**：
  - **Game of X**（Game of 24的广义变体）：随机5个数，用加减乘除构造表达式达到目标值，搜索空间更大。
  - **N-Puzzle**：经典8数码拼图，3×3网格，初始状态经80-120步随机移动生成。
  - **Word Ladder**：从一个英文单词变换到另一个，每次改一个字母，中间步骤需为有效单词。使用NLTK基础词集。
- **基准对比**：与CoT-SFT（链式思维+监督微调）和AoT-SFT（算法思维+监督微调）对比。
- **评估指标**：准确率（%）和平均解长度（步数）。
- **实验数量**：在3种模型（不同规模）、3个基准上各测试了带/不带κ的AoT-O3，共3×3×2 ≈18组主要结果，加上表1对随机示例在微调vs提示下的效果分析，图2对解长度影响的分析，以及消融实验（κ=0 vs κ>0）。总体实验较充分。

## 4. 资源与算力

- **文中明确说明**：
  - 模型：Gemma2-2B、Llama3-1B、Llama3-3B（参数规模1B~3B），使用bfloat16精度。
  - 硬件：8× NVIDIA H100 GPU（80GB显存）。
  - 训练：SFT阶段500步，批大小128，学习率1e-5；RL阶段50步，批大小32，每问题4样本，学习率1e-6。使用DeepSpeed进行多GPU训练。
  - 未报告具体训练时长，但根据步骤数和批大小可推算相对短期。

## 5. 实验数量与充分性

- **数量**：覆盖3个多样性规划任务、3种模型规模（从1B到3B），提供主要结果、消融（κ有无）、解长度影响分析（图2）、随机示例对比（表1）。共约20+组实验数据。
- **充分性与客观性**：
  - 优点：基准选择合理（CoT和AoT的标准SFT变体），任务覆盖简单到复杂规划问题，模型规模梯度有区分。
  - 不足：未对比更多现有方法（如ToT、Self-Refine等，但作者在intro中已批评它们），也未在更大模型（如7B、13B或商业模型）上验证。实验仅用3个较小开源模型，泛化性有待验证。奖励函数参数（α、β、κ）需手动调节，未讨论敏感性。此外，消融实验仅涉及κ，未单独分析α等影响。

## 6. 主要结论与发现

- AoT-O3在保持或提升准确率的前提下，将解长度缩短高达80%（如Llama3-1B在Game of X上从31.9步降至9.7步，准确率从55%升至72%）。
- 在所有3个基准和3个模型上，AoT-O3均一致优于AoT-SFT和CoT-SFT，效率和准确性双提升。
- 随机示例在微调场景下效果显著下降（表1），证明高质量训练数据对微调的关键性。
- 解长度与性能正相关（图2），但AoT-O3通过RL有目的地压缩冗余步骤，同时保留有效推理结构。
- 非LLM奖励模型使RL训练更高效、避免奖励欺骗。

## 7. 优点

- **方法创新**：首次将RL显式用于优化AoT解长度，设计了简洁实用的非LLM奖励函数，避免训练复杂奖励模型。
- **效率显著**：在多个任务上实现60%-80%步数缩减，同时保持或提升准确率，环境与计算友好。
- **通用性**：方法不依赖特定模型或领域，在3种不同架构（Gemma、Llama）和3类规划问题上均有效。
- **理论分析**：提供了随机示例在微调 vs 提示下的对比实验，揭示了训练与推理时的差异，具有洞察力。
- **环境意义**：附录A量化了token减少的潜在能源与碳减排效益，呼应现实应用。

## 8. 不足与局限

- **模型规模有限**：仅测试1B~3B小模型，未验证在7B/13B或商业模型（如GPT-4）上的有效性。
- **基准覆盖窄**：仅3个规划任务（数字、拼图、单词），未涵盖更广泛的规划问题（如Blocksworld、调度等），也未与ToT、Graph-of-Thoughts等更复杂方法对比。
- **消融不充分**：仅对κ进行消融（κ=0 vs κ>0），未对α、β、KT效应等超参数进行系统分析。最终性能对α敏感，如公式(3)需手动调校。
- **RL训练稳定性**：仅使用RLOO，未与其他RL算法（PPO等）对比，未讨论训练中可能的不稳定或模式坍塌。
- **随机示例微调效果差**：表1显示随机示例微调导致准确率剧降，表明方法对训练数据质量有依赖（即使AoT-O3也基于有效解路径）。
- **计算成本**：尽管推理更节能，RL阶段仍需多轮采样（每问题4样本），训练开销可能不低，尤其对于更大模型。

（完）
