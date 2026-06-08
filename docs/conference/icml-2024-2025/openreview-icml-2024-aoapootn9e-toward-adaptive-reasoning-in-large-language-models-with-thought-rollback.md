---
title: Toward Adaptive Reasoning in Large Language Models with Thought Rollback
title_zh: 面向大语言模型的自适应推理：思维回滚方法
authors: "Sijia Chen, Baochun Li"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=aoAPOOtN9E"
tags: ["query:mm-cot"]
score: 7.0
evidence: 具有思维回滚的自适应推理框架用于错误纠正
tldr: 传统链式思维推理结构单向固定，难以应对复杂任务和幻觉。本文提出思维回滚（TR）框架，允许语言模型在执行过程中回溯并修正前面的推理步骤。通过错误分析和思维调整，模型能够自适应地构建推理结构。实验表明，该方法在多种推理任务上显著提升了准确率和鲁棒性。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-aoapootn9e/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1778, \"height\": 510, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-aoapootn9e/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 857, \"height\": 452, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-aoapootn9e/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1769, \"height\": 449, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-aoapootn9e/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1632, \"height\": 1674, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-aoapootn9e/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1762, \"height\": 774, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-aoapootn9e/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1538, \"height\": 1182, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-aoapootn9e/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1766, \"height\": 736, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-aoapootn9e/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1746, \"height\": 961, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-aoapootn9e/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1658, \"height\": 1735, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-aoapootn9e/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1040, \"height\": 1063, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-aoapootn9e/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1649, \"height\": 1454, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-aoapootn9e/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1687, \"height\": 1670, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-aoapootn9e/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1783, \"height\": 721, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-aoapootn9e/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 867, \"height\": 408, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-aoapootn9e/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 867, \"height\": 481, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-aoapootn9e/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1780, \"height\": 267, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-aoapootn9e/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1780, \"height\": 479, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-aoapootn9e/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1782, \"height\": 1321, \"label\": \"Table\"}]"
motivation: 传统推理链单向固定，难以应对复杂任务和幻觉问题。
method: 提出思维回滚机制，允许模型在执行过程中回溯并修正之前的推理步骤。
result: 在多个推理任务上提升了准确率和对幻觉的鲁棒性。
conclusion: 该框架使推理过程更加灵活和自适应，增强了模型的纠错能力。
---

## Abstract
Large language models (LLMs) have been routinely used to solve various tasks using step-by-step reasoning. However, the structure of intermediate reasoning steps, or *thoughts*, is rigid and unidirectional, such as chains, trees, or acyclic-directed graphs. Consequently, the resulting inflexible and forward-only reasoning may not address challenging tasks and fail when the LLM frequently gives false responses, i.e., hallucinations. This paper proposes a new reasoning framework, called *Thought Rollback* (TR), allowing LLMs to adaptively build thought structure while maintaining effective reasoning toward problem-solving under hallucinations. The core mechanism of TR is *rolling back thoughts*, which allows LLMs to perform error analysis on thoughts, and thus roll back to any previously mistaken thought for revision. Subsequently, by including such trial-and-error in the prompt to guide the LLM, each rollback leads to one more reliable reasoning path. Therefore, starting with a simple prompt without human annotations, LLM with TR adaptively and gradually explores thoughts for a correct solution. Comprehensive experiments on mathematical problems and multi-task reasoning demonstrate the state-of-the-art performance of TR in terms of problem-solving rate and interaction cost. For instance, the solving rate of GPT-4 with TR outperforms the current best by $9\%$ on the MATH dataset. The source code is available under the folder *examples/ThoughtRollback* of https://github.com/iQua/llmpebase.

---

## 论文详细总结（自动生成）

# 论文《Toward Adaptive Reasoning in Large Language Models with Thought Rollback》中文总结

## 1. 论文核心问题与整体含义（研究动机和背景）

- **核心问题**：现有的大语言模型（LLM）推理方法（如链式思维 CoT、思维树 ToT、思维图 GoT）采用固定且单向的思维结构，推理过程只能向前推进，无法回溯修正错误。一旦中间推理步骤出现“幻觉”（hallucination）或错误，错误会持续传播，导致最终答案错误。
- **研究动机**：人类在推理时会频繁反思、回顾并修正之前的思考步骤（即“回滚”），从而从错误中学习并逐步逼近正确答案。作者希望将这种自适应推理能力赋予 LLM。
- **整体含义**：提出一种名为 **Thought Rollback (TR)** 的框架，使 LLM 能在推理过程中主动识别错误，回滚到先前错误的思维步骤，并利用错误分析经验生成更可靠的推理路径，从而构建灵活的、有向循环图的思维结构，提高复杂问题求解的准确率和对幻觉的鲁棒性。

## 2. 论文提出的方法论

### 2.1 核心思想
- **自适应推理**：不预先定义思维结构，而是让 LLM 在推理过程中动态生成、调整和修订思维步骤。
- **思维回滚**：当 LLM 生成到第 n 步时，通过错误分析确定是否回滚到之前某一步（通常是第一个错误步骤的前一步），并基于该步骤重新生成推理路径。
- **经验积累**：将每次回滚生成的错误分析作为“经验”累积到提示中，指导后续思维生成，避免重复错误。

### 2.2 关键技术细节
- **三个主要阶段**：
  1. **初始化**：使用零样本提示生成第一个思维步骤。
  2. **思维回滚**：对于每个生成的思维，利用 **回滚控制器**（rollback controller）让 LLM 分析现有思维链，识别错误步骤，决定是否回滚以及回滚到哪一步。一旦触发回滚，**提示增强器**（prompt enhancer）将错误分析作为经验添加到提示中，然后从回滚目标步骤生成新的推理路径。
  3. **早期停止**：当获得 K 个解决方案时停止推理。
  4. **解决方案集成**：使用加权多数投票（W-Voting）对 K 个解进行集成，权重基于每条推理路径的传入回滚次数（经验）和传出回滚次数（错误程度）。
- **回滚规则**：回滚到第一个错误步骤的前一步；同一思维被选为回滚目的地的次数上限为 U（实验中设为 3）。
- **提示设计**：使用任务无关的提示模板，包含问题、已有思维步骤和累积的经验（错误分析），指导 LLM 生成后续思维。

### 2.3 算法流程（文字说明）
1. 给定问题 x，使用零样本提示生成第一步思维 z1。
2. 对于当前推理路径 z0…n，调用 LLM 进行错误分析，获得错误分析 A_nm，并确定需要回滚的步骤 m（第一个错误步骤的前一步）。
3. 若存在错误，则将错误分析积累到提示中，从步骤 m-1 重新生成新思维 z_nm，并继续向前推理。
4. 若没有错误，则正常生成下一步思维 z_{n+1}。
5. 重复步骤 2-4，直到获得 K 个完整解，然后使用加权多数投票输出最终答案。

## 3. 实验设计

### 3.1 使用的数据集
- **数学问题**：GSM8K（1319 样本）、SVAMP（300 样本）、AQuA-RAT（254 样本）、MATH（900 样本，含 5 个难度等级）、TheoremQA（400 样本，不含视觉信息）、Game of 24（100 个难题）
- **多任务推理**：MMLU 的 56 个类别中抽取 900 样本（MMLU_900）
- **符号推理**：包含在 MMLU 中

### 3.2 Benchmark 和对比方法
- **基线方法**：
  - 零样本 / 零样本 CoT
  - 少样本 CoT / 复杂 CoT（C-CoT）
  - 自我一致性（SC）
  - 思维树（ToT）
  - 思维图（GoT）
  - 思维提升（BoT）
  - 累积推理（CR）
  - 渐进提示（PHP）
  - 状态最优方法（SOTA）如 CSV（GPT-4 Code Interpreter）、Faithful-CoT 等
- **对比维度**：求解率（Solve Rate）、交互次数（Interaction Number）、token 成本

### 3.3 实验设置
- 使用 LLM：GPT-3.5-turbo（gpt-3.5-turbo-16k-0613）、GPT-4（gpt-4-1106-preview）、Llama2-13b、Llama2-70b
- 默认温度 0.7，top p=0.7
- TR 的早期停止阈值 K=8
- 每个实验报告求解率和需要的交互次数

## 4. 资源与算力

- 论文**未明确说明**使用的 GPU 型号、数量及训练时长。所有实验均基于 API 调用（GPT-3.5/4）或预训练模型推理（Llama2），无额外的模型训练环节。
- 作者提供了 token 成本分析（表 4），显示 TR 方法在 MATH 和 TheoremQA 上生成 token 数和提示 token 数远高于基线，例如 MATH 上生成 token 是 ZeroShot CoT 的 35 倍，提示 token 是 425 倍，但求解率提升显著（27.19%）。这表明 TR 对算力（API 调用量）的需求较高，但未给出具体硬件指标。

## 5. 实验数量与充分性

- **实验数量**：涵盖了 7 个数学推理数据集 + 1 个多任务推理数据集（MMLU），共 8 个数据集；在多个 LLM 上（GPT-4、GPT-3.5、Llama2）进行了测试；对比了 10 种以上基线方法；进行了消融实验（如 TR vs TR+CoT vs TR+W-Voting）；分析了交互成本、token 成本、回滚对求解率的影响等。
- **充分性与公平性**：
  - 实验设计较为全面，覆盖了不同难度、不同领域的问题。
  - 多数结果标记了†表示作者自行复现，未标记的引用自现有论文，保证了可重复性和公平性。
  - 消融实验验证了回滚机制和经验积累的有效性（图 3）。
  - 但是，论文未进行大范围超参数调优（如只设置 U=3, K=8），也未讨论这些参数的最优性。
  - 部分数据集（如 MMLU）只用了 900 样本子集，可能无法代表完整 MMLU 性能。

## 6. 论文的主要结论与发现

- **TR 显著提升求解率**：在 MATH 上 GPT-4+TR 相比 SOTA CSV 提升约 9%，在 AQuA-RAT 上比 BoT 提升 6.3%，在 TheoremQA 上比最佳基线高 4.35%。
- **交互成本更低**：相比 ToT（150 次交互）和 BoT（500+ 交互），TR 平均交互次数约 30-60 次，在性能相近或更好时交互成本显著降低。
- **回滚机制有效**：有传入回滚的推理路径（In Rollback）求解率更高；越晚的回滚（即从更远的步骤回滚）对修正更有效。
- **过程分析优于结果分析**：基于中间步骤的错误分析（过程监督）比仅基于最终解的分析（结果监督）更能帮助 LLM 修正错误。
- **经验指导的集成投票是关键**：TR+W-Voting 相比纯 TR 有显著提升，说明利用经验权重选择更可靠的解很重要。
- **弱 LLM 限制**：当 LLM 本身能力较弱时（如 GPT-3.5-turbo 或 Llama2-13b），TR 的提升幅度较小，且加入 CoT 示例反而可能使性能下降（因无法区分多种指令）。

## 7. 优点

- **创新性**：首次在 LLM 推理中引入可循环的思维回滚机制，突破了单向思维结构的局限。
- **轻量级与通用性**：无需人工标注或任务特定设计，仅需零样本提示即可工作，易于集成到现有推理流程中。
- **鲁棒性**：通过连续的错误分析和回滚，对幻觉有良好的容忍度，能逐步修正错误。
- **成本友好**：虽然 token 成本高，但交互次数相对较少，适合资源有限的场景（相比 ToT 和 BoT）。
- **实验充分**：在多个数据集和多个模型上验证，包含消融、token 成本、交互成本等多种分析，结论可信度较高。

## 8. 不足与局限

- **对 LLM 能力依赖强**：TR 依赖于 LLM 进行准确的错误分析和理解经验，若 LLM 本身能力弱（如 Llama2-13b），性能提升有限甚至无效。
- **高 token 成本**：在 MATH 和 TheoremQA 等困难问题上，PR 的 token 消耗是零样本 CoT 的数十倍到数百倍，经济成本较高，不适用于频繁调用 API 的用户。
- **复杂任务导致结构过复杂**：在极困难问题上，TR 可能生成超过 100 个节点的思维结构，推理链冗长，可能存在无效分支。
- **未讨论超参数优化**：如 U（回滚上限）、K（解数量）等参数未经系统调优，可能不是最优设置。
- **实验覆盖有限**：MMLU 只用了 900 样本子集，而非完整 57 个任务；缺少对更多类型任务（如常识推理、事实验证）的测试。
- **未与传统微调方法对比**：仅与提示工程类方法对比，未与微调（如 RLHF、监督微调）进行比较。
- **可解释性不足**：尽管 TR 引入了错误分析，但回滚决策和错误分析本身依赖于 LLM 的“不确定”输出，可能存在误判，论文对此缺乏深入分析。

（完）
