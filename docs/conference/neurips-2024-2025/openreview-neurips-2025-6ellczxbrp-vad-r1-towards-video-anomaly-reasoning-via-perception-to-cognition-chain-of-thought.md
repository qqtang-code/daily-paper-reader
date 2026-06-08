---
title: "Vad-R1: Towards Video Anomaly Reasoning via Perception-to-Cognition Chain-of-Thought"
title_zh: Vad-R1：通过感知到认知链式思考实现视频异常推理
authors: "Chao Huang, Benfeng Wang, Wei Wang, Jie Wen, Chengliang Liu, Li Shen, Xiaochun Cao"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=6eLlczxbrp"
tags: ["query:mm-cot"]
score: 8.0
evidence: 通过感知到认知链式推理进行视频异常推理
tldr: 现有视频异常检测仅停留在浅层描述，缺乏深度推理。提出Vad-R1框架，设计感知到认知的链式思考（P2C-CoT），模拟人类从感知到认知的推理过程，引导多模态大模型进行多步视觉推理，在视频异常推理任务上实现了更细粒度的分析和理解。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-6ellczxbrp/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1416, \"height\": 708, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-6ellczxbrp/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1427, \"height\": 516, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-6ellczxbrp/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1424, \"height\": 232, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-6ellczxbrp/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1407, \"height\": 806, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-6ellczxbrp/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1434, \"height\": 583, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-6ellczxbrp/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 694, \"height\": 356, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-6ellczxbrp/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 690, \"height\": 357, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-6ellczxbrp/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1448, \"height\": 1419, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-6ellczxbrp/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1429, \"height\": 302, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-6ellczxbrp/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1425, \"height\": 418, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-6ellczxbrp/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1412, \"height\": 1159, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-6ellczxbrp/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1460, \"height\": 817, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-6ellczxbrp/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1423, \"height\": 254, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-6ellczxbrp/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1438, \"height\": 453, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-6ellczxbrp/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1449, \"height\": 481, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-6ellczxbrp/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 654, \"height\": 817, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-6ellczxbrp/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1442, \"height\": 1109, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-6ellczxbrp/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1445, \"height\": 607, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-6ellczxbrp/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1441, \"height\": 297, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-6ellczxbrp/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1397, \"height\": 459, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-6ellczxbrp/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1403, \"height\": 856, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-6ellczxbrp/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1441, \"height\": 856, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-6ellczxbrp/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1303, \"height\": 283, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-6ellczxbrp/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1463, \"height\": 728, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-6ellczxbrp/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1339, \"height\": 1107, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-6ellczxbrp/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1301, \"height\": 374, \"label\": \"Table\"}]"
motivation: 现有视频异常检测缺乏对异常的深度推理分析。
method: 设计感知到认知链式思考（P2C-CoT）引导MLLM逐步推理。
result: 在视频异常推理任务上显著优于浅层描述方法。
conclusion: 该方法将多步视觉推理成功应用于视频异常分析。
---

## Abstract
Recent advancements in reasoning capability of Multimodal Large Language Models (MLLMs) demonstrate its effectiveness in tackling complex visual tasks. However, existing MLLM-based Video Anomaly Detection (VAD) methods remain limited to shallow anomaly descriptions without deep reasoning. In this paper, we propose a new task named Video Anomaly Reasoning (VAR), which aims to enable deep analysis and understanding of anomalies in the video by requiring MLLMs to think explicitly before answering. To this end, we propose Vad-R1, an end-to-end MLLM-based framework for VAR. Specifically, we design a Perception-to-Cognition Chain-of-Thought (P2C-CoT) that simulates the human process of recognizing anomalies, guiding the MLLMs to reason about anomalies step-by-step. Based on the structured P2C-CoT, we construct Vad-Reasoning, a dedicated dataset for VAR. Furthermore, we propose an improved reinforcement learning algorithm AVA-GRPO, which explicitly incentivizes the anomaly reasoning capability of MLLMs through a self-verification mechanism with limited annotations. Experimental results demonstrate that Vad-R1 achieves superior performance, outperforming both open-source and proprietary models on VAD and VAR tasks.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **核心问题**：现有基于多模态大语言模型（MLLM）的视频异常检测（VAD）方法仅停留在浅层的异常描述，缺乏对异常事件的深度理解和因果推理能力。
- **整体含义**：本文提出新任务 **视频异常推理（Video Anomaly Reasoning, VAR）**，旨在要求 MLLM 在回答前明确进行多步思考，实现对视频异常的结构化、逐步推理，从而提升异常的认知深度。该任务将传统 VAD 从表面检测拓展到更深层的认知理解。

## 2. 方法论
### 核心思想
- 设计 **感知到认知链式思考（Perception-to-Cognition Chain-of-Thought, P2C-CoT）**，模拟人类识别异常的过程：先感知全局环境和局部可疑片段，再从浅层认知（识别异常现象）过渡到深层认知（分析原因、违反的社会规范、后果），最后输出包含异常类别、描述、时空位置、原因和潜在影响的答案。

### 关键技术细节
- **P2C-CoT 结构**：分为两个阶段（感知、认知）共 4 步：
  1. 全局感知：描述场景、环境、正常行为。
  2. 局部感知：聚焦异常事件的时间、空间、外观。
  3. 浅层认知：判断异常性并基于视觉线索解释。
  4. 深层认知：推理原因、违反的规范、潜在后果。
- **数据集 Vad-Reasoning**：基于现有 VAD 数据集（UCF-Crime、XD-Violence、TAD、ShanghaiTech 等）并补充新视频，共 8641 视频：训练集 8203（其中 SFT 子集 1755 带有完整 P2C-CoT 注释，RL 子集 6448 仅含视频级弱标签），测试集 438。定义细粒度异常分类（人类活动、环境、物体 3 大类，37 子类）。
- **训练流程**：
  - Stage 1：在 SFT 子集上用监督微调（SFT）学习基本异常推理能力。
  - Stage 2：在 RL 子集上用提出的 **AVA-GRPO** 强化学习进一步激励推理能力。
- **AVA-GRPO**：扩展自 GRPO，增加 **异常验证奖励**（Anomaly Verification Reward）：
  - 若模型预测视频异常，则剔除预测的异常片段再次输入模型，若新预测为正常，则给予正奖励（0.5）。
  - 若模型预测正常，则随机丢弃开头或结尾片段再次输入，若新预测为异常，则给予负奖励（-0.2）。
  - 结合格式奖励、准确率奖励、长度奖励，计算组内相对优势，优化策略模型。

## 3. 实验设计
### 数据集与基准
- **Vad-Reasoning 测试集**（438 视频）：评估异常推理（BLEU-2、METEOR、ROUGE-2）和检测（Accuracy、F1、mIoU、R@K）。
- **VANE 基准**（325 视频，559 问答对，涵盖真实监控和 AI 生成视频）：评估多选问答准确率。
- **LLM-as-judge 评价**：由 GPT-4o 等评估输出的合理性（R）、细节（D）、一致性（C）。

### 对比方法
- 开源通用视频 MLLM：InternVideo2.5、InternVL3、VideoChat-Flash、VideoLLaMA3、LLaVA-NeXT-Video、Qwen2.5-VL。
- 开源视频推理 MLLM：Open-R1-Video、Video-R1、VideoChat-R1。
- MLLM-based VAD 方法：Holmes-VAD、Holmes-VAU、HAWK。
- 闭源 MLLM：Claude3.5-Haiku、GPT-4o、Gemini2.5-Flash/Pro、QVQ-Max、o4-mini。

## 4. 资源与算力
- **硬件**：4 块 NVIDIA A100 (80GB) GPU。
- **训练时长**：SFT 阶段约 6 小时（4 轮），RL 阶段约 26 小时（1 轮）。
- **输入设置**：视频均匀采样 16 帧，每帧最大像素 128×28×28。训练学习率 1e-6，GRPO 的 β=0.04，每组生成 4 个完成。

## 5. 实验数量与充分性
- **数量**：共约 7 个主表格、4 个补充表格、多个定性示例。包括：
  - 主结果（Table 2/3/4）：对比多种方法在推理和检测上的表现。
  - 推理有效性分析（Table 1）：比较直接回答、随机推理、结构化推理的效果。
  - 消融研究（Table 5/6）：SFT vs RL vs 联合；不同奖励策略；不同帧数/分辨率。
  - 额外评估（Table 10/11/12）：pair-wise 比较、double-right 指标。
- **充分性**：实验覆盖多个数据集、多种基线、多种设置（输入帧数、分辨率、奖励组合），对比公平（控制基线与自身方法同条件）。消融实验全面验证了各组件贡献。定性示例展示实际推理效果，评价指标多元。总体实验设计客观且充分。

## 6. 主要结论与发现
- Vad-R1 在视频异常推理（BLEU-2 0.233，METEOR 0.406）和检测（Accuracy 0.875，F1 0.862，mIoU 0.713）上显著优于所有开源方法，甚至超越闭源模型（如 GPT-4o、o4-mini）。
- 结构化 P2C-CoT 比随机或无推理的提示方式大幅提升检测性能（Recall 提升 26.5%）。
- SFT 和 RL 联合训练效果最佳，RL 单独使用提升有限，表明需先通过 SFT 赋予基础推理能力。
- AVA-GRPO 较原始 GRPO，在异常检测（Precision 从 0.861 升至 0.882）上更优；长度奖励与异常验证奖励组合最关键。
- 增加输入帧数（16→32→64）提升性能，但过高分辨率可能带来冗余。

## 7. 优点
- **任务创新**：首次提出视频异常推理（VAR）任务，填补 VAD 缺乏深度推理的空白。
- **方法设计**：P2C-CoT 模拟人类认知过程，结构化引导逐步推理，可解释性强。
- **自验证机制**：AVA-GRPO 通过视频裁剪自验证，无需复杂标注即可生成有效奖励信号。
- **数据集构建**：Vad-Reasoning 覆盖多场景、细粒度异常类别，包含结构化 CoT 注释，是现有最大之一。
- **实验充分**：对比大量开源/闭源模型，多角度消融分析，定性定量结合，结论可靠。

## 8. 不足与局限
- **推理速度**：多步 CoT 过程增加了计算开销，实时部署困难。
- **注释成本**：高质量 CoT 注释依赖闭源模型（Qwen-VL-Max、Qwen-Max）及人工校验，扩展性受限。
- **测试集规模**：仅 438 个测试视频，可能无法完全反映真实分布的多样性。
- **泛化性**：模型在 VANE 基准上表现良好，但仅在部分公开数据集验证，未见跨领域（如医疗、工业）实验。
- **偏差风险**：可能过度拟合训练集异常模式，对未见过的异常风格（如 AI 生成场景）鲁棒性未充分测试。
- **伦理考量**：论文未深入讨论模型输出可能引发的偏见或误判风险，在社会安全应用中需谨慎。

（完）
