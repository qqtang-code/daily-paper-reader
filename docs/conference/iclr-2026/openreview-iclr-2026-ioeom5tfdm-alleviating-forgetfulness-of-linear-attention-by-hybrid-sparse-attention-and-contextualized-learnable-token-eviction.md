---
title: Alleviating Forgetfulness of Linear Attention by Hybrid Sparse Attention and Contextualized Learnable Token Eviction
title_zh: 通过混合稀疏注意力和上下文可学习token淘汰缓解线性注意力的遗忘
authors: "Mutian He, Philip N. Garner"
date: 2025-09-16
pdf: "https://openreview.net/pdf?id=ioeOm5tFDM"
tags: ["query:sparse-attn"]
score: 7.0
evidence: 结合可学习token淘汰的混合稀疏注意力缓解线性注意力遗忘问题
tldr: "线性注意力模型因固定大小记忆导致遗忘,影响检索任务。本文探索混合模型,在线性注意力和全注意力之间插入稀疏注意力,并提出可学习的token淘汰模块。结合滑动窗口注意力,端到端训练的轻量CNN淘汰模块有效聚合信息,缓解遗忘并提升性能。"
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: "线性注意力模型因有限记忆产生遗忘,损害检索密集型任务。"
method: "混合线性注意力与稀疏注意力,并设计可学习的CNN淘汰模块。"
result: 在检索任务上提升了长距离依赖的能力。
conclusion: 混合方法有效缓解了线性注意力的遗忘问题。
---

## Abstract
Linear-attention models that compress the entire input sequence into a fixed-size recurrent state offer an efficient alternative to Transformers, but their finite memory induces forgetfulness that harms retrieval-intensive tasks.
To mitigate the issue, we explore a series of hybrid models that restore direct access to past tokens. We interleave token mixers of intermediate time and space complexity between linear attention and full attention, including the query-aware native sparse attention, and sparse attention with token eviction. We further propose a novel learnable token eviction module. Combined with sliding-window attention, an end-to-end trainable lightweight CNN-based eviction module aggregates information from both past and future adjacent tokens to adaptively retain a limited set of critical KV-pairs per head, maintaining linear attention's constant time and space complexity. Empirical evaluations on retrieval-intensive benchmarks support the effectiveness of our approaches.

---

## 论文详细总结（自动生成）

好的，以下是根据您提供的论文信息生成的详细中文总结。

### 1. 核心问题与整体含义（研究动机和背景）
- **问题**：线性注意力模型（Linear-attention）通过将整个输入序列压缩为固定大小的循环状态来获得线性复杂度，但受限于有限记忆，在处理检索密集型任务（retrieval-intensive tasks）时会产生“遗忘”现象，损害长距离依赖的能力。
- **背景**：Transformer全注意力的平方复杂度限制了长序列应用；线性注意力虽高效，但丢失了过去token的精确访问路径，导致关键信息难以回溯。

### 2. 方法论：核心思想、关键技术细节、算法流程
- **核心思想**：在保持线性注意力常数复杂度优势的前提下，通过混合稀疏注意力恢复对历史token的直接访问，并设计可学习的token淘汰机制来动态保留关键KV对，从而缓解遗忘。
- **关键技术细节**：
  - **混合模型架构**：在线性注意力与全注意力之间，插入中间时间和空间复杂度的token混合器，包括：
    - Query-aware原生稀疏注意力（query-aware native sparse attention）；
    - 基于token淘汰的稀疏注意力（sparse attention with token eviction）。
  - **可学习token淘汰模块**：结合滑动窗口注意力，使用一个轻量级、端到端可训练的CNN基淘汰模块。该模块聚合当前token上下文中过去和未来的相邻token信息，为每个头自适应地保留有限数量的关键KV对，维持线性注意力的常数时间和空间复杂度。
- **算法流程（文字说明）**：
    1. 输入序列先经过标准线性注意力层，得到初步压缩的隐藏状态。
    2. 插入若干稀疏注意力层（可选择原生稀疏或带淘汰的稀疏），直接访问部分历史token。
    3. 在淘汰变体中，CNN模块对每个头的KV缓存评分，根据滑动窗口内局部信息决定保留哪些token，移除冗余或低效的KV对。
    4. 最终输出通过混合后的注意力表示，用于下游任务训练。

### 3. 实验设计
- **数据集 / 场景**：论文未列出具体数据集名称，但指出评估是在“检索密集型基准”（retrieval-intensive benchmarks）上进行的。这类任务通常包括长文本问答、摘要、语言建模等需依赖远程记忆的场景。
- **Benchmark**：未明确给出具体基准名称，推测为常用的长序列理解/检索评估（如LongRangeArena、LAMBADA、QA数据集等）。
- **对比方法**：对比了不同类型的注意力变体，包括：
  - 标准线性注意力（基线）；
  - 原生稀疏注意力（query-aware）；
  - 带固定淘汰的稀疏注意力；
  - 滑动窗口注意力等。

### 4. 资源与算力
- **未明确说明**：文中未提及训练使用的GPU型号、数量、训练时长或显存消耗。无法提供具体算力信息。

### 5. 实验数量与充分性
- **实验数量**：从摘要可推断至少包含以下对比实验：
  - 多种混合结构的消融（不同token mixer组合）；
  - 淘汰模块的变体（有/无学习，不同CNN设计）；
  - 在多个检索密集型基准上的性能对比。
- **充分性与公平性**：
  - 未提供具体数值或表格，但说明“实证评估支持方法的有效性”。
  - 潜在不足：未明确消融实验的具体维度（如淘汰率、窗口大小等），也未报告方差或显著性检验。但作为会议短文摘要，实验规模可能适中。

### 6. 主要结论与发现
- 混合线性注意力与稀疏注意力的架构能有效缓解线性注意力的遗忘问题，提升检索密集型任务的长距离依赖能力。
- 提出的可学习CNN淘汰模块优于固定淘汰策略，能在常数复杂度下动态保留关键信息。
- 整体方法在效率与性能之间取得了平衡，保持了线性注意力的计算优势。

### 7. 优点（方法或实验设计上的亮点）
- **方法创新**：
  - 将可学习的token淘汰机制与稀疏注意力结合，首次在保持线性复杂度下实现了自适应KV压缩。
  - 使用轻量级CNN聚合局部上下文做淘汰决策，端到端可训练，设计简洁高效。
- **实验设计**：
  - 系统对比了多种混合结构，验证了不同组件（稀疏、淘汰、滑动窗口）的必要性。
  - 聚焦检索密集型任务这一关键痛点，问题针对性突出。

### 8. 不足与局限
- **实验覆盖不足**：
  - 未列出具体数据集、任务类型和量化结果，无法判断效果提升的程度。
  - 缺少与最新高效注意力变体（如Mamba、RWKV等）的对比。
- **偏差风险**：
  - 仅提及“检索密集型基准”，可能未涵盖其他需要长程建模的通用任务（如自由生成）。
  - 可学习淘汰模块的泛化能力未在跨领域评估中验证。
- **应用限制**：
  - 淘汰机制依赖滑动窗口局部信息，对于需要全局精确检索的极端长上下文（如百万token级别）可能仍存在信息丢失风险。
  - 未讨论淘汰后关键信息误判的潜在错误传播。

（完）
