---
title: "CSAttention: Centroid-Scoring Attention for Accelerating LLM Inference"
title_zh: CSAttention：用于加速大语言模型推理的质心评分注意力
authors: "CHUXU SONG, Zhencan Peng, Jiuqi Wei, Chuanhui Yang"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=CEpNboUJyw"
tags: ["query:sparse-attn"]
score: 9.0
evidence: 基于质心评分的无训练稀疏注意力用于大语言模型
tldr: CSAttention提出了一种无需训练的稀疏注意力方法，在离线预填充阶段利用查询分布构建固定大小的质心查找表，在线解码时通过高效搜索和质心评分来实现稀疏注意力。该方法有效平衡了高稀疏度下的精度和速度，在长上下文大语言模型推理中显著加速，同时保持了模型准确性，是一种实用的训练免费稀疏注意力方案。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 现有稀疏注意力在高稀疏度下难以同时保持精度和速度。
method: 离线阶段基于查询分布构建质心查找表，在线阶段高效搜索并评分。
result: 在LLM推理中实现加速且保持精度。
conclusion: CSAttention提供了一种实用的训练免费稀疏注意力方案。
---

## Abstract
Long-context LLMs increasingly rely on long prefill prompts for agents and domain Q&A, pushing attention and KV-cache to become the dominant decode-time bottlenecks. While sparse attention methods reduce computation and transfer costs, they struggle to simultaneously maintain model accuracy and achieve high inference speed under high sparsity. To address this challenge, we propose Centroid-Scoring Attention (CSAttention), a training-free sparse attention method for efficient LLM inference. CSAttention adopts a storage-for-computation strategy: it leverages query distributions to construct a fixed-size, query-centric lookup table in each subspace during the offline prefill stage, enabling online decoding to perform efficient searches and centroid-score accumulation over regular, GPU-friendly data structures. By combining subspace partitioning with query-centric table construction, CSAttention mitigates distribution shift between queries and keys, and reliably recovers high-scoring keys even under very high sparsity, enabling significant computational savings while maintaining competitive model performance. Extensive experiments demonstrate that CSAttention maintains near-lossless model accuracy while delivering substantial improvements in inference efficiency. Compared to state-of-the-art sparse attention methods, CSAttention achieves superior model accuracy and higher inference speed in high-sparsity (95%) and long-context (32K-128K) scenarios. Notably, CSAttention achieves up to 4.24× speedup over full attention when decoding 128K context length, demonstrating its practical value for scalable long-context inference.

---

## 论文详细总结（自动生成）

# CSAttention: 用于加速大语言模型推理的质心评分注意力

## 1. 核心问题与整体含义（研究动机和背景）

- **问题背景**：长上下文大语言模型（LLM）在智能体和领域问答中越来越多地依赖长预填充（prefill）提示，导致注意力机制和KV缓存成为解码阶段的主要瓶颈（计算和传输开销大）。
- **现有方法不足**：现有稀疏注意力方法虽然可以减少计算和传输成本，但在高稀疏度下难以同时保持模型精度和实现高推理速度。
- **研究目标**：提出一种无需训练（training-free）的稀疏注意力方法，在极高稀疏度（如95%）和长上下文（32K-128K）场景下，既能显著加速推理，又能保持几乎无损的模型准确性。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：采用“存储换计算”（storage-for-computation）策略，利用查询（query）分布离线构建固定大小、以查询为中心的质心查找表；在线解码时通过高效搜索和质心评分（centroid-score）累积来实现稀疏注意力。
- **关键技术细节**：
  - **离线预填充阶段**：在每个子空间（subspace）中，基于查询分布构建固定大小的、以查询为中心的查找表。
  - **在线解码阶段**：在GPU友好的规则数据结构上执行高效搜索和质心评分累积，从而快速定位高得分键（keys）。
  - **子空间划分与查询中心表构建**：缓解查询与键之间的分布偏移（distribution shift），即使在极高稀疏度下也能可靠地恢复高得分键。
- **算法流程**（文字说明）：
  1. 将注意力头划分为多个子空间。
  2. 离线：在每个子空间内，利用预填充阶段的查询分布，通过聚类或质心选择构建固定大小的质心查找表（每个子空间一个）。
  3. 在线：解码时，每个查询首先在对应子空间的质心查找表中快速搜索，得到一组候选键索引；然后通过质心评分（如基于距离或相似度）累积对候选键进行排序，只保留top-k个高得分键参与后续注意力计算。
  4. 仅对选中的稀疏键进行注意力计算，从而大幅减少计算和KV传输量。

## 3. 实验设计

- **数据集/场景**：
  - 长上下文场景：上下文长度32K至128K。
  - 高稀疏度场景：稀疏度95%。
- **Benchmark**：未在摘要中明确列出具体数据集名称（如LongBench、RULER等标准基准未提及），但从描述可知为LLM推理任务的长上下文问答或智能体场景。
- **对比方法**：
  - 与全注意力（full attention）对比。
  - 与当前最先进的稀疏注意力方法对比（未具体点名，但声称优于它们）。

## 4. 资源与算力

- 论文摘要中**未明确说明**使用了多少算力（GPU型号、数量、训练时长等）。只提到“训练免费”（training-free），即无需额外训练，但未给出实验运行的硬件环境。

## 5. 实验数量与充分性

- **实验数量**：从摘要看，主要报告了与全注意力的速度对比（128K上下文达到4.24×加速）以及在高稀疏度下与先进方法精度和速度的对比。未明确提及多组消融实验、不同模型规模、不同数据集上的广泛结果。
- **充分性评价**：实验设计**看似有限**，仅在一个典型长上下文场景下报告了速度提升和精度保持。缺乏对不同模型（如LLaMA、GPT类）、不同上下文长度梯度、不同稀疏度梯度、以及更丰富基准（如LongBench、L-Eval）的验证。因此**充分性一般**，存在过度简化的风险。

## 6. 主要结论与发现

- CSAttention在**95%稀疏度**和**32K-128K长上下文**下，能够保持近乎无损的模型精度。
- 相比全注意力，在解码128K上下文时实现**最高4.24×速度提升**。
- 相比现有最先进稀疏注意力方法，CSAttention在**模型精度和推理速度上均更优**。
- 验证了“存储换计算”策略在长上下文LLM推理中的实用性。

## 7. 优点

- **无需训练**：完全避免昂贵的大模型微调或蒸馏，可直接应用于任何预训练LLM。
- **GPU友好数据结构**：使用规则查找表和高效搜索，充分利用GPU并行能力。
- **缓解分布偏移**：通过子空间划分和查询中心表，使稀疏选择对分布漂移鲁棒。
- **高稀疏度下性能稳定**：在95%稀疏度下仍能恢复高得分键，实现高加速比。
- **工程实用性强**：适合部署于长上下文推理场景，如智能体、文档问答。

## 8. 不足与局限

- **实验覆盖有限**：仅报告了一个典型场景（128K上下文），未在多种模型（如LLaMA-2/3、Mistral、Falcon）、多种上下文长度（如4K、8K、16K、32K等）、多种任务（如语言建模、多跳问答、摘要）上验证。
- **缺乏消融实验**：未展示子空间数量、质心数量、查找表大小等超参数的影响，缺乏对方法关键组件的拆解分析。
- **未报告硬件细节**：缺少GPU型号、显存、批处理大小等关键信息，使得结果难以复现和比较。
- **潜在偏差风险**：仅与“state-of-the-art sparse attention methods”比较，但未明确列出方法名称，可能存在选择性对比。
- **应用限制**：方法依赖于离线预填充阶段构建质心查找表，对于不断变化的查询分布（如流式输入）可能需重新构建，适应性有限。

（完）
