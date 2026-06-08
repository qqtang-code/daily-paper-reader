---
title: "SPRINT: Enabling Interleaved Planning and Parallelized Execution in Reasoning Models"
title_zh: SPRINT：在推理模型中实现交织计划和并行执行
authors: "Emil Biju, Shayan Talaei, Zhemin Huang, Mohammadreza Pourreza, Azalia Mirhoseini, Amin Saberi"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=h5YGwnMTke"
tags: ["query:mm-cot"]
score: 7.0
evidence: 在大推理模型中对长链推理进行并行化执行
tldr: 大推理模型生成冗长的顺序思维链导致推理时间长。论文提出SPRINT框架，通过重新组织推理轨迹为结构化计划和并行执行，使模型学会动态识别子任务并并行化执行。在保持准确度的同时显著提升推理速度，为长链推理的实用化提供了重要优化方案。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-h5ygwnmtke/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1451, \"height\": 631, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h5ygwnmtke/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1431, \"height\": 577, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h5ygwnmtke/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1438, \"height\": 453, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h5ygwnmtke/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 655, \"height\": 652, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h5ygwnmtke/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 674, \"height\": 647, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h5ygwnmtke/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1441, \"height\": 489, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h5ygwnmtke/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 589, \"height\": 746, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h5ygwnmtke/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1393, \"height\": 1083, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-h5ygwnmtke/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1373, \"height\": 483, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h5ygwnmtke/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1319, \"height\": 438, \"label\": \"Table\"}]"
motivation: 长链推理的串行执行导致推理时间过长，需要并行化来提升效率。
method: 通过数据重组和微调，使模型学会将推理分解为可并行执行的子任务。
result: 在多个复杂推理任务上，推理速度提升数倍，准确度保持或略有提升。
conclusion: 并行化执行是加速长链推理的有效途径，SPRINT提供了一种通用的实现框架。
---

## Abstract
Large reasoning models (LRMs) excel at complex reasoning tasks but typically generate lengthy sequential chains-of-thought, resulting in long inference times before arriving at the final answer. To address this challenge, we introduce SPRINT, a novel post-training and inference-time framework designed to enable LRMs to dynamically identify and exploit opportunities for parallelization during their reasoning process. SPRINT incorporates an innovative data curation pipeline that reorganizes natural language reasoning trajectories into structured rounds of long-horizon planning and parallel execution. By fine-tuning LRMs on a small amount of such curated data, the models learn to dynamically identify independent subtasks within extended reasoning processes and effectively execute them in parallel. Through extensive evaluations, we demonstrate that models fine-tuned with the SPRINT framework match the performance of reasoning models on complex domains such as mathematics while generating up to 39% fewer sequential tokens on problems requiring more than 8,000 output tokens. Finally, we observe consistent results transferred to two out-of-distribution tasks, namely GPQA and Countdown, with up to 45% and 65% reduction in average sequential tokens respectively for longer reasoning trajectories, while matching the performance of the fine-tuned reasoning model.

---

## 论文详细总结（自动生成）

# SPRINT 论文总结

## 1. 核心问题与整体含义
- **研究动机**：大型推理模型（LRMs，如 DeepSeek-R1、OpenAI o1）虽擅长复杂推理，但生成极长的顺序思维链（chain-of-thought），导致推理延迟极高，难以实际部署。
- **核心问题**：如何在保持高推理准确度的同时，大幅缩短推理时间？
- **整体含义**：SPRINT 提出一种后训练 + 推理框架，训练模型在推理过程中动态识别独立的子任务并将之并行化执行，从而显著减少顺序 token 生成量，加速推理而不牺牲精度。

## 2. 方法论
- **核心思想**：将传统顺序思维链重组为交替进行的“规划”和“并行执行”阶段。推理过程由规划器（planner）和执行器池（pool of executors）协同完成。
- **关键技术细节**：
  - **数据流程**：
    1. **步骤提取**：用 GPT-4o 将原始推理轨迹分解为若干个“步骤”，每个步骤包含“规划”和“执行”两部分。
    2. **DAG 创建**：用 GPT-4o-mini 确定步骤间的依赖关系，形成有向无环图。
    3. **打包**：根据依赖关系将步骤分组为阶段（stages），使得同一阶段内的计划和执行可并行。关键优化：若某步骤的执行仅含计划（plan-only），其子步骤可提前并入同阶段。
    4. **过滤与格式化**：保留并行化比率（步骤数/阶段数 ≥1.5）的样本，并格式化为带 `<Plan_i>`、`<prompt_i.j>`、`<execution_i.j>` 标签的序列。
  - **训练**：仅用约 1700 条这样的重组数据对深度求索 R1-Distill-7B 模型进行全参数监督微调，使其学会按交错规划-执行格式推理。
  - **推理**：模型生成当前阶段的多条独立计划（prompts），每个 prompt 分配给一个执行器并行完成；所有结果同步回上下文，规划器据此生成下一阶段计划或直接输出最终答案。
- **算法流程**（文字说明）：每轮推理：规划器根据累积上下文生成多组独立计划 → 执行器并行执行各任务 → 将执行结果追加到上下文 → 循环直至输出最终答案。

## 3. 实验设计
- **数据集与场景**：
  - **域内**：MATH-500（数学问题）。
  - **域外**：GPQA-diamond（研究生级科学问答）、Countdown（数字组合游戏）。
- **基准方法**：
  - Base：DeepSeek-R1-Distill-7B（原始推理模型）。
  - RFT：用相同 1700 条原始顺序轨迹微调的推理模型（控制数据量）。
  - SoT-chat / SoT-reasoning：Skeleton-of-Thought 方法（无微调）。
  - Self-consistency：多次重复采样+多数投票。
- **指标**：最终答案的准确率（pass@1）和生成的平均顺序 token 数。

## 4. 资源与算力
- **训练**：8 块 NVIDIA A100 (40GB) GPU，全参数微调，batch size=1，训练 5 epochs。采用 bfloat16、DeepSpeed ZeRO Stage 3、4-bit 量化以节省显存。训练具体时长未明确给出，但可推断为相对资源密集（因长上下文）。
- **推理**：每个 7B 模型部署在单张 A100 (40GB) GPU 上，使用 vLLM。

## 5. 实验数量与充分性
- **实验覆盖**：在 3 个数据集上评估（数学、科学问答、数字游戏），对比 4+ 种基线，并进行了消融（RFT 控制数据量影响）。
- **充分性**：实验设计较为全面：
  - 报告了平均 token 和长轨迹（>8k token）的 token 节省比例。
  - 分析了不同难度问题下的并行化阶段数分布。
  - 展示了在域外任务上的泛化结果。
- **公平性**：所有方法使用相同基础模型（R1-Distill-7B），SPRINT 与 RFT 使用完全相同数量的训练数据（1700 条），确保对比公平。
- **潜在不足**：未报告多次运行的标准差或误差条（文中提及因资源限制未做统计显著性检验）；未包含更复杂任务的评估（如代码生成、数学竞赛等）。

## 6. 主要结论与发现
- SPRINT 在 MATH-500 上准确率达 **92.5%**，超过传统蒸馏模型 RFT（91%），同时平均减少 440 个顺序 token（约 15%）。
- 对于长推理轨迹（>8000 token），顺序 token 减少高达 **39%**。
- 在域外任务 Countdown 上，准确率最高（85.9%），顺序 token 减少 **53.5%**；在 GPQA 上准确率最高（51.0%），token 减少 **10.8%**。
- 并行化主要发生在前几个阶段（探索策略），后阶段更趋于确定。

## 7. 优点
- **方法创新**：首次将交织规划-并行执行引入推理模型训练，模型可动态适应任务结构，无需人工设计的搜索树。
- **高效训练**：仅需少量（1700 条）精心重组的数据即可解锁并行推理能力。
- **泛化性强**：在数学外任务（科学、数字游戏）上依然有效，且长轨迹节省更多。
- **推理效率提升**：顺序 token 减少直接对应延迟下降（估计在长轨迹上节省约 38% 时间）。

## 8. 不足与局限
- **硬件依赖**：实际 wall-clock 加速需要优化 KVCache 和高带宽 GPU 互联；受限于资源，论文中仅用近似估计，未实现最优部署。
- **并行度受限**：并行任务数受 GPU 数量限制，实验中使用单卡部署，并行带来的实际加速未充分体现。
- **训练数据质量依赖**：模型学到的并行策略受限于数据中的并行模式，可能无法发现超越训练分布的更优策略。
- **未有强化学习探索**：当前仅使用监督微调，作者指出未来可结合延迟感知的强化学习进一步优化。
- **实验统计性**：未提供误差条或多次运行的标准差，结果的可重复性论证不够充分。

（完）
