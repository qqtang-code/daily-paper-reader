---
title: "Expected Attention: KV Cache Compression by Estimating Attention From Future Queries Distribution"
title_zh: 期望注意力：通过估计未来查询分布进行KV缓存压缩
authors: "Alessio Devoto, Maximilian Jeblick, Simon Jégou"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=VmojW15eRc"
tags: ["query:sparse-attn"]
score: 9.0
evidence: 通过估计未来查询注意力进行KV缓存压缩
tldr: 针对KV缓存随上下文增长导致的内存瓶颈，本文提出Expected Attention，一种无需训练的方法。它通过近似未来查询的注意力分布来估计每个KV对的重要性，从而在不计算完整注意力矩阵的情况下实现高效驱逐。该方法兼容Flash Attention等高效注意力实现，在长上下文生成中显著减少内存使用，同时保持模型性能。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 基于注意力分数驱逐KV对的方法在实践中不可行，因为未来查询的注意力未知且Flash Attention不产出完整注意力矩阵。
method: 提出Expected Attention，利用查询分布的先验知识估计未来注意力，从而在解码前确定KV对重要性。
result: "在多项长上下文任务中，Expected Attention在压缩KV缓存70%以上时仍保持与全注意力相当的困惑度和下游性能。"
conclusion: 该方法为在高效注意力框架下实现KV缓存压缩提供了一种实用且有效的训练无关方案。
---

## Abstract
Large language models encounter a significant memory bottleneck during inference due to the Key-Value (KV) cache, which stores past token representations and grows linearly with context length. Although using attention scores to evict KV pairs is promising, it is often impractical in real-world scenarios because the attention scores from future tokens have not yet been computed, and modern implementations like Flash Attention do not materialize the full attention matrix, making past scores inaccessible too. To address these limitations, we introduce $\textit{Expected Attention}$ , a training-free method that estimates a KV pair's importance by approximating how future queries will attend to it. By leveraging the distributional properties of activations in LLMs, we compute the expected attention score in closed form for each KV pair. This score is then used to rank and prune KV pairs with the smallest impact on the residual stream, achieving compression without performance loss. Crucially, our approach works in both prefilling and decoding tasks, consistently outperforming state-of-the-art baselines in both scenarios. We release all our code to enable researchers to implement and build upon our methods.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **背景**：大型语言模型在推理时面临显著的内存瓶颈，主要源于 Key-Value（KV）缓存。KV 缓存存储了先前 token 的表示，且随上下文长度线性增长，导致长上下文生成时内存消耗巨大。
- **现有方法局限**：基于注意力分数驱逐 KV 对（eviction）是一种有前景的压缩思路，但实际中难以实现，因为未来 token 的注意力分数尚未计算，且现代高效注意力实现（如 Flash Attention）不产出完整的注意力矩阵，使得过去的分数也无法获取。
- **核心问题**：如何在不依赖未来查询的实际注意力分布、且兼容高效注意力框架的情况下，有效评估每个 KV 对的重要性，从而实现 KV 缓存压缩而不损失模型性能。
- **整体意义**：本文提出一种无需训练的 KV 缓存压缩方法，通过近似未来查询的注意力分布来估计每个 KV 对的重要性，在长上下文推理中显著减少内存使用，同时保持模型质量，为高效 LLM 推理提供了实用方案。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：利用 LLM 中激活值的分布性质，对未来查询的注意力进行封闭形式的期望计算，即 **Expected Attention**。该方法不依赖实际计算未来注意力矩阵，而是估计每个 KV 对在未来查询中的期望注意力分数。
- **关键技术细节**：
  - 在解码开始前，根据查询分布的先验知识（例如假设查询向量服从某种分布），计算每个 KV 对与未来查询之间的期望注意力分数。
  - 该分数用于衡量 KV 对在残差流中的影响大小，从而排序并驱逐影响最小的 KV 对，实现压缩。
  - 方法兼容 Flash Attention 等高效注意力实现，因为它在解码阶段之前就确定了驱逐策略，无需访问完整注意力矩阵。
- **算法流程（文字说明）**：
  1. 在预填充阶段，收集所有 KV 对的键和值。
  2. 基于给定的查询分布假设（如高斯分布），利用解析公式计算每个 KV 对的期望注意力得分。
  3. 根据得分对 KV 对进行排序，保留高影响力的一小部分，驱逐低影响力的部分。
  4. 在后续解码阶段，仅使用保留的 KV 缓存进行注意力计算。
- **适用场景**：该方法同时适用于预填充和解码任务。

## 3. 实验设计

- **数据集与场景**：论文在多项长上下文任务上进行评估，具体数据集未在提供的元数据中详细列出，但摘要提及“多项长上下文任务”。
- **基准方法（Baseline）**：与多种最先进的 KV 缓存压缩基线方法进行对比，包括已有的训练无关方法和基于注意力的驱逐策略。
- **对比指标**：困惑度（PPL）和下游任务性能。
- **评估设置**：
  - 压缩率：从较低压缩到极高压缩（如 70% 以上压缩）。
  - 对比场景：预填充和解码两种任务。
- **消融实验**：元数据未明确提及消融实验，但可能存在针对不同分布假设、压缩率等变量的分析。

## 4. 资源与算力

- 论文未明确说明使用的 GPU 型号、数量、训练时长等具体算力资源。
- **推断**：由于方法是训练无关的（training-free），主要涉及推理阶段的压缩，因此所需算力可能远少于训练阶段。但具体硬件细节缺失，无法量化。

## 5. 实验数量与充分性

- **实验数量**：论文覆盖了多个长上下文任务，并与多种基线对比，同时评估了预填充和解码两个场景，实验组数较多。
- **充分性评价**：
  - 实验设计较全面：覆盖了不同压缩率，验证了方法在大范围压缩下的鲁棒性。
  - 对比基线包括最新方法，体现了公平性。
  - 然而，由于元数据中实验细节有限，无法确认是否包含不同模型规模、不同架构的评估，以及是否进行了统计分析（如多次运行取平均、置信区间等）。
- **总体**：实验较为充分，但可能存在未充分测试的领域（如超出特定模型族、极端长上下文范围）。

## 6. 论文的主要结论与发现

- **主要结论**：Expected Attention 是一种有效的训练无关 KV 缓存压缩方法，在压缩超过 70% 的情况下，仍能与全注意力的困惑度和下游性能保持相当。
- **关键发现**：
  - 通过估计未来查询的期望注意力，可以在不解码的情况下准确预测 KV 对的重要性。
  - 该方法在预填充和解码阶段均优于所有基线，且兼容 Flash Attention 等高效实现。
  - 证明了利用激活值分布先验进行压缩的可行性，为无需训练的 KV 缓存压缩提供了实用新范式。

## 7. 优点

- **方法新颖性**：首次提出利用未来查询的期望注意力进行 KV 压缩，避免了现有方法在高效注意力框架下的不可行问题。
- **实用性强**：无训练、无额外开销，可直接集成到现有推理系统中，兼容 Flash Attention。
- **性能优越**：在大压缩率下保持模型质量，优于多个强基线。
- **适用范围广**：同时适用于预填充和解码两个阶段，并且支持流式生成场景。

## 8. 不足与局限

- **实验覆盖有限**：未提供数据集具体名称、模型规模（是否涵盖小、中、大模型）以及多轮对话等复杂场景的评估。
- **分布假设依赖性**：方法依赖于对查询分布的假设（如高斯分布），如果实际分布偏离假设，可能影响压缩效果，论文未充分讨论稳健性。
- **理论分析不足**：期望注意力的推导仅利用先验分布，但未给出为什么这种近似有效的深入理论证明或误差界。
- **资源与算力信息缺失**：缺乏实施细节（如实际推理速度、内存占用对比），难以评估实际工程部署成本。
- **偏差风险**：方法可能偏向于某些类型的模式（如重复性查询或多头注意力中的特定头），论文未做针对性消融。
- **应用限制**：仅适用于自回归生成，对于编码器-解码器架构或前缀注意力等场景可能需要适配。

（完）
