---
title: "SparseCache: Extreme Sparse Coding for KV Cache Compression"
title_zh: SparseCache：基于极端稀疏编码的KV缓存压缩
authors: "Doohyun Cho, Myounghoon Cho, Donghoon Han, Sohyeon Kim, Ji-Hoon Kim, SeungJae Lee"
date: 2025-09-08
pdf: "https://openreview.net/pdf?id=43zTdoRqY4"
tags: ["query:sparse-attn"]
score: 9.0
evidence: KV缓存压缩与稀疏编码方法
tldr: 针对LLM推理中KV缓存内存瓶颈问题，SparseCache受K-SVD算法启发，提出端到端学习框架创建全局共享字典进行稀疏编码压缩。实验表明该方法能大幅降低存储需求，而性能损失极小。这为预计算RAG等场景提供了可行的KV缓存压缩方案。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: LLM推理时KV缓存内存消耗巨大，现有预计算RAG方法存储需求过高。
method: 采用K-SVD交替优化思想，学习全局共享字典对Key和Value向量进行稀疏编码。
result: 在多个LLM上显著降低KV缓存内存占用，同时保持生成质量。
conclusion: 所提稀疏编码框架有效解决了KV缓存压缩难题，为实际部署提供了轻量级方案。
---

## Abstract
The growing memory footprint of the Key-Value (KV) cache is a critical bottleneck in Large Language Models (LLMs), significantly hindering inference efficiency. While emerging "precomputed RAG" paradigms promise to reduce latency by precomputing KV caches for entire corpora, their prohibitive storage requirements render them impractical. This paper introduces SparseCache, a novel KV Cache compression framework that addresses this bottleneck. SparseCache employs an end-to-end learning framework, inspired by the K-SVD algorithm's alternating optimization, to create separate globally shared dictionaries for Key and Value vectors across the model. By optimizing these dictionaries directly against a reconstruction loss objective, SparseCache captures fundamental KV Cache redundancies more holistically than prior per-layer methods. Extensive experiments show that SparseCache achieves a state-of-the-art compression ratio of up to 17.7x while preserving model accuracy on challenging long-context benchmarks. Notably, it maintains high performance at over 8x compression, a level where competing techniques struggle. By enabling high-fidelity compression, SparseCache makes the "precomputed RAG" paradigm practical and feasible, leading to reduced Time-To-First-Token (TTFT) and improved overall system throughput.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：大语言模型（LLM）推理时，Key-Value（KV）缓存的内存占用成为关键瓶颈，严重制约推理效率。新兴的“预计算RAG”范式虽然可以通过预计算整个语料库的KV缓存来降低延迟，但其巨大的存储需求使该方法不切实际。
- **研究动机**：需要一种高效的KV缓存压缩方法，既能大幅减少存储占用，又能保持模型精度，从而使“预计算RAG”变得可行，降低首token延迟（TTFT）并提升系统吞吐量。

## 2. 方法论：核心思想、关键技术细节与算法流程

- **核心思想**：受K-SVD算法的交替优化思想启发，提出端到端学习框架，为模型中的Key向量和Value向量分别创建全局共享字典，通过稀疏编码实现高效压缩。
- **关键技术细节**：
  - 全局共享字典：不同于逐层方法，SparseCache为所有层学习统一的Key字典和Value字典，更全面地捕捉KV缓存中的冗余。
  - 交替优化：借鉴K-SVD的字典学习过程，交替更新字典和稀疏系数，直接针对重建损失（reconstruction loss）进行优化。
  - 稀疏编码：将原始KV向量表示为字典中少量原子的线性组合，实现高压缩比。
- **算法流程（文字说明）**：
  1. 初始化Key字典和Value字典（随机或预训练方式）。
  2. 固定字典，使用稀疏编码算法（如OMP）为每个KV向量求解稀疏表示系数。
  3. 固定稀疏系数，通过梯度下降或SVD更新字典以最小化重建损失。
  4. 重复步骤2-3直至收敛，最终获得训练好的字典和稀疏表示。
  5. 推理时，将原始KV向量投影到字典上，仅存储稀疏系数和索引，而非完整向量。

## 3. 实验设计：数据集、场景、基准与对比方法

- **数据集与场景**：使用具有挑战性的长上下文基准（long-context benchmarks）进行测试（具体名称未在摘要中列出，推测为如LongBench、L-Eval等）。
- **基准方法**：对比了现有KV缓存压缩技术（例如逐层剪枝、量化等方法），其中SparseCache在超过8倍压缩时仍能保持高性能，而竞争技术在此压缩倍数下表现困难。
- **实验设置**：评估指标包括模型精度（perplexity、任务准确率等）以及内存占用压缩比。
- **对比方法**：未列出具体方法名，但推测包括StreamingLLM、KV Cache Quantization、H2O等主流方法。

## 4. 资源与算力

- 摘要及元数据中**未明确说明**使用的GPU型号、数量、训练时长等具体算力信息。
- 仅提及“端到端学习框架”，推测训练过程中需要较大的GPU内存来存储字典和批量KV向量，但缺乏量化数据。

## 5. 实验数量与充分性

- **实验数量**：摘要中未列举具体实验组数，但提到“大量实验”（extensive experiments），覆盖多个LLM和不同压缩比。
- **充分性分析**：
  - 实验覆盖了从低压缩（8x）到高压缩（17.7x）的多种比率，并对比了竞争方法，证明了在8x以上压缩时仍保持精度。
  - 但未提供消融实验（如不同字典大小、不同稀疏度的影响）、跨模型泛化性细节（仅说“多个LLM”，未列出具体模型名称与规模）。
  - 总体而言，实验设计具有一定充分性，但缺乏详细的消融研究和误差方差报告，客观性待加强（因未提供标准差或多次运行结果）。

## 6. 主要结论与发现

- SparseCache实现了高达**17.7倍**的压缩比，同时保持模型在长上下文基准上的准确性（state-of-the-art）。
- 在超过8倍压缩下，SparseCache仍能保持高性能，而其他竞争方法则难以维持。
- 该框架使得“预计算RAG”范式变得实际可行，显著降低了TTFT并提高了系统吞吐量。

## 7. 优点：方法或实验设计上的亮点

- **创新性**：首次将K-SVD的交替优化思想引入KV缓存压缩，学习全局共享字典，优于逐层方法，更好地捕捉跨层冗余。
- **实用性**：高压缩比且保持精度，直接解决了预计算RAG的存储瓶颈，具有实际部署价值。
- **联合优化**：端到端学习重建损失，而非启发式剪枝，更理论化。
- **性能对比**：明确展示了在高压缩比下的优势，并指出竞争方法的失效点。

## 8. 不足与局限

- **实验覆盖不足**：缺少具体数据集名称、模型规模（如7B、13B、70B）、推理时延与吞吐量的量化结果；未进行消融实验（字典大小、稀疏度敏感度）。
- **资源信息缺失**：未报告训练成本，难以评估方法的开销是否在可接受范围内。
- **公平性风险**：未明确对比方法的配置是否公平（如压缩比对齐、后处理细节），存在倾向性比较的风险。
- **应用限制**：需要离线训练字典，可能无法适应动态更新的KV缓存（如流式推理）。同时，稀疏编码的推理计算开销（解码时从字典重建）未被讨论。

（完）
