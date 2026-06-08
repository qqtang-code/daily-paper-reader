---
title: "VisionGraph: Leveraging Large Multimodal Models for Graph Theory Problems in Visual Context"
title_zh: VisionGraph：利用大型多模态模型解决视觉环境中的图论问题
authors: "yunxin li, Baotian Hu, Haoyuan Shi, Wei Wang, Longyue Wang, Min Zhang"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=gjoUXwuZdy"
tags: ["query:mm-cot"]
score: 9.0
evidence: 视觉图上的多步骤多模态推理链
tldr: 现有大型多模态模型在视觉数学推理上表现优异，但在图论问题上的多步推理能力尚未被充分探索。本文设计了VisionGraph基准，涵盖8种复杂图问题，并提出描述-程序-推理(DPR)链来增强模型的多步推理。实验表明，DPR链显著提升了模型在视觉图任务上的推理准确率。该工作拓展了多模态模型在结构化视觉推理中的应用。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-gjouxwuzdy/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1580, \"height\": 1265, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-gjouxwuzdy/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 383, \"height\": 335, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-gjouxwuzdy/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 373, \"height\": 332, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-gjouxwuzdy/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 793, \"height\": 263, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-gjouxwuzdy/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 831, \"height\": 637, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-gjouxwuzdy/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 284, \"height\": 272, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-gjouxwuzdy/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 461, \"height\": 433, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-gjouxwuzdy/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 582, \"height\": 623, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-gjouxwuzdy/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 597, \"height\": 649, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-gjouxwuzdy/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 585, \"height\": 630, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-gjouxwuzdy/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 580, \"height\": 622, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-gjouxwuzdy/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1675, \"height\": 521, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-gjouxwuzdy/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1735, \"height\": 290, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-gjouxwuzdy/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1671, \"height\": 1467, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-gjouxwuzdy/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1734, \"height\": 929, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-gjouxwuzdy/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1689, \"height\": 2332, \"label\": \"Table\"}]"
motivation: 多模态模型在图论视觉问题上缺乏多步推理能力，亟需基准和方法。
method: 提出VisionGraph基准和DPR链，结合描述生成、程序执行和推理步骤。
result: DPR链在多种图推理任务上显著提升了大型多模态模型的性能。
conclusion: 证明了链式推理在多模态图问题中的有效性，为后续研究提供基准。
---

## Abstract
Large Multimodal Models (LMMs) have achieved impressive success in visual reasoning, particularly in visual mathematics. However, problem-solving capabilities in graph theory remain less explored for LMMs, despite being a crucial aspect of mathematical reasoning that requires an accurate understanding of graphical structures and multi-step reasoning on visual graphs. To step forward in this direction, we are the first to design a benchmark named **VisionGraph**, used to explore the capabilities of advanced LMMs in solving multimodal graph theory problems. It encompasses eight complex graph problem tasks, from connectivity to shortest path problems. Subsequently, we present a Description-Program-Reasoning (DPR) chain to enhance the logical accuracy of reasoning processes through graphical structure description generation and algorithm-aware multi-step reasoning. Our extensive study shows that 1) GPT-4V outperforms Gemini Pro in multi-step graph reasoning; 2) All LMMs exhibit inferior perception accuracy for graphical structures, whether in zero/few-shot settings or with supervised fine-tuning (SFT), which further affects problem-solving performance; 3) DPR significantly improves the multi-step graph reasoning capabilities of LMMs and the GPT-4V (DPR) agent achieves SOTA performance.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：大型多模态模型（LMMs）在视觉数学推理（如代数、几何）上已取得显著成功，但在图论问题上的多步推理能力尚未被充分探索。图论推理要求准确理解图结构（节点、边）并进行多步推理，这对于机器人规划、视觉语言导航等实际场景至关重要。
- **整体含义**：本文旨在首次系统评估 LMMs 在视觉图结构理解与多步推理上的能力，填补了这一领域的空白。通过设计专用基准和方法，揭示了当前 LMMs 在图空间感知上的短板，并为提升多模态模型的复杂推理能力提供了新方向。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：提出 **Description-Program-Reasoning (DPR)** 链，通过“自然语言描述 + 程序生成 + 推理验证”的迭代方式，增强 LMMs 在视觉图推理上的逻辑准确性。
- **关键技术细节**：
  1. **图结构描述生成**：使用经过图理解数据增强的小模型（如 LLaVA-7b）生成高精度的图描述（节点数、边列表等）。
  2. **邻接矩阵构建**：将图像和描述输入 GPT-4V，要求其以三元组形式输出邻接矩阵。
  3. **算法选择与代码生成**：让 GPT-4V 选择合适图论算法（如 DFS、Dijkstra）并生成对应 Python 代码。
  4. **多步推理**：可结合外部 Python 解释器执行代码，验证推理结果，最终给出符合格式的答案。
- **整体流程**：DPR 将复杂任务分解为感知增强、代码生成、工具调用等子步骤，形成闭环的多模态 Agent。

## 3. 实验设计
- **数据集/基准**：**VisionGraph** 基准，基于 NLGraph 扩展，包含 8 种图论问题（连通性、环检测、拓扑排序、最短路径、最大流、二分图匹配、哈密顿路径、图神经网络）。共 5,902 个问题，每个图附带 3 个子问题（节点识别、边识别、具体图论问题）。分为 easy、medium、hard 三个难度级别（节点数从 5 到 35 不等）。
- **对比方法**：
  - 商业 LMMs：GPT-4V、Gemini Pro、Qwen-Plus/Max。
  - 开源 LMMs：MiniGPT-4、BLIP-2、InstructBLIP、LLaVA-v1.5 (7B/13B)、SPHINX、InternLM-XComposer。
  - 推理策略：零样本、少样本（2-shot/4-shot）、思维链（CoT）、监督微调（SFT，使用 VisionGraph 训练集）、数据增强（图理解数据）、DPR 链等。
- **评估指标**：
  - 节点识别准确率；边识别正确率与错误率；
  - 具体图问题准确率（如连通性、环检测输出路径的细致准确率）。

## 4. 资源与算力
- 论文未明确说明使用的 GPU 型号、数量或总训练时长。
- 仅列出训练超参数：第一训练阶段 5 个 epoch，batch size 16，AdamW 优化器，学习率 1e-4；第二阶段学习率 3e-5，共 3 个 epoch。梯度检查点和懒惰预处理保持开启。
- 推理时温度设为 0.2，beam size 为 1。
- **需指出**：资源细节缺失，可能影响可重复性。

## 5. 实验数量与充分性
- **实验数量**：论文包含大量实验，主要体现在：
  - 表 3：全模型在 8 个任务上的节点识别、边识别、图问题准确率（含零/少样本、SFT、数据增强等条件）。
  - 表 4：聚焦连通性、环检测、最短路径三个任务，按 easy/medium/hard 难度报告结果，并对比 DPR、Python 工具等变体。
  - 消融实验：引入图理解数据对 LLaVA 的影响；DPR 与零/少样本、CoT 的对比；外部 Python 解释器的作用。
  - 案例分析：展示了若干模型在具体实例上的输出对比。
- **充分性与公平性**：
  - 覆盖了广泛的主流通用 LMMs，且考虑了不同推理策略。
  - 量化指标清晰（正确率、错误率、路径准确率），评价客观。
  - 但数据分布不均衡：某些任务（如拓扑排序、最大流）仅有 easy/hard，缺少 medium；训练集和测试集规模差异较大，可能影响结论的泛化性。

## 6. 主要结论与发现
1. GPT-4V 在多步图推理上全面优于 Gemini Pro。
2. 所有 LMMs 在图结构感知（节点/边识别）上表现不佳，无论采用零/少样本还是微调，错误率往往高于正确率，这严重制约了后续推理。
3. 监督微调和数据增强能够提升图理解能力，但对复杂推理的帮助有限。
4. **DPR 链显著提高了多步推理性能**：GPT-4V(DPR) 在连通性、环检测、最短路径上分别比少样本提升约 8%、10%、14%；结合外部 Python 解释器后提升更明显（分别约 10%、11%、14%）。
5. 多数 LMMs 在最短路径等困难任务上仍无法解决（准确率接近 0），表明当前模型在复杂图推理上仍有巨大差距。

## 7. 优点
- **首创性**：首次系统研究 LMMs 在图论视觉问题上的能力，并构建了专用基准 VisionGraph，涵盖多种难度和问题类型。
- **方法论创新**：DPR 链巧妙融合了自然语言、代码生成和工具调用，形成可操作的多模态 Agent，有效弥补 LMMs 在空间感知上的不足。
- **充分实证**：通过大量实验揭示了 LMMs 在图理解上的普遍短板，并展示了 DPR 的改进效果，结论可靠。
- **开源可复现**：承诺公开基准数据和代码，有助于后续研究。

## 8. 不足与局限
- **数据分布不均衡**：不同任务的样本量差异大（如连通性 2232 个，GNN 仅 240 个），且部分任务缺少 medium 难度，可能影响模型表现的全面评估。
- **视觉图复杂度受限**：为保持可读性，节点数上限设定较低（无向图 25，有向图 20），未涵盖大规模或更复杂图结构，模型泛化性可能受限。
- **模型更新风险**：GPT-4V 和 Gemini 为闭源商业模型，其参数会变化，当前评测结果可能随时间过时。论文提供了部分输出样例以缓解该问题。
- **资源信息缺失**：未提及训练 GPU 型号、数量等关键算力信息，影响可重复性。
- **感知与推理的耦合**：DPR 依赖小模型生成图描述，若描述存在错误，后续推理会受影响。表格中显示 Llava 的 DPR 在部分任务上提升有限，说明感知瓶颈依然存在。
- **应用限制**：当前方法主要针对二维静态图，距离真实世界复杂结构化场景（如动态图、高噪声图）仍有距离。

（完）
