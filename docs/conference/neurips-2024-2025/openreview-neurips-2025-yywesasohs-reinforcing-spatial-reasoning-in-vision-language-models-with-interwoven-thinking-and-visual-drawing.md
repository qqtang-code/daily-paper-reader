---
title: Reinforcing Spatial Reasoning in Vision-Language Models with Interwoven Thinking and Visual Drawing
title_zh: 利用交织思维与视觉绘制增强视觉语言模型的空间推理
authors: "Junfei Wu, Jian Guan, Kaituo Feng, Qiang Liu, Shu Wu, Liang Wang, Wei Wu, Tieniu Tan"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=yyWeSAsOhs"
tags: ["query:mm-cot"]
score: 8.0
evidence: 通过思维与绘制的交织进行多模态空间推理
tldr: 现有视觉语言模型在多模态推理中仅使用文本，在空间推理任务上存在本质局限。论文提出将推理过程与视觉绘制交织的方法，让模型在推理时同时生成视觉草图以辅助空间定位。实验证明该方法在需要精确几何理解和连续空间跟踪的任务上大幅超越纯文本推理方法，为多模态推理提供了新范式。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-yywesasohs/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1443, \"height\": 704, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yywesasohs/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1439, \"height\": 376, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yywesasohs/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1445, \"height\": 280, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yywesasohs/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1448, \"height\": 300, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yywesasohs/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 727, \"height\": 360, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yywesasohs/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 210, \"height\": 205, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yywesasohs/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1413, \"height\": 557, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yywesasohs/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 673, \"height\": 250, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yywesasohs/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 267, \"height\": 199, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yywesasohs/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 268, \"height\": 199, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yywesasohs/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 266, \"height\": 198, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yywesasohs/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1412, \"height\": 292, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yywesasohs/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 239, \"height\": 180, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yywesasohs/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 241, \"height\": 177, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yywesasohs/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 242, \"height\": 176, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yywesasohs/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 241, \"height\": 177, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yywesasohs/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 241, \"height\": 176, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yywesasohs/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 241, \"height\": 178, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-yywesasohs/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1444, \"height\": 973, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-yywesasohs/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1161, \"height\": 255, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-yywesasohs/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 838, \"height\": 295, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-yywesasohs/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1175, \"height\": 191, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-yywesasohs/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1442, \"height\": 850, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-yywesasohs/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1302, \"height\": 283, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-yywesasohs/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 954, \"height\": 269, \"label\": \"Table\"}]"
motivation: 纯文本推理在空间任务中缺乏几何理解和连续跟踪能力。
method: 提出将推理与视觉绘制交织，在推理过程中生成视觉草图辅助空间定位。
result: 在空间推理基准上显著提升，尤其是在复杂几何推理任务中。
conclusion: 视觉绘制作为推理的一部分能有效增强多模态模型的空间感知能力。
---

## Abstract
As textual reasoning with large language models (LLMs) has advanced significant, there has been growing interest in enhancing the multimodal reasoning capabilities of large vision-language models (LVLMs). However, existing methods primarily approach multimodal reasoning in a straightforward, text-centric manner, where both reasoning and answer derivation are conducted purely through text, with the only difference being the presence of multimodal input. As a result, these methods often encounter fundamental limitations in spatial reasoning tasks that demand precise geometric understanding and continuous spatial tracking\textemdash capabilities that humans achieve through mental visualization and manipulation. To address the limitations, we propose drawing to reason in space, a novel paradigm that enables LVLMs to reason through elementary drawing operations in the visual space. By equipping models with basic drawing operations including annotating bounding boxes and drawing auxiliary lines, we empower them to express and analyze spatial relationships through direct visual manipulation, meanwhile avoiding the performance ceiling imposed by specialized perception tools in previous tool-integrated reasoning approaches. To cultivate this capability, we develop a three-stage training framework: cold-start training with synthetic data to establish basic drawing abilities, reflective rejection sampling to enhance self-reflection behaviors, and reinforcement learning to directly optimize for target rewards. Extensive experiments demonstrate that our model, named \textsc{Spark}, consistently outperforms existing methods across diverse spatial reasoning benchmarks involving maze navigation, static spatial reasoning, video-based reasoning and multi-view-based reasoning tasks, with an average improvement of 11.5\%. Ablation studies reveal the critical role of each training stage, with reflective rejection sampling particularly enhancing the model's self-correction capabilities and reasoning potential.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义

- **研究动机**：现有大型视觉语言模型（LVLMs）在多模态推理中主要采用纯文本形式的推理（text-centric reasoning），将视觉信息转化为文本语义空间进行处理。然而，这种转化导致空间细节丢失，尤其在需要精确几何理解和连续空间跟踪的任务（如迷宫导航、视频中的空间关系推理、多视角信息融合）中表现脆弱。人类解决此类问题依赖心理可视化与动态操作，因此论文提出让模型在视觉空间中进行基本绘图操作（如标注边界框、画辅助线），模拟人类的视觉思维过程。

- **核心问题**：如何赋予 LVLMs 通过“绘图+思考”交织的方式执行空间推理的能力，避免依赖外部感知工具（如 grounding 或 OCR）带来的性能瓶颈，并使模型具备自我修正与反思能力。

- **整体含义**：论文提出的“在空间中绘图以推理”（drawing to reason in space）范式，为多模态空间推理提供了一条新路径，将推理过程从纯文本扩展到视觉交互，显著提升了模型在多个空间推理基准上的表现（平均提升 18.4%），并展示了渐进式训练框架的有效性。

## 2. 论文提出的方法论

- **核心思想**：将空间推理分解为一系列交织的视觉绘图操作与语言推理步骤，使模型能够在每次推理迭代中主动编辑图像（标注边界框、画辅助线），从而动态补充空间细节，实现思考与视觉操作的双向反馈。

- **关键技术细节**：
  - **绘图操作集**：仅包含两个基本操作——边界框标注（`T_box`）和辅助线绘制（`T_line`）。每个操作包含参数：图像索引 `k`、空间坐标 `p`、语义标签 `l`。执行后输出带标注的图像。
  - **推理链**：形式化为 `R = {(r_t, e_t, o_t)}`，其中 `r_t` 是自然语言推理，`e_t` 是绘图操作集合，`o_t` 是执行结果。
  - **奖励函数**（公式 2）：
    ```
    S = 1[Scorrect > β] · (Scorrect(A, Â) + Sformat(R))
    ```
    - `Scorrect`：多选题用精确匹配，数值题用多阈值平均相对精度（MRA）。
    - `Sformat`：结构有效性评分（操作是否可执行）。
    - `β`：阈值（设为 0.0），防止奖励黑客。

- **三阶段训练框架**：
  - **阶段1：冷启动训练（Cold-start Training）**：使用 Qwen2.5-72B-VL 生成的合成推理路径进行监督学习（公式 4），建立基础绘图和推理能力。数据筛选要求答案正确、格式有效，且至少包含三步推理。
  - **阶段2：反思拒绝采样（Reflective Rejection Sampling）**：从冷启动模型采样推理路径，过滤出同时满足答案正确、格式有效且包含**反思行为**（同一标签在不同时间步重复出现且操作不同，公式 5）的样本进行监督微调（公式 6）。增强自我修正能力。
  - **阶段3：强化学习（Reinforcement Learning）**：使用 GRPO 目标（公式 7-8），结合反映格式和正确性的奖励函数，并引入早期终止策略（无操作、图像超限、重复操作）。优化模型在任务上的推理表现。

## 3. 实验设计

- **数据集/场景**（共5个基准，覆盖三类任务）：
  - **图像空间推理**：Maze（迷宫导航，2,000 个样本）、SpatialEval-Real（135 个样本，真实世界空间关系）
  - **视频空间推理**：VSI-Bench（5,130 个样本，需跟踪时空关系）
  - **多视图空间推理**：SPAR-Bench（7,211 个样本）、MMSI-Bench（1,000 个样本）

- **对比方法**：
  - **专有 LVLMs**：GPT-4o、Gemini-1.5-Pro/2.0-Flash、OpenAI o3/o4-mini
  - **开源 LVLMs**：Qwen2.5-VL-7B/72B、LLaVA-NeXT-Video-7B/72B、LLaVA-OneVision-7B/72B、Kimi-VL-A3B (16B)
  - **代表性多模态推理方法**：COG COM, VisCoT, SpaceR, VisProg, ViperGPT

- **评估指标**：多选题用准确率，数值题用 Mean Relative Accuracy (MRA)，与训练奖励一致。

## 4. 资源与算力

- **计算配置**：16 张 NVIDIA A100 (80G) GPU。
- **训练时长**：
  - 冷启动训练：约 24 小时（3 个 epoch，学习率 1×10⁻⁵）
  - 反思拒绝采样微调：约 3 小时（3 个 epoch）
  - 强化学习（GRPO）：batch size 32，每问题采样 8 条路径，最大累积图像数 α=42。具体时长未明确给出，但整体三阶段训练均在上述集群上完成。
- **训练数据规模**：
  - VILASR-ColdStart-33k（33,000 样本）
  - VILASR-RRS-8k（7,800 样本）
  - VILASR-RL-40k（40,000 样本）

## 5. 实验数量与充分性

- **主要实验**：在 5 个基准上对比了超过 10 种基线方法（表 1），结果全面。
- **消融实验**：在 VSI-Bench 上进行，分析了三个训练阶段分别对 8 个子任务（Object Count, Absolute Distance 等）的影响，以及 4 个行为指标（反思模式出现率、推理步数、边界框使用数、辅助线使用数）的变化（图 4）。
- **推理时间扩展分析**：评估 pass@1 与 pass@8，验证各阶段对模型能力的逐步提升与强化学习对单次推理能力的整合效果（图 5）。
- **统计分析**：报告了配对 t 检验结果，VILASR 在所有基准上显著优于基模型（p < 0.05）。
- **结论**：实验设计充分、客观公平，覆盖了多种模态和难度，消融实验验证了各阶段的独特贡献。

## 6. 论文的主要结论与发现

- 冷启动训练是建立空间推理基础的必需环节，单纯提示无法激发视觉操作能力。
- 反思拒绝采样显著提升了模型的自我修正行为（反思频率提高约 135%），且改变了绘图操作的使用模式（更多边界框、更少辅助线）。
- 强化学习优化了操作的效率（缩短了响应长度），并在数值精度任务上带来更大提升（因为密集奖励信号）。
- 推理时间扩展显示，冷启动和反思扩张了模型能力的上限（pass@8），而 RL 有效缩小了 pass@1 与 pass@8 的差距。
- VILASR 在迷宫导航（+64.5% vs 未使用 reasoning）和静态空间推理上表现尤为突出，在视频和多视图任务上也取得最佳或次优结果，总体平均提升 18.4%。

## 7. 优点

- **范式创新**：首次系统地将视觉绘图作为推理的核心组成部分，而非外部工具调用，避免了工具依赖和推理碎片化。
- **训练方案完备**：三阶段渐进式训练（冷启→反思→RL）设计合理，每个阶段都针对性地解决特定能力缺失（基础绘图、自我修正、全局优化）。
- **实验全面性**：涵盖图像、视频、多视图三类空间推理任务，对比多种基线和现有方法，且进行了详细消融和推理扩展分析。
- **可解释性与可迁移性**：绘图操作使得推理过程可视化，易于理解和调试；操作集简单（仅两种），便于未来扩展（如加入 3D 工具）。
- **资源与开源友好**：基于 Qwen2.5-VL-7B 开源模型，并开源了代码和模型（GitHub/Hugging Face），有利于社区复现与改进。

## 8. 不足与局限

- **任务覆盖有限**：训练只针对多项选择和数值型问题，无法处理自由形式的推理（如描述运动轨迹），限制了在开放式空间推理场景的适用性。
- **奖励函数耦合风险**：RL 奖励直接基于最终答案正确性，可能导致模型学习数据集特定的捷径，不利于泛化。论文也承认这一点，建议未来探索过程导向的奖励。
- **2D 绘图的局限性**：当前操作仅支持 2D 图像标注，无法直接处理 3D 空间关系或动态摄像机运动，对于复杂三维场景的推理能力有限。
- **计算成本较高**：三阶段训练需要 16 张 A100 GPU，RL 阶段开销更大，可能对资源有限的团队不友好。
- **数据依赖与合成数据质量**：冷启动数据依赖 Qwen2.5-72B-VL 生成，可能存在自动化偏差；反思拒绝采样依赖模型自身采样，若冷启动模型能力不足，可能影响后续阶段。

（完）
