---
title: "Generalizing from SIMPLE to HARD Visual Reasoning: Can We Mitigate Modality Imbalance in VLMs?"
title_zh: 从简单到困难视觉推理的泛化：我们能缓解视觉语言模型的模态不平衡吗？
authors: "Simon Park, Abhishek Panigrahi, Yun Cheng, Dingli Yu, Anirudh Goyal, Sanjeev Arora"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=reuPtSzCU9"
tags: ["query:mm-cot"]
score: 8.0
evidence: 解决视觉语言模型的多步视觉推理和模态不平衡问题
tldr: 视觉语言模型在多步视觉推理上远弱于人类，甚至不如纯文本大模型。本文构建了包含表格读取、网格导航和视觉类比三种任务的合成框架，并区分简单与困难层级。研究发现即使在简单任务上前沿模型也表现不佳，并提出了在简单任务上训练以提升困难任务能力的策略。该工作系统揭示了模态不平衡对多步推理的影响，并为改进提供了可行方向。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-reuptszcu9/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1740, \"height\": 589, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-reuptszcu9/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1707, \"height\": 517, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-reuptszcu9/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 830, \"height\": 458, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-reuptszcu9/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 834, \"height\": 463, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-reuptszcu9/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1606, \"height\": 499, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-reuptszcu9/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 833, \"height\": 466, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-reuptszcu9/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 855, \"height\": 369, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-reuptszcu9/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1605, \"height\": 452, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-reuptszcu9/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 616, \"height\": 459, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-reuptszcu9/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 661, \"height\": 554, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-reuptszcu9/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1250, \"height\": 529, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-reuptszcu9/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1065, \"height\": 584, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-reuptszcu9/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1776, \"height\": 499, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-reuptszcu9/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1744, \"height\": 530, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-reuptszcu9/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1156, \"height\": 498, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-reuptszcu9/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1772, \"height\": 513, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-reuptszcu9/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1249, \"height\": 538, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-reuptszcu9/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1771, \"height\": 519, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-reuptszcu9/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1757, \"height\": 497, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-reuptszcu9/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1727, \"height\": 574, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-reuptszcu9/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 697, \"height\": 479, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-reuptszcu9/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1068, \"height\": 794, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-reuptszcu9/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1773, \"height\": 491, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-reuptszcu9/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1775, \"height\": 527, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-reuptszcu9/fig-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 1249, \"height\": 531, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-reuptszcu9/fig-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 1750, \"height\": 1119, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-reuptszcu9/fig-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 1742, \"height\": 557, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-reuptszcu9/fig-028.webp\", \"caption\": \"\", \"page\": 0, \"index\": 28, \"width\": 1616, \"height\": 665, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-reuptszcu9/fig-029.webp\", \"caption\": \"\", \"page\": 0, \"index\": 29, \"width\": 1604, \"height\": 448, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-reuptszcu9/fig-030.webp\", \"caption\": \"\", \"page\": 0, \"index\": 30, \"width\": 1291, \"height\": 556, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-reuptszcu9/fig-031.webp\", \"caption\": \"\", \"page\": 0, \"index\": 31, \"width\": 416, \"height\": 419, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-reuptszcu9/fig-032.webp\", \"caption\": \"\", \"page\": 0, \"index\": 32, \"width\": 361, \"height\": 358, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-reuptszcu9/fig-033.webp\", \"caption\": \"\", \"page\": 0, \"index\": 33, \"width\": 1355, \"height\": 1074, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-reuptszcu9/fig-034.webp\", \"caption\": \"\", \"page\": 0, \"index\": 34, \"width\": 480, \"height\": 524, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-reuptszcu9/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 462, \"height\": 443, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-reuptszcu9/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1138, \"height\": 492, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-reuptszcu9/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1449, \"height\": 437, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-reuptszcu9/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1339, \"height\": 265, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-reuptszcu9/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1425, \"height\": 337, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-reuptszcu9/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1667, \"height\": 486, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-reuptszcu9/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1660, \"height\": 488, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-reuptszcu9/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1232, \"height\": 313, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-reuptszcu9/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1753, \"height\": 376, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-reuptszcu9/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1405, \"height\": 669, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-reuptszcu9/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1449, \"height\": 376, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-reuptszcu9/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 863, \"height\": 450, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-reuptszcu9/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1480, \"height\": 362, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-reuptszcu9/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1332, \"height\": 525, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-reuptszcu9/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1517, \"height\": 1034, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-reuptszcu9/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 898, \"height\": 491, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-reuptszcu9/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 821, \"height\": 362, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-reuptszcu9/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 909, \"height\": 496, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-reuptszcu9/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 821, \"height\": 361, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-reuptszcu9/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1260, \"height\": 920, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-reuptszcu9/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 552, \"height\": 458, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-reuptszcu9/table-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 470, \"height\": 131, \"label\": \"Table\"}]"
motivation: 视觉语言模型在多步视觉推理上表现脆弱，存在模态不平衡问题。
method: 提出包含多级难度的合成视觉推理框架，并设计简单任务训练策略。
result: 简单任务训练能显著提升模型在困难视觉推理任务上的性能。
conclusion: 通过针对性训练可缓解模态不平衡，增强多步视觉推理能力。
---

## Abstract
Vision Language Models (VLMs) are impressive at visual question answering and image captioning. But they underperform on multi-step visual reasoning---even compared to LLMs on the same tasks presented in text form---giving rise to perceptions of *modality imbalance* or *brittleness*. Towards a systematic study of such issues, we introduce a synthetic framework for assessing the ability of VLMs to perform algorithmic visual reasoning, comprising three tasks: Table Readout, Grid Navigation, and Visual Analogy. Each has two levels of difficulty, SIMPLE and HARD, and even the SIMPLE versions are difficult for frontier VLMs. We propose strategies for training on the SIMPLE version of tasks that improve performance on the corresponding HARD task, i.e., simple-to-hard (S2H) generalization. This controlled setup, where each task also has an equivalent text-only version, allows a quantification of the modality imbalance and how it is impacted by training strategy. We show that 1) explicit image-to-text conversion is important in promoting S2H generalization on images, by transferring reasoning from text; 2) conversion can be internalized at test time. We also report results of mechanistic study of this phenomenon. We identify measures of gradient alignment that can identify training strategies that promote better S2H generalization. Ablations highlight the importance of chain-of-thought.

---

## 论文详细总结（自动生成）

好的，根据您提供的论文内容，以下是对该论文的结构化、深入且客观的中文总结。

---

### 论文总结：从简单到困难视觉推理的泛化：我们能缓解视觉语言模型的模态不平衡吗？

#### 1. 核心问题与整体含义

- **研究动机与背景**：视觉语言模型（VLM）虽在视觉问答和图像描述上表现优异，但在需要多步推理的复杂视觉任务上却表现不佳，甚至不如处理纯文本形式相同任务的大型语言模型（LLM）。这种在视觉输入和文本输入之间存在的性能差距被称为“**模态不平衡**”或“**脆弱性**”（modality imbalance / brittleness）。本文旨在系统性地研究并尝试缓解VLM的这一缺陷。

#### 2. 方法论

- **核心思想**：
    1.  **构建可控的合成任务框架**：设计三个需要算法式视觉推理的合成任务，每个任务都有SIMPLE（简单）和HARD（困难）两个难度级别，并都有一个等价的文本版本（如LaTeX代码）。
    2.  **定义“简单到困难”泛化能力（S2H Generalization）**：模型在SIMPLE样本上训练后，测试其在HARD样本上的表现，以此来量化VLM的泛化能力和模态不平衡程度。
    3.  **提出多种训练策略**：探索不同的监督信息组合，旨在将从文本模态学习到的强大推理能力迁移到图像模态。

- **关键技术细节**：
    - **合成任务**：
        - **表格读取（Table Readout）**：按高亮路径读取表格中的数字。
        - **连续表格读取（Consecutive Table Readout）**：读取表格中按行主序排列的连续数字。
        - **网格导航（Grid Navigation）**：在带障碍和物体的网格中规划路径。
        - **视觉类比（Visual Analogy）**：分析几何图形的属性和关系，进行类比推理。
    - **训练策略**：核心是多种“监督类型”（Types of Supervision）的组合：
        - **文本监督 (Text)**：在文本输入上训练。
        - **图像监督 (Image)**：在图像输入上训练。
        - **图像-文本转换监督 (Image-via-Text)**：在图像输入上训练，但要求模型先将其转换为文本（如LaTeX代码），再进行推理。
        - **Mix监督**：混合上述所有三种监督。
        - **Mix+ 监督**：在Mix基础上，加入HARD任务的文本监督（HARD Text）。
        - **Align-Mix+**：两阶段训练，先使用SIMPLE任务的“文本”和“图像-文本转换”监督进行对齐训练，再使用Mix+进行主训练。
    - **理论基础**：论文通过理论分析（Theorem H.1）和实验测量“梯度对齐分数”（Gradient Alignment Score），论证了为什么Mix等策略能更好地将训练梯度导向HARD图像输入，从而提升泛化能力。

#### 3. 实验设计

- **使用的数据集/场景**：
    - **数据集**：全部为自建的合成数据集，包含上述三个任务（及两个变体）。每个任务都生成了SIMPLE和HARD两个版本的输入（图像和文本形式）。
    - **Benchmark**：主要评估指标是“S2H准确率”（S2H Accuracy），即模型在SIMPLE任务上训练后，在HARD任务上的准确率。此外，还验证了训练数据对MMMU、ChartQA等真实基准测试的性能提升。
- **对比的方法**：
    - **主要基线**：仅使用**文本(Text)** 或仅使用**图像(Image)** 监督训练。
    - **消融策略**：对比了**Text+Image**、**Image-via-Text**、**Mix**、**Mix+**、**Align-Mix+**、**Image-via-Text+** 等多种训练策略。
    - **模型对比**：主要在Eagle-X2-Llama3-8B上进行实验，并在Qwen2.5-VL-3B/7B上进行了复现验证，同时也测试了GPT-4o、Claude-3.5 Sonnet等前沿模型的性能。

#### 4. 资源与算力

- **硬件**：使用8块GPU（具体型号未明确，但提及使用了HPC集群）。
- **框架**：使用Deepspeed ZeRO Stage 2进行分布式数据并行训练。
- **优化器**：AdamW优化器（无权重衰减），学习率调度为线性预热加余弦衰减。
- **训练细节**：
    - 基础模型为Eagle-X2-Llama3-8B。
    - 训练分为预训练（595k数据，学习率1e-3）、指令微调（1.8M数据，学习率2e-5）和在合成任务上的持续微调（学习率2e-5）。总文本token限制为2048。
    - 具体GPU型号和总训练时长未明确说明。

#### 5. 实验数量与充分性

- **实验数量**：论文进行了大量系统性的实验，涵盖了：
    - **主要任务**（3个任务+2个变体）的S2H泛化对比。
    - **多种训练策略**（至少10种不同组合）的横向对比。
    - **消融实验**：对训练数据量、链式思维（CoT）、数据重复、多任务训练、模型规模等关键因素进行了深入消融研究。
    - **梯度分析**：对梯度对齐和损失动态进行了机理分析。
    - **跨模型验证**：在Qwen2.5-VL系列上进行了结果复现。
    - **真实基准测试**：评估了合成数据对MMMU、MMBench等真实基准的影响。
- **充分性与公平性**：
    - **充分性**：实验设计非常全面且有层次，从宏观的性能对比深入到微观的梯度分析，论证充分。
    - **公平性**：在对比不同训练策略时，控制了训练数据总量（NSIMPLE）或唯一样本数（Nu_SIMPLE）以确保公平比较。同时，在不同模型和规模上进行了验证。

#### 6. 主要结论与发现

1.  **模态不平衡显著**：VLM在S2H泛化上存在显著的模态不平衡，在文本输入上可以成功泛化（如连续表格读取），但在图像输入上表现很差。
2.  **“图像-文本转换”是关键**：在训练中加入“图像-文本转换”监督（Image-via-Text）是促进S2H泛化从文本迁移到图像的最可靠方法。
3.  **Mix策略有效**：混合多种监督的**Mix**策略可以同时兼顾性能和推理效率，模型能将文本转换能力内化，从而无需在推理时显式进行转换，降低了推理成本。
4.  **注入文本推理能力可迁移**：对于在文本和图像上都无法S2H泛化的更难任务，通过在训练中加入HARD任务的文本监督（**Mix+**），可以将文本推理能力成功迁移到图像。
5.  **两阶段训练更优**：**Align-Mix+**（先对齐再训练）策略通过前置的对齐阶段，能在后续训练中产生梯度对齐更好的信号，从而进一步提升图像上的S2H泛化性能。
6.  **梯度对齐能预测性能**：论文提出的“梯度对齐分数”是衡量不同训练策略提升S2H泛化能力效果的有效指标。
7.  **链式思维（CoT）必不可少**：消融实验表明，完全去除或在训练后期将CoT内化都会导致S2H泛化失败，说明在本文方法中，显式的CoT是知识迁移的必要条件。

#### 7. 优点

- **严谨的框架**：通过构建可控的合成任务和清晰的S2H泛化指标，为量化研究VLM的模态不平衡问题提供了一个严谨、系统化的框架。
- **直接有效的解决方法**：提出的训练策略（如Mix, Align-Mix+）基于直觉且效果显著，为解决该问题提供了直接可行的思路。
- **深入的机理分析**：不仅报告了性能结果，还从梯度对齐的角度对模型行为进行了深入的机理分析，提升了工作的深度和说服力。
- **丰富且系统的消融实验**：对影响性能的关键因素进行了全面剖析，增强了结论的可靠性和对后续研究的指导价值。

#### 8. 不足与局限

- **合成任务的局限性**：所有实验都基于合成任务，虽然可控性强，但与真实世界中复杂的视觉推理场景存在差距。将结论推广到真实场景仍需进一步验证。
- **模型的局限性**：主要实验在单一模型（Eagle-X2）上进行。虽然跨模型验证了部分结果，但该模型在文本上的S2H泛化能力本身有限，导致需要引入HARD Text监督。结论可能在更强的VLM（如 GPT-4V）上需要重新审视。
- **对CoT的强依赖**：方法高度依赖显式的CoT推理。这不仅增加了训练和推理成本，而且CoT的微小改动都可能导致结果的不稳定，这在应用中是一个潜在的脆弱点。
- **未完全消除不平衡**：即使在最好的策略下，图像和文本之间的S2H泛化差距可以被大幅缩小，但并未被完全消除。
- **开源的博弈**：论文生成合成数据集的过程比预期复杂，需要对数据细节进行大量调整（如分辨率、颜色、CoT格式），这是将这种范式扩展到新任务的一个实际障碍。

（完）
