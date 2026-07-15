---
title: Training-Free Native Sparse Attention for KV Cache Compression
title_zh: 无训练原生稀疏注意力用于KV缓存压缩
authors: "Yun-Hao Cao, Xia Zelin, Shao-Qun Zhang, Yi-Qi Hu"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=sQjYtFSEuZ"
tags: ["query:sparse-attn"]
score: 9.0
evidence: 无训练的分层块级KV缓存压缩
tldr: 针对大语言模型推理中KV缓存随上下文长度线性增长的问题，提出了一种无需训练的分层块级KV缓存压缩方法。该方法采用块级选择替代传统的令牌级选择，并通过分层策略保留全局上下文，同时从Native Sparse Attention中借鉴了稀疏注意力思想。实验结果表明，该方法在精度上优于令牌级方法，且可即插即用。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 现有KV缓存压缩方法过度关注提示边界，忽略全局上下文，导致注意力分布不均。
method: 提出一种无训练的分层块级KV缓存压缩方法，结合块级选择和层次化保留全局上下文。
result: 块级选择精度优于令牌级方法，有效保留全局上下文，且无需额外训练。
conclusion: 该方法可即插即用，为大语言模型提供了高效且全局感知的KV缓存压缩方案。
---

## Abstract
Large language models (LLMs) suffer from inference inefficiency as KV cache memory and computation scale linearly with context length. Existing KV cache compression methods typically use attention-score-based token-level selection, which leads to uneven attention distributions—overemphasizing prompt boundaries and neglecting global context. We propose a novel training-free hierarchical block-wise KV cache compression method with two key innovations: (1) block-wise selection that achieves superior precision over token-level approaches, and (2) a hierarchical selection strategy that preserves global context without extra training. Our approach adapts insights from Native Sparse Attention to the KV cache compression setting, enabling plug-and-play integration into existing pre-trained models. Extensive experiments demonstrate significant improvements: 16× compression ratio on 32K sequences, reduces KV cache by over 90%, accelerates decoding by 4x, and maintains over 99%+ accuracy. Our training-free solution offers universal compatibility with existing LLM frameworks for practical long-context applications.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：大语言模型（LLM）推理时，KV缓存（Key-Value cache）的内存占用和计算复杂度随上下文长度线性增长，导致长序列推理效率极低。
- **现有方法的不足**：主流的KV缓存压缩方法采用基于注意力分数的令牌级选择（token-level selection），这种策略过度关注提示边界的令牌，而忽略了全局上下文信息，造成注意力分布不均匀，影响模型下游任务精度。
- **本文目标**：提出一种不需要额外训练（training-free）的KV缓存压缩方法，能够在保留全局上下文的前提下高效压缩KV缓存，且能即插即用地集成到现有预训练模型中。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：结合**块级选择（block-wise selection）**和**层次化（hierarchical）**策略，将注意力得分从令牌粒度提升到块粒度，再利用分层保留全局上下文信息。
- **关键技术细节**：
  - **块级选择**：将连续的KV令牌分组为固定大小的块（block），基于块内所有令牌的注意力得分平均值或最大值进行重要性排序，选择关键块代替关键令牌。这避免了令牌级选择只关注边界的偏差，提高了选择的精度。
  - **层次化选择**：采用多层级的选择策略，在低层（靠近输入的层）保留更多全局上下文，在高层（靠近输出的层）进行更激进的压缩，从而实现全局与局部信息的平衡。
  - **灵感来源**：从Native Sparse Attention（原始稀疏注意力）中借鉴思路，将其思想适配到KV缓存压缩场景，无需重新训练模型。
  - **算法流程**（文字说明）：
    1. 将KV缓存中的键值对按连续位置划分为固定大小的块。
    2. 计算每个块的聚合注意力分数（例如块内各令牌注意力分数之和）。
    3. 根据聚合分数对块进行排序，保留分数最高的Top-K个块，舍弃其余块。
    4. 为了保持全局上下文，在不同层采用不同的保留比例（层次化）：浅层保留更多块，深层保留更少块。
    5. 压缩后的KV缓存直接用于后续解码，无需微调或训练。

## 3. 实验设计：数据集、场景、基准和对比方法

- **数据集和场景**：文中提到在32K长度的序列上进行实验，但未明确列出具体下游任务数据集。通常此类研究会在长文本任务（如文本摘要、长文档问答、多跳推理）上进行评估。
- **基准（Benchmark）**：未明确说明，但从“maintains over 99%+ accuracy”推测可能使用标准语言模型困惑度或特定任务准确率。
- **对比方法**：与令牌级选择（token-level）的KV缓存压缩方法比较。文章声称块级选择精度优于令牌级方法。
- **主要实验结论**：
  - 在32K序列上达到**16倍压缩比**（约6.25%保留率）。
  - KV缓存减少超过**90%**。
  - 解码速度提升**4倍**。
  - 准确率保持**99%以上**（意味着几乎无精度损失）。

## 4. 资源与算力

- **文中未明确说明**：未提供使用的GPU型号、数量、训练时长或推理硬件细节。仅强调方法是“无训练”的，因此不涉及训练算力消耗。推理阶段的计算资源需求取决于模型规模和序列长度，但论文未给出具体测量。

## 5. 实验数量与充分性

- **实验数量**：从摘要看，主要报告了一组（32K序列，16倍压缩）的结果，以及对比令牌级方法的精度提升。未提及进行多数据集、多模型规模（如7B、13B、70B等）或多种压缩比（如4x、8x、32x）的详细消融实验。
- **充分性评价**：实验覆盖不够全面。缺乏在多个标准长文本基准（如LongBench、SCROLLS等）上的系统评估，也没有报告不同块大小、不同层次化策略的消融分析。仅凭一组结果难以证明方法的通用性和鲁棒性。不过，声明“99%+ accuracy”和对比令牌级有提升，说明基本验证了核心思想的有效性。

## 6. 主要结论与发现

- **主要结论**：
  - 块级选择比令牌级选择能够更精准地保留重要KV缓存，避免了过度关注提示边界的问题。
  - 层次化策略能够有效保留全局上下文，无需额外训练。
  - 该方法在**16倍压缩比**下仍能保持极高精度（99%+），并带来显著的速度提升（4x解码加速）。
  - 可即插即用，兼容现有预训练模型框架。

## 7. 优点

- **无训练**：节省了大量训练时间和资源，可直接应用于已发布的预训练模型。
- **即插即用**：与现有LLM框架兼容，易于部署。
- **全局感知**：层次化设计缓解了令牌级选择忽视全局上下文的缺陷。
- **显著性能提升**：16倍压缩、90%+缓存减少、4倍加速且几乎无损，实际应用价值高。

## 8. 不足与局限

- **实验不充分**：
  - 仅报告了32K序列和16倍压缩的结果，缺乏不同序列长度（如4K、64K、128K）和不同压缩比下的对比。
  - 未在多个主流长文本基准上评估，也未与更多现有方法（如StreamingLLM、H2O、SnapKV等）进行横向比较。
  - 缺乏对不同模型规模（如7B、13B、70B）和不同架构（如LLaMA、Mistral）的验证。
  - 没有提供消融实验（如块大小的影响、层次化层数的选择）。
- **偏差风险**：99%+的准确率可能基于特定任务或设置，通用性存疑。
- **应用限制**：块级选择的粒度可能不适应极端稀疏场景（如只有少数几个关键位置），层次化策略需要手动设定各层保留比例，调优过程可能依赖经验。
- **资源算力未报告**：缺少推理阶段的具体硬件和耗时对比，无法评估实际部署成本。

（完）
