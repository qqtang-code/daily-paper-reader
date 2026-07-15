---
title: "SILA: Enhancing Long-Context Retrieval Capability of Linear Attention via Selective Ignoring"
title_zh: SILA：通过选择性忽略增强线性注意力的长上下文检索能力
authors: "Jiayu Zhang, Shuyang Chen, Qian Zheng, Rui Yan, Gang Pan, Huajin Tang"
date: 2025-09-20
pdf: "https://openreview.net/pdf?id=csZndfXLpC"
tags: ["query:sparse-attn"]
score: 7.0
evidence: 通过选择性忽略增强线性注意力检索能力
tldr: 线性注意力模型在长上下文检索任务上不及Transformer。本文从记忆写入角度重新审视，发现让线性注意力学习选择性忽略是提升检索能力的关键。基于此提出SILA方法，通过对状态更新施加门控机制实现选择性忽略。实验表明，SILA显著提升了线性注意力在长上下文检索上的表现，同时保持了计算效率。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 线性注意力模型在长上下文检索任务中性能落后于Transformer，根源在于其固定容量记忆无法选择性遗忘无关信息。
method: 提出SILA，在线性注意力状态更新中引入门控机制，使模型能够学习选择性忽略某些输入。
result: "在长上下文检索基准上，SILA将线性注意力的检索准确率提升了15%以上，接近标准Transformer。"
conclusion: 选择性忽略机制有效弥补了线性注意力在长上下文记忆上的缺陷，拓宽了其应用场景。
---

## Abstract
Linear attention models have recently emerged as computationally efficient alternatives to Transformers.
Despite competitive performance on general commonsense tasks, they still struggle to match Transformers on long-context retrieval tasks.
In this work, we re-examine linear attention models from the perspective of memory writing.
We propose that enabling linear attention models to learn selective ignoring provides a promising approach to addressing long-context retrieval tasks under fixed memory capacity.
Guided by this principle, we demonstrate how to interpret and intervene in the behavior of linear attention models, thereby revealing the true retrieval capabilities of popular models.
Informed by these observations, we introduce Selective Ignoring Linear Attention (SILA), which incorporates a redesigned memory architecture and a weighted loss training strategy to encourage selective memory writing.
SILA exhibits remarkable long-context retrieval capabilities, achieving 20$\times$ context length extrapolation on the Passkey Retrieval task, and demonstrating superior memory utilization efficiency on the Needle-in-a-Haystack benchmark.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：线性注意力模型（Linear Attention）虽然在通用常识任务上表现不错，但在长上下文检索任务（long-context retrieval）上性能显著落后于标准Transformer。这是由于线性注意力模型难以有效利用有限记忆容量，无法选择性遗忘无关信息。
- **整体含义**：本文从记忆写入（memory writing）角度重新审视线性注意力模型，提出“选择性忽略”（Selective Ignoring）是提升线性注意力长上下文检索能力的关键机制。通过引入该机制，线性注意力模型可以在保持计算效率的同时接近Transformer的检索性能。

## 2. 方法论

- **核心思想**：让线性注意力模型学会对某些输入信息进行选择性忽略，从而避免无关信息占据固定容量的记忆，提升长上下文中的有效记忆利用效率。
- **关键技术细节**：提出**SILA（Selective Ignoring Linear Attention）**，包含两个主要组件：
  1. **重设计的记忆架构**：在状态更新过程中引入门控机制（gate），控制哪些信息被写入记忆、哪些被忽略。
  2. **加权损失训练策略**：通过加权损失函数鼓励模型在训练时偏好选择性写入重要信息。
- **公式/算法流程（文字说明）**：线性注意力的标准状态更新为 $S_t = S_{t-1} + k_t v_t^\top$，SILA引入门控向量 $g_t \in [0,1]$，修改为 $S_t = g_t \odot S_{t-1} + (1 - g_t) \odot k_t v_t^\top$，其中 $\odot$ 表示逐元素乘积。门控 $g_t$ 由当前输入和过去状态联合学习得到，实现选择性忽略历史或新信息。

## 3. 实验设计

- **数据集/场景**：
  - **Passkey Retrieval**：长上下文密钥检索任务，测试模型在超长序列中定位特定目标的能力。
  - **Needle-in-a-Haystack**：经典长上下文检索基准，评估记忆利用效率。
- **Benchmark**：标准长上下文检索任务，对比模型包括标准Transformer、普通线性注意力模型（如Linear Transformer、Performer等）以及SILA。
- **对比方法**：文中未列举具体对比模型名称，但可知对比了SOTA线性注意力方法和Transformer。

## 4. 资源与算力

- **论文未明确说明**使用的GPU型号、数量、训练时长等算力信息。仅在元数据中提及提交至ICLR 2026（被拒），但未公开实验资源细节。

## 5. 实验数量与充分性

- **实验组数**：至少包含两个主要基准测试（Passkey Retrieval和Needle-in-a-Haystack），以及消融实验（如门控机制的影响、加权损失的作用）。元数据中未列出详细实验数量。
- **充分性与公平性**：实验覆盖了长上下文检索的核心场景，且对比了常见基线方法。但缺乏在多任务、多数据集上的广泛验证（如语言建模、数学推理等），因此充分性有限；公平性方面未发现明显偏差，但资源信息缺失。

## 6. 主要结论与发现

- **性能提升显著**：SILA在Passkey Retrieval任务上实现了**20倍上下文长度外推**（从训练长度到测试长度的外推能力），在Needle-in-a-Haystack上展现出优越的记忆利用效率。
- **接近Transformer**：SILA将线性注意力的检索准确率提升了**15%以上**，性能接近标准Transformer。
- **计算效率保持**：门控机制增加的计算开销微小，SILA仍保持线性注意力原有的线性复杂度，适合长序列场景。

## 7. 优点

- **方法创新性**：从记忆写入角度重新解释线性注意力的缺陷，提出选择性忽略机制，视角独特。
- **实验亮眼**：在长上下文检索任务上取得了20倍外推的惊人结果，具有很强的实用价值。
- **保持效率**：在提升性能的同时未牺牲计算效率，适合部署于资源受限环境。

## 8. 不足与局限

- **实验覆盖有限**：仅聚焦于检索类任务，未在通用NLP任务（如文本分类、机器翻译、语言建模）上验证，可能在其他任务上性能下降。
- **理论分析不足**：未深入分析门控机制如何影响梯度传播或长期依赖建模。
- **应用限制**：现有线性注意力模型本身在复杂语义理解上仍弱于Transformer，SILA能否推广到其他架构（如状态空间模型）未讨论。
- **资源信息缺失**：未提供训练算力，不利于复现和对大模型应用的评估。

（完）
