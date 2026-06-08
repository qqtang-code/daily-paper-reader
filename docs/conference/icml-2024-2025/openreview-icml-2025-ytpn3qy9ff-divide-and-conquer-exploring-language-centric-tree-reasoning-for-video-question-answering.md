---
title: "Divide and Conquer: Exploring Language-centric Tree Reasoning for Video Question-Answering"
title_zh: 分而治之：探索面向视频问答的语言中心树推理
authors: "Zhaohe Liao, Jiangtong Li, Siyu Sun, Qingyang Liu, Fengshun Xiao, Tianjiao Li, Qiang Zhang, Guang Chen, Li Niu, Changjun Jiang, Liqing Zhang"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=yTpn3QY9Ff"
tags: ["query:mm-cot"]
score: 9.0
evidence: 面向视频问答的语言中心树推理，逐步分解
tldr: 该论文针对视频问答提出语言中心树推理框架。LTR首先递归地将原始问题分解为逻辑子问题，生成语言中心的逻辑树，然后逐步解决这些子问题。这增强了多模态大模型的推理能力和可解释性。实验表明LTR在多个VideoQA数据集上取得了优异性能，推理过程更透明。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-ytpn3qy9ff/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 847, \"height\": 763, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ytpn3qy9ff/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1767, \"height\": 803, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ytpn3qy9ff/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1776, \"height\": 1393, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-ytpn3qy9ff/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1770, \"height\": 707, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ytpn3qy9ff/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1768, \"height\": 547, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ytpn3qy9ff/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 859, \"height\": 474, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ytpn3qy9ff/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 860, \"height\": 584, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ytpn3qy9ff/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 860, \"height\": 392, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ytpn3qy9ff/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1421, \"height\": 809, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ytpn3qy9ff/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1251, \"height\": 599, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ytpn3qy9ff/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 978, \"height\": 521, \"label\": \"Table\"}]"
motivation: 现有MLLM在视频推理中过程不透明且难以控制，需提升推理能力与可解释性。
method: 提出LTR框架，递归分解问题为逻辑树，逐步征服每个子问题，实现结构化推理。
result: 在多个VideoQA数据集上性能提升，推理过程更清晰可解释。
conclusion: 分治策略有效提升多模态推理的准确性和透明性。
---

## Abstract
Video Question-Answering (VideoQA) remains challenging in achieving advanced cognitive reasoning due to the uncontrollable and opaque reasoning processes in existing Multimodal Large Language Models (MLLMs). To address this issue, we propose a novel Language-centric Tree Reasoning (LTR) framework that targets on enhancing the reasoning ability of models. In detail, it recursively divides the original question into logically manageable parts and conquers them piece by piece, enhancing the reasoning capabilities and interpretability of existing MLLMs. Specifically, in the first stage, the LTR focuses on language to recursively generate a language-centric logical tree, which gradually breaks down the complex cognitive question into simple perceptual ones and plans the reasoning path through a RAG-based few-shot approach. In the second stage, with the aid of video content, the LTR performs bottom-up logical reasoning within the tree to derive the final answer along with the traceable reasoning path. Experiments across 11 VideoQA benchmarks demonstrate that our LTR framework significantly improves both accuracy and interpretability compared to state-of-the-art MLLMs. To our knowledge, this is the first work to implement a language-centric logical tree to guide MLLM reasoning in VideoQA, paving the way for language-centric video understanding from perception to cognition.

---

## 论文详细总结（自动生成）

# 论文中文详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：视频问答（VideoQA）中，现有多模态大模型（MLLMs）的推理过程不可控且不透明，难以实现高级认知推理（System-2 reasoning）。用户无法追溯错误原因，导致结果不可信。
- **研究动机**：现有方法（如Video-LLaMA、Qwen2-VL等）虽能提供一定解释，但推理过程仍是黑箱；可解释方法（如VoT、DSTN）存在逻辑结构不足或缺乏容错性等问题。作者希望同时提升推理的准确性和可解释性。
- **整体含义**：提出语言中心树推理（LTR）框架，以语言为核心驱动力，通过“分而治之”策略，将复杂认知问题逐步分解为简单感知问题，再自底向上推理，实现透明、可控、可验证的推理过程。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：采用两阶段“分治”框架，第一阶段递归分解问题，生成语言中心的逻辑树；第二阶段借助视频内容，在树上自底向上推理得到最终答案。
- **第一阶段：Divide（自上而下递归分解）**
  - **Question Division**：利用视频内容提示，让MLLM将复杂问题分解为若干逻辑子问题。通过RAG（检索增强生成）从AGQA-Decomp数据集中检索相似的（问题-子问题对）作为少样本示例，提升分解质量。
  - **Recursive Perceptual Checking**：对于每个子问题，再次结合视频判断该问题是否已简化为“可感知的”（即MLLM可直接回答）。若否，则继续分解；直至所有叶子节点都是可感知的简单问题。最终生成一个层次化的语言中心逻辑树。
- **第二阶段：Conquer（自底向上树推理）**
  - **Perceptual Question Answering**：用MLLM对所有叶子问题进行回答，得到证据。
  - **Video-Aided Logical Reasoning**：对每个非叶子节点，基于其子问题的答案和视频内容，推理得到该节点的答案。视频信息可弥补分解过程中的疏漏或错误。
  - **In-Process Answer Verification**：对中间节点答案进行逻辑一致性和视觉一致性验证。若发现冲突，则反馈并重新执行推理步骤，增强鲁棒性。
- **模型无关性**：LTR是训练无关的（training-free），可即插即用于任何MLLM（如VideoLLaMA3、VideoChat2、Qwen2-VL、LLaVA-OneVision等）。

## 3. 实验设计：数据集、基准、对比方法

- **数据集**：11个VideoQA基准，涵盖不同难度和类型：
  - 开放型：MSVD-QA、MSRVTT-QA、TGIF-QA、ActivityNet-QA
  - 多重选择型：AGQA-Decomp、NExT-QA、Causal-VidQA、STAR、Ego-Schema、Video-MME、MVBench
- **基准评估指标**：
  - 开放型：使用GPT-3.5评估生成回答的准确率（Acc）和评分（Score）
  - 多重选择型：MLLM根据问题和生成响应从选项中选答
  - 在AGQA-Decomp上额外评估组合一致性（cR、cP、cF1）
- **对比方法**：共4个基线MLLM（VideoLLaMA3、VideoChat2、Qwen2-VL、LLaVA-OneVision），同时与Vo-T、DSTN、Video-LLaVA、MiniGPT4-Video等9种方法在AGQA-Decomp上对比。零样本设置，统一采用16帧采样、分辨率336×336。

## 4. 资源与算力

- 论文中**未明确说明**所使用的GPU型号、数量、训练时长等算力信息。仅提到其他设置遵循各基线模型的零样本生成推荐设置，最大生成长度为2048 tokens。由于LTR框架是训练无关的（仅推理），算力消耗主要体现在多次调用MLLM进行分解和推理，但文中未给出量化对比。

## 5. 实验数量与充分性

- **实验数量**：非常充分。
  - 主实验在11个数据集上报告结果，覆盖开放型、多重选择型、组合一致性评估。
  - 消融实验：在Causal-VidQA和NExT-QA上针对第一阶段（w/o video、w/o RAG）和第二阶段的三个组件（w/o A.V.、w/o P.L.Q.A、R. w/o video）进行了消融，共7个对照设置。
  - 在附录中补充了更多数据集（MSVD-QA、MSRVTT-QA、TGIF-QA、ActivityNet-QA、STAR、Video-MME等）的完整结果。
  - 提供了定性案例和错误分析。
- **充分性与公平性**：
  - 实验设计较客观、公平：所有基线模型均使用其官方发布权重和推荐指令复现，零样本设置一致。
  - 覆盖了从简单感知到复杂认知的各种任务类型，结果一致表明LTR在认知任务上提升更显著。
  - 消融实验验证了各组件的必要性。但未报告多次运行的标准差，结果仅用单一随机种子（未说明），可能存在一定波动风险。

## 6. 论文的主要结论与发现

- LTR框架显著提升了4种基线MLLM在11个VideoQA基准上的准确率和可解释性。
- 在认知密集型任务（如反事实推理、因果推理、时间推理）上提升幅度（2.4%~4.2%）大于简单感知任务（0.9%~2.1%），表明LTR特别擅长增强复杂推理能力。
- 在AGQA-Decomp上，组合一致性（cF1）提升10%以上，大幅优于纯准确率提升，说明树推理有助于保持逻辑一致性。
- 定性分析显示，LTR能捕捉到分解中的逻辑陷阱（如背景物体不应被计数），并通过视觉辅助纠正部分错误，但严重感知错误仍可能导致不可恢复的失败。
- 语言中心的树结构使推理过程完全可追溯，便于错误定位和理解。

## 7. 优点

- **创新性**：首次将语言中心逻辑树引入VideoQA，实现“分而治之”的结构化推理，不同于传统的端到端黑箱或纯模块网络方法。
- **训练无关与模型无关**：框架无需任何训练，可直接增强任意MLLM，具有很强的通用性和实用性。
- **可解释性**：完整的推理路径可追踪，每个中间节点都有逻辑和视觉依据，支持错误诊断和用户信任。
- **容错性**：通过视频辅助推理和验证步骤，能容忍分解过程中的部分错误和逻辑陷阱，不同于NMN的硬性程序执行。
- **实验全面**：覆盖11个数据集，消融实验充分，并提供了定性案例和错误分析，论证充分。

## 8. 不足与局限

- **长视频理解限制**：框架依赖固定16帧采样，对于Ego-Schema等长视频基准，感知信息不足，导致推理效果提升有限（仅1.4%~2.5%）。作者也承认这是底层MLLM的固有限制。
- **计算开销**：递归分解和多次调用MLLM会增加推理延迟，不适用于实时或低延迟场景。文中未量化对比计算成本。
- **依赖零样本能力**：分解和推理完全依赖MLLM本身的知识和逻辑，对于特定领域或罕见概念可能难以正确分解。RAG数据库仅用AGQA-Decomp，泛化性有限。
- **感知错误的级联风险**：尽管视频辅助推理可部分纠错，但严重感知错误仍会导致最终答案失败（如定性案例2），缺乏对感知质量的控制。
- **未报告统计显著性**：未给出多次运行的标准差或置信区间，结果可能受单次随机性影响。
- **资源信息缺失**：未提供训练或推理的算力要求，不利于资源评估和复现。

（完）
