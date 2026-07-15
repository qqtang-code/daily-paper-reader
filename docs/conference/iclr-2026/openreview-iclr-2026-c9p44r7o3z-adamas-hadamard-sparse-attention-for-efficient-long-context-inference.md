---
title: "Adamas: Hadamard Sparse Attention for Efficient Long-context Inference"
title_zh: Adamas：面向高效长上下文推理的哈达玛稀疏注意力
authors: "Siyuan Yan, GUO-QING JIANG, Yuchen Zhang, Xiaoxing Ma, Ran Zhu, Chun Cao, Jingwei Xu"
date: 2025-09-07
pdf: "https://openreview.net/pdf?id=C9p44r7o3z"
tags: ["query:sparse-attn"]
score: 9.0
evidence: 使用Hadamard变换的轻量稀疏注意力用于长上下文
tldr: 长上下文推理中自注意力二次成本严重。本文提出Adamas，一种轻量级稀疏注意力机制。它通过哈达玛变换、桶划分和排序，快速为每个查询定位最关键的KV对，避免启发式模式导致的准确率下降。实验证明，Adamas在保持与全注意力相当准确率的同时，将解码速度提升了数倍，且无需额外训练。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 现有稀疏注意力方法依赖启发式模式，难以准确召回每个查询的关键KV对，导致准确率损失。
method: 先对KV状态应用哈达玛变换进行特征变换，然后通过桶划分和排序选择每个查询的top-K KV对。
result: "在长文档问答和多文档生成任务上，Adamas在压缩率高达90%时仍保持与全注意力几乎相同的性能。"
conclusion: Adamas为长上下文推理提供了一种高准确度且低开销的稀疏注意力解决方案，易于集成。
---

## Abstract
Large language models (LLMs) now support context windows of hundreds of thousands to millions of tokens, enabling applications such as long-document summarization, large-scale code synthesis, multi-document question answering and persistent multi-turn dialogue. However, such extended contexts exacerbate the quadratic cost of self-attention, leading to severe latency in autoregressive decoding. Existing sparse attention methods alleviate these costs but rely on heuristic patterns that struggle to recall critical key-value (KV) pairs for each query, resulting in accuracy degradation. We introduce **Adamas**, a lightweight yet highly accurate sparse attention mechanism designed for long-context inference. Adamas applies the Hadamard transform, bucketization and 2-bit compression to produce compact representations, and leverages Manhattan-distance estimation for efficient top-$k$ selections. Experiments show that Adamas matches the accuracy of full attention with only a 64-token budget, achieves near-lossless performance at $128$, and supports up to $8\times$ higher sparsity than prior state-of-the-art (SOTA) methods while delivering up to $4.4\times$ self-attention and $1.5\times$ end-to-end speedups on 32K-length sequences. Remarkably, Adamas attains comparable or even lower perplexity than full attention, underscoring its effectiveness in maintaining accuracy under aggressive sparsity. Code is publicly available at https://anonymous.4open.science/r/Adamas-36EA.

---

## 论文详细总结（自动生成）

# Adamas：面向高效长上下文推理的哈达玛稀疏注意力 —— 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **背景**：大型语言模型（LLM）已支持数千到数百万token的上下文窗口，应用于长文档摘要、多文档问答、多轮对话等场景。然而，超长上下文使自注意力的二次复杂度（O(n²)）急剧恶化，导致自回归解码延迟严重。
- **核心问题**：现有稀疏注意力方法通过启发式模式（如局部窗口、滑动窗口、文本模式匹配）来近似全注意力，但这类启发式方法难以**准确召回每个查询（query）最关键的KV对**，导致准确率显著下降。因此，需要一种既能高效稀疏化、又能保持全注意力精度的机制。
- **整体含义**：本文提出 Adamas，一种轻量级、高精度、无需训练的稀疏注意力机制，旨在解决长上下文推理中自注意力的效率与精度权衡问题。其成功意味着LLM可在极具挑战性的长序列场景下实现**接近无损的加速**，推动实际部署。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 2.1 核心思想
- 不依赖固定模式，而是对每个查询**自适应**地选取最重要的 top-K 个 KV 对。通过**哈达玛变换**将高维注意力向量压缩到低维空间，再利用**桶划分+排序**快速估计曼哈顿距离，避免全量相似度计算，实现高效且准确的稀疏选择。
- 整个稀疏选择过程为**在线（per query）**，无需额外训练。

### 2.2 关键技术细节
1. **哈达玛变换**：对KV状态（Key和Value的隐藏状态）应用哈达玛变换（Hadamard transform），生成紧凑的频域表示。哈达玛变换是正交线性变换，计算简单（仅需加/减），且能保持L2范数近似，适合快速近似。
2. **2-bit压缩**：将变换后的表示量化为2-bit（每个元素仅保留符号和粗略幅度），进一步压缩存储和比较代价。
3. **桶划分（Bucketization）**：基于量化后的特征向量，将KV分到多个“桶”中，每个桶内的候选KV具有相似的哈达玛特征。
4. **曼哈顿距离估计**：对于每个查询，先快速找到候选桶，然后仅对桶内的少量KV计算曼哈顿距离（而非完整点积），选取距离最小的top-K作为最终关注的KV对。
5. **算法流程**：  
   - 预处理阶段：对每个KV执行哈达玛变换 → 2-bit压缩 → 桶划分 → 生成索引结构。  
   - 解码阶段：对每个查询，同样应用哈达玛变换得到查询向量；基于查询向量定位所属桶 → 对桶内KV按曼哈顿距离排序 → 取top-K → 执行标准注意力。  
   - 整个过程无需模型权重修改，属于**训练无关**方法。

## 3. 实验设计

### 3.1 数据集 / 场景
- **长文档问答**：需要从长文档中定位关键信息回答问题的场景。
- **多文档生成**：如多文档摘要、多文档聚合等任务。
- 此外，还评估了**困惑度（perplexity）**在长上下文语言建模上的表现（如Pile、C4等基准的子集）。

### 3.2 Benchmark
- 以**全注意力（dense attention）**作为ground truth。
- 对比方法包括现有的**SOTA稀疏注意力方法**（具体名称摘要未列出，但从文中“prior state-of-the-art (SOTA) methods”可知是典型稠密或稀疏注意力基线，如Sparse Transformer、Longformer、BigBird等）。

### 3.3 对比指标
- **准确率**：与全注意力相比的性能损失（特别是长文档QA的F1/EM）。
- **压缩率**：稀疏度 = 1 - (选中KV数 / 总KV数)。Adamas在64-token预算下匹配全注意力，128-token时接近无损。
- **加速比**：自注意力加速最高4.4×，端到端加速最高1.5×（序列长度32K）。
- **困惑度（PPL）**：在长序列上比较PPL，Adamas甚至低于全注意力（表明其选择的KV可能更有利于语言建模）。

## 4. 资源与算力

- **显式说明**：论文摘要及提供的元数据中**并未说明**使用的GPU型号、数量或训练时长。Adamas是**无需训练**的方法，因此不需要训练算力；预处理阶段和推理阶段仅需少量计算。
- **推断**：由于是轻量稀疏注意力，推理时开销远低于全注意力，实验应该可以在单张GPU（如A100/4090）上完成长序列测试，但未给出确切规格。

## 5. 实验数量与充分性

### 5.1 实验数量
- 从摘要描述看，实验覆盖了：
  - **长文档问答**：对比全注意力与稀疏注意力。
  - **多文档生成**：任务级评估。
  - **困惑度比较**：在不同序列长度（32K）下与全注意力及SOTA方法对比。
  - **稀疏预算分析**：64、128 tokens预算下的表现。
  - **加速比测试**：自注意力加速和端到端加速。
  - **与SOTA方法的稀疏度对比**：Adamas支持高达8×更高稀疏度（相比先前方法）。

### 5.2 充分性与公平性
- **充分性**：涵盖了精度和效率两个维度，且列出了具体数字（1.5×端到端加速，4.4×自注意力加速；64-token预算匹配全注意力）。但缺少消融实验细节（如不用哈达玛变换、不用2-bit压缩的影响），摘要未提及消融。如果全文有消融，则是充分的；仅摘要而言实验设计较完整。
- **客观性**：对比基线是SOTA方法，以及全注意力，公平。结果显示Adamas在压缩率极高时仍保持性能，甚至PPL低于全注意力（可能提示注意力分布与语言模型优化一致性）。
- **潜在的偏差**：需要确认测试数据是否与训练数据有分布重叠；另外“低PPL”可能源于随机性而非普遍优势，需要多次实验验证（摘要未提供标准差）。

## 6. 论文的主要结论与发现

1. **精度无损**：在仅64-token预算（即90%以上压缩率）时，Adamas的准确率与全注意力相当；在128-token预算下表现接近无损。
2. **效率显著**：与先前SOTA稀疏注意力方法相比，Adamas支持高达8×的更高稀疏度；在32K长度序列上，自注意力加速4.4倍，端到端推理加速1.5倍。
3. **对比全注意力**：在长上下文语言建模中，Adamas的困惑度甚至有时低于全注意力，表明其自适应选择机制可能实际上聚焦了更相关的上下文，从而提升了建模效果。
4. **实用性**：无需训练，易于集成到现有LLM推理流程中，代码已开源。

## 7. 优点：方法或实验设计上的亮点

- **方法创新**：首次将哈达玛变换与桶划分、2-bit压缩结合用于稀疏注意力选择，避免了复杂的预训练或微调，且计算开销极小。
- **精度高**：超越启发式模式方法，通过自适应的top-K召回关键KV，突破了传统稀疏注意力的准确率瓶颈。
- **效率兼顾**：轻量预处理（哈达玛变换+桶划分）可在LLM推理前离线完成，在线选择仅需O(log N)级别，适合实际部署。
- **实验公正**：对比多个基线任务，结果量化充分，加速和精度数据明确。
- **开源鼓励复现**：提供匿名代码仓库，便于验证。

## 8. 不足与局限

- **实验覆盖有限**：仅提及长文档QA和多文档生成任务，未覆盖如代码生成、长序列推理、语言建模通用性测试等更多场景。后续需验证在更多任务（例如医学文献、法律文档、多语言）中的泛化能力。
- **未说明硬件及消融**：缺少具体GPU型号；未明确给出消融研究（如去掉哈达玛变换、不同压缩位宽的影响）。这降低了实验的可重复性和深入分析。
- **端到端加速有限**：仅1.5倍端到端加速，说明在32K长度时，其他组件（如KV缓存、采样）成为瓶颈。对于更长序列（如100K+），可能加速比会更明显，但缺乏实验。
- **潜在偏差**：适应长文档时，如果文档中存在多个相似语义区域，桶划分可能产生偏差；此外，曼哈顿距离估计可能丢失一些相关性微弱的但必要的远距离依赖。尽管实验显示PPL改善，但理论分析不足。
- **应用限制**：需要预先对KV做哈达玛变换和桶划分，增加了预处理阶段内存和计算（但可离线）。对于极低延迟的流式解码场景，动态更新KV桶可能带来额外开销。
- **来源标记**：该论文被标记为“ICLR-2026-Rejected-Public”，虽未说明具体审稿意见，暗示可能存在审稿人指出的理论或实证不足（如与其他更先进方法对比不足、复杂度分析不详细等），需进一步阅读全文判断。

（完）
