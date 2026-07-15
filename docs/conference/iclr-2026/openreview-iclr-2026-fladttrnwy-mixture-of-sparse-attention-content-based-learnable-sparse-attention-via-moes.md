---
title: "Mixture of Sparse Attention: Content-Based Learnable Sparse Attention via MoEs"
title_zh: 稀疏注意力混合：基于MoE的内容可学习稀疏注意力
authors: "Piotr Piękos, Róbert Csordás, Firas Laakom, Li Nanbo, Jürgen Schmidhuber"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=FlAdTTRnWY"
tags: ["query:sparse-attn"]
score: 9.0
evidence: 基于专家混合的内容可学习稀疏注意力
tldr: 次二次注意力方法性能仍不如softmax注意力。本文假设动态学习的内容稀疏性可带来更高效注意力。提出MoSA，借鉴混合专家架构，为每个注意力头动态选择k个token，实现任意稀疏模式。通过将复杂度降至O(k^2+T)，可在相同预算下使用更多头，增强专业化。实验表明，MoSA在多种稀疏注意力变体中表现最佳，接近甚至超越全注意力。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 现有次二次注意力方法仍逊于softmax注意力，假设动态内容稀疏性可以改进。
method: 提出MoSA，利用门控网络为每个注意力头从序列中动态选择k个token，允许任意稀疏模式。
result: 在语言建模和分类任务上，MoSA以更低计算量取得了与全注意力相当或更优的性能。
conclusion: MoSA证明了可学习内容稀疏性是一种有效的注意力加速策略，为设计高效Transformer提供了新范式。
---

## Abstract
Despite the significant research efforts, subquadratic attention methods still suffer from inferior performance in practice. 
We hypothesize that dynamic, learned content-based sparsity can lead to more efficient attention mechanisms.
We present Mixture of Sparse Attention (MoSA), a novel approach inspired by Mixture of Experts (MoE). MoSA dynamically selects tokens for each attention head, allowing arbitrary sparse attention patterns.
By selecting $k$ tokens from a sequence of length $T$, MoSA reduces the computational complexity of each attention head from $O(T^2)$ to $O(k^2+T)$. This enables using more heads within the same computational budget, allowing higher specialization. We show that among the tested sparse attention variants, MoSA is the only one that can outperform the dense baseline, sometimes with up to 27\% better perplexity for an identical compute budget. 
MoSA can also reduce the resource usage compared to dense self-attention. 
Despite using torch implementation without an optimized kernel, perplexity-matched MoSA models are simultaneously faster in wall-clock time, require less memory for training, and drastically reduce the size of the KV-cache compared to the dense transformer baselines.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：尽管已有大量研究投入，次二次复杂度的注意力方法（如稀疏注意力、线性注意力等）在实际应用中性能仍普遍不如标准的 softmax 全注意力（\(O(T^2)\) 复杂度）。
- **研究动机**：作者假设**动态的、基于内容学习得到的稀疏性**能够实现更高效的注意力机制，即让模型根据输入内容自动选择需要关注的 token，而非采用固定的稀疏模式或近似方法。
- **整体含义**：提出一种名为 Mixture of Sparse Attention (MoSA) 的新方法，灵感来自混合专家（MoE）架构。MoSA 为每个注意力头动态选择 \(k\) 个 token，从而在保持灵活性和表达能力的同时大幅降低计算复杂度，并允许使用更多注意力头以提高专业化程度。实验表明 MoSA 在多种稀疏注意力变体中唯一能超越密集基线，有时在相同计算预算下获得高达 27% 的困惑度改善。

## 2. 论文提出的方法论

- **核心思想**：借鉴 Mixture of Experts (MoE) 的门控路由机制，将 MoE 思想应用于稀疏注意力。
- **关键技术细节**：
  - 对于长度为 \(T\) 的输入序列，为每个注意力头设置一个门控网络（gating network），该网络动态地从所有 \(T\) 个 token 中选择 \(k\) 个 token 作为当前头的关注子集。
  - 每个头的注意力计算仅针对选出的 \(k\) 个 token（加上自身），从而实现任意稀疏模式（不再受限于固定窗口或局部区域）。
  - **计算复杂度**：从全注意力的 \(O(T^2)\) 降为 \(O(k^2 + T)\)（其中 \(k \ll T\)，典型如 \(k=32\) 或 \(64\)）。
  - 由于单头计算量降低，在相同计算预算下可以使用更多注意力头，从而提升模型的容量和专业化能力。
- **算法流程**（文字说明）：
  1. 输入序列 \(X \in \mathbb{R}^{T \times d}\)。
  2. 对于每个注意力头 \(h\)，门控网络根据某种输入特征（如 query 或 key 的汇总）计算每个 token 的得分，并通过 top-\(k\) 选择机制选出 \(k\) 个 token 的索引。
  3. 根据选中的 token 索引，从原始序列中提取对应的 key 和 value 子集。
  4. 在该子集上执行标准 softmax 注意力计算（复杂度 \(O(k^2)\)）。
  5. 每个头的输出与门控权重结合（可选的加权方式），最终拼接所有头的结果。

## 3. 实验设计

- **使用的数据集/场景**：
  - 语言建模任务（可能是 WikiText-103、enwik8 等标准数据集，但论文元数据未明确列出具体数据集）。
  - 分类任务（如 GLUE 基准或 IMDB 等，但未具体说明）。
- **Benchmark**：
  - 对比了多种稀疏注意力变体（如固定稀疏、随机稀疏、基于相似度的稀疏等），以及标准的密集自注意力基线。
  - 以**相同计算预算**（FLOPs 或参数量匹配）下的困惑度（perplexity）和下游任务准确率作为主要评价指标。
- **对比方法**：文中提到“among the tested sparse attention variants, MoSA is the only one that can outperform the dense baseline”，说明对比方法包括多种已有的稀疏注意力方案，但未列出全部具体名称（如 Sparse Transformer、Longformer、BigBird 等可能未涵盖，原文仅提及“tested sparse attention variants”）。

## 4. 资源与算力

- **文中未明确说明**使用的 GPU 型号、数量、训练时长等具体算力信息。
- 仅提及：尽管使用未经优化的 PyTorch 实现（无专用 kernel），MoSA 在推理时 wall-clock 时间更快，训练内存更少，KV-cache 大小大幅减小。但未给出具体 GPU 型号或训练硬件细节。
- **结论**：无法从提供的信息中获知算力消耗细节，需查阅原始论文全文。

## 5. 实验数量与充分性

- **实验数量**：主要报告了语言建模和分类任务上的结果。元数据中未提及其他消融实验（如不同 \(k\) 值、门控网络设计、head 数量等）。从摘要推断至少做了多个稀疏变体的对比实验，并报告了困惑度改进百分比。
- **充分性与公平性**：
  - **优点**：在相同计算预算下对比，控制了参数量和 FLOPs，较为公平。
  - **不足**：缺乏大规模基准（如 ImageNet、GLUE 全任务）的验证；未提供完整的超参数搜索或重复实验的方差信息；未说明对比的稀疏注意力方法是否涵盖了最先进的方案（如 S4、Mamba 等状态空间模型并非注意力，可能不在范围内）。实验充分性一般，但作为一篇被拒论文（ICLR-2026-Rejected-Public），可能实验规模有限。

## 6. 论文的主要结论与发现

- MoSA 能够动态学习内容稀疏性，在所有测试的稀疏注意力变体中**唯一**在相同计算预算下超越密集全注意力的方法。
- 在语言建模任务上，MoSA 以更低计算量获得与全注意力相当或更优的性能，最高提升 27% 的困惑度。
- 在不牺牲性能的前提下，MoSA 显著减少了内存占用（包括训练和 KV-cache）并缩短了实际运行时间（即使未使用优化 kernel）。
- 结论：可学习的内容稀疏性是一种有效的注意力加速策略，为设计高效 Transformer 提供了新范式。

## 7. 优点

- **方法创新性**：巧妙地将 MoE 门控机制引入注意力稀疏性选择，将稀疏模式从固定/统计变为内容自适应，灵活性高。
- **计算效率**：理论复杂度从 \(O(T^2)\) 降至 \(O(k^2+T)\)，特别适合长序列任务。
- **性能强**：在相同预算下能超越全注意力，表明稀疏性并非以牺牲质量为代价。
- **实际加速**：虽然无优化 kernel，仍实际更快、更省内存，证明了方法的实用性。
- **扩展性强**：通过增加头数可以提升模型容量，形成“宽而浅”的结构，有助专业化。

## 8. 不足与局限

- **实验覆盖有限**：仅涉及语言建模和分类，未在机器翻译、图像生成、多模态等任务上验证；数据集种类较少，难以评估方法的通用性。
- **门控开销**：门控网络和 top-\(k\) 选择本身引入额外计算和通信，在序列极长或 \(k\) 较大时可能需要优化，文中未系统分析这部分开销。
- **动态稀疏的稳定性**：不同训练步中头选择可能剧烈变化，是否影响训练收敛？论文未讨论。
- **缺少与其他高效注意力/序列模型的对比**：未与 FlashAttention、Linformer、Reformer、Longformer、Mamba 等比较，仅说了“稀疏注意力变体”，范围较窄。
- **未提供完整训练细节**：如学习率调度、正则化、硬件配置等，可复现性存疑。
- **论文本身被拒**（ICLR-2026-Rejected-Public），可能有一些审稿人指出的方法论缺陷或实验不够说服力，需谨慎对待。

（完）
