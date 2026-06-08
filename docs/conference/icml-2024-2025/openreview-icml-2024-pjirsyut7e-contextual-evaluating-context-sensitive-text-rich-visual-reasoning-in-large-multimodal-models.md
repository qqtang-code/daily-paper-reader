---
title: "ConTextual: Evaluating Context-Sensitive Text-Rich Visual Reasoning in Large Multimodal Models"
title_zh: "ConTextual: 评估大语言模型在文本丰富视觉推理中的上下文敏感性"
authors: "Rohan Wadhawan, Hritik Bansal, Kai-Wei Chang, Nanyun Peng"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=PjiRSyUt7e"
tags: ["query:multimodal"]
score: 8.0
evidence: 上下文敏感文本丰富视觉推理评估数据集
tldr: 该论文提出ConTextual数据集，用于评估大语言模型在文本丰富图像上的上下文敏感视觉推理能力。数据包含人工设计的指令，强调文本与视觉元素之间的交互关联。对14个基础模型（包括GPT-4V、Gemini-Pro-Vision等）的测试发现，当前模型在此类推理上仍有显著差距，特别是在细粒度上下文理解方面。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 809, \"height\": 450, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 629, \"height\": 523, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1569, \"height\": 825, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 594, \"height\": 591, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 814, \"height\": 571, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 395, \"height\": 480, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1710, \"height\": 431, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1743, \"height\": 352, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1710, \"height\": 599, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1696, \"height\": 605, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1701, \"height\": 697, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1700, \"height\": 307, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1695, \"height\": 571, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1699, \"height\": 332, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 759, \"height\": 758, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 778, \"height\": 848, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1045, \"height\": 780, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1147, \"height\": 783, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1143, \"height\": 780, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 783, \"height\": 540, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 727, \"height\": 504, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 803, \"height\": 713, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 801, \"height\": 692, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1333, \"height\": 360, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 433, \"height\": 532, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 781, \"height\": 594, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 345, \"height\": 366, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-028.webp\", \"caption\": \"\", \"page\": 0, \"index\": 28, \"width\": 202, \"height\": 200, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-029.webp\", \"caption\": \"\", \"page\": 0, \"index\": 29, \"width\": 601, \"height\": 344, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-030.webp\", \"caption\": \"\", \"page\": 0, \"index\": 30, \"width\": 1142, \"height\": 773, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-031.webp\", \"caption\": \"\", \"page\": 0, \"index\": 31, \"width\": 564, \"height\": 357, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-032.webp\", \"caption\": \"\", \"page\": 0, \"index\": 32, \"width\": 681, \"height\": 832, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-033.webp\", \"caption\": \"\", \"page\": 0, \"index\": 33, \"width\": 1097, \"height\": 437, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-034.webp\", \"caption\": \"\", \"page\": 0, \"index\": 34, \"width\": 549, \"height\": 419, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-035.webp\", \"caption\": \"\", \"page\": 0, \"index\": 35, \"width\": 873, \"height\": 605, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-036.webp\", \"caption\": \"\", \"page\": 0, \"index\": 36, \"width\": 939, \"height\": 759, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-037.webp\", \"caption\": \"\", \"page\": 0, \"index\": 37, \"width\": 273, \"height\": 372, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-038.webp\", \"caption\": \"\", \"page\": 0, \"index\": 38, \"width\": 456, \"height\": 560, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-039.webp\", \"caption\": \"\", \"page\": 0, \"index\": 39, \"width\": 550, \"height\": 969, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-040.webp\", \"caption\": \"\", \"page\": 0, \"index\": 40, \"width\": 521, \"height\": 900, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-041.webp\", \"caption\": \"\", \"page\": 0, \"index\": 41, \"width\": 376, \"height\": 651, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-042.webp\", \"caption\": \"\", \"page\": 0, \"index\": 42, \"width\": 617, \"height\": 1071, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-043.webp\", \"caption\": \"\", \"page\": 0, \"index\": 43, \"width\": 1328, \"height\": 892, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-044.webp\", \"caption\": \"\", \"page\": 0, \"index\": 44, \"width\": 1324, \"height\": 903, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-045.webp\", \"caption\": \"\", \"page\": 0, \"index\": 45, \"width\": 1412, \"height\": 211, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-046.webp\", \"caption\": \"\", \"page\": 0, \"index\": 46, \"width\": 1424, \"height\": 620, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-047.webp\", \"caption\": \"\", \"page\": 0, \"index\": 47, \"width\": 1415, \"height\": 951, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-048.webp\", \"caption\": \"\", \"page\": 0, \"index\": 48, \"width\": 462, \"height\": 684, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-049.webp\", \"caption\": \"\", \"page\": 0, \"index\": 49, \"width\": 1098, \"height\": 725, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-050.webp\", \"caption\": \"\", \"page\": 0, \"index\": 50, \"width\": 1024, \"height\": 874, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-051.webp\", \"caption\": \"\", \"page\": 0, \"index\": 51, \"width\": 1379, \"height\": 1041, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-052.webp\", \"caption\": \"\", \"page\": 0, \"index\": 52, \"width\": 1106, \"height\": 633, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-053.webp\", \"caption\": \"\", \"page\": 0, \"index\": 53, \"width\": 925, \"height\": 696, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-054.webp\", \"caption\": \"\", \"page\": 0, \"index\": 54, \"width\": 1060, \"height\": 734, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pjirsyut7e/fig-055.webp\", \"caption\": \"\", \"page\": 0, \"index\": 55, \"width\": 1105, \"height\": 835, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-pjirsyut7e/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1239, \"height\": 543, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pjirsyut7e/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 525, \"height\": 481, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pjirsyut7e/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1596, \"height\": 277, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pjirsyut7e/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 771, \"height\": 120, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pjirsyut7e/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1694, \"height\": 652, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pjirsyut7e/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1331, \"height\": 489, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pjirsyut7e/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1241, \"height\": 237, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pjirsyut7e/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 376, \"height\": 651, \"label\": \"Table\"}]"
motivation: 缺乏评估模型在文本与视觉交互推理中的上下文敏感能力的数据集。
method: 构建人工标注的指令数据集，要求模型联合推理图像中的文本和视觉元素。
result: 测试14个模型，发现它们在上下文敏感推理上表现不足，有较大提升空间。
conclusion: ConTextual揭示了当前多模态模型在文本-视觉联合推理上的短板。
---

## Abstract
Many real-world tasks require an agent to reason jointly over text and visual objects, (e.g., navigating in public spaces), which we refer to as context-sensitive text-rich visual reasoning. Specifically, these tasks require an understanding of the context in which the text interacts with visual elements within an image. However, there is a lack of existing datasets to benchmark the state-of-the-art multimodal models' capability on context-sensitive text-rich visual reasoning. In this paper, we introduce ConTextual, a novel dataset featuring human-crafted instructions that require context-sensitive reasoning for text-rich images. We conduct experiments to assess the performance of 14 foundation models (GPT-4V, Gemini-Pro-Vision, LLaVA-Next) and establish a human performance baseline. Further, we perform human evaluations of the model responses and observe a significant performance gap of 30.8% between GPT-4V (the current best-performing Large Multimodal Model) and human performance. Our fine-grained analysis reveals that GPT-4V encounters difficulties interpreting time-related data and infographics. However, it demonstrates proficiency in comprehending abstract visual contexts such as memes and quotes. Finally, our qualitative analysis uncovers various factors contributing to poor performance including lack of precise visual perception and hallucinations. Our dataset, code, and leaderboard can be found on the project page https://con-textual.github.io/.

---

## 论文详细总结（自动生成）

# 论文《ConTextual: Evaluating Context-Sensitive Text-Rich Visual Reasoning in Large Multimodal Models》详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **现实需求**：许多实际任务（如导航、购物、理解信息图或表情包）要求模型**同时理解图像中的文本与视觉对象**，并基于二者之间的**上下文交互**进行推理。例如，在路口看路牌时，需要结合指示文字和道路布局判断方向。这种能力被称为**上下文敏感的文本丰富视觉推理**。
- **现有数据集不足**：已有数据集（如 TextVQA、STVQA、ESTVQA）主要测试模型的 **OCR 能力**，即仅需识别图像中的文字便可回答问题，**不需要**联合文本与视觉上下文进行推理。例如，问题“这里能吃什么？”可以从 OCR 结果“Angelo's Car Hop Service Hamburgers Laundromat”直接回答，无需理解图像中的视觉布局。
- **研究空白**：缺乏专门评估大语言模型（LMM）在**需要联合文本与视觉上下文推理**能力的基准。
- **论文目标**：提出 **ConTextual 数据集**，设计**人工编写的指令**，要求模型必须同时利用图像中的文本和视觉元素进行推理，以此评估现有 LMM 的真正能力，并揭示其与人类之间的差距。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 2.1 核心思想
- **定义**：上下文敏感文本丰富视觉推理 = 理解文本与视觉元素在图像中的**交互关系**，回答问题时**不能仅靠 OCR 或仅靠视觉**。
- **构建原则**：
  - 每个样本为 `<图像, 指令, 标准答案>` 三元组。
  - 指令必须**强制联合推理**：例如，不能问“图像中有多少文字”，因为仅靠 OCR 可解；也不能问“图像中有什么物体”，因为仅靠视觉可解。必须同时引用文本和视觉属性（如“找到那个带有三个黄色和一个红色圆形物悬挂的船号”）。
  - 涵盖问题式和任务式指令，复杂度多样（信息提取型、数学推理型等）。

### 2.2 数据来源
- **8 种视觉场景**：时间、购物、导航、抽象（表情包/语录）、应用使用（UI）、网页使用、信息图、杂项自然场景。
- **图像来源**：
  - LAION-5B（使用 CLIP 检索 + 关键词 + “text”）；
  - Rico 数据集（移动应用 UI 截图）；
  - OpenWebText 的网站截图；
  - 现有 VQA 数据集（InfographicVQA、STVQA、ESTVQA）的图像，但重新标注新的指令。

### 2.3 数据标注流程
1. **Stage 1**：筛选图像（部分人工，部分基于 OCR 词数启发式筛选）。
2. **Stage 2**：作者分为两组，每组负责 4 个类别，严格遵循标注指南创作指令和答案。
3. **Stage 3**：MTurk 工人验证正确性（96% 正确率），然后两组交叉审核，剔除不合格样本，最终得到 **506 个样本**。
4. 平均指令长度 65 词，平均答案长度 117 词。每个样本还标注了类型（提取/数学推理）。

### 2.4 评估方法
- **人类评估（黄金标准）**：从 506 个样本中随机抽取 280 个，隐藏模型名称，由 3 名 MTurk 工人对每个预测答案判断是否“可接受”，最终采用多数投票得到接受率（0-100%）。
- **自动评估**：
  - 使用 **GPT-4**（仅文字，给定指令+标准答案+预测答案）和 **GPT-4V**（给定图像）进行评分。
  - 标准文本指标：BLEURT、Rouge-L、BERTScore。
- **相关性分析**：计算自动指标与人类判断的 **ROC-AUC** 和 **Spearman 相关系数**，选择最佳自动评估（GPT-4）用于全数据集评估。

## 3. 实验设计：数据集/场景、benchmark、对比方法

### 3.1 数据集与场景
- **ConTextual 数据集**（506 样本），8 个场景：时间（50）、购物（50）、导航（50）、抽象（50）、应用使用（50）、网页使用（50）、信息图（50）、杂项自然场景（156）。
- 额外实验：合成数据（200 样本，由 GPT-4V 生成，属于杂项自然场景）。

### 3.2 对比方法（共 14 个模型 + 人类基线）
- **增强 LLM**（不给图像，只给文本）：
  - GPT-4 + 原始 OCR
  - GPT-4 + 布局感知 OCR（按图像中文字位置排列）
  - GPT-4 + 布局感知 OCR + 图像描述（来自 ShareGPT-4V-7B）
- **专有 LMM**：
  - GPT-4V (OpenAI)
  - Gemini-Pro-Vision
- **开源 LMM**（9 个）：
  - LLaVA-Next-34B、LLaVA-1.5-13B、ShareGPT-4V-7B、Qwen-VL-7B、mPLUG-Owl-v2-7B、InstructBLIP-Vicuna-7B、Idefics-9B、LLaVAR-13B、BLIVA-Vicuna-7B
- **人类基线**：通过 MTurk 收集答案。

### 3.3 评估指标与实验设置
- **主要实验**：零样本评估，使用人类评价（280 样本）和自动评价（全部 506 样本）。
- **少数实验**：
  - 少样本（0-shot、2-shot、4-shot、8-shot）测试 GPT-4 + OCR、Gemini-Pro-Vision、Idefics-9B。
  - 合成数据实验：在 200 个合成样本上测试 GPT-4V、GPT-4 + OCR、LLaVA-1.5-13B、ShareGPT-4V-7B。
- **细粒度分析**：按 8 个场景、按任务类型（提取 vs 数学推理）、按场景自然/数字分类。

## 4. 资源与算力

- 论文**未明确报告 GPU 型号、数量或训练时长**。所有评估基于推理（调用 API 或运行开源模型），不涉及模型训练。
- 主要资源消耗：
  - 人类标注和评估：MTurk 费用 $180（人类基线）+ $1000（人类判断）= 总计 **$1180**。
  - 使用 PaddleOCR 进行 OCR 提取，ShareGPT-4V-7B 生成图像描述（推理）。
  - GPT-4、GPT-4V、Gemini-Pro-Vision 通过 API 调用。

## 5. 实验数量与充分性

| 维度 | 数量 | 评价 |
|------|------|------|
| 单组主实验 | 14 个模型 on 506 样本 | 覆盖广泛，但人类评估仅 280 样本 |
| 少样本实验 | 3 个模型，4 种 shot | 充分展示少样本不显著提升 |
| 合成数据实验 | 200 样本，4 个模型 | 验证合成数据与人工数据的一致性，但规模小 |
| 细粒度分析 | 8 场景、2 任务类型、2 场景类型 | 充分揭示各模型在不同维度上的弱点 |
| 消融实验 | 增强 LLM 三种 OCR 配置对比 | 有限，但足够说明视觉感知的必要性 |
| 相关性分析 | 5 种自动指标 vs 人类 | 确定了最佳自动评估（GPT-4） |
| 统计显著性检验 | 配对 t 检验（95% CI） | 证明模型间差异显著 |

- **充分性**：实验设计合理，对比方法全面，涵盖专有与开源、增强 LLM 与端到端 LMM。人类评估和自动评估结合，并有相关性验证。
- **局限性**：
  - 数据集规模较小（506），可能限制泛化性。
  - 人类评估仅覆盖一半样本，可能引入抽样偏差。
  - 未控制标注者地域/文化背景。
  - 没有涉及模型微调或训练实验。

## 6. 论文的主要结论与发现

1. **人类表现最好**：80.1% 接受率，远高于所有 LMM。
2. **GPT-4V 是最佳 LMM**：49.3%，但与人类差距 30.8%。
3. **开源模型显著落后**：最佳 ShareGPT-4V-7B 仅 21.8%。
4. **增强 LLM 失败**：即使给 OCR 和 caption，GPT-4 仅有 17.2-22.2%，说明**视觉感知不可或缺**。
5. **GPT-4V 在抽象场景上甚至超越人类**（100% vs 人类 75.5%），但在**时间**（18%）和**信息图**（28%）上极弱。
6. **所有模型在时间任务上表现最差**，人类则擅长。
7. **GPT-4 自动评估与人类相关性最高**（ROC-AUC 85.9，Spearman 0.71），标准文本指标（BLEURT等）相关性差。
8. **少样本学习提升不显著**，模型仍需通过训练数据提升。
9. **合成数据生成可行**，但生成的指令质量低于人工标注。
10. **定性分析发现**：失败主因是**缺乏细粒度视觉感知**和**幻觉**（使用先验知识而非图像事实）。

## 7. 优点

- **填补空白**：首次聚焦“上下文敏感文本丰富视觉推理”，与仅测 OCR 的数据集形成鲜明对比。
- **多样化真实场景**：8 个类别覆盖自然与数字场景，指令风格多样，增加评测的全面性。
- **严格的数据质量控制**：三阶段标注 + MTurk 验证 + 作者交叉审核，确保指令必须联合推理。
- **细致的评估设计**：同时使用人类评价和自动评价，并验证相关性，使大规模评估可靠。
- **丰富的细粒度分析**：按类别、任务类型、场景类型、定性示例深入剖析模型弱点，为后续改进提供方向。
- **开源共享**：数据集、代码、排行榜公开，可复现并持续更新。

## 8. 不足与局限

- **数据集规模较小**（506 样本），可能无法覆盖所有复杂文本图像场景，统计稳定性有限。
- **人类评估仅 280 样本**，且由 MTurk 工人判定“可接受性”，主观性较强；未做跨文化验证。
- **标注者主要来自美国**，在处理抽象表情包、语录时可能存在文化偏差，影响基线。
- **未考虑多语言、手写体、文字方向等复杂 OCR 挑战**，这些在现实场景中常见。
- **合成数据实验简单**（仅 200 样本），未系统探索规模扩展的可靠性。
- **未评估更大开源模型**（如 70B 以上），最新 LMM（如 LLaVA-1.6、Gemini Ultra）未包含。
- **未进行训练或微调实验**，无法判断模型通过针对性训练能否提升，限制了应用建议。
- **实验资源未报告**，不利于其他研究者复现或估算成本。

（完）
