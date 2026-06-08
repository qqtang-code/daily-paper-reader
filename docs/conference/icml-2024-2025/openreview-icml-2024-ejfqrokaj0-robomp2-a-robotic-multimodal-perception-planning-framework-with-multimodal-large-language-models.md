---
title: "RoboMP$^2$: A Robotic Multimodal Perception-Planning Framework with Multimodal Large Language Models"
title_zh: RoboMP^2：基于多模态大语言模型的机器人多模态感知-规划框架
authors: "Qi Lv, Hao Li, Xiang Deng, Rui Shao, Michael Y Wang, Liqiang Nie"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=eJFQROkaj0"
tags: ["query:mm-cot"]
score: 8.0
evidence: 基于多模态大模型的感知-规划框架
tldr: 机器人在未知任务上泛化能力有限，且忽视了多模态环境信息。本文提出RoboMP^2框架，由目标条件多模态感知器和检索增强多模态规划器组成，利用多模态大语言模型进行机器人操作。在多个基准上验证了其出色的泛化能力和决策质量。该工作将多模态推理成功应用于具身智能。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-ejfqrokaj0/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 859, \"height\": 883, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ejfqrokaj0/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1595, \"height\": 790, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ejfqrokaj0/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1757, \"height\": 541, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ejfqrokaj0/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 561, \"height\": 326, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ejfqrokaj0/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1754, \"height\": 1066, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ejfqrokaj0/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1760, \"height\": 330, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ejfqrokaj0/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1478, \"height\": 2241, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-ejfqrokaj0/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1757, \"height\": 541, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-ejfqrokaj0/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1076, \"height\": 469, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-ejfqrokaj0/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1301, \"height\": 194, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-ejfqrokaj0/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 619, \"height\": 467, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-ejfqrokaj0/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 858, \"height\": 258, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-ejfqrokaj0/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 644, \"height\": 193, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-ejfqrokaj0/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 853, \"height\": 191, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-ejfqrokaj0/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 859, \"height\": 207, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-ejfqrokaj0/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1772, \"height\": 1552, \"label\": \"Table\"}]"
motivation: 现有端到端多模态模型在机器人任务上泛化能力不足，且缺乏对多模态环境信息的有效利用。
method: 提出包含目标条件多模态感知器和检索增强多模态规划器的RoboMP^2框架。
result: 在机器人操作任务上取得了优异的泛化性能和决策效果。
conclusion: 该框架展示了多模态大模型在具身智能中的潜力，提高了任务的泛化性。
---

## Abstract
Multimodal Large Language Models (MLLMs) have shown impressive reasoning abilities and general intelligence in various domains. It inspires researchers to train end-to-end MLLMs or utilize large models to generate policies with human-selected prompts for embodied agents. However, these methods exhibit limited generalization capabilities on unseen tasks or scenarios, and overlook the multimodal environment information which is critical for robots to make decisions. In this paper, we introduce a novel **Robo**tic **M**ultimodal **P**erception-**P**lanning (**RoboMP$^2$**) framework for robotic manipulation which consists of a Goal-Conditioned Multimodal Preceptor (GCMP) and a Retrieval-Augmented Multimodal Planner (RAMP). Specially, GCMP captures environment states by employing a tailored MLLMs for embodied agents with the abilities of semantic reasoning and localization. RAMP utilizes coarse-to-fine retrieval method to find the $k$ most-relevant policies as in-context demonstrations to enhance the planner. Extensive experiments demonstrate the superiority of RoboMP$^2$ on both VIMA benchmark and real-world tasks, with around 10% improvement over the baselines.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 核心问题与整体含义
- **研究动机**：现有机器人操作框架存在两大局限：一是端到端模型或基于提示的模型在未见过任务或场景上泛化能力差；二是它们仅依赖文本指令，忽略了关键的多模态环境信息（如物体空间关系、动态干扰等）。
- **整体含义**：本文提出 **RoboMP$^2$** 框架，借助多模态大语言模型（MLLMs）同时增强机器人的感知和规划能力，实现更深层的语义理解、复杂引用定位以及自适应策略生成，从而提升对未知任务的泛化性。

## 2. 方法论
- **核心思想**：将机器人操作拆分为感知与规划两个模块，分别利用MLLMs进行定制化改进。
- **Goal-Conditioned Multimodal Perceptor (GCMP)**  
  - 功能：根据图像和引用表达式（如“蓝色方块下方的橙色块”）输出目标坐标。  
  - 架构：视觉编码器（ViT）+ 语言编码器（flan‑t5‑xl），通过MLP连接；并引入LoRA进行高效微调。  
  - 训练数据格式：`{image, ref_exp, coordinates}` 三元组，采用自回归损失 $L = -\sum_k \log P(y_{k+1} | y_{<k}, (x_I, x_T); \theta)$。
- **Retrieval-Augmented Multimodal Planner (RAMP)**  
  - 流程：先通过**粗检索器**（TF‑IDF）从代码库（约50个程序）中召回 $K$ 个候选；然后经**指令重写器**（GPT‑4）提取核心操作，再用**精细重排器**（SentenceBERT）进行语义排序，最终选出 $k$ 个最相关的策略作为上下文示例。  
  - 最终输入：完整提示模板 + 多模态环境图像 + 选出的示例，由GPT‑4V生成代码形式的高层计划。

## 3. 实验设计
- **数据集与场景**：
  - **VIMABench**（17个任务，难度L1‑L4，其中L4为未见任务）。
  - **真实世界任务**（6个：基本操作、相同形状、相同颜色、操纵旧邻居、干扰操作等）。
- **对比方法**：
  - 端到端模型：Gato、Flamingo、VIMA、RT‑2。
  - 基于提示的方法：VisProg、CaP、I2A。
- **评估指标**：成功率（Success Rate）。

## 4. 资源与算力
- **GCMP训练**：8×A100‑80G‑SXM4 平台，训练时间约24小时。  
  - 超参数：epoch=10，batch size=128，融合模块学习率3e‑5，LoRA学习率1e‑4，优化器AdamW，余弦学习率衰减。  
- **RAMP**：基于GPT‑4（重写器）和GPT‑4V（多模态生成器）API调用，本文未报告具体API计算量。

## 5. 实验数量与充分性
- **多组实验**：
  - VIMABench上全部17任务的完整结果（表8）。
  - 真实世界6个任务的对比（表2）。
  - 消融实验：移除粗检索、指令重写、语义重排、整个RAMP模块（表4）。
  - 不同相似度度量（TF‑IDF、BM25、SentenceBERT）与λ值对比（表5）。
  - 多模态 vs 纯文本规划器对比（表6）。
  - 感知器对比：GCMP vs SAM+CLIP vs Shikra（表7）。
  - 鲁棒性测试：用GPT‑4扩充指令后的表现（表3）。
  - 定性可视化（图5）。
- **充分性评价**：实验覆盖了多种难度、多种场景，且进行了全面的消融和对比，较为客观和公平。但真实世界任务数量偏少（6个），且未分析失败案例。

## 6. 主要结论与发现
- RoboMP$^2$ 在VIMABench上平均成功率 **82.4%**，比最优基线提升约 **10%**；在L4未见任务上提升约 **20%**。
- 真实世界任务平均成功率 **79.2%**，大幅优于I2A（39.2%）。
- 消融实验证实：粗检索、指令重写、语义重排、多模态信息均对性能有显著贡献。
- GCMP能够处理基于属性、空间关系、知识推理的复杂引用，远超现有感知器（如SAM+CLIP）。

## 7. 优点
- **感知突破**：首次将MLLM定制为机器人感知器，解决复杂语义引用定位问题。
- **规划自适应**：检索增强策略自动选择最相关演示，避免人工提示模板的泛化不足与干扰。
- **多模态融合**：规划时纳入环境图像，使策略对环境变化（如干扰物体）做出合理响应。
- **实验全面**：涵盖仿真与真实场景、不同难度级别、多项消融及鲁棒性测试。

## 8. 不足与局限
- **依赖强大API**：规划器基于GPT‑4V，推理成本高、延迟大，不适用于实时场景。
- **真实任务数量有限**：仅6个任务，场景多样性不足，可能存在选择偏差。
- **未分析失败案例**：无法揭示具体错误模式（如感知错误还是规划错误）。
- **代码库规模小**：仅约50条程序，可能限制了复杂任务的覆盖。
- **迁移性待验证**：对完全不同的机器人平台或非固定场景的泛化能力尚未评估。

（完）
