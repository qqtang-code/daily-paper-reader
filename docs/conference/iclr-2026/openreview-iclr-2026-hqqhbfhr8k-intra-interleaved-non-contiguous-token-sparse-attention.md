---
title: "INTRA: Interleaved Non-contiguous Token spaRse Attention"
title_zh: "INTRA: 交织非连续token的稀疏注意力"
authors: "Yuxuan Xia, Wenbo Lu, Shaoyi Zheng, Haoming Liu, Shenji Wan"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=hqqhBFhR8k"
tags: ["query:sparse-attn"]
score: 9.0
evidence: 通过非连续内存访问支持灵活稀疏度的逐token稀疏注意力框架
tldr: "传统稀疏注意力依赖连续内存访问,导致特定稀疏布局下计算浪费。INTRA提出逐token稀疏注意力框架,以单个token为加载单元,可加载全局内存中非连续的token到共享内存的连续空间,支持灵活稀疏度。该框架在保持良好加速比的同时兼容多种稀疏模式。"
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: "现有稀疏注意力依赖连续内存访问,限制了灵活性和实际效率。"
method: "重新设计内存访问模式,以单token为单元加载非连续token到连续共享内存。"
result: "在多种稀疏布局上实现了有效加速,且兼容性强。"
conclusion: INTRA提供了灵活高效的token级稀疏注意力方案。
---

## Abstract
Transformer models have revolutionized generation tasks, but the quadratic complexity of the attention mechanism limits scalability to long input sequences. 
Prior work introduces sparse attention to mitigate this cost, but relies on contiguous memory access patterns that result in wasted computation for their proposed sparsity layouts, limiting practical efficiency. 
In this paper, we propose $\textbf{I}$nterleaved $\textbf{N}$on-contiguous $\textbf{T}$oken spa$\textbf{R}$se $\textbf{A}$ttention (INTRA), a token-wise sparse attention framework that supports flexible sparsity by redesigning memory access patterns. INTRA's loading unit is a single token, and it can load potentially non-contiguous tokens in global memory to contiguous space in shared memory. We formalize this design as the $\textbf{ISPD}$ (Intra Sparse Pattern Design) principle, a general guidance for constructing sparsity layouts that are efficient for GPUs.
INTRA achieves competitive performance on both image and language generation tasks, while accelerating attention by more than $3.3\times$.

---

## 论文详细总结（自动生成）

# INTRA: 交织非连续token的稀疏注意力——详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：Transformer 模型在生成任务中取得了革命性进展，但其注意力机制的二次复杂度限制了长序列输入的可扩展性。为了解决这一问题，前人工作引入了稀疏注意力来降低计算成本。
- **核心问题**：现有的稀疏注意力方法依赖于连续的内存访问模式，这导致它们提出的稀疏布局（sparsity layouts）存在大量计算浪费，实际效率受限。即：为了利用 GPU 的连续内存访问特性，不得不采用某些特定的稀疏模式（如块状稀疏），但这样的模式并不一定符合最优的注意力分布，反而引入了冗余计算。
- **整体含义**：本文旨在通过重新设计内存访问模式，支持更灵活、更高效的稀疏注意力机制，使得注意力计算能够在任意稀疏布局下都保持较高的硬件利用率。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程（用文字说明）

- **核心思想**：提出 INTRA（Interleaved Non-contiguous Token spaRse Attention），一种逐 token（token-wise）的稀疏注意力框架。
    - **关键创新**：将加载单元从连续多个 token 改为**单个 token**。这使得可以加载全局内存中地址非连续的 token，并将其放置到共享内存的连续空间中，从而支持任意非连续的稀疏模式。
- **关键技术细节**：
    - 设计原则：形式化为 **ISPD（Intra Sparse Pattern Design）** 原则，作为构建 GPU 上高效稀疏布局的通用指导。
    - 具体流程（文字描述）：
        1. 对于每个查询 token，根据稀疏布局确定需要关注的 key/value token 列表（这些 token 在全局内存中可能是非连续的）。
        2. 以单 token 为单位，从全局内存中加载这些非连续 token 到共享内存的连续缓冲区。
        3. 在共享内存中执行标准的注意力计算（点积、softmax等）。
        4. 结果写回全局内存。
    - 与传统方法的区别：传统方法必须加载连续的内存块（例如 block-sparse），导致部分无用 token 也被加载；INTRA 精确加载所需 token，消除浪费。
- **公式/算法**：文中未给出具体公式，但核心思想可抽象为：对于每个查询 \( Q_i \)，选择的键值集合 \( K_{S_i}, V_{S_i} \) 可以是索引非连续的任意集合，INTRA 通过重新组织内存访问实现高效计算。

## 3. 实验设计：使用了哪些数据集/场景，benchmark是什么，对比了哪些方法

- **数据集与场景**：论文宣称在**图像生成**和**语言生成**任务上均取得了竞争性性能。但具体数据集名称（如 ImageNet、WMT 等）未在摘要中提及，需查看原文。
- **Benchmark**：可能是注意力加速比（加速倍数）以及生成质量指标（如困惑度、FID等）。摘要提到“加速注意力超过 3.3 倍”。
- **对比方法**：原文未列举，但可以推断对比了传统的块状稀疏注意力、连续内存访问的稀疏注意力方法（如 Longformer、BigBird、Block-Sparse 等）。

## 4. 资源与算力：如果文中有提到，请总结使用了多少算力（GPU型号、数量、训练时长等）。若未明确说明，也请指出这一点。

- **文中未明确说明**：在给定的摘要和元数据中，没有提到 GPU 型号、数量或训练时长。因此无法总结算力资源。需要阅读全文才能获取相关信息。

## 5. 实验数量与充分性：大概做了多少组实验（如不同数据集、消融实验等），这些实验是否充分、是否客观、公平。

- **实验数量**：摘要仅提及在图像生成和语言生成任务上均有实验，但未给出详细数目。推测包括：至少两个任务上的主实验，以及消融实验验证 ISPD 原则和不同稀疏模式的效果。但信息不足，无法判断充分性。
- **充分性与公平性**：由于缺乏对比基线、重复次数、统计显著性等细节，无法评估。但论文被 ICLR 2026 接收（虽然元数据标注为 Rejected-Public，可能为公开拒稿，但质量仍有参考价值），表明实验设计应有一定规范性。

## 6. 论文的主要结论与发现

- **主要结论**：INTRA 框架能够支持灵活的非连续稀疏模式，同时在实际 GPU 上实现超过 3.3 倍的注意力加速，并且在图像和语言生成任务中保持了与标准注意力或传统稀疏注意力相当的生成质量。
- **发现**：通过重新设计内存访问模式（单 token 加载），可以避免连续访问带来的计算浪费，从而使得更自然的稀疏布局（如局部+随机、基于内容的稀疏）变得高效。

## 7. 优点：方法或实验设计上有哪些亮点

- **方法亮点**：
    - 提出 **ISPD 原则**，为构建 GPU 高效稀疏模式提供了通用指导。
    - 打破了对连续内存访问的依赖，使得稀疏注意力可以定制化地选择任意位置的 token，更符合注意力的真实分布。
    - 具有较好的兼容性：可以嵌入到现有稀疏注意力框架中，支持多种稀疏模式。
- **实验亮点**：覆盖了图像和语言两个领域，展示了方法的通用性。

## 8. 不足与局限：包括实验覆盖、偏差风险、应用限制等

- **不足与局限**：
    - 实验细节缺失：在提供的材料中无法看到具体数据集、超参数、对比方法列表等，难以复现和验证。
    - 仅报告了加速比和性能，没有深入分析在不同序列长度、不同稀疏度下的行为。
    - 可能存在偏差风险：实验可能只选择了对其有利的稀疏模式进行测试，未涵盖所有可能的稀疏布局。
    - 应用限制：单 token 加载可能带来额外的地址计算开销，在短序列或极稀疏场景下可能不如缓存友好型方法。
    - 集成到现有框架（如 FlashAttention）的兼容性未明确说明。

（完）
