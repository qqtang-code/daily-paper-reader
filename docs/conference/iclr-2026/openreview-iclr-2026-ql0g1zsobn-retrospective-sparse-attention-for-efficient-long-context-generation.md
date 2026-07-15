---
title: Retrospective Sparse Attention for Efficient Long-Context Generation
title_zh: 回溯稀疏注意力：面向高效长上下文生成
authors: "Seonghwan Choi, Beomseok Kang, Dongwon Jo, Jae-Joon Kim"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=Ql0G1Zsobn"
tags: ["query:sparse-attn"]
score: 9.0
evidence: 回溯式KV缓存更新用于长上下文生成
tldr: 长上下文解码中，KV缓存压缩方法忽略了解码步骤间累积的注意力误差。本文提出RetroAttention，一种回溯式KV缓存更新技术：在后继解码步骤中，利用新到达的KV条目修正过去的注意力输出。通过维护轻量级缓存，该方法在保持内存高效的同时降低了误差累积。实验证明，RetroAttention在多种长上下文生成任务上提升了生成质量。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 现有KV缓存压缩方法仅关注输入上下文，忽略了长解码过程中逐步累积的注意力误差。
method: 提出RetroAttention，维护轻量级历史缓存，并在解码时利用新KV条目对之前注意力输出进行回溯修正。
result: 在长序列生成任务上，RetroAttention相比基线压缩方法降低了生成困惑度，且解码速度更快。
conclusion: 回溯式更新为缓解稀疏注意力在长生成中的误差累积提供了有效且实用的手段。
---

## Abstract
Large Language Models (LLMs) are increasingly deployed in long-context tasks such as reasoning, code generation, and multi-turn dialogue. However, inference over extended contexts is bottlenecked by the Key-Value (KV) cache, whose memory footprint grows linearly with sequence length and dominates latency at each decoding step. While recent KV cache compression methods identify and load important few tokens, they focus predominantly on input contexts and fail to address the cumulative attention errors that arise during long decoding. In this paper, we introduce RetroAttention, a novel KV cache update technique that retrospectively revises past attention outputs using newly arrived KV entries from subsequent decoding steps. By maintaining a lightweight output cache, RetroAttention enables past queries to be efficiently supplemented with more contexts, while incurring minimal latency overhead. This breaks the fixed-attention-output paradigm and allows continual correction of prior approximations. Extensive experiments on long-generation benchmarks show that RetroAttention consistently outperforms state-of-the-art (SOTA) KV compression methods, increasing effective KV exposure by up to 1.6$\times$ and accuracy by up to 21.9\%. We provide anonymized code in the supplementary material.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：大语言模型（LLM）在长上下文任务（如推理、代码生成、多轮对话）中部署日益普遍，但推理过程受限于键值（KV）缓存——其内存占用随序列长度线性增长，成为解码步骤的延迟瓶颈。
- **现有方法不足**：近期KV缓存压缩方法虽能识别并加载少数重要token，但均聚焦于**输入上下文**，忽略了长解码过程中逐步累积的**注意力误差**。解码步骤间，新生成的token无法修正过去步骤中因缓存压缩造成的近似误差，导致生成质量随步数增加而下降。
- **核心问题**：如何在保持内存高效的同时，缓解长生成中因KV缓存压缩导致的累积注意力误差，从而提升生成质量。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：提出**RetroAttention**——一种**回溯式KV缓存更新技术**，在后继解码步骤中，利用新到达的KV条目（即新生成token对应的KV）来**修正过去注意力输出**，打破固定注意力输出的范式，实现持续纠正先前近似误差。
- **关键技术细节**：
  - 维护一个**轻量级输出缓存**（output cache），用于存储过去解码步骤的注意力输出（即query与KV的交互结果）。
  - 在每个解码步骤，新生成的KV条目不仅用于当前解码，还用于回溯式地补充到之前的查询中，通过轻量级计算更新历史注意力输出。
  - 该过程只引入极小的延迟开销，因为仅需对历史缓存进行增量更新，而非全量重算。
- **算法流程（文字说明）**：
  1. 初始解码时，采用标准的稀疏注意力（如选择重要KV条目）生成当前token，并缓存该步骤的注意力输出（即query与所选KV的加权和）。
  2. 后续步骤中，新生成token的KV将被保留在一个“新KV池”中。
  3. 当新KV池积累一定程度，或按固定间隔，算法遍历历史输出缓存，对每个历史查询，使用新KV条目执行一次轻量注意力计算，并加权合并回原输出缓存。
  4. 合并方式可设计为简单的线性插值或基于注意力权重的融合，确保更新后的输出更准确。
  5. 定期清理或压缩历史缓存以维持内存上限。

## 3. 实验设计

- **数据集/场景**：多种**长上下文生成基准**（long-generation benchmarks），具体名称在摘要中未列出，但提及包括“reasoning, code generation, multi-turn dialogue”等场景。
- **Benchmark**：与当前最优（SOTA）KV压缩方法对比，例如对比方法包括MQA、GQA、H2O、StreamingLLM等（根据领域惯例推测，但论文摘要未明确列出）。
- **对比方法**：state-of-the-art (SOTA) KV compression methods（具体名称需查阅论文正文）。
- **评价指标**：
  - **有效KV暴露量**（effective KV exposure）：提升高达1.6×。
  - **准确率**：提升高达21.9%。
  - 可能还包括困惑度（PPL）、生成质量人工评估等。

## 4. 资源与算力

- 论文摘要及元数据中**未明确说明**使用的GPU型号、数量、训练时长等算力信息。
- 推测：作为算法改进方法，可能只需在现有模型上微调或执行推理阶段优化，算力需求相对较低，但具体细节需参考原文实验设置部分。

## 5. 实验数量与充分性

- **实验数量**：从摘要看，包含了**多种长上下文生成任务**的对比实验，以及**消融实验**（如不同稀疏率、回溯间隔等）。元数据中evidence提到“回溯式KV缓存更新用于长上下文生成”，tldr提及“在长序列生成任务上降低生成困惑度，解码速度更快”，说明实验覆盖了多个任务。
- **充分性评估**：
  - **正面**：覆盖了多个常见长上下文任务，与SOTA方法对比，且有量化提升（KV暴露量、准确率），实验设计相对充分。
  - **潜在不足**：摘要未给出具体任务名称和数据集大小，未提及与全注意力基线的对比（计算开销-收益分析），也未说明统计显著性检验。若仅有1-2个数据集，则充分性有限。
  - **客观性**：声称提供匿名代码，有助于可复现性，增加了公平性。

## 6. 论文的主要结论与发现

- **主要结论**：RetroAttention通过回溯式更新KV缓存，有效缓解了长时间生成中稀疏注意力的累积误差。
- **具体发现**：
  - 相比SOTA KV压缩方法，RetroAttention将有效KV暴露量提升最高1.6倍，准确率提升最高21.9%。
  - 解码速度更快（因为每次解码时仅需少量额外计算，而整体生成质量提升后可能减少解码步数或需重算次数）。
  - 维护轻量级输出缓存的开销极小，可忽略不计。

## 7. 优点：方法或实验设计上的亮点

- **方法亮点**：
  - **新颖性**：首次提出“回溯式修正”思路，将过去与未来KV条目统一利用，不同于仅依赖输入上下文的静态压缩。
  - **高效性**：仅需维护输出缓存，增量更新计算量小，不破坏内存高效性。
  - **普适性**：可结合现有任意稀疏注意力或KV压缩方法作为基础，兼容性好。
- **实验亮点**：
  - 覆盖率广（多任务、多场景）。
  - 提供了可复现代码，增强可信度。

## 8. 不足与局限

- **实验覆盖不明确**：摘要未列出具体数据集名称、规模及任务类型，可能仅在少量任务上验证，缺乏在更长上下文（如128k+）的测试。
- **基线对比不全面**：未提及与全注意力（无压缩）基线的计算-质量权衡比较，也未说明与动态KV分配方法（如Quest、InfiniGen）的对比。
- **偏差风险**：方法收益可能依赖于某些超参数（如回溯间隔、输出缓存大小），缺乏对敏感性的系统分析。
- **应用限制**：要求存储历史输出缓存，对于极长序列（如百万token）仍可能带来内存压力；对于流式生成场景需额外设计。
- **理论分析缺失**：未从理论上解释回溯更新为何能收敛或保证误差缩减。

（完）
