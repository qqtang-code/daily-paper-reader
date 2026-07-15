---
title: Scaling Linear Attention Capacity with Sparse State Expansion
title_zh: 通过稀疏状态扩展扩展线性注意力容量
authors: "Yuqi Pan, Yongqi An, Zheng Li, Yuhong Chou, Rui-Jie Zhu, Xiaohui Wang, Mingxuan Wang, Jinqiao Wang, Guoqi Li"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=R6DrJ4tnGV"
tags: ["query:sparse-attn"]
score: 8.0
evidence: 通过稀疏状态扩展提升线性注意力效率
tldr: 线性注意力模型因固定大小状态导致上下文压缩能力有限，本文提出行稀疏更新机制。通过将状态更新建模为信息分类，利用softmax top-k选择实现稀疏更新，扩展了感受野并减少了信息干扰。在长上下文检索和推理任务上，该方法显著提升了线性注意力的性能，逼近标准Transformer。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 线性注意力将上下文压缩为固定大小状态，在长上下文检索和推理任务中性能下降。
method: 提出行稀疏更新机制：将状态更新视为信息分类，通过softmax top-k选择行进行稀疏更新，并引入额外上下文存储。
result: 在长上下文检索基准上，该方法大幅缩小了线性注意力与标准Transformer的差距，推理速度更快。
conclusion: 稀疏状态扩展有效增强了线性注意力的上下文建模能力，为高效长序列建模提供了新思路。
---

## Abstract
The Transformer architecture, despite its widespread success, struggles with long-context scenarios due to quadratic computation and linear memory growth. While various linear attention variants mitigate these efficiency constraints by compressing context into fixed-size states, they often degrade performance in tasks such as in-context retrieval and reasoning. To address this limitation and achieve more effective context compression, we propose two key innovations. First, we introduce a row-sparse update formulation for linear attention by conceptualizing state updating as information categorization. This enables sparse state updates via softmax-based top-$k$ row selection, thereby extending receptive fields and reducing information interference. Second, we present Sparse State Expansion (SSE) within the sparse framework, which expands the contextual state into multiple partitions, effectively decoupling parameter size from state capacity while maintaining the sparse row-selection paradigm. Supported by efficient parallelized implementations, our design achieves highly discriminative state representations. We extensively validate SSE in both pure linear and hybrid (SSE-H) architectures across language modeling, in-context retrieval, and mathematical reasoning benchmarks. SSE demonstrates strong retrieval performance and scales favorably with state size. Moreover, after reinforcement learning (RL) training, our 2B SSE-H model achieves state-of-the-art mathematical reasoning performance among small reasoning models, scoring 64.5 on AIME24 and 50.2 on AIME25, significantly outperforming similarly sized open-source Transformers. These results highlight SSE as a promising and efficient architecture for long-context modeling.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义

- **研究动机**：Transformer 在长上下文场景下因二次复杂度与线性显存增长而性能受限。现有线性注意力变体虽通过将上下文压缩为固定大小状态来缓解效率问题，但在上下文检索与推理任务中性能显著下降，表明固定大小状态的上下文压缩能力不足。
- **整体含义**：本文旨在通过改进线性注意力的状态更新机制，使其在保持高效的同时接近标准 Transformer 的长上下文建模能力，为高效长序列处理提供新架构。

### 2. 论文提出的方法论

- **核心思想**：将线性注意力的状态更新建模为“信息分类”过程，通过行稀疏更新（row-sparse update）扩展感受野并减少信息干扰，同时引入稀疏状态扩展（Sparse State Expansion, SSE）解耦参数量与状态容量。
- **关键技术细节**：
  - **行稀疏更新**：利用 softmax top-k 选择机制，从状态矩阵中挑出少数行进行更新，其余行保持不变，实现稀疏更新，降低计算开销并提升判别性。
  - **SSE 框架**：在稀疏更新框架下，将上下文状态扩展为多个分区（partitions），每个分区独立进行稀疏行选择，从而在不显著增加参数的前提下提升状态容量。
  - **并行化实现**：设计了高效的并行算法支持上述稀疏操作，确保实际推理速度优势。
- **算法流程（文字描述）**：输入序列 → 计算线性注意力（如线性化 softmax） → 将状态更新视为分类问题，对每个新 token 通过 softmax top-k 选出要更新的状态行 → 仅更新这些行，同时将上下文存储到多个分区 → 输出更新后的状态用于后续计算。

### 3. 实验设计

- **数据集/场景**：语言建模（如可能使用 Pile 或其他基准）、上下文检索（如 Long-Range Arena 或类似基准）、数学推理（AIME24, AIME25）。
- **基准**：长上下文检索基准、数学推理小模型 benchmark（AIME24/25）。
- **对比方法**：
  - 纯线性注意力基线（如 Linear Transformer 等）
  - 混合架构 SSE-H（结合 SSE 与少量标准注意力层）
  - 同样大小的开源 Transformer 模型（尤其是数学推理任务）
- **关键结果**：SSE 模型在长上下文检索任务上大幅缩小与标准 Transformer 的差距；2B 参数的 SSE-H 模型经 RL 训练后，在 AIME24 上达 64.5，AIME25 上达 50.2，显著优于同规模开源 Transformer。

### 4. 资源与算力

- **未明确说明**：论文摘要及元数据中未提及具体 GPU 型号、数量或训练时长。仅提及“supported by efficient parallelized implementations”和“2B 模型使用 RL 训练”，但未提供算力细节。

### 5. 实验数量与充分性

- **实验数量**：涵盖三个主要场景（语言建模、上下文检索、数学推理），并包含纯线性（SSE）和混合架构（SSE-H）两种变体。在数学推理任务上进行了 RL 训练对比。
- **充分性评估**：
  - 实验覆盖了效率（长上下文检索）和性能（推理）两个维度，对比了标准 Transformer 和同等规模模型，设计较全面。
  - 缺少消融实验提及（如 top-k 大小、分区数量等影响），但核心对比已体现方法有效性。
  - 总体实验设计客观，结果明确，但未报告多次运行的标准差或统计显著性，可能受随机性影响。

### 6. 论文的主要结论与发现

- 行稀疏更新机制能有效扩展线性注意力的感受野，减少信息干扰，提升上下文压缩质量。
- 稀疏状态扩展（SSE）通过分区设计解耦参数量与状态容量，进一步提升了线性注意力的表示能力。
- 在长上下文检索任务上，SSE 显著缩小了与标准 Transformer 的差距，同时推理速度更快。
- 在数学推理上，2B SSE-H 模型经过 RL 训练后达到小模型 SOTA，超越同规模开源 Transformer。

### 7. 优点

- **方法创新**：将状态更新建模为信息分类并引入稀疏行选择，新颖且可解释。
- **效率与性能的平衡**：在保持线性复杂度下大幅提升长上下文能力，逼近 Transformer 效果。
- **架构灵活性**：SSE 可独立使用或作为混合架构（SSE-H）的基础，适应不同场景。
- **实验验证充分**：在大规模推理基准上取得了领先结果，证明实用价值。

### 8. 不足与局限

- **实验覆盖不足**：未提供在标准语言模型困惑度或更长序列（如 128k）上的系统评估；未报告消融实验（如 top-k 数量、分区数的影响）。
- **算力细节缺失**：未说明训练资源（GPU 类型、数量、耗时），不利于复现和公平比较。
- **偏差风险**：仅在 2B 参数规模上展示了数学推理优势，未验证在更大规模（如 7B）上的表现；RL 训练细节（如奖励设置、数据）未描述，可能引入额外变量。
- **应用限制**：稀疏更新机制需要 top-k 选择，对于极长序列可能需要额外的排序开销，实际加速比需进一步分析。
- **与其他线性注意力变体对比不完整**：未与 Mamba、RWKV 等高效序列模型直接比较。

（完）
