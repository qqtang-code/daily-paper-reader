---
title: Generating Chain-of-Thoughts with a Pairwise-Comparison Approach to Searching for the Most Promising Intermediate Thought
title_zh: 通过成对比较方法生成为最有希望的中间思维而搜索的链式思维
authors: "Zhen-Yu Zhang, Siwei Han, Huaxiu Yao, Gang Niu, Masashi Sugiyama"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=CpcaL75UgY"
tags: ["query:mm-cot"]
score: 6.0
evidence: 通过成对比较搜索最有希望的中间思维来生成链式思维
tldr: 在链式思维生成过程中，使用LLM评估中间思想存在噪声和不稳定性。本文基于Vapnik原理，提出成对比较方法，通过比较候选思维对的相对优劣来减少评估噪声，从而更可靠地选择最有希望的中间思维。实验结果表明该方法生成更高质量的推理链。该工作提升了链式思维生成的鲁棒性。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-cpcal75ugy/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 776, \"height\": 323, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-cpcal75ugy/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1704, \"height\": 646, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-cpcal75ugy/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 402, \"height\": 313, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-cpcal75ugy/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 399, \"height\": 319, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-cpcal75ugy/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 302, \"height\": 297, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-cpcal75ugy/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 303, \"height\": 298, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-cpcal75ugy/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 302, \"height\": 297, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-cpcal75ugy/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 738, \"height\": 385, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-cpcal75ugy/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1591, \"height\": 336, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-cpcal75ugy/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 882, \"height\": 151, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-cpcal75ugy/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1059, \"height\": 406, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-cpcal75ugy/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1058, \"height\": 406, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-cpcal75ugy/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1058, \"height\": 410, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-cpcal75ugy/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1723, \"height\": 252, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-cpcal75ugy/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1733, \"height\": 171, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-cpcal75ugy/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1582, \"height\": 105, \"label\": \"Table\"}]"
motivation: LLM对中间思维的评估存在噪声，影响链生成质量。
method: 使用成对比较替代直接评分，减少评估噪声。
result: 生成了更高质量的推理链。
conclusion: 成对比较是一种有效的链式思维生成改进策略。
---

## Abstract
To improve the ability of the large language model (LLMs) to tackle complex reasoning problems, chain-of-thoughts (CoT) methods were proposed to guide LLMs to reason step-by-step, enabling problem solving from simple to complex. State-of-the-art methods for generating such a chain involve interactive collaboration, where the learner generates candidate intermediate thoughts, evaluated by the LLM, guiding the generation of subsequent thoughts. However, a widespread yet understudied problem is that the evaluation from the LLM is typically noisy and unreliable, potentially misleading the generation process in selecting promising intermediate thoughts. In this paper, motivated by Vapnik's principle, we use pairwise-comparison evaluation instead of point-wise scoring to search for promising intermediate thoughts with the noisy feedback from the LLM. In each round, we randomly pair intermediate thoughts and directly prompt the LLM to select the more promising one from each pair, allowing us to identify the most promising thoughts through an iterative process. To further alleviate the noise in the comparison, we incorporate techniques from ensemble learning and dueling bandits, proposing two variants of the algorithm. Experiments on three real-world tasks demonstrate the effectiveness of our proposed algorithm and verify the rationale of the pairwise comparison mechanism.

---

## 论文详细总结（自动生成）

# 论文结构化中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：大型语言模型（LLM）在复杂多步推理任务（如数学推理、数独等）中存在局限性。链式思维（Chain-of-Thought, CoT）方法通过引导LLM逐步推理提升性能，但现有方法（如基于评分的 Tree-of-Thoughts, S-ToT）依赖LLM对每个中间思维进行点式评分，而LLM的评分存在严重噪声，导致后续思维生成被误导。
- **背景**：Vapnik原则指出，不应为解决更通用的困难问题（如精确评估每个候选的分数）作为中间步骤。在CoT生成中，只需识别最有希望的中间思维，而非精确打分。LLM对两个思维的比较比单独打分更稳健（如图1中数独示例所示）。
- **目标**：提出一种基于成对比较的CoT生成框架，利用LLM的噪声比较反馈，鲁棒地搜索最有希望的中间思维，从而提升推理链质量。

## 2. 方法论

### 核心思想
- 用**成对比较**替代点式评分：每轮随机配对候选中间思维，直接要求LLM选择更优的一个；迭代淘汰，最终保留K个最有希望的思维。
- 保留历史未选中思维：将之前未被选中的思维纳入后续轮次的比较中，实现“回溯”，避免因噪声导致有价值思维被过早丢弃。
- 通过集成学习（多次比较取多数）和决斗式赌博机（dueling bandits）进一步抑制比较噪声。

### 关键技术细节
1. **标准模式（Standard Mode）**：每对思维比较n次（实验中n=1或3），取多数投票获胜者。
2. **决斗模式（Dueling Mode）**：假设比较结果服从未知概率，采用自适应比较次数，直到置信度足够或达到预算（n=3），基于(Falahatgar et al., 2017)的Knockout算法，保证以高概率输出ε-最优思维。
3. **算法流程**（文字描述）：
   - 初始化：根据查询生成m个候选思维。
   - 每轮迭代t：
     - 将当前候选集Z<sub>t</sub>（包含所有历史未丢弃思维）随机配对。
     - 对每对思维，通过LLM比较（标准或决斗方式）选出胜者。
     - 重复配对直到剩余不多于K个思维，作为本轮选中的思维集。
     - 基于每个选中思维生成下一层的数个新思维。
   - 达到最大深度T或获得最终答案时停止。

### 复杂度与Token成本
- 比较次数：O(nT K log m)。
- Token成本随保留历史思维而增加，但可通过计数器限制比较次数来降低。

## 3. 实验设计

### 数据集/场景
- **AQuA**（数学推理问答，254题）
- **Game of 24**（24点游戏，100题）
- **Sudoku Puzzles**（3×3, 4×4, 5×5，各10题）
- 额外在**GSM8K、Coin Flip (OOD)、BBH**上扩展实验。

### Benchmark 与方法对比
- 基础方法：Direct（直接查询）、CoT、Self-Consistent CoT (SC-CoT)
- 现有SOTA：S-ToT、PoT、Self-Refine、GoT（部分对比）
- 自行构造的消融对照：
  - SC-SToT：对S-ToT中每个思维多次评分取多数（考虑噪声，但成本高）
  - Comp-SToT：仅将S-ToT的点式评分替换为成对比较（不加回溯）
  - Back-SToT：仅替换回溯机制（保留历史思维但用点式评分）
- 本文方法：C-ToT (Stand.) 和 C-ToT (Duel.)

### 实验设置概要
- LLM：一律使用 GPT-3.5-turbo-1106（通过API调用，非本地训练）。
- 每任务树深度T、每层生成数m、每层保留数K等参数随任务调整（详见附录A）。
- 所有实验重复3次（部分扩展实验5次），报告平均准确率和/或标准差。

## 4. 资源与算力

- 论文**未明确说明**使用的GPU型号、数量或训练时长。所有实验均通过调用 OpenAI 的 GPT-3.5-turbo API 完成，不涉及本地模型训练或微调。
- 资源消耗主要体现在API调用的Token数量（表6-8给出了各方法的prompt/completion tokens和成本估算），无传统算力指标。

## 5. 实验数量与充分性

- **主要实验**：在AQuA、Game of 24、Sudoku（三个子规模）上进行主对比，共5个任务场景。
- **扩展实验**：在GSM8K、Coin Flip、BBH上补充了与CoT、SToT、PoT、Self-Refine的对比（表4）。
- **消融实验**：
  - 比较/生成数量参数（m, K）的影响（表9）。
  - 历史思维保留阈值的影响（表10）。
  - 比较次数n的影响（表11）。
  - 组件消融（SC-SToT, Comp-SToT, Back-SToT）分析。
- **公平性**：控制Token成本大致相当（如SC-CoT取与C-ToT接近的样本数）；并行计算用于效率说明但未强制使用；各方法使用相同的LLM和相同的树深度/生成参数（除直接法外）。
- **充分性**：实验覆盖了问答、数学推理、逻辑推理三大类任务，消融实验较完整，消解了各设计因素的作用，结论可信。

## 6. 主要结论与发现

1. 成对比较机制在LLM反馈噪声下显著优于点式评分，能够更可靠地选择最有希望的中间思维。
2. C-ToT（Stand.）和C-ToT（Duel.）在所有三个主要任务上均取得了最高平均准确率（见表1-3，表4），优于S-ToT、SC-CoT等基线。
3. 保留历史未选中思维（回溯机制）有助于纠正因初始噪声造成的误弃，进一步提升了性能。
4. 决斗模式（Dueling）在比较噪声较大时（如AQuA）比标准模式效果更好；而在Sudoku等比较相对清晰的任务中，标准模式即可达到相近性能。
5. 成对比较的Token成本与S-ToT大致可比或略高，但性能提升明显；通过限制比较次数可控制成本。

## 7. 优点

- **方法创新性**：基于Vapnik原则，将CoT生成中的评估问题从点式回归转化为成对比较，更贴合LLM的能力特点，理论动机清晰。
- **鲁棒性设计**：通过集成投票和决斗式自适应比较，系统性地处理了LLM反馈中的噪声，提升可靠性。
- **回溯机制**：将历史未被选中思维纳入后续比较，解决了传统树搜索中人工剪枝门限难以设定的问题，且是一种软性重评估，无需硬阈值。
- **实验充分**：主任务+扩展任务+多角度消融，对比方法覆盖主流基线（包括专门考虑噪声的SC-SToT），验证了各组件有效性。
- **理论分析**：给出了决斗模式下保证找到ε-最优思维的复杂度上界，增强了说服力。

## 8. 不足与局限

- **成本与效率**：保留历史思维可能使比较轮次增多，Token成本在部分任务（如AQuA）中高于S-ToT；尽管提出了计数器剪枝，未在实验中充分应用。
- **任务局限性**：主要测试了可拆解为树结构的推理任务（数学、数独），未涉及需要图结构或多种推理类型混合的复杂任务（如科研论文推理）。
- **LLM依赖性**：实验仅基于GPT-3.5-turbo，未验证在GPT-4或其他开源LLM（如LLaMA）上的泛化性；不同LLM的比较噪声特性可能不同，算法超参数（如n）需重新调整。
- **评估指标单一**：仅使用准确率作为指标，未评估生成链条的质量（如中间步骤的合理性、多样性）或用户偏好。
- **理论假设局限**：决斗模式依赖随机超越性假设和偏好独立性，在实际LLM反馈中可能不完全成立。
- **消融实验粒度**：虽分析了K、m、n等参数，但未系统研究树深度T的敏感性；回溯机制的具体收益缺乏定量分析（如多少比例的错误被纠正）。

（完）
