---
title: Multipole Attention for Efficient Long Context Reasoning
title_zh: Multipole Attention：面向高效长上下文推理的多极注意力
authors: "Coleman Richard Charles Hooper, Sebastian Zhao, Luca Manolache, Sehoon Kim, Michael W. Mahoney, Sophia Shao, Kurt Keutzer, Amir Gholami"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=5Qe7AGO3Eq"
tags: ["query:sparse-attn"]
score: 9.0
evidence: 用于长链推理的稀疏注意力和KV缓存压缩
tldr: 大推理模型生成长链思维链导致KV缓存压力巨大，现有稀疏注意力方法可能引入误差。论文提出Multipole Attention，仅对最重要令牌计算精确注意力，其余令牌用近似表示，在加速自回归推理的同时保持推理准确性。实验表明该方法在长链推理任务中显著减少缓存并保持准确度，为高效长上下文推理提供新方案。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-5qe7ago3eq/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1446, \"height\": 467, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5qe7ago3eq/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1448, \"height\": 538, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5qe7ago3eq/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1426, \"height\": 672, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5qe7ago3eq/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1442, \"height\": 563, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5qe7ago3eq/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1430, \"height\": 658, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5qe7ago3eq/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1439, \"height\": 858, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-5qe7ago3eq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 858, \"height\": 215, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-5qe7ago3eq/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 682, \"height\": 360, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-5qe7ago3eq/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 681, \"height\": 358, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-5qe7ago3eq/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1443, \"height\": 333, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-5qe7ago3eq/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 707, \"height\": 121, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-5qe7ago3eq/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 941, \"height\": 121, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-5qe7ago3eq/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1291, \"height\": 180, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-5qe7ago3eq/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1290, \"height\": 178, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-5qe7ago3eq/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1422, \"height\": 152, \"label\": \"Table\"}]"
motivation: 长链推理中KV缓存压力大，现有稀疏注意力方法可能破坏推理过程。
method: 提出Multipole Attention，只对最重要令牌计算精确注意力，其余维护近似表示。
result: 在长链推理任务中加速推理并减少缓存，同时保持与精确注意力相近的准确性。
conclusion: 该注意力机制能有效兼顾推理效率与准确性，适用于需要生成长链推理的大模型。
---

## Abstract
Large Reasoning Models (LRMs) have shown promising accuracy improvements on complex problem-solving tasks. While these models have attained high accuracy by leveraging additional computation at test time, they need to generate long chain-of-thought reasoning in order to think before answering, which requires generating thousands of tokens.
While sparse attention methods can help reduce the KV cache pressure induced by this long autoregressive reasoning, these methods can introduce errors which disrupt the reasoning process.
Our work addresses these challenges by introducing Multipole Attention, which accelerates autoregressive reasoning by only computing exact attention for the most important tokens, while maintaining approximate representations for the remaining tokens. 
Our method first performs clustering to group together semantically similar key vectors, and then uses the cluster centroids both to identify important key vectors and to approximate the remaining key vectors in order to retain high accuracy.
Additionally, in order to accelerate long generation tasks, we design a fast cluster update process to quickly re-cluster the input and previously generated tokens, thereby allowing for  accelerating attention to the previous output tokens.
We evaluate our method using emerging LRMs such as Qwen-8B and Deepseek-R1-Distil-Qwen2.5-14B, demonstrating that our approach can maintain accuracy on complex reasoning tasks even with aggressive attention sparsity settings.
We also provide kernel implementations to demonstrate the practical efficiency gains from our method, achieving up to 4.5$\times$ speedup for attention in long-context reasoning applications.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

大型推理模型（LRM）通过生成长链思维（chain-of-thought）在复杂问题求解中取得了显著精度提升，但生成长达数千 token 的自回归推理过程带来了巨大的 KV 缓存压力。传统稀疏注意力方法通过仅加载重要 KV 缓存条目来减少内存带宽需求，但在推理任务中容易引入误差，破坏推理过程，尤其是在需要精确上下文信息的复杂推理场景下精度损失较大。此外，现有方法通常需要对输入进行预处理以便在生成时识别重要标记，而对于在线生成的推理 token 难以执行这种预处理。

本文提出 **Multipole Attention**，通过仅对最重要 token 计算精确注意力，同时对其余 token 维护近似表示，在加速推理的同时保持高精度，旨在解决长上下文推理中的效率与精度矛盾。

## 2. 论文提出的方法论

### 核心思想
- 基于语义相似性对 key 向量进行 k-means 聚类，得到每个簇的代表性质心。
- 在注意力计算时，将当前 query 与质心比较，识别重要簇（高注意力分数）并对其中的 key 加载精确注意力；对剩余簇，直接使用质心的注意力分数近似所有 key 的贡献，从而保留全序列的上下文信息。
- 扩展为层次化多极近似：逐步使用更粗粒度的质心，降低质心比较开销。

### 关键技术细节
- **质心选取与重要性估计**：  
  对于簇 \( i \)，质心注意力分数为：
  \[
  S_i = \frac{\exp(q K_c^i)}{\sum_j N_j \exp(q K_c^j)}
  \]
  其中 \( K_c^i \) 为簇 i 的 key 质心，\( N_j \) 为簇 j 的 key 数量。根据 \( S_i \) 排序，保留前 k 个簇的 key 用于精确计算。

- **近似注意力贡献**：  
  对不重要的簇，使用质心近似计算：
  \[
  N_i \exp(q K_c^i) V_c^i
  \]
  其中 \( V_c^i \) 为对应的 value 质心（均值），代替所有 key 的注意力。

- **快速在线聚类更新**：  
  采用块式聚类（block-wise），以 \( W \) token 为一块，生成新 token 时仅更新最后一块。当最后一块达到 \( W + \alpha \) 时，将前 \( W \) 个 token 固定为独立块，剩余 \( \alpha \) 个 token 作为新的最后窗口，保证始终有足够 token 用于聚类。同时使用快速初始分配（类似批量化顺序 k-means）加少量全块 k-means 迭代来精炼聚类质量。

- **层次化多极注意力**：  
  采用两层层次聚类：第一层粗粒度（每 64 token 一个质心），第二层细粒度（每 8 token 一个质心）。仅对高评分粗粒度簇进行第二层质心比较，其余粗粒度簇直接用第一层质心近似，降低计算开销。

- **系统实现**：  
  使用 Triton 编写自定义内核，包括 centroid lookup、sparse FlashDecoding 和 centroid replacement 三阶段。centroid lookup 保存 query-key 质心点积结果供后续 replacement 重用；sparse FlashDecoding 仅加载重要簇的 key；centroid replacement 计算不重要簇的近似注意力。快速聚类更新使用 PyTorch 配合 torch.compile 实现。

## 3. 实验设计

- **数据集**：
  - **LongBenchV2**：复杂真实世界长上下文问题（文档 QA、长上下文学习、对话理解、代码库理解等）。
  - **GSM-Infinite**：合成数学推理任务，需要多步算术操作。
  - 附录额外使用 **LongBenchV1**（非推理长上下文任务）。

- **模型**：
  - **Qwen3-8B** 和 **DeepSeek-R1-Distil-Qwen-14B**，均使用 YaRN 扩展至 128K 上下文长度。

- **对比方法**：
  - 基线：完整 FlashDecoding（不压缩）。
  - 稀疏注意力方法：**Squeezed Attention**、**QUEST**（主要对比），以及在 LongBenchV1 上额外对比 **DuoAttention** 和 **TOVA**。

- **评估设置**：
  - 报告 token 预算为 128 和 512 时的准确率，并考虑本地缓冲区大小（MULTIPOLE ATTENTION 保留最后 128-256 token 不聚类，精确计算）。
  - 超参数：块大小 \( W=8K \)，\( \alpha = \frac{1}{2}W \)，每 16 token 一个质心（一级），层次化时第一级每 64 token，第二级每 8 token。
  - 报告平均结果（3 次试验）。

## 4. 资源与算力

- **实验硬件**：A6000 和 A100 GPU 用于内核基准测试。
- 训练时间：未提及（本文不涉及模型训练，仅推理优化）。
- 基准测试细节：使用 `triton.testing.do_bench` 进行 500 次预热和 500 次测量；split size 设为 2048。
- 未明确说明总 GPU 小时数，但实验规模适中（两个模型、多个数据集、3 次重复），算力消耗合理。

## 5. 实验数量与充分性

- **实验数量丰富**：
  - 主要结果：在 LongBenchV2 上对两个模型、两种 token 预算（128, 512）进行准确率对比。
  - GSM-Infinite 上对 1 步和 2 步操作、8K 和 16K 上下文长度、单级与层次化变体进行实验。
  - 消融实验：质心比例（每 128/64/32/16/8 token 一个质心）和块大小（2K/4K/8K/16K）。
  - 系统基准测试：在 A6000 和 A100 上测试不同 batch size（1,4,16），报告端到端速度提升及组件耗时分解。
  - 附录 LongBenchV1 上与非推理模型（Llama-3.1-8B-Instruct）对比，验证泛化性。

- **充分性评价**：实验覆盖了不同模型、不同上下文长度、不同稀疏度、不同任务类型（推理与非推理），并包含层次化变体、消融和系统性能，较为充分。对比方法设置公平（统一 token 预算、考虑元数据开销）。但主要依赖两个推理模型，模型多样性有限；未在更大规模模型（如 70B）上验证。

## 6. 论文的主要结论与发现

- **精度保持**：Multipole Attention 在激进稀疏（如仅保留 128 token）下仍能保持接近基线的准确率，显著优于 Squeezed Attention 和 QUEST。例如在 LongBenchV2 上，DeepSeek-R1-Distil-Qwen-14B 模型在 token 预算 512 时，整体准确率与基线无显著差距。
- **加速效果**：实际内核实现实现最高 4.5× 注意力加速（A6000，batch size 16，95% 稀疏度）。层次化变体进一步降低 centroid lookup 开销。
- **聚类更新开销低**：快速聚类更新仅占解码总时间的 3-5%（中位数），预填充阶段聚类开销约 13-15%，可接受。
- **泛化性**：在非推理长上下文任务（LongBenchV1）上也优于现有方法，表明方法不限于推理场景。

## 7. 优点

- **创新性**：联合利用质心进行重要 token 识别和近似注意力计算，实现“近似而不丢弃”，比单纯稀疏方法更鲁棒。
- **实用性**：设计快速的在线聚类更新策略，使方法能够适应推理过程中不断生成的 token，弥补了之前方法无法在线处理输出 token 的缺陷。
- **系统实现**：提供完整的 Triton 内核实现，展示了实际效率增益，并开源代码。
- **层次化扩展**：通过层次质心进一步降低查询开销，在相同内存操作下获得更高精度。
- **实验设计严谨**：考虑了 token 预算公平对比、元数据开销、多次重复、消融分析等。

## 8. 不足与局限

- **未加速预填充阶段**：方法只加速自回归解码，不加速 prompt 处理（prefill），在某些场景（如预填充很长）可能成为瓶颈。
- **额外内存开销**：需要存储 key 和 value 质心，虽然相对于完整 KV 缓存较小，但仍需额外内存。
- **集成成本**：需要进一步实现才能在现有 LLM 服务框架（如 vLLM）中使用。
- **模型规模有限**：仅在 8B 和 14B 模型上评估，未在更大模型（如 70B）上验证，可能影响结论泛化性。
- **超参数敏感**：质心比例、块大小等超参数需手动调整，不同任务可能需重新优化。
- **评估偏差风险**：LongBenchV2 上 Qwen3-8B 在长上下文分片准确率低于随机，说明模型本身在长上下文处理上存在缺陷，可能影响了方法有效性的评估。

（完）
