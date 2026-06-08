---
title: Modularized Self-Reflected Video Reasoner for Multimodal LLM with Application to Video Question Answering
title_zh: 面向多模态大语言模型的模块化自反射视频推理器及其在视频问答中的应用
authors: "Zihan Song, Xin Wang, Zi Qian, Hong Chen, Longtao Huang, Hui Xue, Wenwu Zhu"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=dtmTQawQN2"
tags: ["query:mm-cot"]
score: 9.0
evidence: 具有显式推理路径的模块化多模态视频问答
tldr: 多模态大模型在视频问答中缺乏可解释性，无法展示推理路径。本文提出MSR-ViR，首次将模块化网络集成到多模态大模型中，通过空间-时间定位模块生成显式推理链。在视频问答基准上，该方法不仅保持了高性能，还提供了可解释的推理过程。该工作提升了多模态推理的透明度和可信度。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-dtmtqawqn2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1596, \"height\": 570, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dtmtqawqn2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1546, \"height\": 942, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dtmtqawqn2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 777, \"height\": 685, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dtmtqawqn2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1595, \"height\": 1047, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dtmtqawqn2/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1482, \"height\": 2135, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dtmtqawqn2/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1498, \"height\": 2045, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dtmtqawqn2/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1592, \"height\": 840, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dtmtqawqn2/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1590, \"height\": 894, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dtmtqawqn2/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1599, \"height\": 648, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dtmtqawqn2/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1645, \"height\": 653, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-dtmtqawqn2/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1450, \"height\": 690, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dtmtqawqn2/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 714, \"height\": 383, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dtmtqawqn2/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 844, \"height\": 459, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dtmtqawqn2/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 792, \"height\": 618, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dtmtqawqn2/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 752, \"height\": 638, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dtmtqawqn2/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1354, \"height\": 480, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dtmtqawqn2/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1510, \"height\": 676, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dtmtqawqn2/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1265, \"height\": 538, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dtmtqawqn2/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1326, \"height\": 236, \"label\": \"Table\"}]"
motivation: 多模态大模型在视频问答中缺乏可解释性，无法呈现推理路径。
method: 提出模块化自反射视频推理器MSR-ViR，集成模块化网络生成显式推理链。
result: 在视频问答任务上保持了高性能，同时提供了可解释的推理路径。
conclusion: 该工作增强了多模态推理的可解释性，有助于模型诊断和信任建立。
---

## Abstract
Multimodal Large Language Models (Multimodal LLMs) have shown their strength in Video Question Answering (VideoQA). However, due to the black-box nature of end-to-end training strategies, existing approaches based on Multimodal LLMs suffer from the lack of interpretability for VideoQA: they can neither present reasoning paths nor indicate where the answers are derived from the video. To address this issue, we propose **MSR-ViR** (**M**odularized **S**elf-**R**eflected **Vi**deo **R**easoner), which for the first time integrates modular networks to Multimodal LLMs, capable of providing VideoQA with explicit reasoning paths for more interpretability. Specifically, a **MoST-Grounding** (Modularized Spatial-Temporal Grounding) network is proposed to decompose complex questions via tree-structured policies, localizing relevant temporal and spatial segments within videos through step-by-step reasoning. The proposed MoST-Grounding network provides explicit visually grounded information for Multimodal LLMs with clear reasoning paths, thus enhancing interpretability for the predicted answers. To further improve the reasoning quality, we design an **Alternate Self-reflection Training Strategy** to jointly optimize policy generation and Multimodal LLMs. Experiments on real-world datasets demonstrate the superiority of our proposed MSR-ViR framework in video understanding, reasoning transparency, and providing explicit localization evidence for answers.

---

## 论文详细总结（自动生成）

# 论文《Modularized Self-Reflected Video Reasoner for Multimodal LLM with Application to Video Question Answering》详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：当前基于多模态大语言模型（Multimodal LLM）的视频问答（VideoQA）方法大多采用端到端黑盒训练，缺乏可解释性——模型既不能呈现推理路径，也无法指出答案源自视频的哪些时空片段。这限制了模型在需要透明度和可信度的场景中的应用。
- **整体含义**：论文旨在通过引入模块化网络（Modular Network）到多模态大语言模型中，首次为VideoQA提供显式的推理路径和视觉定位证据，从而提升可解释性，同时保持甚至提高问答准确性。
- **背景**：现有工作主要分为三类：① 黑盒端到端多模态大模型；② 基于定位的VideoQA方法（提供视觉证据但无推理路径）；③ 模块化方法（生成推理路径但依赖视频描述，丢失细节信息）。三者均存在明显缺陷。

## 2. 方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：提出MSR-ViR框架，包含三个核心组件：**问题解析器（Question Parser）**、**模块化时空定位网络（MoST-Grounding）**、**多模态大语言模型回答器（Multimodal LLM Answerer）**。通过“问题解析→逐步推理→视觉定位→答案生成”的流程提供可解释推理链。
- **关键技术细节**：
  - **问题解析器**：基于大语言模型（如Qwen2-7B），通过精心设计的指令和上下文示例，将复杂问题分解为树状结构化策略（JSON格式），指导MoST-Grounding模块调用不同子模块。
  - **MoST-Grounding模块**：包含**时间定位器**和**空间定位器**，共7种子模块（如DetectAct借助UniVTG做动作时间定位，LocateObj借助YOLO-World做目标空间定位）。策略递归调用子模块，逐步定位视频中的相关时间段和空间区域。
  - **多模态大模型回答器**：接收定位后的时空帧、全局视频表示（均匀采样帧平均池化）以及引导提示，生成答案。损失函数为交叉熵损失。
  - **交替自反射训练策略**：交替优化问题解析器（通过DPO强化学习，以多模态大模型损失为反馈信号）和多模态大模型（通过SFT）。周期为200步，使两者协同提升。
- **算法流程（文字说明）**：
  1. 问题解析器根据问题生成模块化执行策略。
  2. MoST-Grounding按策略递归调用子模块，依次进行时间定位和空间定位，输出相关视频帧和边界框。
  3. 多模态大模型基于定位帧、全局视频表示和引导提示生成答案。
  4. 训练时：固定问题解析器，SFT多模态大模型；固定多模态大模型，用DPO训练问题解析器，交替进行。

## 3. 实验设计：数据集、Benchmark、对比方法

- **数据集**：
  - **NExT-QA**（含Temporal, Causal, Descriptive子集）
  - **STAR**（使用Interaction和Sequence子集，排除Prediction和Feasibility类型）
  - **EgoSchema**（长视频，零样本测试）
  - **VideoMME**（长视频，零样本测试，含Short/Medium/Long子集）
  - **NExT-GQA**（基于NExT-QA的接地VideoQA数据集，提供人工标注时间跨度）
- **Benchmark**：遵循各数据集的官方划分，评价指标包括准确率（Acc）、mIoU、IoU@0.3/0.5、Acc@GQA等。
- **对比方法**：
  - 小型视觉语言模型：ATP, MIST, CoVGT, HiTeA, InternVideo, BLIP-2, InstructBLIP等。
  - 基于多模态大模型的方法：Qwen-VL, LLaVA-NeXT, Qwen2-VL, LLaVA-Video等。
  - 接地方法：TGB, SeViLa, GCG, LangRepo等。
  - 模块化方法：LLoVi, MoReVQA等。
  - 其他：VGT, VIOLETv2, Temp[CLIP], FrozenBiLM等。

## 4. 资源与算力

- 论文**明确提到**使用**一个NVIDIA A100 GPU**进行推理速度测试，但**未明确说明**训练所需的GPU数量、训练时长等具体算力信息。
- 训练框架：基于SWIFT，使用LoRA进行监督微调。问题解析器使用Qwen2-7B，多模态大模型使用Qwen-VL、LLaVA-NeXT、Qwen2-VL、LLaVA-Video。
- 训练超参数：交替周期200步，梯度累积16，SFT共5个epoch（NExT-QA和STAR），EgoSchema和VideoMME为零样本或1个epoch。

## 5. 实验数量与充分性

- **实验数量**：非常充分，涵盖：
  - 5个数据集（NExT-QA, STAR-sub, EgoSchema, VideoMME, NExT-GQA）上的评估。
  - 与多种基线（20+方法）的对比。
  - 全面的消融实验：移除自反射训练、空间定位模块、指令提示、全局表示等；替换时间定位模型（UniVTG vs R2-Tuning vs Moment-DETR）；框架采样策略。
  - 推理速度实验。
  - 计算复杂度理论分析。
- **充分性**：实验设计全面、客观、公平。不同数据集覆盖不同难度（短/长视频、不同推理类型），基线包括同等规模的多模态大模型（直接对比）以及不同的接地/模块化方法。消融实验有效验证了各组件贡献。结果报告了多个子集指标，避免单一指标偏差。

## 6. 主要结论与发现

- MSR-ViR框架在**NExT-QA、STAR-sub**上显著优于直接基线（Qwen-VL、LLaVA-NeXT）和其他接地方法，尤其在需要时间推理的场景下提升明显。
- 在**EgoSchema、VideoMME**零样本场景中，长视频子集提升更显著，验证了模块化推理在长视频中的优势。
- 在**NExT-GQA**上，MSR-ViR不仅提高了问答准确率，还实现了更精确的时间定位（mIoU、IoU@0.5、Acc@GQA均最佳），证明了其提供可解释视觉证据的能力。
- 消融实验表明：自反射训练、空间定位、全局表示、指令提示等组件均不可或缺；移除其中任何一项都会导致性能下降。
- 计算复杂度分析证明额外开销有严格上界，主要来自问题解析器（固定长度提示），与视频复杂度无关。

## 7. 优点

- **创新性**：首次将模块化网络与多模态大语言模型相结合，用于VideoQA的可解释性，填补了该领域空白。
- **方法论完整性**：从问题解析、逐步推理、视觉定位到答案生成，形成了完整、透明的推理链路。
- **训练策略巧妙**：交替自反射训练结合SFT和DPO，使问题解析器和多模态大模型相互提升，无需人工标注策略。
- **实验验证充分**：在多个基准数据集、多种指标、零样本/微调场景下全面验证，消融实验设计严谨。
- **理论分析**：提供了计算复杂度上界的严格证明，表明额外开销可控且可接受，增强了方法可信度。
- **可视化展示**：提供了推理路径示例，直观展示了可解释性。
- **模块可替换**：MoST-Grounding中的子模块（如时间定位模型）可灵活替换，利于后续改进。

## 8. 不足与局限

- **计算开销**：尽管有上界证明，但引入问题解析器（7B模型）和多个子模块，实际推理速度约为直接基线的2-3倍，在资源受限场景下可能成为瓶颈。
- **对子模块依赖**：性能受限于预小子模块（如UniVTG、YOLO-World）的准确度，若这些模块在特定场景下性能不佳，可能影响整体表现。
- **实验局限**：未在更多样化的视频类型（如自动驾驶、医学视频）上验证；未与其他模块化方法（如EN-TER、ProViQ）直接对比（这些方法使用了不同规模的大模型，部分使用了GPT-4等更强模型，导致公平性挑战）。
- **可扩展性**：问题解析的策略模板和子模块数量可能需随任务复杂度增加而扩展，论文未探讨如何自动扩展模块库。
- **泛化风险**：在STAR数据集上仅使用Interaction和Sequence子集，排除了Prediction和Feasibility问题，未验证框架在所有类型上的适用性。
- **训练细节缺失**：未报告具体训练GPU数量、总时长等算力资源信息，不利于复现。
- **消融实验范围**：虽然充分，但未测试不同大小的问题解析器（如1.5B vs 7B）在更多数据集上的影响，仅在NExT-QA上给出了速度和精度对比。

（完）
