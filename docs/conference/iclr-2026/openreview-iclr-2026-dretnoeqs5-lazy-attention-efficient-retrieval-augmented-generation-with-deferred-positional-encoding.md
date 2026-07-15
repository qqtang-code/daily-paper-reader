---
title: "Lazy-Attention: Efficient Retrieval-Augmented Generation with Deferred Positional Encoding"
title_zh: Lazy-Attention：通过延迟位置编码实现高效检索增强生成
authors: "Haocheng Xia, Mihir Pamnani, Hanxi Fang, Supawit Chockchowwat, Yongjoo Park"
date: 2025-09-17
pdf: "https://openreview.net/pdf?id=DrETNoeqS5"
tags: ["query:sparse-attn"]
score: 7.0
evidence: 通过延迟位置编码实现位置无关的KV重用
tldr: Lazy-Attention提出了一种新颖的注意力机制，通过核化延迟位置编码实现零拷贝、位置无关的KV重用。这解决了传统KV缓存中位置信息固定导致重用受限的问题，在检索增强生成和上下文学习中显著降低了内存开销并提高了计算效率。该方法为KV缓存的高效利用提供了新思路。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 传统KV缓存嵌入位置信息，限制了其在不同上下文中的可重用性。
method: 将位置编码与注意力计算分离并核化，实现零拷贝位置无关KV重用。
result: 降低了内存开销并提高了KV缓存的重用效率。
conclusion: Lazy-Attention为高效KV缓存提供了新方法。
---

## Abstract
Key-value (KV) caching accelerates inference in large language models (LLMs) by reusing computations from previously generated tokens. Its importance becomes even greater in long-context applications such as retrieval-augmented generation (RAG) and in-context learning (ICL). However, conventional KV caching embeds positional information directly into the cache, limiting its reusability. Existing solutions face a memory-compute trade-off. Specifically, they either restrict reuse to prefixes or require expensive memory materialization for position adjustment.
We introduce Lazy-Attention, a novel attention mechanism that kernelizes deferred positional encoding to enable zero-copy, position-agnostic KV reuse. By fusing positional adjustment into the attention kernel on the fly, Lazy-Attention resolves the materialization bottleneck, allowing a single physical KV copy to serve multiple logical requests at arbitrary positions.
Leveraging two optimized kernels tailored for prefilling and decoding, Lazy-Attention achieves significant efficiency improvements: under skewed document distributions, it reduces time-to-first-token (TTFT) by 1.37$\times$ and increases inference throughput by 1.40$\times$ compared to the state-of-the-art Block Attention, while maintaining comparable output quality.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **背景**：在大语言模型（LLM）中，键值缓存（KV caching）通过重用先前生成 token 的计算来加速推理。在长上下文应用（如检索增强生成 RAG 和上下文学习 ICL）中，KV 缓存的重要性更为突出。
- **问题**：传统的 KV 缓存将位置信息直接嵌入其中，导致缓存只能用于固定的上下文位置，限制了其可重用性。现有解决方案存在内存与计算之间的权衡——要么限制重用仅限于前缀，要么需要昂贵的内存实现来进行位置调整。
- **整体含义**：Lazy-Attention 旨在解决上述权衡，提出一种位置无关的 KV 重用机制，在保持低内存开销的同时提高计算效率。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
- **核心思想**：通过核化延迟位置编码（kernelized deferred positional encoding），实现零拷贝、位置无关的 KV 重用。将位置编码与注意力计算分离，并在注意力内核中动态融合位置调整，从而避免显式的位置调整内存开销。
- **关键技术细节**：
  - **延迟位置编码**：不将位置信息固化到 KV 缓存中，而是在注意力计算时按需引入。
  - **核化融合**：将位置调整操作融入注意力内核（kernel）中，使得单个物理 KV 拷贝可以服务多个不同位置的逻辑请求。
  - **两个优化内核**：针对预填充（prefilling）和解码（decoding）阶段分别设计了专用内核，以最大化效率。
- **公式/算法流程**（文字描述）：
  - 对于给定的查询和键值对，传统注意力计算中位置信息已预先嵌入。Lazy-Attention 将其分离：缓存中仅存储无位置嵌入的 KV 表示，而位置编码在注意力核中通过核函数动态计算并融合，等效于在注意力分数计算中引入了位置偏移量。这一过程无需显式拷贝或修改缓存数据，实现了“零拷贝”重用。

### 3. 实验设计：使用了哪些数据集/场景、基准测试、对比方法
- **应用场景**：检索增强生成（RAG）和上下文学习（ICL），特别是文档分布偏斜（skewed document distributions）的场景。
- **基准方法**：与最先进的 **Block Attention** 进行对比。
- **对比指标**：首 token 延迟（TTFT）、推理吞吐量（throughput）以及输出质量（output quality）。

### 4. 资源与算力
- 论文的元数据中未明确提及使用的 GPU 型号、数量或训练时长。仅从摘要中可知实验是在推理场景下进行，并未说明具体的硬件配置。因此，算力信息缺失，需指出这一点。

### 5. 实验数量与充分性
- 论文摘要中报告了主要结果：在文档分布偏斜场景下，与 Block Attention 相比，Lazy-Attention 将 TTFT 降低 1.37 倍，推理吞吐量提升 1.40 倍，且输出质量相当。
- 缺少对更多数据集、消融实验、不同模型尺寸、不同序列长度等方面的系统报告。由于原文内容有限，无法判断实验的全面性。根据现有信息，实验覆盖场景较窄（仅提及偏斜文档分布），公平性依赖于与单一基线（Block Attention）的比较，可能需要更多对比来验证优势。

### 6. 论文的主要结论与发现
- Lazy-Attention 通过延迟位置编码解决了传统 KV 缓存位置相关性导致的重用限制。
- 与 Block Attention 相比，在保持输出质量的前提下，显著降低了首 token 延迟并提高了推理吞吐量。
- 证明了零拷贝位置无关 KV 重用的可行性和效率优势，为高效 KV 缓存提供了新方法。

### 7. 优点
- **创新性**：提出核化延迟位置编码，将位置调整过程融入注意力内核，避免了显式内存操作，属于注意力机制的新颖改进。
- **效率提升**：在特定场景（偏斜文档分布）下实现了明显的性能提升（TTFT 降低 1.37×，吞吐量提高 1.40×）。
- **实用性**：直接面向 RAG 和 ICL 等实际应用，对长上下文推理有直接帮助。
- **零拷贝设计**：单个物理 KV 拷贝可服务多个逻辑请求，有效降低内存开销。

### 8. 不足与局限
- **实验覆盖不足**：仅报告了与 Block Attention 的对比，缺乏与更多基线（如标准注意力、FlashAttention、其他 KV 复用方法）的比较，也未提供不同模型、不同序列长度的详细结果。
- **数据来源受限**：仅提及偏斜文档分布场景，未说明数据集具体名称、规模或多样性，实验泛化性存疑。
- **硬件资源未说明**：无法评估实验环境对结果的潜在影响，也不利于复现。
- **输出质量评估简单**：仅声称“输出质量相当”，未提供具体指标或量化结果（如 ROUGE、BLEU、准确率等），可能削弱结论的说服力。
- **应用限制**：方法可能仅适用于需要大量重用 KV 的场景（如多轮 RAG），对于单次推理或严格前缀匹配的场景优势可能不明显。

（完）
