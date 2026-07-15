---
title: "SSD: Spatial-Semantic Head Decoupling for Efficient Autoregressive Image Generation"
title_zh: "SSD: 用于高效自回归图像生成的空间-语义头解耦"
authors: "Siyong Jian, Huan Wang"
date: 2025-09-03
pdf: "https://openreview.net/pdf?id=lfO9M3dTVS"
tags: ["query:sparse-attn"]
score: 7.0
evidence: 利用空间和语义注意力模式的自回归图像生成KV缓存压缩
tldr: "自回归图像生成任务中视觉token的KV缓存压缩尚未被充分探索。SSD识别出空间局部性和涌现语义汇点两种注意力现象,通过将注意力头解耦为两类来压缩视觉token的KV缓存:空间局部性头保留近期窗口,语义汇点头保留紧凑集合。实验表明该方法在图像生成中有效降低内存并保持质量。"
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: "自回归图像生成中大量视觉token导致高内存和计算需求,现有KV缓存压缩集中在语言建模。"
method: "解耦注意力头为空间局部性和语义汇点两类,分别采用不同压缩策略。"
result: 在图像生成任务上显著降低KV缓存内存并保持生成质量。
conclusion: SSD为图像生成中的KV缓存压缩提供了有效框架。
---

## Abstract
Autoregressive image generation models like Janus-Pro produce high-quality images, but at the cost of high memory and computational demands due to the large number of visual tokens. 
While KV cache compression has been extensively studied in language modeling, it remains largely unexplored for image generation.

In this work, we begin by identifying a distinct attention phenomenon, which we term spatial locality and emergent semantic sink. 
To leverage this, we introduce a novel KV cache compression framework. 
Specifically, we compress the KV cache for visual tokens by decoupling attention heads into two types: for spatial-locality heads, our method maintains a short recent token window; for semantic-sink heads, it preserves a compact set of highly-attended tokens. 
Experiments demonstrate that our method achieves a 5$\times$ reduction in memory usage and a 6.6$\times$ speedup in throughput with negligible performance loss, enabling efficient native autoregressive image generation.

---

## 论文详细总结（自动生成）

# 论文总结

## 1. 核心问题与整体含义  
- **研究动机**：自回归图像生成模型（如 Janus-Pro）虽然能生成高质量图像，但由于生成过程依赖大量视觉 token，导致内存和计算需求高昂。现有 KV 缓存压缩技术主要针对语言建模领域，在图像生成任务中尚未得到充分探索。  
- **整体含义**：本文提出一种利用视觉注意力特有模式来压缩 KV 缓存的框架，旨在降低自回归图像生成的内存占用和延迟，同时保持生成质量，使原生自回归图像生成更加高效。

## 2. 方法论  
- **核心思想**：识别并利用两种独特的注意力现象——**空间局部性**（spatial locality）和**涌现语义汇点**（emergent semantic sink）。  
- **关键技术细节**：  
  - 将多头注意力的各个头解耦为两类：  
    - **空间局部性头**：在解码时仅保留最近一小段窗口内的视觉 token 的 KV 缓存。  
    - **语义汇点头**：保留一个紧凑的、被高度关注的 token 集合（即“语义汇点”），这些 token 在生成过程中始终受到强关注。  
  - 不同类别的注意力头采用不同的压缩策略，从而在不显著影响生成质量的前提下大幅减少 KV 缓存大小。  
- **算法流程**（文字说明）：  
  1. 离线分析注意力模式，将注意力头分为空间局部性头和语义汇点头。  
  2. 在推理阶段，对空间局部性头只缓存当前最近的 N 个 token，对语义汇点头只缓存一个预先筛选出的压缩 token 集。  
  3. 其他注意力操作不变，整体生成过程维持自回归顺序。

## 3. 实验设计  
- **数据集/场景**：文中未明确指出使用的具体数据集或生成场景（例如 ImageNet 或特定文本到图像任务）。  
- **基准方法**：未明确列出对比的基线方法。从上下文推测可能比较了标准自回归生成（无 KV 缓存压缩）以及一些通用的 KV 缓存压缩策略（如剪枝、量化等），但原文未提供具体名称。  
- **对比结果**：实验表明，所提方法实现了 **5 倍内存减少** 和 **6.6 倍吞吐量提升**，同时性能损失可忽略不计。

## 4. 资源与算力  
- 原文**未明确说明**所使用的 GPU 型号、数量、训练时长或推理设备等算力信息。因此，无法评估其计算开销或可复现性。

## 5. 实验数量与充分性  
- 论文提供的结果较为宏观（内存减 5×、吞吐提 6.6×），但**缺乏详细的消融实验**（如不同压缩窗口大小的影响、不同头分类阈值的敏感性）和**多数据集或不同模型架构的泛化验证**。  
- 由于未能看到完整论文正文，仅从摘要和元数据判断，实验规模似乎有限，**充分性和公平性有待进一步审阅**。

## 6. 主要结论与发现  
- 自回归图像生成中存在两种显著且可预测的注意力模式：空间局部性和涌现语义汇点。  
- 通过将注意力头解耦为两类并分别施以针对性压缩，可以在图像生成任务中有效压缩 KV 缓存，显著降低内存和加速推理，且几乎不损失生成质量。  
- SSD 为图像生成领域的 KV 缓存压缩提供了一个有效框架。

## 7. 优点  
- **问题新颖**：将 KV 缓存压缩从语言建模拓展至图像生成，填补了该方向的研究空白。  
- **思路简洁**：利用注意力头的自然分化，免去了复杂的训练或微调，仅需在推理阶段调整缓存策略。  
- **效果显著**：在保持质量的前提下实现 5× 内存降低和 6.6× 吞吐提升，具有实际应用价值。

## 8. 不足与局限  
- **实验覆盖不足**：未提供具体数据集、对比基线及详细的消融实验，难以全面评估方法的鲁棒性和泛化能力。  
- **资源信息缺失**：未给出算力细节，影响可复现性和效率评估的可信度。  
- **假设依赖**：方法有效性依赖于注意力头能否被稳定地划分为空间局部性和语义汇点两类。若该现象在更大规模或不同架构的模型中出现变化，压缩效果可能下降。  
- **仅针对视觉 token**：未讨论对文本 token 或其他模态的处理，适用范围有限。

（完）
