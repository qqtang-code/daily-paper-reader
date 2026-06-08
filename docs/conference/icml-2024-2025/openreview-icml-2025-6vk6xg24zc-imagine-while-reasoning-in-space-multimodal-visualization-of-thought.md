---
title: "Imagine While Reasoning in Space: Multimodal Visualization-of-Thought"
title_zh: 在空间中边想象边推理：多模态可视化思维
authors: "Chengzu Li, Wenshan Wu, Huanyu Zhang, Yan Xia, Shaoguang Mao, Li Dong, Ivan Vulić, Furu Wei"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=6vk6Xg24ZC"
tags: ["query:mm-cot"]
score: 9.0
evidence: 多模态链式思维生成可视化推理轨迹，用于空间推理
tldr: 传统链式思维在复杂空间推理任务中表现不足，因为人类推理不仅依赖语言还依赖视觉想象。本文提出多模态可视化思维(MVoT)，让多模态大模型在推理过程中生成图像来可视化思维轨迹，并引入令牌差异损失保证图像质量。在空间推理基准上，MVoT显著优于标准CoT方法。该工作拓展了多模态推理的新范式。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-6vk6xg24zc/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 776, \"height\": 471, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-6vk6xg24zc/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1759, \"height\": 823, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-6vk6xg24zc/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 642, \"height\": 470, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-6vk6xg24zc/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1642, \"height\": 763, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-6vk6xg24zc/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 483, \"height\": 486, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-6vk6xg24zc/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1768, \"height\": 1376, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-6vk6xg24zc/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1760, \"height\": 1576, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-6vk6xg24zc/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1749, \"height\": 413, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-6vk6xg24zc/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 275, \"height\": 288, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-6vk6xg24zc/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 793, \"height\": 598, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-6vk6xg24zc/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1754, \"height\": 480, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6vk6xg24zc/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 777, \"height\": 200, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6vk6xg24zc/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1327, \"height\": 369, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6vk6xg24zc/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 894, \"height\": 405, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6vk6xg24zc/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 945, \"height\": 365, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6vk6xg24zc/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 632, \"height\": 576, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6vk6xg24zc/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 723, \"height\": 216, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6vk6xg24zc/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 988, \"height\": 406, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6vk6xg24zc/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1329, \"height\": 112, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6vk6xg24zc/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1713, \"height\": 960, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6vk6xg24zc/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1071, \"height\": 1287, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6vk6xg24zc/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1772, \"height\": 752, \"label\": \"Table\"}]"
motivation: 链式思维缺乏视觉思维，在空间推理中受限。
method: MVoT生成图像可视化推理轨迹，并使用令牌差异损失提升保真度。
result: 在空间推理任务上超越了标准链式思维方法。
conclusion: 可视化思维能有效增强多模态模型的空间推理能力。
---

## Abstract
Chain-of-Thought (CoT) prompting has proven highly effective for enhancing complex reasoning in Large Language Models (LLMs) and Multimodal Large Language Models (MLLMs). Yet, it struggles in complex spatial reasoning tasks. Nonetheless, human cognition extends beyond language alone, enabling the remarkable capability to think in both words and images. Inspired by this mechanism, we propose a new reasoning paradigm, Multimodal Visualization-of-Thought (MVoT). It enables visual thinking in MLLMs by generating image visualizations of their reasoning traces. To ensure high-quality visualization, we introduce token discrepancy loss into autoregressive MLLMs. This innovation significantly improves both visual coherence and fidelity. We validate this approach through several dynamic spatial reasoning tasks. Experimental results reveal that MVoT demonstrates competitive performance across tasks. Moreover, it exhibits robust and reliable improvements in the most challenging scenarios where CoT fails. Ultimately, MVoT establishes new possibilities for complex reasoning tasks where visual thinking can effectively complement verbal reasoning.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：传统的 Chain-of-Thought（CoT）在复杂空间推理任务中表现不佳，因为它仅依赖文本推理，无法像人类那样同时使用语言和视觉想象进行认知。
- **背景**：人类认知基于双编码理论，同时处理语言和非语言（视觉）信息。现有多模态推理方法要么依赖两阶段（先描述再推理），要么依赖外部工具（如代码解释器），限制了模型的原生多模态推理能力。
- **目标**：提出 Multimodal Visualization-of-Thought（MVoT），让多模态大模型在推理过程中生成图像作为“视觉思维”，从而在文字和图像之间无缝切换，提升空间推理的准确性和可解释性。

## 2. 论文提出的方法论

### 核心思想
- MVoT 让 MLLM 生成**交错的多模态推理轨迹**：每个推理步骤包含文字思考（verbal thought）和对应的图像可视化（visual thought），后者作为当前状态的“心智图像”。
- 利用**原生多模态自回归模型**（如 Chameleon-7B）实现，该模型统一处理文本和图像 token。

### 关键技术细节
- **模型架构**：基于 Chameleon（统一 Transformer），使用图像 tokenizer（Esser et al.）和文本 tokenizer，将图像和文本均转化为离散 token 序列，由因果 Transformer 建模。
- **训练方式**：在任务数据上微调（LoRA），输入为交错的文本-图像对，输出为包含推理轨迹的文本和图像。训练时计算所有 token 的损失。
- **Token Discrepancy Loss（令牌差异损失）**：
  - 由于图像 tokenizer 和文本 tokenizer 是分别训练的，导致视觉嵌入空间与语言模型预测空间不匹配，影响生成图像质量。
  - LD 损失：对于第 i 个图像 token，计算其标签的视觉嵌入与所有 codebook 条目之间的 MSE 距离，然后用该距离向量与预测的概率分布做点积，惩罚偏离正确嵌入的预测。
  - 总损失：L = LC（交叉熵损失）+ LD。

### 推理流程
- 给定多模态输入 x，MVoT 依次生成：verbal thought z_i → visual thought v_i → 下一个 verbal thought z_{i+1}，直到得出答案。

## 3. 实验设计

### 数据集/场景
- **MAZE**：迷宫导航，给定初始迷宫图（带起点）和动作序列，预测最终位置（A/B/C/D）。网格大小 3-6。
- **MINI BEHAVIOR**：安装打印机任务（InstallingAPrinter），需拾取打印机并放到桌子上。预测任务成功或失败原因（A/B/C/D）。网格大小 7-10。
- **FROZEN LAKE**：冰湖行走，避免跌入洞中到达礼物。预测成功、掉洞或安全但未到达（A/B/C）。网格大小 3-6，有复杂图案。

### 对比方法
- **Direct**：直接输出答案，无中间推理。
- **CoT（带环境布局）**：用文本描述环境和坐标，逐步推理。
- **CoT（不带环境布局）**：仅用坐标，无环境描述。
- **Interleaved**：训练时也使用交错文本-图像对，但只计算文本 token 的损失，图像不参与损失。
- **MVoT**：本文方法。
- **GPT-4o**：多种设置（零样本、零样本 CoT、加上 MVoT 生成的视觉思维作为插件）。

### 评估指标
- **任务准确率**：多选题准确率。
- **可视化质量**：V-Acc（可视化准确性）、V-Red（冗余模式率）、V-Steps（连续正确步数）、V-Ratio（连续正确比例）。仅对 MAZE 和 MINI BEHAVIOR 自动评估（FROZEN LAKE 图案复杂）。

## 4. 资源与算力

- **模型**：Anole-7B（基于 Chameleon-7B 修改），支持交错图像文本生成。
- **训练**：使用 LoRA 微调，40 个 epoch。
- **GPU**：具体配置见表8：
  - Direct / CoT / Interleaved：8 块 GPU（MI300X）。
  - MVoT：32 块 GPU（MI300X）。
- **推理**：GPT-4o 使用 Azure 部署的 2024-07-01 版本。

（论文未明确说明训练耗时，但给出了 GPU 数量。）

## 5. 实验数量与充分性

- **实验组数**：共在 3 个任务上对比了 5 种方法（加上 GPT-4o 的多种变体），每个任务均报告整体和按 grid size 划分的细粒度结果。
- **消融实验**：
  - 有无 token discrepancy loss 的对比（表3、图4）。
  - 有无环境布局的 CoT 消融（表1）。
  - MVoT 与 CoT 的互补性分析（表2，计算联合上界）。
  - 不同 grid size 下的性能对比（表15、16）。
- **充分性**：实验设计系统，覆盖不同复杂度场景，对比了多种基线，包含消融和可视化质量分析。结果报告了多次运行？未明确但使用了固定随机种子。总体客观公平。

## 6. 论文的主要结论与发现

1. **MVoT 在复杂空间推理上优于 CoT**：在 FROZEN LAKE 上 MVoT 准确率 85.6%，而 CoT 仅 61.5%（甚至低于 Direct 77.9%）；在 MAZE 和 MINI BEHAVIOR 上 MVoT 也达到 93% 和 95%，与 CoT 相当或略低但更鲁棒。
2. **鲁棒性更强**：CoT 在环境复杂度增加时性能下降（如 FROZEN LAKE 从 6×6 降 39%），MVoT 稳定在 83% 以上；CoT 对文本描述质量敏感，MVoT 不依赖文本描述环境。
3. **Token Discrepancy Loss 提升可视化质量**：加入 LD 后，V-Acc 从约 64% 提高到 93%（MAZE），V-Red 从 49% 降至 10%，并提升任务性能。
4. **MVoT 与 CoT 互补**：两者联合预测的上界接近 100%（MAZE）和 92%（FROZEN LAKE），表明融合两种思维策略有潜力。
5. **MVoT 可作为插件增强其他模型**：为 GPT-4o 提供 MVoT 生成的视觉思维后，准确率提升 >15%。

## 7. 优点

- **创新性**：首次提出让 MLLM 在推理过程中原生生成图像作为“视觉思维”，实现真正的多模态推理轨迹。
- **方法与架构巧妙**：利用自回归 MLLM 的统一 token 表示，通过 token discrepancy loss 缓解嵌入空间不匹配问题，提升生成质量。
- **全面实验**：涵盖多个任务、多种 baseline、细粒度 grid 分析、消融和互补性分析，验证了方法的有效性和鲁棒性。
- **可扩展性**：MVoT 可作为插件用于其他模型（如 GPT-4o），不局限于单一架构。
- **可解释性**：可视化推理轨迹便于人类理解模型决策过程。

## 8. 不足与局限

- **可视化质量仍有提升空间**：生成的图像有时会重构任务无关的细节（如 FROZEN LAKE 背景），而忽略预期修改；细节易模糊（受 tokenization 精度限制）。
- **计算开销大**：生成多个图像 token 导致推理速度慢，MVoT 需要 32 个 GPU 训练，资源需求高。
- **依赖特定模型**：当前实现基于 Chameleon（Anole-7B），虽然理论上可扩展，但未验证其他架构。
- **评估限制**：FROZEN LAKE 的自动可视化质量评估未进行（因图案复杂），仅做了任务准确率和定性分析；领域仅限简单的网格世界，未在真实复杂场景（如 3D 空间）验证。
- **数据集规模**：每个任务约 5000-7000 训练样本，中等规模，但可能不足以泛化到更复杂现实任务。
- **未讨论多次运行统计**：虽然设了种子，但未报告多次重复实验的方差。

（完）
