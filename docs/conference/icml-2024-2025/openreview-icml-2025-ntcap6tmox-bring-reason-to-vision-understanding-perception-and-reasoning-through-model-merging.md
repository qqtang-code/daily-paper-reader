---
title: "Bring Reason to Vision: Understanding Perception and Reasoning through Model Merging"
title_zh: 将推理引入视觉：通过模型合并理解感知与推理
authors: "Shiqi Chen, Jinghan Zhang, Tongyao Zhu, Wei Liu, Siyang Gao, Miao Xiong, Manling Li, Junxian He"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=ntCAP6tMoX"
tags: ["query:mm-cot"]
score: 8.0
evidence: 通过模型合并将推理能力从LLM迁移到VLM
tldr: 视觉-语言模型（VLM）的感知与推理能力如何结合仍不明确。本文提出跨模态模型合并方法，将大语言模型（LLM）的逻辑推理能力迁移到VLM中。实验证明，无需额外训练即可显著提升VLM的推理性能。该工作提供了一种注理能力的高效途径，有助于理解多模态模型中感知与推理的交互机制。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-ntcap6tmox/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1752, \"height\": 657, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ntcap6tmox/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 850, \"height\": 639, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ntcap6tmox/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 765, \"height\": 440, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ntcap6tmox/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1771, \"height\": 998, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ntcap6tmox/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1765, \"height\": 993, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ntcap6tmox/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1692, \"height\": 620, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ntcap6tmox/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1076, \"height\": 372, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ntcap6tmox/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 625, \"height\": 359, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ntcap6tmox/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 779, \"height\": 790, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ntcap6tmox/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 799, \"height\": 588, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-ntcap6tmox/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1772, \"height\": 530, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ntcap6tmox/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1771, \"height\": 423, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ntcap6tmox/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1770, \"height\": 477, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ntcap6tmox/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1773, \"height\": 641, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ntcap6tmox/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1083, \"height\": 317, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ntcap6tmox/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1777, \"height\": 237, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ntcap6tmox/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1775, \"height\": 211, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ntcap6tmox/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1122, \"height\": 838, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ntcap6tmox/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1610, \"height\": 335, \"label\": \"Table\"}]"
motivation: 探索如何将大语言模型的强大推理能力迁移到视觉-语言模型中。
method: 提出跨模态模型合并，直接连接不同模型的参数以融合感知和推理。
result: 无需训练即可提升VLM的推理能力，实验验证了方法的有效性。
conclusion: 模型合并为多模态推理提供了一种轻量级迁移学习方案。
---

## Abstract
Vision-Language Models (VLMs) combine visual perception with the general capabilities, such as reasoning, of Large Language Models (LLMs). However, the mechanisms by which these two abilities can be combined and contribute remain poorly understood.
In this work, we explore to compose perception and reasoning through model merging that connects parameters of different models.  
Unlike previous works that often focus on merging models of the same kind, we propose merging models **across modalities**, enabling the incorporation of the reasoning capabilities of LLMs into VLMs. 
Through extensive experiments, we demonstrate that model merging offers a successful pathway to transfer reasoning abilities from LLMs to VLMs in a **training-free** manner.
Moreover, we utilize the merged models to understand the internal mechanism of perception and reasoning and how merging affects it. We find that perception capabilities are predominantly encoded in the early layers of the model, whereas reasoning is largely facilitated by the middle-to-late layers. After merging, we observe that all layers begin to contribute to reasoning, whereas the distribution of perception abilities across layers remains largely unchanged. These observations shed light on the potential of model merging as a tool for multimodal integration and interpretation.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：视觉-语言模型（VLM）将视觉感知与大语言模型（LLM）的通用能力（如推理）相结合，但两者如何协同、内部机制尚不明确。现有VLM在复杂多模态推理任务上往往落后于纯文本LLM，主要原因之一是缺乏高质量的多模态推理训练数据。
- **研究动机**：能否通过一种“免费午餐”的方式，将LLM强大的推理能力迁移到VLM中，而不需要额外的训练？同时，利用这种方法作为工具，探究VLM中感知与推理能力在参数空间中的分布与交互机制。
- **整体含义**：本文首次探索跨模态模型合并（model merging across modalities），实现推理能力的训练自由转移，并借此揭示VLM内部的工作原理。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
- **核心思想**：利用模型合并技术，直接对VLM的语言模型部分与专用的推理LLM进行参数加权平均，实现能力组合。不同于以往同类型模型合并，本文跨越视觉与文本模态。
- **关键技术细节**：
    - 仅合并VLM的语言模型组件（保持视觉塔和投影器不变）。
    - 定义任务向量（task vector）：τ = θ_ft - θ_base，其中θ_base是共享的基模型（如LLaMA-3），θ_ft是微调后的模型。
    - 线性合并公式：θ'_vlm = θ_base + λ·τ_vlm + (1-λ)·τ_reason，其中λ控制VLM原始能力与推理能力的平衡（λ ∈ [0,1]）。
    - 超参数λ通过在验证集（MathVista）上调优确定，主要实验中取λ=0.9。
    - 还尝试了TIES合并、Dare合并、层交换等变体作为对比。
- **算法流程**（文字说明）：
    1. 选择与VLM语言模型同族的基模型（如LLaMA-3-8B）。
    2. 获得VLM语言模型组件相对于基模型的任务向量τ_vlm。
    3. 获得推理LLM（如Dart-Math）相对于同一基模型的任务向量τ_reason。
    4. 计算合并后的参数：θ_new = θ_base + λ·τ_vlm + (1-λ)·τ_reason。
    5. 将θ_new替换到VLM的语言模型部分，输出合并后的VLM。

## 3. 实验设计：使用了哪些数据集 / 场景，它的 benchmark 是什么，对比了哪些方法
- **使用的VLM**：
    - LLaVA-NeXT-LLaMA3-8B（主实验）
    - Idefics2-8B（基于Mistral）
    - InternVL2-LLaMA3-76B（大规模）
- **推理任务向量（LLM）**：
    - Dart-Math（两个变体：Dart-Uniform、Dart-Prop）
    - MAmmoTH-1、MAmmoTH-2
    - Magpie-v0.3
    - DeepSeek-R1-Distill
    - MetaMath（仅用于Idefics）
- **评估基准**：
    - **数学推理**：MathVista（含General与Math子集）、MathVerse（含Text-Dominant、Text-Lite、Vision-Integrated、Vision-Dominant、Vision-Only）、MathVision、DynaMath、MMStar（含Math子集）——共计5个主流基准。
- **对比方法**：
    - 基线：原始VLM（无合并）。
    - 不同推理任务向量的线性合并（相同λ）。
    - 不同合并方法的比较（TIES、Dare、层交换等）。
    - 不同λ的敏感性实验（在[0.8,0.85,0.9]中调优）。
    - 逻辑推理向量的迁移实验（验证跨域泛化）。
    - 显著性检验（标记统计显著的结果）。

## 4. 资源与算力
- 论文**没有明确说明**使用的GPU型号、数量、训练时长等算力资源。
- 由于方法是“训练自由”（training-free），仅需推理和参数合并，不涉及训练过程，因此算力需求很小。推测可以使用单块或少量GPU（如A100 80GB）完成合并与评估，但文中未给出具体配置。

## 5. 实验数量与充分性
- **实验数量**：非常丰富。主实验覆盖3种VLM × 5~6种推理由，在5个基准上报告结果（表2、表3），共计约30余组主要结果。还进行了：
    - 合并方法对比（TIES、Dare、层交换，表5）。
    - 超参数λ调优实验（附录）。
    - 逻辑推理迁移实验（附录表6）。
    - 显著性检验（附录表9）。
    - 对MathVista子任务的分析（图2、图7、图8）。
    - 对回答长度与准确率关系的分析（图3）。
    - 对模型内部层级的 knockout 分析（图4、图5）。
- **充分性评估**：
    - 实验设计覆盖了不同规模的VLM、不同系列的推理LLM、多个数学推理基准，具有较好的泛化性。
    - 包含了消融（不同合并方法、不同λ）和解释性分析，较为全面。
    - 公平性：统一使用相同λ（在MathVista上调优后固定），对不同方法使用相同的搜索空间，对比较为客观。
    - 但仍存在一定局限（见缺点部分）。

## 6. 论文的主要结论与发现
- **结论1**：跨模态模型合并能有效将LLM的数学推理能力迁移到VLM，显著提升数学推理基准上的性能（例如在MathVista Math子集上提升3.5~3.6个点，在MathVerse Text-Dominant上提升6个点），且对视觉主导任务影响较小。
- **结论2**：合并后的VLM展现出更好的推理时间缩放能力（inference-time scaling），即回答长度显著增加（链式推理更强），且与性能提升呈线性关系。
- **结论3**（通过knockout分析发现）：
    - 感知能力主要编码在VLM的早期层（前几层）。
    - 推理能力主要集中在中后层。
    - 合并后，推理能力扩散到几乎所有层，而感知能力的层分布基本不变。
- **结论4**（关于不同VLM）：
    - 对于已经经过充分数学SFT的VLM（如Idefics2），合并带来的提升较小，表明基数模型的能力重叠限制了进一步收益。
    - 对于大规模VLM（InternVL2-76B），合并仍带来约1个点的提升，说明方法可扩展。

## 7. 优点：方法或实验设计上的亮点
- **方法简单、高效、训练自由**：无需任何微调或额外数据，仅通过参数加权平均即可实现能力迁移，适合快速部署。
- **跨模态首创**：打破传统模型合并局限于同类型模型的惯例，首次探索视觉与语言模型之间的参数组合。
- **解释性工具**：利用合并作为解释手段，通过knockout实验揭示了VLM内感知与推理的层次分离，为理解多模态模型内部机制提供了新视角。
- **实验全面**：覆盖多种VLM架构与规模、多种推理LLM、多个难度的数学基准，并进行了显著性检验，结论稳健。
- **开源代码**：提供了完整的实现代码，有利于复现和后续研究。

## 8. 不足与局限
- **局限1**：方法对视觉主导任务（如Figure QA、Visual QA）有轻微性能下降（约1-2个点），说明合并存在权衡，并非无代价。
- **局限2**：提升主要集中在数学推理，对其他类型的推理（如常识推理、科学推理）缺乏验证；仅附录中简单测试了逻辑推理迁移。
- **局限3**：超参数λ需要基于某个验证集（此处为MathVista）调优，在实际应用中可能需要调整。
- **局限4**：模型合并假设所有模型共享相同的基模型（如LLaMA-3），限制了适用性；如果VLM和推理LLM基模型不同，则无法直接合并。
- **局限5**：对已经具备强数学能力的VLM（如Qwen2-VL）提升有限甚至下降，表明该方法对“能力溢出”情况帮助不大。
- **局限6**：未讨论合并后模型的安全性、一致性或偏见问题，可能存在未知风险。
- **局限7**：实验资源未明确报告，可复现性稍显不足。

（完）
