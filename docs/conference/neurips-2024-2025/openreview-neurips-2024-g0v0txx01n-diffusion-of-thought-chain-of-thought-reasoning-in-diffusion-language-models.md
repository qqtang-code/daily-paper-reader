---
title: "Diffusion of Thought: Chain-of-Thought Reasoning in Diffusion Language Models"
title_zh: 扩散思维：扩散语言模型中的链式推理
authors: "Jiacheng Ye, Shansan Gong, Liheng Chen, Lin Zheng, Jiahui Gao, Han Shi, Chuan Wu, Xin Jiang, Zhenguo Li, Wei Bi, Lingpeng Kong"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=G0v0TxX01N"
tags: ["query:mm-cot"]
score: 7.0
evidence: 扩散语言模型中的链式推理
tldr: 自回归语言模型通过逐token生成进行推理，扩散模型提供了另一种范式。本文提出扩散思维(DoT)，将链式推理融入扩散语言模型，允许推理步骤在时间上扩散，而非从左到右生成。该方法在多个推理任务上取得竞争力结果，且可灵活权衡计算量与推理质量。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-g0v0txx01n/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 665, \"height\": 637, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-g0v0txx01n/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1445, \"height\": 411, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-g0v0txx01n/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 493, \"height\": 390, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-g0v0txx01n/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1385, \"height\": 521, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-g0v0txx01n/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1440, \"height\": 983, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-g0v0txx01n/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 636, \"height\": 306, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-g0v0txx01n/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1438, \"height\": 469, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-g0v0txx01n/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1335, \"height\": 223, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-g0v0txx01n/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 755, \"height\": 248, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-g0v0txx01n/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 641, \"height\": 327, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-g0v0txx01n/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 542, \"height\": 397, \"label\": \"Table\"}]"
motivation: 自回归模型推理受限于从左到右的生成顺序，扩散模型提供并行生成的可能。
method: 将链式推理步骤建模为扩散过程，通过迭代去噪生成推理序列，同时保留步骤间依赖。
result: 在算术和符号推理任务上，DoT相比同参数自回归模型准确率相当，但推理延迟更低。
conclusion: 扩散模型为链式推理提供了新的计算权衡维度，值得进一步探索。
---

## Abstract
Recently, diffusion models have garnered significant interest in the field of text processing due to their many potential advantages compared to conventional autoregressive models.
In this work, we propose Diffusion-of-Thought (DoT),  a novel approach that integrates diffusion models with Chain-of-Thought, a well-established technique for improving the reasoning ability of autoregressive language models. In contrast to autoregressive language models that make decisions in a left-to-right, token-by-token manner, DoT allows reasoning steps to diffuse over time through a diffusion language model and offers greater flexibility in trading-off computation for reasoning performance. Our experimental results demonstrate the effectiveness of DoT in multi-digit multiplication, boolean logic, and grade school math problems. In addition to that, DoT showcases promising self-correction abilities and benefits from existing reasoning-enhancing techniques like self-consistency decoding. Our findings contribute to the understanding and development of reasoning with diffusion language models.

---

## 论文详细总结（自动生成）

# Diffusion of Thought: 扩散语言模型中的链式推理

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **背景**：大语言模型（LLMs）在推理任务中表现突出，链式推理（CoT）通过逐步生成中间推理步骤显著提升了复杂推理能力。然而，自回归（AR）模型的逐token左到右生成方式存在效率低下、错误累积以及难以自纠正等问题。
- **动机**：扩散模型在文本处理领域显示出潜力（如全局规划、自纠正、效率优势），但尚未被充分探索用于复杂推理。本文提出关键问题：扩散语言模型能否利用CoT风格的技术来获得增强的复杂推理能力？
- **核心目标**：提出一种名为**Diffusion-of-Thought (DoT)** 的方法，将CoT与扩散模型自然融合，让推理步骤在扩散时间步上并行“扩散”，从而实现推理效率与性能的灵活折中。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 2.1 核心思想
- DoT不再像AR模型那样从左到右逐个token生成推理链，而是在扩散模型的反向去噪过程中，所有推理步骤（思想）的隐表示随时间步并行更新。
- 通过**部分加噪（partial noising）** 方式，保留问题陈述（输入）不变，仅对推理步骤序列进行扩散和去噪，实现条件生成。
- 提出了**单遍（Single-Pass）** 和**多遍（Multi-Pass, DoT MP）** 变体。多遍变体生成一步推理后，将其加入条件再生成下一步，引入因果偏置。

### 2.2 关键技术细节
1. **训练策略**：
   - **计划采样（Scheduled Sampling）**：在训练时以一定概率用模型自生成的噪声替代真实噪声，让模型学习从自身错误中恢复。
   - **耦合采样（Coupled Sampling）**：针对DoT MP，在训练时不仅对当前推理步加噪，还对前序推理步也加噪，增强鲁棒性。
2. **推理加速**：
   - 采用**条件ODE求解器**（基于DPM-Solver）加速连续扩散模型的采样，可将所需步数从数千降至数十步。
3. **自洽性（Self-consistency）**：类似AR模型中的自洽性解码，通过多次采样并多数投票进一步提升性能。
4. **训练目标**：最小化变分下界（VLB），结合扩散损失和舍入损失。

## 3. 实验设计：数据集、场景、基准与对比方法

### 3.1 数据集与场景
- **简单任务**：
  - 四位乘法（4×4）和五位乘法（5×5）——来自BIG-bench基准。
  - 布尔逻辑推理任务（Boolean logic）。
- **复杂任务**：
  - GSM8K（小学数学应用题），使用增强训练集。

### 3.2 基准模型与对比方法
- **基线方法**：
  - Answer-only（直接输出答案）
  - Chain-of-Thought (CoT)（自回归生成推理链）
  - Implicit CoT（将思想隐藏到Transformer层中）
- **基础模型**：
  - 自回归：GPT-2（small/medium/large），ChatGPT（few-shot）
  - 扩散：从零训练的DoT（类似DiffuSeq），以及微调预训练模型Plaid (1.3B)、SEDD (small/medium)
- **评测指标**：准确率（Accuracy）和吞吐量（Throughput，样本数/秒）

## 4. 资源与算力

- **GPU**：8块NVIDIA V100 32GB GPU。
- **训练时长**（App B.3）：
  - DoT（单遍）训练约29小时；DoT MP约10小时。
  - SEDD微调设置200k步，其他训练细节见附录。
- **其他**：使用fp16精度（因V100不支持bf16），Adam优化器。

## 5. 实验数量与充分性

- **实验数量**：
  - 主要实验：在三个简单任务（4×4、5×5、布尔逻辑）和一个复杂任务（GSM8K）上对比多种方法。
  - 消融实验：包括梯度引导 vs. 无分类器引导、计划采样与耦合采样的影响、使用ODE求解器的加速效果、自洽性采样数量的影响、不同扩散步数T的性能-效率折中。
  - 自纠正能力分析：给出了逐时间步的推理案例。
- **充分性评估**：
  - 覆盖了不同难度、不同模型规模（从零训练到微调预训练模型）、不同架构（连续扩散Plaid、离散扩散SEDD）。
  - 对比了同规模AR模型（GPT-2）以及更大规模的ChatGPT。
  - 实验设计较全面，统计显著性通过多次运行验证（附录B.3末尾提及）。
  - 局限性：仅聚焦数学/逻辑推理，未扩展到其他自然语言推理任务；预训练扩散模型规模远小于当前主流LLM。

## 6. 论文的主要结论与发现

1. **有效性**：DoT在简单推理任务上可达100%准确率，且吞吐量显著高于AR CoT（最高27倍加速）。
2. **复杂任务**：在GSM8K上，基于SEDD-medium的DoT优于同参数GPT-2-medium（53.5% vs. 43.9%），甚至超过更大模型；基于Plaid的DoT也接近GPT-2-small CoT性能。
3. **灵活性**：DoT可通过调整扩散步数T灵活控制计算量与性能，简单任务仅需1-2步，复杂任务增加步数即可持续提升。
4. **自纠正能力**：扩散模型的多步去噪天然支持自纠正，结合计划采样和耦合采样进一步强化，能够修正中间推理错误。
5. **自洽性收益**：自洽性解码对DoT同样有效，且扩散模型自然产生多样性推理路径。
6. **架构差异**：DoT的推理无需遵循左到右顺序，中间步骤可以并行或非单调更新。

## 7. 优点：方法或实验设计的亮点

- **新颖的方法融合**：首次将CoT与扩散模型结合，突破了AR模型的生成范式。
- **效率-性能可调**：通过简单调整推理步数即可为不同难度任务选择合适的计算量，这是AR模型难以做到的。
- **自纠正优势**：扩散模型的迭代去噪过程天然支持纠错，实验展示了模型在推理阶段的错误识别与修复能力。
- **实验设计全面**：对比了多种基线（AR、Implicit CoT、ChatGPT），覆盖从零训练与微调预训练模型，并进行了充分的消融分析。
- **代码开源**：便于复现和后续研究。

## 8. 不足与局限

- **预训练模型规模有限**：当前扩散语言模型（如Plaid 1.3B、SEDD-medium 424M）远小于流行LLM（如GPT-4、Llama 7B），限制了直接比较的公平性。
- **需要额外训练**：DoT需要在目标任务上微调或从零训练，缺乏zero-shot推理能力（本文仅初探微调范式）。
- **任务覆盖窄**：仅测试了数学和逻辑推理，未涉及常识推理、阅读理解等更广泛NLP推理任务。
- **潜在偏差风险**：模型可能继承训练数据中的统计偏差，生成结果需谨慎解读。
- **计算资源**：尽管效率可调，但扩散模型在需要高质量生成时仍需较多步数（如64步），对于实时性要求极高的场景仍有压力。
- **未探讨更大规模**：由于缺乏更大规模的预训练扩散模型，无法验证DoT在LLM级别的表现。

（完）
