---
title: Learning to Reason Iteratively and Parallelly for Complex Visual Reasoning Scenarios
title_zh: 学习在复杂视觉推理场景中迭代与并行推理
authors: "Shantanu Jaiswal, Debaditya Roy, Basura Fernando, Cheston Tan"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=uoJQ9qadjY"
tags: ["query:mm-cot"]
score: 8.0
evidence: 迭代与并行推理机制用于复杂视觉问答
tldr: 复杂视觉问答需要多步组合推理，但现有方法难以动态存储和调用中间结果。本文提出迭代并行推理机制(IPRM)，融合串行计算（逐步推理）和并行计算（同时处理多个子问题），在CLEVR等数据集上实现了更优的逐步推理能力，且不需要显式步骤标注。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-uojq9qadjy/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1342, \"height\": 402, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-uojq9qadjy/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1327, \"height\": 359, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-uojq9qadjy/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 357, \"height\": 629, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-uojq9qadjy/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 807, \"height\": 464, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-uojq9qadjy/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 554, \"height\": 410, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-uojq9qadjy/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1451, \"height\": 256, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-uojq9qadjy/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1443, \"height\": 716, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-uojq9qadjy/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1338, \"height\": 2261, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-uojq9qadjy/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 547, \"height\": 369, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-uojq9qadjy/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1336, \"height\": 1317, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-uojq9qadjy/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1316, \"height\": 2248, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-uojq9qadjy/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1346, \"height\": 2255, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-uojq9qadjy/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1524, \"height\": 1601, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-uojq9qadjy/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1511, \"height\": 1734, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-uojq9qadjy/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1526, \"height\": 1594, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-uojq9qadjy/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 694, \"height\": 348, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-uojq9qadjy/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 698, \"height\": 250, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-uojq9qadjy/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 696, \"height\": 239, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-uojq9qadjy/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 721, \"height\": 208, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-uojq9qadjy/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1433, \"height\": 103, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-uojq9qadjy/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1439, \"height\": 330, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-uojq9qadjy/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 685, \"height\": 352, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-uojq9qadjy/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1442, \"height\": 215, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-uojq9qadjy/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 680, \"height\": 454, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-uojq9qadjy/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 938, \"height\": 325, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-uojq9qadjy/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 493, \"height\": 410, \"label\": \"Table\"}]"
motivation: 复杂视觉推理需要动态的多步计算和记忆，现有方法缺乏灵活的步骤组合机制。
method: 提出IPRM，结合迭代式逐步推理和并行处理分支，通过注意力机制动态路由计算资源。
result: "在CLEVR等多个复杂VQA数据集上，IPRM准确率超过先前方法的SOTA，平均提升3%。"
conclusion: 迭代与并行的融合为复杂视觉推理提供了一种有效的神经网络架构。
---

## Abstract
Complex visual reasoning and question answering (VQA) is a challenging task that requires compositional multi-step processing and higher-level reasoning capabilities beyond the immediate recognition and localization of objects and events. Here, we introduce a fully neural Iterative and Parallel Reasoning Mechanism (IPRM) that combines two distinct forms of computation -- iterative and parallel -- to better address complex VQA scenarios.  Specifically, IPRM's "iterative" computation facilitates compositional step-by-step reasoning for scenarios wherein individual operations need to be computed, stored, and recalled dynamically (e.g. when computing the query “determine the color of pen to the left of the child in red t-shirt sitting at the white table”). Meanwhile, its  "parallel'' computation allows for the simultaneous exploration of different reasoning paths and benefits more robust and efficient execution of  operations that are mutually independent (e.g. when counting individual colors for the query: "determine the maximum occurring color amongst all t-shirts'"). We design IPRM as a lightweight and fully-differentiable neural module that can be conveniently applied to both transformer and non-transformer vision-language backbones. It notably outperforms prior task-specific methods and transformer-based attention modules across various image and video VQA benchmarks testing distinct complex reasoning capabilities such as compositional spatiotemporal reasoning (AGQA), situational reasoning (STAR), multi-hop reasoning generalization (CLEVR-Humans) and causal event linking (CLEVRER-Humans). Further, IPRM's internal computations can be visualized across reasoning steps, aiding interpretability and diagnosis of its errors.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：复杂视觉推理与问答（VQA）要求模型能够进行组合式的多步处理和高阶推理，例如因果关联、逻辑推理、时空处理等。然而，现有方法在处理这类任务时面临两个关键挑战：一是需要动态地计算、存储和回溯中间结果（如“红T恤小孩左边桌子的笔的颜色”）；二是需要同时处理多个相互独立的操作（如“统计所有T恤中出现最多的颜色”）。
- **背景**：纯迭代计算（step-by-step）适用于序列化操作，但在处理独立并行操作时效率低且容易遗忘；而纯并行计算（如Transformer的注意力机制）虽然能同时处理多个信息，但难以实现逐步组合推理。因此，论文提出融合迭代与并行两种计算范式的必要性。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：提出**迭代并行推理机制（IPRM）**，它是一个全可微的神经网络模块，内部维护一个“工作记忆”`M = {M_op, M_res}`，其中`M_op`是操作状态（operation states），`M_res`是对应的结果状态（result states）。IPRM在多个推理步骤中交替进行三个子阶段：操作形成（Operation Formation）、操作执行（Operation Execution）、操作组合（Operation Composition），从而既支持逐步迭代推理，又能并行处理多个独立操作。
- **关键技术细节**：
  - **操作形成**：基于当前操作状态`M_op`，通过注意力机制从语言特征`XL`中检索相关信息，生成一组新的潜在操作`Z_op`（Nop个并行操作）。
  - **操作执行**：基于新操作`Z_op`和当前结果状态`M_res`，通过视觉注意力从视觉特征`XV`中检索相关信息，生成对应的新结果`Z_res`。这里使用了特征调制（feature modulation）来联合指导注意力。
  - **操作组合**：将新操作和结果与历史记忆进行融合，通过交叉注意力（inter-operation attention）实现动态组合，更新记忆状态。其中使用了自掩码（self-mask）防止操作关注自身，并支持窗口大小为W的回溯。
  - **推理输出**：在最后一步，通过注意力池化从最终操作状态中提取推理结果`ys`，同时输出所有推理步骤的注意力权重，便于可视化。
- **公式与算法流程**：具体公式见论文式(1)-(19)，核心包括线性投影、注意力计算、特征调制、循环更新等。IPRM是权重共享的，参数数量不随推理步骤或并行操作数变化。

## 3. 实验设计

- **使用的数据集与benchmark**：
  - **视频推理**：STAR（情景推理）、AGQAv2（组合时空推理）、CLEVRER-Humans（因果事件关联）。
  - **图像推理**：CLEVR-Humans（多跳推理泛化）、CLEVR-CoGenT（属性组合泛化）、CLOSURE（系统泛化）、GQA（真实图像组合VQA）。
- **对比方法**：
  - 视频任务：LRR、All-in-One、Temp[ATP]、MIST、InternVideo、SeViLA-BLIP2、Concat-Att、Cross-Att等。
  - 图像任务：PG+EE、NS-VQA、FiLM、MAC、MDETR、MCAN、LXMERT、OSCAR等。
- **评价指标**：准确率（Acc.），部分任务分问题类型和设置（零样本/微调/从头训练）。

## 4. 资源与算力

- 论文明确说明：所有实验使用**单张NVIDIA A40 GPU（46GB内存）**，批量大小根据数据集调整（最大216）。训练时长未具体说明，但提到在CLEVR-Humans上预训练35个epoch，微调40个epoch；STAR上训练20个epoch；AGQAv2上8个epoch；CLEVRER-Humans上从头训练250个epoch等。总体算力需求中等。

## 5. 实验数量与充分性

- **实验数量**：约包含7个主要基准（含多个子任务），以及详细的消融实验（并行操作数Nop vs. 迭代步数T、操作组合块、降维比r、窗口长度W）。此外还有不同训练数据比例实验、CLIP集成实验。
- **充分性与公平性**：
  - 对比方法覆盖了任务专用方法、大型预训练模型、以及相同架构的注意力变体（Concat-Att、Cross-Att）。
  - 消融实验系统性强，控制了关键超参数。
  - 所有结果报告了多次重复（至少3个种子）的平均值（未明确给出误差棒，但附录提及）。
  - 在STAR上还使用了ground-truth视觉输入和预测视觉输入两种设置，验证了方法的鲁棒性。
  - 总体实验设计较为全面、客观，但部分对比方法（如LRR）使用了额外监督，论文也做了公平比较（如LRR去掉辅助任务后性能下降）。

## 6. 论文的主要结论与发现

- IPRM在多个复杂视觉推理基准上达到了新的最先进结果：
  - STAR平均准确率69.9%（比先前最佳高5%）。
  - AGQAv2总体60.4%（比先前最佳高5%）。
  - CLEVRER-Humans零样本/微调/从头训练均显著提升。
  - CLEVR-Humans零样本63.8%、微调85.5%，超过MDETR等。
  - CLEVR-CoGenT泛化80.3%，CLOSURE零样本75.6%。
  - GQA上60.3%，超过LXMERT等大型模型（但不使用额外预训练数据）。
- 迭代与并行计算的结合是关键：单独使用迭代或并行性能均大幅下降。
- IPRM内部注意力可被可视化，有助于解释错误案例。

## 7. 优点

- **方法创新性**：首次在单一神经网络模块中明确融合迭代与并行两种计算范式，结构简洁、可微分、端到端可训练。
- **通用性强**：可灵活应用于Transformer和非Transformer的视觉-语言骨干，无需额外监督（如程序、边界框）。
- **参数高效**：IPRM仅4.4M参数，远低于同类注意力模块（如MDETR 17.4M）。
- **可解释性好**：支持跨推理步骤的注意力可视化，有助于诊断错误。
- **实验验证全面**：覆盖图像和视频、合成与真实、多种推理能力，消融实验严谨。

## 8. 不足与局限

- **实验覆盖**：虽然在多个基准上达到SOTA，但在STAR的“可行性”类型问题中，IPRM弱于SeViLA-BLIP2，说明在处理需要常识知识的问题上仍有不足。
- **偏差风险**：论文承认IPRM可能继承训练数据中的偏见（视觉、语言、文化），且可视化工具可帮助识别但未完全解决。
- **应用限制**：IPRM主要面向复杂VQA场景，未在纯语言或具身推理等任务上验证，尽管论文认为有潜力。
- **计算资源**：未报告完整训练时间，对于更大型任务（如视频）可能需要更长时间，但总体算力需求可接受。
- **鲁棒性**：在预测视觉输入（非ground-truth）下性能下降约9%，表明依赖检测器质量。

（完）
