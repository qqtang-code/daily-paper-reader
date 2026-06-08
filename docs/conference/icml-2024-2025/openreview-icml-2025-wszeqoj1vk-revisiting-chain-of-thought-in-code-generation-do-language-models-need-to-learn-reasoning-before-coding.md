---
title: "Revisiting Chain-of-Thought in Code Generation: Do Language Models Need to Learn Reasoning before Coding?"
title_zh: 重新审视代码生成中的链式思维：语言模型需要在编码前学习推理吗？
authors: "Ren-Biao Liu, Anqi Li, Chaoding Yang, Hui Sun, Ming Li"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=wSZeQoJ1Vk"
tags: ["query:mm-cot"]
score: 7.0
evidence: 链式思维训练在代码生成中的实证研究
tldr: 链式思维（CoT）在代码生成任务中有效，但模型如何从CoT数据中学习推理尚不清楚。本文通过分离CoT过程与代码解决方案，合成数据集并实验，发现反直觉的现象：即使CoT步骤不准确，模型仍能生成正确代码。这表明CoT训练中推理与代码学习可能存在解耦。为理解CoT在代码生成中的作用提供了新视角。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-wszeqoj1vk/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 851, \"height\": 346, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wszeqoj1vk/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1772, \"height\": 541, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wszeqoj1vk/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 831, \"height\": 260, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wszeqoj1vk/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 834, \"height\": 272, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wszeqoj1vk/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 860, \"height\": 386, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wszeqoj1vk/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 857, \"height\": 373, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wszeqoj1vk/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 834, \"height\": 383, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wszeqoj1vk/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 836, \"height\": 383, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wszeqoj1vk/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 834, \"height\": 381, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wszeqoj1vk/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 837, \"height\": 381, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wszeqoj1vk/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 826, \"height\": 269, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wszeqoj1vk/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1779, \"height\": 481, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wszeqoj1vk/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1777, \"height\": 490, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wszeqoj1vk/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1777, \"height\": 484, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wszeqoj1vk/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1776, \"height\": 488, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-wszeqoj1vk/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 796, \"height\": 243, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wszeqoj1vk/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 829, \"height\": 324, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wszeqoj1vk/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 741, \"height\": 320, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wszeqoj1vk/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 798, \"height\": 208, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wszeqoj1vk/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 793, \"height\": 208, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wszeqoj1vk/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 793, \"height\": 207, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wszeqoj1vk/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 819, \"height\": 246, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wszeqoj1vk/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 833, \"height\": 239, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wszeqoj1vk/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 851, \"height\": 209, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wszeqoj1vk/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1173, \"height\": 366, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wszeqoj1vk/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1201, \"height\": 281, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wszeqoj1vk/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1143, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wszeqoj1vk/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1322, \"height\": 238, \"label\": \"Table\"}]"
motivation: 探索链式思维数据如何影响语言模型在代码生成任务中的推理学习。
method: 合成独立CoT过程和代码的数据集，进行可控实验分析。
result: 发现CoT步骤与代码生成可分离，模型不一定需要先准确推理才能正确编码。
conclusion: 该工作揭示了CoT在代码生成中的学习机制，对未来CoT训练策略有指导意义。
---

## Abstract
Large Language Models (LLMs) have demonstrated exceptional performance in code generation, becoming increasingly vital for software engineering and development. Recently, Chain-of-Thought (CoT) has proven effective for complex tasks by prompting LLMs to reason step-by-step and provide a final answer.
However, research on *how LLMs learn to reason with CoT data for code generation* remains limited.
In this work, we revisit classic CoT training, which typically learns reasoning steps before the final answer.
We synthesize a dataset to separate the CoT process from code solutions and then conduct extensive experiments to study how CoT works in code generation empirically.
We observe counterintuitive phenomena, suggesting that the traditional training paradigm may not yield benefits for code generation. Instead, training LLMs to generate code first and then output the CoT to explain reasoning steps for code generation is more effective.
Specifically, our results indicate that a 9.86% relative performance improvement can be achieved simply by changing the order between CoT and code. Our findings provide valuable insights into leveraging CoT to enhance the reasoning capabilities of CodeLLMs and improve code generation.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：尽管 Chain-of-Thought（CoT）在复杂推理任务（如数学、逻辑）中被证明有效，但语言模型（LLM）如何通过 CoT 数据**学习推理**以提升代码生成能力，尚缺乏系统研究。
- **背景**：经典 CoT 训练范式通常要求模型先输出推理步骤，再生成最终答案。本文质疑该范式在代码生成任务中的必要性，提出“高质量代码本身即可视为推理过程，而传统 CoT 应被视为代码的解释”。
- **核心问题**：在代码生成的监督微调（SFT）中，CoT 和代码之间的**顺序**是否影响模型性能？模型是否必须先“学会推理”再“编写代码”？

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：通过合成高质量、结构化数据，分离 CoT 过程和代码解决方案，设计四种数据策略（Seed、Cw/o、Cfollow、Cprecede），系统对比不同排序对代码生成能力的影响。
- **关键技术细节**：
  - **数据合成**：从多个开源种子数据集（如 Magicoder-OSS-Instruct、ShareGPT Python 子集、Evol-CodeAlpaca 等）收集问题-答案对，使用教师模型 DeepSeek-V2.5-1210（或 GPT-4o）通过上下文蒸馏生成 CoT 和代码，并通过 **Self-Consistency**（自生成测试用例并验证正确性）过滤噪声数据。
  - **四种 SFT 策略**：
    - **Seed**：原始数据集（问题+原始回答）。
    - **Cw/o**：仅包含代码，不含 CoT。
    - **Cfollow**：先输出 CoT，再输出代码（经典顺序）。
    - **Cprecede**：先输出代码，再输出 CoT（本文提出顺序）。
  - **训练目标**：标准自回归交叉熵损失，公式略。
- **算法流程**：给定种子数据集 \(S = \{(x_i, y_i)\}\)，用少量示例 \(P\) 构建 few-shot prompt，调用教师模型生成推理步骤 \(r_i\) 和代码 \(c_i\)，再通过测试过滤得到高质量三元组 \((x_i, r_i, c_i)\)，最后按不同策略组织输入-输出对进行 SFT。

### 3. 实验设计：使用了哪些数据集 / 场景，其 benchmark 是什么，对比了哪些方法

- **数据集**：
  - **训练数据**：合成数据集，共约 52,293 个样本，随机选取 51,200 作为训练集，其余为验证集。数据来源包括 CodeExercise-Python、Codefuse-Evol-Instruct、Evol-Instruct-Code、Evol-CodeAlpaca、Python ShareGPT、Magicoder-OSS-Instruct。
  - **基准测试**（Benchmark）：
    - **Python 代码生成**：HumanEval、MBPP、HumanEval+、MBPP+（EvalPlus 扩展版）。
    - **跨分布泛化**：LiveCodeBench（按时间分片，评估 OOD）、BigCodeBench（指令跟随和工具调用）、LeetCode Contest（Easy/Medium/Hard 三级）。
    - **多语言**：MultiPL-E（C++、Java、PHP、Bash）。
    - **代码效率**：EvalPerf。
- **对比方法**：Seed、Cw/o、Cfollow、Cprecede 四种策略，并在不同基础模型（DeepSeek-Coder-6.7B/33B、Llama-3.1-8B、Qwen2.5-Chat-7B、Qwen2.5-Coder-7B/32B）、不同教师模型（GPT-4o）、不同数据源（Stack）、不同合成顺序下进行对比。

### 4. 资源与算力

- **实验硬件**：8 张 NVIDIA A100-SXM4-80GB GPU。
- **训练配置**：
  - 混合精度 BF16，使用 DeepSpeed ZeRO-3 和 FlashAttention-2。
  - 微批次大小：每 GPU 4，梯度累积步数可变。
  - 优化器：AdamW。学习率：峰值 1e-5，余弦衰减，预热比例 0.1。
  - 最大序列长度：4096 tokens。
  - 训练周期：主要实验为 3 epochs（其他实验中调整过 1、2、4 epochs）。
- **未明确说明**：具体训练时长（小时/天）未在文中给出。

### 5. 实验数量与充分性

- **实验数量**：非常丰富，包括：
  - 不同基础模型（6 种架构/规模）。
  - 不同教师模型（DeepSeek-V2.5 和 GPT-4o）。
  - 不同数据源（种子集和 Stack）。
  - 不同合成顺序（有无参考代码）。
  - 数据消融（不一致数据、签名删除、注释删除、混合模式、对抗代码）。
  - 超参数消融（批次大小、总 epochs、学习率）。
  - 不同评估维度（Pass@k、温度、多语言、效率）。
  - 统计显著性检验（t-test，5 次不同随机种子）。
- **充分性评价**：实验设计全面、系统，覆盖了模型架构、训练数据、策略变体、超参数和跨语言/任务迁移。结论在多种条件下稳定复现，客观性和公平性较高。

### 6. 论文的主要结论与发现

- **反直觉发现**：经典“先推理后编码”（Cfollow）在代码生成中并无优势，反而可能降低性能；而“先编码后解释”（Cprecede）带来 **9.86% 相对性能提升**（在 HumanEval+ 和 MBPP+ 平均得分上）。
- **核心观点**：高质量代码本身已具备“推理”属性，传统 CoT 应视为对代码的**解释**而非独立的推理过程。
- **机制分析**：
  - 条件困惑度（PPL）分析表明，先产生代码可降低两部分的学习难度差距，避免模型“过度思考”（overthinking）。
  - 注意力权重和梯度分析显示，Cprecede 使模型更均衡地关注代码和 CoT，且代码部分梯度贡献更稳定。
  - LLM-as-a-Judge 评估和代码质量（CodeBLEU）验证了 Cprecede 更符合人类偏好，且推理效率更高（推理步骤和 token 数更少）。
- **泛化性**：结论在不同规模（6.7B~33B）和架构的模型、不同教师模型、不同数据源下均成立，且在更复杂任务（LeetCode Hard、MultiPL-E）中依然有效。

### 7. 优点

- **数据质量高**：通过 Self-Consistency 过滤和上下文蒸馏，合成了结构清晰、推理和代码分离的数据集，为可控实验提供基础。
- **实验设计系统**：不仅对比了四种策略，还从多个角度（模型、数据、合成方法、超参数、消融）验证结论的鲁棒性。
- **见解新颖且实用**：挑战了 CoT 在代码生成中的传统应用方式，提供了直接可操作的训练策略（先代码后解释），对 CodeLLM 的 SFT 有明确指导意义。
- **理论分析深入**：从条件困惑度、KL 散度、注意力权重、梯度范数等角度揭示了内部机制，增强了结论的可信度。

### 8. 不足与局限

- **领域覆盖有限**：实验主要基于 Python 代码生成，虽然进行了多语言泛化（MultiPL-E），但其他语言（如 JavaScript、Rust）的验证不够充分。
- **合成数据潜在偏差**：数据依赖教师模型（DeepSeek-V2.5 / GPT-4o）生成，可能引入教师模型的偏见和错误模式，且过滤过程不一定完全消除噪声。
- **评估指标单一**：主要使用 Pass@k 衡量正确性，缺乏对代码安全性、可读性、鲁棒性等维度的评估。EvalPerf 虽涉及效率，但仅针对正确样本。
- **训练资源需求**：实验依赖 8×A100 GPU，对于资源有限的研究团队可能难以复现全部实验。
- **可解释性未深入**：虽然分析了注意力权重等，但关于“为什么先代码后推理有效”的理论解释仍偏定性，缺乏严格数学证明。
- **未考虑更长序列**：最大序列长度 4096 tokens，在更长程序或复杂多文件项目中效果未知。
- **未对比强化学习等方法**：工作仅限于 SFT 阶段，未探讨结合 RLHF 或在线学习时的效果差异。

（完）
