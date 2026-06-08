---
title: Re-ranking Reasoning Context with Tree Search Makes Large Vision-Language Models Stronger
title_zh: 通过树搜索重排序推理上下文增强大型视觉语言模型
authors: "Qi Yang, Chenghao Zhang, Lubin Fan, Kun Ding, Jieping Ye, Shiming Xiang"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=DJcEoC9JpQ"
tags: ["query:multimodal"]
score: 8.0
evidence: 多模态检索增强生成，通过推理上下文丰富和树搜索重排序增强视觉语言模型
tldr: 多模态检索增强生成中存在知识匮乏和检索结果不稳定等问题。本文提出RCTS框架，通过自洽评估机制构建富含推理模式的知识库，并采用蒙特卡洛树搜索进行重排序。在视觉问答任务上，RCTS显著提升了大型视觉语言模型的回答准确性和鲁棒性。该方法为多模态模型的知识增强提供了新途径。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-djceoc9jpq/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 827, \"height\": 458, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-djceoc9jpq/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1617, \"height\": 474, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-djceoc9jpq/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1567, \"height\": 615, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-djceoc9jpq/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1568, \"height\": 480, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-djceoc9jpq/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 860, \"height\": 383, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-djceoc9jpq/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1577, \"height\": 792, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-djceoc9jpq/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1783, \"height\": 444, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-djceoc9jpq/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1783, \"height\": 484, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-djceoc9jpq/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1782, \"height\": 483, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-djceoc9jpq/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1770, \"height\": 531, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-djceoc9jpq/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1803, \"height\": 74, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-djceoc9jpq/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1777, \"height\": 70, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-djceoc9jpq/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1770, \"height\": 72, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-djceoc9jpq/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1739, \"height\": 1487, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-djceoc9jpq/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1737, \"height\": 2017, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-djceoc9jpq/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1748, \"height\": 1851, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-djceoc9jpq/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1746, \"height\": 2153, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-djceoc9jpq/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1703, \"height\": 2195, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-djceoc9jpq/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1738, \"height\": 2176, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-djceoc9jpq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 887, \"height\": 307, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-djceoc9jpq/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1703, \"height\": 628, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-djceoc9jpq/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 854, \"height\": 375, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-djceoc9jpq/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 838, \"height\": 291, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-djceoc9jpq/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 821, \"height\": 271, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-djceoc9jpq/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 809, \"height\": 203, \"label\": \"Table\"}]"
motivation: 现有视觉语言模型在检索增强问答中面临知识匮乏和响应不稳定问题。
method: 构建推理上下文知识库并采用蒙特卡洛树搜索重排序检索结果。
result: 在VQA任务上显著提升性能，展示了推理上下文的重要性。
conclusion: 推理上下文和树搜索有效增强了多模态检索增强生成。
---

## Abstract
Recent advancements in Large Vision Language Models (LVLMs) have significantly improved performance in Visual Question Answering (VQA) tasks through multimodal Retrieval-Augmented Generation (RAG). However, existing methods still face challenges, such as the scarcity of knowledge with reasoning examples and erratic responses from retrieved knowledge. To address these issues, in this study, we propose a multimodal RAG framework, termed RCTS, which enhances LVLMs by constructing a Reasoning Context-enriched knowledge base and a Tree Search re-ranking method. Specifically, we introduce a self-consistent evaluation mechanism to enrich the knowledge base with intrinsic reasoning patterns.  We further propose a Monte Carlo Tree Search with Heuristic Rewards (MCTS-HR) to prioritize the most relevant examples.  This ensures that LVLMs can leverage high-quality contextual reasoning for better and more consistent responses. Extensive experiments demonstrate that our framework achieves state-of-the-art performance on multiple VQA datasets, significantly outperforming In-Context Learning (ICL) and Vanilla-RAG methods. It highlights the effectiveness of our knowledge base and re-ranking method in improving LVLMs.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义

- **研究动机与背景**：大型视觉语言模型（LVLMs）在视觉问答（VQA）任务中表现出色，但仍然存在幻觉问题：一是生成与真实世界事实不一致的内容（如错误陈述历史事件）；二是响应与用户指令或问题对齐不佳。为了增强模型对指令的准确把握，现有方法尝试通过多模态检索增强生成（RAG）引入外部知识，或通过上下文学习（In-Context Learning, ICL）加入示例对。然而，现有RAG方法仍面临两个主要挑战：(i) 检索到的示例常以固定的问答格式呈现，缺乏内在的推理步骤，难以让模型捕获潜在逻辑模式；(ii) 检索到的示例可能不一致，不能保证正向效果。为此，论文提出一个名为RCTS（Reasoning Context with Tree Search）的多模态RAG框架，旨在构建一个富含推理上下文的知识库，并通过树搜索方法对检索结果进行重排序，从而提升LVLMs回答质量。

- **整体意义**：论文致力于将LVLMs从“仅仅知道”（known）提升到“更好理解”（better understood），即通过提供高质量的推理上下文示例，使模型不仅知道答案，还能掌握其背后的推理方式。

## 2. 论文提出的方法论

### 核心思想
RCTS框架包含三个核心模块：
1. **知识库构建**：利用自洽评估机制为问答对自动生成推理上下文，丰富知识库。
2. **混合嵌入检索**：采用文本和视觉的混合嵌入，从知识库中检索最相关的前N个样本。
3. **蒙特卡洛树搜索重排序**：基于启发式奖励函数，对检索到的样本进行重排序，选出最优的K个作为上下文示例，以最大化答案准确率。

### 关键技术细节

#### (1) 推理上下文生成（Self-consistent Reasoning Context Generation）
- 对每个问答对 `(Q_kb, A_kb)`，用LVLM先生成N_c个候选推理上下文 `{C_i}`。
- 每个候选上下文 `C_i` 与问题 `Q_kb` 拼接作为输入，让LVLM预测答案，得到N_p个预测答案。
- 使用规则评价器计算预测答案与真实答案 `A_kb` 之间的一致性得分。
- 选择得分最高的候选上下文作为该问答对的关联推理上下文.

#### (2) 知识检索（Hybrid Retrieval）
- 对用户查询 `(I_u, Q_u)`，用文本编码器 `F_L` 和图像编码器 `F_I` 得到文本和图像嵌入。
- 将两种嵌入按Token级拼接，得到混合嵌入 `E_u = [E_Tu, E_Iu]`。
- 知识库中每个样本也采用相同的混合嵌入 `E_i`。
- 计算相关性分数 `r(E_u, E_i)`：对用户查询的所有Token与知识库样本的所有Token做最大点积求和。
- 选择Top-N最相关的问答对作为候选动作空间。

#### (3) 蒙特卡洛树搜索与启发式奖励（MCTS-HR）
- **动作空间**：由Top-N个检索到的样本构成，每个样本附带归一化相似度得分 `s_i`。
- **节点选择**：利用上置信界（UCT）公式平衡探索与利用。
- **动作采样**：在扩展时，从有效动作空间中按概率 `P(a_i) = s_i / sum_{j} s_j` 采样下一个示例，直至达到最大深度K。
- **奖励函数**：由两部分组成：
  - **自洽启发式奖励（Self-consistency Heuristic Reward）**：将用户查询与当前分支的K个上下文组合，生成预测响应 `y_i`；然后多次重复生成答案（基于预测推理上下文 `C_i`），计算与原始预测答案 `A_i` 一致的比例。
  - **互启发式奖励（Mutual Heuristic Reward）**：从动作空间中选Nm个样本，将当前分支的预测答案作为上下文，让LVLM回答这些样本问题，计算预测答案与真实答案一致的比例。
  - 最终奖励 `Q_i = α·Q_S,i + (1-α)·Q_M,i`，其中α为权重（默认0.2）。
- **反向传播**：将奖励值向上传播更新父节点价值，父节点的新价值为原有均值和最优子节点价值的均值。
- **终止条件**：达到最大滚动次数（rollouts）或满足早停策略（当零炮响应与分支响应一致时停止）。

#### 算法流程（文字说明）
1. 初始化根节点（零炮响应）。
2. 利用混合嵌入检索Top-N样本作为动作空间。
3. 利用UCT选择节点，从动作空间中采样动作（即一个示例）扩展树。
4. 当达到深度K时，将路径上的K个示例与用户查询拼接形成K-shot提示，生成响应。
5. 利用自洽奖励和互奖励计算分数，反向传播更新树节点价值。
6. 重复步骤3-5，直至满足终止条件。
7. 输出最终重排序后的K个示例及答案。

## 3. 实验设计

### 数据集
- **推理VQA数据集**：ScienceQA (test 4241个样本, trainval 16967个样本)；MMMU (Dev 150个, Val 900个)；MathV (testmini 304个, test 2736个)。
- **非推理VQA数据集**：VizWiz (val 4319, train 20523)；VSR-MC (test 1181, trainval 4440)。
- 训练集用于构建知识库，测试集用于评估，且保证评估集和知识库无重叠。

### 基准方法
- **Zero-Shot**：无示例，直接回答问题。
- **ICL (随机检索)**：随机从知识库中选择示例。
- **Vanilla-RAG**：基于混合嵌入相似度检索Top-K示例。
- **RCTS (本文方法)**：使用推理上下文和MCTS重排序。

### 模型
- Qwen2-VL (2B / 7B)
- InternVL-2 (8B)

### 评估指标
- 准确率（Accuracy）。

### 实验结果概述
- 在三个推理VQA数据集上，RCTS超过所有基线，例如在ScienceQA上Qwen2-VL(2B)从71.94%提升至78.99%，Qwen2-VL(7B)从86.68%提升至91.44%。
- 在非推理数据集上也有一致提升（VizWiz +1.61%, VSR-MC +3.05%）。

## 4. 资源与算力

- 论文中提到：对于超过7B参数的LVLM，采用4-bit量化（AWQ）在单个NVIDIA 4090 24GB GPU上运行。
- 冻结的BERT-base和ViT-L + 2层MLP作为编码器（来自PreFLMR）。
- 未明确说明总训练时长或GPU数量，但指出模型是免费（训练-免费）的，仅需进行推理和重排序，无需额外训练知识库或模型。因此主要开销在MCTS的多次滚动（默认10次）。推理和MCTS均在单卡完成，但论文未量化具体时间。

## 5. 实验数量与充分性

- 实验覆盖**5个数据集**（ScienceQA, MMMU, MathV, VizWiz, VSR-MC）。
- 对比了**3个基线**（Zero-shot, ICL, Vanilla-RAG）在**3种不同规模/类型的LVLM**上（Qwen2-VL 2B / 7B, InternVL-2 8B），共得到多个性能表格（表2、表3）。
- 进行了详细的**消融实验**：
  - 关键组件（推理上下文、MCTS）的单独与组合效果（表4）。
  - 奖励策略（自洽奖励、互奖励、混合奖励）比较（图5a）。
  - 滚动次数（rollouts）的影响（图5b）。
  - 权重参数α的敏感性分析（表5）。
  - 推理上下文生成质量（表6）：评估生成推理上下文后预测答案与真实答案的一致性。
- 定性分析：提供了MCTS重排序过程的可视化案例（图6及附录D多个例子），显示重排序如何改善答案。
- 实验设计较为充分，对比公平（相同模型、相同知识库、相同种子设置）。但部分数据集（如MMMU）只有150个开发样本用于评估，样本量较小，可能存在统计波动。

## 6. 论文的主要结论与发现

1. 推理上下文的自动生成显著提升了LVLMs对示例推理模式的理解，使模型从“已知”转向“更好理解”。
2. 基于MCTS的启发式重排序能有效筛选出最有益的上下文示例，缓解随机检索带来的不稳定问题。
3. 在多个推理和非推理VQA数据集上，RCTS一致优于Zero-Shot、ICL和Vanilla-RAG，验证了框架的通用性和有效性。
4. 混合重排序奖励（自洽+互）优于单一奖励，表明结合多个评价视角可获得更准确的选择。
5. 推理上下文生成的质量很高（在ScienceQA上达100%），验证了自洽评估机制的有效性。

## 7. 优点

- **创新性**：将马尔可夫决策过程（MCTS）与启发式奖励引入多模态RAG的示例重排序，是一个新颖尝试。
- **无训练开销**：整个框架无需微调LVLM或知识库，仅需推理计算，易于部署和扩展。
- **自动化程度高**：推理上下文自动生成，无需人工标注。
- **实验充分**：涵盖了多个数据、多个模型、多种消融，结果可靠。
- **可视化分析**：通过附录D提供了大量MCTS分支可视化，直观展示重排序改善过程，有助于理解机制。

## 8. 不足与局限

1. **依赖知识库质量**：检索到的示例质量仍取决于知识库中是否存在相似样本。如果知识库缺乏相关示例，RCTS也无法提供有效增益（论文在附录D的图16展示了该类失败案例）。
2. **计算开销**：MCTS需要多次滚动（默认10次），每次滚动需调用多次LVLM生成奖励，带来额外推理时间，对实时应用可能不友好。
3. **数据集规模限制**：MMMU开发集仅150个样本，实验结果可能存在偏差；MathV testmini也只有304个样本。
4. **领域覆盖有限**：所有数据集集中在英语、科学、数学、空间等，未验证其他语言或领域（如医学、法律）的泛化性。
5. **奖励函数权重α设置**：虽然通过分析确定了默认值0.2，但针对不同任务可能需要自适应调整，论文未探讨自动调参。
6. **没有与其他先进重排序方法对比**：仅比较了简单的Top-K检索和随机检索，缺少与其他重排序策略（如基于BERT的重新排名）的对比。

（完）
