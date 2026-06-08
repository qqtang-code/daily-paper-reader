---
title: "PENCIL: Long Thoughts with Short Memory"
title_zh: "PENCIL: 短记忆中的长思考"
authors: "Chenxiao Yang, Nathan Srebro, David McAllester, Zhiyuan Li"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=6wglsDXIei"
tags: ["query:mm-cot"]
score: 9.0
evidence: 长思维链的内存减少机制
tldr: 该论文指出长思维链推理受限于中间计算无限积累的内存问题。提出PENCIL方法，通过训练学习到的模式递归清理中间思考，交替生成与擦除。这使得模型能够用更短的上下文和更少的计算进行更深层次的推理。实验表明，仅25M参数、2048上下文长度的Transformer即可解决爱因斯坦谜题，验证了方法的有效性。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-6wglsdxiei/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1693, \"height\": 806, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-6wglsdxiei/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1697, \"height\": 631, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-6wglsdxiei/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1710, \"height\": 342, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-6wglsdxiei/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1635, \"height\": 311, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-6wglsdxiei/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1665, \"height\": 689, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-6wglsdxiei/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 777, \"height\": 361, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-6wglsdxiei/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1775, \"height\": 546, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-6wglsdxiei/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1750, \"height\": 737, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-6wglsdxiei/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1752, \"height\": 715, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-6wglsdxiei/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1784, \"height\": 788, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-6wglsdxiei/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 797, \"height\": 305, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6wglsdxiei/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 779, \"height\": 304, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6wglsdxiei/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 784, \"height\": 342, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6wglsdxiei/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1776, \"height\": 298, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6wglsdxiei/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1783, \"height\": 168, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6wglsdxiei/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1788, \"height\": 171, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6wglsdxiei/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1786, \"height\": 306, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6wglsdxiei/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1782, \"height\": 274, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6wglsdxiei/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1782, \"height\": 303, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6wglsdxiei/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1782, \"height\": 270, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6wglsdxiei/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1783, \"height\": 302, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6wglsdxiei/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1783, \"height\": 237, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6wglsdxiei/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1779, \"height\": 236, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6wglsdxiei/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1778, \"height\": 170, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6wglsdxiei/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1780, \"height\": 205, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6wglsdxiei/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1781, \"height\": 97, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6wglsdxiei/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1773, \"height\": 107, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6wglsdxiei/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1789, \"height\": 76, \"label\": \"Table\"}]"
motivation: 解决长思维链推理中中间计算无限积累导致的内存和计算效率问题。
method: 引入基于训练模式的递归清理机制，在自回归生成中交替生成与擦除中间思考。
result: 小模型（25M参数）用短上下文成功解决爱因斯坦谜题，效率显著提升。
conclusion: PENCIL范式使得模型能用更少资源进行更深入思考，推动长链推理实用化。
---

## Abstract
While state-of-the-art LLMs have demonstrated great promise of using long Chains-of-Thought (CoT) to boost reasoning, scaling it up to more challenging problems is fundamentally limited by suboptimal memory usage — intermediate computations accumulate indefinitely in context even no longer needed for future thoughts. We introduce PENCIL, which incorporates a novel reduction mechanism into the autoregressive generation process that recursively clean up intermediate thoughts based on patterns learned from training. By alternately generating and erasing, PENCIL can think deeper to solve harder problems using shorter context and less computes. Empirically, for example, we demonstrate PENCIL with a small 25M-parameter transformer and 2048 context length solves Einstein's puzzle — a task that challenges much larger models like GPT-4. Theoretically, we prove PENCIL can perform universal efficient computation by simulating any Turing machines with optimal time and space complexity, and thus can solve arbitrary computable tasks that are otherwise intractable for vanilla CoT.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：长思维链（Chain-of-Thought, CoT）在提升推理能力时，中间计算会无限累积在上下文中，即使后续不再需要也无法释放，导致内存资源消耗过高，限制了模型在复杂、需要大量步骤的任务上的可扩展性。
- **整体含义**：通过引入“擦除”机制，使得模型能够在生成过程中主动清理已完成的中间推理，从而用更短的上下文和更少的计算实现更深层的推理。这一范式提升了 Transformer 在固定内存约束下处理计算密集任务的能力，理论上可实现通用高效计算。

---

## 2. 论文提出的方法论

### 核心思想
- 将 CoT 与一个 **减少规则（reduction rule）** 结合，在每一步生成后检查是否满足模式：
  ```
  C [CALL] T [SEP] A [RETURN] ⇒ C A
  ```
  其中 `[CALL]`、`[SEP]`、`[RETURN]` 为特殊分隔符。一旦匹配，则删除中间思考 T，仅保留答案 A 和上下文 C。
- 该规则可递归应用，模拟嵌套函数调用，实现层次化推理。

### 关键技术细节
- **PENCIL 步**：每步先执行标准下一个 token 生成（f），再应用减少规则（φ），即 `PENCIL = φ ∘ f`。
- **交替过程**：生成阶段（产生直到 `[RETURN]` 的序列）→ 减少阶段（匹配模式并压缩）→ 下一轮生成，如此迭代直至生成 `[EOS]`。
- **训练数据生成**：先运行实际算法（如 DPLL 求解 SAT、递归求解 QBF、约束传播求解爱因斯坦谜题），生成带特殊 token 的“脚手架 CoT”，再切分成多个较短序列 `x^(i)`（以 `[RETURN]` 或 `[EOS]` 结尾）。
- **损失计算**：仅对每段中从上一轮压缩点之后生成的 token 计算损失，其余部分（上下文和答案）不参与梯度更新。
- **理论证明**：使用自回归机（Autoregressive Machine）和 FASP 编程语言证明，PENCIL 能够以最优时间和空间复杂度模拟任何图灵机，即在 O(T) 步内生成，最大上下文长度 O(S)，其中 T 为图灵机步数，S 为空间需求。

---

## 3. 实验设计

### 使用的数据集 / 场景
- **SAT（3-SAT）**：NP 完全问题，子句数/变量数比为 4.3，产生困难实例。
- **QBF（量化布尔公式）**：PSPACE 完全问题，变量随机量化为存在/全称。
- **爱因斯坦拼图（Einstein's Puzzle）**：经典约束满足问题，需通过自然语言线索推理出属性分配。规模涵盖 `3×3`、`4×4`、`5×5`。

### Benchmark
- 基线：不使用 CoT 的“直接答案”模型。
- 对比方法：标准 CoT（即不应用减少规则，但包含相同特殊 token 以公平对比）。
- 评估指标：**准确率（Accuracy）** 和 **跟踪率（Trace Rate）**——跟踪率指模型生成步骤与算法真实步骤的匹配比例。

---

## 4. 资源与算力

- 论文 **未明确说明** GPU 型号、数量、训练时长等具体算力信息。
- 仅指出使用的模型规模：
  - SAT/QBF：6 层 Transformer，参数约 **10.63M**。
  - 爱因斯坦拼图：8 层 Transformer，参数约 **25.19M**。
- 所有实验采用 **2048 上下文窗口**，并使用旋转位置编码（RoPE）。训练采用在线学习（在线生成数据），批次大小和学习率在不同方法间保持一致。

---

## 5. 实验数量与充分性

### 实验组数
- **SAT 和 QBF**：每个问题规模 `n = 3` 到 `10`（共 8 个尺度），各自进行了准确率和跟踪率评估，并绘制了推理时间 vs 最大可解规模图、训练收敛曲线（不同 FLOPs 预算）。
- **爱因斯坦拼图**：三种规模（3×3、4×4、5×5），每个规模报告准确率和跟踪率；另做了模型大小（参数数量）和上下文长度的消融实验。
- **额外分析**：绘制最大序列长度对比（带/不带减少规则）；测试时间可扩展性（给定时间预算能解的最大问题规模）；训练收敛速度（固定 FLOPs 或迭代次数）。

### 充分性与公平性
- 实验覆盖了三个从 NP 完全到 PSPACE 完全、再到自然语言推理的典型任务，且数据规模从简单到极具挑战。
- 对比 CoT 时，CoT 也使用了相同特殊 token，确保结构信息一致，减少不公平因素。
- 消融实验考察了模型容量和上下文长度对性能的影响，证明了 PENCIL 对较小模型的鲁棒性。
- **总体充分**，但未在更大语言模型（如 GPT-3 scale）上验证，也未测试其他领域（如数学推理、代码生成）。

---

## 6. 论文的主要结论与发现

1. **内存管理至关重要**：CoT 的“只写不删”机制是处理计算密集型任务的瓶颈，而 PENCIL 的减少规则能显著节省空间。
2. **实际效果显著**：
   - 在 SAT 和 QBF 上，PENCIL 在问题规模增大时保持接近 100% 准确率，而 CoT 准确率在 `n=10` 时分别降至 50% 和 61%。
   - 在 `5×5` 爱因斯坦拼图上，PENCIL 以 25M 参数、2048 上下文达到 **97%** 准确率，CoT 仅 25%（接近随机）。
3. **训练更高效**：在相同 FLOPs 预算下，PENCIL 收敛更快，尤其在大问题规模时优势明显。
4. **理论强大**：PENCIL 能以最优时间和空间复杂度模拟图灵机，从而能解决任何可计算问题，而标准 CoT 需要上下文随时间线性增长。

---

## 7. 优点

- **方法创新**：首次将函数调用栈式回收机制与深度学习生成结合，解决 CoT 固定内存痛点，概念简洁但有效。
- **理论完备**：提供了 Transformer 能在固定大小下实现通用空间高效计算的严格证明，使用 FASP 语言构建，连接了深度学习与图灵机模拟。
- **实验扎实**：覆盖 NP/PSPACE 完全问题和自然语言推理，展示极端挑战下的显著提升；消融实验验证了空间压缩带来的实际收益（FLOPs、收敛速度）。
- **实用价值**：小模型 + 短上下文可解决大模型都困难的问题，为资源受限场景下的推理提供了新思路。

---

## 8. 不足与局限

- **模型规模有限**：所有实验仅使用千万级参数的小模型，未在数十亿或更大模型上验证 PENCIL 的泛化能力。
- **任务覆盖窄**：仅验证了三个特定类型（SAT、QBF、爱因斯坦拼图），未在更广泛的自然语言推理、数学、代码生成等任务上测试。
- **依赖算法生成训练数据**：当前训练数据基于人工编写的算法（DPLL、递归 QBF、约束传播），若任务没有已知高效算法，如何自动产生训练数据存疑。
- **减少规则固定**：仅使用 `[CALL]/[SEP]/[RETURN]` 模式，更复杂的重叠或非嵌套推理结构可能需要更复杂的规则。
- **实际部署成本**：虽然节省空间，但每次减少后 KV 缓存需部分重新计算（附录 B 提及），可能抵消部分计算收益。
- **缺少与近期方法的直接对比**：未与 Tree-of-Thoughts、Graph-of-Thoughts 等同类结构化推理方法比较。
- **未讨论对长文档或对话任务的影响**：该工作主要针对问题求解，未考察在摘要、问答等场景的适用性。

（完）
