---
title: "MiCo: Multi-image Contrast for Reinforcement Visual Reasoning"
title_zh: MiCo：用于强化视觉推理的多图像对比
authors: "Xi Chen, Mingkang Zhu, Shaoteng Liu, Xiaoyang Wu, Xiaogang Xu, Yu Liu, Xiang Bai, Hengshuang Zhao"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=TUCHMVzXin"
tags: ["query:mm-cot"]
score: 8.0
evidence: 多图像对比实现跨图像思维链推理
tldr: 多图像视觉推理需要模型链接不同图像中的线索，但传统RL方法依赖人工问答对。本文受自监督视觉表示学习启发，构建图像三元组（同一图像的两个增强视图和另一相似图像），让模型生成推理过程以对比异同。通过规则RL训练，实现无需标注的跨图像CoT推理。实验表明该方法有效提升了跨图像推理能力。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-tuchmvzxin/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1400, \"height\": 513, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tuchmvzxin/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1433, \"height\": 312, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tuchmvzxin/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1407, \"height\": 1327, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-tuchmvzxin/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1448, \"height\": 657, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-tuchmvzxin/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1435, \"height\": 748, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-tuchmvzxin/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 614, \"height\": 810, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-tuchmvzxin/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 608, \"height\": 811, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-tuchmvzxin/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1387, \"height\": 212, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-tuchmvzxin/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1397, \"height\": 325, \"label\": \"Table\"}]"
motivation: 跨图像多步推理缺乏无需人工标注的有效训练方法。
method: 构建图像三元组，利用对比任务引导模型生成CoT推理过程，结合规则RL训练。
result: 在跨图像推理任务上取得显著效果，验证了无监督训练范式的可行性。
conclusion: 提出了一种新颖的无需标注的多图像推理训练方法。
---

## Abstract
This work explores enabling Chain-of-Thought (CoT) reasoning to link visual cues across multiple images. A straightforward solution is to adapt rule-based reinforcement learning for Vision-Language Models (VLMs). However, such methods typically rely on manually curated question-answer pairs, which can be particularly challenging when dealing with fine-grained visual details and complex logic across images. Inspired by self-supervised visual representation learning, we observe that images contain inherent constraints that can serve as supervision. Based on this insight, we construct image triplets comprising two augmented views of the same image and a third, similar but distinct image. During training, the model is prompted to generate a reasoning process to compare these images (i.e., determine same or different). Then we optimize the model with rule-based reinforcement learning. Due to the high visual similarity and the presence of augmentations, the model must attend to subtle visual cues and perform logical reasoning to succeed. Experimental results demonstrate that, although trained solely on visual comparison tasks, the learned reasoning ability generalizes effectively to a wide range of questions. Without relying on any human-annotated question-answer pairs, our method achieves significant improvements on multi-image reasoning benchmarks and shows strong performance on general vision tasks.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

多图像视觉推理要求模型能够链接不同图像中的细粒度视觉线索，并进行逻辑推理（如比较异同、跟踪变化、理解对应关系）。当前视觉语言模型（VLM）在单图像理解上表现良好，但在跨图像任务中常出现幻觉，例如无法正确识别相机运动、区分不同物体、跟踪语义变化等。现有基于规则强化学习的方法依赖人工标注的问答对，构建成本高且难以覆盖细粒度视觉细节。本文受自监督视觉表示学习的启发，提出利用图像自身固有的约束（如对比一致性）作为监督信号，从而无需人工标注即可激励 VLM 进行多图像推理。

### 2. 论文提出的方法论：核心思想、关键技术细节

**核心思想**：通过构建具有挑战性的图像对比三元组，引导模型生成思维链（CoT）推理过程，并使用基于规则的强化学习进行优化，以学习跨图像比较的核心元能力。

**关键技术细节**：

- **图像三元组构建**：对同一源图像 **Iₐ** 应用随机裁剪和缩放得到两个增强视图 **T₁(Iₐ)** 和 **T₂(Iₐ)**；再选取一个与 **Iₐ** 相似但不同的图像 **I_b** 及其增强视图 **T₃(I_b)**，组成三元组 `{T₁(Iₐ), T₂(Iₐ), T₃(I_b)}`。相似图像来源：同一视频中的不同帧（时间间隔约2秒，通过SSIM过滤高度相似帧）或图像编辑数据集（如 OmniEdit、UltraEdit，通过MSE过滤差异过大样本）。
- **问答提示设计**：提示模型在 `<think>` 标签内输出推理过程，在 `<answer>` 标签内输出三对比较结果（T/F）。除三元组外，还引入图像对比较问题，并使用 GPT-4o 扩展问题表述的多样性。
- **Augmented GRPO**：基于 GRPO 框架，在弱增强（易）样本上采样多个推理轨迹，然后利用这些轨迹及其优势值在强增强（难）样本上优化策略。具体：
  1. 对三元组分别施加弱增强 **T_w** 和强增强 **T_s**。
  2. 从旧策略 **π_θold** 基于弱增强提示 **q_w** 采样 G 个响应 {o_i}。
  3. 使用规则奖励（格式正确性和答案正确性）计算每个响应的奖励 R_i，并归一化得到优势 **Â_i**。
  4. 在强增强提示 **q_s** 上，利用采样轨迹计算策略梯度，目标函数包含剪切项和 KL 散度正则项。

**算法流程**（文字描述）：
1. 输入：策略 π_θ，旧策略 π_θold，三元组数据集 D，训练步骤 T_max，组大小 G，裁剪参数 ϵ，弱/强增强算子。
2. 每步训练：采样一个三元组，分别施加弱和强增强 → 构建两个提示 q_w 和 q_s → 从 π_θold 基于 q_w 采样 G 个 CoT 响应 → 计算奖励和优势 → 在 q_s 上优化 π_θ 以最大化加权似然（包含裁剪和 KL 正则）。
3. 重复直到收敛。

**奖励设计**：二元格式奖励（匹配标签）+ 准确率奖励（三对比较全部正确才得1分），权重1:1。

### 3. 实验设计：数据集、基准和对比方法

**主要基准**：
- **VLM2-Bench**：专为评估跨图像细粒度线索链接能力设计，包含 General、Object、Person 三个轨道，子任务有 Mat、Trk、Cpr、Cnt、Grp、VID。
- **其他多图像基准**：MuirBench、BLINK。
- **单图像基准**：MMStar、MMMU、HallusionBench、MathVista，用于检验泛化能力。

**训练数据**：来自 OmniEdit（编辑数据集）和 VidGen-1M（视频帧）。

**对比方法**：
- 通用 VLM：LLaVA-OneVision、Qwen2.5-VL-7B、InternVL2.5-8B/26B、GPT-4o 等。
- 基于推理的方法（标记 •）：MM-Eureka-7B、NoisyRollout-7B、ThinkLite-VL-7B、VLAA-Thinker-7B。
- 消融中还包括 SFT、No-CoT RL、不同数据源、增强策略等变体。

**评估方式**：所有模型使用 VLMEvalKit 按照默认超参数评估，推理基线使用官方提示格式。

### 4. 资源与算力

论文明确说明：
- 训练使用 **8 块 A100 GPU**。
- 学习率 1e-6，batch size 16，每样本生成 8 个 rollout，共训练 **600 次迭代**。
- 未给出具体训练时长（如小时数），也未说明是否使用混合精度或分布式策略。

### 5. 实验数量与充分性

- **主要实验**（Table 1）：在 VLM2-Bench 上对比 10+ 个模型，涵盖三种轨道，报告详细子任务分数和整体平均。
- **消融实验**（Table 2）：共6组，分别探究学习范式（SFT、No-CoT RL、CoT RL）、数据源（编辑数据1/2、视频数据及其组合）、rollout增强组合（强弱搭配）、样本形式（对、三元组、混合）、提示多样性（单/20/50变体）、图像增强类型（裁剪+缩放、翻转、旋转、颜色变换）。每组都报告 General、Object、Person 轨道平均分。
- **泛化实验**（Table 3）：在 MuirBench、BLINK、MMStar、MMMU、HallusionBench、MathVista 上对比，包含6个基准。
- **任务分析**（Table 4）：在 MuirBench 和 BLINK 的特定子任务上（如视觉检索、语义对应、空间关系等）与 MM-Eureka、VLAA-Thinker 对比。
- **定性分析**（图3）：展示4个示例及 MiCo 的推理过程。
- **失败尝试**：置信度重加权、重要性采样未带来提升，并分析了可能原因。

总体而言，实验设计系统、消融全面，覆盖了训练数据、增强策略、学习范式等核心因素，对比方法多样。但在一些基准上仅报告单一指标，未提供误差棒或多次运行统计。不过，本文遵循该领域常见做法，公平性可接受。

### 6. 论文的主要结论与发现

- 在 VLM2-Bench 上，**MiCo 7B 以 61.06% 的整体平均分超越所有基线**，包括 GPT-4o（60.36%），证明了无需人工标注即可获得强大的跨图像推理能力。
- 对比学习框架有效：**CoT RL 显著优于 SFT 和 No-CoT RL**（Table 2a）。
- 数据来源和增强策略关键：**混合编辑数据+视频数据**、**弱增强采样+强增强优化**的组合最优（Table 2b,c）。
- 模型学到的视觉比较能力**泛化到多图像基准（MuirBench、BLINK）及部分单图像任务**（如 MMStar、MMMU 略有提升），但在视觉数学（MathVista）上提升有限。
- 任务分析显示：**对比训练在视觉检索、语义对应、空间关系等对应类任务上优势明显**，但在场景理解、法医检测、相对深度等依赖先验知识或单图像 QA 的任务上落后于专用推理模型。
- 人脸相关任务 CoT 推理效果有限，认为原因是面部细微差异难以语言化。

### 7. 优点：方法或实验设计上的亮点

- **自监督范式的创新应用**：将对比学习原理引入多图像推理训练，无需任何人工问答对标注，大幅降低数据成本。
- **Augmented GRPO**：通过增强强度分离（弱增强采样、强增强优化）提升了训练效率和模型的鲁棒性。
- **数据构建简洁高效**：仅需视频帧或编辑数据集中的相似图像对，无需人工标注，可大规模扩展。
- **实验全面且消融充分**：系统验证了学习范式、数据源、增强策略、样本形式、提示多样性等设计选择，结论可靠。
- **7B 模型超越 GPT-4o**：在 VLM2-Bench 上以小参数量实现超越闭源模型，展示了强化学习在视觉推理中的潜力。

### 8. 不足与局限

- **任务覆盖有限**：在面部识别、视觉数学（MathVista）和空间理解（相对深度）等需要结构化先验的任务上表现不佳，说明当前对比训练未充分覆盖这些技能。
- **数据来源依赖**：依赖视频帧和编辑数据集，若任务场景偏离这些数据分布，泛化能力可能受限。
- **部分失败尝试未奏效**：置信度重加权和重要性采样未能提升性能，表明该方法在奖励设计上仍有改进空间。
- **实验统计可增强**：未报告误差棒或多次运行结果，也未详细说明超参数调优过程，可能影响结果的鲁棒性。
- **应用风险**：改进的跨图像比较能力可能被用于隐私侵犯或监控等不当场景，论文虽讨论了社会影响，但未提供具体防护措施。

（完）
