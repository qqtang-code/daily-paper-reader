---
title: "MME-CoT: Benchmarking Chain-of-Thought in Large Multimodal Models for Reasoning Quality, Robustness, and Efficiency"
title_zh: MME-CoT：面向大型多模态模型链式思考推理的质量、鲁棒性和效率基准
authors: "Dongzhi Jiang, Renrui Zhang, Ziyu Guo, Yanwei Li, Yu Qi, Xinyan Chen, Liuhui Wang, Jianhan Jin, Claire Guo, Shen Yan, Bo Zhang, Chaoyou Fu, Peng Gao, Hongsheng Li"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=YZvefQVLJI"
tags: ["query:mm-cot"]
score: 10.0
evidence: 面向大型多模态模型的链式思考推理基准
tldr: 链式思考虽提升了大语言模型推理能力，但对多模态模型的影响缺乏系统评估。本文提出MME-CoT基准，覆盖数学、科学、OCR、逻辑、时空和通用场景六个领域，并设计了评估推理质量、鲁棒性和效率的新指标。通过精心构建的高质量数据和评估策略，首次全面揭示了CoT在多模态模型中的表现和挑战，为后续研究提供了标准化测试平台。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-yzvefqvlji/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 861, \"height\": 937, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yzvefqvlji/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1695, \"height\": 617, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yzvefqvlji/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1741, \"height\": 790, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yzvefqvlji/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1105, \"height\": 624, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yzvefqvlji/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1769, \"height\": 1234, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yzvefqvlji/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 856, \"height\": 1095, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yzvefqvlji/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 856, \"height\": 1095, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yzvefqvlji/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1770, \"height\": 1004, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yzvefqvlji/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 703, \"height\": 706, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yzvefqvlji/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1777, \"height\": 1547, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yzvefqvlji/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1777, \"height\": 1376, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yzvefqvlji/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 542, \"height\": 548, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yzvefqvlji/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 742, \"height\": 556, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yzvefqvlji/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 952, \"height\": 1395, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yzvefqvlji/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1542, \"height\": 1747, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yzvefqvlji/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 910, \"height\": 1406, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yzvefqvlji/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1733, \"height\": 730, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yzvefqvlji/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 808, \"height\": 1298, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yzvefqvlji/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 399, \"height\": 201, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yzvefqvlji/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1465, \"height\": 571, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yzvefqvlji/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 427, \"height\": 208, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yzvefqvlji/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 64, \"height\": 64, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yzvefqvlji/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 66, \"height\": 70, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-yzvefqvlji/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 518, \"height\": 643, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-yzvefqvlji/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1769, \"height\": 569, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-yzvefqvlji/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1750, \"height\": 150, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-yzvefqvlji/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1763, \"height\": 852, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-yzvefqvlji/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1782, \"height\": 306, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-yzvefqvlji/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1769, \"height\": 272, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-yzvefqvlji/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 697, \"height\": 237, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-yzvefqvlji/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 788, \"height\": 303, \"label\": \"Table\"}]"
motivation: 链式思考在多模态模型上的影响缺乏系统评估和标准化基准。
method: 构建覆盖六领域的多模态CoT基准，提出质量、鲁棒性和效率三维评估指标。
result: 揭示了不同多模态模型在CoT推理上的差异和瓶颈。
conclusion: MME-CoT为多模态链式思考研究提供了全面的评估工具。
---

## Abstract
Answering questions with Chain-of-Thought (CoT) has significantly enhanced the reasoning capabilities of Large Language Models (LLMs), yet its impact on Large Multimodal Models (LMMs) still lacks a systematic assessment and in-depth investigation. In this paper, we introduce **MME-CoT**, a specialized benchmark evaluating the CoT reasoning performance of LMMs, spanning six domains: math, science, OCR, logic, space-time, and general scenes. 
As the first comprehensive study in this area, we propose a thorough evaluation suite incorporating three novel metrics that assess the reasoning quality, robustness, and efficiency at a fine-grained level.
Leveraging curated high-quality data and a unique evaluation strategy, we conduct an in-depth analysis of state-of-the-art LMMs, uncovering several key insights: *1)* Models with reflection mechanism demonstrate a superior CoT quality, with Kimi k1.5 outperforming GPT-4o and demonstrating the highest quality results; *2)* CoT prompting often degrades LMM performance on perception-heavy tasks, suggesting a potentially harmful overthinking behavior; and *3)* Although the CoT quality is high, LMMs with reflection exhibit significant inefficiency in both normal response and self-correction phases.
We hope MME-CoT serves as a foundation for advancing multimodal reasoning in LMMs.

---

## 论文详细总结（自动生成）

### 论文核心问题与整体含义

- **研究动机**：链式思考（Chain-of-Thought, CoT）在大语言模型（LLM）中显著提升了推理能力，但在大型多模态模型（LMM）上的影响缺乏系统评估和深入分析。现有评估多聚焦最终答案，忽略推理过程的质量、鲁棒性和效率。
- **整体含义**：为填补这一空白，论文提出了 **MME-CoT**，一个专门的基准测试，旨在全面评估 LMM 在 CoT 推理中的表现，并为未来研究提供标准化测试平台。

### 方法论：核心思想与关键技术细节

- **核心思想**：通过构建覆盖多领域的 CoT 数据集，并提出三维评估套件（质量、鲁棒性、效率），以细粒度方式分析 LMM 的推理过程。
- **关键技术细节**：
  1. **CoT 质量评估**：
     - **Recall（召回率）**：使用 GPT-4o 匹配模型输出中的关键步骤（推理结论 + 图像描述）与人工标注的关键步骤，衡量信息的覆盖程度。
     - **Precision（精确率）**：将模型输出分割为原子步骤（逻辑推理、图像描述、背景信息），并判断每个步骤的正确性（匹配标注或逻辑合理）。最终以 F1 分数作为整体质量指标。
  2. **CoT 鲁棒性评估**：
     - 通过两种提示（直接回答 `DIR` vs. 逐步思考 `COT`）在感知任务（需最小推理）和推理任务上比较性能差异。
     - **Stability（稳定性）**：`Acc_{COT}^{感知} - Acc_{DIR}^{感知}`，衡量 CoT 对感知任务的干扰程度。
     - **Efficacy（有效性）**：`Acc_{COT}^{推理} - Acc_{DIR}^{推理}`，衡量 CoT 对推理任务的提升程度。
  3. **CoT 效率评估**：
     - **Relevance Rate（相关率）**：通过 GPT-4o 判断每个步骤是否对回答问题有帮助（不考虑正确性），并施加缩放因子放大差异。
     - **Reflection Quality（反思质量）**：识别出以“Wait”、“Alternatively”等为标志的反思步骤，判断其有效性（纠正错误或通过新见解验证结论）。
- **数据构建**：数据集包含 1130 个问题（837 推理 + 293 感知），覆盖数学、科学、OCR、逻辑、时空、通用场景六大领域。采用两阶段标注（GPT-4o 初版 + 人工审核），提供 3865 个关键步骤标注和参考描述。

### 实验设计

- **数据集与场景**：使用 MME-CoT 自身基准，包含 6 个主要领域和 17 个子类别。同时从 MathVerse、MMMU-Pro、OlympiadBench 等多个公开源收集。
- **基准（Benchmark）**：MME-CoT 本身即为评估基准，包含三维评价指标（质量、鲁棒性、效率）。
- **对比方法**：
  - 早期模型：LLaVA-OneVision (7B/72B)、Qwen2-VL (7B/72B)、MiniCPM-V-2.6、InternVL2.5 (8B)
  - 推理增强模型：LLaVA-CoT (11B)、Mulberry (8B)、InternVL2.5-MPO (8B/78B)
  - 具备反思能力的模型：QVQ-72B、Virgo-72B（开源）；Kimi k1.5、GPT-4o、Claude-3.5、Gemini-2.0-Flash（闭源）
- **实现细节**：使用 GPT-4o mini 进行最终答案提取，GPT-4o 执行所有其他评判任务。遵循 VLMEvalKit 默认超参数。

### 资源与算力

- **文中未明确说明**：论文没有提及训练模型所需的 GPU 型号、数量或训练时长。评估过程依赖 GPT-4o/GPT-4o mini 进行推理和评判，但未给出调用成本或硬件配置。因此，无法报告具体算力消耗。

### 实验数量与充分性

- **实验数量**：主要结果如表 2（整体性能）和表 3（按类别分解）所示，覆盖 10+ 个模型，在 6 个领域上分别报告质量、鲁棒性、效率分数。此外，附录中进行了误差分析（附录 E，梳理 4 种 CoT 错误类型和 4 种反思错误类型）以及人类一致性验证（附录 D.2，对 216 个预测、2368 个步骤进行抽样评测，一致性率 >85%，幻觉率 ≤2.1%）。
- **充分性与公平性**：实验设计较全面，覆盖了不同规模、有无反思能力、开源/闭源的多种模型。鲁棒性评估中特别标注了某些模型（如 Mulberry、Virgo）因无法正确响应直接提示而导致不可靠结果（标记*），体现了客观性。但主要依赖 GPT-4o 作为评判器，可能存在模型固有偏差。数据集规模（1130 问）相对有限，对某些任务（如逻辑、时空）的样本数量可能不足。

### 主要结论与发现

1. **反思机制提升 CoT 质量**：Kimi k1.5 在质量指标（F1 分数）上超越 GPT-4o；QVQ 相比其基础模型 Qwen2-VL-72B 提升 5.8%。
2. **CoT 损害感知任务**：大部分模型在感知任务上使用 CoT 提示后准确率下降（负稳定性分数），最严重为 InternVL2.5-8B（下降 6.8%），表现出“过度思考”（overthinking）行为。
3. **大模型更善用 CoT**：更大参数量（如 Qwen2-VL-72B 对比 7B）在推理任务上表现出更好的有效性（Efficacy 正分）。
4. **反思步骤常无效**：QVQ 和 Virgo 的反思质量仅约 60%，即约 40% 的反思无助于正确答案，甚至引入干扰。
5. **长 CoT 不保证覆盖关键步骤**：虽精确率高，但长 CoT 模型的召回率并不高，说明可能跳过必要中间步骤。
6. **低相关率问题**：在通用场景、时空、OCR 任务中，模型常生成与问题无关的描述，降低效率。

### 优点

- **系统性创新**：首次提出针对 LMM CoT 的三维评估框架（质量、鲁棒性、效率），弥补了以往仅关注最终答案的不足。
- **可解释指标**：使用 Recall/Precision 评估推理过程覆盖度和正确性，引入 Stability/Efficacy 及 Relevance/Reflection Quality，均具有直观含义。
- **高质量标注**：数据集经过两阶段（GPT-4o 初版 + 人工审核）精细标注，提供关键步骤和参考描述，支撑细粒度评估。
- **人类验证**：通过随机采样的人类评估验证了 GPT-4o 评判的可靠性，增强了结论可信度。
- **全面覆盖**：考虑了 6 大领域、17 个子类，涵盖多种视觉推理场景。

### 不足与局限

- **数据集规模偏小**：仅 1130 个问题，可能无法完全覆盖多模态推理的复杂性和多样性，尤其对某些子类别（如逻辑、时空）样本数较少。
- **评判器偏差**：主要依赖 GPT-4o 进行步骤划分和正确性判断，可能存在模型自身的限制或偏见，尽管人类验证显示一致性较高。
- **鲁棒性评估中的不可靠标记**：部分模型（如 Mulberry、Virgo）无法遵循直接提示，导致其 Stability/Efficacy 分数被标记为不可靠，影响了比较的公平性。
- **未探讨更广泛的多模态任务**：实验局限于静态图像，未拓展至视频、3D 或交互式场景等更复杂的多模态输入。
- **未提供计算资源细节**：缺失训练或评估的硬件配置和耗时，不利于可重复性评估。
- **反思质量定义较严格**：仅将“纠正错误”或“新见解验证”视为有效反思，可能忽略部分合理但未被标准识别的情况。

（完）
