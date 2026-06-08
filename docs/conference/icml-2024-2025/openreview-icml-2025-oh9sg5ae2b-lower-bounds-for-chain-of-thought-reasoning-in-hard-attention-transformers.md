---
title: Lower Bounds for Chain-of-Thought Reasoning in Hard-Attention Transformers
title_zh: 硬注意力Transformer中链式思维推理的下界
authors: "Alireza Amiri Bavandpour, Xinting Huang, Mark Rofin, Michael Hahn"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=Oh9sG5ae2b"
tags: ["query:mm-cot"]
score: 8.0
evidence: 链式思维步数的理论下界
tldr: 现有研究对链式思维（CoT）所需步数的理解不足，尤其是硬注意力Transformer中。本文首次系统性地研究了不同算法问题的CoT步数下界，在硬注意力机制下给出了紧界。通过分析奇偶性、乘法等问题，论文证明了在某些情况下Transformer需要长CoT链，这与乐观的电路复杂度上界形成对比。这项工作为理解CoT的表示能力提供了理论基础。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-oh9sg5ae2b/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 677, \"height\": 319, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oh9sg5ae2b/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 823, \"height\": 385, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oh9sg5ae2b/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 810, \"height\": 540, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oh9sg5ae2b/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 822, \"height\": 416, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oh9sg5ae2b/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 705, \"height\": 527, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oh9sg5ae2b/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1751, \"height\": 502, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oh9sg5ae2b/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1601, \"height\": 511, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oh9sg5ae2b/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1606, \"height\": 538, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oh9sg5ae2b/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1770, \"height\": 605, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oh9sg5ae2b/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1345, \"height\": 730, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oh9sg5ae2b/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 876, \"height\": 650, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oh9sg5ae2b/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1774, \"height\": 1143, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-oh9sg5ae2b/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 933, \"height\": 470, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oh9sg5ae2b/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1145, \"height\": 64, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oh9sg5ae2b/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1672, \"height\": 66, \"label\": \"Table\"}]"
motivation: 理解链式思维推理所需的步数下界对评估Transformer的表示能力至关重要。
method: 通过理论分析，在硬注意力机制下推导了多种算法问题的CoT步数下界。
result: 给出了多个问题的紧下界，表明简单问题也可能需要长CoT链。
conclusion: 该工作为CoT步数的必要下界提供了系统性理论，有助于理解Transformer的推理能力边界。
---

## Abstract
Chain-of-thought reasoning and scratchpads have emerged as critical tools for enhancing the computational capabilities of transformers. While theoretical results show that polynomial-length scratchpads can extend transformers' expressivity from $TC^0$ to $PTIME$, their required length remains poorly understood. Empirical evidence even suggests that transformers need scratchpads even for many problems in $TC^0$, such as Parity or Multiplication, challenging optimistic bounds derived from circuit complexity. In this work, we initiate the study of systematic lower bounds for the number of CoT steps across different algorithmic problems, in the hard-attention regime. We study a variety of algorithmic problems, and provide bounds that are tight up to logarithmic factors. Overall, these results contribute to emerging understanding of the power and limitations of chain-of-thought reasoning.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **研究动机**：链式思维（Chain-of-Thought, CoT）推理已成为增强Transformer计算能力的关键技术，但其所需步数的理论上界尚不明确。虽然已知多项式长度的CoT可将Transformer表达能力从 \(TC^0\) 扩展到 \(PTIME\)，但实际经验表明，即便对于 \(TC^0\) 中的简单问题（如奇偶性、乘法），Transformer也需要CoT才能有效求解，这与基于电路复杂度的乐观上界相矛盾。
- **研究问题**：在硬注意力（Unique Hard-Attention, UHAT）模型下，针对不同算法问题，CoT步数必须满足怎样的下界？是否存在理论上最优（紧）的CoT长度？
- **整体意义**：通过系统性地给出多个基础问题的CoT步数下界（且紧至对数因子），该工作揭示了CoT推理在硬注意力Transformer中的本质限制，为理解CoT的表示能力与效率约束提供了理论基础。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
- **核心思想**：利用**随机限制（Random Restrictions）**方法，建立通用CoT步数下界定理（Theorem 3.3）。该定理指出：若某函数 \(f\) 存在长度为 \(o(|x|)\) 的UHAT可表示CoT，则存在一个限制 \(\rho\) 使得（1）\(\rho\) 保留常数比例的输入位置自由；（2）在 \(\rho\) 限制下 \(f\) 为常值函数。这直接导致：对于无法通过固定少量输入位就确定输出的高敏感度函数（如PARITY），其CoT长度必须为 \(\Omega(N)\)。
- **关键技术细节**：
  - **深度约简引理（Lemma 3.4）**：对于任意UHAT Transformer，通过迭代应用随机限制，可在保留恒定自由位置比例的前提下，使每一层每个位置的激活值仅依赖于常数个输入位置。
  - **从Lemma 3.4到Theorem 3.3**：先对输入自身应用限制，再通过固定CoT序列中每个token所依赖的输入位（每步至多固定 \(c\cdot H\cdot L\) 个输入位），逐步将CoT整体固定，从而得到全局限制。若CoT长度为 \(o(N)\)，则最终限制仍保留恒定自由位置。
- **具体应用**：对每个算法问题，先证明其具有线性平均敏感度（从而UHAT无法直接表示），再应用Theorem 3.3得到线性下界，并构造显式CoT匹配该下界（至多对数因子）。

## 3. 实验设计：使用了哪些数据集/场景，benchmark，对比了哪些方法
- **任务与输入**：
  - **PARITY**：随机生成长度 1~500 的二进制串。
  - **MULTIPLICATION**：二进制乘法，操作数位数 4~16。
  - **MEDIAN**：随机生成 \(N\) 个三位十进制数（\(N\) 从1到99），任务为找出中位数。
  - **REACHABILITY**：随机DAG（顶点数5~35），输入为边列表和查询对。
- **Benchmark**：各任务均以**准确率（Accuracy）**为评价指标。
- **对比方法**：
  - 是否有CoT：训练相同架构的Transformer，分别使用完整CoT、无CoT、缩短的CoT（如每k步取一步）进行对比。
  - 对深度推理模型：还测试了DeepSeek-R1和o1-mini在相同任务上的CoT长度增长趋势。
- **额外分析**：
  - 对MULTIPLICATION，比较了直接并行解码、自回归解码、以及基于NTT的 \(O(N\log N)\) 长度CoT。
  - 对PARITY，还研究了“点对点”（dot-by-dot）CoT（仅重复点号）的效果。

## 4. 资源与算力
- **硬件**：使用 **NVIDIA A100 GPU（40GB显存）**。
- **训练细节**（论文部分提及）：
  - PARITY实验：2层2头Transformer，\(d=256\)，训练30K步，batch size 64。
  - MULTIPLICATION实验：BART架构（1层编码器+2层解码器），训练20 epochs，batch size 8，梯度累积4步，学习率0.0001。
  - MEDIAN实验：3层4头Transformer，\(d=256\)，训练50K步，batch size 64，学习率从 \(3\times10^{-4}\) 线性衰减。
  - REACHABILITY实验：4层4头GPT-2，\(d=256\)，训练50K步，batch size 64。
- **未明确说明**：具体使用的GPU数量、总训练时长、并行度等未详细给出。各个实验均独立进行，未报告总计算开销。

## 5. 实验数量与充分性
- **实验组数**：
  - PARITY：在不同输入长度（1~500）和不同CoT步长缩减比例（k=1,2,3,…）下训练，每个配置3次随机种子取平均。
  - MULTIPLICATION：操作数位数4~16，无CoT训练（4/6/8位）和有CoT训练（8~16位），测试集10K样本。另测试了LLM（两个模型各若干长度点）。
  - MEDIAN：N=1,9,19,…99（即输入长度6~398），每个N下测试了多种CoT步长缩减（k=1,2,3,4,5,6,9,12），每个配置3次运行。
  - REACHABILITY：顶点数5~35，有CoT vs 无CoT，3次运行取平均。
- **充分性评价**：
  - **充分**：覆盖了多种算法问题、多种输入长度、多种CoT变体，并使用多次运行保证稳定性。消融实验（如缩短CoT）直接验证下界紧性。
  - **客观**：所有实验均基于固定随机种子和分离的测试集，避免数据泄露。
  - **公平**：对比了有无CoT时相同架构的Transformer表现，且LLM实验仅用于观察趋势而非正式对比。

## 6. 论文的主要结论与发现
- **理论界**：
  - PARITY、MULTIPLICATION（关键中间位）、MEDIAN、REACHABILITY在UHAT下均需 \(\Omega(N)\) 长度的CoT（N为输入规模）。这些下界在大多情况下紧至对数因子。
  - 对于有限状态语言，存在二分法：\(AC^0\) 内语言无需CoT，\(AC^0\) 外语言需线性CoT。
  - “点对点”（dot-by-dot）CoT无法用多项式长度解决PARITY，需超多项式长度（\(\omega(N^k)\) for all \(k\)）。
- **实验验证**：
  - 无CoT时Transformer准确率随输入长度急剧下降；完整CoT（线性长）可保持高准确率。
  - 缩短CoT（如每k步取一步）会导致准确率大幅下降，验证了线性长的必要性。
  - 深度推理模型（DeepSeek-R1、o1-mini）生成的CoT长度也呈线性增长，与理论预测一致。

## 7. 优点：方法或实验设计上的亮点
- **理论创新**：首次系统性地为硬注意力Transformer的CoT推理步数建立通用下界，将随机限制技术扩展到含CoT的场景，方法通用且可应用于多种问题。
- **紧性证明**：下界与构造的上界在大多问题中仅差对数因子，说明结果本质上是紧的。
- **实验与理论紧密结合**：不仅在抽象模型上证明下界，还通过实际训练（软注意力）验证了理论预测的正确性，并测试了主流LLM的行为，增强了结论的普适性。
- **消融实验设计**：通过系统性地缩短CoT步数，直观展示了CoT长度与任务准确率之间的依赖关系，为下界提供了实证支持。

## 8. 不足与局限
- **模型假设限制**：所有下界仅在**硬注意力（UHAT）**模型下证明，不直接适用于软注意力、对数精度或其他注意力变体。虽然论文指出UHAT是软注意力在固定精度下的上界，但严格的下界传递可能不完整。
- **未提供平均情况界**：下界均为最坏情况，实际中可能平均所需步数较少，论文未深入探索。
- **实验规模有限**：乘法实验仅做到16位数字（受计算资源限制），未在更大规模上验证。所有实验输入长度均较小（最多500），与真实LLM应用中的长上下文仍有距离。
- **LLM实验非正式对比**：对DeepSeek-R1和o1-mini的测试仅用于观察CoT长度趋势，未进行严格消融或控制变量，且模型内部机制不透明。
- **可学习性与表示性分离**：论文关注表示性（存在性），但实际可学习性可能受更复杂的因素影响（如优化、初始化）。论文虽引用敏感度与学习困难的关系，但未直接证明这些下界对应的问题在实际训练中无法“压缩”CoT。
- **架构局限**：结论限制在固定深度/头数的Transformer，未考虑更深层或更宽模型可能带来的突破。

（完）
