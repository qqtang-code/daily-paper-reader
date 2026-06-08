---
title: Demystifying Long Chain-of-Thought Reasoning
title_zh: 解密长链式思考推理
authors: "Shiming Yang, Yuxuan Tong, Xinyao Niu, Graham Neubig, Xiang Yue"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=OLodUbcWjB"
tags: ["query:mm-cot"]
score: 9.0
evidence: 系统研究长链式思考推理涌现机制，基于强化学习
tldr: 长链式思考推理能显著提升大模型能力，但其涌现条件尚未明确。本文通过系统的监督微调和强化学习实验，揭示了三个关键发现：数据质量、奖励设计和探索策略对长CoT生成的影响。这项研究为如何训练模型生成结构化、可回溯的长推理链提供了实践指导，有助于推动复杂推理的发展。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-olodubcwjb/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1774, \"height\": 453, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-olodubcwjb/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1767, \"height\": 387, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-olodubcwjb/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 851, \"height\": 374, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-olodubcwjb/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 852, \"height\": 377, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-olodubcwjb/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1773, \"height\": 444, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-olodubcwjb/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1776, \"height\": 474, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-olodubcwjb/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1777, \"height\": 430, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-olodubcwjb/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1773, \"height\": 440, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-olodubcwjb/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1735, \"height\": 382, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-olodubcwjb/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 973, \"height\": 540, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-olodubcwjb/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 874, \"height\": 456, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-olodubcwjb/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 887, \"height\": 538, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-olodubcwjb/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 885, \"height\": 568, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-olodubcwjb/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1326, \"height\": 578, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-olodubcwjb/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1749, \"height\": 992, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-olodubcwjb/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 862, \"height\": 298, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-olodubcwjb/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 864, \"height\": 347, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-olodubcwjb/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 858, \"height\": 325, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-olodubcwjb/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 853, \"height\": 282, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-olodubcwjb/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 857, \"height\": 338, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-olodubcwjb/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 880, \"height\": 442, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-olodubcwjb/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 672, \"height\": 132, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-olodubcwjb/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1697, \"height\": 264, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-olodubcwjb/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1710, \"height\": 1076, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-olodubcwjb/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1856, \"height\": 1319, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-olodubcwjb/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1687, \"height\": 1113, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-olodubcwjb/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1687, \"height\": 1113, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-olodubcwjb/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1684, \"height\": 659, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-olodubcwjb/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1701, \"height\": 2184, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-olodubcwjb/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1779, \"height\": 1411, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-olodubcwjb/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1703, \"height\": 172, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-olodubcwjb/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1465, \"height\": 1228, \"label\": \"Table\"}]"
motivation: 长链式思考的涌现条件和训练策略尚不明确。
method: 通过大量SFT和RL实验，系统分析影响长CoT生成的要素。
result: 识别出数据质量、奖励设计和探索策略三个关键因素。
conclusion: 为设计有效的长链推理训练方案提供了理论基础。
---

## Abstract
Scaling inference compute has become a key driver of advanced reasoning in large language models (LLMs). A proven approach for scaling inference compute is to generate long chains-of-thought (CoTs), enabling models to engage in structured reasoning strategies such as backtracking and error correction. Reinforcement learning (RL) has emerged as a crucial method for developing these capabilities, yet the conditions under which long CoTs emerge remain unclear, and RL training requires careful design choices. In this study, we systematically investigate the underlying *mechanics of long CoT reasoning*—examining the factors that enable models to generate extended reasoning trajectories. Through extensive supervised fine-tuning (SFT) and RL experiments, we identify three key findings: 1) while SFT is not strictly necessary, it significantly simplifies training and improves efficiency; 2) reasoning capabilities tend to emerge with increased training compute but are not guaranteed, making reward shaping essential for stabilizing CoT length growth; and 3) scaling verifiable reward signals is critical for RL, and we find that leveraging noisy, web-extracted solutions with filtering mechanisms shows promising potential, particularly in out-of-distribution (OOD) reasoning tasks such as STEM problem-solving. These insights provide practical guidance for optimizing training strategies to enhance long CoT reasoning in LLMs.

---

## 论文详细总结（自动生成）

# 解密长链式思考推理

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：大语言模型（LLM）的推理能力可通过扩展推理计算（inference compute）来提升。一种有效的方法是生成**长链式思考（long CoT）**，使模型能够执行回溯、纠错等结构化推理策略。强化学习（RL）在培养这些能力方面日益重要，但长 CoT 的涌现条件尚不明确，RL 训练也需要精心设计。
- **核心问题**：模型如何在 RL 训练下学习生成并稳定扩展长 CoT？哪些因素（如 SFT 数据、奖励设计、可验证信号）对长 CoT 的涌现和性能提升至关重要？
- **整体含义**：通过系统分析 SFT 和 RL 中影响长 CoT 的机制，为优化训练策略提供实用指导，推动复杂推理能力的发展。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：将长 CoT 视为一个马尔可夫决策过程（MDP），使用基于最终答案正确性的稀疏奖励（outcome-based reward），并通过 PPO 或 REINFORCE 进行策略优化。重点在于 SFT 初始化、奖励函数设计以及可验证数据的利用。
- **关键技术细节**：
  - **SFT 初始化**：采用拒绝采样（rejection sampling）从长 CoT 模型（如 QwQ-32B-Preview）蒸馏数据，作为 RL 的初始策略。
  - **奖励函数设计**：提出**余弦长度缩放奖励（Cosine Reward）**，它是一个分段余弦函数，根据生成长度和答案正确性动态调整奖励：
    - 正确回答：短 CoT 得高分，长 CoT 得稍低分；
    - 错误回答：短 CoT 受重罚，长 CoT 受轻罚；
    - 超出长度限制时给予强惩罚。
    - 公式：`R(C, L_gen) = CosFn(L_gen, L_max, r_c0, r_cL)` 或 `CosFn(L_gen, L_max, r_w0, r_wL)`，其中 `CosFn(t,T,η_min,η_max) = η_min + 0.5*(η_max-η_min)*(1+cos(tπ/T))`。
  - **重复惩罚**：引入 N-gram 重复惩罚机制（算法 1），在每步 token 级别施加惩罚，并用低折扣因子强化局部信号。
  - **多折扣因子 GAE**：修改 PPO 的 GAE 公式，为正确性奖励和重复惩罚分别设置不同折扣因子 γ_c 和 γ_p，以优化不同信号的学习。
  - **可验证信号扩展**：利用带噪声的网络数据（WebInstruct），通过规则验证器或模型验证器获得奖励，并采用过滤策略提升质量。

## 3. 实验设计：数据集、Benchmark、对比方法

- **数据集**：
  - **SFT 数据**：从 QwQ-32B-Preview（长 CoT）和 Qwen2.5-Math-72B-Instruct（短 CoT）蒸馏，基于 MATH 训练集（7,500 样本）。部分实验使用 WebInstruct-462k（网络提取的 QA 对，带有噪声）。
  - **RL 数据**：MATH 训练集（可验证）或 WebInstruct 子集。
- **Benchmark**：
  - MATH-500（数学，领域内）
  - AIME 2024（数学，领域外）
  - TheoremQA（STEM，领域外）
  - MMLU-Pro-1k（通用，领域外）
- **对比方法**：
  - 长 CoT vs 短 CoT SFT
  - 从长 CoT 模型蒸馏 vs 通过动作编排构建长 CoT
  - 经典奖励（Classic Reward，正确+1/错误-1） vs 余弦奖励 vs 余弦奖励+重复惩罚
  - 不同折扣因子组合
  - 不同上下文窗口（4K, 8K, 16K）
  - 规则验证器 vs 模型验证器（LLM-as-judge）
  - 不同模型大小：Llama-3.1-8B、Qwen2.5-Math-7B、Qwen-2.5-1.5B、Qwen-2.5-32B
  - PPO vs REINFORCE++

## 4. 资源与算力

- 论文未明确说明使用的 GPU 型号、具体数量及总训练时长。仅提到使用 OpenRLHF 框架、DeepSpeed ZeRO、Flash Attention 2 等加速技术，并提及遇到 32B 模型扩展时 GPU 数量需求过大而无法进行。因此**算力信息未公开**。

## 5. 实验数量与充分性

- **实验数量**：涉及大量消融实验和对比：
  - SFT 缩放实验（4 种采样数 × 2 种 CoT 类型）
  - SFT+RL 联合实验（多种初始化条件）
  - 奖励函数对比（经典、余弦、余弦+重复惩罚，多种超参数）
  - 上下文窗口规模（3 种）
  - 折扣因子组合（7 种以上）
  - 不同模型规模（4 种）
  - 噪声数据利用（无过滤、部分过滤、完全过滤，规则 vs 模型验证器）
  - REINFORCE++ 稳定性实验
- **充分性与公平性**：
  - 实验设计较为充分，覆盖了 SFT 数据量、奖励设计、模型大小、数据质量等多个维度。
  - 控制变量较为严谨（如 SFT 数据子集包含关系、相同基座模型对比）。
  - 但某些实验（如 REINFORCE++）只进行了初步观察，未深入调优，结论有限。此外，32B 模型扩展因资源限制未完成，可能影响结论的通用性。整体上实验客观公平，但部分结论依赖有限设置。

## 6. 论文的主要结论与发现

1. **SFT 数据影响**：长 CoT SFT 比短 CoT SFT 具有更高的性能上限，且 SFT 初始化对 RL 改进至关重要：长 CoT 初始化使得 RL 容易进一步提升，短 CoT 初始化则几乎无收益。
2. **数据来源**：从已有长 CoT 模型（如 QwQ-32B-Preview）蒸馏的数据（涌现模式）优于通过动作编排构建的数据，尤其在 OOD 任务上。
3. **奖励设计**：
   - 经典奖励（+1/-1）导致 CoT 长度不稳定，易超出上下文窗口，性能下降。
   - 余弦奖励能稳定控制 CoT 长度增长，提升训练准确率和下游性能。
   - 重复惩罚可缓解奖励破解（reward hacking），保持推理结构（如分支频率）。
   - 不同奖励类型需不同折扣因子：正确性奖励宜用高折扣（长期依赖），重复惩罚宜用低折扣（局部惩罚）。
4. **上下文窗口**：相同训练样本数下，8K 窗口优于 4K，但 16K 反而效果更差，说明更大窗口需要更多训练数据才能有效利用。
5. **可验证信号扩展**：将带噪声的网络数据（WebInstruct）用于 SFT 和 RL 能提升平均性能，尤其在 OOD 任务上。使用规则验证器时需过滤数据；使用模型验证器可处理未过滤数据。
6. **训练稳定性**：REINFORCE++ 比 PPO 更不稳定，PPO 仍为首选方案。

## 7. 优点

- **系统性**：全面分析了影响长 CoT 生成的多个关键因素（SFT、奖励、数据、模型大小），并给出具体设计原则。
- **创新奖励设计**：余弦长度缩放奖励结合重复惩罚，方法简洁有效，易于实现。
- **噪声数据利用**：展示了低成本获取可验证信号的方法，对实际应用有参考价值。
- **详细消融**：大量超参数消融实验（折扣因子、上下文窗口、奖励超参数等），结论可信度高。
- **可复现性**：代码开源，实验设置详尽（见附录）。

## 8. 不足与局限

- **模型规模局限**：主要实验基于 8B/7B 模型，32B 实验未完成，更大型号（>70B）的效果未知。
- **领域局限**：训练数据以数学为主，虽然评估包括 STEM 和通用，但其他推理领域（如编程、逻辑）未涉及。
- **奖励依赖**：依赖可验证的最终答案，不适用于开放性任务；模型验证器在未过滤数据上表现更好但有被攻击风险。
- **训练稳定性**：REINFORCE++ 调优困难，PPO 虽稳定但计算效率低（多人反映硬件利用率低）。
- **实验充分性**：部分实验（如折扣因子）仅在一组设置下验证，推广性需更多证据；重复惩罚与余弦奖励的交互机制未深入分析。
- **资源未公开**：算力消耗未说明，不利于成本预估和复现。

（完）
