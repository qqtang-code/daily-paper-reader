---
title: "Mind Your Step (by Step): Chain-of-Thought can Reduce Performance on Tasks where Thinking Makes Humans Worse"
title_zh: 注意你的步骤：当思考损害性能时链式思维会降低任务表现
authors: "Ryan Liu, Jiayi Geng, Addison J. Wu, Ilia Sucholutsky, Tania Lombrozo, Thomas L. Griffiths"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=J3gzdbYZxS"
tags: ["query:mm-cot"]
score: 9.0
evidence: 研究链式思维何时降低多模态模型性能
tldr: "链式思维（CoT）被广泛用于提升模型性能，但何时会降低性能仍待探究。本文借鉴认知心理学，选取六种人类思考过多反而变差的任务进行测试。发现最先进模型（如OpenAI o1）在三种任务上使用CoT后准确率下降高达36.3%。该工作警示CoT并非万能，为合理应用CoT提供了边界条件。"
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-j3gzdbyzxs/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1238, \"height\": 729, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-j3gzdbyzxs/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 567, \"height\": 436, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-j3gzdbyzxs/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1067, \"height\": 467, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-j3gzdbyzxs/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1070, \"height\": 466, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-j3gzdbyzxs/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 831, \"height\": 981, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-j3gzdbyzxs/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1299, \"height\": 631, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-j3gzdbyzxs/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1294, \"height\": 629, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-j3gzdbyzxs/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 821, \"height\": 369, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-j3gzdbyzxs/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 205, \"height\": 205, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-j3gzdbyzxs/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1078, \"height\": 249, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-j3gzdbyzxs/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 809, \"height\": 396, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-j3gzdbyzxs/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 867, \"height\": 287, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-j3gzdbyzxs/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 860, \"height\": 190, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-j3gzdbyzxs/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 865, \"height\": 273, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-j3gzdbyzxs/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 867, \"height\": 253, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-j3gzdbyzxs/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 869, \"height\": 231, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-j3gzdbyzxs/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1391, \"height\": 232, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-j3gzdbyzxs/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1408, \"height\": 181, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-j3gzdbyzxs/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1427, \"height\": 541, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-j3gzdbyzxs/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 792, \"height\": 134, \"label\": \"Table\"}]"
motivation: 探究链式思维提示在哪些任务上会系统性降低模型性能。
method: 从认知心理学中选取六种典型任务，对比有/无CoT下的模型表现。
result: "发现CoT在某些任务上导致准确率显著下降，最大降幅达36.3%。"
conclusion: 该工作提醒研究人员注意CoT的适用范围，避免盲目使用。
---

## Abstract
Chain-of-thought (CoT) prompting has become a widely used strategy for improving large language and multimodal model performance. 
However, it is still an open question under which settings CoT systematically reduces performance. In this paper, we seek to identify the characteristics of tasks where CoT reduces performance by drawing inspiration from cognitive psychology, focusing on six representative tasks from the psychological literature where deliberation hurts performance in humans. In three of these tasks, state-of-the-art models exhibit significant performance drop-offs with CoT (up to 36.3\% absolute accuracy for OpenAI o1-preview compared to GPT-4o), while in others, CoT effects are mixed, with positive, neutral, and negative changes. While models and humans do not exhibit perfectly parallel cognitive processes, considering cases where thinking has negative consequences for humans helps identify settings where it negatively impacts models. By connecting the literature on human verbal thinking and deliberation with evaluations of CoT, we offer a perspective for understanding the impact of inference-time reasoning.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **背景**：链式思维（Chain-of-Thought, CoT）提示已广泛应用于提升大语言模型（LLM）和多模态模型（LMM）的性能，尤其在数学推理和符号推理任务上效果显著。然而，已有研究表明 CoT 在某些任务上反而会降低性能，但缺乏系统性的模式识别。
- **核心问题**：究竟哪些任务特征会导致 CoT 系统性降低模型性能？如何高效、先验地预测这些失败场景？
- **整体含义**：本文借鉴认知心理学中“人类在言语思考（deliberation）下表现反而变差”的经典任务，将其迁移至 LLM/LMM 的 CoT 评估中。通过对比模型与人类在类似任务上的表现，不仅揭示了 CoT 的适用范围，还为理解推理时推理（inference-time reasoning）的局限性提供了心理学视角。

## 2. 方法论

### 核心思想
- 从认知心理学中筛选出六种典型任务，这些任务在人类身上表现出“思考反而损害表现”的现象。本文假设在这些任务上，CoT 提示（等同于让模型“言语思考”）也可能导致模型性能下降。
- 由于人类与模型的能力存在差异（如记忆容量、先验知识等），本文预期并非所有六种任务都会在模型上重现人类效果，但可以利用心理学知识高效识别 CoT 失败的任务。

### 关键技术细节
- **选取的六种任务**：
  1. **隐式统计学习**：人工语法学习（Artificial Grammar Learning, AGL），模型需判断字母串是否由同一有限状态文法生成，CoT 可能干扰对统计模式的隐式感知。
  2. **语言不适于表征的刺激（人脸识别）**：经典“言语遮蔽”现象，要求模型在相似人脸中识别目标，CoT 可能导致言语描述干扰视觉判断。
  3. **含例外模式的学习**：分类数据中存在 80% 可概括规则但 20% 的例外，人类解释会过度概括；模型在 CoT 下可能偏向寻找简单规则而忽略例外。
  4. **逻辑不一致检测**：识别两个陈述是否逻辑矛盾，人类解释会降低检测率（因缺乏逻辑训练）；模型可能有先验逻辑知识。
  5. **空间直觉**：判断杯子倾斜后水位高度，人类依赖视觉/运动模拟；模型可能缺乏此类先验。
  6. **多特征偏好聚合**：在大量公寓信息中选最优项，人类工作记忆受限；模型拥有长上下文。

- **实验设计**：
  - 对每个任务，设计**零样本直接提示**（Direct / Zero-shot）与**CoT 提示**两种条件，对比性能差异。
  - 对于任务 4、5、6，除标准 CoT 外还设计了更贴合心理学实验的变体（如要求“解释不一致为何为真”）。
- **可扩展的数据集**：将原始心理学实验从少量样本（如 12 对逻辑对）大规模扩展到数百到数千个问题，构造开放式基准。
- **进一步分析**：包括树状思维（Tree-of-Thought）、温度鲁棒性、复杂度简化（简化文法节点）、上下文引导（steering）等消融。

## 3. 实验设计

### 使用的数据集/场景
- **隐式统计学习**：
  - 100 个随机有限状态文法（FSG），每个文法产生 44 个测试字母串（22 正例、22 负例），共 4400 个二分类问题。
  - 每个问题提供 15 个训练样本。
- **人脸识别**：
  - 500 个问题，2500 张合成人脸（Stable Image Ultra 生成）。
  - 每个问题：一张初始人脸 + 5 张候选图片（其中一张为同一人，其余四张为不同人且都满足相同文字描述）。
- **含异常的分类学习**：
  - 240 个列表，每个列表 10 辆车，特征包括：唯一标识（车牌号）、80% 相关特征（如“气候”）、3 个无关特征。
  - 多轮学习：模型依次预测每辆车类别，获反馈，反复迭代直至全部正确或满 15 轮。
- **逻辑不一致检测**：
  - 1608 个 {A, B} 对（来自 MNLI、SNLI 和 GPT-4o 合成数据），每个对构造一致与不一致两个问题，共 3216 个二分类问题。
- **空间直觉**：
  - 100 个问题，每问题包含两杯子（一满一空），空杯旁有 A–D 标记，要求选择正确水位高度。
- **工作记忆偏好（公寓选择）**：
  - 80 个特征 × 4 个描述（正、负、两个中性）→ 构造 300 个选择集（四选一），按难度（∆）分为三档（100+100+100）。

### 对比方法
- **零样本直接提示**：直接询问答案。
- **CoT 提示**：要求“逐步思考”或“解释后再回答”。
- **额外方法**（部分任务）：树状思维（ToT）、自一致性、不同的 prompt 引导（如强调追踪车牌号）。

### 模型
- **语言模型**：GPT-4o, o1-preview, Claude 3.5 Sonnet, Claude 3 Opus, Gemini 1.5 Pro, Llama 3.1 70B/8B Instruct, Llama 3 70B/8B Instruct。
- **视觉语言模型**：GPT-4o, Claude 3.5 Sonnet, Claude 3 Opus, Gemini 1.5 Pro, InternVL2 26B, InternVL2 Llama3 76B。
- 由于成本限制，o1-preview 仅在子集上测试。

## 4. 资源与算力

- 文中未明确说明使用的 GPU 型号、数量、训练时长。
- 实验主要依赖 API 调用（Azure 积分由微软 AFMR 拨款支持），不使用本地训练。
- 对于开源模型可能涉及本地推理，但未报告算力细节。总体而言，算力需求中等，主要涉及推理而非训练。

## 5. 实验数量与充分性

- **实验数量**：总计在 6 个任务上进行了涵盖多个模型和条件的广泛比较。
  - 隐式统计学习：9 个模型 + 子集 o1 测试 + 消融（ToT、温度、复杂度、引导）。
  - 人脸识别：6 个 LMM + 简化难度 + 二元分类变体。
  - 含异常分类：3 个 LLM + 简化（二进制 oracle）+ 引导 prompt 分析。
  - 逻辑不一致：6 个 LLM（o1 子集）+ 两个 CoT 变体。
  - 空间直觉：5 个 LMM。
  - 工作记忆偏好：4 个 LLM + 三个难度范围。
- **充分性与公平性**：
  - 多模型覆盖，包含闭源和开源，避免单一模型偏见。
  - 控制 prompt 格式一致，temperature 设为 0.0 以减少随机性；o1 因 API 限制 temperature=1.0。
  - 进行了多种消融和鲁棒性检查，结果稳定。
  - 然而，部分任务（如空间直觉）可能因任务改为多选题而偏离原心理学实验，但作者讨论了此改动。
  - 总体而言，实验设计客观，对比公平，统计检验（p值）报告充分。

## 6. 主要结论与发现

1. **CoT 显著降低性能的三类任务**（与人类“思考变差”现象高度一致）：
   - **隐式统计学习**：CoT 导致最大降幅，如 o1-preview 相比 GPT-4o 零样本准确率下降 36.3%（绝对），多数模型降幅 1.98%–23.1%。
   - **人脸识别**：所有 6 个 LMM 均显示下降，GPT-4o 下降 12.8% 绝对（20% 相对），弱模型下降更明显。
   - **含异常的分类学习**：CoT 导致模型需要更多轮数才能学会（GPT-4o 增加 331%，从平均 2.9 轮增至 12.5 轮），且最终无法突破 80% 准确率（即只学概括性规则无视例外）。
2. **CoT 效果混合的三类任务**（人类变差但模型不一定）：
   - **逻辑不一致**：CoT 有时改善（如 GPT-4o +40%），有时轻微下降（如 Gemini 1.5 Pro）。差异源于模型拥有逻辑训练知识。
   - **空间直觉**：无显著差异，因模型缺乏运动模拟先验。
   - **工作记忆偏好**：CoT 有时提升，尤其更强模型能利用长上下文汇总特征；弱模型（Llama 3.1 70B）难以处理长推理导致下降。
3. **心理学启发的启发式方法有效**：通过对 Sprague et al. (2025) 的 378 个比较的 bootstrap 检验，本文选取的 50 个比较的平均性能下降幅度和下降频率均显著高于随机（p < 0.0001），证明该启发式能高效识别 CoT 失败任务。

## 7. 优点

- **跨学科创新**：系统性地将认知心理学经典范式用于分析 CoT 失败，提供理论支撑和预测能力。
- **大规模实验**：将每个原始心理学实验从十几个刺激扩展到数百上千个，构造了开放基准（human overthinking benchmark）。
- **多模型、多条件验证**：覆盖主流 LLM 和 LMM，并进行多种消融（ToT、温度、难度简化、引导），结论鲁棒。
- **可操作性建议**：明确指出 CoT 在隐式统计学习、视觉识别、含异常规则学习上应谨慎使用，甚至避免默认启用推理时推理。
- **开放科学**：数据集开源，促进后续研究。

## 8. 不足与局限

- **任务覆盖有限**：仅聚焦六种任务，未能穷尽 CoT 失败的所有场景；心理学启发式可能遗漏模型特有的失败模式。
- **人类-模型差异**：后三种任务未观察到一致性下降，说明心理学映射并不完美，需要针对模型能力进行额外推理，增加了预测难度。
- **心理学任务改动**：为适应模型，部分任务做了较大改动（如人脸识别取消了分心任务、空间直觉改为选择题），可能改变原任务的核心特征，需谨慎解释。
- **Prompt 工程影响**：不同指导语可能影响 CoT 效果；虽然探索了引导，但未进行完全的 prompt 空间搜索。
- **计算成本限制**：o1-preview 仅在子集测试；部分模型（如 Llama 3.1 70B）在工作记忆任务上输出异常，可能影响结论。
- **未探索更高级推理方法**：仅测试 CoT 和 ToT，未涵盖自一致性、思维程序等，推广性有限。

（完）
