---
title: "A*-Thought: Efficient Reasoning via Bidirectional Compression for Low-Resource Settings"
title_zh: "A*-思考：通过双向压缩实现低资源环境下的高效推理"
authors: "Xiaoang Xu, Shuo Wang, Xu Han, Zhenghao Liu, Huijia Wu, Pei Pei Li, Zhiyuan Liu, Maosong Sun, Zhaofeng He"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=uvyr9bYwL6"
tags: ["query:mm-cot"]
score: 8.0
evidence: 通过树搜索压缩推理链
tldr: "现有的推理模型通过延长思考链提升性能，但导致效率低下。本文提出A*-Thought框架，将推理过程建模为搜索树，利用A*算法双向压缩，从长链中提取核心思考步骤。实验表明，该方法在保持推理性能的同时显著降低计算开销，尤其适用于低资源环境。该工作为高效推理链压缩提供了新范式。"
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-uvyr9bywl6/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1285, \"height\": 371, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uvyr9bywl6/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1430, \"height\": 933, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uvyr9bywl6/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1409, \"height\": 338, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uvyr9bywl6/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1411, \"height\": 358, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uvyr9bywl6/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1411, \"height\": 359, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uvyr9bywl6/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1402, \"height\": 380, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uvyr9bywl6/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1450, \"height\": 774, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uvyr9bywl6/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 578, \"height\": 447, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uvyr9bywl6/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 893, \"height\": 703, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uvyr9bywl6/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 703, \"height\": 493, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-uvyr9bywl6/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1438, \"height\": 1083, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uvyr9bywl6/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1358, \"height\": 763, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uvyr9bywl6/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1441, \"height\": 264, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uvyr9bywl6/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1451, \"height\": 258, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uvyr9bywl6/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1439, \"height\": 700, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uvyr9bywl6/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1440, \"height\": 811, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uvyr9bywl6/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1441, \"height\": 959, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uvyr9bywl6/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1440, \"height\": 953, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uvyr9bywl6/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1211, \"height\": 341, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uvyr9bywl6/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1448, \"height\": 362, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uvyr9bywl6/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1434, \"height\": 1129, \"label\": \"Table\"}]"
motivation: 长推理链导致计算效率低下，现有压缩方法常导致性能下降。
method: "将推理过程形式化为搜索树，结合A*搜索算法识别关键推理节点。"
result: 在低资源设置下，该方法在保持性能的同时显著减少了推理时间。
conclusion: "A*-Thought实现了推理链的高效压缩，平衡了性能与效率。"
---

## Abstract
Large Reasoning Models (LRMs) achieve superior performance by extending the thought length. However, a lengthy thinking trajectory leads to reduced efficiency. Most of the existing methods are stuck in the assumption of overthinking and attempt to reason efficiently by compressing the Chain-of-Thought, but this often leads to performance degradation. To address this problem, we introduce A*-Thought, an efficient tree search-based unified framework designed to identify and isolate the most essential thoughts from the extensive reasoning chains produced by these models. It formulates the reasoning process of LRMs as a search tree, where each node represents a reasoning span in the giant reasoning space. By combining the A* search algorithm with a cost function specific to the reasoning path, it can efficiently compress the chain of thought and determine a reasoning path with high information density and low cost. In addition, we also propose a bidirectional importance estimation mechanism, which further refines this search process and enhances its efficiency beyond uniform sampling. Extensive experiments on several advanced math tasks show that A*-Thought effectively balances performance and efficiency over a huge search space. Specifically, A*-Thought can improve the performance of QwQ-32B by 2.39$\times$ with low-budget and reduce the length of the output token by nearly 50\% with high-budget. The proposed method is also compatible with several other LRMs, demonstrating its generalization capability. The code can be accessed at: https://github.com/AI9Stars/AStar-Thought.

---

## 论文详细总结（自动生成）

### 论文中文总结

#### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大型推理模型（LRM）通过延长思考链（Chain-of-Thought, CoT）来提升性能，但长推理轨迹导致严重的计算效率低下，尤其在资源受限的环境（如端侧设备）中难以部署。现有压缩方法（如过度思考假设下的简单剪枝）常以性能下降为代价。
- **整体含义**：作者提出一种统一框架A*-Thought，旨在从LRM生成的长推理链中自动识别并提取最关键的思考步骤，形成简洁高效的推理路径，从而在保持甚至提升性能的同时显著减少计算开销。

#### 2. 论文提出的方法论

- **核心思想**：将LRM的推理过程建模为搜索树，每个节点代表一个思考跨度（包含当前步骤及其前后步骤）。通过结合双向重要性评分（BIS）和A*搜索算法，高效地在指数级候选路径中寻找信息密度高且成本低的推理路径。
- **关键技术细节**：
  - **步骤级双向重要性评分（BIS）**：评估每个思考步骤对问题（forward importance）和最终解（backward importance）的重要性，综合注意力水平和模型负对数似然。使用轻量模型（GPT-2）计算以提高效率。BIS = 融合ATTN与NLL的加权分数（公式4），超参数α控制问题与解的权重。
  - **路径级A*搜索**：
    1. **初始化**：将原始CoT步骤按BIS降序排列成队列Q，取出最高BIS的步骤作为根节点。
    2. **验证**：若当前路径达到最低验证深度kmin，则使用验证模型V判断能否得出正确解；若是则返回当前路径。
    3. **扩展**：若未通过验证，则从Q中取出W个节点作为候选树叶节点，分别追加到当前路径形成候选路径。
    4. **成本函数**：f = g + h。g（当前路径质量）基于验证模型对路径的负对数似然（公式8）；h（估计未来成本）基于给定当前路径时正确解的条件自信息（公式10）。选择f最小的节点作为活跃叶节点。
    5. **终止**：若搜索深度达到上限kmax，则返回原始CoT；否则继续迭代。
- **算法流程**（Algorithm 1）：排序→初始化→循环（验证→扩展→选择→更新），直至找到解或达深度上限。

#### 3. 实验设计

- **数据集/场景**：数学推理任务：MATH500、AMC23、OlympiadBench、GSM8K；额外域外测评：LiveCodeBench（代码）、MMLU（通用知识）。
- **基准方法**：Chain-of-Draft (CoD)、Break-the-Chain (BtC) 两种变体（Effective Shortcut, Skip Steps）、TokenSkip（训练方法），以及直接微调QwQ-32B w/ s1K-1.1。
- **骨干模型**：QwQ-32B、DeepSeek-R1-Distill-Qwen-32B、s1.1-32B；另有小规模7B/14B实验。
- **评估指标**：Accuracy（↑）、Length（↓）、Accuracy per Computation Unit (ACU = Accuracy / Length)。

#### 4. 资源与算力

- **训练设置**：8块NVIDIA A100 80G GPU，每GPU batch size=1，8梯度累积步数，训练3个epoch，峰值学习率1e-5，warm-up比例0.1。
- **训练时间**（表4）：A*-Thought压缩后数据量仅为原始的31.31%，训练时间相比原始s1K-1.1减少约22-24%（例如QwQ-32B从13819.60秒降至10468.20秒）。
- **验证/推理**：使用s1.1-32B作为验证模型；BIS计算使用GPT-2。

#### 5. 实验数量与充分性

- **实验多样性**：覆盖4个主要数学基准+2个域外基准；4种预算（512/1024/2048/4096 tokens）；3种骨干模型；2种小模型；多个基线方法。
- **消融与分析**：包括BIS中ATTN vs NLL贡献（图8）、α超参数影响（图9）、kmin/kmax探索深度影响（表3、图10）、β权重影响（表9）、与best-of-N缩放策略结合（表5）。
- **充分性评估**：实验设计全面，覆盖多维度（数据、模型、预算、组件）。但论文未报告误差棒（说明因高计算成本未重复实验），但主要结论一致性高，总体较客观公平。

#### 6. 论文的主要结论与发现

- **低预算场景**（512 tokens）：A*-Thought将QwQ-32B平均准确率从12.3%提升至29.4%（+2.39×），ACU从2.41提升至5.99（+2.49×）。
- **高预算场景**（4096 tokens）：在几乎不损失准确率（从70.6%降至69.3%）的情况下，输出长度减少33.59%（从2826降至1876 tokens），ACU最高。
- **泛化能力**：在R1-Distill-32B、s1.1-32B及7B/14B小模型上均有效；在域外任务（LiveCodeBench、MMLU）上也提升了性能与效率。
- **与test-time scaling兼容**：与best-of-N策略结合后，pass@8进一步提升。

#### 7. 优点

- **方法创新性**：首次将A*搜索与双向重要性评估结合用于CoT压缩，从步骤级和路径级双重优化，优于简单剪枝或提示压缩方法。
- **效率显著**：在极低计算预算下大幅提升性能，在较高预算时也能大幅压缩长度而保持准确率，平衡了性能与效率。
- **通用性强**：不依赖特定模型结构，可适配多种LRM及不同规模模型；训练数据压缩率高（68.69%），训练时间缩短约24%。
- **实验设计扎实**：多数据集、多预算、多模型、多基线对比及充分消融，验证了方法的有效性。

#### 8. 不足与局限

- **当前应用范围**：仅限监督微调（SFT），未扩展到强化学习（RL）范式；论文在附录H中明确指出这一限制，并计划未来探索RL扩展。
- **计算成本**：虽训练时间减少，但A*搜索本身需要额外验证步骤（使用验证模型V），在推理时可能增加少量延迟；不过相比原始长CoT的生成成本仍大幅降低。
- **实验覆盖**：主要基于数学推理任务，域外测评仅两个（LiveCodeBench、MMLU），对更广泛场景（如常识推理、开放域问答）尚未充分验证。
- **误差未报告**：因计算资源限制未做多次重复实验，无法提供统计显著性分析，可能影响稳定性结论。
- **超参数敏感**：BIS权重α、成本权重β、搜索深度kmin/kmax等参数需要调整，最优值可能因任务或模型而异。
- **验证模型依赖**：使用固定的s1.1-32B作为验证模型，其质量影响压缩效果；若验证模型较弱或与目标模型不匹配，可能降低收益。

（完）
