---
title: "VeriThinker: Learning to Verify Makes Reasoning Model Efficient"
title_zh: VeriThinker：学习验证使推理模型高效化
authors: "Zigeng Chen, Xinyin Ma, Gongfan Fang, Ruonan Yu, Xinchao Wang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=Y1bt0YIS6Y"
tags: ["query:mm-cot"]
score: 6.0
evidence: 通过学习验证实现高效长链推理
tldr: 大推理模型的长链推理存在过度思考问题，推理链过长增加成本。提出VeriThinker方法，不直接压缩推理链，而是通过辅助验证任务微调模型，使其学会判断推理步骤的必要性，从而自发删减不必要的自我反思，在保持准确率的同时显著降低推理长度和计算开销。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-y1bt0yis6y/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1454, \"height\": 804, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-y1bt0yis6y/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1384, \"height\": 347, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-y1bt0yis6y/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1379, \"height\": 316, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-y1bt0yis6y/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1444, \"height\": 825, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-y1bt0yis6y/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1445, \"height\": 373, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-y1bt0yis6y/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1446, \"height\": 421, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-y1bt0yis6y/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 733, \"height\": 299, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-y1bt0yis6y/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1278, \"height\": 222, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-y1bt0yis6y/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 646, \"height\": 260, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-y1bt0yis6y/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1127, \"height\": 298, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-y1bt0yis6y/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1387, \"height\": 260, \"label\": \"Table\"}]"
motivation: 长链推理的过度思考导致高推理成本。
method: 通过辅助验证任务微调模型，使其学习判断步骤必要性。
result: 在多个推理基准上压缩链长而准确率基本不变。
conclusion: VeriThinker为长链推理的效率优化提供了新范式。
---

## Abstract
Large Reasoning Models (LRMs) have garnered considerable attention for their ability to tackle complex tasks through the Chain-of-Thought (CoT) approach. However, their tendency toward overthinking results in unnecessarily lengthy reasoning chains, dramatically increasing the inference costs. To mitigate this issue, we introduce VeriThinker, a novel approach for CoT compression. Unlike conventional methods that fine-tune LRMs directly on the original reasoning task using synthetic concise CoT data, we innovatively fine-tune the model solely through an auxiliary verification task. By training LRMs to accurately verify the correctness of CoT solutions, the LRMs inherently become more discerning about the necessity of subsequent self-reflection steps, thereby effectively suppressing overthinking. Extensive experiments validate that VeriThinker substantially reduces reasoning chain lengths while maintaining or even slightly improving accuracy. When applied to DeepSeek-R1-Distill-Qwen-7B, our approach reduces reasoning tokens on MATH500 from 3790 to 2125 while improving accuracy by 0.8% (94.0% to 94.8%), and on AIME25, tokens decrease from 14321 to 10287 with a 2.1% accuracy gain (38.7% to 40.8%). Additionally, our experiments demonstrate that VeriThinker can also be zero-shot generalized to speculative reasoning.

---

## 论文详细总结（自动生成）

# VeriThinker: 学习验证使推理模型高效化 —— 论文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：大型推理模型（LRMs，如GPT-o1、DeepSeek-R1）通过长链思维（CoT）解决复杂任务，但存在严重的“过度思考”（overthinking）现象：推理链中充斥着大量不必要的自我反思步骤，导致推理成本激增。
- **现有方法局限**：传统CoT压缩方法（如SFT、RL）需要合成高质量、简洁的推理链作为训练目标，生成这类数据计算开销大、耗时长，且很难同时兼顾简洁性与保留关键反思步骤，导致压缩后准确率下降，尤其在复杂问题上。
- **研究意义**：如何在不依赖合成目标链的前提下，实现有效压缩并保持原有推理能力，是提升LRMs实际部署效率的关键问题。VeriThinker通过辅助验证任务微调模型，使其自发学会判断步骤必要性，从而抑制过度思考，提供了一种新范式。

## 2. 方法论

### 核心思想
- **监督验证微调（SVFT）**：不是直接训练模型生成短链，而是训练模型对给定的CoT解进行正确性二分类（正确/错误）。通过让模型学会区分正确与错误的解，其在推理时能更精准地判断是否需要自我反思，从而自动减少不必要的反思步骤，实现CoT压缩。

### 关键技术细节
- **数据构建**：收集约300K数学问题（来自PRM12K、GSM8K、LIMO、Numina-Math），用多个小型非推理模型（Qwen-2.5系列、Qwen-Math系列）生成短CoT解（无自我反思），共约150万对。通过比较最终答案与标准答案自动标注正确性。最终筛选出约340K对（每个问题至少包含一个正确和一个错误解），作为微调数据集。
- **训练方式**：对每个数据实例，输入为问题+CoT解，输出为固定响应：“Yes, I’m sure that every step is absolutely correct.”（正确）或“No, I think there might be some mistakes in the proposed solution.”（错误）。微调时仅对响应部分计算交叉熵损失，避免输入解引入偏差。
- **LoRA高效微调**：使用Low-Rank Adaptation（LoRA）降低训练成本并缓解灾难性遗忘，不同模型设置不同秩和alpha（7B: rank256, alpha512; 14B/8B: rank128, alpha128）。
- **机制分析**：通过实验验证，SVFT本质类似于对比学习，模型习得区分正确与错误解的能力，而非显式语义。SVFT显著提高了模型对反思必要性的判断精度：对正确步骤，模型生成“Wait”（自我反思标记）的概率大幅下降；对人为引入错误的步骤，概率反而略有上升。这解释了为何压缩不会降低准确率。

## 3. 实验设计

### 数据集与基准
- **推理基准**：MATH500、AIME2024、AIME2025、GSM8K（数学推理），以及跨域泛化GPQA-Diamond（科学多选题）。
- **验证基准**：使用Qwen-2.5-Math-1.5B/7B-Instruct生成的CoT解，测试SVFT模型的验证准确率，并与GPT-4o、GPT-4.1等对比。
- **推测推理**：在MATH500和GSM8K上测试吞吐量提升。

### 对比方法
- **原始模型**：DeepSeek-R1-Distill-Qwen-7B/14B、DeepSeek-R1-Distill-Llama-8B
- **基线方法**：
  - Truncating（截断最大token数）
  - Fast-Prompting（prompt工程限制token数）
  - CoT-Valve（可调节推理链长度）
  - SFT（用合成短链数据微调，短链由模型合并生成，长度为原链的60%）
- **所有基线均在相同LoRA配置下训练**，保证公平。

### 评估指标
- 推理准确率（Accuracy）、平均推理token数（Tokens）
- 验证准确率、精确率、召回率、F1分数
- 推测推理：吞吐量倍数、LRM激活率（AcR）

## 4. 资源与算力

- **训练硬件**：4块RTX 6000 Ada GPU，使用DeepSpeed ZeRO-2优化，Hugging Face SFTTrainer。
- **数据生成**：使用4块NVIDIA A6000 GPU，3-4小时内完成约300K问题的解生成。
- **训练配置**：学习率3e-5，LoRA dropout 0.05，weight decay 0.01，batch size 64，训练2个epoch。
- **推理**：使用vLLM框架，温度0.6，top-p 0.95，同样在RTX 6000 Ada上执行。
- **注意**：论文未明确报告单次训练总时长，但上述配置可给出大致量级。

## 5. 实验数量与充分性

- **主实验**：在3种LRM（7B/14B/8B）共3个模型上，对比4种基线，在3个推理基准上报告准确率和token数，结果取2-16次运行平均值（表1）。
- **验证实验**：测试SVFT模型的CoT正确性验证能力，与4个开源/闭源模型对比（表2、表8）。
- **推测推理实验**：使用两个短CoT模型作为草稿模型，在MATH500和GSM8K上评估吞吐量和准确率（表3）。
- **短CoT模型应用**：在Qwen-2.5系列短CoT模型上测试SVFT效果（表4）。
- **消融与机制分析**：
  - 不同响应设计（反向、单token、随机等）的影响（图4）
  - 反思概率变化分析（图2c）
  - 正确/错误问题上token减少差异分析
  - 跨域泛化（仅用PRM12K+GSM8K训练，在AIME和GPQA上测试，表6、表7）
- **主观评价**：实验设计较为全面，覆盖多种模型规模、多种基线、多个数据集，并有消融和机制验证。对比方法公平（均用相同LoRA配置），结果统计分析合理。实验充分且客观。

## 6. 主要结论与发现

1. **SVFT能有效压缩CoT**：在保持或轻微提升准确率的同时，显著减少推理token数。例如，R1-Distill-Qwen-7B在MATH500上token减少44%，准确率提升0.8%；在AIME25上token减少28%，准确率提升2.1%。
2. **压缩源于更精确的反思判断**：SVFT模型对正确步骤减少了不必要的自我反思，对错误步骤保持了甚至略微增加了反思概率，从而避免了传统方法中盲目压缩导致准确率下降的问题。
3. **验证能力可迁移至推测推理**：SVFT模型的验证能力可用于构建“解级推测推理”流水线：短CoT模型快速生成候选解，由SVFT模型验证正确性，仅当验证为错误时才触发长CoT推理，大幅提升吞吐量（最高7倍）。
4. **对短CoT模型也有提升**：SVFT训练也能提高短CoT模型的推理准确率，但不会显著改变token数。
5. **跨域泛化能力强**：即使训练数据仅为数学问题，在GPQA（科学领域）上也能有效压缩且保持准确率。
6. **方法本质是对比学习**：模型学到区分正确与错误解的能力，而非显式语义，这解释了为何只需标签（正确/错误）即可实现压缩。

## 7. 优点

- **创新性**：首次提出通过辅助验证任务实现CoT压缩，不依赖合成目标链，避免了高成本的数据生成和难以平衡简洁性与准确性的问题。
- **简洁有效**：方法简单，仅需对模型进行二分类训练，却能取得显著效果，且易于实现和扩展。
- **机制清晰**：通过反思概率变化等实验，深入揭示了SVFT为什么有效，增强了方法可信度。
- **泛化能力强**：在跨域（GPQA）、跨任务（推测推理）上均表现出色，验证了方法的鲁棒性和实用性。
- **全面的实验验证**：涵盖多种模型、多种基线、消融分析、机制探究，实验设计严谨，结论可靠。

## 8. 不足与局限

- **小模型效果不佳**：在较小模型（如1.5B参数）上，由于SVFT是辅助任务而非直接推理任务，小模型容量有限，容易发生灾难性遗忘，导致压缩效果不理想。
- **领域覆盖有限**：主要实验集中在数学推理，虽然做了跨域验证（GPQA-Diamond），但仅涉及一个科学多选题数据集，未涵盖代码、逻辑推理、常识推理等其他重要领域。
- **推测推理的局限性**：随问题难度增加，短CoT草稿模型准确率下降，LRM激活率上升，吞吐量增益可能降低，限制了在高难度任务上的加速效果。
- **计算资源细节不充分**：论文未明确报告每次实验的训练总时间，也未讨论不同规模模型的训练成本对比，对可复现性和资源估算的细节有所欠缺。
- **潜在偏差风险**：验证数据集的正确性标注仅基于最终答案匹配，未考虑推理步骤本身正确但答案错误的情况，可能引入噪声。此外，训练数据来自数学问题，对其他模态（如视觉推理）的适用性未知。

（完）
