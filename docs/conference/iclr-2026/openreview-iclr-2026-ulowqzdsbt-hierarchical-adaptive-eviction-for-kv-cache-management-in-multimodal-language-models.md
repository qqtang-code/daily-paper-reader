---
title: Hierarchical Adaptive Eviction for KV Cache Management in Multimodal Language Models
title_zh: 用于多模态大模型KV缓存管理的分层自适应淘汰
authors: "Xindian Ma, Yidi Lu, Peng Zhang, Jing Zhang"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=ulOwQZdSbT"
tags: ["query:sparse-attn"]
score: 7.0
evidence: 利用视觉token稀疏性的多模态大模型分层自适应KV缓存淘汰
tldr: "多模态大模型中视觉与文本token注意力分布异质,现有KV缓存淘汰策略效率低或性能下降。HAE提出分层自适应淘汰框架:在预填充阶段利用视觉token稀疏性和注意力方差进行双注意力剪枝,在解码阶段采用动态解码淘汰策略。方法在保持性能的同时显著降低缓存占用。"
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: "多模态大模型中视觉与文本token注意力分布异质,现有KV淘汰方法效果不佳。"
method: "预填充阶段双注意力剪枝,解码阶段动态淘汰策略。"
result: 在多个MLLM上降低了KV缓存占用且性能几乎无损。
conclusion: HAE为多模态大模型提供了高效的KV缓存管理方案。
---

## Abstract
The integration of visual information into Large Language Models (LLMs) has enabled Multimodal LLMs (MLLMs), but the quadratic memory and computational costs of Transformer architectures remain a bottleneck. Existing KV cache eviction strategies fail to address the heterogeneous attention distributions between visual and text tokens, leading to suboptimal efficiency or degraded performance.
In this paper, we propose Hierarchical Adaptive Eviction (HAE), a KV cache eviction framework that optimizes text-visual token interaction in MLLMs by implementing Dual-Attention Pruning during pre-filling (leveraging visual token sparsity and attention variance) and a Dynamic Decoding Eviction Strategy (inspired by OS Recycle Bins) during decoding. 
HAE minimizes KV cache usage across layers, reduces computational overhead via index broadcasting, and theoretically ensures superior information integrity and lower error bounds compared to greedy strategies, enhancing efficiency in both comprehension and generation tasks. 
Empirically, HAE reduces KV-Cache memory by 41\% with minimal accuracy loss (0.3\% drop) in image understanding tasks and accelerates story generation inference by 1.5× while maintaining output quality on Phi3.5-Vision-Instruct model.

---

## 论文详细总结（自动生成）

# 用于多模态大模型KV缓存管理的分层自适应淘汰（HAE）论文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：多模态大语言模型（MLLM）中，Transformer架构的KV缓存占用二次方内存和计算成本，成为瓶颈；现有KV缓存淘汰策略未能处理视觉token与文本token之间**异质的注意力分布**，导致效率低下或性能下降。
- **研究动机**：视觉token通常具有稀疏性且与文本token的注意力模式差异大，简单的全局淘汰策略（如统一保留高频注意力token）会丢失关键信息，需要针对多模态特性设计分层自适应淘汰机制。
- **整体含义**：提出一种兼顾预填充和解码两个阶段的KV缓存管理方案，在保持生成质量的前提下显著降低内存占用，提升推理效率。

## 2. 方法论：核心思想、关键技术细节

### 核心思想：Hierarchical Adaptive Eviction (HAE)
- 采用**分阶段、分层次**的自适应淘汰策略：
  - **预填充阶段**：利用视觉token的稀疏性及注意力方差进行**双注意力剪枝**（Dual-Attention Pruning）
  - **解码阶段**：受操作系统回收站启发，采用**动态解码淘汰策略**（Dynamic Decoding Eviction Strategy）

### 关键技术细节
1. **预填充阶段的双注意力剪枝**  
   - 将视觉token与文本token的注意力矩阵分离处理，根据视觉token的稀疏性（许多视觉token与文本无关）以及各token的注意力方差（重要性分布）进行剪枝，仅保留对当前生成任务最重要的部分视觉token。
2. **解码阶段的动态淘汰策略**  
   - 类似操作系统的回收站机制：保留一个“回收站”缓存区域，被淘汰的KV对可能重新被激活（当后续查询需要时），避免因贪婪淘汰导致的信息永久丢失。
3. **索引广播（index broadcasting）**  
   - 通过广播共享索引信息，减少跨层的冗余计算，降低计算开销。
4. **理论保证**  
   - 相比贪婪策略，HAE能实现更好的信息完整性和更低的误差上界。

（无具体公式，文中仅用文字描述）

## 3. 实验设计

- **使用的模型**：Phi3.5-Vision-Instruct（一个多模态大模型）
- **任务/场景**：
  - 图像理解任务（Image Understanding）
  - 故事生成推理（Story Generation Inference）
- **评估指标**：
  - 图像理解：准确率下降（Accuracy loss，0.3%）
  - KV缓存内存减少（41%）
  - 故事生成：推理加速（1.5×），生成质量保持（未量化说明）
- **对比方法**：文中仅提到与"贪婪策略"（greedy strategies）对比，未列出具体基线方法名。

## 4. 资源与算力

- **未明确说明**：文中未提及使用的GPU型号、数量、训练时长等具体算力信息。仅给出了推理阶段的加速比（1.5×）和内存减少率。

## 5. 实验数量与充分性

- **实验数量**：仅报告了一个模型（Phi3.5-Vision-Instruct）上的两组任务（图像理解 + 故事生成），每个任务只提供了1~2个关键指标。无消融实验、无不同模型对比、无不同缓存大小或淘汰策略的详细对比。
- **充分性评估**：**不够充分**。缺乏在多个MLLM（如LLaVA、Qwen-VL等）上的验证，缺少消融研究（例如是否每个组件都有贡献），也缺乏与当前主流KV淘汰方法（如H2O、Scissorhands、StreamingLLM等）的实验对比。实验覆盖范围窄，结论的可推广性存疑。

## 6. 论文的主要结论与发现

- HAE在多模态大模型中实现了**41%的KV缓存内存减少**，同时图像理解准确率仅下降0.3%。
- 故事生成推理速度提升**1.5倍**，且输出质量基本保持。
- 理论分析表明HAE相比贪婪策略具有更优的信息完整性和更低的误差界。
- 整体而言，HAE为MLLM提供了一种高效的KV缓存管理方案，在效率和性能之间取得了良好的平衡。

## 7. 优点

- **针对性设计**：首次明确针对多模态大模型中视觉与文本token的异质注意力分布进行分层淘汰，比通用方法更合理。
- **两阶段策略**：预填充时的双注意力剪枝有效利用视觉稀疏性；解码时的回收站机制避免信息永久丢失，灵感新颖。
- **索引广播**降低计算开销，使得实际部署更高效。
- **理论误差分析**提供了形式化保证，增加了方法的可信度。

## 8. 不足与局限

- **实验严重不足**：仅在一个小型模型（Phi3.5-Vision-Instruct）上进行测试，未在其他主流MLLM（如LLaVA-NeXT、InternVL、Qwen-VL等）上验证，也未与最先进的KV缓存方法（如H2O、FastGen、StreamingLLM等）进行对比。结果可能不具有泛化性。
- **缺乏消融实验**：无法确认双注意力剪枝和动态淘汰策略各自的具体贡献。
- **缺少详细指标**：故事生成任务中只提到了“maintain output quality”，未给出定量度量（如BLEU、ROUGE、CLIP评分等）。
- **未讨论扩展性**：未分析在不同视觉分辨率、不同序列长度、不同batch size下的表现。
- **资源开销未报告**：方法本身引入的额外计算（如回收站管理、索引广播）可能抵消部分收益，但没有提供时间或内存开销的详细分解。
- **局限性**：被拒稿状态（ICLR-2026-Rejected）暗示审稿人可能认为方法创新性或实验强度不足。

（完）
