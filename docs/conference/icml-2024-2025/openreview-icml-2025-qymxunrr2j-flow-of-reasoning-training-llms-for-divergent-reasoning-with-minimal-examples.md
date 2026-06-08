---
title: "Flow of Reasoning: Training LLMs for Divergent Reasoning with Minimal Examples"
title_zh: 推理流：用最少示例训练大语言模型进行发散推理
authors: "Fangxu Yu, Lai Jiang, Haoqiang Kang, Shibo Hao, Lianhui Qin"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=qyMxunrR2j"
tags: ["query:mm-cot"]
score: 6.0
evidence: 多步推理但侧重多样性
tldr: 现有多步推理方法只关注准确性而忽视了解决方案的多样性。本文提出Flow of Reasoning (FoR)，通过高效训练使大语言模型在少量示例下生成多样化的推理路径，在保证推理质量的同时提升多样性，适用于科学发现等需要创造力的场景。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-qymxunrr2j/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1756, \"height\": 747, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qymxunrr2j/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1691, \"height\": 486, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qymxunrr2j/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 872, \"height\": 316, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qymxunrr2j/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1653, \"height\": 838, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qymxunrr2j/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 862, \"height\": 560, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qymxunrr2j/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1733, \"height\": 699, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qymxunrr2j/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1696, \"height\": 871, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qymxunrr2j/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1770, \"height\": 1568, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qymxunrr2j/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1746, \"height\": 1159, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qymxunrr2j/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1745, \"height\": 721, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qymxunrr2j/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1775, \"height\": 1270, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qymxunrr2j/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1734, \"height\": 849, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qymxunrr2j/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1733, \"height\": 1045, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qymxunrr2j/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1695, \"height\": 1101, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qymxunrr2j/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1754, \"height\": 1366, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qymxunrr2j/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1716, \"height\": 758, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-qymxunrr2j/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1728, \"height\": 882, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qymxunrr2j/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 821, \"height\": 555, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qymxunrr2j/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 760, \"height\": 482, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qymxunrr2j/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 800, \"height\": 388, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qymxunrr2j/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1399, \"height\": 310, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qymxunrr2j/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 767, \"height\": 307, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qymxunrr2j/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 858, \"height\": 411, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qymxunrr2j/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1213, \"height\": 271, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qymxunrr2j/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 443, \"height\": 241, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qymxunrr2j/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1364, \"height\": 503, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qymxunrr2j/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1602, \"height\": 329, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qymxunrr2j/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 842, \"height\": 198, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qymxunrr2j/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1101, \"height\": 401, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qymxunrr2j/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 828, \"height\": 637, \"label\": \"Table\"}]"
motivation: 现有方法只关注推理准确性，忽略了解决方案的多样性。
method: 提出Flow of Reasoning（FoR），一种追求多样性的高效训练方法。
result: 在保持推理质量的同时显著提升了输出多样性。
conclusion: FoR为需要多样化解的问题提供了有效训练范式。
---

## Abstract
The ability to generate diverse solutions to a given problem is a hallmark of human creativity. This divergent reasoning is also crucial for machines, enhancing their robustness and enabling them to assist humans in many applications such as scientific discovery. However, existing approaches to multi-step reasoning with large language models (LLMs) have mostly focused only on reasoning accuracy, without further discovering more diverse valid solutions. For example, supervised fine-tuning improves reasoning quality but requires vast labeled data, while reward-maximizing reinforcement learning finds top-reward solutions while neglecting the solution diversity. To fill this gap, we propose Flow of Reasoning (FoR), an efficient diversity-seeking LLM finetuning method aimed at improving reasoning quality and diversity with minimal data. FoR formulates multi-step LLM reasoning as a Markovian flow on a DAG-structured reasoning graph. This formulation allows us to incorporate and adapt principled GFlowNet approaches, for finetuning LLMs to sample divergent paths with probabilities proportional to the (unnormalized) reward of target problems. Extensive experiments show that, with limited training examples (e.g., 15 examples), FoR enables the discovery of diverse, creative, high-quality solutions, greatly outperforming a wide range of existing inference and training methods across six challenging reasoning tasks, including BlocksWorld (embodied reasoning), Game24 (math puzzle solving), Rubik's Cube (spatial reasoning), 1D-ARC (abstraction reasoning), GSM8k (math reasoning), and ProntoQA (logical reasoning). Code is available at https://github.com/Yu-Fangxu/FoR.

---

## 论文详细总结（自动生成）

好的，以下是基于您提供的论文文本生成的结构化、深入、客观的中文总结。

---

## 论文总结：Flow of Reasoning: Training LLMs for Divergent Reasoning with Minimal Examples

### 1. 核心问题与整体含义（研究动机和背景）

- **问题**：现有的大语言模型（LLM）多步推理方法（如 CoT、ToT 以及 SFT、PPO 等微调方法）主要关注**推理准确性**（即找到一条正确解），而忽视了**解决方案的多样性**（即生成多条不同但正确的推理路径）。这在需要创造力、鲁棒性和科学发现等场景中至关重要。
- **背景**：监督微调（SFT）需要大量标注数据，且容易坍缩到单一模式；强化学习（如 PPO）最大化奖励，同样牺牲多样性。基于搜索的推理（如 ToT、RAP）推理成本高，且受限于预训练模型能力。
- **动机**：提出一种**数据高效**（仅需少量示例，如 15 条）且能生成多样化、高质量推理路径的训练方法，填补现有方法在“发散推理”任务上的空白。

### 2. 论文提出的方法论

- **核心思想**：将多步 LLM 推理建模为**有向无环图（DAG）上的马尔可夫流**。每个推理步骤对应图中的一个边（动作），状态为节点，完整轨迹为从初始状态到终止状态的路径。目标是学习一个前向策略 \( P_F(s_t|s_{t-1}) \)，使得采样出的轨迹概率正比于该轨迹终止状态的奖励 \( R(s_n) \)（即未归一化的奖励分布），而非只采样最高奖励路径。
- **关键技术细节**：
    - **流网络视角**：定义轨迹流函数 \( F(\tau) \)，要求所有终止状态的流等于奖励：\( F(s_n) = R(s_n) \)。
    - **轨迹平衡（Trajectory Balance）损失**：利用 GFlowNet 的轨迹平衡目标训练策略。损失函数如下：
        \[
        \ell(\tau;\theta, g) = \left( \log \frac{Z(s_0,g) \prod_{t=1}^n P_F(s_t|s_{t-1};\theta,g)}{R(s_n) \prod_{t=1}^n P_B(s_{t-1}|s_t;\theta,g)} \right)^2
        \]
        其中 \( Z \) 为总流（正则化常数），\( P_B \) 为后向策略（设为均匀分布）。通过最小化轨迹上 \( \Phi(\tau;\theta) \) 的方差来训练，避免显式学习 \( Z \)。
    - **LLM 参数化**：前向策略由 LLM 参数化，输入当前状态和任务目标，输出动作概率。动作和状态用自然语言表示。
    - **高效探索策略**：结合多种采样方式：
        - 在线策略（on-policy）和温度放缩变体；
        - 离线策略：优先回放缓冲区（Prioritized Replay Buffer）；
        - \( \epsilon \)-采样：以概率 \( \epsilon \) 随机采样动作；
        - **改进的局部搜索**（Local Search）：从当前批次中选取最高奖励轨迹，截断后部分并用随机策略重构，收集更高奖励的轨迹加入回放缓冲区，提高探索效率。

### 3. 实验设计

- **数据集/场景**：六个具有挑战性的推理任务，覆盖多种推理类型：
    1.  **BlocksWorld**（具身推理）：操作积木达到目标配置。
    2.  **Game24**（数学谜题）：用四个数和四则运算组合成24。
    3.  **Rubik's Cube**（空间推理）：恢复打乱的2x2魔方。
    4.  **1D-ARC**（抽象推理）：推断一维网格变换规则。
    5.  **GSM8K**（数学推理）：小学应用题。
    6.  **PrOntoQA**（逻辑推理）：基于本体推理真值判断。
- **基准方法**：
    - 提示方法：CoT、ToT（BFS/DFS）、GoT、RAP、XoT、Hypothesis Search 等。
    - 微调方法：SFT（含多种解码策略：温度采样、核采样、典型采样、多样束搜索）、PPO、GFN-CoT、STaR。
    - 先进模型：OpenAI O1-mini、O1-preview、GPT-4o。
- **评估指标**：
    - **准确性（Accuracy）**：至少一个正确解的比例。
    - **多样性（Diversity）**：对有解问题，平均不同正确解的数量。
    - **创造力（Creativity）**：该方法独有、其他方法未发现的正确解比例。
    - **运行时间（Runtime）**。

### 4. 资源与算力

- **硬件**：单张 NVIDIA A100 80GB GPU。
- **训练时间**（以 BlocksWorld 6-step 为例）：
    - SFT：约 196 秒
    - PPO：约 1741 秒
    - **FoR**：约 6833 秒
- **说明**：论文明确给出了 BlocksWorld 任务的训练时间，其他任务类似但未逐一列出。FoR 训练成本较高，因需在线探索与环境交互。

### 5. 实验数量与充分性

- **数量**：在全部6个任务上进行了实验，每个任务均与至少6种以上基线方法对比。此外，还进行了：
    - **消融实验**（BlocksWorld）：移除局部搜索、中间奖励、回放缓冲区、\( \epsilon \)-采样，分析各组件贡献。
    - **不同模型规模与族**：在 Llama3-8B/70B、Qwen2.5-7B/72B、InternLM2.5-7B 上测试。
    - **数据效率实验**：变化训练样本量（15, 30, 45, 60）对比 FoR 与 SFT。
    - **超参数分析**：中间奖励权重 \( \lambda \) 的影响。
    - **OOD（分布外）泛化实验**：BlocksWorld 上跨步数迁移（2->4步, 4->6步）。
- **充分性与公平性**：实验设计较为全面，覆盖了多个维度；基线选择多样，包括最新强模型（O1系列）；指标多样（准确率、多样性、创造力）。公平性方面，微调方法均使用相同基座模型（Llama3-8B）和相同训练数据。标准偏差在多次运行中报告。

### 6. 主要结论与发现

- **主结果**：FoR 在所有六个任务上**准确率和多样性均显著优于所有基线**，尤其在 Limited 数据（15个示例）下表现突出。
    - 例如 BlocksWorld 6-step：FoR 准确率78.44%，多样性1.33，创造力9.52%；而 SFT 最优（+核采样）仅42.08%准确率、1.12多样性、0%创造力。
    - 其他任务同样显著领先，如 Rubik's Cube 准确率从4.92%提升至10.87%，多样性从1.00提升至1.29。
- **数据效率**：FoR 在很少样本下（15个）即可获得高准确率和多样性，且随样本量增加持续提升，而 SFT 提升有限。
- **消融证实**：局部搜索、中间奖励、回放缓冲区对性能贡献显著；中间奖励最重要，移除后准确率下降50%以上。
- **泛化能力**：OOD 设置下，FoR 泛化远好于 SFT 和 CoT（如2-step训到4-step测试，准确率71.43% vs 14.28%）。
- **与强模型对比**：O1-mini 在准确性上很强（如 Game24 94%），但多样性仍不如 FoR（未报告多样性，但从创造力看FoR更高）。

### 7. 优点

- **方法创新**：首次将 GFlowNet 的高效多样化采样思想系统性地引入 LLM 多步推理任务，提出基于轨迹平衡的微调框架。
- **数据高效**：仅需极少标注示例（15条），即可训练出同时具备高准确率和高多样性的模型。
- **探索策略新颖**：融合局部搜索、回放缓冲区、\( \epsilon \)-采样等多种探索机制，有效解决 LLM 在线采样效率低的问题。
- **广泛验证**：在六个差异显著的推理任务、多种模型规模（8B~72B）、多种模型族上均取得一致提升，实验扎实。
- **开源**：代码已公开，便于复现和后续研究。

### 8. 不足与局限

- **计算成本**：在线采样和局部搜索导致训练时间远高于 SFT（约35倍），在资源受限场景可能不实用。
- **长期推理挑战**：论文指出 LLM 在长程推理上仍较弱，FoR 在处理超长步数问题时可能效果下降，未来需结合 MCTS 等外部规划。
- **离线轨迹依赖**：在 Game24 等空间大的任务中，FoR 仍依赖离线生成的正确轨迹作为增强，不完全自主探索。
- **多样性度量局限**：GSM8K 的多样性度量采用人工标注和 GPT-4o 自动判别，可能存在主观性；其他任务多样性仅统计语义不同正确解，未深入分析差异类型。
- **应用限制**：当前方法仅针对步骤可拆解、奖励可定义的多步推理问题，对于更开放、无明确终止状态的创造性任务（如写故事）尚未探索。
- **公平性注意**：与 O1 系列对比时，O1 未报告多样性，且 O1 的内部训练数据可能已包含类似任务，比较需谨慎解读。

（完）
