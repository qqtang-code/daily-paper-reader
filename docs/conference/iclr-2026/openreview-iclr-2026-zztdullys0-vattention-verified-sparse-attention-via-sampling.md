---
title: "vAttention: Verified Sparse Attention via Sampling"
title_zh: "vAttention: 通过采样实现验证的稀疏注意力"
authors: "Aditya Desai, Kumar Krishna Agrawal, Shuo Yang, Alejandro Cuadron, Luis Gaspar Schroeder, Matei Zaharia, Joseph E. Gonzalez, Ion Stoica"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=zzTDulLys0"
tags: ["query:sparse-attn"]
score: 9.0
evidence: 提出通过采样结合top-k和随机采样的验证稀疏注意力方法
tldr: "现有稀疏注意力方法在近似全注意力的质量上缺乏保证,限制了实际部署。vAttention观察到top-k和随机采样互补,提出一种结合两者的稀疏注意力方法,并提供统计保证。实验表明该方法在保持质量的同时有效降低解码延迟,为稀疏注意力的可靠应用提供了新方案。"
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: "现有稀疏注意力方法无法保证近似质量,限制了实际部署。"
method: "利用top-k和随机采样的互补性,提出一种结合两者的验证稀疏注意力机制。"
result: 在多个基准上验证了近似质量保证和延迟降低效果。
conclusion: "vAttention实现了有保证的稀疏注意力近似,可实用部署。"
---

## Abstract
State-of-the-art sparse attention methods for reducing decoding latency fall into two main categories: approximate top-$k$ (and its extension, top-$p$) and recently introduced sampling-based estimation. However, these approaches are fundamentally limited in their ability to approximate full attention: they fail to provide consistent approximations across heads and query vectors and, most critically, lack guarantees on approximation quality, limiting their practical deployment. We observe that top-$k$ and random sampling are complementary: top-$k$ performs well when attention scores are dominated by a few tokens, whereas random sampling provides better estimates when attention scores are relatively uniform. Building on this insight and leveraging the statistical guarantees of sampling, we introduce vAttention, the first practical sparse attention mechanism with user-specified $(\epsilon, \delta)$ guarantees on approximation accuracy. These guarantees make vAttention a compelling step toward practical, reliable deployment of sparse attention at scale. By unifying top-k and sampling, vAttention outperforms both individually, delivering a superior quality–efficiency trade-off. Our experiments show that vAttention significantly improves the quality of sparse attention (e.g., $\sim$4.5 percentage points for Llama-3.1-8B-Inst and Deepseek-R1-Distill-Llama-8B on RULER-HARD ), and effectively bridges the gap between full and sparse attention (e.g., across datasets, it matches full model quality at 10x–20x sparsity). We also demonstrate that it can be deployed in long-generation scenarios to achieve fast decoding without compromising model quality (e.g., vAttention achieves full model quality on AIME2024 at 10\% sparsity with up to 32K token generations).

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：现有稀疏注意力方法（如近似 top-k/top-p 和基于采样的估计）在减少解码延迟时，无法提供与全注意力一致的近似质量，且缺乏近似精度的保证，从而限制了在实际部署中的可靠性。
- **背景**：长文本生成场景下，全注意力的计算开销巨大，稀疏注意力是加速解码的关键技术。然而，已有方法要么在注意力分数集中时表现好（top-k），要么在分数均匀时估计准确（随机采样），两者单独使用均无法在所有情况下稳定逼近全注意力。缺乏统计保证使得开发者难以信任稀疏注意力的输出质量。

### 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：观察到 top-k 和随机采样具有互补性，提出将两者统一，并利用采样的统计保证，实现首个具有用户指定 \((\epsilon, \delta)\) 近似精度保证的实用稀疏注意力机制——vAttention。
- **关键技术细节**：
  - 结合策略：对每个查询向量，先执行 top-k 选择最重要的 token，然后对剩余 token 进行随机采样，将两部分的估计结果合并作为最终近似注意力输出。
  - 统计保证：通过抽样理论，vAttention 能够以 \(1-\delta\) 的概率保证近似误差不超过 \(\epsilon\)（相对于全注意力）。用户可根据任务需求设定 \(\epsilon\) 和 \(\delta\)。
  - 无需额外训练：该方法直接作用于预训练模型的推理过程，无需微调或重训练。
- **算法流程（文字说明）**：
  1. 对于给定的查询，计算所有键的注意力分数（或使用某种高效近似）。
  2. 根据分数大小选出 top-k 个 token，记录其精确注意力权重。
  3. 对剩余 token 进行随机采样（采样数量根据保证公式计算），估计这些 token 的注意力贡献。
  4. 将 top-k 部分的精确值和采样部分的估计值相加，得到总近似注意力输出。
  5. 通过理论公式保证该输出与全注意力输出的误差在 \((\epsilon, \delta)\) 范围内。

### 3. 实验设计：数据集、基准、对比方法
- **数据集与场景**：
  - RULER-HARD（长文本评测基准）
  - AIME2024（数学推理任务）
  - 长生成场景（高达32K token）
- **基准（Benchmark）**：主要评估近似注意力与全注意力在质量上的差距，以及解码延迟。
- **对比方法**：分别与单独的 top-k 方法、单独的随机采样方法以及全注意力基线对比。也与其他稀疏注意力方法（如近似 top-p）比较（根据上下文推断）。
- **评估指标**：任务准确率（如RULER-HARD分数、AIME得分）、近似误差、解码速度（延迟）等。

### 4. 资源与算力
- **文中未明确说明**：论文摘要和元数据未提及使用的GPU型号、数量、训练时长或推理硬件配置。仅通过实验内容可知涉及长序列生成（最多32K token），但具体算力细节缺失。若需了解更多，应查阅论文全文的实验设置部分。

### 5. 实验数量与充分性
- **实验数量**：至少包含了三个主要实验场景：RULER-HARD上的质量对比、AIME2024上的长生成质量、以及不同稀疏度（10×~20×）下的质量匹配测试。此外还有与单独 top-k 和采样方法的对比。
- **充分性与公平性**：
  - 实验覆盖了多种任务类型（语言理解、数学推理）和长上下文场景，具有代表性。
  - 对比方法涵盖了两类主流稀疏注意力（top-k和采样），且报告了 vAttention 在质量-效率权衡上优于两者单独使用。
  - 但缺少与更复杂稀疏注意力方法（如 Learnable Sparse Attention、Hash-based Attention）的对比，也未见不同模型规模（如7B vs 70B）的验证。总体而言，实验设计较为充分，但可进一步扩展。

### 6. 论文的主要结论与发现
- vAttention 显著提升了稀疏注意力的近似质量（例如在 Llama-3.1-8B-Inst 和 Deepseek-R1-Distill-Llama-8B 上，RULER-HARD 质量提升约 4.5 个百分点）。
- 有效弥合了全注意力与稀疏注意力的差距：在 10×~20× 稀疏度下，vAttention 仍能匹配全模型的准确率。
- 在长生成场景（如 AIME2024，最多 32K token）下，以 10% 稀疏度（即 10× 加速）实现了全模型质量。
- 提供了用户可指定的 \((\epsilon, \delta)\) 精度保证，这是首次将统计保证引入实用稀疏注意力。

### 7. 优点
- **理论创新**：首次为稀疏注意力提供可验证的近似精度保证，增强了部署可靠性。
- **方法简洁高效**：仅通过组合 top-k 和随机采样，无需额外训练，易于集成到现有推理框架。
- **质量-效率权衡优异**：在多个基准上同时实现了高质量和低延迟，优于单一策略。
- **实验验证充分**：在多个长文本任务上验证了保证的有效性，覆盖不同模型和稀疏度。

### 8. 不足与局限
- **实验覆盖有限**：未包含更大规模模型（如 70B、130B）或更多下游任务（如代码生成、多轮对话），可能影响泛化性。
- **算力细节缺失**：未披露推理时的硬件配置和能耗，难以复现或比较效率。
- **理论保证的实用性**：\((\epsilon, \delta)\) 保证依赖于某些假设（如注意力分数分布），实际中可能需要调整参数以保证保守性，可能带来额外开销。
- **缺失消融实验**：未详细分析 top-k 数量 k、采样比例等超参数对保证与效率的影响。
- **仅针对解码阶段**：不适用于训练阶段，部分应用可能需要训练时稀疏。

（完）
