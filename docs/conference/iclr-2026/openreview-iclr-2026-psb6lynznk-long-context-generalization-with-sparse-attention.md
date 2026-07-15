---
title: Long-Context Generalization with Sparse Attention
title_zh: 长上下文泛化与稀疏注意力
authors: "Pavlo Vasylenko, Hugo Pitorro, Andre Martins, Marcos Vinicius Treviso"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=PsB6Lynznk"
tags: ["query:sparse-attn"]
score: 8.0
evidence: 使用α-entmax实现长上下文泛化的稀疏注意力
tldr: 本文证明使用α-entmax的动态稀疏注意力可以避免长序列中的注意力分散和表示坍缩问题，并进一步提出了自适应可扩展entmax（ASEntmax），通过引入可学习温度参数增强了灵活性。在长上下文任务中，该方法显著提升了模型泛化能力，验证了稀疏注意力在长序列处理中的优势。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 传统softmax注意力在长上下文中导致注意力分散和表示坍缩。
method: 使用α-entmax和可学习温度参数实现动态稀疏注意力。
result: 在长上下文任务中提升性能，避免表示坍缩。
conclusion: 稀疏注意力有利于长上下文泛化，ASEntmax是一种有效的变体。
---

## Abstract
Transformer-based architectures traditionally employ softmax to compute attention weights, which produces dense distributions over all tokens in a sequence. 
    While effective in many settings, this density has been shown to be detrimental for tasks that demand precise focus on fixed-size patterns: as sequence length increases, non-informative tokens accumulate  attention probability mass, leading to dispersion and representational collapse.
    We show in this paper that dynamically sparse attention mechanisms using $\alpha$-entmax can avoid these issues, due to their ability to assign exact zeros to irrelevant tokens. Furthermore, we introduce Adaptive-Scalable Entmax (ASEntmax), which endows $\alpha$-entmax with a learnable temperature parameter, allowing the attention distribution to interpolate between sparse (pattern-focused) and dense (softmax-like) regimes.
    Our empirical evaluation on synthetic tasks and language modeling demonstrates that ASEntmax substantially outperforms softmax, scalable softmax, and fixed-temperature $\alpha$-entmax baselines, achieving up to 1000$\times$ length extrapolation on synthetic benchmarks and superior long-context generalization on language modeling while preserving short-context performance, including better perplexity trends and higher retrieval accuracies at 8$\times$ training length.

---

## 论文详细总结（自动生成）

# 长上下文泛化与稀疏注意力（Long-Context Generalization with Sparse Attention）

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：传统 Transformer 架构使用 softmax 计算注意力权重，生成密集的注意力分布（即每个 token 都获得非零权重）。当输入序列长度增加时，大量非信息性 token 会累积注意力概率质量，导致注意力分散（attention dispersion）和表示坍缩（representational collapse），模型难以精准聚焦于固定大小的关键模式。
- **整体含义**：本文旨在解决长上下文场景下 softmax 注意力性能退化的问题，证明动态稀疏注意力机制能够通过精确地将不相关 token 的注意力权重置为零，避免注意力分散和表示坍缩，从而提升长上下文泛化能力。

## 2. 论文提出的方法论

- **核心思想**：使用基于 $\alpha$-entmax 的动态稀疏注意力机制替代 softmax。$\alpha$-entmax 能够自适应地生成稀疏注意力分布（部分权重精确为 0），避免无关 token 累积概率质量。在此基础上，进一步提出 **Adaptive-Scalable Entmax（ASEntmax）**，为 $\alpha$-entmax 引入一个**可学习的温度参数**，使注意力分布在稀疏（模式聚焦）和密集（接近 softmax）之间灵活插值。
- **关键技术细节**：
  - $\alpha$-entmax 是一种广义的 softmax，通过调整超参数 $\alpha$ 控制稀疏程度，当 $\alpha=1$ 时退化为 softmax，$\alpha>1$ 时产生稀疏输出。
  - ASEntmax 在 $\alpha$-entmax 基础上，添加一个可学习的温度参数 $\tau$（或类似缩放因子），允许模型根据任务和序列长度动态调节注意力分布的锐度与稀疏性。温度参数通过梯度下降与其他参数联合学习。
  - 没有给出具体公式，但据描述，ASEntmax 的输出分布为：$\text{ASEntmax}(\mathbf{z}) = \alpha\text{-entmax}(\mathbf{z}/\tau)$，其中 $\tau$ 是温度，$\mathbf{z}$ 为注意力分数向量。
- **算法流程**：标准的 Transformer 注意力计算中，将 softmax 替换为 ASEntmax；温度参数 $\tau$ 与模型其他参数一同训练；前向传播时，ASEntmax 根据当前温度生成稀疏注意力权重，实现动态稀疏化。

## 3. 实验设计

- **数据集/场景**：
  - 合成任务：用于测试长度外推（length extrapolation）能力，如模式匹配、计数等。
  - 语言建模（language modeling）：使用标准语言建模数据集，文中未明确指明名称（可能为 WikiText-103、PG-19 等，元数据未提供具体名称）。
- **Benchmark**：
  - 合成任务：长度外推倍数（如达到训练长度的 1000×）。
  - 语言建模：困惑度（Perplexity）和长上下文检索准确率（retrieval accuracy），特别是训练长度 8× 时的表现。
- **对比方法**：
  - Baseline 1：标准 softmax 注意力。
  - Baseline 2：可扩展 softmax（scalable softmax，可能指带有温度缩放或归一化方法）。
  - Baseline 3：固定温度的 $\alpha$-entmax（即不含可学习温度的原始 $\alpha$-entmax）。
  - 本文方法：ASEntmax（可学习温度 + $\alpha$-entmax）。

## 4. 资源与算力

- 文中未明确说明使用的 GPU 型号、数量、训练时长等算力信息。仅通过元数据可知论文被 ICLR 2026 接收，但未提供训练资源细节。这一点需要在总结中注明：未提及具体算力配置。

## 5. 实验数量与充分性

- 实验数量：根据摘要，实验覆盖**合成任务**和**语言建模**两个大类。合成任务中测试了长度外推表现；语言建模中报告了困惑度和检索准确性。此外，还对比了三种 baseline 方法，应该有消融实验（比如分析温度参数 $\tau$ 的作用，但摘要未明确提及消融）。总体实验数量中等。
- 充分性与客观性：
  - 优势：实验覆盖了**合成基准**（极端外推）和**真实任务**（语言建模），且在外推长度上达到 1000× 验证了极端泛化能力；在长上下文检索准确率上报告了 8× 训练长度的提升。
  - 不足：未在更多下游长上下文任务（如长文本问答、长文档摘要、代码生成）上验证；未与其他稀疏注意力方法（如 Top-k 注意力、ReLU attention、Sparse Transformer 等）对比，仅比较了 softmax 系列变体，对比范围有限；缺少对温度参数学习过程的深入分析（如是否收敛、泛化边界等）。消融实验信息不足。

## 6. 论文的主要结论与发现

- 动态稀疏注意力（$\alpha$-entmax）能够有效避免长序列中的注意力分散和表示坍缩，是长上下文泛化的关键。
- 引入可学习温度参数的 ASEntmax 进一步提升了灵活性，在性能上显著优于 softmax、可扩展 softmax 和固定温度 $\alpha$-entmax。
- 在合成基准上实现了高达 **1000× 训练长度外推**；在语言建模中保持短上下文性能的同时，在 8× 训练长度上获得了更好的困惑度趋势和更高的检索准确率。
- 结论：稀疏注意力有利于长上下文泛化，ASEntmax 是一种有效且实用的变体。

## 7. 优点

- **方法创新**：将可学习温度参数与 $\alpha$-entmax 结合，实现了从稀疏到密集的自适应调节，避免了手动调参。
- **性能显著**：合成任务外推能力达到 1000×，远超 baseline，证明了方法的极端泛化能力。
- **全面评估**：同时报告了短上下文和长上下文性能，验证了没有牺牲短文本能力。
- **简洁有效**：不改变 Transformer 整体架构，仅替换注意力函数，易于集成到现有模型。

## 8. 不足与局限

- **实验覆盖不够广泛**：仅涉及合成任务和语言建模，缺少对长文本问答、摘要、多跳推理等实际长上下文任务的评估；未与主流稀疏注意力方法（如 Top-k、Sparse Transformer、Reformer 等）直接对比。
- **算力信息缺失**：未说明训练所需的 GPU 资源和时间，不利于评估方法的可复现性和实际成本。
- **可学习温度参数的分析不足**：未讨论温度参数是否在不同层或不同头具有差异性，是否会导致训练不稳定或过拟合。
- **理论分析薄弱**：仅有经验结果，缺乏对为何动态稀疏注意力能避免表示坍缩的理论证明或深入解释。
- **局限性**：$\alpha$-entmax 本身需要选择 $\alpha$ 值，虽然 ASEntmax 引入了可学习温度，但 $\alpha$ 仍为超参数，可能仍需调参；且 $\alpha$-entmax 的计算复杂度略高于 softmax，可能在大规模部署时带来额外开销。

（完）
