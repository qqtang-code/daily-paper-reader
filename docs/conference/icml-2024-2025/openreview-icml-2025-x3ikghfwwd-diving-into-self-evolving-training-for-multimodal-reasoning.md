---
title: Diving into Self-Evolving Training for Multimodal Reasoning
title_zh: 深入探究多模态推理的自进化训练
authors: "Wei Liu, Junlong Li, Xiwen Zhang, Fan Zhou, Yu Cheng, Junxian He"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=X3ikghfWwD"
tags: ["query:mm-cot"]
score: 9.0
evidence: 面向多模态推理的自进化训练，涉及链式思考数据
tldr: 自进化训练虽在文本推理中成功，但在多模态推理中却面临性能饱和。本文从强化学习视角重新审视这一范式，将训练方法、奖励模型和数据质量视为三个关键因素。通过在多模态推理任务上的实验，揭示了这些因素如何影响自进化效果，并提出了缓解饱和的策略。该工作为多模态环境下自动生成高质量链式思考数据提供了重要指导。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-x3ikghfwwd/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1599, \"height\": 528, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x3ikghfwwd/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 828, \"height\": 476, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x3ikghfwwd/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 855, \"height\": 500, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x3ikghfwwd/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 855, \"height\": 477, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x3ikghfwwd/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 855, \"height\": 499, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x3ikghfwwd/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 509, \"height\": 513, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x3ikghfwwd/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1605, \"height\": 704, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-x3ikghfwwd/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 856, \"height\": 533, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-x3ikghfwwd/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 860, \"height\": 410, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-x3ikghfwwd/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 803, \"height\": 446, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-x3ikghfwwd/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 801, \"height\": 370, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-x3ikghfwwd/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1244, \"height\": 453, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-x3ikghfwwd/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1481, \"height\": 1166, \"label\": \"Table\"}]"
motivation: 自进化训练在多模态推理中性能饱和，影响因素不明确。
method: 从强化学习视角解构自进化训练，系统分析三个关键因素。
result: 揭示了训练方法、奖励模型和数据质量对多模态推理自进化的影响。
conclusion: 提出的框架有助于突破多模态推理自进化训练的性能瓶颈。
---

## Abstract
Self-evolving training—where models iteratively learn from their own outputs—has emerged as a key approach for complex reasoning tasks, addressing the scarcity of high-quality chain-of-thought data. However, its effectiveness in multimodal reasoning, a domain more intricate than text-only reasoning, remains underexplored, and the understanding of critical factors in this training paradigm remains limited. Furthermore, a central challenge for this training method is performance saturation, which impedes further improvements and scalability. Inspired by reinforcement learning (RL), in this paper, we reframe self-evolving training for multimodal reasoning through the lens of RL, identifying three pivotal factors: $\textit{Training Method}$, $\textit{Reward Model}$, and $\textit{Prompt Variation}$. Through systematic analysis, we establish relatively optimal design principles that significantly enhance multimodal reasoning capabilities. Moreover, delving deeper into training dynamics, we uncover the roots of saturation and propose a new automatic balancing mechanism to mitigate this limitation. Building on these insights, we propose M-STaR (**M**ultimodal **S**elf-evolving **T**r**a**ining for **R**easoning), a framework that achieves consistent performance gains across models of varying sizes and diverse benchmarks. All resources will be made publicly available.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：多模态推理（如视觉数学推理）是智能体、机器人等应用的关键技能，但高质量链式思考（CoT）数据稀缺。自进化训练（模型迭代利用自身输出学习）在纯文本推理中已取得成功，但在更复杂的多模态领域中的有效性尚不明确，且面临性能饱和的挑战，阻碍了进一步改进和可扩展性。
- **整体含义**：本文从强化学习（RL）视角重新审视多模态推理的自进化训练，系统识别并分析了三个关键组成部分（训练方法、奖励模型、提示变化），旨在建立最优设计原则，并通过动态调整缓解性能饱和，从而提出一个统一、有效且可推广的框架 M-STaR。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：将自进化训练建模为 RL 框架，优化目标为最大化期望奖励：  
  $\pi_\theta = \arg\max_{\pi_\theta} \sum_i \mathbb{E}_{x,o\sim D, \hat{y}_i\sim\pi_\theta[\cdot|x,o]}[R(\hat{y}_i)]$。  
  实际采用离线解耦的两阶段流程：**生成**（当前策略生成响应）和**改进**（根据奖励筛选正样本，用 SFT 损失训练）。迭代进行，类似于 Rejection Fine-Tuning (RFT)。
- **关键技术细节**：
  - **训练方法**：提出 **Continuous Self-Evolving**，在每次迭代时不仅继承模型参数，还继承优化器状态和学习率调度器，使整个训练过程更连续、更接近在线 RL。同时探索迭代间隔（iteration interval）的影响。
  - **奖励模型**：首次为多模态推理训练 **Process Reward Model (PRM)**，对中间步骤进行奖励。奖励函数改为 $R(\hat{y}_i) = H(\mathbb{1}(a^* = \hat{a}_i) \times R_p(\hat{y}_i))$，其中 $R_p(\hat{y}_i) = \min(f(s_0^i), f(s_1^i), ..., f(s_m^i))$，使用 min 聚合。利用 Monte Carlo rollout 生成步骤级标注。对比 Top-K 选择与阈值过滤两种 H 操作。
  - **提示变化**：探索引入无标注提示（unlabeled prompts）的效果，使用加权投票生成伪标签，并与 PRM 结合筛选。研究何时混合无标签数据（0%、25%、50%、75% 训练进程时）。
  - **动态平衡**：提出 **Reward-Pass@K** 指标（在奖励模型排序的前 K 个响应中存在正确响应的比例），用于监控探索与利用的权衡。通过自动调整采样温度（在 0.3~1.6 范围、步长 0.1，每两次迭代调整一次，以验证集 Reward-Pass@2 最大化为目标）来维持探索能力，缓解饱和。
- **算法流程**（文字说明）：
  1. **预热阶段（Warm-up）**：使用包含正确答案的三元组（问题、图像、答案）引导模型生成 CoT，过滤正确样本后微调，获得初始策略。
  2. **迭代自进化**：在每个迭代中，a) 当前策略模型生成 16 个候选响应（温度为可调参数）；b) 使用 PRM 对正确响应（基于答案匹配）进行排序，取 Top-2 作为训练样本；c) 用 SFT 损失连续微调模型（继承优化器状态）。每两个迭代后根据验证集 Reward-Pass@2 自动调整温度。

### 3. 实验设计：使用了哪些数据集 / 场景，它的 benchmark 是什么，对比了哪些方法

- **数据集**：
  - **训练集**：MathV360K（30 万样本），下采样一半（180K）作为标注集，另一半作为无标注集（隐藏答案）。
  - **验证集**：从 MathV360K 无标注部分中抽取 750 条作为域内（ID）测试集，另留 250 条作为全局验证集。
  - **测式基准**：
    - 域内：MathV360K 测试集（750 条）。
    - 域外（OOD）：**MathVista**（涉及 VQA、图问答、科学问答等）；额外还使用 **M3CoT**、**MMStar**（剔除感知子任务，得到推理子集 MMStar-R）、**MMBench**（Dev 集 v1.1，同样剔除感知子任务 MMBench-R）、**AI2D**。
- **对比方法**：
  - 基线：原始模型（Base）、预热的模型（+warmup）、标准 SFT、**Iterative RFT**、**ReST EM**。
  - 本文提出的变体：**Continuous Self-Evolving**、**+PRM Re-Rank**（添加 PRM 重排）、**M-STaR**（最终版，含动态温度调整）。
- **模型**：主要探索基于 **MiniCPM-V-2.5 (8B)**，并在 **Phi-3.5-Vision (4B)** 和 **InternVL2 (2B)** 上验证泛化性。

### 4. 资源与算力：如果文中有提到，请总结使用了多少算力（GPU 型号、数量、训练时长等）。若未明确说明，也请指出这一点。

- 文中未明确说明使用的 GPU 型号、数量及训练时长等具体算力信息。仅提到训练超参数：学习率 1e-6，batch size 128，训练 10K steps，采样温度设为 1.0（固定温度实验），每问题采样 16 个响应。对于动态调整温度版本，同样为 10K steps。算力消耗未量化。

### 5. 实验数量与充分性：大概做了多少组实验（如不同数据集、消融实验等），这些实验是否充分、是否客观、公平

- **实验数量**：大量消融与对比实验。
  - 训练方法：比较了 Iterative RFT、ReST EM、不同间隔的 Continuous Self-Evolving（6.25%~100%），共约 7 种设置。
  - 奖励模型：对比无 PRM、随机选择、PRM + Top-K（K=1,2,4）、阈值过滤等，至少 5 种。
  - 提示变化：对比无标注数据不同混入时机（0%,25%,50%,75%），以及是否使用 PRM 和 oracle 信号，共约 10 种。
  - 动态调整：对比固定温度与自适应温度（M-STaR），并在 3 个模型上验证。
  - 最终框架在 5 个基准（MathVista、M3CoT、MMStar-R、MMBench-R、AI2D）、3 种模型上报告结果。
- **充分性**：实验设计较为系统，覆盖了三个关键因素的不同选择，并单独研究了动态饱和问题。消融实验全面，对比方法具有代表性（如 ReST EM、Iterative RFT 等经典方法）。在多个模型尺度（2B/4B/8B）和多个基准上验证，增强了结论的可信度。实验设计较为客观公平，控制变量良好（如固定基础模型、训练步数等）。

### 6. 论文的主要结论与发现

- **训练方法**：Continuous Self-Evolving（继承模型与优化器）优于传统 Iterative RFT 和 ReST EM，且迭代间隔为 25%（45K 查询）时效果最佳。
- **奖励模型**：PRM 作为重排器（Reranker）比作为验证器（Verifier）更有效；Top-2 选择在质量与多样性间取得最佳平衡，优于随机选择或阈值过滤。
- **提示变化**：加入无标注数据仅在具有完美奖励信号（oracle）时才可能有益，否则由于 PRM 泛化不足反而伤害性能；最佳时机是从训练开始即混合（0% 时机）。
- **动态平衡**：训练过程中模型探索能力（Pass@K）持续下降，导致性能饱和；通过自动调整温度维持 Reward-Pass@K 指标，可有效延缓饱和并持续提升性能。
- **最终框架 M-STaR** 在多个模型和基准上一致超越基线，尤其在大模型（8B）上提升显著（MathVista +6.9 百分点），小模型（2B）部分场景提升有限。

### 7. 优点：方法或实验设计上有哪些亮点

- **创新性**：将自进化训练系统解构为三个关键因素，并提出 Continuous Self-Evolving 与自动温度调整机制，首次在多模态领域训练 PRM 并揭示其重排能力优于验证能力。
- **实验严谨性**：通过大规模消融实验排除混淆因素，每个因素独立控制变量，并在不同尺寸模型上验证泛化性；引入 Reward-Pass@K 这一新颖监控指标，动态指导训练。
- **实用性**：提出的 M-STaR 框架无需额外人工标注，仅利用模型自身生成和简单规则，即可在多模态推理任务上取得显著提升，易于复现和应用。
- **公开资源**：全部资源（代码、数据等）将公开，促进可复现研究。

### 8. 不足与局限：包括实验覆盖、偏差风险、应用限制等

- **实验覆盖**：仅限于数学推理为主的基准（MathVista、AI2D 等），未涉及更开放的多模态任务（如视觉常识推理、图文对话等）；模型也仅局限于开源 LMM（MiniCPM-V、Phi-3.5、InternVL2），未在更大模型（如 LLaMA-NeXT-V 或 Qwen-VL）上验证。
- **偏差风险**：
  - PRM 训练数据使用 Monte Carlo rollout 从模型自身生成，可能引入自洽偏差；PRM 作为重排器时，其质量依赖于初始模型能力，对于小模型可能效果有限。
  - 温度自动调整基于验证集 Reward-Pass@2 最大化，可能对验证集过拟合，泛化性需进一步验证。
- **应用限制**：
  - 方法依赖于答案标注（ground-truth 答案）进行初始筛选，对于开放式任务（无标准答案）不适用。
  - 无标注数据的利用目前效果不佳（仅 oracle 信号有益），实际应用场景中可能难以获取高质量伪标签。
  - 动态温度调整需要额外的验证集评估计算，增加一定开销。
- **可扩展性**：小模型（2B）上提升有限甚至部分基准下降，表明方法对模型容量有一定要求，在小模型上可能无法充分自我进化。

（完）
