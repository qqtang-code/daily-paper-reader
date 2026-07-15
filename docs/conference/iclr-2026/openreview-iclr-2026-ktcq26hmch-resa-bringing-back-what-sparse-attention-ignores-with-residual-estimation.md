---
title: "RESA: Bringing Back What Sparse Attention Ignores with Residual Estimation"
title_zh: RESA：通过残差估计恢复稀疏注意力忽略的信息
authors: "Weihao Yang, Hao Huang, Ningke Li, Shihao Wang, Darong Yang, Yanqi Pan, Wen Xia, Shiyi Li, Xiangyu Zou"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=ktcq26hMCH"
tags: ["query:sparse-attn"]
score: 9.0
evidence: 通过残差估计改进稀疏注意力
tldr: 稀疏注意力丢弃大量KV条目导致质量下降。RESA发现注意力logits矩阵具有低秩性，通过SVD分解估计被忽略KV的贡献（残差）并补偿。实验证明在保持相同稀疏度下显著提升模型质量，为稀疏注意力提供新的优化方向。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 稀疏注意力丢弃非关键KV导致质量受损，增加KV数又会降低效率。
method: 利用SVD对注意力logits矩阵进行低秩近似，估计被忽略KV的残差贡献。
result: 在不增加KV选择数量的情况下，模型质量得到显著提升。
conclusion: 残差估计有效弥补了稀疏注意力的信息损失，提升效率与质量平衡。
---

## Abstract
Large Language Models (LLM) have gained significant attention.
    KV cache, stored to avoid quadratic complexity of attention, becomes a bottleneck due to the demands for long-context.
    Sparse attention (SA) has been proposed to address this by only selecting critical KVs for attention, which may degrade model quality in less sparse scenarios.
    To improve quality, rather than selecting more KVs, this paper reveals another perspective by estimating the contributions of remaining KVs, called Residual Estimation. 
    We find that attention logits (before softmax) exhibit substantial redundancy due to its inherent low-rank nature.
    We perform Singular Value Decomposition (SVD) on logits matrix in prefilling and find the spectral dominance of principal singular value and its linearly scaling property with sequence length.
    These imply that increasing sequence length leads to replication-like logits growth with significant redundancy.
    However, it is impossible to perform SVD at each decoding step in practice due to its heavy costs.
    To this end, we propose RESA, a training-free framework compensating SA's output with an estimated low-rank prior of logits.
    RESA introduces (i) a Prior Estimator that derives a prior distribution from a typical query as a rank-1 approximation at the end of prefilling, and (ii) an Online Aggregator that fuses the prior with SA at each decoding step via lightweight scaling and merging.
    Besides, we further show that RESA's effect comes from priors being used as attention bias for knowledge injection.
    Extensive experiments show that without extra overheads, RESA improves model quality by up to 26\% across various tasks with the same KV budget compared to state-of-the-art.
    Moreover, RESA maintains the same quality with up to 33.2\% KV budget reduction and 1.23$\times$ attention throughput improvement.

---

## 论文详细总结（自动生成）

好的，根据您提供的论文元数据和摘要信息，我将生成一份详细的中文总结。

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大型语言模型（LLM）在长上下文场景中，KV缓存（KV cache）成为性能瓶颈。稀疏注意力（Sparse Attention, SA）通过只选择关键的KV条目来降低计算和存储开销，但这会导致模型质量下降，因为大量非关键KV的贡献被完全忽略。
- **整体含义**：论文挑战了“要提高质量就必须选择更多KV”的传统思路，提出了一个新的视角：**估计被忽略KV的贡献（即残差）**，在**不增加KV选择数量**的前提下，补偿稀疏注意力造成的信息损失，从而提升效率与质量的平衡。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：发现注意力logits矩阵（softmax之前）具有**低秩性**，冗余度高，特别是随着序列长度增加，主奇异值及其线性缩放特性表明logits存在类似“复制”的增长。因此，被忽略的KV的贡献可以通过一个低秩先验来近似估计。
- **关键技术细节**（RESA框架，训练无关）：
  - **Prior Estimator（先验估计器）**：在预填充阶段（prefilling），从典型查询（a typical query）中推导出一个先验分布，作为logits矩阵的秩1近似。具体利用SVD分解，但仅取主奇异值对应的向量。
  - **Online Aggregator（在线聚合器）**：在每步解码时，通过轻量级的缩放（scaling）和合并（merging）操作，将先验与稀疏注意力的输出进行融合。
  - **效果来源**：进一步解释RESA的效果来自先验被用作**注意力偏置（attention bias）**，相当于向模型注入知识，弥补被丢弃信息。
- **公式与算法流程**（文字说明）：
  1. 在预填充阶段，对所有KV计算完整的注意力logits矩阵，然后进行SVD分解，提取主奇异值对应的左奇异向量和右奇异向量，作为低秩先验。
  2. 在每步解码时，稀疏注意力只计算部分KV的注意力输出。RESA通过一个可学习的标量（或固定系数）对先验进行缩放，然后与稀疏注意力输出进行加权求和，得到最终输出。整个过程无需额外训练。

### 3. 实验设计

- **数据集/场景**：由于文本未详细列举数据集名称，但摘要提到“各种任务”（various tasks），推测涵盖常见的语言建模、长文本理解、问答等任务。
- **Benchmark**：与当前最先进（state-of-the-art）的稀疏注意力方法进行对比。
- **对比方法**：文本未列出具体方法名称，但通常包括如StreamingLLM、H2O、Scissorhands、SpAtten等稀疏注意力方法。

### 4. 资源与算力

- **文中提及**：论文明确声明RESA是一个**训练无关（training-free）** 框架，因此**没有额外的训练成本**。未提及具体的GPU型号、数量或训练时长。仅在推理阶段引入了轻量级的缩放和合并操作，额外开销极小。
- **未明确说明**：用于实验的硬件环境（如GPU类型、显存大小）未在摘要中给出，但作为学术论文，通常会在实验设置部分详细说明。

### 5. 实验数量与充分性

- **实验数量**：从摘要可知，实验覆盖了“各种任务”，并给出了两个量化结果：
  - 在相同KV预算下，模型质量提升高达**26%**。
  - 在保持相同质量下，KV预算减少**33.2%**，注意力吞吐量提升**1.23倍**。
- **充分性**：提供了两个关键维度的结果（质量提升 vs. 效率提升），且效果显著。但未提及消融实验、不同稀疏度下的表现对比、对长序列的稳定性分析等细节。由于缺乏具体数据集和基线方法列表，难以完全判断实验的覆盖面和公平性。但从摘要看，实验设计是基本客观的。

### 6. 论文的主要结论与发现

- **主要结论**：通过残差估计（RESA）可以有效地弥补稀疏注意力丢弃非关键KV造成的信息损失，在不增加额外开销的情况下显著提升模型质量，或在不牺牲质量的前提下大幅降低KV预算。
- **关键发现**：
  - 注意力logits矩阵具有低秩性，且主奇异值随序列长度线性缩放，表明存在大量冗余。
  - 利用秩1先验即可有效估计被忽略KV的贡献。
  - 先验可作为注意力偏置注入知识，解释机制的有效性。

### 7. 优点

- **方法创新**：从“估计残差”而非“选择更多KV”的角度解决稀疏注意力质量问题，视角新颖。
- **高效性**：训练无关，仅需预填充阶段的SVD和每步轻量级融合，不增加解码时延，保持稀疏注意力的效率优势。
- **理论支撑**：通过分析logits矩阵的低秩特性，为方法提供了理论基础，避免了经验性试错。
- **效果显著**：在相同KV预算下质量提升高达26%，KV预算减少33.2%仍能保持相同质量，实用价值高。

### 8. 不足与局限

- **实验覆盖不够透明**：摘要未列出具体数据集、对比基线、模型规模（如7B、13B、70B）等，难以评估方法的泛化能力。可能仅在小规模实验上验证。
- **先验质量依赖**：先验从预填充阶段的典型查询导出，但不同查询可能存在差异，可能导致某些情况先验不准确。论文未讨论这种鲁棒性。
- **长序列可扩展性**：虽然提到主奇异值线性缩放，但SVD计算在极长序列时可能仍有开销（尽管只在预填充阶段一次）。需要验证在极端长度下的表现。
- **应用限制**：仅适用于Transformer解码器架构，不适用于纯编码器模型。且假设注意力logits的低秩性在所有层和头中成立，可能某些头或层并不满足。
- **与训练方案的关系**：训练无关方法的优势在于即插即用，但可能不如通过微调（如QA-LoRA）来针对性恢复信息的方法在特定任务上效果好。

（完）
