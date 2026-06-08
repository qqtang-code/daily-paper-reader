---
title: Keypoint-based Progressive Chain-of-Thought Distillation for LLMs
title_zh: 面向大语言模型的基于关键点的渐进式链式思考蒸馏
authors: "Kaituo Feng, Changsheng Li, Xiaolu Zhang, JUN ZHOU, Ye Yuan, Guoren Wang"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=tgsSKziIEa"
tags: ["query:mm-cot"]
score: 9.0
evidence: 关注关键点的渐进式链式思考蒸馏方法
tldr: 传统链式思考蒸馏平等对待所有token，忽略关键点且未区分学习顺序。本文提出基于关键点的渐进式蒸馏：首先识别推理链中的关键token并重点学习，然后按由易到难的步骤顺序逐步训练。实验表明，该方法有效提升了学生模型的推理准确性，更符合人类认知规律，为CoT蒸馏提供了更精细化的训练策略。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-tgsskziiea/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1754, \"height\": 759, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-tgsskziiea/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 845, \"height\": 345, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-tgsskziiea/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1563, \"height\": 464, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-tgsskziiea/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1536, \"height\": 1088, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-tgsskziiea/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 889, \"height\": 871, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-tgsskziiea/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 877, \"height\": 656, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-tgsskziiea/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 880, \"height\": 305, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-tgsskziiea/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1777, \"height\": 648, \"label\": \"Table\"}]"
motivation: 链式思考蒸馏中token重要性不均，且学习顺序不符合由易到难的认知规律。
method: 提出基于关键点的渐进式蒸馏，先关注关键token再逐步学习完整步骤。
result: 在多个推理任务上，学生模型性能优于传统蒸馏方法。
conclusion: 关键点聚焦和渐进学习能更高效地迁移大模型的推理能力。
---

## Abstract
Chain-of-thought distillation is a powerful technique for transferring reasoning abilities from large language models (LLMs) to smaller student models. Previous methods typically require the student to mimic the step-by-step rationale produced by LLMs, often facing the following challenges: (i) Tokens within a rationale vary in significance, and treating them equally may fail to accurately mimic keypoint tokens, leading to reasoning errors. (ii) They usually distill knowledge by consistently predicting all the steps in a rationale, which falls short in distinguishing the learning order of step generation. This diverges from the human cognitive progression of starting with easy tasks and advancing to harder ones, resulting in sub-optimal outcomes. To this end, we propose a unified framework, called KPOD, to address these issues. Specifically, we propose a token weighting module utilizing mask learning to encourage accurate mimicry of keypoint tokens by the student during distillation. Besides, we develop an in-rationale progressive distillation strategy, starting with training the student to generate the final reasoning steps and gradually extending to cover the entire rationale. To accomplish this, a weighted token generation loss is proposed to assess step reasoning difficulty, and a value function is devised to schedule the progressive distillation by considering both step difficulty and question diversity. Extensive experiments on four reasoning benchmarks illustrate our KPOD outperforms previous methods by a large margin.

---

## 论文详细总结（自动生成）

## 论文总结：Keypoint-based Progressive Chain-of-Thought Distillation for LLMs

### 1. 核心问题与整体含义（研究动机和背景）

- **背景**：大型语言模型（LLMs）通过链式思考（Chain-of-Thought, CoT）提示展现出强大的推理能力，但通常需要超过1000亿参数，部署成本高。CoT蒸馏旨在将大模型的推理能力迁移到较小的学生模型中。
- **核心问题**：现有CoT蒸馏方法存在两个主要缺陷：
  1. **Token重要性不均**：推理链中的每个token重要性不同，关键token（如数字、运算符）对推理结果起决定性作用，而无关token（如“just”“simply”）影响较小。传统方法平等对待所有token，导致学生模型无法精确模仿关键token，引发推理错误。
  2. **学习顺序缺乏区分**：现有方法要求学生在整个蒸馏过程中一致地预测所有步骤，没有区分步骤生成的难易顺序，这与人类由易到难的认知规律相悖，导致次优结果。
- **研究目标**：提出一个统一的框架KPOD，同时解决token重要性和学习顺序两个问题，更高效地从大模型向小模型迁移推理能力。

### 2. 方法论：核心思想、关键技术细节

- **整体框架**：KPOD包含两个核心组件：**推理链token加权模块**（基于掩码学习确定token重要性）和**推理链内渐进式蒸馏策略**（由易到难组织步骤学习顺序）。token重要性权重同时用于促进关键token模仿和减少无关token对步骤难度评估的干扰。

- **推理链token加权模块**：
  - 将推理链token输入预训练嵌入层和自注意力层得到嵌入，再通过一个两层MLP（权重生成器）和sigmoid激活，输出每个token的不被掩码的概率 \( w_j^{(i)} \)，作为其重要性指标。
  - 优化目标包含两个损失：
    - **答案预测损失** \( L_p \)：将推理链部分token掩码（通过Gumbel-Softmax采样得到掩码 \( m_j^{(i)} \)），再将掩码后的推理链前缀与问题一起输入Transformer层，要求预测正确答案。鼓励权重生成器给关键token高权重（不被掩码），以帮助答案预测。
    - **掩码比率损失** \( L_m \)：最小化不被掩码的token数量，鼓励识别并掩盖不重要的token。
    - 总损失 \( L_k = L_p + \alpha L_m \)，通过优化该损失学习 \( w_j^{(i)} \)。

- **推理链内渐进式蒸馏策略**：
  - **步骤难度评估**：基于token重要性权重 \( w_j^{(i)} \) 计算每个步骤的加权token生成损失，作为该步骤的难度 \( d_k^{(i)} \)。使用蒸馏前的预训练学生模型计算生成概率，权重经softmax归一化，避免无关token影响难度判断。
  - **渐进式学习调度**：每个训练阶段（一个epoch）设定一个总体学习难度上限 \( D(t) \)，随阶段增长（\( D(t) = \frac{u t^{p+1}}{p+1} + C_0 \)）。从阶段 \( t-1 \) 到 \( t \) 时，需要选择一组问题，减少其输入步骤数量（即要求学生生成更多后续步骤），使增大的难度总和 \( \Delta H(S(t)) \) 不超过 \( \Delta D(t) \)。选择问题集合通过最大化一个**价值函数** \( F(S(t)) \) 来实现，该函数同时考虑难度接近度和问题多样性（基于K-means聚类和平方根项促进各类别均衡选择）。由于该函数是单调子模的，可用FTGP算法在近线性时间内近似求解。
  - 蒸馏损失 \( L_o(t) \) 为在选定的问题上，仅对需要生成的步骤中的token使用其重要性权重 \( w_j^{(i)} \) 进行加权交叉熵损失，其余步骤不参与当前阶段训练。

### 3. 实验设计

- **数据集**：数学推理任务：GSM8K、ASDiv、SVAMP；常识推理任务：CommonsenseQA。数据集划分遵循先前工作。
- **教师模型**：GPT-3.5-Turbo（通过零样本CoT提示生成推理链）。
- **学生模型**：三种不同架构：LLaMA-7B（7B参数）、FlanT5-XL（3B）、FlanT5-Large（760M）。
- **对比基准方法**：四个最先进的CoT蒸馏方法：SCoTD、Specialized KD、SCOTT、MCC-KD。还对比了多种课程学习方法（Adaptive CL、SPL、ICL）作为消融。
- **评估指标**：准确率（%）。

### 4. 资源与算力

- 论文在**GeForce RTX 3090 GPU**上进行实验。
- 没有明确说明使用的GPU数量、训练时长等具体算力信息。
- 训练时使用了LoRA（低秩适配）加速，秩设置：LLaMA-7B为64，FlanT5-XL为128。
- 优化器：Adam，学习率：LLaMA-7B为1×10⁻⁵，FlanT5模型为5×10⁻⁵，批量大小4。
- 训练轮数：LLaMA-7B在GSM8K和CommonsenseQA上为20轮，在ASDiv和SVAMP上为40轮；FlanT5模型为100轮。

### 5. 实验数量与充分性

- **主要性能对比**（表1）：在三个学生模型×四个数据集上，与四个基线方法全面对比，共12组结果。KPOD在所有设置下均优于基线，性能提升显著（例如LLaMA-7B上GSM8K提升5.16%）。
- **消融实验**（表2）：设计了六个变体，分别去除token重要性权重、去除权重用于难度计算、去除渐进策略、去除多样性选择，以及替换为三种课程学习方法。在LLaMA-7B和FlanT5-XL上进行两组数据集（GSM8K和CommonsenseQA）的消融，共16组结果，验证了各组件的有效性。
- **分布外（OOD）泛化实验**（表3）：使用GSM8K训练，在ASDiv和SVAMP测试，在LLaMA-7B和FlanT5-XL上对比所有基线，共16组结果，KPOD在多数情况下最优，展示了较强的OOD能力。
- **可视化分析**（图2）：展示了token重要性权重的热图，直观说明关键token（数字、运算符等）获得高权重，无关token（如“can”“say”）低权重。
- **参数敏感性分析**（图3、图4）：分析了超参数α、β、p、K、C₀，表明KPOD在较大范围内不敏感。
- **充分性评价**：实验设计较为全面，覆盖了不同模型规模（760M到7B）、不同任务类型（数学、常识）、分布内和分布外场景、消融每种核心设计，并分析了参数敏感性。实验对比了多个最先进的方法，结果客观公平。但缺少与更大规模学生模型（如13B）的对比，也未探讨在更多样化任务（如符号推理、多步推理扩展）上的表现。

### 6. 主要结论与发现

- KPOD在所有四个推理基准上显著优于现有的CoT蒸馏方法，例如在LLaMA-7B上，GSM8K准确率从41.58%（MCC-KD）提升至46.74%，ASDiv从65.76%提升至71.02%，SVAMP从64.67%提升至68.67%，CommonsenseQA从76.41%提升至77.89%。
- 消融实验表明，token重要性加权和渐进式蒸馏策略都是提升性能的关键组成部分；简单的课程学习（如Adaptive CL、SPL、ICL）直接应用于CoT蒸馏效果不如本文设计的渐进策略。
- 分布外泛化实验表明，KPOD训练的学生模型具有更强的泛化能力。
- token重要性权重可视化显示，数字、运算符、关键指令词（如“total”“adding”）和有意义的主语获得高权重，而无关词获得低权重，验证了加权模块的有效性。
- 模型对主要超参数α、β、p、K、C₀不敏感，易于实际设置。

### 7. 优点

- **创新性**：首次同时关注CoT蒸馏中token重要性和步骤学习顺序两个关键问题，提出统一的KPOD框架。
- **方法设计巧妙**：利用掩码学习自动区分关键token，无需人工标注；将课程学习思想引入推理链内部，实现由易到难的渐进学习，并考虑了问题多样性避免过拟合。
- **实验全面**：在多个模型规模、多个数据集、OOD场景、详细消融和参数分析下验证了有效性。
- **性能提升显著**：在多个设置下大幅优于现有方法。
- **通用性**：框架不依赖于特定教师模型或学生模型架构，可推广到不同LLMs。

### 8. 不足与局限

- **算力消耗未具体报告**：没有说明训练一个模型所需的具体GPU时间、内存占用等，不利于复现和资源评估。
- **实验覆盖范围有限**：仅评估了数学和常识推理，未覆盖更复杂的推理任务（如科学推理、逻辑推理）或长文本推理。学生模型最大为7B，未探索更大学生模型（如13B）或更小的模型（如350M）的表现。
- **依赖教师模型质量**：教师模型使用GPT-3.5-Turbo生成推理链，教师本身可能出错，影响蒸馏质量；未探讨使用更强教师（如GPT-4）或较弱教师的影响。
- **渐进策略调度复杂度**：需要预先计算步骤难度并求解子模最大化问题，增加了额外的计算开销和工程实现复杂度。
- **未讨论token加权模块对长推理链的扩展性**：当推理链非常长时，掩码学习可能面临挑战（如稀疏性、计算效率）。
- **简化假设**：每个epoch作为阶段，可能不是最优粒度；某些步骤可能长度不一，简单用“.”分隔步骤可能不鲁棒。

（完）
