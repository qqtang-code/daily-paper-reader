---
title: "SRPO: Enhancing Multimodal LLM Reasoning via Reflection-Aware Reinforcement Learning"
title_zh: SRPO：通过反思感知强化学习增强多模态大模型推理
authors: "Zhongwei Wan, Zhihao Dou, Che Liu, Yu Zhang, Dongfei Cui, Qinjian Zhao, Hui Shen, Jing Xiong, Yi Xin, Yifan Jiang, Chaofan Tao, Yangfan He, Mi Zhang, Shen Yan"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=h3lyFa5e1W"
tags: ["query:mm-cot"]
score: 8.0
evidence: 反思感知强化学习增强多模态链式推理
tldr: SRPO提出反思感知强化学习框架，增强多模态大模型的自反思和自纠正能力。包含两阶段：先训练反思生成，再通过GRPO优化推理质量。在复杂推理任务上显著提升性能。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-h3lyfa5e1w/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1436, \"height\": 417, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h3lyfa5e1w/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1424, \"height\": 314, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h3lyfa5e1w/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1436, \"height\": 519, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h3lyfa5e1w/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1435, \"height\": 349, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h3lyfa5e1w/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 502, \"height\": 377, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h3lyfa5e1w/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1426, \"height\": 489, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h3lyfa5e1w/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 467, \"height\": 423, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h3lyfa5e1w/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 635, \"height\": 622, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h3lyfa5e1w/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 548, \"height\": 421, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h3lyfa5e1w/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 576, \"height\": 267, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h3lyfa5e1w/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1427, \"height\": 1305, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-h3lyfa5e1w/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1444, \"height\": 1060, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h3lyfa5e1w/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 563, \"height\": 609, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h3lyfa5e1w/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1420, \"height\": 399, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h3lyfa5e1w/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1087, \"height\": 181, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h3lyfa5e1w/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1354, \"height\": 244, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h3lyfa5e1w/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 837, \"height\": 188, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h3lyfa5e1w/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1093, \"height\": 238, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h3lyfa5e1w/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1039, \"height\": 122, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h3lyfa5e1w/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1099, \"height\": 259, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h3lyfa5e1w/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1173, \"height\": 156, \"label\": \"Table\"}]"
motivation: 多模态大模型在复杂推理中缺乏有效的自反思和自纠正能力。
method: 两阶段反思感知强化学习框架，先生成反思，再通过GRPO优化。
result: 在多个多模态推理基准上取得显著改进。
conclusion: 反思感知强化学习能有效提升多模态模型的推理深度。
---

## Abstract
Multimodal large language models (MLLMs) have shown promising capabilities in reasoning tasks, yet still struggle significantly with complex problems requiring explicit self-reflection and self-correction, especially compared to their unimodal text-based counterparts. Existing reflection methods are simplistic and struggle to generate meaningful, instructive feedback, as the reasoning ability and knowledge limits of pre-trained models are largely fixed during initial training. To overcome these challenges, we propose \textit{multimodal \textbf{S}elf-\textbf{R}eflection enhanced reasoning with Group Relative \textbf{P}olicy \textbf{O}ptimization} \textbf{SRPO}, a two-stage reflection-aware reinforcement learning (RL) framework explicitly designed to enhance multimodal LLM reasoning. In the first stage, we construct a high-quality, reflection-focused dataset under the guidance of an advanced MLLM, which generates reflections based on initial responses to help the policy model to learn both reasoning and self-reflection. In the second stage, we introduce a novel reward mechanism within the GRPO framework that encourages concise and cognitively meaningful reflection while avoiding redundancy. Extensive experiments across multiple multimodal reasoning benchmarks—including MathVista, MathVision, Mathverse, and MMMU-Pro—using Qwen-2.5-VL-7B and Qwen-2.5-VL-32B demonstrate that SRPO significantly outperforms state-of-the-art models, achieving notable improvements in both reasoning accuracy and reflection quality.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 核心问题与整体含义（研究动机和背景）

多模态大语言模型（MLLMs）在复杂推理任务中表现出一定能力，但与纯文本推理模型相比，在需要明确自反思（self-reflection）和自纠正（self-correction）的复杂问题上仍然存在显著不足。现有反思方法通常较为简单，难以生成有意义的指导性反馈，因为预训练模型的推理能力和知识边界在很大程度上在初始训练阶段就已固定。论文旨在通过一种新的反思感知强化学习框架，突破这一限制，显式地增强MLLMs的自我反思和纠错能力，从而提升整体推理质量。

## 2. 方法论：核心思想、关键技术细节

**核心思想**：提出两阶段反思感知强化学习框架 **SRPO**（多模态自反思增强推理 + 组相对策略优化）。  
**第一阶段 – 冷启动初始化**：  
- 构造高质量反思数据集：从 Mulberry、MathV360K、LLaVA-CoT 等公开数据集中选取约 10K 样本。  
- 使用先进 MLLM（如 GPT-o4-mini）根据策略模型的初始响应与真实答案的差异生成反思内容。  
- 通过有监督微调（SFT）训练策略模型，使其学会在给出初始答案后进行反思和修正。  
- 损失函数：  
  \[
  L_{\text{cold-start}} = -\mathbb{E}_{\tau\sim D}\left[ \sum_{t=1}^T \log \pi_{\text{initial}}(a_1, \langle\text{reflection}\rangle, a_2 | q) \right]
  \]
  其中 \(a_1\) 为初始回答，\(\langle\text{reflection}\rangle\) 为生成的反思，\(a_2\) 为正确答案。  

**第二阶段 – 反思感知强化学习**：  
- 基于 GRPO（Group Relative Policy Optimization）算法，引入专门设计的反思感知奖励函数。  
- 总奖励：  
  \[
  R_{\text{total}} = R_{\text{task}} + R_{\text{reflection}}
  \]
  - **任务奖励** \(R_{\text{task}}\)：包括格式奖励（0.5分，要求正确使用 `<think>` 等格式）和准确性奖励（0.5分，第一轮答案是否正确）。  
  - **反思奖励** \(R_{\text{reflection}}\)：包含三个部分  
    - 格式指示符 \(I_{\text{ref}}\)（0 或 0.25：反思段格式正确）  
    - 长度奖励 \(f_{\text{len}}(L_{\text{response}})\)：鼓励输出简洁，用指数形式惩罚过长或过短  
    - 有效性指示符 \(I_{\text{eff}}\)：根据反思是否真正改进答案给予额外奖励（修正错误得 +0.5，保持正确得 +0.25，未修正或误导分别得 0 或 -0.25）  

**优势**：相比标准 GRPO，SRPO 通过结构化反思格式、平滑长度约束、有效性奖励等机制，避免模型利用反思进行奖励游戏（如生成冗长但无意义的反思），引导模型产生真正有益的自我修正。

**算法流程**：  
1. 收集初始 CoT 回答 → 区分正确/错误 → 生成反思 → 构建 SFT 数据集。  
2. SFT 训练策略模型（Qwen-2.5-VL-7B/32B-Instruct）获得基本反思能力。  
3. 在 RL 阶段，对每个问题采样 G 个回答，使用 GRPO 优化，奖励函数中融入反思成分。

## 3. 实验设计

### 数据集
- **SFT 数据**：从 Mulberry（260K）、MathV360K、LLaVA-CoT（100K）中采样并筛选出约 10K 高质量反思样本（70% 初始错误，30% 正确）。  
- **RL 数据**：从 ScienceQA、GeoQA、ChartQA、DVQA、AI2D、MATH、Virgo、R1-OneVision、MMK12、PhyX 等共计约 37K 样本（涵盖数学、几何、图表、自然科学、通用推理等）。  

### 基准测试（Benchmark）
- **数学推理**：MathVista、MathVerse、MathVision、OlympiadBench、WeMath  
- **通用推理**：MMMU-Pro、MMMU、EMMA  
- **跨学科推理**：MMK12（含物理、化学、生物）  

### 对比方法
- **闭源模型**：Claude3.7-Sonnet、GPT-4o、GPT-o1、Gemini2-flash、Seed1.5-VL-T  
- **开源通用 MLLMs**：InternVL2.5（7B-38B）、Qwen-2.5-VL（7B-72B）、Kimi-VL-16B、Llava-OV-7B  
- **开源推理 MLLMs**：MM-Eureka、OpenVLThinker、VL-Rethinker、R1-Onevision、R1-VL、Vision-R1、InternVL2.5-MPO  

## 4. 资源与算力

论文明确报告了训练资源：
- **7B 模型**：SFT 阶段 8×NVIDIA H100，约 3.5 小时；RL 阶段 8×H100，约 31.2 小时。  
- **32B 模型**：SFT 阶段 4×8 H100（即 32 GPU），约 4.7 小时；RL 阶段 4×8 H100，约 45.1 小时。  
- 采用 Adam 优化器，学习率 1×10⁻⁶，bf16 混合精度，梯度 checkpointing 和 flash attention。  
- 未报告多轮重复实验的算力消耗总估算。

## 5. 实验数量与充分性

论文设计并报告了多个维度的实验，较为充分：
- **主实验**：表 1 展示 7B 和 32B 模型在 8 个基准上的结果；表 2 展示跨学科 MMK12 的 4 个学科结果。  
- **消融实验**：  
  - 表 3：RL 数据量（5K/15K/37K）、是否使用反思 SFT、反思 RL、长度奖励、有效性奖励。  
  - 表 4：与 2-Step Thinking 模式对比。  
  - 表 5：反思格式与教师蒸馏的剥离分析。  
  - 表 6：反射长度奖励系数 α 的敏感度。  
- **额外验证**：  
  - 图 5：将反思融入 PPO 和 DAPO 的对比。  
  - 图 4：训练动态（奖励、长度、裁剪率）。  
  - 图 3：定性案例展示。  
- **量化评估**：附录 B.1 中有人工评审和 GPT-4o 作为评判者的反思质量打分。  

**公平性**：在主实验中对比了包括闭源和开源的最新模型，消融实验细致分离各个组件。但所有 RL 实验仅使用一个固定随机种子，未报告误差棒或置信区间，可能影响结果的统计可靠性。

## 6. 主要结论与发现

1. **SRPO 显著优于现有模型**：在 MathVista 等基准上，SRPO-7B 达到 75.8%，SRPO-32B 达到 78.5%，超过 GPT-o1（73.9%）和所有开源模型。  
2. **反思 SFT 和反思 RL 均不可或缺**：单独移除任一阶段性能大幅下降（表 3）。  
3. **反思奖励组件有效**：长度奖励和有效性奖励的移除都会降低性能（从 53.5 到 52.0-53.1）。  
4. **反思模式优于简单两步思维**：直接生成两个 `<think>` 步骤的 GRPO 无明显提升（表 4）。  
5. **反思增强可泛化至不同 RL 算法**：将反思融入 PPO 和 DAPO 同样带来性能提升（图 5）。  
6. **反思提高了推理深度**：训练动态显示 SRPO 产生更长但更有效的反思，且策略更新更稳定。  
7. **跨学科泛化能力强**：在物理、化学、生物任务上超越专注单一领域的推理模型。

## 7. 优点

- **方法创新性**：首次系统地将明确的自反思机制融入 MLLM 的 SFT 和 RL 两个阶段，并设计了专门的奖励函数。  
- **数据构造精细**：采用质量筛选（“Less is More”），并同时包含对正确和错误答案的反思，使得模型既能纠正错误也能优化正确推理。  
- **奖励设计全面**：同时考虑格式、长度、有效性，并通过指数长度函数避免硬约束，具有良好的可导性。  
- **实验覆盖全面**：涵盖数学、通用、跨学科推理，对比大量先进基线，消融实验深入。  
- **开源友好**：基于公开数据和模型（Qwen-2.5-VL）构建，并详细公开了超参数和 prompt 模板，便于复现。  
- **训练稳定性**：通过反思 SFT 冷启动，RL 训练收敛更快，策略更新更平滑（较低的 clip upper ratio）。

## 8. 不足与局限

- **模型规模范围有限**：仅在 7B 和 32B 的密集 MLLM 上测试，未在更大规模（72B+）或 MoE/扩散模型上验证。  
- **数据规模有限**：RL 训练仅使用了 37K 公开数据，未探索更大规模或商业数据集；SFT 仅 10K 样本。  
- **缺乏统计显著性报告**：所有 RL 实验仅运行一次固定随机种子，未报告多次重复的均值和标准差，可能影响结论的稳健性。  
- **计算开销**：反思生成需要额外推理步骤，导致响应更长，推理延迟增加（表 10 显示从 GRPO 的 45.6 分钟增加到 60.5 分钟）。  
- **反思质量依赖强教师**：第一阶段反思生成依赖 GPT-o4-mini 等大型模型，可能引入教师偏差；人工评估显示仍有约 20-30% 的反思效果有限或冗余。  
- **未涉及安全性与偏见分析**：论文在附录中提及偏见风险，但未做系统性评估或缓解措施。  
- **通用性待验证**：目前主要聚焦于数学和科学推理，对语义理解、视觉定位等非推理任务的有效性未探讨。

（完）
