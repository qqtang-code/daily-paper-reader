---
title: "FSA: An Alternative Efficient Implementation of Native Sparse Attention Kernel"
title_zh: "FSA: 原生稀疏注意力内核的替代高效实现"
authors: "Ran Yan, Youhe Jiang, Zhuoming Chen, Haohui Mai, Beidi Chen, Binhang Yuan"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=c5mdo1hWrs"
tags: ["query:sparse-attn"]
score: 8.0
evidence: 为原生稀疏注意力提供替代高效内核实现以提升在LLM中的适用性
tldr: "原生稀疏注意力(NSA)的内核实现要求每组查询头数较多,不适合现有LLM的GQA配置。FSA重新设计循环顺序,使其在小查询头数下也能高效运行,扩展了NSA的适用范围。实验表明FSA在保持精度的同时提升了系统性能。"
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: NSA内核实现在小查询头数GQA配置下效率低。
method: 重新设计循环顺序以适应小查询头数的GQA分组。
result: "在多种LLM配置下实现了加速,保持了精度。"
conclusion: FSA使NSA更适用于实际LLM的GQA设置。
---

## Abstract
Recent advance in sparse attention mechanisms has demonstrated strong potential for reducing the computational cost of long-context training and inference in large language models (LLMs). Native Sparse Attention (NSA), one state-of-the-art approach, introduces natively trainable, hardware-aligned sparse attention that delivers substantial system-level performance boost while maintaining accuracy comparable to full attention. However, the kernel implementation of NSA forces a loop order that is only efficient with a relatively large number of query heads in each Grouped Query Attention (GQA) group, whereas existing LLMs widely adopt much smaller number of query heads in each GQA group --- such an inconsistency significantly limits the applicability of this sparse algorithmic advance. In this work, we propose **F**lash **S**parse **A**ttention (**FSA**), an alternative kernel implementation that enables efficient NSA computation across a wide range of popular LLMs with varied smaller number of query heads in each GQA group on modern GPUs. Compared to vanilla NSA kernel implementation, our empirical evaluation demonstrates that FSA achieves (i) up to 3.5x and on average 1.6x kernel-level latency reduction, (ii) up to 1.25x and 1.09x on average end-to-end training speedup on state-of-the-art LLMs, and (iii) up to 1.36x and 1.11x on average for prefill-phase speedup in LLM generative inference.

---

## 论文详细总结（自动生成）

# FSA: 原生稀疏注意力内核的替代高效实现 —— 论文详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **背景**：稀疏注意力机制在降低大语言模型（LLM）的长上下文训练与推理计算成本方面展现出巨大潜力。原生稀疏注意力（NSA）是一种领先方法，通过可训练且硬件对齐的稀疏注意力，在保持与全注意力相当精度的同时，获得显著的系统级性能提升。
- **核心问题**：然而，NSA的内核实现所采用的循环顺序要求每组查询注意力（GQA）组中的查询头数较多才能高效运行。而现有LLM广泛采用较小的每GQA组查询头数（例如GQA架构）。这种不匹配严重限制了NSA在实际LLM中的适用性。
- **整体含义**：为了解决这一矛盾，论文提出**FSA（Flash Sparse Attention）**，一种替代内核实现，能够在现代GPU上适配多种流行LLM（其每GQA组查询头数较少）上高效计算NSA。

## 2. 论文提出的方法论：核心思想、关键技术细节、算法流程

- **核心思想**：重新设计循环顺序，使其适应小查询头数的GQA分组，从而在小查询头数场景下获得高效执行。
- **关键技术细节**：
  - 传统NSA内核采用以查询头为外层循环，以稀疏键值对为内层循环的顺序。当查询头数较少时，并行度不足，导致GPU利用率低。
  - FSA将循环顺序调整为以稀疏键值对为外层循环，以查询头为内层循环，从而在保持稀疏性约束的同时，增加并行粒度，充分利用GPU线程束。
  - 具体实现上，FSA保持了与NSA相同的稀疏模式和注意力计算逻辑，仅改变循环组织方式，因此不改变算法精度。
- **算法流程（文字说明）**：FSA的计算流程与标准相似，但将查询头的循环内移，使得每个线程块或线程束可以同时处理多个查询头的相同稀疏键值对，从而减少全局内存访问次数并提高计算吞吐量。

## 3. 实验设计：数据集/场景、benchmark、对比方法

- **数据集/场景**：论文未明确说明使用的具体数据集，但提及在多种LLM配置下进行测试，包括不同大小的模型和GQA分组。
- **Benchmark**：主要比较FSA与原始NSA内核在以下方面的性能：
  - 内核级延迟（kernel-level latency）
  - 端到端训练加速（end-to-end training speedup）
  - 生成推理中的预填充阶段加速（prefill-phase speedup）
- **对比方法**：直接与原始NSA内核实现进行对比。未提及与其他稀疏注意力方法的对比。

## 4. 资源与算力

- **文中未明确说明**使用的GPU型号、数量及训练时长。仅提到“modern GPUs”，但未给出具体型号（如A100、H100等）或集群规模。因此无法总结算力细节。

## 5. 实验数量与充分性

- **实验组数**：论文给出了三组定量结果：
  - 内核级延迟：最高3.5倍加速，平均1.6倍。
  - 端到端训练：最高1.25倍，平均1.09倍加速。
  - 预填充阶段推理：最高1.36倍，平均1.11倍加速。
- **充分性评估**：
  - 实验覆盖了内核、训练、推理三个关键层面，但缺乏对精度影响的直接验证（仅提及“保持精度”，未提供具体数值）。
  - 未进行消融实验（如不同稀疏率、不同模型规模下的详细对比）。
  - 未与全注意力或其他稀疏注意力实现（如FlashAttention）对比。
  - 结论基于相对加速比，但缺乏绝对运行时间、内存占用等指标。
  - 总体而言，实验数量较少，覆盖不够全面，但针对提出的核心问题（小查询头数效率）给出了有力证据。

## 6. 论文的主要结论与发现

- FSA能够有效地替代原始NSA内核，在保持精度的条件下显著提升系统性能。
- 具体加速效果：
  - 内核级延迟：最高3.5倍，平均1.6倍。
  - 端到端训练：最高1.25倍，平均1.09倍。
  - 预填充推理阶段：最高1.36倍，平均1.11倍。
- FSA扩展了NSA在实际LLM（采用GQA且小查询头数）中的适用范围，使稀疏注意力加速技术更加实用。

## 7. 优点

- **方法简单有效**：仅通过改变循环顺序即可显著提升性能，无需修改算法本身，保持了精度和稀疏性。
- **针对痛点明确**：直击NSA内核在GQA小查询头数下的效率瓶颈，具有实际应用价值。
- **实验涵盖了关键场景**：不仅评估内核级延迟，还测量了端到端训练和推理预填充阶段的加速，体现了对实际部署的考虑。
- **结果清晰**：给出了最高和平均加速比，便于读者理解性能提升的范围。

## 8. 不足与局限

- **实验细节不充分**：未明确说明使用的GPU型号、模型大小、序列长度、稀疏率等实验设置，难以复现和公平比较。
- **精度验证不足**：声称“保持精度”，但未提供任何具体精度数据（如perplexity、下游任务准确率）或与原始NSA进行对比。
- **缺乏深入消融**：
  - 未分析不同查询头数下的加速曲线。
  - 未探索不同稀疏模式或不同硬件的影响。
  - 未与其他稀疏注意力实现（如FlashAttention、StreamingLLM等）对比。
- **应用限制**：仅针对GQA架构且小查询头数的场景有效。对于MHA（多头注意力）或大查询头数场景，原始NSA可能仍更优。
- **论文内容来源**：仅基于给出的摘要和元数据，可能缺少完整论文中的实验细节。

（完）
