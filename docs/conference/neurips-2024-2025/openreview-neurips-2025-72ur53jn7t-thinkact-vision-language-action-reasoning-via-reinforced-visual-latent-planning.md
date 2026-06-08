---
title: "ThinkAct: Vision-Language-Action Reasoning via Reinforced Visual Latent Planning"
title_zh: ThinkAct：通过强化视觉隐式规划进行视觉-语言-动作推理
authors: "Chi-Pin Huang, Yueh-Hua Wu, Min-Hung Chen, Yu-Chiang Frank Wang, Fu-En Yang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=72UR53jN7T"
tags: ["query:mm-cot"]
score: 7.0
evidence: 面向长程规划的多模态推理，结合强化视觉隐式规划
tldr: 视觉-语言-动作推理任务需要长程规划和自适应执行，现有端到端方法缺乏显式推理。论文提出ThinkAct双系统框架，使用多模态大模型生成嵌入推理计划，并通过强化学习使计划与动作奖励对齐。实验表明该方法在复杂操作任务上显著优于端到端基线，实现了多步骤推理与动作执行的有效结合。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-72ur53jn7t/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1447, \"height\": 510, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-72ur53jn7t/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1442, \"height\": 637, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-72ur53jn7t/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1436, \"height\": 748, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-72ur53jn7t/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1448, \"height\": 869, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-72ur53jn7t/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 642, \"height\": 439, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-72ur53jn7t/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1362, \"height\": 242, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-72ur53jn7t/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1369, \"height\": 239, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-72ur53jn7t/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1444, \"height\": 582, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-72ur53jn7t/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1442, \"height\": 594, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-72ur53jn7t/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 757, \"height\": 275, \"label\": \"Table\"}]"
motivation: 现有VLA模型缺乏显式推理能力，难以进行多步骤规划和适应任务变化。
method: 提出双系统框架，训练多模态LLM生成嵌入推理计划，并利用强化学习对齐动作奖励。
result: 在多种机器人操作任务上取得显著性能提升，验证了长程多模态推理的有效性。
conclusion: 将多模态推理与强化视觉规划结合，能有效提升VLA模型的长程任务完成能力。
---

## Abstract
Vision-language-action (VLA) reasoning tasks require agents to interpret multimodal instructions, perform long-horizon planning, and act adaptively in dynamic environments. Existing approaches typically train VLA models in an end-to-end fashion, directly mapping inputs to actions without explicit reasoning, which hinders their ability to plan over multiple steps or adapt to complex task variations. In this paper, we propose ThinkAct, a dual-system framework that bridges high-level reasoning with low-level action execution via reinforced visual latent planning. ThinkAct trains a multimodal LLM to generate embodied reasoning plans guided by reinforcing action-aligned visual rewards based on goal completion and trajectory consistency. These reasoning plans are compressed into a visual plan latent that conditions a downstream action model for robust action execution on target environments. Extensive experiments on embodied reasoning and robot manipulation benchmarks demonstrate that ThinkAct enables few-shot adaptation, long-horizon planning, and self-correction behaviors in complex embodied AI tasks.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：现有视觉-语言-动作（VLA）模型通常采用端到端的方式，直接从多模态输入映射到低层动作，缺乏显式的推理步骤。这导致模型难以进行多步长程规划，也无法有效适应复杂任务变化或动态环境。
- **研究动机**：为了赋予VLA模型“先思考后行动”的能力，使其能够在物理环境中进行长程推理、自我纠错和少样本适应，从而提升在真实机器人操作和具身智能任务中的表现。
- **整体含义**：通过引入双系统架构（推理+执行），将高层规划与低层控制有机结合，并提出一种基于强化学习的视觉隐式规划方法，使模型能够生成与动作对齐的推理计划，进而指导执行。这为构建更具推理能力和适应性的具身智能体提供了可行路径。

## 2. 论文提出的方法论

- **核心思想**：采用**双系统架构**——一个多模态大语言模型（MLLM）负责进行长程推理并生成“视觉计划隐变量”（visual plan latent），另一个基于扩散Transformer的动作模型则以此隐变量为条件，预测具体的可执行动作。两个系统异步运行，实现“慢思考、快控制”。
- **关键技术细节**：
  1. **推理MLLM（$F_\theta$）**：基于Qwen2.5-VL 7B初始化。在接收到视觉观测$o_t$和语言指令$l$后，生成包含推理链和视觉计划轨迹（2D点序列$\tau$）的响应。
  2. **动作对齐的视觉反馈奖励**：
     - **目标奖励**$r_{goal}$：比较预测轨迹的起点/终点与真实检测得到的轨迹对应点之间的欧氏距离，鼓励模型预测正确的目标位置。
     - **轨迹奖励**$r_{traj}$：通过动态时间规整（DTW）距离衡量预测轨迹与演示轨迹的分布匹配程度，确保动作序列的物理合理性。
     - 总体奖励$r = 0.9r_{visual} + 0.1r_{format}$，其中$r_{visual} = 0.5 r_{goal} + 0.5 r_{traj}$，$r_{format}$为格式正确性奖励。
  3. **强化微调（GRPO）**：对MLLM应用组相对策略优化（Group Relative Policy Optimization），采样一组响应并根据上述奖励计算优势值，最大化目标函数同时通过KL散度约束避免偏离原始模型。
  4. **视觉计划隐变量$c_t$**：将推理MLLM生成的轨迹文本压缩为一个紧凑的隐变量，作为动作模型的额外条件输入。
  5. **动作模型（$\pi_\phi$）**：基于DiT（扩散Transformer）的策略网络，预训练于Open X-Embodiment数据集。在目标环境中微调时，冻结推理MLLM，仅更新状态编码器、隐投影器（Q-Former）和动作模型，通过行为克隆损失优化。
- **学习流程**：
  1. 冷启动SFT：让MLLM学习理解视觉轨迹并输出正确格式的推理和计划。
  2. 强化微调（GRPO）：使用动作对齐的视觉奖励优化MLLM的推理能力。
  3. 推理增强的动作适应：冻结MLLM，在目标环境数据上微调动作模型。

## 3. 实验设计

- **数据集**：
  - 训练：Open X-Embodiment（OXE）子集、Something-Something v2人类视频、RoboVQA、EgoPlan-IT、Video-R1-CoT、LLaVA-Video-178K等。
  - 评估：两个机器人操作基准（SimplerEnv、LIBERO）；三个具身推理基准（EgoPlan-Bench2、RoboVQA、OpenEQA）。
- **Benchmark与对比方法**：
  - **SimplerEnv**：包含Google-VM、Google-VA、Bridge-VM三种设置。对比Octo-Base、RT1-X、OpenVLA、DiT-Policy、TraceVLA、CoT-VLA、Magma。
  - **LIBERO**：含Spatial、Object、Goal、Long四个子任务。对比OpenVLA、DiT-Policy、TraceVLA、CoT-VLA、Magma。
  - **EgoPlan-Bench2**：多选QA准确率。对比GPT-4V、LLaVA-Video、InternVL2.5/3、NVILA、Qwen2.5-VL、Magma。
  - **RoboVQA**：BLEU分数。对比同上。
  - **OpenEQA**：LLM评分。对比同上。
- **实验充分性**：
  - 覆盖了多个不同难度和场景的具身任务（短程/长程操作、空间推理、零样本推理）。
  - 进行了消融实验（去掉目标奖励、轨迹奖励、同时去掉等），验证各组件贡献。
  - 分析了少样本适应能力（10-shot微调）和自我纠错能力（通过视频输入检测失败并重新规划）。
  - 对比了多种最新开/闭源模型，并报告了多次评估的平均结果（LIBERO上3个随机种子×100次试验）。

## 4. 资源与算力

- 论文明确说明：所有实验在 **16块 NVIDIA A100 GPU（80GB内存）** 上运行。
- 训练迭代数：
  - SFT冷启动：20K迭代，batch size 32，学习率1e-5。
  - GRPO强化微调：6K迭代，batch size 64，学习率1e-6，rollout size 5。
  - 动作模型预训练：120K迭代，batch size 256，学习率2e-5（在OXE 100K样本上）。
  - LIBERO进一步微调：75K迭代，batch size 128。
- 未提供总耗时或具体GPU小时数，但算力描述足够明确。

## 5. 实验数量与充分性

- 共涉及**5个主要基准**（SimplerEnv含3种设置、LIBERO含4个子任务、EgoPlan-Bench2含4个子类、RoboVQA 4个BLEU指标、OpenEQA 7个能力维度），每组均与其他方法进行了对比。
- 消融实验：分别移除目标奖励、轨迹奖励、两个同时移除、以及仅SFT基线，共5种配置，在3个基准上验证。
- 额外分析：少样本适应（3个场景×10-shot微调）、自我纠错（定性演示2例）、推理速度对比（与OpenVLA）。
- **充分性判断**：实验覆盖范围较广，消融设计合理，定量与定性结合。但未报告统计误差棒（仅提及3随机种子，未在表中展示方差），部分数据集（如EgoPlan-Bench2）仅报告总体准确率，缺乏更多性能细节。总体上实验充分且客观。

## 6. 论文的主要结论与发现

- ThinkAct在所有评估基准上均显著优于端到端基线（如DiT-Policy）和现有推理VLA方法（如CoT-VLA、Magma）。
- 动作对齐的视觉反馈奖励（目标+轨迹）对于长程推理至关重要，缺少任一部分都会导致性能下降。
- 强化微调（GRPO）相比纯SFT能显著提升推理质量和任务成功率（SFT冷启动比完整模型在SimplerEnv上低约3.7个点）。
- 通过推理生成的视觉计划隐变量能够有效指导下游动作模型在目标环境中的执行，并支持异步的“慢思考-快控制”范式。
- ThinkAct展示了**少样本适应**能力（仅10个演示即可在新任务上大幅超越基线），以及**自我反思与纠错**能力（通过观察短片段检测失败并重新规划）。

## 7. 优点

- **架构新颖**：双系统设计（推理MLLM+动作模型）融合了高层推理与低层控制，且允许异步运行，兼顾性能与实时性。
- **奖励设计巧妙**：动作对齐的视觉反馈（目标完成+轨迹分布匹配）无需任何中间人工标注，完全从视觉数据中自动推导，可扩展性强。
- **训练策略清晰**：多阶段（冷启动→强化微调→动作适应）逐步提升能力，各阶段目标明确。
- **实验全面**：涵盖操作和推理两大类任务，对比方法包含最新SOTA（如Magma、CoT-VLA），并做了充足的消融。
- **额外能力展示**：少样本适应和自我纠错是具身智能的关键能力，论文通过具体案例和量化实验证明了其有效性。

## 8. 不足与局限

- **继承MLLM的幻觉**：推理计划可能产生不正确的物体属性或空间关系，影响后续执行。虽然隐式规划在一定程度上缓解，但并没有彻底解决。
- **仅使用2D轨迹**：当前奖励仅基于2D端点轨迹，未包含接触力、力矩等精细信号，对复杂操作（如抓取松软物体）可能不足。作者也提到可以扩展但未实现。
- **推理速度开销**：相比端到端模型（如OpenVLA）平均增加17%的推理时间，虽带来显著性能提升，但在实时性要求极高的场景中可能成为瓶颈。
- **实验统计报告不够完整**：未在表中提供误差范围或置信区间，只提及“3 random seeds”但未呈现具体方差，影响对显著性的判断。
- **开放环境验证不足**：主要基于模拟环境（SimplerEnv、LIBERO）以及部分真实场景数据（OpenEQA），但未在真实机器人平台上进行部署测试，实际泛化性有待验证。
- **可复现性**：代码暂未开源（论文声明计划后公开），但训练数据均为公开数据集，训练细节描述较充分，可复现性较好。

（完）
