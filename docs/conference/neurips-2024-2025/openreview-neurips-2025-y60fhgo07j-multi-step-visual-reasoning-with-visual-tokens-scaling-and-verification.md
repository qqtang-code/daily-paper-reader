---
title: Multi-step Visual Reasoning with Visual Tokens Scaling and Verification
title_zh: 多步视觉推理中的视觉Token缩放与验证
authors: "Tianyi Bai, Zengjie Hu, Fupeng Sun, Qiu Jiantao, Yizhen Jiang, Guangxin He, Bohan Zeng, Conghui He, Binhang Yuan, Wentao Zhang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=y60FhgO07j"
tags: ["query:mm-cot"]
score: 9.0
evidence: 推理时视觉Token缩放与验证引导的迭代推理
tldr: 多模态大语言模型（MLLM）通常将图像编码为固定视觉token，限制了推理时的迭代细化能力。本文提出推理时视觉token缩放框架，通过验证器引导，模型能够迭代地选择性地关注视觉内容并更新理解。这实现了一种动态的多步视觉推理范式，类似于人类感知的反馈驱动过程。实验表明该方法在需要多步细节理解的视觉问答任务上取得显著提升。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-y60fhgo07j/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1112, \"height\": 1048, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-y60fhgo07j/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1395, \"height\": 563, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-y60fhgo07j/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1363, \"height\": 1670, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-y60fhgo07j/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1463, \"height\": 1913, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-y60fhgo07j/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1401, \"height\": 1606, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-y60fhgo07j/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 183, \"height\": 230, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-y60fhgo07j/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 57, \"height\": 54, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-y60fhgo07j/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 163, \"height\": 214, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-y60fhgo07j/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 153, \"height\": 150, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-y60fhgo07j/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 56, \"height\": 53, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-y60fhgo07j/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 231, \"height\": 158, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-y60fhgo07j/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 275, \"height\": 183, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-y60fhgo07j/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 242, \"height\": 169, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-y60fhgo07j/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 305, \"height\": 209, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-y60fhgo07j/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 195, \"height\": 257, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-y60fhgo07j/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 177, \"height\": 232, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-y60fhgo07j/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 127, \"height\": 145, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-y60fhgo07j/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 223, \"height\": 183, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-y60fhgo07j/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 206, \"height\": 167, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-y60fhgo07j/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 222, \"height\": 217, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-y60fhgo07j/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 195, \"height\": 197, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-y60fhgo07j/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 253, \"height\": 194, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-y60fhgo07j/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 164, \"height\": 125, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-y60fhgo07j/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 133, \"height\": 107, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-y60fhgo07j/fig-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 167, \"height\": 131, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-y60fhgo07j/fig-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 196, \"height\": 136, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-y60fhgo07j/fig-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 178, \"height\": 122, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-y60fhgo07j/fig-028.webp\", \"caption\": \"\", \"page\": 0, \"index\": 28, \"width\": 205, \"height\": 142, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-y60fhgo07j/fig-029.webp\", \"caption\": \"\", \"page\": 0, \"index\": 29, \"width\": 1397, \"height\": 1497, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-y60fhgo07j/fig-030.webp\", \"caption\": \"\", \"page\": 0, \"index\": 30, \"width\": 1394, \"height\": 1576, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-y60fhgo07j/fig-031.webp\", \"caption\": \"\", \"page\": 0, \"index\": 31, \"width\": 1401, \"height\": 1377, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-y60fhgo07j/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1452, \"height\": 599, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-y60fhgo07j/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 816, \"height\": 392, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-y60fhgo07j/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 826, \"height\": 209, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-y60fhgo07j/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 710, \"height\": 642, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-y60fhgo07j/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 970, \"height\": 228, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-y60fhgo07j/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1450, \"height\": 266, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-y60fhgo07j/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1180, \"height\": 269, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-y60fhgo07j/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 835, \"height\": 231, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-y60fhgo07j/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 730, \"height\": 150, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-y60fhgo07j/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1245, \"height\": 230, \"label\": \"Table\"}]"
motivation: 静态固定视觉token限制了MLLM在推理时动态调整理解的能力。
method: 提出推理时视觉token缩放，结合验证器引导的迭代推理过程。
result: 在多项视觉推理任务上超越固定token基线。
conclusion: 实现了更灵活、更类似人类的视觉推理机制。
---

## Abstract
Multi-modal large language models (MLLMs) have achieved remarkable capabilities by integrating visual perception with language understanding, enabling applications such as image-grounded dialogue, visual question answering, and scientific analysis. However, most MLLMs adopt a static inference paradigm, encoding the entire image into fixed visual tokens upfront, which limits their ability to iteratively refine understanding or adapt to context during inference. This contrasts sharply with human perception, which is dynamic, selective, and feedback-driven.
In this work, we introduce a novel framework for inference-time visual token scaling that enables MLLMs to perform iterative, verifier-guided reasoning over visual content. We formulate the problem as a Markov Decision Process, involving a reasoner that proposes visual actions and a verifier—trained via multi-step Direct Preference Optimization (DPO)—that evaluates these actions and determines when reasoning should terminate. To support this, we present a new dataset, VTS, comprising supervised reasoning trajectories (VTS-SFT) and preference-labeled reasoning comparisons (VTS-DPO).
Our method significantly outperforms existing approaches across diverse visual reasoning benchmarks, offering not only improved accuracy but also more interpretable and grounded reasoning processes. These results demonstrate the promise of dynamic inference mechanisms for enabling fine-grained, context-aware visual reasoning in next-generation MLLMs. Code and datasets are publicly released at https://vts-v.github.io/.

---

## 论文详细总结（自动生成）

# 论文总结：Multi-Step Visual Reasoning with Visual Tokens Scaling and Verification

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：现有多模态大语言模型（MLLM）采用**静态推理范式**：将整个图像一次性编码为固定数量的视觉 token，后续推理仅基于该静态表示。这导致模型无法在推理过程中根据上下文动态调整视觉理解，难以处理模糊、遮挡或细节缺失的情况，与人类“动态、选择、反馈驱动”的感知过程形成鲜明对比。
- **核心挑战**：缺乏一个灵活的框架，使模型能在推理时**主动决策**该观察什么、如何聚焦、何时停止，从而实现细粒度、上下文相关的视觉推理。
- **研究目标**：提出一种**推理时视觉 token 缩放**框架，让 MLLM 能够通过验证器引导的迭代过程，逐步增强对图像的理解，提升复杂视觉推理任务的准确性和可解释性。

## 2. 提出的方法论

### 核心思想
将视觉推理形式化为一个**马尔可夫决策过程（MDP）**，包含两个核心组件：
- **推理器（Reasoner）**：一个预训练的 VLM，配备可插拔的视觉工具模块（如裁剪、OCR、深度估计、目标检测等），负责在每个步骤生成规划文本、选择工具并执行动作。
- **验证器（Verifier）**：一个通过**多步直接偏好优化（Multi-step DPO）** 训练的模型，用于评估推理动作的质量，并决定何时终止推理。

### 关键技术细节
1. **状态与动作**：每一步包含规划（文本 token）、动作（选择视觉工具）、观测（工具执行结果）。推理器根据当前历史生成下一个规划，并动作。
2. **推理器训练**：使用监督微调（SFT）在 VTS-SFT 数据集上训练，损失函数为交叉熵，同时优化规划和动作生成。
3. **验证器训练**：基于 VTS-DPO 数据集（包含偏好对：正确轨迹 vs 错误轨迹），通过多步 DPO 优化，使验证器能输出奖励分数，指导推理器继续或停止。
4. **终止条件**：若当前步与上一步的奖励差小于阈值 ε，则终止推理。理论保证（定理 3.2）表明该停止时间几乎必然有界。

### 算法流程（文字描述）
- 输入：图像-问题对 s1
- 迭代过程：
  1. 推理器生成规划 th
  2. 推理器选择动作 ah 并执行，得到观测 oh
  3. 验证器计算奖励差 Δr
  4. 若 Δr < ε 则终止，否则进入下一步
- 最终输出：最后一步的规划作为答案。

## 3. 实验设计

### 使用数据集
- **训练数据集**：基于 LLaVA-OneVision 的单图像部分，采样 83 类任务，通过 Qwen2.5-VL-72B 生成初始推理轨迹，经 LLM 裁判过滤后得到 315K 高质量轨迹。
  - VTS-SFT：315K 正确轨迹，用于推理器 SFT。
  - VTS-DPO：301K 偏好对（正确 vs 错误轨迹），用于验证器 DPO 训练。

### 评估基准（Benchmarks）
- **BLINK**：13 个子任务（深度、空间、拼图、视觉对应、语义对应、艺术风格、计数、功能对应、局部、多视图、反射、法医、相似性），共约 1300 样本。
- **V*Bench**：细粒度视觉搜索。
- **MMStar**：通用视觉问答。
- **MathVista**：视觉数学推理。

### 对比方法
- **闭源模型**：GPT-4o 及其变体（零样本、CoT、SoM、Visual Sketchpad、MMFactory）。
- **开源模型**：Qwen2-VL-7B、Qwen2.5-VL-7B、LLaMA-3.2-Vision-11B，分别评估：
  - 基础模型
  - 基础模型 + VTS-V（无微调）
  - 经过 VTS-SFT 微调后的模型 + VTS-V（即完整方法）

## 4. 资源与算力

- **硬件**：8 张 NVIDIA A800 GPU（80GB）。
- **训练超参数**（附录 B 表 4）：
  - LoRA rank=8, α=16, dropout=0，目标所有线性层。
  - 学习率 3e-5，cosine 调度，warmup 比例 0.03。
  - Batch size：每设备 1，梯度累积步 1，共 1 个 epoch。
  - 最大长度 65536，bf16 混合精度。
- **估算**：未明确给出训练总时长，但基于 8 卡 A800 和 1 epoch（315K 样本），训练时间应在数小时至一天内。推理时每步约 3 秒（附录 E 分析）。

## 5. 实验数量与充分性

- **主要实验**：表 1（BLINK 13 子任务，对比 8 种方法，共约 100+ 个结果）、表 2（三个基准，9 行对比）、表 3（消融实验，3 模型 + 2 种移除条件）。
- **补充实验**（附录）：
  - 推理开销分析（附录 E）
  - 扩展基准（附录 F，GPT-4o + VTS-V 在 V*Bench/MMStar/MathVista）
  - 视觉 token 缩放分析（附录 H）
  - 验证器鲁棒性（附录 I，数据集组成）
  - 分离 reasoner/verifier 效果（附录 J）
  - 可解释性示例（附录 K）
  - 不同工具使用模式（附录 L）
- **评估**：实验覆盖了多种模型、多种任务类型，对比了主流闭源与开源基线，消融实验验证了各组件贡献。整体充分、公平，但缺少大规模额外计算如多次运行取方差。

## 6. 主要结论与发现

- **VTS-V 显著提升性能**：
  - GPT-4o + VTS-V 在 BLINK 平均 69.15%（+6.90% 相对基线），优于所有对比方法（CoT、SoM、Sketchpad、MMFactory）。
  - 开源模型 SFT 后 + VTS-V 也获显著提升：Qwen2.5-VL-7B +7.58%，Qwen2-VL-7B +4.18%，LLaMA-3.2-11B +2.34%。
- **Verifier 至关重要**：移除 verifier 后性能下降（表 3），说明其引导作用。
- **SFT 数据集关键**：无 SFT 的开源模型无法产生有效工具调用（LLaMA-3.2 直接失败），SFT 后恢复并超越。
- **泛化性好**：在 V*Bench、MMStar、MathVista 上也有提升（附录 F）。
- **可解释性增强**：推理轨迹包含显式动作和中间观测，便于人工审查。

## 7. 优点

- **理论创新**：将视觉推理形式化为 MDP，并证明停止时间有界。
- **框架通用**：可用于闭源（GPT-4o）和开源模型，无需微调即可提升闭源模型。
- **数据集贡献**：首个大规模多步视觉工具推理数据集（VTS-SFT/DPO），覆盖 80+ 任务，可促进后续研究。
- **实验扎实**：多基准、多模型、多消融，结论可靠。
- **可解释性**：推理过程透明，每个步骤可视化。

## 8. 不足与局限

- **工具集固定**：仅支持预定义的 10 种视觉工具，扩展性受限于工具库。
- **验证器泛化性**：当前 verifier 针对特定训练分布，对分布外任务适应性可能有限（作者在局限性部分提到）。
- **开源模型需要微调**：直接应用 VTS-V 到未微调的开源模型会降低性能，需先进行 SFT，增加了使用成本。
- **推理开销**：平均约 3 秒/样本（GPT-4o），比单步推理慢，但已在附录分析中讨论。
- **实验可重复性**：未提供多次运行的标准差，统计显著性未明确报告。
- **局限性声明**：作者指出未来可扩展工具集和提升 verifier 适应性。

（完）
