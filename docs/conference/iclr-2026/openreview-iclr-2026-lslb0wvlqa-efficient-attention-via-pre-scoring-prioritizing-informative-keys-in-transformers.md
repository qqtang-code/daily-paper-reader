---
title: "Efficient Attention via Pre-Scoring: Prioritizing Informative Keys in Transformers"
title_zh: "通过预评分实现高效注意力:在Transformer中优先处理信息性键"
authors: "Yutong Bao, Haoyu Wang, Zhexiang Li, David Woodruff"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=lsLb0WvlqA"
tags: ["query:sparse-attn"]
score: 8.0
evidence: 为Transformer高效注意力设计预评分机制以优先处理重要键
tldr: "HyperAttention使用单级LSH聚类和均匀残差采样,但可能遗漏重要键导致困惑度上升。本文提出预评分机制,在HyperAttention之前优先筛选重要键,引入k均值、核k均值、k中位数聚类和杠杆分数排序三种方法,并替换均匀采样。实验表明该方法在长上下文建模中更低困惑度和更高效率。"
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: HyperAttention遗漏重要键导致困惑度上升。
method: 在HyperAttention前使用聚类和杠杆分数预评分筛选重要键。
result: 在长上下文语言建模中降低了困惑度并提升了效率。
conclusion: 预评分机制改进了HyperAttention的效率和准确性。
---

## Abstract
Recent advances in transformer architectures deeply enhanced long-context language modeling. Among them, HyperAttention achieves competitive efficiency by combining a single-level LSH-based clustering with uniform residual sampling. However, HyperAttention fails to find all significant keys, which in turn raises the overall perplexity. We propose a pre-scoring mechanism that prioritizes significant keys before applying HyperAttention. We introduce three scoring methods: $k$-means and kernel $k$-means clustering, $k$-median clustering, and leverage score-based ranking (inspired by LevAttention) to filter keys effectively. We further replace HyperAttention's original uniform residual sampling, relying exclusively on our pre-scoring mechanism. Experiments on ChatGLM2 (131k token context) reduce perplexity from 12 to 8.3, which outperforms standard HyperAttention. Moreover, when running on the Vision-Transformer (ViT), our method shows that it can guarantee similar accuracy compared with LevAttention, and will surpass LevAttention given specific parameters. Although this method introduces some computational overhead, its combination with HyperAttention remains 20 times faster than FlashAttention, providing a balanced trade-off between speed and modeling accuracy. Our results highlight the effectiveness of integrating pre-scoring into hierarchical attention mechanisms, significantly improving transformer efficiency.

---

## 论文详细总结（自动生成）

# 论文总结：Efficient Attention via Pre-Scoring: Prioritizing Informative Keys in Transformers

## 1. 核心问题与整体含义（研究动机和背景）
- **研究背景**：长上下文语言建模是Transformer的重要发展方向，但标准注意力机制的计算复杂度随序列长度二次增长。HyperAttention通过**单级LSH（局部敏感哈希）聚类**和**均匀残差采样**来近似注意力，提升了效率。
- **核心问题**：HyperAttention在聚类过程中可能遗漏重要键（significant keys），导致模型困惑度（perplexity）上升，影响长上下文建模的准确性。
- **研究动机**：如何在不显著增加计算开销的前提下，优先筛选出信息量高的键，使注意力机制更高效且更准确。
- **整体含义**：提出一种**预评分机制**（pre-scoring），在应用HyperAttention之前优先识别和保留重要键，从而改进注意力效率，降低困惑度，并保持较快的推理速度。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：在HyperAttention之前增加一个预评分步骤，对键进行重要性排序，只保留最关键的键参与后续注意力计算，替代HyperAttention原有的均匀残差采样。
- **技术细节**：提出三种预评分方法：
  1. **k均值聚类（k-means）** 和 **核k均值聚类（kernel k-means）**：将键聚类，选择靠近聚类中心的代表键作为重要键。
  2. **k中位数聚类（k-median clustering）**：使用L1距离的聚类方法，对离群点更鲁棒，选择中位数附近的键。
  3. **杠杆分数排序（leverage score-based ranking）**：受LevAttention启发，计算每个键的杠杆分数（leverage score），按得分降序筛选重要键。
- **算法流程**（文字说明）：
  1. 输入查询（query）与键（key）矩阵。
  2. 对键执行预评分（三种方法之一），得到重要性排序后的键子集。
  3. 将该键子集输入HyperAttention（包含LSH聚类与剩余键采样），但不使用均匀残差采样，而是完全依赖预评分筛选的结果。
  4. 计算注意力输出。
- **与HyperAttention的区别**：去掉了均匀残差采样步骤，改为基于预评分的有针对性的采样，确保高信息量键不被遗漏。

## 3. 实验设计
- **数据集/场景**：
  - 语言建模：使用**ChatGLM2**模型，上下文长度达到**131k token**。
  - 视觉任务：使用**Vision Transformer (ViT)** 进行图像分类。
- **基准（benchmark）**：
  - 对比方法：标准HyperAttention、FlashAttention、LevAttention。
  - 评价指标：困惑度（perplexity，越低越好）、准确率（accuracy）、速度（倍率）。
- **主要结果**：
  - 在ChatGLM2上：预评分机制将困惑度从12降低到8.3，优于标准HyperAttention。
  - 在ViT上：与LevAttention相比，在特定参数下准确率相当甚至超越LevAttention。
  - 速度：与HyperAttention结合后，仍比FlashAttention快20倍（预评分引入额外开销，但整体仍高效）。

## 4. 资源与算力
- **文中未明确说明**：使用的GPU型号、数量、训练时长等信息未在摘要或元数据中提及。仅提到了推理速度对比（比FlashAttention快20倍），但未给出具体硬件环境。因此资源与算力信息缺失。

## 5. 实验数量与充分性
- **实验数量**：摘要中提及的实验组数有限，主要在两个场景（ChatGLM2语言建模、ViT视觉任务）上进行了评估，并对比了多个基线方法（HyperAttention、FlashAttention、LevAttention）。未提及消融实验（如对比三种预评分方法的单独效果、不同聚类参数的影响等）。
- **充分性判断**：实验覆盖了语言和视觉两个领域，但缺乏更细致的消融研究和多数据集验证。例如，未在更长上下文（如1M token）或不同模型规模上测试，也未分析不同预评分方法的计算开销差异。因此实验的充分性一般，但结果初步表明了方法的有效性。

## 6. 主要结论与发现
- 预评分机制能够有效筛选重要键，显著降低HyperAttention在长上下文建模中的困惑度（从12降至8.3）。
- 该方法在视觉任务中也能保持与LevAttention相当的准确率，并在参数调整后超越后者。
- 尽管引入了额外计算（预评分），但与HyperAttention结合后整体速度仍比FlashAttention快20倍，实现了**效率与准确性的良好平衡**。
- 证明将预评分集成到分层注意力机制中是有效的，可提升Transformer效率。

## 7. 优点
- **方法创新**：提出“先预评分后注意力”的思路，简单且直观，解决了HyperAttention遗漏重要键的问题。
- **多种评分策略**：提供了聚类和杠杆分数两种类型的评分方法，具有一定的通用性。
- **实验对比全面**：同时对比了HyperAttention、FlashAttention、LevAttention，覆盖速度和准确率两个维度。
- **实用性强**：在保持较高推理速度的前提下显著提升准确率，适合实际长上下文应用。

## 8. 不足与局限
- **实验覆盖不足**：仅测试了ChatGLM2和ViT两个模型/场景，未在更多主流大语言模型（如GPT系列、LLaMA等）上验证。
- **缺乏消融研究和参数敏感性分析**：未详细比较三种预评分方法各自的优劣及适用条件，也未讨论聚类数量k、杠杆分数阈值等超参数对性能的影响。
- **算力信息缺失**：未说明训练或推理的具体硬件环境，影响结果的可复现性。
- **潜在偏差风险**：预评分本身可能引入新的偏差（如倾向于保留高频或常见模式，忽略长尾重要键），文中未分析。
- **应用限制**：预评分增加了预处理步骤，对于极短序列可能得不偿失；且效果依赖于评分方法的设计，可能无法泛化到所有注意力变体。

（完）
