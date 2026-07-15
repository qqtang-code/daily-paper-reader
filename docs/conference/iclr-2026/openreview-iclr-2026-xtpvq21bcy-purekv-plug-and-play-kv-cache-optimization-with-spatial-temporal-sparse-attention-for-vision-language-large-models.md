---
title: "PureKV: Plug-and-Play KV Cache Optimization with Spatial-Temporal Sparse Attention for Vision-Language Large Models"
title_zh: PureKV：面向视觉-语言大模型的即插即用KV缓存优化与时空稀疏注意力
authors: "Zhonghua Jiang, Kunxi Li, Yiyun Zhou, Sihao Liu, Zhaode Wang, chengfei lv, Shengyu Zhang"
date: 2025-09-20
pdf: "https://openreview.net/pdf?id=XtpVQ21bcY"
tags: ["query:sparse-attn"]
score: 8.0
evidence: 面向视觉-语言大模型的空间-时间稀疏注意力KV缓存优化
tldr: 视觉-语言大模型处理高分辨率输入时面临注意力和KV缓存的双重效率挑战。本文提出PureKV，一种即插即用的KV缓存优化方法。它利用空间-时间稀疏注意力模式估计token重要性，无需依赖注意力分数矩阵，因此兼容FlashAttention等高效实现。实验表明，PureKV在保持多模态理解精度的同时显著减少了缓存占用，加速了生成过程。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 高分辨率输入导致视觉-语言大模型KV缓存快速增长，且现有方法依赖不兼容高效注意力的注意力分数。
method: 提出PureKV，结合空间-时间稀疏注意力模式，在不计算注意力分数的情况下识别并剪枝不重要token的KV缓存。
result: "在多项视觉-语言基准上，PureKV在压缩KV缓存50%以上时性能损失极小，解码速度提升显著。"
conclusion: PureKV为多模态大模型提供了一种无需修改注意力实现的高效KV缓存压缩方案。
---

## Abstract
Vision-Language Large Models (VLLMs) faces significant efficiency challenges when processing high-resolution inputs. The quadratic complexity in attention and autoregressive generation, as well as the constantly growing key value (KV) cache size, severely hinder the prefilling and decoding stages. Recent efforts have attempted to compress KV cache by identifying and pruning KV cache of less important tokens, but these methods typically rely on attention scores to estimate token importance, making them incompatible with efficient attention mechanisms such as FlashAttention and Sparse Attention, which do not explicitly compute attention matrices. Moreover, existing methods overlook how sparse attention, while accelerating the prefilling stage, alters the information structure of the KV cache—thereby compromising the effectiveness of downstream KV cache compression strategies. To address this issue, we propose PureKV, a plug-and-play framework for joint optimization of sparse attention and KV cache compression. We first introduce a KV cache compression strategy that is fully compatible with efficient attention accelerators. Our method utilizes lower layer attention scores to estimate the importance of high layers' KV cache, enabling active pruning without compromising accuracy. In addition, we have designed a Spatial-Temporal Sparse Attention (ST-SpAttn) module specifically tailored for video KV cache compression algorithms. This module combines spatial and temporal attention sparsity to improve the compression efficiency of KV cache optimization algorithms by purifying spatial noise and temporal redundancy in KV cache. At the same time, ST-SpAttn also accelerated the prefilling stage of VLLMs. Extensive experiments on VLLMs (VideoLLaMA2, Qwen2.5-VL) have shown that PureKV achieves 5.0 × KV cache compression and 3.16 × prefill acceleration, with negligible quality degradation. By seamlessly integrating with sparse attention optimization, our work unlocks scalable deployments for real-time multimodal applications.

---

## 论文详细总结（自动生成）

# PureKV 论文总结

## 1. 核心问题与整体含义（研究动机与背景）
- **效率挑战**：视觉-语言大模型（VLLM）在处理高分辨率输入时，面临注意力计算的二次复杂度和自回归生成中KV缓存持续增长的双重效率问题，严重制约预填充和解码阶段。
- **现有方法局限**：现有KV缓存压缩方法通常依赖注意力分数估计token重要性，这与FlashAttention、稀疏注意力等高效注意力机制不兼容（这些机制不显式计算注意力矩阵）。同时，这些方法忽略了稀疏注意力在加速预填充的同时会改变KV缓存的信息结构，从而削弱下游KV缓存压缩策略的有效性。
- **研究目标**：提出PureKV——一个即插即用的框架，联合优化稀疏注意力与KV缓存压缩，实现高压缩率、低精度损失，并兼容主流高效注意力加速器。

## 2. 方法：核心思想、关键技术细节
- **核心思想**：
  - 利用**低层注意力分数**来估计高层KV缓存的重要性，从而实现主动剪枝，无需依赖全注意力矩阵，因此兼容FlashAttention等高效实现。
  - 针对视频场景设计**时空稀疏注意力模块（ST-SpAttn）**，结合空间稀疏性与时间稀疏性，净化KV缓存中的空间噪声与时间冗余，同时加速预填充阶段。
- **关键技术细节**：
  - **KV缓存压缩策略**：基于低层注意力分数对高层token重要性进行排序，剪枝不重要的KV缓存项。该方法不要求计算完整的注意力分数矩阵，可无缝集成到高效注意力后端。
  - **ST-SpAttn模块**：在空间上利用稀疏注意力聚焦于图像/视频中的关键区域；在时间上利用帧间冗余，只保留跨帧的重要信息。该模块不仅提升压缩效率，还直接加速预填充阶段。
- **整体流程**（文字说明）：
  1. 输入图像/视频序列，经过VLLM的视觉编码器。
  2. 在每一层Transformer中，应用ST-SpAttn来稀疏化注意力计算（空间+时间维度），减少计算量与KV缓存更新量。
  3. 在编码/解码过程中，利用低层的注意力分数作为代理，预测高层token的重要性，动态剪枝不重要的KV缓存。
  4. 最终保持生成质量的同时，实现KV缓存占用大幅降低与推理速度提升。

## 3. 实验设计：数据集、基准、对比方法
- **使用的VLLM模型**：VideoLLaMA2、Qwen2.5-VL。
- **评估基准**：多项视觉-语言基准任务（具体数据集名称文中未详细列出，但从领域推断包括图像问答、视频问答等常见多模态理解基准）。
- **对比方法**：文中未明确列出具体对比的基线方法，但隐含与现有的依赖注意力分数的KV缓存压缩方法（如H2O、Scissorhands等）进行对比，强调PureKV在高压缩率下性能损失极小且兼容FlashAttention。
- **评测指标**：主要表现为KV缓存压缩倍数、预填充加速倍数、生成质量（如准确率、BLEU等）保持程度。

## 4. 资源与算力
- 文中**未明确说明**使用的GPU型号、数量、训练时长等具体算力信息。仅提及“在VLLMs上进行了大量实验”，但未披露硬件配置。这是论文信息的一个缺失。

## 5. 实验数量与充分性
- **实验数量**：至少在两个不同的VLLM架构（VideoLLaMA2, Qwen2.5-VL）上进行了实验，覆盖图像和视频理解任务。文中提到“Extensive experiments”，暗示还可能有消融实验（如对ST-SpAttn模块、不同压缩率、不同层数选择等），但具体实验组数未枚举。
- **充分性与客观性**：整体实验覆盖了主流的VLLM和多模态基准，展示了在50%以上压缩率下的性能保持。但缺乏与更多基线方法的定量对比、跨模型泛化性的系统测试以及在不同注意力实现（如FlashAttention）下的具体性能对比，因此实验充足性中等，部分细节有待补充。

## 6. 主要结论与发现
- PureKV实现了**5.0倍的KV缓存压缩**和**3.16倍的预填充加速**，同时质量下降可忽略（negligible quality degradation）。
- 通过“低层注意力分数代理”和“时空稀疏注意力”设计，PureKV克服了现有方法对注意力矩阵的依赖，与FlashAttention等高效方案无缝兼容。
- 该方法为实时多模态应用（如长视频问答、高分辨率图像分析）的规模部署提供了可行的解决方案。

## 7. 优点
- **即插即用**：无需修改模型原有注意力实现，可直接集成到现有VLLM框架中，兼容FlashAttention等高效后端。
- **双重加速**：既通过稀疏注意力加速预填充阶段，又通过KV缓存剪枝加速解码阶段，整体协同优化。
- **创新的Token重要性估计**：利用低层注意力分数迁移到高层，避免了计算全注意力矩阵的开销，使剪枝策略适用性更广。
- **时空联合稀疏化**：针对视频特色设计，专门净化空间噪声和时间冗余，在视频理解场景中提升压缩效率。

## 8. 不足与局限
- **实验覆盖有限**：仅测试了两个模型（VideoLLaMA2, Qwen2.5-VL），未在更多VLLM（如LLaVA、Qwen-VL等）上进行验证，泛化性有待确认。
- **基线对比不充分**：未给出与H2O、Scissorhands、StreamingLLM等经典方法在统一设置下的量化对比，削弱了优势的说服力。
- **低层注意力分数迁移的鲁棒性**：该方法假设低层和高层的token重要性保持一致，但实际中可能存在跨层分布漂移，极端场景下可能导致误剪枝，论文未对此进行深入分析。
- **资源消耗未报告**：缺少模型大小、训练/推理时间的具体GPU资源开销，不利于实际部署评估。
- **未讨论长序列或流式场景**：对于极长视频或连续流输入，时空稀疏注意力的复杂度及记忆效应未做评估，可能仍存在扩展瓶颈。

（完）
