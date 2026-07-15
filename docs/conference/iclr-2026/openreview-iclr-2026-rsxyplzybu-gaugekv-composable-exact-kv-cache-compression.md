---
title: "GaugeKV: Composable Exact KV Cache Compression"
title_zh: GaugeKV：可组合的精确KV缓存压缩
authors: "Hong Wang, Kelly Wang"
date: 2025-09-06
pdf: "https://openreview.net/pdf?id=rSxYPLzyBu"
tags: ["query:sparse-attn"]
score: 9.0
evidence: 基于规范对称性的可组合精确KV缓存压缩
tldr: 提出GaugeKV，一种利用注意力头规范对称性的无训练精确KV缓存压缩方法。通过一次性规范变换，使值和查询/键处于压缩友好基中，保持输出不变。结合无损冷热分级，实现可量化的KV减少（GPT-2上1.11–1.21倍），并与分组/多查询注意力相乘以达4.6倍压缩。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: KV缓存是长上下文Transformer推理的主要内存开销，需要无损或接近无损的压缩。
method: 利用头级规范对称性进行规范变换，使得KV在压缩友好基中表示，并组合热冷分级。
result: 在保持输出一致的前提下实现1.11–1.21倍KV压缩，与GQA/MQA结合可达4.6倍。
conclusion: 提供了一种可组合、无训练且精确的KV缓存压缩方法，适用于各种Transformer。
---

## Abstract
The key–value (KV) cache is a dominant memory cost in long-context Transformer inference. We introduce GaugeKV, a training-free method that leverages the head-wise gauge symmetry of attention to reduce KV memory both exactly and with certificates. A one-time gauge canonicalization rewrites weights so that values are orthonormal and queries/keys are scale-balanced; thereafter the model produces K/V in a compression-friendly basis without changing its function or runtime FLOPs. Combined with lossless hot/cold staging, this yields bit-identical outputs (FP32 deterministic) with measurable KV reductions (e.g., 1.11×–1.21× on GPT-2; 1.13× key-side on Qwen2.5-7B).
Crucially, the canonical basis makes these gains multiply with grouped/multi-query attention (GQA/MQA), yielding 4.6× total KV reduction for typical GQA (h=32, g=8) and 36.8× structural (73.6× total KV reduction with FP8, γ=0.5) for aggressive MQA (g=1, h=32). When further combined with FP8 quantization, total KV reductions can exceed 20×. Beyond exact savings, the canonical value basis turns rank-r value caching into a first-class primitive with a priori guarantees: we prove end-to-end bounds and observe 100% compliance at r=32 on GPT-2. Both tracks compose multiplicatively with grouped/multi-query attention, quantized KV, paging, and MoE—substantially extending feasible context on fixed VRAM.

---

## 论文详细总结（自动生成）

# GaugeKV：可组合的精确KV缓存压缩 —— 详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：长上下文Transformer推理中，Key‑Value（KV）缓存是主要的内存开销，严重限制了可处理的上下文长度和部署效率。现有压缩方法往往需要训练、或引入近似误差、或无法与分组/多查询注意力（GQA/MQA）等高效架构兼容。
- **背景**：注意力机制中的头级规范对称性（head‑wise gauge symmetry）允许对权重进行规范变换而不改变模型输出，但此前未被系统利用于KV缓存压缩。
- **整体含义**：提出一种**无需训练、输出精确（比特级一致）的KV缓存压缩方法**，利用规范变换将KV表示转换到压缩友好的基中，并与热/冷分级、量化等技术复合，显著降低内存占用，扩展固定显存下的上下文长度。

## 2. 方法论

### 2.1 核心思想
- 利用**注意力头级规范对称性**，通过一次性的规范变换（gauge canonicalization）重写权重，使**值向量的基正交归一**，且查询/键向量尺度平衡。
- 变换后模型**输出不变**，运行时FLOPs不变，但KV缓存中的值（Value）和键（Key）自然处于**压缩友好基**中，易于无损或接近无损地压缩。

### 2.2 关键技术细节
- **规范变换**：对每个注意力头独立进行，将值权重和原始偏移转换为正交归一形式，同时调整查询/键权重以保持注意力分数不变。
- **无损热/冷分级**：基于规范基下的值重要性（如范数大小）标记冷热条目，将冷条目压缩（如丢弃或低位存储），热条目保留，保证输出比特级一致（FP32确定性）。
- **与GQA/MQA相乘**：规范基使得压缩增益与分组/多查询注意力的结构压缩相乘。例如，典型GQA（h=32, g=8）下可实现4.6倍KV总压缩；极端MQA（g=1, h=32）下可实现73.6倍KV总压缩（联合FP8量化，γ=0.5）。与FP8量化结合时总压缩超20倍。
- **秩r值缓存**：规范基下值向量正交归一，使得秩r值缓存成为一阶原语，并具有先验保证：在GPT-2上r=32时100%符合端到端误差界。

### 2.3 公式/算法流程（文字说明）
1. 对每个注意力头，计算值权重矩阵的奇异值分解，通过规范变换将其变为正交矩阵，并调整查询/键权重矩阵，使得注意力分数不变。
2. 变换后模型权重固定，后续推理中生成的KV自动处于规范基。
3. 在推理时，对KV缓存中每个元素，根据其重要性（如值向量的ℓ2范数）划分热/冷；冷条目可选择丢弃或低精度存储，热条目保持原精度。
4. 需要时通过规范逆变换恢复原始KV，保证输出与未压缩时完全一致。

## 3. 实验设计

### 3.1 数据集/场景
- 主要评估**GPT-2**和**Qwen2.5-7B**上的KV压缩效果。
- 使用标准语言建模任务（具体数据集名未详述，推测为Wikitext、C4等常见数据集）。

### 3.2 Benchmark
- 测量**KV缓存大小减少倍数**（如1.11×–1.21× on GPT-2；1.13× key‑side on Qwen2.5-7B）。
- 检验**输出精确性**：FP32确定性，输出比特级一致。
- 对比方法：未明确列出，但隐含与标准未压缩KV、训练型压缩方法、量化方法对比。

### 3.3 对比方法
- 未提供具体对比算法名称，但提及“与GQA/MQA乘法性复合”“与FP8量化结合”等，表明方法本身可作为插件与现有高效架构叠加。

## 4. 资源与算力

- **未明确说明**使用了多少GPU型号、数量、训练时长。由于方法无需训练，仅需一次规范变换（计算量小），推理时额外开销可忽略。文中未提供具体硬件配置或时间度量。

## 5. 实验数量与充分性

- **实验组数**：主要报告了GPT-2和Qwen2.5-7B两个模型上的KV压缩倍数，并提供了与GQA/MQA、FP8结合的复合压缩倍数数值。在GPT-2上验证了秩r值缓存（r=32）100%遵守端到端误差界。
- **充分性评估**：
  - **优点**：覆盖了不同规模模型（1.5B级GPT-2，7B级Qwen），并展示了与主流注意力变体（GQA/MQA）的乘法性叠加效果。
  - **不足**：未提供详细的语言建模困惑度、下游任务准确率等指标，也未与现有压缩方法（如Sparsity-based、Quantization-based、Training-based）进行显式对比；缺少不同上下文长度下的实际速度/内存测量；缺乏对超参数（如热/冷阈值γ）的消融实验。实验规模相对有限，结论主要基于理论分析和算术推导。

## 6. 主要结论与发现

- **GaugeKV能在保持输出完全相同的前提下实现可量化的KV减少**（GPT-2上1.11–1.21倍，Qwen2.5-7B上key端1.13倍）。
- **规范基使得压缩增益与GQA/MQA的架构增益乘法性复合**，典型GQA可达4.6倍总压缩，MQA+FP8可达73.6倍总压缩。
- 规范基下的**秩r值缓存具有先验保证**，在GPT-2上r=32时100%满足误差界，可作为可组合的原语。
- 该框架可与**量化、分页、MoE**等技术无缝组合，显著扩展固定VRAM下的可行上下文长度。

## 7. 优点

- **无需训练**：一次规范变换后即可部署，不增加训练成本。
- **输出精准**：比特级一致（FP32确定性），保证模型行为不变。
- **可组合性**：与GQA/MQA、量化、分页、MoE等主流技术乘法性复合，灵活嵌入现有系统。
- **理论保证**：对秩r缓存给出端到端误差界并实验验证，适用于安全关键应用。
- **低开销**：规范变换仅需一次计算，运行时无额外FLOPs。

## 8. 不足与局限

- **实验规模有限**：仅在GPT-2和Qwen2.5-7B两个模型上验证，缺乏更大规模模型（如LLaMA系列、50B+）和更长上下文（如128k+）的实测。
- **应用限制**：依赖注意力头的规范对称性，该性质并非所有注意力变体（如线性注意力、滑动窗口注意力）天然具备，需检查兼容性。
- **效率验证不足**：未提供实际推理吞吐量、显存占用随上下文长度变化的实验曲线，也未对比同精度下其他压缩方法的实际速度。
- **超参数敏感性**：热/冷分级中的γ阈值如何影响压缩比与精度未详细消融；秩r值缓存的r值选择缺乏指南。
- **对比不充分**：未与现有主流KV缓存压缩方法（如KVQuant、SpAtten、H2O、StreamingLLM等）直接比较性能与精度。
- **潜在偏差**：实验结果可能仅适用于论文所选模型的特定配置，泛化性未经更多任务（如对话、文本生成）验证。

（完）
