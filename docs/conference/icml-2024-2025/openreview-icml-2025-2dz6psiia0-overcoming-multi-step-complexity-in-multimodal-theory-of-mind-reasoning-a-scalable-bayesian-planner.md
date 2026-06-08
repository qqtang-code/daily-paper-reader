---
title: "Overcoming Multi-step Complexity in Multimodal Theory-of-Mind Reasoning: A Scalable Bayesian Planner"
title_zh: 克服多模态心理理论推理中的多步复杂性：可扩展贝叶斯规划器
authors: "Chunhui Zhang, Zhongyu Ouyang, Kwonjoon Lee, Nakul Agarwal, Sean Dae Houlihan, Soroush Vosoughi, Shao-Yuan Lo"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=2dz6psiiA0"
tags: ["query:mm-cot"]
score: 8.0
evidence: 多模态心理理论中的多步推理
tldr: 现有计算心理理论方法在多模态环境中难以扩展，受限于多步规划复杂度。本文提出可扩展贝叶斯心理理论规划器，将复杂度分解为逐步骤贝叶斯更新，并利用弱到强控制机制用小语言模型细化似然估计。实验表明该方法在多步多模态推理任务上具有有效性和可扩展性。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-2dz6psiia0/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 806, \"height\": 486, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-2dz6psiia0/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1764, \"height\": 369, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-2dz6psiia0/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 677, \"height\": 612, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-2dz6psiia0/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 903, \"height\": 655, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-2dz6psiia0/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1774, \"height\": 581, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-2dz6psiia0/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 845, \"height\": 334, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-2dz6psiia0/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1340, \"height\": 913, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-2dz6psiia0/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1508, \"height\": 947, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-2dz6psiia0/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1514, \"height\": 522, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-2dz6psiia0/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1766, \"height\": 329, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-2dz6psiia0/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 888, \"height\": 150, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-2dz6psiia0/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 846, \"height\": 133, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-2dz6psiia0/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 586, \"height\": 392, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-2dz6psiia0/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 897, \"height\": 333, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-2dz6psiia0/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1160, \"height\": 254, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-2dz6psiia0/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1426, \"height\": 401, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-2dz6psiia0/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1772, \"height\": 1201, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-2dz6psiia0/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 861, \"height\": 464, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-2dz6psiia0/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 888, \"height\": 466, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-2dz6psiia0/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 890, \"height\": 293, \"label\": \"Table\"}]"
motivation: 现有心理理论方法在复杂多模态环境中扩展性差。
method: 提出可扩展贝叶斯规划器，通过逐步贝叶斯更新分解复杂度，结合弱到强控制。
result: 在复杂多模态场景中展示了较高的推理准确性和可扩展性。
conclusion: 为多模态心理理论推理提供了可扩展的解决方案。
---

## Abstract
Theory-of-mind (ToM) enables humans to infer mental states—such as beliefs, desires, and intentions—forming the foundation of social cognition. Existing computational ToM methods rely on structured workflows with ToM-specific priors or deep model fine-tuning but struggle with scalability in multimodal environments. They remain trapped within the gravitational pull of multi-step planning complexity, failing to generalize as task demands increase. To overcome these limitations, we propose a scalable Bayesian ToM planner. It breaks down ToM complexity into stepwise Bayesian updates. Meanwhile, weak-to-strong control specializes smaller LMs to refine ToM-specific likelihood estimation, transferring their ToM reasoning behavior to larger LMs (7B to 405B) for social and world knowledge integration. This synergistic approach enables scalability, aligning large-model inference with human mental states with Bayesian principles. Extensive experiments demonstrate a 4.6% improvement in accuracy over state-of-the-art methods on multimodal ToM benchmarks, including unseen scenarios, establishing a new standard for modeling human mental states in complex environments.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **动机**：心理理论（Theory-of-Mind, ToM）是人类社会认知的基础，使个体能够推断他人的信念、欲望和意图。现有的计算ToM方法主要分为两类：结构化规划工作流（如贝叶斯逆规划）和基于深度模型的微调。然而，这些方法在多模态、动态环境中面临严重的可扩展性问题：随着规划步数增加，推理精度急剧下降（如图1所示），且难以泛化到更复杂的任务。
- **关键挑战**：
  - 多步规划复杂度导致的“推理边界”限制了CoT、o1等推理时扩展方法的效果。
  - 多模态ToM推理严重依赖广泛的社会和世界知识，而小模型由于其有限的预训练容量，难以有效泛化。
- **核心目标**：提出一种可扩展的贝叶斯ToM推理方法，能够克服多步复杂性，并在多模态场景中实现高精度、稳定的推理，同时避免对大型模型进行昂贵的后训练。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将多模态ToM推理分解为模块化的 **逐步贝叶斯更新**，并通过 **弱到强控制（Weak-to-Strong Control）** 机制，将小模型经过后训练学到的ToM特定行为转移到大型语言模型（LLM）上，从而利用大模型的世界知识和推理能力，同时保持贝叶斯推理的结构化优势。
- **关键技术细节**：
  1. **贝叶斯逆规划（BIP）**：基于部分可观测马尔可夫决策过程（POMDP），通过逆推观测到的行为来推断智能体的目标 \( g \) 和信念 \( b_t \)。后验概率公式为：
     \[
     P(g, b_t | s_{1:t}, a_{1:t-1}) \propto \prod_{\tau=1}^{t} \pi(a_\tau | g, b_\tau) P(b_\tau | b_{\tau-1}, s_\tau) P(b_0) P(g)
     \]
     其中 \( \pi(a_\tau | g, b_\tau) \) 为智能体的策略函数，由LLM估计。
  2. **弱到强控制**：
     - **后训练阶段**：对一个小语言模型（如3.1-8B）进行指令微调和偏好优化（基于DPO的变体），使其专门化于ToM场景。训练数据来自具身模拟器VirtualHome生成的20,000条样本。
     - **推理阶段**：将后训练的小模型 \( \pi_E \) 与原始未训练的小模型 \( \pi_N \) 的差距作为调整量，应用到大型语言模型 \( \pi_L \) 的输出上：
       \[
       \bar{\pi}(a_t | s_t, g, \hat{b}_t) = \frac{1}{\bar{Z}} \pi_L(a_t | s_t, g, \hat{b}_t) \cdot \frac{\pi_E(a_t | s_t, g, \hat{b}_t)}{\pi_N(a_t | s_t, g, \hat{b}_t)}
       \]
       该比率近似了后训练对策略函数的梯度更新效果，使得大模型的输出逐渐偏向ToM特定行为，而无需对大型模型进行任何参数更新。
  3. **理论保证**：定理1证明，该调整近似于对大型模型交叉熵损失的负梯度更新，且KL散度有界，确保了推理与直接微调接近。

### 3. 实验设计：数据集、基准与方法对比

- **数据集**：
  - **后训练**：使用VirtualHome具身模拟器生成的1,000个程序化合成视频（MMToM训练集），每个视频标注有状态、目标、信念和动作。
  - **评估**：使用 **MMToM-QA基准**，包含134个视频（平均1462帧、约36个人类动作）、600个问题，均匀分布在**信念推理**（类型1.1-1.3）和**目标推理**（类型2.1-2.4）上。
- **迁移场景**：额外构建了5个未见过的主题场景（安徒生童话、古埃及、外太空、狂野西部、中世纪城堡），通过词汇映射改变环境描述，测试泛化能力。
- **基线方法**：
  - **纯文本**：GPT-4、GPT-3.5、DeepSeek-R1-671B、o3-mini等，以及基于提示的SimToM、SymbolicToM。
  - **仅视频**：Video-Llama2-13B、LLaVA-7B、GPT-4V，以及结合贝叶斯规划的BIPALM（使用GPT-J-6B或Llama2-7B）。
  - **多模态**：同上，但输入为视频+文本。
  - **人类基线**：180名参与者回答120个随机问题。
- **对比设置**：在文本、视频、多模态三种输入模式下比较；同时比较不同模型规模（8B、70B、405B）和是否使用弱到强控制。

### 4. 资源与算力

- **后训练**：使用单个NVIDIA H100 GPU（80GB），BF16精度。对Llama3.1-8B训练约8小时（20,000条数据，3个epoch，学习率1e-3，批次大小16）。对于70B模型，LoRA设置调整（rank=8，alpha=16）。
- **推理**：大型模型（70B、405B）仅用于推理，无需后训练。弱到强控制中，小模型和大模型可并行部署，经实验，在8B+70B配置下，600个任务的推理耗时约14-15.5分钟（约1.4-1.55秒/问题），与单独使用70B模型相当。

### 5. 实验数量与充分性

- **实验数量**：论文包含5张主要表格和补充材料中的更多结果。主要实验如下：
  - **表1**：多模态、文本、视频三个模态下的总体性能对比，包含7种以上基线和人类。
  - **表2**：缩放大模型（70B、405B）在弱到强控制下的性能，对比零样本、直接后训练和本方法。
  - **表3**：缩小小模型（4B宽度/深度）作为弱控制器的影响。
  - **表4**：迁移到5个未见场景的性能。
  - **图3、图4**：定性分析似然变化和概念级注意力。
  - **消融实验**：包括Table 5（朴素logit组合）、Table 14（有无弱到强控制对比）、Table 13（不同微调方法组合）等。
- **充分性评价**：
  - 实验设计客观公平：涵盖了多种基线（包括不同模型规模、模态、提示方法），并设置了人类上界。
  - 消融实验充分：验证了弱到强控制、小模型尺度、大模型尺度的各自贡献。
  - 迁移测试覆盖5个差异化的新场景，增强了泛化结论的可信度。
  - 统计细节：每个实验记录多类子任务（1.1-2.4）的准确率，而非单一整体分。

### 6. 论文的主要结论与发现

- **核心结论**：提出的**可扩展贝叶斯规划器**结合逐步贝叶斯更新和弱到强控制，在多模态ToM基准上实现了 **81.3%的平均准确率**，比现有最好方法（BIPALM w/ Llama2-7B的76.7%）提高 **4.6个百分点**，在迁移场景中也保持领先（约79-80%）。
- **重要发现**：
  1. **规模正相关**：大型LLM（如405B）零样本表现接近小模型后训练后的结果，但弱到强控制进一步提升。
  2. **弱控制器的有效性**：即使将小模型缩小到4B，仍能有效引导大模型，且宽度缩减比深度缩减更易泛化。
  3. **概念级调整**：后训练使小模型关注细粒度物品，而大模型初始分布更均匀；弱到强控制成功将大模型的似然估计拉向任务关键区域。
  4. **直接后训练大模型不稳定**：对70B直接后训练需大量超参数调优，且性能不如弱到强控制。

### 7. 优点：方法或实验设计上的亮点

- **方法论亮点**：
  - **避免大模型后训练**：通过小模型的后训练行为间接引导大模型，显著节省计算资源，同时保留大模型的世界知识。
  - **结构化与可扩展的统一**：贝叶斯框架提供了清晰的逐步推理，弱到强控制则扩展了模型规模，两者协同。
  - **理论保证**：定理1从KL散度角度提供了近似微调的理论合理性。
- **实验设计亮点**：
  - **全面基准**：覆盖文本、视频、多模态三种输入，对比多种SOTA方法及人类表现。
  - **迁移测试**：5个风格迥异的主题环境验证了方法的泛化性。
  - **细粒度分析**：图4展示了概念级似然变化，直观揭示了弱到强控制的工作机理。

### 8. 不足与局限

- **实验覆盖**：
  - 评估仅在VirtualHome模拟器及其衍生场景上进行，未在真实复杂社交互动（如多人对话、真实视频）中验证。论文在附录E.8中补充了MuMA-ToM的初步结果，显示与GPT-4o的LIMP方法相当，但整体仍局限于模拟环境。
  - 数据集规模有限（134个测试视频，600个问题），可能不足以捕捉所有边缘情况。
- **偏差风险**：
  - 弱控制器（小模型）的行为依赖于特定后训练数据（合成视频），若环境变化超出该分布，指导可能失效。虽然迁移测试显示较强泛化，但需更多真实场景验证。
- **应用限制**：
  - 需要同时部署两个模型（小+大），尽管计算开销可控，但在资源极受限的场景（如边缘设备）仍可能不适用。
  - 方法假设符号化输入已正确提取（通过感知模块），对于复杂、嘈杂的真实视频，提取质量可能影响后续推理。
- **其他**：未讨论失败案例或错误分析，对方法在难度极高任务上的上限未作深入探讨。

（完）
