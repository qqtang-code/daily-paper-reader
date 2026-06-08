---
title: "Visual Graph Arena: Evaluating Visual Conceptualization of Vision and Multimodal Large Language Models"
title_zh: 视觉图竞技场：评估视觉和多模态大语言模型的视觉概念化能力
authors: "Zahra Babaiee, Peyman Kiasari, Daniela Rus, Radu Grosu"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=BCJPAmlfxv"
tags: ["query:mm-cot"]
score: 7.0
evidence: 通过图基推理评估多模态大模型的视觉概念化能力
tldr: 多模态大模型在视觉问答中表现优异，但抽象概念化推理仍存差距。作者提出Visual Graph Arena，包含六种基于图的任务，使用不同布局（如Kamada-Kawai和平面对布局）测试模型能否忽略视觉形式进行推理。实验表明前沿模型与人类存在巨大鸿沟：人类接近满分而模型表现不佳。该工作强调了多模态推理中视觉抽象能力的重要性。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1718, \"height\": 404, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1673, \"height\": 481, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1646, \"height\": 951, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 565, \"height\": 252, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 334, \"height\": 297, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 386, \"height\": 246, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 843, \"height\": 482, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1418, \"height\": 2031, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1690, \"height\": 878, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1694, \"height\": 877, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1691, \"height\": 876, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1690, \"height\": 875, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1688, \"height\": 874, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1689, \"height\": 877, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1715, \"height\": 609, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1715, \"height\": 608, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1716, \"height\": 608, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1714, \"height\": 610, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1718, \"height\": 608, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1091, \"height\": 1097, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1093, \"height\": 1098, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1095, \"height\": 1097, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1095, \"height\": 1098, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1097, \"height\": 1099, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 1097, \"height\": 1101, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-bcjpamlfxv/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1504, \"height\": 235, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bcjpamlfxv/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1588, \"height\": 704, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bcjpamlfxv/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 826, \"height\": 317, \"label\": \"Table\"}]"
motivation: 多模态模型在视觉概念化推理上存在明显不足，缺乏相关评估。
method: 设计基于六种图任务的基准，用不同布局测试视觉抽象推理。
result: 人类几乎完美，而多模态模型表现远低，显示视觉概念化缺陷。
conclusion: 视觉抽象能力是多模态推理的关键瓶颈，需进一步研究。
---

## Abstract
Recent advancements in multimodal large language models have driven breakthroughs in visual question answering. Yet, a critical gap persists, `conceptualization'—the ability to recognize and reason about the same concept despite variations in visual form, a basic ability of human reasoning. To address this challenge, we introduce the Visual Graph Arena (VGA), a dataset featuring six graph-based tasks designed to evaluate and improve AI systems’ capacity for visual abstraction. VGA uses diverse graph layouts (e.g., Kamada-Kawai vs. planar) to test reasoning independent of visual form. Experiments with state-of-the-art vision models and multimodal LLMs reveal a striking divide: humans achieved near-perfect accuracy across tasks, while models totally failed on isomorphism detection and showed limited success in path/cycle tasks. We further identify behavioral anomalies suggesting pseudo-intelligent pattern matching rather than genuine understanding. These findings underscore fundamental limitations in current AI models for visual understanding. By isolating the challenge of representation-invariant reasoning, the VGA provides a framework to drive progress toward human-like conceptualization in AI visual models. The Visual Graph Arena is available at: \href{https://vga.csail.mit.edu/}{vga.csail.mit.edu}.

---

## 论文详细总结（自动生成）

# Visual Graph Arena 论文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：当前视觉和多模态大语言模型在视觉问答任务上取得显著进展，但缺乏“概念化”（conceptualization）能力——即在不同视觉形式（如不同图形布局）下识别并推理同一概念的能力。这种能力是人脑基本推理能力的一部分。
- **研究动机**：现有的评估基准多关注表面特征或分布外泛化，但专门测试“表示不变性推理”的基准不足。作者选择图（graph）作为理想测试媒介，因为图结构包含节点、边和布局，人类可轻松理解，而AI容易受布局变化干扰。
- **整体含义**：通过构建Visual Graph Arena（VGA）基准，揭示当前AI在视觉抽象推理上与人类的巨大差距，推动向类人概念化能力的研究。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：设计一组基于图的视觉推理任务，训练集和测试集使用不同的图形布局（如Kamada-Kawai布局 vs 平面布局），迫使模型从底层结构而非表面视觉特征做出判断，从而隔离“概念化”能力。
- **关键技术细节**：
  - VGA包含六个任务，分为三大类：
    - **图同构**：易（随机非同构对）和难（度等价非同构对），二分类。
    - **路径**：哈密顿路径存在性（二分类）和最短路径长度（四分类：1,2,3,4）。
    - **环**：哈密顿环存在性（二分类）和最大无弦环长度（四分类：3,4,5,6）。
  - 每个图的节点数为8~9，保证视觉可解析性。
  - 训练数据用一种布局（如随机或Kamada-Kawai），测试数据换用其他布局（如平面布局），共3种布局（随机、Kawai、平面）。
  - 数据量：每个任务训练样本2.5万~14万，测试样本0.25万~1.57万，平衡正负样本。
  - 可视化采用700×700像素的绘图，节点形状（圆或方）区分标记点。

## 3. 实验设计：数据集、基准、对比方法

- **数据集**：VGA本身作为基准数据集，包含六个子任务，每个任务有独立的训练/测试划分。
- **人类基准**：15名工程院学生/员工，每任务4道题，共24题，人具备对图的一般理解但并非专家。
- **对比模型**：
  - **视觉模型（Vision Models）**：ViT-Base、Swin-T-Base、ConvNeXt-Base（ImageNet监督预训练）；SigLIP-Base（多模态视觉-语言预训练）；DINOv2-Base（自监督）。所有模型在VGA任务上微调10个epoch。
  - **多模态大模型（MLLMs）**：GPT-4o、GPT-o1、Claude 3 Opus、Claude 3.5 Sonnet、Google Gemini。对每任务随机取100个样本进行零样本测试。
- **评估设置**：
  - 视觉模型：训练后测试不同布局的测试集（同构任务仅用Kawai+平面；最短路径任务测试三个布局；其余任务训练Kawai、测试平面）。
  - MLLMs：直接给出图像和文字问题，要求输出答案。

## 4. 资源与算力

- **明确信息**：
  - 视觉模型训练使用2块NVIDIA TITAN RTX GPU。
  - 优化器：Adam，学习率1e-4，batch size 32，训练10个epoch。
  - 输入图像大小：384×384像素。
- **未明确说明**：训练时长（小时）、总计算量（FLOPs）、MLLMs API调用成本、人类实验的设施等未提及。

## 5. 实验数量与充分性

- **实验数量**：
  - 视觉模型：5种架构 × 6个任务 = 30组微调实验，每个任务报告最佳验证准确率。
  - MLLMs：5个模型 × 6个任务 = 30组零样本评估（每任务100样本）。
  - 人类：1组实验，15人×24题。
  - 额外分析：GPT-o1的混淆矩阵、异常行为分析（中间分数异常、更简单更差异常）。
- **充分性与公平性**：
  - **优点**：覆盖多种模型类型（CNN、Transformer、自监督、多模态），任务设计系统（同构、路径、环），布局变化严格分离训练/测试。
  - **不足**：
    - 人类样本量小（15人），统计显著性有限。
    - MLLMs每任务仅100样本，可能不足以准确评估性能。
    - 未进行消融实验（如不同布局的训练比例、不同节点数的影响）。
    - 未考虑模型在预训练阶段是否见过类似图数据（虽然作者提及确认模型训练数据中包含图相关内容）。
    - 未测试视觉模型在不同布局组合下的迁移（如训练用平面、测试用Kawai）。

## 6. 论文的主要结论与发现

- **人类表现**：接近完美，准确率88%~100%，最大无弦环任务最低（88.2%）。
- **视觉模型**：
  - 所有模型在同构检测上完全失败（近乎随机），仅SigLIP在易同构上达到54.4%。
  - 其他任务表现远低于人类，ConvNeXt在所有未失败任务中表现最佳（如最短路径Kawai测试82.4%），优于Transformer架构。
  - 最大无弦环任务对所有视觉模型最困难（最高ConvNeXt仅36.3%）。
- **MLLMs**：
  - GPT-4o、Claude 3.5 Sonnet等在所有任务上失败（接近随机或完全错误）。
  - GPT-o1在最短路径（55%）和哈密顿环（66%）上略高于随机，但表现出异常行为：
    - **更简单更差异常**：相邻节点（长度1）准确率29%远低于长度2的69%。
    - **中间分数异常**：部分任务出现非100%或50%的中间性能，暗示伪智能。
  - GPT-o1的哈密顿环成功主要依赖识别叶节点（叶子节点→无环），而非真正的图概念理解。
- **核心发现**：当前AI模型在视觉概念化（表示不变性推理）上存在根本性缺陷，依赖表面模式匹配而非深度抽象理解。

## 7. 优点

- **任务设计巧妙**：通过训练/测试布局分离，精确衡量概念化能力，避免模型学到布局特定假相关。
- **数据规模充分**：每个任务数万样本，适合深度学习微调。
- **多维度评估**：同时测试视觉模型和多种MLLMs，并纳入人类基线，提供完整对比。
- **发现异常行为**：提出“中间分数异常”和“更简单更差异常”两种现象，揭示伪智能模式，具有诊断价值。
- **开源性**：数据集和网站公开（vga.csail.mit.edu），便于复现和扩展。
- **可扩展性**：方法可推广到其他抽象表示领域（化学结构、逻辑电路等）。

## 8. 不足与局限

- **节点规模限制**：仅8~9个节点，无法测试更大规模图的推理能力（可能受绘图可读性约束）。
- **人类实验样本有限**：15名被试、每题仅4个样本，统计稳健性不足。
- **MLLMs评估样本少**：每任务100个样本，且未进行多次随机抽样或置信区间分析。
- **缺乏消融研究**：未分析不同训练布局、不同节点数、不同模型初始化方式的影响。
- **训练数据泄露风险**：虽提及确认模型训练数据包含图，但未系统评估测试图是否在预训练集中出现。
- **仅涉及图领域**：概念化能力广泛存在，未在其他视觉抽象领域（如流程图、分子结构）验证。
- **未使用强化学习等新方法**：仅测试标准监督微调和零样本MLLM，未探索如RL训练能否改善概念化。

（完）
