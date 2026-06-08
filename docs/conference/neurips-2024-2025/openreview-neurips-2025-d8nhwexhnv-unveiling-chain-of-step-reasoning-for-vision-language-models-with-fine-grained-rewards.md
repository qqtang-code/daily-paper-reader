---
title: Unveiling Chain of Step Reasoning for Vision-Language Models with Fine-grained Rewards
title_zh: 面向视觉语言模型的链式步骤推理：基于细粒度奖励的方法
authors: "Honghao Chen, Xingzhou Lou, Xiaokun Feng, Kaiqi Huang, Xinlong Wang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=D8nHwexHNv"
tags: ["query:mm-cot"]
score: 9.0
evidence: 面向视觉语言模型的细粒度步骤推理
tldr: 现有视觉语言模型的链式推理多采用粗粒度步骤，难以评估中间推理质量。本文提出面向VLM的链式步骤推理框架，通过细粒度奖励机制精确评估每一步质量，并支持强化学习和推理时扩展。该框架简单透明，在多个视觉推理基准上取得显著提升，为多模态CoT提供了系统化的解决方案。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8nhwexhnv/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 778, \"height\": 823, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8nhwexhnv/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1449, \"height\": 749, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8nhwexhnv/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 898, \"height\": 565, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8nhwexhnv/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1440, \"height\": 644, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8nhwexhnv/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1444, \"height\": 495, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8nhwexhnv/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 903, \"height\": 631, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8nhwexhnv/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1147, \"height\": 687, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8nhwexhnv/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1402, \"height\": 684, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-d8nhwexhnv/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1454, \"height\": 726, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-d8nhwexhnv/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 833, \"height\": 245, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-d8nhwexhnv/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 837, \"height\": 243, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-d8nhwexhnv/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1288, \"height\": 350, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-d8nhwexhnv/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1102, \"height\": 206, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-d8nhwexhnv/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1422, \"height\": 496, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-d8nhwexhnv/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1090, \"height\": 387, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-d8nhwexhnv/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 859, \"height\": 373, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-d8nhwexhnv/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 885, \"height\": 242, \"label\": \"Table\"}]"
motivation: 现有VLM的CoT推理步骤粗粒度，中间步骤质量评估困难，限制了强化学习效果。
method: 设计细粒度步骤拆解方法，结合逐步奖励模型，对每一步推理质量进行精确评估，并用于强化学习训练。
result: "在VQA和视觉推理任务上，该方法相比基线提升5-8%，且推理时间可灵活调整。"
conclusion: 细粒度步骤推理结合奖励模型是提升多模态CoT有效性的关键途径。
---

## Abstract
Chain of thought reasoning has demonstrated remarkable success in large language models, yet its adaptation to vision-language reasoning remains an open challenge with unclear best practices. Existing attempts typically employ reasoning chains at a coarse-grained level, which struggles to perform fine-grained structured reasoning and, more importantly, are difficult to evaluate the reward and quality of intermediate reasoning. In this work, we delve into chain of step reasoning for vision-language models, enabling assessing reasoning step quality accurately and leading to effective reinforcement learning and inference-time scaling with fine-grained rewards. We present a simple, effective, and fully transparent framework, including the step-level reasoning data, process reward model (PRM), and reinforcement learning training. With the proposed approaches, our models set strong baselines with consistent improvements on challenging vision-language benchmarks. More importantly, we conduct a thorough empirical analysis and ablation study, unveiling the impact of each component and several intriguing properties of inference-time scaling. We believe this paper serves as a baseline for vision-language models and offers insights into more complex multimodal reasoning. Our dataset, PRM, and code at https://github.com/baaivision/CoS.

---

## 论文详细总结（自动生成）

# 面向视觉语言模型的链式步骤推理：基于细粒度奖励的方法——论文总结

## 1. 核心问题与整体含义
- **研究动机**：链式思维（CoT）推理在大型语言模型中取得了显著成功，但其在视觉语言模型（VLM）中的应用仍存在挑战。现有方法通常采用粗粒度的推理链（如长段无结构文本），导致难以评估中间推理步骤的质量，进而无法有效利用强化学习（RL）和推理时扩展来提升性能。
- **核心问题**：如何为VLM设计细粒度、结构化的步骤推理，并精确评估每一步的奖励，以指导RL训练和推理时优化？
- **整体含义**：本文提出**Chain-of-Step (CoS)**框架，通过将推理分解为可评估的步骤、训练过程奖励模型（PRM）以及基于细粒度奖励的迭代偏好学习，显著提升了VLM在复杂多模态推理任务上的能力。研究表明，步骤质量比推理长度更重要，且结合步骤和最终答案的评估效果最佳。

## 2. 方法论：核心思想、关键技术细节与流程
- **核心思想**：将整个推理链分解为多个**逻辑连贯的步骤**，每个步骤由三部分组成：**Name**（步骤摘要）、**Thought**（详细推理）、**Reflection**（与视觉信息和前序步骤的联系）。使用特殊标记（如 `<|reasoning_step_start|>`）实现结构化输出，确保步骤可分割、可评估。
- **关键技术细节**：
  - **步骤定义与数据生成**：通过GPT-4o（给定问题与参考答案）生成了**ShareGPT-Step-300K**数据集，包含300K个结构化步骤推理样例，覆盖数学、科学、图表、世界知识等17个数据集，确保多样性。
  - **过程奖励模型 (PRM)**：使用两种方法自动标注步骤正确性：Monte Carlo估计（类似Math-Shepherd）和LLM-as-Judge（GPT-4o）。训练基于InternVL2.5-38B的PRM（200K标注数据，二元交叉熵损失），用于评估中间步骤质量。
  - **强化学习训练（迭代DPO）**：以SFT模型为策略网络，使用PRM对生成的16条推理路径进行打分（加权综合步骤平均分与最终答案分），选择正负对比对，应用迭代DPO（3轮）优化模型。公式为标准DPO损失，β=0.1，阈值t确保正负样本差异足够。
  - **推理时扩展**：支持步骤级束搜索（Step-level Beam Search）：在每一步用PRM评分，保留最优步骤继续生成，采样效率与Best-of-N一致。
- **算法流程（文字描述）**：
  1. **Stage 1 (SFT)**：在ShareGPT-Step-300K上对基座VLM进行监督微调，使其学会结构化步骤推理。
  2. **Stage 2 (PRM训练)**：使用MC估计或GPT-4o标注步骤正确性数据，训练一个PRM（基于InternVL2.5-38B）。
  3. **Stage 3 (迭代偏好学习)**：用PRM评估模型生成的推理路径，构建正负对比对，执行迭代DPO（3轮），逐步提升推理质量。

## 3. 实验设计：数据集、基准与对比方法
- **数据集/基准**：6个代表性多模态推理基准：
  - MathVista（数学推理）
  - MMStar（视觉内容依赖的多模态问题）
  - MMMU（大学级多学科推理）
  - M3CoT（多领域多步骤链式思维）
  - AI2D（科学知识推理）
  - ChartQA（图表逻辑推理）
- **对比方法**：包括主流开源VLM：LLaVA-1.5, IXC-2.5, Ovis1.5-LLaMA3, LLaVA-CoT, LlamaV-o1, Vision-R1-LlamaV, R1-VL, MiniCPM-V-2-6, LLaVA-OneVision, Qwen2-VL, Insight-V, InternVL-2.5, LLaVA-NeXT-LLaMA3, InternVL2.5-MPO 等。
- **实验设置**：作者以**LLaVA-NeXt-8B**和**InternVL2.5-MPO-8B**作为基座，分别测试SFT和迭代DPO的效果，并消融了奖励形式、推理模式、PRM基座、推理长度等。

## 4. 资源与算力
- **训练资源**：
  - **SFT**：在8×NVIDIA-A800 GPU上运行约9小时，数据规模300K，批次大小128，学习率5e-6。
  - **迭代DPO（3轮）**：在8×NVIDIA-A800 GPU上总计约6小时，每轮构建约20K偏好对，批次大小256，学习率1e-6。
  - **PRM训练**：在16×NVIDIA-A800 GPU上进行2个epoch，数据200K，学习率1e-6，批次大小128。
- **推理资源**：未详细说明，但提到采样16条路径进行PRM评估。

## 5. 实验数量与充分性
- **总体实验数量**：论文进行了大量且系统的实验：
  - **主表（Table 1）**：在6个基准上对比12+种方法，包含两个基座模型的SFT和DPO结果。
  - **消融研究**：
    - 步骤权重（Fig 3）：从0%到100%调整步骤得分权重，评估最佳16选1精度（M3CoT）。
    - 推理时扩展（Fig 5）：在M3CoT和MMStar上比较Pass@N、Self-Consistency、PRM Best-of-N、PRM Step Beam Search，样本数从1到64。
    - 奖励来源（Table 2）：Outcome（最终答案正确性）、PRM Answer、PRM Step&Answer三种选择策略。
    - PRM基座（Table 3）：LLaVA-NeXt-8B、InternVL2.5-8B、InternVL2.5-38B在seen/unseen数据上的步骤和答案准确率。
    - 推理长度变化（Fig 6）：outcome DPO vs PRM DPO的步骤长度随迭代变化。
    - 推理模式（Table 4）：No Reason、Direct Prompt、CoS三种推理格式（SFT+RL对比）。
    - GRPO算法（Table 5）：outcome GRPO vs CoS GRPO（细粒度PRM奖励）。
    - 逐步骤DPO尝试（附录Table 9）：per-step-wise DPO效果不佳。
- **充分性与公平性**：
  - 实验设计较全面，涵盖了方法关键组件的独立验证。
  - 对比基线为开源SOTA，且复现了标准训练流程。
  - 但是所有实验均在单一精度的GPU上进行，未报告多次随机种子结果，存在一定偏差风险。

## 6. 主要结论与发现
1. **CoS框架显著提升VLM推理性能**：在6个基准上平均提升4.9%（LLaVA-NeXt）和3.2%（InternVL2.5-MPO），达到新的SOTA（73.4%平均分）。
2. **步骤与答案综合评估最优**：步骤权重在20%时最佳，单纯依赖步骤或答案均次优（Fig 3, Table 2）。
3. **较长的推理不一定更好**：对于VLM，步骤质量比长度更重要。outcome DPO导致长度增加但质量不稳定，而PRM DPO先缩短步骤再缓慢增长（Fig 6）。
4. **PRM指导的RL优于outcome RL**：在迭代DPO和GRPO中都得到验证（Table 2, Table 5）。
5. **推理时步骤束搜索有效**：在N从1到64时，PRM-BS相比PRM Best-of-N有持续提升（Fig 5）。
6. **更强的PRM基座提升步骤评估准确率**：38B模型在步骤准确率上优于8B模型（Table 3）。

## 7. 优点
- **方法设计简洁且透明**：结构化步骤定义清晰，使用特殊token保证格式稳定，易于分割和评估。
- **细粒度奖励实现精确引导**：PRM能评估中间步骤质量，避免了单纯依赖最终答案的噪声，提升了RL的有效性。
- **推理时扩展灵活**：步骤级束搜索在相同采样开销下优于最佳N选择，实用性强。
- **实验全面且深入**：覆盖多类基准、多种消融、两种RL算法（DPO、GRPO），结论可靠。
- **代码、数据集和模型均已开源**，可复现性强。

## 8. 不足与局限
- **过程标注数据可靠性有限**：Monte Carlo估计和LLM-as-Judge无法保证100%正确，存在噪声。作者也承认人工标注虽然更好但成本高。
- **逐步骤DPO尝试失败**：由于正负步骤差异过小，模型倾向于拒绝输出任何步骤，无法直接用于训练（附录Table 9）。这表明细粒度步骤对比需要更好的构造策略。
- **未考虑多轮图像交互**：方法目前仅适用于单次图像输入，不涉及多轮视觉对话中的动态步骤推理。
- **计算成本较高**：SFT和迭代DPO需要8或16张A800，对于资源有限的研究组可能难以复现。
- **推理时扩展的代价**：虽然束搜索采样效率与Best-of-N相同，但需要多次调用PRM，引入额外推理开销。
- **偏差风险**：数据集主要来自公开学术基准，可能无法覆盖真实场景中的复杂视觉推理（如低质量图像、模糊问题）。此外，SFT数据由GPT-4o生成，存在模型特有的偏差或伪影。

（完）
