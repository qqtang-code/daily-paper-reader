---
title: Premise-Augmented Reasoning Chains Improve Error Identification in Math reasoning with LLMs
title_zh: 前提增强推理链提升大语言模型数学推理中的错误识别
authors: "Sagnik Mukherjee, Abhinav Chinta, Takyoung Kim, Tarun Anoop Sharma, Dilek Hakkani Tur"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=4tYckHNVXV"
tags: ["query:mm-cot"]
score: 7.0
evidence: 基于前提增强的推理链用于数学错误识别
tldr: 链式思维（CoT）在数学推理中步骤冗长且依赖关系复杂，导致错误回溯困难。本文提出前提增强推理链（PARC）框架，为每个推理步骤标注其依赖的前提步骤，从而重构推理链。实验表明，该方法显著提升了错误定位的准确性。该工作在推理链的可解释性和错误诊断方面具有重要价值。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-4tyckhnvxv/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1629, \"height\": 532, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4tyckhnvxv/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1657, \"height\": 922, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-4tyckhnvxv/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1556, \"height\": 376, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4tyckhnvxv/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1212, \"height\": 361, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4tyckhnvxv/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1744, \"height\": 928, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4tyckhnvxv/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 820, \"height\": 426, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4tyckhnvxv/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 722, \"height\": 372, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4tyckhnvxv/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 778, \"height\": 492, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4tyckhnvxv/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 777, \"height\": 494, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4tyckhnvxv/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1749, \"height\": 962, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4tyckhnvxv/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1221, \"height\": 375, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4tyckhnvxv/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1218, \"height\": 375, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4tyckhnvxv/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1221, \"height\": 375, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4tyckhnvxv/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1221, \"height\": 372, \"label\": \"Table\"}]"
motivation: 线性推理链中步骤依赖关系复杂，难以验证和回溯错误。
method: 提出前提增强推理链，为每步标注关键前提并重构结构。
result: 在数学推理错误检测任务上取得了更高精度。
conclusion: 该框架增强了推理链的可审计性，有助于提升模型可靠性。
---

## Abstract
Chain-of-Thought (CoT) prompting enhances mathematical reasoning in large language models (LLMs) by enabling detailed step-by-step solutions. However, due to the verbosity of LLMs, the resulting reasoning chains can be long, making it harder to verify the reasoning steps and trace issues resulting from dependencies between the steps that may be farther away in the sequence of steps. Importantly, mathematical reasoning allows each step to be derived from a small set of premises, which are a subset of the preceding steps in the reasoning chain. In this paper, we present a framework that identifies the premises for each step, to improve the evaluation of reasoning. We restructure conventional linear reasoning chains into Premise Augmented Reasoning Chains (PARC) by introducing premise links, resulting in a directed acyclic graph where the nodes are the steps and the edges are the premise links. Through experiments with a PARC-based dataset that we built, namely (Premises and ERrors identification in LLMs), we demonstrate that LLMs can reliably identify premises within complex reasoning chains. In particular, even open-source LLMs achieve 90% recall in premise identification.  We also show that PARC helps to identify errors in reasoning chains more reliably. The accuracy of error identification improves by 6% to 16% absolute when step-by-step verification is carried out in PARC under the premises.
Our findings highlight the utility of premise-centric representations in addressing complex problem-solving tasks and open new avenues for improving the reliability of LLM-based reasoning evaluations.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- 链式思维（CoT）提示增强了LLM在数学推理中的表现，但生成的推理链往往冗长，步骤间依赖关系复杂，导致验证和错误回溯困难。
- 现有评估方法要么依赖人工标注（成本高），要么只给出链级分数，无法定位具体错误步骤；自验证方法也易受无关上下文干扰。
- 本文提出**前提增强推理链（PARC）**框架，通过为每个推理步骤显式标注其依赖的前提（premises），将线性推理链重构为有向无环图，从而提升错误识别的准确性和可解释性。

## 2. 方法论
- **核心思想**：数学推理中每一步都可以从少量前序步骤（即前提）推导得出。将步骤与前提显式关联，可减少验证时的干扰信息，便于追溯误差传播。
- **关键技术细节**：
  - **前提定义**：对于步骤 \(s_i\)，其前提 \(P_i\) 是前序步骤的子集，满足可验证性和最小性（去除任一前提则步骤不可验证）。
  - **前提映射**：两种方法：
    - **聚合式（Aggregative）**：一次查询LLM，给出步骤的所有前提。
    - **二元式（Dyadic）**：逐对判断前序步骤是否为当前步骤的前提，时间复杂度 O(n²)。
  - **错误分类**：除原生错误（数学计算错误、逻辑不一致）外，新增**积累错误**：步骤本身正确但依赖的前提有误。
- **算法流程（Algorithm 1）**：
  1. **前提提取**：对每个步骤 \(k\)，识别其前提 \(P_k\)。
  2. **原生错误检测**：独立判断步骤是否有数学错误；结合前提判断是否有逻辑不一致。
  3. **积累错误检测**：对每个正确步骤，DFS遍历其前提，若有前提为错误，则标记为积累错误。
- **验证策略**：仅基于该步骤的前提进行验证，而非整个上下文。

## 3. 实验设计
- **数据集**：
  - 使用 GSM8K、MATH、Orca-Math、MetaMathQA 四个数学推理 benchmark。
  - 构建 PERL 数据集：从各数据集采样1000例，用 Llama-3.1-8B 生成推理链，筛选正例（答案正确）和负例（答案错误），并用 GPT-4o 生成合成负例（在正链中人为引入错误）。
  - 最终 PERL 包含 607 条推理链（203 正例、214 真实负例、190 合成负例），共 2134 步正确、321 步数学错误、443 步逻辑不一致、741 步积累错误。
- **评估模型**：Llama 3.1 8B/70B、Qwen 2.5 7B/32B/72B、GPT4o-mini、GPT-4o。
- **对比方法**：
  - **前提识别**：无额外指导的零样本提示。
  - **错误识别**：基线（全上下文验证） vs. Oracle前提 vs. 模型自动生成前提（Model Premises）。
  - 额外在 ProcessBench（GSM8K 和 MATH 子集）上验证。

## 4. 资源与算力
- 论文未明确说明所使用的 GPU 型号、数量和训练时长。
- 提到使用 vLLM 进行模型服务、AzureOpenAI 访问 GPT 系列模型，所有推理均设置 temperature=0。
- 因未报告具体硬件配置，无法评估算力开销。

## 5. 实验数量与充分性
- **实验数量**：
  - 前提识别实验：4 个数据集 × 6 个模型（共24组），并报告精度、召回、F1。
  - 错误识别实验：4 个数据集 × 7 个模型（共28组），每个模型又分 Full Context、Oracle Premises、Model Premises 三种设置，且按正/负/合成负例给出详细结果。
  - 消融实验：Oracle vs 模型生成前提、聚合式 vs 二元式前提映射、错误类型细分。
  - 额外在 ProcessBench 上验证（2 个数据集 × 5 个模型）。
- **充分性与公平性**：
  - 覆盖多种模型规模和类型（开源/闭源），结果趋势一致。
  - 在真实负例和合成负例上分别评估，注意到差异（合成更易），体现了公平性。
  - 消融实验合理，验证了前提的作用。
  - 不足：数据集规模有限（约607条链），可能不足以覆盖复杂推理场景；未在更大模型（如 GPT-4o 以上）上测试；未报告多次运行的标准差。

## 6. 主要结论与发现
- LLM 能够高召回率（开源模型可达 90% 以上）识别前提，成功将 LRC 转换为 PARC。
- 基于前提的错误识别准确率比全上下文基线提升 6%–16% 绝对值（表3）。
- 积累错误是最难检测的类型，PARC 可显著改善其识别（表5：积累错误准确率从 12% 提升至 57.5%）。
- 合成负例比真实负例更容易识别，说明不能仅依赖人为扰动来评估错误检测能力。
- 使用模型自动生成的前提与使用 oracle 前提的性能相当（表4），表明端到端 pipeline 可行。

## 7. 优点
- **方法创新**：将前提显式化，减少了验证时的无关信息，符合数学推理的局部依赖性本质。
- **错误分类完善**：引入积累错误，弥补了现有工作在误差传播检测上的空白。
- **数据集构建细致**：PERL 提供带前提和错误标注的推理链，有利于后续研究。
- **实验设计全面**：涵盖多种模型、数据集和设置，并在 ProcessBench 上验证泛化性。
- **可解释性好**：每个步骤的错误类型和前提链接清晰，便于审计与调试。

## 8. 不足与局限
- **实验覆盖有限**：仅测试了数学推理（初等数学），未在符号推理、科学证明等更复杂场景验证。
- **前提识别依赖模型能力**：召回虽高，但漏取关键前提可能导致后续验证失败；二元式方法精度低且计算成本高。
- **积累错误检测简化**：仅通过 DFS 检查直接前提，未考虑高阶传递或并行错误叠加。
- **数据集规模较小**：PERL 仅 607 条链，可能无法充分捕捉多样化的错误模式。
- **未考虑错误修正**：论文聚焦识别而非修正，未探索如何利用 PARC 引导模型自我纠正。
- **资源开销未报告**：缺少计算时间、GPU 使用等细节，难以评估实际部署成本。

（完）
