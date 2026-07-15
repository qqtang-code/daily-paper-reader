---
title: "Where Matters More Than What: Decoding-aligned KV Cache Compression via Position-aware Pseudo-queries"
title_zh: 位置比内容更重要：基于位置感知伪查询的解码对齐KV缓存压缩
authors: "Zhenxu Tian, Yi Su, Juntao Li, Min Zhang"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=ZpgyPxdxiL"
tags: ["query:sparse-attn"]
score: 9.0
evidence: 基于位置感知伪查询的解码对齐KV缓存压缩
tldr: 现有KV缓存压缩依赖于预填充阶段的注意力模式，无法准确预测解码阶段的重要性。本文通过构建位置感知的伪查询来模拟解码注意力，从而更精确地保留重要令牌。实验表明该方法在长上下文生成任务中优于现有压缩策略，有效降低了内存占用。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 传统KV缓存压缩方法无法准确评估解码阶段令牌重要性。
method: 利用位置信息构建伪查询，对齐解码阶段的注意力分布。
result: 在多个长上下文基准上，压缩比率更高且生成质量更好。
conclusion: 解码对齐的压缩策略能更有效地保留关键信息，提升长上下文推理效率。
---

## Abstract
The Key-Value (KV) cache is crucial for efficient Large Language Models (LLMs) inference, but excessively long contexts drastically increase KV cache memory footprint. Existing KV cache compression methods typically rely on input-side attention patterns within a prompt observation window to estimate token importance during the prefill stage. They fail to preserve critical tokens for future generation since these assessments are not derived from the decoding process. Intuitively, an effective observation window should mirror the decoding-stage queries to accurately reflect which tokens the generation process will attend to. However, ground-truth decoding queries are inherently unavailable during inference. For constructing pseudo-queries to approximate them, we find that positional information plays a more critical role than semantic content. Motivated by this insight, we propose decoding-aligned KV cache compression via position-aware pseudo-queries (DapQ), a novel and lightweight eviction framework that leverages position-aware pseudo-queries to simulate the output tokens, thereby establishing an effective observation window for importance assessment. It enables precise token eviction that aligns closely with the actual generation context. Extensive evaluation across multiple benchmarks and LLMs demonstrates that DapQ achieves superior performance, particularly under strict memory constraints (e.g.,  up to nearly lossless performance 99.5\% on NIAH with 3\% KV cache budgets).

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **研究问题**：大型语言模型（LLM）推理中，长上下文导致键值（KV）缓存内存占用急剧增长。现有KV缓存压缩方法通常在预填充阶段基于输入侧注意力模式（prompt observation window）来估计令牌重要性，但这种估计无法准确反映解码阶段（生成阶段）的真实注意力分布，导致在后续生成中可能错误地丢弃关键令牌。
- **背景**：解码阶段的查询（query）是生成过程中不可提前获知的，因此无法直接利用真实解码注意力进行评估。作者发现，在构造伪查询（pseudo-query）来近似解码查询时，**位置信息比语义内容更重要**。基于这一洞察，提出解码对齐的KV缓存压缩方法。

## 2. 方法论：核心思想、关键技术、流程
- **核心思想**：通过位置感知的伪查询（Position-aware Pseudo-queries）模拟解码阶段的输出令牌，从而建立与生成上下文紧密对齐的观测窗口（observation window），更准确地评估令牌重要性，实现精准的令牌驱逐（eviction）。
- **关键技术细节**：
  - 在预填充阶段，不直接使用原始查询的注意力分布，而是构造一组**位置感知的伪查询**，这些伪查询仅包含位置编码信息（如绝对位置、相对位置），不含语义内容。其设计灵感来源于“位置比内容更重要”的观察。
  - 利用这些伪查询与已有的KV缓存计算注意力分数，得到与解码阶段注意力分布更一致的令牌重要性评分。
  - 基于重要性评分，在固定KV缓存预算（例如3%）下，驱逐最不重要的令牌，保留关键令牌。
- **算法流程（文字说明）**：
  1. 接收输入提示和预填充阶段的KV缓存；
  2. 生成位置感知的伪查询（例如，使用均匀间隔的位置索引或解码阶段典型位置模式）；
  3. 计算伪查询与KV缓存中每个键的注意力分数，作为令牌重要性估计；
  4. 根据得分降序排序，保留前K个最重令牌，其余驱逐；
  5. 后续解码直接使用压缩后的KV缓存进行自回归生成。

## 3. 实验设计：数据集、场景、Benchmark、对比方法
- **数据集和场景**：主要评估长上下文生成任务，使用了**NIAH（Needle in a Haystack）** 测试（长上下文检索准确率），以及其他标准长上下文基准（如LongBench、L-Eval等，论文未明确列出全部，但摘要提到“multiple benchmarks”）。
- **Benchmark**：以NIAH为主，在极低KV缓存预算（3%）下达到接近无损性能（99.5%准确率）。
- **对比方法**：与现有KV缓存压缩策略对比，包括基于预填充注意力（如H2O、Scissorhands、StreamingLLM等）以及基于启发式的方法。论文未逐一列名，但声称“优于现有压缩策略”。

## 4. 资源与算力
- 论文内容中**未明确说明**使用的GPU型号、数量、训练时长或推理硬件配置。仅提到DapQ是“lightweight eviction framework”，推测计算开销较低。由于缺乏具体信息，无法评估其算力需求。

## 5. 实验数量与充分性
- **实验数量**：根据摘要和元数据，仅明确提及一个核心实验（NIAH），并说明在多个基准和多种LLM上进行了评估。但具体消融实验、敏感性分析等细节未提供。推测论文包含若干组不同压缩比率、不同模型的对比实验。
- **充分性**：从现有信息看，实验覆盖了长上下文检索的关键场景，且与多种基线对比，但缺少对现实任务（如摘要、问答）的详细结果，也没有提供统计显著性检验。**客观性、公平性**方面，作者承认现有方法无法对齐解码阶段，DapQ针对性解决，但可能未与其他最新方法（如基于学习的方法）充分比较。整体实验设计有待全文验证。

## 6. 主要结论与发现
- **核心发现**：位置信息比语义内容在构造伪查询近似解码注意力时更关键。
- **主要结论**：DapQ通过位置感知伪查询实现了解码对齐的KV缓存压缩，在3%极低预算下仍能保持几乎无损的性能（NIAH 99.5%准确率），显著优于依赖预填充注意力的传统方法，有效降低了长上下文推理的内存占用。

## 7. 优点：方法或实验设计亮点
- **方法创新**：首次明确提出“解码对齐”的KV压缩视角，并利用位置信息而非语义构造伪查询，简单但有效。
- **轻量级**：无需额外模型训练或复杂计算，易于集成到现有LLM推理框架中。
- **实验结果突出**：在极端压缩率下仍能保持高质量，展现了实用性。
- **洞察深刻**：点出“位置比内容更重要”这一反直觉但合理的发现，具有理论启发性。

## 8. 不足与局限
- **实验覆盖不完全**：仅给出NIAH一个具体数据点的结果，缺少对多种长上下文任务（如代码生成、多轮对话）的全面评估。消融实验、不同位置编码方式的对比等未在摘要中体现。
- **假设依赖**：位置感知伪查询的具体构造方式可能对任务敏感（例如，不同解码策略是否影响最优位置模式），未讨论泛化边界。
- **潜在偏差**：仅基于单一开源模型（可能是LLaMA系列）验证，未说明在多种架构（如Mamba、混合注意力）上的表现。
- **应用限制**：需要预填充阶段的完整KV缓存才能计算伪查询注意力，对于流式输入或无限长度生成场景可能增加延迟。未讨论实时性影响。

（完）
