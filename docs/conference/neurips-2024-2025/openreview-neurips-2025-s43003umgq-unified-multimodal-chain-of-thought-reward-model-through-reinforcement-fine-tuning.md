---
title: Unified Multimodal Chain-of-Thought Reward Model through Reinforcement Fine-Tuning
title_zh: 通过强化微调的统一多模态链式思考奖励模型
authors: "Yibin Wang, Zhimin Li, Yuhang Zang, Chunyu Wang, Qinglin Lu, Cheng Jin, Jiaqi Wang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=S43003uMGq"
tags: ["query:mm-cot"]
score: 9.0
evidence: 统一多模态链式思考奖励模型，结合长链推理
tldr: 当前多模态奖励模型缺乏深度推理，奖励信号不准确。为此提出UnifiedReward-Think，第一个统一的多模态链式思考奖励模型，通过显式融入长链推理过程，增强了奖励的可靠性和鲁棒性，实验表明其直接响应精度也得到改善，为多模态链式推理提供了更优的反馈机制。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-s43003umgq/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1397, \"height\": 738, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-s43003umgq/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1434, \"height\": 1116, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-s43003umgq/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1432, \"height\": 563, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-s43003umgq/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 316, \"height\": 227, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-s43003umgq/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 113, \"height\": 106, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-s43003umgq/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 405, \"height\": 177, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-s43003umgq/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 249, \"height\": 513, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-s43003umgq/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 453, \"height\": 138, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-s43003umgq/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 450, \"height\": 138, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-s43003umgq/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 96, \"height\": 107, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-s43003umgq/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 351, \"height\": 270, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-s43003umgq/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 405, \"height\": 202, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-s43003umgq/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 93, \"height\": 106, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-s43003umgq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1449, \"height\": 370, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-s43003umgq/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1444, \"height\": 496, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-s43003umgq/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1455, \"height\": 370, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-s43003umgq/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1456, \"height\": 461, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-s43003umgq/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1454, \"height\": 241, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-s43003umgq/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1446, \"height\": 227, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-s43003umgq/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1447, \"height\": 240, \"label\": \"Table\"}]"
motivation: 现有奖励模型推理深度不足导致奖励信号不准确。
method: 提出UnifiedReward-Think，将长链推理融入奖励模型训练。
result: 在多个多模态对齐任务上取得更优的奖励质量。
conclusion: 该工作证明了长链推理对于提升多模态奖励模型有效性的价值。
---

## Abstract
Recent advances in multimodal Reward Models (RMs) have shown significant promise in delivering reward signals to align vision models with human preferences. However, current RMs are generally restricted to providing direct responses or engaging in shallow reasoning processes with limited depth, often leading to inaccurate reward signals. We posit that incorporating explicit long chains of thought (CoT) into the reward reasoning process can significantly strengthen their reliability and robustness. Furthermore, we believe that once RMs internalize CoT reasoning, their direct response accuracy can also be improved through implicit reasoning capabilities. To this end, this paper proposes UnifiedReward-Think, the first unified multimodal CoT-based reward model, capable of multi-dimensional, step-by-step long-chain reasoning for both visual understanding and generation reward tasks. Specifically, we adopt an exploration-driven reinforcement fine-tuning approach to elicit and incentivize the model's latent complex reasoning ability: (1) We first use a small amount of image generation preference data to distill the reasoning process of GPT-4o, which is then used for the model's cold start to learn the format and structure of CoT reasoning. (2) Subsequently, by leveraging the model's prior knowledge and generalization capabilities, we prepare large-scale unified multimodal preference data to elicit the model's reasoning process across various vision tasks. During this phase, correct reasoning outputs are retained for rejection sampling to refine the model (3) while incorrect predicted samples are finally used for Group Relative Policy Optimization (GRPO) based reinforcement fine-tuning, enabling the model to explore diverse reasoning paths and optimize for correct and robust solutions. Extensive experiments confirm that incorporating long CoT reasoning significantly enhances the accuracy of reward signals. Notably, after mastering CoT reasoning, the model exhibits implicit reasoning capabilities, allowing it to surpass existing baselines even without explicit reasoning traces.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：当前多模态奖励模型（Reard Models, RMs）在将视觉模型与人类偏好对齐方面展现了潜力，但大多局限于直接输出得分或进行浅层推理，缺乏深度和结构化逻辑，导致在复杂场景下奖励信号不准确，且难以解释。
- **核心假设**：论文指出，将显式的长链式思考（Chain-of-Thought, CoT）融入奖励推理过程可以显著增强奖励信号的可靠性和鲁棒性；并且一旦模型内化了这种推理能力，即使不生成显式推理痕迹，其直接响应的准确性也能借助隐式推理能力得到提升。
- **整体目标**：提出第一个统一的多模态CoT奖励模型——**UnifiedReward-Think**，能够对视觉理解和生成任务进行多维、逐步的长链推理，从而提供更准确、可解释的奖励信号。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：利用探索驱动的强化微调（Reinforcement Fine-Tuning）来激发和强化视觉语言模型（VLM）潜在的复杂长链推理能力，使其学会在评估候选输出时，先按多个维度评分，再汇总做出最终决策。
- **关键的三阶段训练流程**：
  1. **冷启动（Cold Start）**：使用少量图像生成偏好数据，蒸馏GPT-4o的推理过程，筛选出最终答案与真实标签一致的推理轨迹，用于监督微调，让模型学习CoT推理的格式和结构（如`<think>`和`<answer>`标签）。
  2. **拒绝采样（Rejection Sampling）**：准备大规模统一多模态偏好数据（涵盖图像/视频生成和理解），让模型生成CoT推理。保留最终答案与真实标签一致的推理轨迹，用于进一步监督微调，强化正确推理模式的分布。
  3. **GRPO强化微调**：将先前预测错误的样本用于GRPO（Group Relative Policy Optimization）训练。作者设计了两种可验证的奖励：格式奖励（确保输出包含`<think>`和`<answer>`标签）和准确性奖励（最终答案与真实标签匹配）。通过归一化优势函数、重要性采样裁剪和KL散度惩罚，引导模型探索不同推理路径并优化到正确解。

- **多维CoT奖励评分策略**：为解决推理与最终决策不一致的问题（即推理看似不合理但预测正确），模型在推理过程中对每个候选按多个任务相关维度（如语义一致性、美学、真实性等）分别评分，再汇总决定最终偏好，从而强制推理与结果对齐。

## 3. 实验设计：数据集、基准与对比方法

- **数据集**：
  - 图像生成：HPD (25.6K)、OIP (7.4K)、EvalMuse (3K)、OpenAI-4o_t2i_human_preference (6.7K)
  - 视频生成：VideoDPO (10K)、Text2Video-Human Preferences (5.7K)
  - 图像理解：从LLaVA-Critic-113K中采样30K数据
  - 视频理解：ShareGPTVideo-DPO (17K)
  - 冷启动数据集：自行构建的ImageGen-CoT-Reward-5K（从上述图像生成数据集中随机采样5K，经GPT-4o蒸馏并筛选）。
- **评估基准**：
  - 图像/视频理解：VLRewardBench (1,250样本) 和 ShareGPTVideo (5K样本)
  - 图像/视频生成：GenAI-Bench（图像和视频子集）和 VideoGen-RewardBench
- **对比方法**：包括PickScore、HPSv2、ImageReward、LLaVA-Critic、VisionReward、VideoScore、LiFT-Critic、VideoReward、UnifiedReward等多个现有奖励模型，覆盖图像/视频生成和理解任务。

## 4. 资源与算力

- **冷启动和拒绝采样阶段**：使用8块NVIDIA H100 (80GB) GPU，batch size=1，16梯度累积步数，学习率2.5×10⁻⁶，warm-up比例0.3。
- **GRPO阶段**：使用64块NVIDIA H20 (97GB) GPU，batch size=1，单步梯度累积，学习率1×10⁻⁶，KL惩罚系数β=0.04，每组生成8个响应。
- 论文未明确给出总训练时长，但各阶段分别陈述了硬件配置。

## 5. 实验数量与充分性

- **实验数量**：论文报告了多个基准上的定量比较（表1、表2），包括图像理解、图像生成、视频生成的不同指标（总体准确率、宏观准确率、tau和diff等）。此外，还进行了丰富的消融实验：
  - 各训练阶段的消融（冷启动、拒绝采样、GRPO）
  - GRPO有无CoT推理的对比
  - 不同基座模型（LLaVA-OneVision-7B vs Qwen2.5-VL-7B）的鲁棒性测试
  - 冷启动蒸馏来源比较（GPT-4o vs Qwen2.5-VL-72b）
  - 拒绝采样阶段效果消融（表5）
- **充分性与公平性**：实验设计比较全面，覆盖了多种主流基准和对比方法，并在不同任务上验证一致性。消融实验清晰展示了各阶段的贡献。但需要注意部分指标（如“tau”用于包含平局的情况）上，作者明确表示模型未针对平局优化，因此在该指标上可能弱于专门训练的基线，但论文对此进行了说明，整体比较是客观的。另外，未报告误差棒或置信区间，可能因计算成本较高。

## 6. 论文的主要结论与发现

- 显式引入长CoT推理显著提升了奖励信号的准确性和鲁棒性，在所有视觉奖励任务（图像理解、图像生成、视频生成、视频理解）上均超越了现有方法。
- 模型在掌握CoT推理后，即使不输出显式推理痕迹（即仅提供直接答案），其性能仍优于所有基线，说明模型内化了隐式推理能力。
- 三阶段训练（冷启动→拒绝采样→GRPO）中，GRPO阶段带来的提升最为显著，而冷启动则能有效学习推理格式。
- 拒绝采样阶段对提升泛化能力至关重要，而GRPO对纠正错误样本的推理路径尤其有效。

## 7. 优点

- **首次提出统一的多模态CoT奖励模型**，能够同时处理视觉理解和生成任务，展示了多任务联合训练和CoT推理的协同效应。
- **多维评分策略**强制推理过程与最终决策保持一致，减少推理与结论脱节的风险，增强了可解释性和可靠性。
- **利用强化学习（GRPO）探索多样推理路径**，不同于监督微调的被动模仿，GRPO通过试错学习引导模型发现更深层的正确推理模式。
- 在多个基准上取得最优结果，且隐式推理能力使模型在推理时更高效（无需生成冗长推理链）。
- 实验设计较为全面，消融实验清晰验证了各阶段的贡献，并验证了方法对不同基座模型的鲁棒性。

## 8. 不足与局限

- **推理时间增加**：生成长CoT推理在测试时会导致更多延迟，但论文指出模型可以通过隐式推理避免此代价。
- **能力扩展受限于监督质量**：作者承认，强化学习本身不能从根本上扩展模型能力，只能放大SFT中已获得的知识；要进一步提高需更大规模的高质量CoT监督数据。
- **未处理平局场景**：训练数据中未包含平局样本，因此模型在判断两个候选质量相当时表现可能不如某些专门训练的基线。
- **潜在偏差风险**：奖励模型依赖于人类偏好数据，这些数据可能包含主观或偏差，可能被放大。论文未深入讨论公平性验证或去偏策略。
- **计算资源需求较高**：GRPO阶段需要64块H20 GPU，可能限制可复制性。

（完）
