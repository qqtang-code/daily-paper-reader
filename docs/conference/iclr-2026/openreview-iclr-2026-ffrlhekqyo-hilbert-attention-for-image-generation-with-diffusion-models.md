---
title: Hilbert Attention for Image Generation with Diffusion Models
title_zh: 希尔伯特注意力：用于扩散模型图像生成的2D感知稀疏注意力
authors: "Shaoyi Zheng, Wenbo Lu, Yuxuan Xia, Haoming Liu, Shenji Wan"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=FfRlHeKqYO"
tags: ["query:sparse-attn"]
score: 7.0
evidence: 基于希尔伯特曲线的扩散变换器稀疏注意力
tldr: HilbertA针对扩散模型中的图像生成任务，设计了一种2D感知且GPU高效的稀疏注意力机制。通过沿希尔伯特曲线重排图像token，实现了连续内存布局并保留了空间邻域关系，采用跨层滑动调度实现长距离信息传播。该方法在保持图像生成质量的同时显著提高了计算效率，为扩散模型中的注意力优化提供了新方案。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 现有稀疏注意力难以同时实现2D空间局部性和GPU效率。
method: 沿希尔伯特曲线重排token，采用滑动调度和中心共享区域实现高效稀疏注意力。
result: 在图像生成任务上加速并保持生成质量。
conclusion: HilbertA为扩散模型提供了高效的稀疏注意力方案。
---

## Abstract
Designing sparse attention for diffusion transformers requires reconciling two-dimensional spatial locality with GPU efficiency, a trade-off that current methods struggle to achieve. Existing approaches enforce two-dimensional spatial locality but often incur uncoalesced memory access. We present HilbertA, a 2D-aware and GPU-efficient sparse attention mechanism. HilbertA reorders image tokens along Hilbert curves to achieve a contiguous memory layout while preserving spatial neighborhoods, and employs a sliding schedule across layers to enable long-range information propagation without repeated or uncoalesced memory access. To further enhance cross-tile communication and positional awareness, HilbertA introduces a small central shared region. Implemented in Triton, HilbertA delivers comparable image quality with significant acceleration over prior methods on Flux.1-dev, demonstrating the feasibility of hardware-aligned two-dimensional sparse attention for high-resolution image generation. HilbertA delivers attention speedups of $2.3\times$ when generating 1024 $\times$ 1024 images, and up to $4.17\times$ at 2048 $\times$ 2048, while achieving image quality comparable to or surpassing baselines.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：在扩散变换器（Diffusion Transformers）中设计稀疏注意力机制时，需要同时满足**二维空间局部性**（2D spatial locality）和**GPU计算效率**（GPU efficiency），现有方法难以兼顾两者。
- **背景**：已有稀疏注意力方法虽然能强制保持二维空间局部性，但往往导致**非合并内存访问**（uncoalesced memory access），严重降低GPU利用率。随着高分辨率图像生成需求增长，注意力计算开销成为瓶颈。
- **整体含义**：本文旨在提出一种新的稀疏注意力机制，在保持生成质量的前提下显著提升计算效率，使扩散模型能够更高效地生成高分辨率图像。

## 2. 论文提出的方法论
- **核心思想**：利用**希尔伯特曲线**（Hilbert curve）对图像token进行重排，实现连续内存布局的同时保留空间邻域关系，并设计跨层滑动调度实现长距离信息传播。
- **关键技术细节**：
  - **Token重排**：沿希尔伯特曲线重新排列图像token，使得在内存中连续排列的token在二维空间上也是相邻的，从而支持**合并内存访问**（coalesced memory access）。
  - **跨层滑动调度**（sliding schedule across layers）：在不同层之间滑动注意力窗口，逐步实现长距离信息传播，避免重复或非合并内存访问。
  - **中心共享区域**（central shared region）：在注意力计算中引入一个小的中心共享区域，增强跨tile通信和位置感知能力。
- **公式/算法流程说明**：
  - 输入：图像token序列（初始顺序为光栅扫描次序）。
  - 步骤1：根据希尔伯特曲线索引对token进行重排序，得到新序列。
  - 步骤2：在每一层执行滑动窗口注意力，窗口大小固定，但窗口的起始位置在各层中滑动变化。
  - 步骤3：在每个注意力计算中，额外包含一个固定的中心共享区域（小区域）的token，以促进全局信息交换。
  - 步骤4：注意力计算采用Triton实现，优化GPU内核。
- **实现工具**：基于Triton编写自定义算子。

## 3. 实验设计
- **数据集/场景**：未明确说明具体训练数据集。实验针对**图像生成**任务，在**Flux.1-dev**模型上进行评估。
- **基准（Benchmark）**：生成了**1024×1024**和**2048×2048**分辨率的图像。
- **对比方法**：摘要提到“优于先前方法”（over prior methods），但未列出具体模型名称。元数据中标题提及“2D感知稀疏注意力”，推测与常见的稀疏注意力（如局部注意力、块稀疏注意力等）进行了对比。
- **评估指标**：图像质量（comparable image quality）和注意力加速比（attention speedup）。

## 4. 资源与算力
- **未明确说明**：摘要和元数据中**未提及**使用的GPU型号、数量、训练时长或推理环境。仅提到实现基于Triton，暗示在NVIDIA GPU上运行。需要指出这一点在论文中缺失。

## 5. 实验数量与充分性
- **实验数量**：从提供信息看，仅有**一个模型（Flux.1-dev）**、**两个分辨率（1024和2048）** 的加速比和图像质量对比。未提及**消融实验**（如不同重排策略、滑动调度设计、共享区域大小的影响）、**不同数据集**（如ImageNet、COCO等）或**下游任务**（如文本到图像、无条件生成）的验证。
- **充分性评价**：实验覆盖**不够充分**。虽然加速效果显著，但：
  - 缺乏对**不同扩散模型架构**（如DiT、U-Net变体）的通用性验证。
  - 缺少**定量图像质量指标**（如FID、IS、CLIP score）的对比，仅称“comparable image quality”。
  - 未提供**消融实验**，无法证明各组件（重排、滑动、共享区域）的必要性。
- **客观公平性**：对比方法未具体说明，难以判断是否公平。有潜在的选择偏差风险。

## 6. 论文的主要结论与发现
- HilbertA在生成1024×1024图像时实现**2.3倍**注意力加速，生成2048×2048时加速**4.17倍**。
- 在图像质量上达到或超过基线方法（comparable to or surpassing baselines）。
- 证明**硬件对齐的二维稀疏注意力**在高分辨率图像生成中是可行的，且能平衡空间局部性与效率。

## 7. 优点
- **创新性**：将希尔伯特曲线引入扩散模型的token重排，实现2D感知与GPU友好内存访问的结合。
- **工程实现**：基于Triton实现，便于集成和优化。
- **效率显著**：在高分辨率下加速比达到4倍以上，对实际应用价值大。
- **设计简洁**：滑动调度和中心共享区域机制无需复杂的学习过程，即插即用。

## 8. 不足与局限
- **实验覆盖不足**：仅在一个模型（Flux.1-dev）上验证，缺乏在其他扩散模型（如Stable Diffusion、DiT等）和多任务（如视频生成、超分辨率）上的结果。
- **缺少定量图像质量指标**：未报告FID、IS等标准指标，仅称“comparable”，说服力有限。
- **无消融实验**：无法确认希尔伯特曲线重排是否优于其他空间填充曲线（如Z-order、Peano），也无法量化滑动调度和共享区域的贡献。
- **资源信息缺失**：未说明GPU型号、训练/推理配置，影响可复现性。
- **潜在偏差风险**：对比的基线方法可能并非最优或最新，可能存在选择偏差。
- **应用限制**：仅适用于图像生成任务中的二维token，对于视频、3D或非结构化数据的扩展性未讨论。

（完）
