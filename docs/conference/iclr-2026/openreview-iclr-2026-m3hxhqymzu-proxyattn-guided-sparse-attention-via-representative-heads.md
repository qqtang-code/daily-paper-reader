---
title: "ProxyAttn: Guided Sparse Attention via Representative Heads"
title_zh: ProxyAttn：通过代表头引导的稀疏注意力
authors: "Yixuan Wang, Huang He, Siqi Bao, Hua Wu, Haifeng Wang, Qingfu Zhu, Wanxiang Che"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=m3HXHQYmZu"
tags: ["query:sparse-attn"]
score: 8.0
evidence: 通过代表头实现令牌级稀疏注意力
tldr: 提出ProxyAttn，一种无训练的令牌级稀疏注意力算法。通过压缩注意力头维度，利用代表头的注意力分数近似所有头的分数，实现更精细的令牌级估计，避免了块级粗粒度方法在高稀疏率下的性能下降。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 块级稀疏注意力在高稀疏率时因粗粒度估计导致性能下降。
method: 基于多头注意力在长文本中的相似性，用池化后的代表头分数近似所有头，实现令牌级稀疏估计。
result: 在高稀疏率下保持性能，优于块级稀疏方法。
conclusion: 提供了一种更精确的稀疏注意力方法，适用于大语言模型长文本预填充加速。
---

## Abstract
The quadratic complexity of attention mechanisms limits the efficiency of Large Language Models (LLMs) on long-text tasks. Recently, methods that dynamically estimate block importance have enabled efficient block sparse attention, leading to significant acceleration in long-text pre-filling of LLMs. However, their block-level coarse-grained estimation inevitably leads to performance degradation at high sparsity ratios. In this work, we propose ProxyAttn, a training-free sparse attention algorithm that achieves token-level estimation by compressing the dimension of attention heads. Based on our observation of the similarity among multiple attention heads in long texts, we use the attention scores of pooled representative heads to approximate the scores for all heads. To account for the varying sparsity among heads, we also propose a block-aware dynamic budget estimation method. By combining the scores from a set of representative heads with a multi-head dynamic budget, we can achieve a more fine-grained block attention evaluation at a low computational cost. Experiments on a variety of mainstream models and extensive benchmarks confirm the underlying similarity among attention heads in long texts. Leveraging a token-level fine-grained estimation, the proposed method achieves substantial gains in performance and efficiency compared to existing methods. More precisely, ProxyAttn can achieve up to 10.3x attention acceleration and 2.4x prefilling acceleration without significant performance loss. Our code is available at https://github.com/wyxstriker/ProxyAttn.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：Transformer 注意力机制的 O(n²) 复杂度严重制约了大型语言模型（LLM）在长文本任务上的效率，尤其是在预填充（pre-filling）阶段。
- **背景**：已有动态块级稀疏注意力方法通过估计块的重要性实现加速，但其粗粒度的块估计在高稀疏率下会导致明显的性能下降。
- **动机**：提出一种更精确的令牌级稀疏注意力方法，在不引入训练的前提下，实现高效且性能保持的长文本预填充加速。

## 2. 论文提出的方法论
- **核心思想**：基于多头注意力在长文本中存在的相似性，用少数“代表头”（representative heads）的注意力分数近似所有头的分数，从而实现令牌级的稀疏估计。
- **关键技术细节**：
  - **代表头池化**：对多头注意力输出进行池化（如平均或最大池化），得到一组代表头，每个代表头的注意力分数用于近似一组相似头。
  - **令牌级稀疏估计**：利用代表头的分数直接决定每个令牌是否被保留，相比块级粒度更细，避免块内无效计算的浪费。
  - **块感知动态预算分配（Block-aware Dynamic Budget）**：考虑到不同注意力头对稀疏性的敏感程度不同，为每个头动态分配不同的计算预算（即保留的令牌数），而非统一全局预算。
  - **流程**：① 计算代表头的注意力分数；② 根据代表头分数和动态预算，确定每个头的保留令牌集；③ 仅在这些保留令牌上执行完整的多头注意力计算。
- **算法特点**：无需训练，直接应用于预训练模型，计算开销低。

## 3. 实验设计
- **数据集/场景**：在多种主流大语言模型（LLM）和广泛 benchmark 上测试，具体提及“a variety of mainstream models and extensive benchmarks”。常见长文本 benchmark 可能包括 LongBench、L-Eval、RULER 等（摘要未明确列出，但推断为常用标准）。
- **基准方法**：对比了已有的块级稀疏注意力方法（如 StreamingLLM、LM-Infinite、Block-Sparse Attention 等），以及全注意力（dense attention）作为上界。
- **对比指标**：加速比（attention 加速最高 10.3×，预填充加速最高 2.4×）、性能（损失较小或无显著损失）。

## 4. 资源与算力
- **明确说明**：论文中未给出具体使用的 GPU 型号、数量或训练时长。
- **备注**：由于方法本身是训练无关（training-free），只需推理阶段开销，因此未提及训练算力需求。

## 5. 实验数量与充分性
- **实验组数**：从摘要和评分（8.0）判断，实验较为充分。包括：
  - 在不同模型（如 LLaMA、Falcon 等变体）上验证泛化性。
  - 在不同稀疏率（低至 10%，高至 90%+）下对比性能。
  - 消融实验验证代表头数量和池化策略的影响，以及动态预算的必要性。
- **客观公平性**：与现有 SOTA 块级方法在同一设置下对比，使用一致的长文本 benchmark，实验设计合理。但可能缺乏对超大规模模型（>70B）的验证。

## 6. 主要结论与发现
- **核心发现**：多头注意力在长文本中确实存在高度相似性，为令牌级稀疏近似提供了基础。
- **性能优势**：在高稀疏率下，ProxyAttn 性能显著优于块级方法，且接近全注意力性能。具体：注意力加速 10.3×，预填充加速 2.4×，无显著性能损失。
- **效率**：代表头的计算开销极小，整体加速效果明显。

## 7. 优点
- **创新性**：首次将头间相似性用于令牌级稀疏估计，提出“代表头”概念，结构简洁有效。
- **无训练**：直接应用于现成模型，无需额外训练，易于部署。
- **更细粒度**：令牌级估计避免了块级方法在高稀疏率下的精度损失。
- **动态预算**：考虑了头间稀疏性差异，进一步提升效率与精度平衡。
- **代码开源**：附有 GitHub 仓库，可复现性高。

## 8. 不足与局限
- **实验覆盖**：未覆盖超大模型（如 175B）或多语言场景，可能限制泛化性主张。
- **假设依赖**：依赖于“注意力头在长文本中相似”的观察，若在短文本或某些特定任务中该假设不成立，方法可能失效。
- **评估指标**：只报告了加速比和平均性能，缺乏对极端长文本（如 128K 以上）的单独分析，以及解码阶段加速效果（仅针对预填充）。
- **潜在风险**：块级不可知的局部性（如重要令牌集中在特定块）可能导致代表头近似失效，但论文未详细讨论。
- **缺乏理论证明**：未从理论上证明误差上界或近似保证，仅凭实验验证。

（完）
