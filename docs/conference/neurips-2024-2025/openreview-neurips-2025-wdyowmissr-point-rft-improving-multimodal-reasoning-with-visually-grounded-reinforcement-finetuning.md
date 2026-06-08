---
title: "Point-RFT: Improving Multimodal Reasoning with Visually Grounded Reinforcement Finetuning"
title_zh: Point-RFT：利用视觉基础强化微调改进多模态推理
authors: "Minheng Ni, Zhengyuan Yang, Linjie Li, Chung-Ching Lin, Kevin Lin, Wangmeng Zuo, Lijuan Wang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=wdyOwMISSR"
tags: ["query:mm-cot"]
score: 10.0
evidence: 视觉基础链式推理与强化微调
tldr: Point-RFT提出一种多模态推理框架，利用视觉基础链式推理进行文档理解。第一阶段进行格式微调（71K视觉推理问题，含逐步标注），第二阶段使用强化微调对齐视觉和语言。有效减少幻觉并增强多模态集成。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-wdyowmissr/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1431, \"height\": 703, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wdyowmissr/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1439, \"height\": 727, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wdyowmissr/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1428, \"height\": 813, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wdyowmissr/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1454, \"height\": 742, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wdyowmissr/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 729, \"height\": 674, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wdyowmissr/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 661, \"height\": 676, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wdyowmissr/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1433, \"height\": 501, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-wdyowmissr/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 965, \"height\": 295, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wdyowmissr/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1448, \"height\": 243, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wdyowmissr/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 780, \"height\": 261, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wdyowmissr/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 665, \"height\": 261, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wdyowmissr/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 549, \"height\": 178, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wdyowmissr/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1446, \"height\": 264, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wdyowmissr/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 857, \"height\": 611, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wdyowmissr/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1243, \"height\": 356, \"label\": \"Table\"}]"
motivation: 文本CoT在视觉语言任务中存在幻觉和集成不足问题。
method: 先进行格式微调，再使用视觉基础强化微调对齐多模态推理。
result: 在视觉文档理解任务上减少幻觉，提升推理准确性。
conclusion: 视觉基础CoT和强化微调有效改进了多模态推理质量。
---

## Abstract
Recent advances in large language models have significantly improved textual reasoning through the effective use of Chain-of-Thought (CoT) and reinforcement learning. However, extending these successes to vision-language tasks remains challenging due to inherent limitations in text-only CoT, such as visual hallucinations and insufficient multimodal integration. In this paper, we introduce Point-RFT, a multimodal reasoning framework explicitly designed to leverage visually grounded CoT reasoning for visual document understanding. Our approach consists of two stages: First, we conduct format finetuning using a curated dataset of 71K diverse visual reasoning problems, each annotated with detailed, step-by-step rationales explicitly grounded to corresponding visual elements. Second, we employ reinforcement finetuning targeting visual document understanding. On ChartQA, our approach improves accuracy from 70.88% (format-finetuned baseline) to 90.04%, surpassing the 83.92% accuracy achieved by reinforcement finetuning relying solely on text-based CoT. The result shows that our grounded CoT is more effective for multimodal reasoning compared with the text-only CoT. Moreover, Point-RFT exhibits superior generalization capability across several out-of-domain visual document reasoning benchmarks, including CharXiv, PlotQA, IconQA, TabMWP, etc., and highlights its potential in complex real-world scenarios.

---

## 论文详细总结（自动生成）

# 论文总结：Point-RFT: Improving Multimodal Reasoning with Visually Grounded Reinforcement Finetuning

## 1. 核心问题与研究动机

- **背景**：大型语言模型（LLM）通过链式思考（CoT）和强化学习（RL）在文本推理上取得巨大成功；但直接将这些技术扩展到视觉语言任务时，纯文本CoT存在**视觉幻觉**和**多模态集成不足**的根本性限制。
- **核心问题**：如何让模型在推理过程中不仅生成文本思路，还能显式地引用和定位图像中的具体视觉元素，从而提升多模态推理的准确性和可解释性。
- **研究目标**：提出一个视觉基础链式思考（visually grounded CoT）的强化微调框架，有效减少幻觉，增强感知-推理对齐。

## 2. 方法论

### 核心思想：两阶段训练框架
- **第一阶段：监督格式微调（SFT）**  
  使用精心构建的**Point-CoT数据集**（71K样本），每个推理步骤都附带指向图像中具体点的坐标标注，训练模型生成符合格式的“思考+指向+答案”输出。
  - 模板：`<think> <points...>...</points> ... </think> <answer>...</answer>`
  - 损失函数：标准交叉熵损失，仅对SFT阶段使用。
- **第二阶段：强化微调（RFT）**  
  采用**GRPO（Group-wise Relative Policy Optimization）** 算法，结合两项奖励：
  - **格式奖励（R_f）**：通过正则表达式检查输出是否严格遵循模板（`<think>`和`<answer>`标签完整性）。
  - **准确性奖励（R_a）**：根据预测答案与真实答案的匹配（数值容忍±5%相对误差）给予奖励。
  - 总奖励：`R = R_f + R_a`
  - 优化目标：在保持KL散度约束下最大化期望奖励（参考PPO/GRPO）。
- **训练过程**：SFT在Point-CoT上训练500步；RL在ChartQA训练集（15K）上训练100步。

### 关键技术细节
- **Point-CoT数据集构建**：
  1. 使用**GPT-4o**为每个图像-问题-答案三元组生成逐步推理文本，其中显式提及视觉元素并标记`<point>`。
  2. 使用**Molmo-7B**（定位专家模型）为每个提及的视觉元素生成原始图像坐标点，并通过交叉验证（文本中声称的元素数量与定位实例数量一致）过滤幻觉和错误。
  3. 数据来源：Mammoth-VL子集（ChartQA、DVQA、PlotQA、CLEVR、TallyQA），共71K样本。
- **模型架构**：基于**Qwen2.5-VL-7B**作为基础模型进行微调。

## 3. 实验设计

### 数据集与Benchmark
- **域内（In-Domain）**：**ChartQA**（官方测试集）—— 图表理解问答。
- **域外（Out-of-Domain）**：
  - CharXiv（学术论文中的科学图表）
  - PlotQA（统计图趋势与数值推理）
  - IconQA（图标符号推理）
  - TabMWP（表格数学推理）
  - Counting（基于SuperCLEVR的物体计数）

### 对比方法
- **Base**：Qwen2.5-VL-7B无微调（直接输出CoT）。
- **Base-RFT**：纯文本CoT + GRPO强化微调（无点标注）。
- **Point-SFT**：使用Point-CoT进行监督微调（含点标注）。
- **Point-RFT**：Point-SFT基础上再用GRPO强化微调（含点标注）。

### 评估指标
- **Overall**：从`<answer>`标签中提取内容并与真实答案匹配的准确率。
- 消融实验还报告**Format**（格式合规率）和**Inner**（合规样本中的准确率）。

## 4. 资源与算力

- **GPU配置**：8块NVIDIA A100 GPU（使用PyTorch和Easy-R1框架）。
- **训练超参数**：
  - 优化器：AdamW，学习率5e-5。
  - SFT：batch size 512，训练500步。
  - RL：batch size 56，训练100步（β=0.00）。
- 论文未详细报告总训练时长，但指出训练在合理步数内收敛。

## 5. 实验数量与充分性

- **主要实验结果**：在**6个数据集**上对比了4种方法（包含域内外），并报告了统计显著性（p<0.01的t检验）。
- **消融实验**：
  1. **指向格式**：XML vs JSON语法，索引方案（0基 vs 1基）的影响。
  2. **显式指向的必要性**：移除点标注后性能大幅下降（SFT准确率从56.72%降至27.60%）。
  3. **训练步数**：SFT在500步达到最佳，RL随步数单调提升至100步。
  4. **训练数据集**：混合其他数据集反而降低性能，证实针对性格式学习更有效。
- **额外分析**：定性案例（域内图表、域外图表、推理步骤演化、泛化场景）展示了模型行为。
- **数据质量验证**：用10名志愿者和GPT-4o分别验证1000个随机样本，高质量比例分别为94.5%和96.8%。
- **整体评价**：实验设计全面，覆盖多个维度（域内、域外、消融、定性），对比基线合理，统计显著性表明结果可靠。实验充分且客观。

## 6. 主要结论与发现

- **核心结论**：视觉基础CoT（Point-RFT）在**ChartQA**上将准确率从70.88%（Base）提升至**90.04%**，远超纯文本强化微调（Base-RFT）的83.92%，验证了视觉基础CoT对多模态推理更有效。
- **泛化能力**：在5个域外数据集上平均准确率**53.16%**，而Base-RFT仅33.80%，证明视觉基础推理可迁移至新视觉布局。
- **可解释性**：点指向机制允许分离感知错误与推理错误，便于诊断和改进。
- **强化学习的作用**：RL进一步提升了SFT模型的性能（Point-SFT 87.21% → Point-RFT 90.04%），并改善了域外泛化。

## 7. 优点

1. **方法创新**：首个将视觉基础CoT与强化微调结合的多模态推理框架。
2. **数据质量高**：双模型交叉验证（GPT-4o + Molmo-7B）有效过滤幻觉，数据集质量接近95%。
3. **显著提升与泛化**：域内大幅领先，域外平均提升近20个百分点，展示强迁移能力。
4. **可解释性与诊断价值**：通过点坐标可精确定位感知错误，为模型改进提供明确方向。
5. **开放性**：承诺开源模型、代码和数据集，便于复现和后续研究。

## 8. 不足与局限

1. **计算成本高**：两阶段训练（SFT + RL）需要较大算力（8×A100），且RL可能对超参数敏感。
2. **推理延迟大**：逐步骤生成点和文本的顺序解码方式在复杂文档上可能导致显著延迟。
3. **应用范围有限**：实验主要集中于图表/文档视觉问答，对自然场景、开放式视觉问答等任务的泛化性尚未验证。
4. **依赖外部模型**：数据集构建依赖GPT-4o和Molmo-7B，可能存在偏见或标注噪声（尽管交叉验证降低风险）。
5. **评估维度单一**：主要报告准确率，缺乏对推理质量、鲁棒性（如对抗样本）的深入分析。
6. **未讨论公平性与安全性**：论文未涉及潜在的偏见、滥用风险或社会影响，这部分在附录中未充分展开。

（完）
