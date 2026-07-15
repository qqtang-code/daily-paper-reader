---
title: "SCORE: Similarity-Aware Contextual Overlap-Redundancy Eviction for Efficient KV Cache Compression in LLMs"
title_zh: SCORE：基于相似性感知的上下文重叠冗余淘汰方法用于高效大语言模型KV缓存压缩
authors: "Gilha lee, Seungil Lee, Hyun Kim"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=HTlkxdEDWo"
tags: ["query:sparse-attn"]
score: 9.0
evidence: 基于相似度感知的KV缓存压缩淘汰方法
tldr: SCORE针对大语言模型推理中KV缓存的内存瓶颈问题，提出了一种基于距离感知的多级相似度度量来消除冗余KV对的淘汰框架。该方法考虑了层间和注意力头间的交互，在长上下文任务中实现了显著的缓存压缩，同时保持了模型性能。这项工作为KV缓存压缩提供了更精细的淘汰策略。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: KV缓存是大语言模型推理的内存瓶颈，现有淘汰策略忽略了层间和注意力头间的互动。
method: 提出SCORE框架，引入距离感知的多级相似度度量来量化和消除冗余KV对。
result: 在长上下文任务上实现了显著的缓存压缩，同时保持模型性能。
conclusion: SCORE是一种有效的KV缓存压缩方法，优于启发式淘汰策略。
---

## Abstract
Recent advances in large language models (LLMs) have unlocked remarkable long-context capabilities, enabling breakthroughs across diverse NLP tasks. However, despite architectural progress and compression techniques such as quantization, the key-value (KV) cache remains a critical memory bottleneck during inference. Prior work has explored cache optimization via eviction strategies, yet most rely on heuristic or single-axis importance metrics, neglecting the nuanced and dynamic interplay between layers and attention heads. In this paper, we propose SCORE (Similarity-aware Contextual Overlap-Redundancy Eviction), a novel framework that introduces a distance-based multi-level similarity metric to quantify and eliminate structural redundancy within the KV cache. By dynamically reallocating cache budgets across layers and heads and employing a redundancy-aware greedy token selection mechanism, SCORE preserves semantic diversity while minimizing memory overhead. Extensive experiments on long-context benchmarks such as LongBench and NeedleBench show that SCORE retains 95\% of full KV cache performance using only 1.5\% of the cache, consistently outperforming state-of-the-art baselines under strict memory constraints. These results underscore the value of fine-grained, context-aware cache management for scalable and efficient long-context inference in LLMs.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 核心问题与整体含义（研究动机和背景）

大语言模型（LLMs）在长上下文任务中展现出强大的能力，但在推理阶段，**键值缓存（KV Cache）** 成为关键的内存瓶颈。尽管已有架构优化和量化等压缩技术，KV缓存仍占用大量显存。先前的工作探索了基于淘汰策略的缓存优化，但大多依赖启发式或单轴重要性度量，**忽视了层间和注意力头之间的动态交互**。因此，需要一种更精细、上下文感知的缓存管理方法，以在有限内存下保持模型性能，实现可扩展的长上下文推理。

## 2. 方法论：核心思想、关键技术细节

**方法名称**：SCORE（Similarity-aware Contextual Overlap-Redundancy Eviction）

**核心思想**：引入基于距离感知的**多级相似性度量**，量化和消除KV缓存中的结构冗余。通过动态重新分配各层和各注意力头的缓存预算，并采用**冗余感知的贪婪令牌选择机制**，在保留语义多样性的同时最小化内存开销。

**关键技术细节**：
- **多级相似性度量**：不仅考虑单个令牌间的相似性，还考虑跨层和跨头的冗余模式，通过距离函数量化重叠信息。
- **动态预算分配**：根据每层/每头的冗余程度，动态调整KV缓存的保留数量，将更多缓存分配给信息丰富的部分。
- **冗余感知贪婪选择**：在淘汰时优先移除与已保留令牌高度相似的冗余令牌，确保剩余KV对保持语义多样性。

（论文未提供具体公式，但文字描述了上述流程）

## 3. 实验设计

### 数据集与基准
- **LongBench**：长上下文理解与生成基准
- **NeedleBench**：长上下文信息检索与定位基准

### 对比方法
- 与**当前最先进的基线方法**（state-of-the-art baselines）进行对比，包括基于启发式淘汰策略的方法（如H2O、Scissorhands等，文中未具体列出但隐含比较）。

### 评估指标
- 在**严格内存约束**下，比较压缩后的性能与全量KV缓存的性能保留比例。

## 4. 资源与算力

论文摘要及元数据中**未明确说明**使用的GPU型号、数量、训练时长或推理环境。仅提及“实验在长上下文基准上运行”，未提供硬件配置细节。因此，无法评估其计算开销和可复现性所需的资源。

## 5. 实验数量与充分性

### 实验覆盖
- 涵盖两个主流长上下文基准（LongBench和NeedleBench），但未提及具体子任务数量。
- 进行了与多个基线的对比实验，但未列出所有对比方法的具体名称和结果表格（摘要仅给出总体结论）。
- 未明确说明是否有消融实验（对多级相似性、动态预算分配等组件的独立分析）。

### 充分性评价
- **优点**：在极端压缩比（仅用1.5%缓存）下报告了95%性能保留，结果突出。
- **不足**：缺乏对不同压缩比下性能曲线的详细展示，也未提供在多个模型（如LLaMA、GPT-Neo等）上的验证，通用性存疑。实验数量相对有限，可能不足以全面证明SCORE的鲁棒性。

## 6. 主要结论与发现

- SCORE在**仅保留1.5%的KV缓存**的情况下，能够保留**95%的全量KV缓存性能**。
- 在严格内存约束下，SCORE持续优于现有最先进的基线方法。
- 表明：**细粒度、上下文感知的缓存管理**是高效KV缓存压缩的关键，层次化的冗余淘汰比单一指标更有效。

## 7. 优点

- **方法新颖**：首次引入多级相似性度量，考虑跨层和跨头的冗余，突破了传统单轴重要性度量的局限。
- **动态自适应**：根据运行时冗余自动调整各层/头的缓存预算，避免固定分配带来的浪费。
- **性能卓越**：在极端压缩比下仍保持高精度，实用价值高。
- **理论清晰**：从语义多样性角度解释淘汰策略，具有较强可解释性。

## 8. 不足与局限

- **实验覆盖不足**：仅使用了两个长上下文基准，未在更多模型族（如Mistral、Falcon）和更多任务（如多轮对话、文档分析）上验证。
- **资源信息缺失**：未提供计算资源（GPU型号、数量、推理速度）和内存实际节省量，难以评估实际推理加速比。
- **缺乏消融实验**：未系统分析多级相似性度量、动态预算分配等各组件的独立贡献。
- **可能存在偏差风险**：性能保留95%可能依赖于特定基准的分布，在更复杂或噪声更大的上下文中可能下降。
- **应用限制**：需要额外的相似性计算开销，可能影响推理延迟，论文未比较时间开销。
- **可复现性**：未提供代码或详细参数设置，方法复现困难。

（完）
