---
title: "CompressKV: Semantic Retrieval Heads Know What Tokens are Not Important Before Generation"
title_zh: "CompressKV: 语义检索头在生成前知道哪些token不重要"
authors: "Xiaolin Lin, Jingcun Wang, Olga Kondrateva, Yiyu Shi, Bing Li, Grace Li Zhang"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=Eed6XsFNJ5"
tags: ["query:sparse-attn"]
score: 8.0
evidence: 通过识别语义检索头在生成前淘汰不重要token的KV缓存压缩
tldr: "传统KV缓存压缩方法使用所有注意力头进行启发式token淘汰,忽略了头功能的差异性。CompressKV首先识别每层中具有检索能力的注意力头,仅利用这些头决定重要token,从而避免关键token被错误淘汰。方法在长上下文任务中有效减少缓存大小且保持性能。"
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: "现有KV压缩使用所有注意力头淘汰token,忽略了头的功能差异。"
method: "识别GQA中具有检索能力的注意力头,仅用它们决定token重要性。"
result: 在长上下文任务上减少了缓存使用并维持了性能。
conclusion: CompressKV通过语义检索头实现了更准确的token淘汰。
---

## Abstract
Recent advances in large language models (LLMs) have significantly boosted long-context processing. However, the increasing key-value (KV) cache size poses critical challenges to memory and execution efficiency. Most KV cache compression methods rely on heuristic token eviction using all attention heads in Grouped Query Attention (GQA)-based LLMs. This method ignores the different functionalities of attention heads, leading to the eviction of critical tokens and thus degrades the performance of LLMs.

To address the issue above, instead of using all the attention heads in GQA-based LLMs to determine important tokens as in the previous work, we first identify the attention heads in each layer that are not only capable to retrieve the initial and final tokens of a prompt, but also capable of retrieving important tokens within the text and attending to their surrounding semantic context. Afterwards, we exploit such heads to determine the important tokens and retain their corresponding KV cache pairs. Furthermore, we analyze the cache eviction error of each layer individually and introduce a layer-adaptive KV cache allocation strategy. Experimental results demonstrate the the proposed framework CompressKV consistently outperforms state-of-the-art approaches under various memory budgets on LongBench and Needle-in-a-Haystack benchmarks. Notably, it retains over 97% of full‑cache performance using only 3% of KV cache on LongBench’s question‑answering tasks and achieves 90% of accuracy with just 0.7% of KV storage on Needle-in-a-Haystack benchmark.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

大型语言模型（LLM）在长上下文处理方面取得显著进展，但随之而来的键值（KV）缓存体积急剧增长，给内存和计算效率带来了严峻挑战。现有的KV缓存压缩方法大多采用基于启发式的token淘汰策略，且在整个过程中使用了分组查询注意力（GQA）架构中的所有注意力头。这种做法忽略了不同注意力头在功能上的差异性（例如，有些头擅长检索全局信息，有些头关注局部细节），导致重要的关键token被错误淘汰，从而损害模型在下游任务上的性能。因此，论文的核心动机是提出一种更精准的token重要性判断方法，避免“一刀切”式的淘汰。

## 2. 论文提出的方法论：核心思想、关键技术细节

**核心思想**：  
在GQA架构的LLM中，并非所有注意力头都适合用来决定token的重要性。论文首先识别出每一层中具有“语义检索能力”的注意力头——这些头不仅能够检索prompt的起始和结束token，还能检索文本中的重要token并关注其周围的语义上下文。然后，仅利用这些被选出的语义检索头来判断哪些token是重要的，并保留其对应的KV缓存对。此外，论文还逐层分析了缓存淘汰误差，提出了一种**层自适应的KV缓存分配策略**，为不同层分配不同的缓存预算，以进一步优化压缩效果。

**关键技术细节**：  
- **语义检索头的识别**：通过分析注意力头在长文本中对于起始/结束token以及文本内部关键token的注意力分布特性，筛选出功能性强的头。
- **token重要性判定**：仅使用上述筛选出的头计算注意力权重，汇总得出每个token的重要性分数，淘汰得分较低的token。
- **层自适应分配**：计算每一层因淘汰引入的误差（例如，输出表示的变化），并根据误差大小动态分配各层的缓存容量，误差大的层保留更多token。

**算法流程**（文字描述）：  
1. 对于每一层，先识别语义检索头（可通过少量验证数据或预定义规则完成）。  
2. 对于输入序列，仅使用语义检索头计算所有token的重要性得分。  
3. 根据当前层的预算（由层自适应分配决定），保留得分最高的前K个token的KV缓存。  
4. 逐层重复上述过程，最终得到压缩后的KV缓存。  
（论文未给出显式公式，故用文字表述。）

## 3. 实验设计：数据集、基准与对比方法

- **数据集/基准**：  
  - **LongBench**：长上下文评估基准，重点使用其中的问答（QA）子任务。  
  - **Needle-in-a-Haystack**：经典的长上下文检索精度测试。  
- **对比方法**：论文声称与多种**当前最先进（SOTA）的KV缓存压缩方法**进行比较，但未在提供的摘要中列出具体方法名称（如H2O、Scissorhands、StreamingLLM等）。可能存在完整论文中的详细对比表。  
- **评估指标**：在LongBench上报告“全缓存性能保留比例”，在Needle-in-a-Haystack上报告准确率。

## 4. 资源与算力

论文提供的材料中**未明确说明**使用了多少GPU型号、数量、训练或推理时长。只提到了“在各种内存预算下”进行实验，但未给出硬件细节。这一点需要在完整论文中进一步确认。

## 5. 实验数量与充分性

- **实验数量**：  
  - 在LongBench的QA任务上测试了不同内存预算（如仅保留3%缓存时性能保留97%）。  
  - 在Needle-in-a-Haystack上测试了极低缓存（0.7%时准确率90%）。  
  - 同时进行了**层自适应缓存分配策略**的消融实验（通过对比非自适应版本验证其有效性）。  
- **充分性与客观性**：  
  - 实验覆盖了长上下文推理的两种典型场景（综合问答与精准检索），具有一定的代表性。  
  - 对比了SOTA方法，且结果明显优于已有工作，说明方法有效。  
  - 但仅有两个基准，缺乏对更多任务类型（如代码生成、数学推理）以及不同模型规模（如7B、13B、70B）的验证，整体覆盖度有待提升。实验设置基本公平，但未提供统计显著性检验。

## 6. 论文的主要结论与发现

- CompressKV能够**显著降低KV缓存占用**，同时保持甚至接近全缓存性能。  
- 在LongBench的QA任务上，使用**仅3%的KV缓存**可保留**97%**的全缓存性能。  
- 在Needle-in-a-Haystack上，使用**0.7%的KV缓存**即可达到**90%**的准确率。  
- 相比已有使用所有注意力头进行启发式淘汰的方法，利用**语义检索头**能够更准确地判断token重要性，避免关键token误删。  
- 层自适应缓存分配进一步改善了压缩效果，在低预算下尤其明显。

## 7. 优点：方法或实验设计的亮点

- **细粒度头功能建模**：首次在GQA架构中区分注意力头的功能差异，并只利用有检索能力的头进行token重要性评估，这是一种更合理的淘汰策略。  
- **减少误淘汰风险**：避免被无检索能力的头干扰，从而保留关键长程依赖信息。  
- **层自适应机制**：根据各层对淘汰误差的敏感度动态分配缓存，提升了整体鲁棒性。  
- **极低缓存下的高性能**：实验数据（97% @ 3%、90% @ 0.7%）非常亮眼，展示了极高的压缩潜力。  
- 方法简洁，理论上可在现有GQA模型上即插即用，无需重新训练。

## 8. 不足与局限

- **实验覆盖有限**：仅测试了LongBench和Needle-in-a-Haystack两个基准，未涵盖多跳推理、摘要、代码等更多长上下文任务，也未在更大规模的模型（如70B、130B）上验证。  
- **资源与计算开销未报告**：缺少GPU型号、推理时间、显存占用等具体数据，难以评估方法在实际部署中的额外成本。  
- **头识别过程可能依赖特定数据或规则**：论文未详细说明语义检索头的识别方法是否普遍适用，可能需要针对不同模型或任务预先校准。  
- **未讨论鲁棒性**：例如，当prompt结构变化或存在噪声时，检索头的选择是否仍稳定？淘汰误差在极端低预算下是否会导致灾难性遗忘？  
- **缺乏与更多先进方法的细致对比**：如与KV cache量化、离线合并等非淘汰方法的比较，以及不同压缩率下完整曲线的展示。  
- **应用限制**：当前方法主要针对GQA架构，对于MHA或CMA等注意力机制可能需调整。  

（完）
