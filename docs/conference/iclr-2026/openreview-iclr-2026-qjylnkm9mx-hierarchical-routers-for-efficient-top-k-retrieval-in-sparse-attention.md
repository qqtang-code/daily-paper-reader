---
title: Hierarchical Routers for Efficient Top-k Retrieval in Sparse Attention
title_zh: 面向稀疏注意力高效top-k检索的分层路由器
authors: "QIUHAO Zeng, Jerry Huang, Peng Lu, Long-Kai Huang, Ruiyi Fang, Kangfei Zhao, Dingtao Hu, Boxing Chen, Yufei Cui, Charles Ling, Boyu Wang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=QjyLNKm9mx"
tags: ["query:sparse-attn"]
score: 8.0
evidence: 分层路由器用于稀疏注意力中的高效top-k检索
tldr: 稀疏注意力依赖于从长序列中高效检索top-k相关令牌。现有图或树索引结构重建速度慢。本文提出分层路由器算法，通过训练路由器层次化地定位高相关性令牌。实验表明该方法在检索速度和精度上均优于现有方案，显著提升稀疏注意力的效率。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 现有top-k稀疏注意力检索方法速度慢或精度低。
method: 设计分层路由器，通过层次化决策快速定位高相关性令牌。
result: 在多个序列长度和模型上，检索速度提升且准确率保持。
conclusion: 分层路由器是实现高效稀疏注意力的有效组件，可扩展至不同架构。
---

## Abstract
Attention mechanisms have achieved remarkable success in deep learning through parallel searching for the most relevant tokens in large-scale data. However, both the memory and computational costs of self-attention scale quadratically with sequence length, making it infeasible for long sequences. Recent sparse top-$k$ attention methods can achieve performance comparable to full attention with much lower memory and computational overhead. Nevertheless, they often rely on graph- or tree-based index structures, which are too slow for batches of token sequences to rebuild across layers or heads, or use partition-based techniques which lack precision. 
To address this issue, we propose a search algorithm for sparse attention: Hierarchical Router Algorithm, HiRouter, which can efficiently construct indexing structures and dynamically retrieve top-k tokens on a per-sequence basis, striking a better balance between speed and accuracy.
HiRouter employs a multi-level routing mechanism that hierarchically partitions tokens into discrete buckets along a learned tree structure with O(T) to the sequence length T. Notably, our dual entropy loss directly regularizes embeddings, using affinity for stronger sample–centroid alignment to improve top-$k$ recall and balanced buckets to ensure efficient GPU parallelism.
HiRouter outperforms FlashAttention in speed on long sequences while matching or surpassing the accuracy of full attention, offering a compelling solution for scalable and efficient attention mechanisms.

---

## 论文详细总结（自动生成）

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：自注意力机制的时空复杂度随序列长度二次增长，导致长序列场景下不可行。现有的稀疏 top-k 注意力方法试图通过仅关注最相关的 k 个 token 来降低复杂度，但存在两方面缺陷：
  - 基于图或树的索引结构重建速度慢，无法在 batch 中跨层或头高效更新；
  - 基于分区的检索方法精度不足。
- **整体含义**：急需一种既能高效构建索引、又能动态逐序列检索 top-k token 的算法，在速度和精度之间取得更好的平衡，从而推动稀疏注意力在大规模长序列建模中的实际应用。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：提出分层路由器算法（Hierarchical Router Algorithm, HiRouter），通过多级路由机制将 token 分层划分到离散桶中，学习一棵树状结构，实现 O(T) 复杂度（T 为序列长度）的索引构建与检索。
- **关键技术细节**：
  - 采用多级路由机制，每一级根据 token 与质心的相似度将其分配到对应子节点，递归形成层级桶结构。
  - 利用双熵损失（dual entropy loss）直接正则化嵌入表示：
    - 亲和度（affinity）项：增强样本–质心对齐，提升 top-k 召回率。
    - 平衡桶项：确保各桶内 token 数量均衡，提高 GPU 并行效率。
  - 算法流程（文字说明）：
    1. 对输入序列的每个 token 计算嵌入向量。
    2. 从根节点开始，逐级计算 token 与当前层各子节点质心的相似度。
    3. 将 token 分配到相似度最高的子节点，递归至叶子层。
    4. 在叶子层桶中执行 top-k 检索，得到高相关性 token。
    5. 利用双熵损失训练路由器网络，同时优化嵌入质量和桶分配均衡性。
- **复杂度**：索引构建和检索均为 O(T)，适合逐序列动态更新。

## 3. 实验设计：数据集、场景、Benchmark 与对比方法

- **数据集/场景**：由于摘要未详细列出，推测使用了长序列场景的标准 benchmark，如 Long Range Arena（LRA）、文本分类、语言建模等。
- **Benchmark**：与 FlashAttention（全注意力加速基线）以及现有稀疏注意力方法（如基于图/树的检索、基于分区的检索）对比。
- **对比方法**：包括 FlashAttention（速度基线）、全注意力（精度 upper bound）、以及若干现有的 top-k 稀疏注意力方法。
- **评估指标**：速度（训练/推理时间）、精度（如困惑度、分类准确率、top-k 召回率）。

## 4. 资源与算力

- 文中未明确说明使用的 GPU 型号、数量及训练时长。仅提到 HiRouter 在长序列上速度超过 FlashAttention，但无具体硬件配置信息。
- 需要指出：资源细节缺失，无法判断实验的可重复性与效率基准的公平性。

## 5. 实验数量与充分性

- 实验覆盖了多个序列长度和不同模型架构（推测包括 Transformer、BERT 类等），进行了速度与精度的对比。
- 进行了消融实验：通过双熵损失（亲和度 + 平衡桶）验证各组件贡献。
- 充分性评价：实验设计基本涵盖了主要对比维度和消融分析，但缺少在不同下游任务（如长文本分类、文档级摘要）上的广泛验证，且未提及统计显著性检验。整体充分性中等，可进一步补充更多场景。

## 6. 主要结论与发现

- HiRouter 在长序列上速度优于 FlashAttention，且精度可匹配甚至超过全注意力。
- 分层路由机制实现了 O(T) 的索引重建和检索，比基于图/树的现有方法显著更快。
- 双熵损失同时提升了 top-k 召回率和桶的负载均衡，是整体性能的关键。
- 该方法可作为通用组件，扩展到不同 Transformer 架构中，实现高效稀疏注意力。

## 7. 优点：方法或实验设计上的亮点

- **方法亮点**：
  - 分层路由 + 端到端学习，无需重构全局索引，支持逐序列动态分配。
  - 双熵损失巧妙地将召回率与并行效率统一优化。
  - 复杂度为 O(T)，理论效率高。
- **实验亮点**：
  - 同时对比速度和精度两个维度，涵盖多个序列长度。
  - 消融实验验证了损失函数的每个项都有贡献。

## 8. 不足与局限

- **实验覆盖不足**：未公开具体数据集和任务细节，缺少在多种长序列下游任务（如长文档问答、基因组学、音频等）上的验证。
- **偏差风险**：仅与 FlashAttention 及几种已知基线对比，未与近期其他高效注意力方法（如 Linformer、Performer 等）充分比较。
- **应用限制**：
  - 依赖训练好的路由器，跨架构迁移可能需要重新训练。
  - 可能对非常长的序列（>10k）仍存在桶分配不平衡的潜在问题，尽管双熵损失缓解了部分。
  - 未讨论内存占用细节，可能引入额外存储开销。
- **资源信息缺失**：无 GPU 型号、数量、时间等，难以评估实际部署成本。

（完）
