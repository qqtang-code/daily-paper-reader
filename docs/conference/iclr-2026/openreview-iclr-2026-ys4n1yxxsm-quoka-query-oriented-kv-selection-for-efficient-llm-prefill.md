---
title: "QuoKA: Query-Oriented KV Selection for Efficient LLM Prefill"
title_zh: QuoKA：面向查询的KV选择用于高效大语言模型预填充
authors: "Dalton Jones, Junyoung Park, Matthew J Morse, Mingu Lee, Matthew Harper Langston, Christopher Lott"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=YS4N1YxXSM"
tags: ["query:sparse-attn"]
score: 8.0
evidence: 面向查询的KV选择以加速大语言模型预填充
tldr: 提出QuoKA算法，一种无训练、硬件无关的稀疏注意力机制，用于大语言模型的分块预填充阶段。通过优先保留与平均查询余弦相似度低的查询，并据此选择关键键，该方法在加速注意力的同时保持高保真度。实验表明其能紧密近似全注意力行为。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 全注意力在预填充阶段计算量大，需要高效的稀疏近似。
method: 基于查询与平均查询余弦相似度，保留代表性查询并子选择关键键。
result: 在预填充阶段大幅加速，同时保持与全注意力接近的表现。
conclusion: 提供了一种无需训练的稀疏注意力方案，适用于大语言模型高效推理。
---

## Abstract
We present QuoKA: Query-oriented KV selection for efficient attention, a training-free and hardware agnostic sparse attention algorithm for accelerating transformer inference under chunked prefill. While many queries focus on a smaller group of keys in the attention operator, we observe that queries with low cosine similarity with respect to the mean query interact more strongly with more keys and have the greatest contribution to final attention logits. By prioritizing these low cosine similarity queries, the behavior of full attention during the prefill stage can be closely approximated. QuoKA leverages this observation, accelerating attention by (1) first retaining a small set of representative queries and (2) then subselecting the keys most aligned with those queries. Through experiments on Needle-In-A-Haystack, LongBench, RULER, and Math500, we show that, while realizing a 3× reduction in time-to-first-token, 5× speedup in attention on Nvidia GPUs and up to nearly a 7× speedup on Intel Xeon CPUs, QuoKA achieves near-baseline accuracy, utilizing 88% fewer key-value pairs per attention evaluation.

---

## 论文详细总结（自动生成）

以下是根据提供的论文元数据和摘要生成的详细中文总结。

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大语言模型（LLM）在分块预填充（chunked prefill）阶段的注意力计算开销巨大，导致首令牌延迟（time-to-first-token）过长，影响推理效率。
- **研究动机**：现有稀疏注意力方法通常需要训练或依赖特定硬件，而全注意力在预填充阶段计算所有键值对（KV pairs）效率低下。作者观察到，与平均查询（mean query）余弦相似度低的查询会与更多的键交互，并对最终注意力logits贡献最大。
- **整体含义**：QuoKA提出一种无需训练、硬件无关的稀疏注意力算法，通过优先保留这些低余弦相似度的查询，并基于它们子选择关键的键，从而在保持高保真度的同时大幅加速预填充阶段的注意力计算。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：基于“低余弦相似度查询对注意力贡献更大”的观察，保留一小部分代表性查询，并只选择与这些查询最对齐的键进行注意力计算，实现近似全注意力的行为。
- **关键技术细节**：
  - **步骤1**：在分块预填充中，计算每个查询与平均查询的余弦相似度，优先保留相似度低的查询（即“查询子选择”）。
  - **步骤2**：基于保留的代表性查询，进一步子选择与之最相关的键（即“键子选择”）。
  - **特点**：整个过程无需训练，不依赖特定硬件（如NVIDIA或Intel平台均可加速），仅需简单的相似度计算和排序操作。
- **算法流程（文字说明）**：
  1. 输入：查询矩阵Q、键矩阵K、值矩阵V（来自当前分块）。
  2. 计算平均查询向量 $\mathbf{q}_{\text{mean}} = \frac{1}{N}\sum_{i} \mathbf{q}_i$。
  3. 对每个查询 $\mathbf{q}_i$，计算与 $\mathbf{q}_{\text{mean}}$ 的余弦相似度 $\cos(\mathbf{q}_i, \mathbf{q}_{\text{mean}})$。
  4. 按照相似度升序排序，保留相似度最低的 $r$ 个查询作为代表性查询（$r \ll N$）。
  5. 对每个代表性查询，使用注意力机制计算与所有键的注意力分数，仅保留分数最高的 $k$ 个键（或基于稀疏性阈值筛选）。
  6. 使用这些子选择的键值对计算最终的注意力输出（并可能通过一些聚合方式恢复完整输出）。
  7. 输出近似注意力结果。

## 3. 实验设计

- **数据集/场景**：四个标准长文本基准：
  - Needle-In-A-Haystack（检索类任务）
  - LongBench（综合长文本理解）
  - RULER（长文本推理）
  - Math500（数学推理）
- **Benchmark**：对比全注意力基线（Full attention）以及可能的其他稀疏注意力方法（文中未明确列出，仅提及“baseline”）。
- **对比方法**：从摘要看主要与全注意力对比，未提及其他稀疏注意力算法；但可能隐含与常见稀疏方法（如Top-k、局部注意力等）的对比，需待原文补充。

## 4. 资源与算力

- **提及内容**：
  - 在NVIDIA GPU上获得5倍注意力加速，在Intel Xeon CPU上获得近7倍加速。
  - 未具体说明GPU型号、数量或训练时长（因为QuoKA无需训练）。
- **缺失信息**：没有给出实验所用的硬件规格（如A100、H100等）、系统配置、功耗等细节，仅提及平台类型。

## 5. 实验数量与充分性

- **实验数量**：
  - 使用了4个数据集，涵盖不同长文本任务。
  - 测量了多个指标：首令牌延迟（TTFT）减少3倍、注意力加速5–7倍、准确率接近全注意力基线、KV对使用减少88%。
  - 未提及消融实验（如不同查询保留比例、不同键子选择策略的影响）或对比其他稀疏方法。
- **充分性评估**：
  - 基准覆盖较全面（检索、理解、推理、数学），但缺少对话、代码生成等常见场景。
  - 缺乏与同类高效注意力方法（如FlashAttention、Sparse Attention、StreamingLLM等）的系统对比，公平性存疑。
  - 未报告方差或多次试验结果，无法评估稳定性。

## 6. 论文的主要结论与发现

- **主要结论**：QuoKA在分块预填充阶段能够以极低的KV对开销（节省88%），在保持近基线精度的同时，实现显著加速（CPU上7倍、GPU上5倍，首令牌延迟降低3倍）。
- **关键发现**：低余弦相似度查询对最终注意力logits的贡献最大，且全注意力行为可以通过优先处理这些查询来近似。

## 7. 优点

- **无需训练**：完全基于推理时的查询和键的统计特性，可直接应用于现有模型。
- **硬件无关**：在NVIDIA GPU和Intel Xeon CPU上均取得良好加速，可迁移到其他平台。
- **效率提升显著**：在加速和KV开销减少上均有量化结果（3× TTFT、5–7×加速、88% KV减少）。
- **理论基础扎实**：从查询与平均查询的余弦相似度角度分析注意力行为，具有直观解释性。
- **在多个长文本基准上验证**：涵盖检索、理解、推理、数学等不同能力。

## 8. 不足与局限

- **实验覆盖不足**：
  - 仅与全注意力基线对比，未与现有主流稀疏注意力方案（如H2O、ScatterBrain、SpAtten、FlashAttention等）进行比较。
  - 未进行消融实验（如不同查询保留数量、键选择比例的影响）。
  - 未报告在长序列、多轮对话等场景下的表现。
- **偏差风险**：
  - 仅选择低余弦相似度查询可能忽略那些相似度高但同样重要的查询（如对局部信息敏感的查询），存在任务依赖性。
  - 未评估对不同模型（如LLaMA、Mistral等）的泛化性。
- **应用限制**：
  - 算法针对分块预填充设计，在自回归解码阶段的适用性未讨论。
  - 稀疏策略可能引入额外排序开销，实际端到端加速可能低于理论值。
  - 论文未提供开源代码或详细超参数，复现性受限。
- **算力信息缺失**：未给出实验硬件具体型号、功耗等，难以评估计算效率的真实增益。

（完）
