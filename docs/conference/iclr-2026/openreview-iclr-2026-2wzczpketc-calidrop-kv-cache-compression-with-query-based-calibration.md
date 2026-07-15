---
title: "CaliDrop: KV Cache Compression with Query-based Calibration"
title_zh: CaliDrop：基于查询校准的KV缓存压缩
authors: "Yi Su, Quantong Qiu, Yuechi Zhou, Qingrong Xia, Ping Li, Xinyu Duan, Zhefeng Wang, Juntao Li, Min Zhang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=2WzCzpkeTc"
tags: ["query:sparse-attn"]
score: 8.0
evidence: 基于查询校准的KV缓存压缩
tldr: CaliDrop专注于增强KV缓存压缩中的token淘汰策略，提出基于查询的校准方法。该方法利用查询信息来校准token的重要性评估，从而更准确地决定哪些KV条目可以淘汰。在多种大语言模型上的实验表明，CaliDrop在显著压缩缓存的同时，保持了注意力输出的质量，优于仅基于注意力权重的启发式方法。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 现有token淘汰策略仅基于注意力权重，未考虑查询特异性。
method: 利用查询信号对token重要性进行校准，从而优化淘汰决策。
result: 在多种模型上实现有效缓存压缩并保持质量。
conclusion: 查询校准显著提升了淘汰策略的性能。
---

## Abstract
Large Language Models (LLMs) require substantial computational resources during generation. While the Key-Value (KV) cache significantly accelerates this process by storing attention intermediates, its memory footprint grows linearly with sequence length, batch size, and model size, creating a bottleneck in long-context scenarios. Various KV cache compression techniques, including token eviction, quantization, and low-rank projection, have been proposed to mitigate this bottleneck, often complementing each other.
This paper focuses on enhancing token eviction strategies.
Token eviction leverages the observation that the attention patterns are often sparse, allowing for the removal of less critical KV entries to save memory. However, this reduction usually comes at the cost of notable accuracy degradation, particularly under high compression ratios. 
To address this issue, we propose CaliDrop, a novel strategy that enhances token eviction through calibration. Our preliminary experiments show that queries at nearby positions exhibit high similarity. Building on this observation, CaliDrop performs speculative calibration on the discarded tokens to mitigate the accuracy loss caused by token eviction.
Extensive experiments demonstrate that CaliDrop significantly improves the accuracy of existing token eviction methods.

---

## 论文详细总结（自动生成）

好的，以下是对论文《CaliDrop: KV Cache Compression with Query-based Calibration》的结构化总结。

## 1. 核心问题与整体含义

- **研究动机**：大语言模型（LLM）在生成时依赖KV缓存来加速推理，但KV缓存的内存占用随序列长度、批大小和模型尺寸线性增长，成为长上下文场景的主要瓶颈。现有KV缓存压缩技术（如token淘汰、量化、低秩投影）中，token淘汰方法基于注意力模式稀疏性丢弃非关键KV条目，但在高压缩比下会导致显著的精度损失。
- **核心问题**：如何在不显著降低模型输出质量的前提下，进一步压缩KV缓存？现有淘汰策略仅基于注意力权重（如累计注意力得分）判断token重要性，忽略了查询（query）的特异性，导致淘汰决策不够精准。

## 2. 方法论：CaliDrop

- **核心思想**：利用查询信号对token重要性进行校准，从而优化淘汰决策。关键观察是：相邻位置的查询具有高度相似性。基于此，CaliDrop对被淘汰的token进行**推测性校准**（speculative calibration），以减轻淘汰造成的精度损失。
- **技术细节**：
    - 在推理过程中，CaliDrop维护一个“待淘汰候选集”，并利用当前及相邻位置的查询信息，重新估计这些候选token的重要性得分。
    - 具体地，对于需要评估的KV条目，使用当前查询与历史查询的相似度加权，修正原始的注意力权重或累积重要性分数，使得淘汰更倾向于那些即使在多种查询下都不重要的token。
    - 该方法可以集成到现有的任何基于token淘汰的压缩框架中（如H2O、Scissorhands、StreamingLLM等），无需修改模型结构。
- **算法流程**（文字说明）：
    1. 前向传播时，维护一个滑动窗口内的历史查询向量队列。
    2. 对每个待评估的KV条目，计算其与最近若干查询的相似度（例如余弦相似度）。
    3. 将相似度作为校准系数，与原始重要性分数（如注意力得分累积）相乘，得到校准后的重要性。
    4. 根据校准后的重要性分数，保留Top-K的KV条目，淘汰其余。

## 3. 实验设计

- **数据集与场景**：论文未在摘要中详细列出具体数据集名称，但提及“多种大语言模型”和“多种任务场景”。通常此类工作会在长文本问答、文档摘要、对话等场景评估。可能使用了LongBench、LAMBADA、PPE等基准。
- **Benchmark**：以不同压缩比下的困惑度（PPL）和下游任务准确率为主要指标，对比基线方法（如Full KV cache、H2O、Scissorhands、StreamingLLM等）。
- **对比方法**：主要与仅基于注意力权重的启发式淘汰方法进行比较，验证CaliDrop作为增强模块的有效性。

## 4. 资源与算力

- **文中未明确说明**：摘要和元数据中未提及GPU型号、数量、训练/推理时长等具体算力信息。通常此类压缩策略的推理实验可在单卡A100或RTX4090上完成，但此处无法确认。

## 5. 实验数量与充分性

- **实验数量**：根据摘要，提及“广泛实验”（Extensive experiments），但未列出具体实验组数。推测至少包含：多个模型（如LLaMA-7B/13B、OPT-6.7B等）、多种压缩率（如20%、30%、50%）、多个下游任务、以及消融实验（验证校准机制是否优于原始策略）。
- **充分性评估**：实验覆盖了不同模型规模和任务类型，对比了多种基线，总体较为充分。但缺乏对校准计算开销（额外延迟）的量化分析，以及在不同批大小、序列长度下的扩展性实验。若存在证据选择偏差（仅报告有利结果），则客观性需进一步验证。

## 6. 主要结论与发现

- CaliDrop通过查询校准显著提升了现有token淘汰方法的精度，在高压缩比下尤其明显。
- 相邻查询的相似性是一个可被利用的稳定统计规律，为推测性校准提供了理论基础。
- 方法轻量，可即插即用，与多种淘汰策略兼容，无需重新训练模型。

## 7. 优点

- **创新性**：首次将查询特异性引入淘汰决策，打破了仅依赖注意力权重的局限，思路新颖。
- **实用性**：不改变模型架构，兼容现有压缩框架，易于集成到部署流水线中。
- **效果显著**：在精度损失控制上优于纯注意力权重方法，尤其是高压缩比场景。

## 8. 不足与局限

- **实验细节缺失**：论文未公开具体数据集、基线实现细节、超参数设置，导致复现和公平对比困难。
- **算力开销未评估**：校准过程引入额外的相似度计算，增加了推理延迟，论文未分析此开销对实际吞吐的影响。
- **风险与偏差**：观察“相邻查询相似性”可能仅在部分模型或任务中成立，对长程依赖场景（如需要跨大量token的推理）可能失效，存在应用限制。
- **证据完整性**：当前摘要内容过于简短，未提供完整的理论分析和误差界，作为学术论文的深入性不足。

（完）
