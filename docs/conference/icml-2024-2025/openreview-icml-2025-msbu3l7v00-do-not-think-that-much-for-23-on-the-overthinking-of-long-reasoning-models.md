---
title: Do NOT Think That Much for 2+3=? On the Overthinking of Long Reasoning Models
title_zh: 别为2+3=？想太多：论长推理模型的过度思考
authors: "Xingyu Chen, Jiahao Xu, Tian Liang, Zhiwei He, Jianhui Pang, Dian Yu, Linfeng Song, Qiuzhi Liu, Mengfei Zhou, Zhuosheng Zhang, Rui Wang, Zhaopeng Tu, Haitao Mi, Dong Yu"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=MSbU3L7V00"
tags: ["query:mm-cot"]
score: 8.0
evidence: 长链式思维推理模型中的过度思考研究
tldr: 长推理模型通过扩展链式思维（CoT）提升性能，但存在过度思考问题。本文首次系统研究该现象，发现长推理模型在简单问题上生成冗余步骤，浪费计算资源。作者提出了新的效率指标，并验证了不同模型架构下的计算冗余程度。这项工作为智能分配测试时计算量提供了基础。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-msbu3l7v00/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 702, \"height\": 663, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-msbu3l7v00/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1688, \"height\": 981, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-msbu3l7v00/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 692, \"height\": 619, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-msbu3l7v00/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1220, \"height\": 552, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-msbu3l7v00/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 845, \"height\": 578, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-msbu3l7v00/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 702, \"height\": 497, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-msbu3l7v00/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 755, \"height\": 456, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-msbu3l7v00/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 805, \"height\": 554, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-msbu3l7v00/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1363, \"height\": 1110, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-msbu3l7v00/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 864, \"height\": 295, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-msbu3l7v00/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 849, \"height\": 336, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-msbu3l7v00/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1374, \"height\": 1226, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-msbu3l7v00/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 866, \"height\": 1967, \"label\": \"Table\"}]"
motivation: 长推理模型在简单问题上生成冗余CoT步骤，浪费计算资源。
method: 定义效率度量，分析长推理模型在不同难度问题上的输出冗余。
result: 发现长推理模型在简单任务上产生大量无效步骤，造成计算浪费。
conclusion: 该工作呼吁根据问题难度动态调整CoT长度，以实现高效推理。
---

## Abstract
The remarkable performance of long reasoning models can be attributed to their ability to emulate human-like long-time thinking during inference. These models employ extended chain-of-thought (CoT) processes, exploring multiple strategies to enhance problem-solving capabilities. However, a critical question remains: How to intelligently and efficiently scale computational resources during testing. This paper presents the first comprehensive study on the prevalent issue of overthinking in these models, where long reasoning models generate redundant solutions that contribute minimally to accuracy and diversity, thereby wasting computational resources on simple problems with minimal benefit. We introduce novel efficiency metrics from both outcome and process perspectives to evaluate the rational use of computational resources by long reasoning models. Using a self-training paradigm, we propose strategies to mitigate overthinking, simplifying reasoning processes without compromising accuracy.  Experimental results show that our approach successfully reduces computational overhead while preserving model performance across a range of testsets with varying difficulty levels, such as GSM8K, MATH500, GPQA, and AIME. Our code is open-source and available at https://github.com/galaxyChen/overthinking.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **核心问题**：长推理模型（如 OpenAI o1、QwQ-32B-Preview、DeepSeek-R1）通过扩展链式思维（CoT）和探索多种策略来提升推理能力，但在简单问题上生成了大量冗余的推理步骤（即“过度思考”），这些步骤对准确性和多样性贡献极小，却浪费了大量计算资源。
- **研究背景**：现有工作主要关注如何通过“测试时计算扩展”提升模型性能，但很少思考如何**智能且高效**地分配这些计算资源。本文首次系统性地研究长推理模型中的过度思考现象，揭示其效率低下的本质，并提出缓解策略。

## 2. 方法论：核心思想与关键技术
- **核心思想**：定义新的效率指标来量化过度思考，然后通过自训练范式让模型学会生成更简洁的推理过程，同时保持准确性。
- **关键技术细节**：
  - **效率指标**：
    - **结果效率（Outcome Efficiency, ξO）**：衡量有效token占比（即首次出现正确答案之前的token除以总token）。公式：ξO = (1/N) Σ (σi * ˆTi / Ti)，其中σi表示至少有正确解，ˆTi为到首次正确解为止的token数。
    - **过程效率（Process Efficiency, ξP）**：衡量用于不同推理策略的token占比（即对每个唯一策略的token求和后除以总token）。公式：ξP = (1/N) Σ (Di / Ti)，Di为属于不同策略的token数。
  - **简化响应策略**：
    - **FCS（First-Correct Solutions）**：只保留从开头到第一个正确解之间的内容。
    - **FCS+Reflection**：保留前两个正确解（第一个正确解+紧跟的另一个正确解），以保持反思能力。
    - **GDS（Greedily Diverse Solutions）**：贪心选择引入新推理策略的解，平衡多样性和简洁性。
  - **偏好优化训练**：将生成的短推理轨迹作为正例，最长的响应作为负例，使用SimPO（Simple Preference Optimization）等方法进行训练，鼓励模型输出简洁推理。
- **算法流程**（文字说明）：
  1. 基于PRM12K数据集，用原始模型（QwQ-32B-Preview）生成10个推理轨迹，只保留正确轨迹。
  2. 从正确轨迹中提取短轨迹（如FCS+Reflection等）作为正例，最长轨迹作为负例。
  3. 使用偏好优化（默认SimPO）训练模型，使其倾向于生成更短的响应。

## 3. 实验设计：数据集、基准与对比方法
- **数据集**：
  - **ASDIV**（小学级别数学问题，2305实例）
  - **GSM8K**（初中数学问题，1319实例）
  - **MATH500**（高中数学竞赛问题，分1-5难度等级）
  - **GPQA Diamond**（研究生级别科学问题，198题）
  - **AIME24**（美国数学邀请赛问题）
  - **训练集**：PRM12K（数学问题，用于生成训练数据）
- **基准（Benchmark）**：准确率（Accuracy）、#Solution（平均解数量）、#Token（平均token数）、结果效率（ξO）、过程效率（ξP）。
- **对比方法**：
  - **基线模型**：QwQ-32B-Preview、DeepSeek-R1、QwQ-32B、Qwen3-235B-A22B
  - **传统模型**：Llama-3.3-70B-Instruct、Qwen2.5-Math-72B-Instruct（仅单解）
  - **简化策略**：SFT、DPO、RPO、SimPO（以及不同的正例构建方式：Shortest、FCS、FCS+Reflection、GDS）

## 4. 资源与算力
- **论文未明确说明**使用的GPU具体型号、数量或训练时长。仅提到采用QwQ-32B-Preview模型（32B参数量）进行采样和自训练，以及偏好优化训练。未量化训练的计算开销。

## 5. 实验数量与充分性
- **实验数量**：在3个数学数据集（ASDIV, GSM8K, MATH500）上进行系统对比，并在2个更具挑战的数据集（GPQA, AIME24）上验证泛化性。进行了消融实验比较不同简化策略（FCS, FCS+Reflection, GDS）和不同偏好优化方法（SFT, DPO, RPO, SimPO）。共展示约10组主要对比表。
- **充分性**：实验覆盖了从简单到困难的多种数学推理任务，且对比了多种方法，消融充分。
- **客观性与公平性**：采用公开数据集和标准评估流程；效率指标是新颖的但基于合理假设；使用GPT-4o进行多样性聚类虽然可能引入偏差，但提供了详细的prompt。整体实验设计严谨，结论有数据支撑。

## 6. 主要结论与发现
- 长推理模型存在严重的过度思考，尤其在简单问题上：生成2-4个解，其中第一个解已正确（超过80%情况），后续解贡献极小。
- 提出的效率指标（ξO, ξP）能有效量化计算浪费。
- 采用SimPO + FCS+Reflection 策略能大幅减少token（如MATH500上减少44.5%），同时保持或小幅提升准确率。
- 该方法在具有挑战性的GPQA和AIME上也能保持性能，不会显著削弱模型的复杂推理能力。
- 过度思考的根源在于模型缺少根据问题难度自适应分配计算的能力，本文方法通过精简冗余步骤改善了这一点。

## 7. 优点
- **首次系统定义过度思考**：提出明确的量化指标（ξO, ξP），为后续研究提供工具。
- **自训练范式无需外部数据**：利用模型自身生成的轨迹进行精简和优化，实用性强。
- **方法简洁有效**：通过简单的剪枝和偏好优化即可显著降低计算开销，且不损害性能。
- **实验覆盖全面**：从小学数学到竞赛级别、研究生科学问题，验证了方法的鲁棒性。
- **开源代码**：促进复现和扩展。

## 8. 不足与局限
- **领域局限**：所有实验仅在数学和科学推理数据集上进行，未验证在常识推理、代码生成、医疗等领域的效果，泛化性存疑。
- **依赖外部模型进行聚类**：多样性分析依赖GPT-4o进行解的策略分组，可能引入分类偏差或计算成本。
- **模型种类有限**：仅测试了QwQ-32B-Preview和DeepSeek-R1两个代表性长推理模型，未覆盖其他架构或更大规模模型。
- **未探索动态自适应**：提出的简化策略是静态的（固定剪枝规则），未研究根据问题难度动态调整CoT长度的方法。
- **训练数据来源单一**：仅使用PRM12K（数学问题）生成训练轨迹，可能限制模型在其他任务上的泛化。
- **计算资源未报告**：未说明训练所需的GPU数量、时长等，影响可复现性和成本评估。
- **可能的风险**：过度剪枝（如FCS）在极难问题上可能导致性能下降（尽管FCS+Reflection缓解了此问题），需要谨慎选择剪枝程度。

（完）
