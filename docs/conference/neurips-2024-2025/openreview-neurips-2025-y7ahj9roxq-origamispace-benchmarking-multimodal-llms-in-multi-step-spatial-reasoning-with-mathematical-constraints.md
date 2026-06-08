---
title: "ORIGAMISPACE: Benchmarking Multimodal LLMs in Multi-Step Spatial Reasoning with Mathematical Constraints"
title_zh: ORIGAMISPACE：带数学约束的多步空间推理基准
authors: "Rui Xu, Dakuan Lu, Zicheng Zhao, Xiaoyu Tan, Xintao Wang, Siyu Yuan, Jiangjie Chen, Xu Yinghui"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=y7ahj9RoXQ"
tags: ["query:mm-cot"]
score: 7.0
evidence: 多步空间推理与数学约束
tldr: 该论文提出ORIGAMISPACE基准，通过折纸任务评估多模态大模型的多步空间推理能力。数据集包含350个实例，每个实例有严格的折痕图和约束。实验表明当前模型在复杂空间推理和数学约束处理上仍有挑战。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-y7ahj9roxq/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1161, \"height\": 594, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-y7ahj9roxq/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1439, \"height\": 622, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-y7ahj9roxq/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1439, \"height\": 491, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-y7ahj9roxq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1458, \"height\": 1007, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-y7ahj9roxq/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1469, \"height\": 961, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-y7ahj9roxq/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1456, \"height\": 1778, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-y7ahj9roxq/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1456, \"height\": 2306, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-y7ahj9roxq/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1457, \"height\": 1465, \"label\": \"Table\"}]"
motivation: 多模态大模型在复杂空间推理中的评估尚缺乏多步推理和数学约束的基准。
method: 构建基于折纸任务的基准，包含折痕图和组合约束，设计多步推理问题。
result: 模型在简单任务上表现尚可，但在复杂多步推理中性能显著下降。
conclusion: 该基准揭示了当前多模态大模型在空间推理方面的局限性。
---

## Abstract
Spatial reasoning is a key capability in the field of artificial intelligence, especially crucial in areas such as robotics, computer vision, and natural language understanding. However, evaluating the ability of multimodal large language models (MLLMs) in complex spatial reasoning still faces challenges, particularly in scenarios requiring multi-step reasoning and precise mathematical constraints. This paper introduces ORIGAMISPACE, a new dataset and benchmark designed to evaluate the multi-step spatial reasoning ability and the capacity to handle mathematical constraints of MLLMs through origami tasks. The dataset contains 350 data instances, each comprising a strictly formatted crease pattern (CP diagram), the Compiled Flat Pattern, the complete Folding Process, and the final Folded Shape Image. We propose four evaluation tasks: Pattern Prediction, Multi-step Spatial Reasoning, Spatial Relationship Prediction, and End-to-End CP Code Generation. For the CP code generation task, we design an interactive environment and explore the possibility of using reinforcement learning methods to train MLLMs. Through experiments on existing MLLMs, we initially reveal the strengths and weaknesses of these models in handling complex spatial reasoning tasks.

---

## 论文详细总结（自动生成）

好的，以下是根据您提供的论文内容生成的结构化、深入、客观的中文总结。

# ORIGAMISPACE：带数学约束的多步空间推理基准——论文详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

*   **核心问题**：当前的多模态大语言模型（MLLMs）在复杂的空间推理任务上表现如何，尤其是在需要多步推理和严格数学约束的场景下？现有基准多聚焦于静态图像或简单场景，缺乏对连续空间变换、多步操作和物理数学约束的综合评估。
*   **研究动机**：
    *   **弥补评估空白**：现有基准如CLEVR、NLVR2等主要评估静态场景理解或图像对比较，而StepGame、LEGO-Puzzles虽涉及多步过程，但要么局限于纯文本，要么未强调精确的几何和物理约束。
    *   **利用折纸的天然优势**：折纸艺术是一个理想的评估平台，其折叠过程天然包含**多步推理**（每一步依赖上一步结果）、**严格的数学约束**（如Maekawa定理、Kawasaki定理）和**空间想象**（从2D折痕图到3D立体形态的转换）。
*   **整体含义**：该论文旨在通过构建基于折纸的基准（ORIGAMISPACE），来系统地揭示当前MLLMs在处理复杂、动态、受约束的空间推理任务时的能力与不足。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

*   **核心思想**：利用折纸艺术的结构化、多步骤、强约束特性，设计一套从简单理解到复杂生成的递进式任务，以全面评估MLLMs的空间推理能力。
*   **关键技术细节**：
    1.  **数据集构建**：收集并验证了350组高质量的折纸数据（来自网站、论坛、书籍）。每组数据包含：
        *   **CP Diagram (折痕图)**：标准化的2D折痕图，可用代码表示。
        *   **Compiled Flat Pattern (编译后平面图)**：通过优化的折纸编译器计算出的最终折叠状态的2D表示，包含折痕位置和堆叠关系。
        *   **Folded Shape Image (折叠后形状图像)**：直观的3D渲染或照片。
        *   **Folding Process (折叠过程)**：多步骤的顺序图像（从教程中收集）。
    2.  **编译器优化**：改进了现有的折纸编译器，使其能：
        *   标记每条折痕在编译后图像中的位置。
        *   计算纸张堆叠顺序信息。
        *   构建MLLMs与编译器的直接交互接口。
        *   提供四种细粒度错误反馈：**CSE (CP代码语法错误)**、**GIF (几何不可折叠)**、**PSI (纸张自交/穿透)**、**AFS (折叠状态不明确)**。
    3.  **任务设计**：提出四个难度递进的评估任务：
        *   **图案预测 (Pattern Prediction)**：根据折痕图选择正确的最终折叠形状名称（多项选择）。
        *   **多步空间推理 (Multi-step Spatial Reasoning)**：对随机打乱的折叠步骤图像进行正确排序（多项选择）。
        *   **空间关系预测 (Spatial Relationship Prediction)**：预测折叠后的空间状态，细分为三个子任务：
            *   空间姿势定位 (Spatial Pose Localization)
            *   分层关系分析 (Layering Relationship Analysis)
            *   几何变化分析 (Geometric Change Analysis)
        *   **端到端CP代码生成 (End-to-End CP Code Generation)**：根据目标折叠形状的平面图和图像，生成符合所有约束的CP代码。
    4.  **代码生成评估框架**：设计了多维度的评估指标（总分为四个维度的加权平均，各占25%）：
        *   **拓扑结构相似性 (TSS)**：比较顶点、边、面、折痕类型分布。
        *   **几何相似性 (GS)**：通过双向Hausdorff距离比较3D点云位置、二面角分布、边界框比例。
        *   **约束满足度 (CS)**：检查关键约束类型（Taco-Taco, Taco-Tortilla, 传递性）和局部平坦可折叠定理（Maekawa、Kawasaki）的满足情况。
        *   **最终折叠状态相似性 (FFS)**：直接比较生成的3D模型与参考模型的点云Hausdorff距离和分层关系。

## 3. 实验设计：使用的数据集/场景、基准、对比方法

*   **数据集**：ORIGAMISPACE数据集，包含350个实例，以及额外471组用于训练的无中间过程的实例。前三个任务共设计了1500道多项选择题（图案预测350道、多步推理250道、空间关系预测900道），代码生成任务包含120道生成题。
*   **基准与对比方法**：
    *   **模型对比**：评估了多个代表性MLLM，包括：
        *   **开源模型**：MiniCPM-o 2.6, LLaVA-1.5-7B, DeepSeek-VL2, NVILA-15B, VideoLLaMA3-7B, Qwen2.5-VL (7B/32B/72B), InternVL2.5-78B。
        *   **闭源模型**：Claude-3.5-Sonnet, GPT-4o, Gemini2.5-Flash/Pro。
    *   **人类基线**：招募了5名普通人和3名折纸专家来完成任务1-3。
    *   **三种学习策略**（针对代码生成任务）：
        *   **上下文学习 (In-context Learning)**：给模型详细指令和示例，要求一次生成完整代码。
        *   **环境学习 (Environmental Learning)**：模型与编译器进行迭代交互（最多10轮），根据编译结果反馈（错误类型或部分成功）修改代码。
        *   **强化学习 (Reinforcement Learning)**：在环境学习的基础上，利用额外的471组数据，通过TRICO算法（基于PPO）对Qwen2.5-VL-32B模型进行多轮训练。奖励机制包括中间奖励（基于部分质量进展和编译成功）、步骤惩罚和最终奖励（基于生成代码的评估总分）。

## 4. 资源与算力

*   **明确提及的算力**：仅在强化学习实验中提到，使用了**16块H100 GPU**，对Qwen2.5-VL-32B进行了**10.2小时**的训练。其他实验（如评估所有模型的任务1-4）未明确说明使用的具体GPU型号、数量或总耗时。

## 5. 实验数量与充分性

*   **实验数量**：
    *   任务1-3：在10余种MLLM上进行了评估，每项任务报告了三次运行的平均值和标准差。
    *   任务4：在7种模型（开源和闭源）上对比了上下文学习和环境学习，并在Qwen2.5-VL-32B上测试了强化学习，结果展示了编译通过率、各维度得分和总分。
    *   消融/分析实验：探究了交互轮次对环境学习性能的影响（图3），以及数学约束的影响分析。
*   **充分性与客观性**：
    *   **积极方面**：覆盖了从7B到78B的不同规模的模型，包括开源和闭源，对照了人类专家和普通人基线，提供了统计误差。任务设计细致，评估指标全面（从错误类型到多维相似度）。环境学习和强化学习的探索增强了实验的深度。
    *   **可能不足**：强化学习仅在单一模型（Qwen2.5-VL-32B）上测试，泛化性有待验证。环境学习的交互轮次上限（10轮）是人为设定的，可能不是最优。实验未涉及对模型大小、架构等因素的深入消融分析。数据集规模（350）相对较小，可能限制统计显著性。

## 6. 论文的主要结论与发现

1.  **ORIGAMISPACE具有挑战性**：目前所有MLLM在各项任务上的表现均远低于人类专家，甚至部分模型在简单任务上接近随机水平（25%）。这表明现有模型在复杂、多步空间推理方面仍存在巨大短板。
2.  **模型能力排名**：在各项任务中，闭源模型（如GPT-4o、Gemini 2.5 Pro）普遍优于开源模型，并展现出最强的空间推理能力。Qwen2.5-VL-72B和InternVL2.5-78B是开源模型中的佼佼者。
3.  **学习策略的显著影响**：在代码生成任务中，**环境学习**（迭代交互）远优于一次性生成的**上下文学习**，证明了通过反馈进行试错和规划的重要性。
4.  **强化学习的潜力**：基于PPO的强化学习能够进一步提升模型性能，使32B模型超越72B模型（在部分指标上），证明了通过奖励机制优化模型的有效性。
5.  **数学约束是主要瓶颈**：失败的分析表明，满足数学约束（如几何可折叠性、非自交）是生成有效CP代码最困难的环节，即使是顶级模型也表现不佳，揭示了模型在深层几何与分层推理方面的不足。

## 7. 优点：方法或实验设计上的亮点

*   **创新性的评估平台**：创造性选择折纸作为测试空间推理的载体，完美融合了多步推理、数学约束和空间想象，填补了现有基准的空白。
*   **精细化任务设计**：四个任务由浅入深，从识别、排序、预测到生成，覆盖了空间推理能力的多个维度。特别是空间关系预测的三个子任务和代码生成的四维评估体系，提供了非常细粒度的能力诊断。
*   **交互式评估环境**：改造并提供了编译器交互接口，使得环境学习和强化学习成为可能，不仅用于评估，也探索了提升模型能力的新途径，极具启发性。
*   **严谨的错误分类**：编译器的四种错误反馈（CSE、GIF、PSI、AFS）具体且具解释性，能清晰定位模型生成代码失败的原因，为模型改进提供了明确方向。

## 8. 不足与局限

*   **数据集规模有限**：350个核心实例的规模相对较小，可能影响统计分析的可靠性和结论的普适性。未来可通过半自动生成技术扩展。
*   **领域特异性**：折纸是一个高度结构化的领域。模型在该基准上表现出的能力，在多大程度上能泛化到其他形态的空间推理任务（如动态真实场景、抽象图表）上仍不明确。
*   **任务设计可能不全面**：当前的四个任务侧重于静态理解、排序、关系预测和代码生成，可能未完全覆盖空间推理的其他方面，如基于自然语言的实时路径规划、三维空间中的物理交互等。
*   **人类评估细节有限**：虽然介绍了人类评估的招募方式和规则，但未报告具体评估过程（如时间限制、实验环境等），也未提供评估者间信度等统计指标。
*   **强化学习探索的局限性**：强化学习实验仅在一个模型（Qwen2.5-VL-32B）上执行，且未与更广泛的环境学习超参数进行对比，其有效性仍需更多验证。

（完）
