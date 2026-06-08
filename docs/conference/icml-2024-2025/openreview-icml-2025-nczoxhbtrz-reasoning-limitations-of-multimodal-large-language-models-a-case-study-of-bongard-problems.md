---
title: Reasoning Limitations of Multimodal Large Language Models. A case study of Bongard Problems
title_zh: 多模态大模型在Bongard问题上的推理局限性研究
authors: "Mikołaj Małkiński, Szymon Pawlonka, Jacek Mańdziuk"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=NCZOxhBTrz"
tags: ["query:mm-cot"]
score: 8.0
evidence: 多模态推理局限性的Bongard问题研究
tldr: 该论文研究了多模态大语言模型在Bongard问题上的抽象视觉推理能力。实验表明，尽管在真实世界数据集上有所成功，但模型在合成Bongard问题上表现不佳。为了深入探究这一差距，作者引入了Bongard-RWR数据集，使用真实图像表示合成概念。这项工作揭示了当前多模态模型在抽象推理方面的局限性。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-nczoxhbtrz/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 863, \"height\": 700, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nczoxhbtrz/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1731, \"height\": 705, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nczoxhbtrz/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1629, \"height\": 338, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nczoxhbtrz/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1740, \"height\": 889, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nczoxhbtrz/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1769, \"height\": 449, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nczoxhbtrz/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1774, \"height\": 1187, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nczoxhbtrz/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1769, \"height\": 646, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nczoxhbtrz/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1768, \"height\": 1169, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nczoxhbtrz/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1758, \"height\": 465, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nczoxhbtrz/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1414, \"height\": 2132, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nczoxhbtrz/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1777, \"height\": 1291, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nczoxhbtrz/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1059, \"height\": 690, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nczoxhbtrz/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 860, \"height\": 458, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nczoxhbtrz/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 779, \"height\": 683, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nczoxhbtrz/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1760, \"height\": 1182, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nczoxhbtrz/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1434, \"height\": 413, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nczoxhbtrz/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1437, \"height\": 443, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nczoxhbtrz/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 628, \"height\": 412, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nczoxhbtrz/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1437, \"height\": 416, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nczoxhbtrz/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1492, \"height\": 1001, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nczoxhbtrz/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1331, \"height\": 900, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nczoxhbtrz/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1493, \"height\": 999, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nczoxhbtrz/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1333, \"height\": 900, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nczoxhbtrz/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1493, \"height\": 1000, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nczoxhbtrz/fig-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 1334, \"height\": 902, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nczoxhbtrz/fig-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 1488, \"height\": 1003, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nczoxhbtrz/fig-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 1331, \"height\": 898, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nczoxhbtrz/fig-028.webp\", \"caption\": \"\", \"page\": 0, \"index\": 28, \"width\": 1761, \"height\": 734, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nczoxhbtrz/fig-029.webp\", \"caption\": \"\", \"page\": 0, \"index\": 29, \"width\": 1761, \"height\": 823, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nczoxhbtrz/fig-030.webp\", \"caption\": \"\", \"page\": 0, \"index\": 30, \"width\": 850, \"height\": 562, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nczoxhbtrz/fig-031.webp\", \"caption\": \"\", \"page\": 0, \"index\": 31, \"width\": 1742, \"height\": 584, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nczoxhbtrz/fig-032.webp\", \"caption\": \"\", \"page\": 0, \"index\": 32, \"width\": 861, \"height\": 603, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-nczoxhbtrz/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1734, \"height\": 441, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-nczoxhbtrz/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1238, \"height\": 390, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-nczoxhbtrz/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1631, \"height\": 335, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-nczoxhbtrz/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1757, \"height\": 1876, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-nczoxhbtrz/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1199, \"height\": 187, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-nczoxhbtrz/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1201, \"height\": 189, \"label\": \"Table\"}]"
motivation: 探究多模态大语言模型在抽象视觉推理任务（Bongard问题）上的能力局限。
method: 设计了多种适用于MLLM的解题策略，并在合成和真实世界数据集上测试了多个模型。
result: MLLM在真实世界数据集上取得部分成功，但在合成BPs上表现困难。
conclusion: 揭示了MLLM在抽象推理方面的不足，并提供了新数据集以促进研究。
---

## Abstract
Abstract visual reasoning (AVR) involves discovering shared concepts across images through analogy, akin to solving IQ test problems. Bongard Problems (BPs) remain a key challenge in AVR, requiring both visual reasoning and verbal description. We investigate whether multimodal large language models (MLLMs) can solve BPs by formulating a set of diverse MLLM-suited solution strategies and testing $4$ proprietary and $4$ open-access models on $3$ BP datasets featuring synthetic (classic BPs) and real-world (Bongard HOI and Bongard-OpenWorld) images. Despite some successes on real-world datasets, MLLMs struggle with synthetic BPs. To explore this gap, we introduce Bongard-RWR, a dataset representing synthetic BP concepts using real-world images. Our findings suggest that weak MLLM performance on classical BPs is not due to the domain specificity, but rather comes from their general AVR limitations. Code and dataset are available at: https://github.com/pavonism/bongard-rwr

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义
- **研究动机**：类比推理是人类认知的关键，Bongard Problems（BPs）是经典抽象视觉推理（AVR）任务，要求同时进行视觉推理和自然语言描述。多模态大语言模型（MLLMs）的出现为端到端解决BPs提供了可能，但其抽象推理能力尚不明确。
- **核心问题**：MLLMs能否解决Bongard Problems？它们在合成与真实世界图像上的表现差异根源是什么？
- **整体含义**：揭示当前MLLMs在抽象概念识别、跨图像比较、上下文利用等方面的根本性局限，为未来模型改进提供方向。

## 2. 方法论：核心思想与关键技术
- **核心思想**：将BPs转化为MLLMs可处理的形式，设计多种提示策略，涵盖开发生成答案和二元分类两种评估范式。
- **关键技术细节**：
  - **生成策略（7种）**：
    - **Direct**：直接输入整张BP矩阵图像，要求输出自然语言规则。
    - **Descriptive**：先对每个图像面板分别生成描述（独立上下文），再基于所有描述生成答案。
    - **Descriptive-iterative**：在单侧面板描述过程中利用上下文窗口逐步细化概念。
    - **Descriptive-direct**：在Descriptive基础上增加整张BP图像作为额外输入。
    - **Contrastive**：对左右侧对应的图像对生成差异描述，再整合为答案。
    - **Contrastive-iterative**：在单一上下文窗口中逐步改进差异描述。
    - **Contrastive-direct**：Contrastive基础上增加整张BP图像。
  - **二元分类策略（3种）**：
    - **Ground-Truth**：提供整张BP图像和真实答案，判断是否匹配。
    - **Incorrect Label**：提供整张BP图像和错误答案，判断是否不匹配。
    - **Images to Sides**：给定两张测试图像（分别来自左右侧），要求分配到正确侧。
  - **答案评估方法**：使用4个专有MLLM组成硬投票集成，判断生成答案是否与真实答案语义一致。
- **公式/算法**：未涉及明确数学公式，仅用伪代码（Algorithm 1）描述Bongard-RWR数据集生成流程：利用GPT-4o翻译概念、Pexels API下载图像、模型筛选、手动校正。

## 3. 实验设计
- **数据集**：
  - **经典Bongard（合成）**：前100个手动构建的合成BPs（Bongard, 1970）。
  - **Bongard HOI**：人类-物互动真实图像数据集，取100个样本（测试集分层抽样）。
  - **Bongard-OpenWorld**：开放世界自由形式概念真实图像数据集，取100个样本。
  - **Bongard-RWR**（新提出）：60个真实世界图像BPs，对应合成BPs的概念。
  - **Bongard-RWR变体**：RWR-S（裁剪为正方形）、RWR-G（灰度）、RWR-SG（正方形灰度）。
- **Benchmark**：以随机猜测基线（50%准确率）作为二元分类任务的下界；人类在Bongard-RWR上的平均正确率（65%，39.2/60）作为上限参考。
- **对比方法**：
  - 4个专有MLLM：GPT-4o, GPT-4 Turbo, Gemini 1.5 Pro, Claude 3.5 Sonnet。
  - 4个开源MLLM：InternVL2-8B, LLaVA-1.6 Mistral-7B, Phi-3.5-Vision, Pixtral 12B。
  - 额外模型缩放实验：GPT-4o mini, Gemini 1.5 Flash, InternVL2-26B/40B/76B, LLaVA-v1.6 13B/34B, LLaVA-NeXT 72B/110B等。
  - 与现有方法对比：Wu et al.(2024)的两阶段方法（BLIP-2+ChatGPT）等。

## 4. 资源与算力
- **文中明确信息**：
  - 开源模型在NVIDIA DGX A100节点上本地运行；专有模型通过API调用。
  - 未明确GPU型号、数量、训练时长（因所有模型均直接使用预训练权重，无微调）。
  - 数据集生成使用了GPT-4o和Pexels API，未详细说明计算开销。
- **未明确说明**：具体GPU小时数、总API调用次数、生成Bongard-RWR的耗时等。

## 5. 实验数量与充分性
- **实验分组**：
  - 主实验：在4个数据集上，对8个模型分别测试3种二元分类 + 7种生成策略，共约(4×3 + 8×7)×4数据集 ≈ 272组条件（注意有些模型未全部覆盖）。
  - 额外实验：
    - 模型缩放实验（不同大小模型在Direct和Descriptive策略上，4数据集）。
    - 多类分类实验（概念选择，k=2,4,8,16）。
    - Bongard-RWR变体对比（4种变体，4个开源模型，3种二元分类）。
    - 人类对照实验（30位参与者，Bongard-RWR）。
- **充分性评价**：
  - **优点**：策略覆盖面广（生成+分类），数据集横跨合成/真实/跨域，消融实验（迭代、直接变体）系统，并引入人类基线。
  - **不足**：实验规模受限于100个实例（Bongard-RWR仅60），部分开源模型在部分策略上无法生成有效输出（如LLaVA-1.6 JSON格式问题）；未进行统计显著性检验；评估依赖MLLM集成，存在潜在偏差。

## 6. 主要结论与发现
- MLLMs在合成BPs上表现极差（最佳GPT-4o只有17/100正确），在真实世界数据集（Bongard HOI、Bongard-OpenWorld）上显著提升（最佳约40-46/100）。
- **Bongard-RWR实验证明**：MLLMs在表示相同抽象概念的真实图像上仍表现糟糕（最佳GPT-4o仅5/60），说明弱点不在于领域特异性，而在于通用的抽象推理能力不足。
- **策略对比**：Descriptive策略整体最优；Contrastive策略（人类常用方式）反而更差，表明MLLMs不擅长直接跨图像比较。
- **上下文利用**：迭代策略（-iterative）未稳定提升，Direct策略增加整图（-direct）偶有改善，但一致性差。
- **专有模型显著优于开源模型**，但Pixtral 12B在多个任务上具备竞争力。
- **人类仍大幅领先**：Bongard-RWR上人类平均65%正确率，而所有模型合计只解决22/60。

## 7. 优点
- **策略多样性**：系统设计了7种生成策略和3种分类策略，全面覆盖不同推理路径。
- **新数据集贡献**：Bongard-RWR填补了对比合成/真实世界抽象推理的空白，可支持跨域分析。
- **严谨评估**：采用MLLM集成对生成答案进行语义一致性判断，并手动验证（99%一致）；在Bongard-RWR上开展人类实验，提供有力基线。
- **深入分析**：通过模型缩放、多类分类、数据集变体等实验，多维度揭示推理局限。
- **开源与可复现**：代码和数据集公开。

## 8. 不足与局限
- **实验覆盖有限**：
  - 仅使用Bongard Problems作为AVR代表，未涉及ARC、RPM等其他主流任务。
  - 数据集实例数较少（合成100，Bongard-RWR 60），可能影响结论稳定性。
  - 开源模型版本较旧（如LLaVA-1.6），未包含最新更强模型（如InternVL2.5 78B等仅在缩放实验中部分使用）。
- **评估偏差风险**：
  - 自然语言答案评估依赖MLLM集成（仅4个专有模型），可能偏向于与这些模型一致的答案。
  - 仅量化了正确/错误，未分析错误类型或模型置信度。
- **方法局限**：
  - 策略设计基于特定提示模板，未进行提示优化（如链式思考）。
  - 未尝试微调或参数调整，仅评估零样本/少样本性能。
- **应用限制**：研究聚焦于诊断当前模型能力，未提出改进方法或训练方案。
- **伦理影响**：仅简要提及可能被用于作弊IQ测试等风险，未深入讨论。

（完）
