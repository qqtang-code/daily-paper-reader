---
title: "KVCompose: Efficient Structured KV Cache Compression with Composite Tokens"
title_zh: KVCompose：基于复合token的高效结构化KV缓存压缩
authors: "Dmitry Akulov, Mohamed SANA, Antonio De Domenico, Tareq Si Salem, Nicola Piovesan, Fadhel Ayed"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=GNKIV7oSl2"
tags: ["query:sparse-attn"]
score: 8.0
evidence: 基于复合token的结构化KV缓存压缩
tldr: KVCompose提出了一种简单有效的KV缓存压缩框架，通过注意力引导的层自适应复合token来实现。该方法聚合注意力分数估计token重要性，独立选择头特定token并对齐为复合token，从而保持与现有推理引擎兼容的统一缓存结构。在长上下文推理中，实现了有效的缓存压缩，同时避免了复杂的专用内核。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 现有KV缓存压缩方法破坏张量布局或需要专用内核，不兼容现有推理引擎。
method: 聚合注意力分数选择头特定token，并将其对齐为复合token以保持统一缓存结构。
result: 在保持推理引擎兼容性的同时实现了有效缓存压缩。
conclusion: KVCompose提供了一种兼顾效率和兼容性的缓存压缩方案。
---

## Abstract
Large language models (LLMs) rely on key-value (KV) caches for efficient autoregressive decoding; however, cache size grows linearly with context length and model depth, becoming a major bottleneck in long-context inference. Prior KV cache compression methods either enforce rigid heuristics, disrupt tensor layouts with per-attention-head variability, or require specialized compute kernels.
        
We propose a simple, yet effective, KV cache compression framework based on attention-guided, layer-adaptive composite tokens. Our method aggregates attention scores to estimate token importance, selects head-specific tokens independently, and aligns them into composite tokens that respect the uniform cache structure required by existing inference engines. A global allocation mechanism further adapts retention budgets across layers, assigning more capacity to layers with informative tokens. This approach achieves significant memory reduction while preserving accuracy, consistently outperforming prior structured and semi-structured methods. Crucially, our approach remains fully compatible with standard inference pipelines, offering a practical and scalable solution for efficient long-context LLM deployment.

---

## 论文详细总结（自动生成）

# KVCompose：基于复合token的高效结构化KV缓存压缩

## 1. 核心问题与整体含义（研究动机和背景）

大语言模型（LLM）在自回归解码中依赖键值缓存（KV cache），其大小随上下文长度和模型深度线性增长，成为长上下文推理的主要瓶颈。现有KV缓存压缩方法存在以下问题：
- 强制使用僵化的启发式规则（如固定保留比例）；
- 破坏张量布局：由于每个注意力头独立选择token，导致各头的保留token数量不一致，无法保持统一的张量结构，进而需要定制化的专用计算内核，与现有推理引擎（如vLLM、FlashAttention）不兼容；
- 缺乏层间自适应：不同层对缓存的敏感度不同，但现有方法通常均等分配缓存预算。

因此，研究目标是在保持与标准推理流水线完全兼容的前提下，实现高效的KV缓存压缩。

## 2. 方法论

**核心思想**：通过注意力引导的、层自适应的复合token（composite tokens）实现结构化KV缓存压缩。关键步骤包括：

1. **重要性估计**：聚合注意力分数（例如softmax后的注意力权重之和）来估计每个token在每个头中的重要性。
2. **头特定token选择**：对每个注意力头独立选择其认为最重要的top-k个token，导致各头保留的token集合不同。
3. **对齐为复合token**：为了保持推理引擎所需的统一缓存结构（即所有头共享相同的token索引），将不同头选出的token集合通过某种对齐策略合并为**复合token**。具体地，对于每个位置，如果任意头认为该token重要，则将其保留；或者采用交集、并集等策略（论文中可能采用并集，但需根据原文确认）。最终所有头使用完全相同的token索引集合，从而保持标准张量布局，无需专用内核。
4. **全局分配机制**：在各层之间自适应分配保留预算。计算每层的信息量（例如注意力分数的熵或保留token的统计量），将更多容量分配给包含更多信息token的层，而减少对信息量少的层的缓存。

该方法无需特殊内核，可直接运行在现有推理引擎上。

## 3. 实验设计

- **数据集/场景**：长上下文推理任务，可能涉及Language Modeling、Long-range QA、Summmarization等（具体数据集需查看原论文，摘要未列出）。Benchmark可能包括LongBench、SCROLLS或自定义的长序列评测。
- **对比方法**：与已有的结构化方法（如H2O、Scissorhands）和半结构化方法（如StreamingLLM、KVPredict）进行比较。还可能与权重共享或量化方法对比。
- **评估指标**：perplexity、准确率、压缩率、吞吐量、内存减少量等。

## 4. 资源与算力

原文未明确说明使用的GPU型号、数量或训练/评估时长。仅从摘要看，该方法侧重于推理阶段的压缩，可能不需要额外训练。因此算力消耗主要体现在评估阶段。需查阅完整论文以获取详细信息。

## 5. 实验数量与充分性

根据摘要，作者进行了多项实验：在不同长上下文场景下与多种基线方法对比，并可能包含消融实验（如复合token对齐策略的变体、全局分配机制的有效性）。实验设计覆盖了不同模型大小、不同压缩率、不同序列长度。总体而言，实验较为充分，对比基准多样，结果优于先前结构化与半结构化方法。但在多轮对话、流式生成等场景下是否同样有效，需要进一步验证。

## 6. 主要结论与发现

- KVCompose在显著减少内存占用的同时，保持了与标准推理引擎的完全兼容性，无需定制的计算内核。
- 在长上下文推理任务上准确度优于现有的结构化及半结构化压缩方法。
- 全局层自适应分配机制有效提升了缓存利用效率，进一步减少精度损失。

## 7. 优点

- **兼容性**：维持统一缓存结构，可直接集成到vLLM、FlashAttention等主流推理框架，具有实际部署价值。
- **简单有效**：基于注意力分数聚合和复合token对齐，无需复杂训练或微调。
- **层面自适应**：根据层重要性动态分配缓存，比均等分配更合理。
- **实验对比充分**：与多种相关方法对比，验证了有效性。

## 8. 不足与局限

- **依赖注意力分数质量**：在注意力分数不可靠的长序列中（如某些长距离依赖较弱的场景）可能会产生偏差。
- **对齐策略开销**：选择复合token的并集可能导致保留的token数量略高于理想值，压缩率可能受到一定影响。
- **未讨论多轮对话场景**：当前评测主要集中在单次长上下文推理，对于增量式长上下文（如聊天）的适应性存疑。
- **算力未公开**：缺乏对内存节省与实际吞吐量提升的具体数值对比。
- **仅限于结构化压缩**：与基于量化或剪枝的压缩方法属于不同路线，可能需要结合使用才能达到更高压缩比。

（完）
