---
title: Enhancing the Outcome Reward-based RL Training of MLLMs with Self-Consistency Sampling
title_zh: 通过自一致性采样增强多模态大模型基于结果奖励的强化学习训练
authors: "Jiahao Wang, Weiye Xu, Aijun Yang, Wengang Zhou, Lewei Lu, Houqiang Li, Xiaohua Wang, Jinguo Zhu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=cGkfMGQdCy"
tags: ["query:mm-cot"]
score: 8.0
evidence: 通过自一致性采样改善多模态逐步推理
tldr: 多模态逐步推理的强化学习常因不忠实轨迹获得错误奖励。提出自一致性采样（SCS），通过引入视觉扰动和截断重采样生成一致性轨迹，过滤掉侥幸正确的虚假推理，从而提升结果奖励信号的可靠性，实验表明该方法能有效改善多模态推理的实际质量。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-cgkfmgqdcy/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1420, \"height\": 813, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cgkfmgqdcy/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1381, \"height\": 811, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cgkfmgqdcy/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1378, \"height\": 554, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cgkfmgqdcy/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1356, \"height\": 658, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cgkfmgqdcy/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 578, \"height\": 376, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cgkfmgqdcy/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 577, \"height\": 375, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cgkfmgqdcy/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1414, \"height\": 662, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cgkfmgqdcy/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1435, \"height\": 470, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cgkfmgqdcy/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1441, \"height\": 587, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cgkfmgqdcy/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1433, \"height\": 491, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cgkfmgqdcy/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1443, \"height\": 608, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cgkfmgqdcy/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1448, \"height\": 525, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cgkfmgqdcy/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1457, \"height\": 523, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cgkfmgqdcy/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1419, \"height\": 834, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cgkfmgqdcy/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 253, \"height\": 183, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cgkfmgqdcy/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 75, \"height\": 71, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cgkfmgqdcy/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 301, \"height\": 138, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cgkfmgqdcy/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 267, \"height\": 151, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cgkfmgqdcy/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 76, \"height\": 70, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cgkfmgqdcy/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 600, \"height\": 92, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cgkfmgqdcy/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 488, \"height\": 181, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cgkfmgqdcy/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 317, \"height\": 144, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cgkfmgqdcy/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 432, \"height\": 250, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-cgkfmgqdcy/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 975, \"height\": 517, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-cgkfmgqdcy/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1453, \"height\": 733, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-cgkfmgqdcy/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1449, \"height\": 278, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-cgkfmgqdcy/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1451, \"height\": 287, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-cgkfmgqdcy/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1154, \"height\": 208, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-cgkfmgqdcy/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1310, \"height\": 903, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-cgkfmgqdcy/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1308, \"height\": 954, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-cgkfmgqdcy/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1332, \"height\": 906, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-cgkfmgqdcy/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1547, \"height\": 907, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-cgkfmgqdcy/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1422, \"height\": 102, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-cgkfmgqdcy/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 537, \"height\": 183, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-cgkfmgqdcy/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 541, \"height\": 183, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-cgkfmgqdcy/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 537, \"height\": 184, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-cgkfmgqdcy/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1200, \"height\": 144, \"label\": \"Table\"}]"
motivation: 结果奖励中不忠实轨迹会导致奖励信号不可靠。
method: 提出SCS，通过视觉扰动和截断重采样生成一致性轨迹。
result: 在多模态推理基准上训练出的模型获得更准确的推理能力。
conclusion: SCS为多模态逐步推理的RL训练提供了有效的防作弊机制。
---

## Abstract
Outcome‑reward reinforcement learning (RL) is a common—and increasingly significant—way to refine the step‑by‑step reasoning of multimodal large language models (MLLMs). In the multiple‑choice setting—a dominant format for multimodal reasoning benchmarks—the paradigm faces a significant yet often overlooked obstacle: unfaithful trajectories that guess the correct option after a faulty chain of thought receive the same reward as genuine reasoning, which is a flaw that cannot be ignored. We propose Self‑Consistency Sampling (SCS) to correct this issue. For each question, SCS (i) introduces small visual perturbations and (ii) performs repeated truncation‑and‑resampling of a reference trajectory; agreement among the resulting trajectories yields a differentiable consistency score that down‑weights unreliable traces during policy updates. Plugging SCS into RLOO, GRPO, REINFORCE++ series improves accuracy by up to 7.7 percentage points on six multimodal benchmarks with negligible extra computation, offering a simple, general remedy for outcome‑reward RL in MLLMs.

---

## 论文详细总结（自动生成）

## 论文详细总结

### 1. 核心问题与整体含义（研究动机和背景）
- **问题背景**：多模态大语言模型（MLLM）的推理能力可通过基于结果奖励的强化学习（Outcome‑reward RL）来增强。在选择题（multiple‑choice）这一主流评测格式中，一个关键却被忽视的缺陷是：不忠实的推理轨迹（即错误推理过程但偶然猜对答案）会获得与正确推理完全相同的奖励，从而鼓励模型学习虚假的推理模式。
- **研究动机**：作者通过实验证实，传统 outcome‑reward RL 在选择题训练中提升精度有限，且大量正确回答伴随错误推理（“侥幸正确”），这种现象普遍存在。因此，需要一种机制来区分真实推理与虚假推理，提升奖励信号的信噪比。
- **整体意义**：提出了一种轻量级、通用的自一致性采样（SCS）方法，可在不依赖额外奖励模型的情况下，显著提升 MLLM 在多项选择题中的推理忠实度和最终精度，为 outcome‑reward RL 提供了有效且可广泛采纳的改进方案。

### 2. 方法论：核心思想、关键技术细节与算法流程
- **核心思想**：利用多次采样结果之间的一致性作为推理质量的代理信号。如果模型推理是可靠的，那么轻微扰动（截断或图像噪声）下重复采样应产生一致答案；若推理不可靠，则答案会分散。基于此设计一个一致性奖励，与原始正确性奖励共同指导策略优化。
- **关键技术细节**：
  - **截断‑重采样（Truncation‑Resampling）**：对于每个问题，首先生成一个初始推理轨迹 τ，然后按比例 k 截断至前缀 τ<；从该前缀出发，多次重采样得到多个后续回答，记录所有答案集合 A。若答案集合大小较小（即一致性高），则给予高奖励。
  - **视觉扰动（Visual‑Perturbation）**：在每次重采样时，对输入图像添加随机高斯噪声（σi ∼ U(σmin, σmax)），迫使模型依赖稳健的视觉证据而非偶然特征。
  - **一致性奖励公式**：rcon = (1/N) * (N - |A|) * c，其中 N 为重采样次数，c 为缩放系数。正确的推理轨迹会得到最大一致性奖励（因为 A 中只有一个答案），而错误推理则通常产生多个不同答案，奖励较低。
  - **与现有 RL 算法集成**：SCS 作为一个奖励项附加到原始的准确率奖励 r_acc 和格式奖励之上，形成总奖励 r = r_acc + r_format + rcon，可与 GRPO、RLOO、REINFORCE++ 等任意 outcome‑reward RL 算法结合。
- **算法流程**（文字描述）：
  1. 输入一个问题 x，从当前策略 πθ 采样初始答案和推理轨迹 a, τ。
  2. 计算准确率奖励 r_acc。
  3. 对初始轨迹进行截断（比例 k），并对图像施加随机噪声。
  4. 从截断点重采样 m 个新答案，收集到集合 A。
  5. 计算一致性奖励 rcon = (N - |A|) * c / N。
  6. 总奖励 r = r_acc + rcon。
  7. 使用任意策略梯度方法（如 RLOO）更新策略参数 θ。

### 3. 实验设计
- **训练数据集**：M3CoT（通用）、ScienceQA（科学）、Geometry3K（几何），仅保留含图像的多选题，共约 1.6 万题。
- **评测基准（6 个）**：M3CoT、ScienceQA、MathVision、We-Math、MMMU（多学科）、MathVerse，涵盖数学、科学、医学等，全部使用选择题子集。
- **对比方法**：
  - 基础预训练模型（Qwen2.5‑VL‑7B‑Instruct 等）。
  - SFT（监督微调）在相同数据集上。
  - 原始 outcome‑reward RL 算法：RLOO、GRPO、REINFORCE++、REINFORCE++‑baseline。
  - 每种 RL 算法 + SCS 版本。
- **额外分析**：人工评估推理忠实度（采样 100 个正确回答，检查推理是否合理），并使用 o3‑mini 和 Gemini 2.5 Flash 两个闭源 LLM 作为评判者。

### 4. 资源与算力
- 使用 **8 块 A800 GPU**，每次实验约 **24 小时**。未提供具体显存或总计算量细节。
- 训练基于 OpenRLHF 框架，推理使用 vLLM 加速。

### 5. 实验数量与充分性
- **实验规模**：共涉及 4 种 RL 算法 × 2（加/不加 SCS）× 6 个评测基准，共 48 个主实验结果。此外还包含 3 种模型（Qwen‑7B、Qwen‑3B、InternVL‑8B）的跨模型验证、消融实验（组件贡献、超参数灵敏度）、统计稳健性（重复 3 次计算 95% 置信区间）、推理忠实度定量分析（人工+LLM 评价）。
- **充分性与公平性**：实验覆盖了主流 RL 算法、多模型规模、多领域基准，并与 SFT 和原始 RL 基线严格对比，使用相同超参数（仅 SCS 组件差异）。消融实验清晰展示了两个组件的单独与联合贡献。超参数分析展示了方法的鲁棒性。统计检验表明提升显著。因此实验设计比较充分、客观、公平。

### 6. 主要结论与发现
- SCS 可显著提升所有 tested RL 算法的精度，其中 **RLOO 提升最大（+7.7 个百分点）**，REINFORCE++ 提升 2.0%，GRPO 提升 0.9%。
- SCS 的收益对不同模型结构（Qwen、InternVL）和规模（3B、7B、8B）均成立。
- SCS 不仅提升答案正确率，还提高了推理的忠实度：人工检查和 LLM 评判均显示不忠实推理比例下降约 15%。
- 消融实验表明，截断‑重采样和视觉扰动各自贡献约 5 个百分点，组合使用效果最佳。
- 超参（截断比例、重采样次数）对性能有一定影响，但总体波动在 4 个百分点以内，表明方法稳健。

### 7. 优点
- **简单且通用**：无需额外奖励模型或复杂训练策略，可直接插入现有 outcome‑reward RL 框架。
- **低计算开销**：仅增加采样阶段（可批量化、并行化），相对训练总时间增加约 38%，但性能收益显著。
- **有效应对虚假推理**：通过一致性奖励明确惩罚侥幸猜对的情况，提升模型推理的可解释性和可信度。
- **理论支撑清晰**：论文提供了公式推导，证明正确轨迹的一致性期望奖励高于错误轨迹。
- **跨模型、跨算法普适**：在多种基座模型和多种 RL 方法上均取得一致改善，泛化性强。

### 8. 不足与局限
- **实验覆盖有待扩展**：仅测试了多模态模型（MLLM），未在纯文本 LLM 上验证；也仅覆盖了选择题格式，未验证在自由回答（open‑ended）或生成型任务上的适用性。
- **假设有一定限制**：方法依赖于“唯一正确推理路径”的假设，对于存在多种有效解的问题可能不适用。
- **计算开销并非零**：虽然作者称“negligible extra computation”，但实际训练时间增加约 38%（从 12.5h 到 17.2h），在资源敏感场景下需权衡。
- **未讨论负效应**：一致性奖励可能过度惩罚合理但多样化的推理方式（如多步推导中阈值不同导致答案一致但过程不同），论文未分析这类潜在负面情况。
- **安全性/伦理讨论缺失**：未涉及模型滥用风险、偏见放大等社会影响。

（完）
